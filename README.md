# react-ecosystem

## fetch 参数
注意问题：
- POST数据时content-type必须为json否则接受不到参数
- php不能打印参数，否则前台报错，跨域的错误

```javascript
function requestDelete() {
	return fetch(API.COMMENT_DELETE, {
		method: "POST",  // 接口是POST类型
		headers: {       // 指定header类型
			'Accept': 'application/json',
			'Content-Type': 'application/json' 
			// 必须设置content-type为json否则php接受不到参数
		},
		body: JSON.stringify({'data':[{"id":"572849707eb738db128b4567","qid":"351025251462257996","aid":1}]})  
		// 请求体，也就是传参的部分
	}).then(response => { response.json() }).then(() => {
		message.destroy();
		message.success("删除成功");
		dispatch(loadComment(page, 0)); 
		// 删除成功之后重新加载页面
	})
		.catch(err => {
			message.destroy();
			message.error(err);
		});
}
```
---
- [ HTTP的请求方法OPTIONS](http://blog.csdn.net/leikezhu1981/article/details/7402272)
