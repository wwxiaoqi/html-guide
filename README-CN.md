# HTML-guide

> [English](README.md) | 中文

这是一个使用 HTML + CSS + JavaScript 写的导航栏，创造它只是为了自己搭建一个引用于 [EtherDream/jsproxy](https://github.com/EtherDream/jsproxy) 的导航，因为它的导航实在是太简陋啦（：

在原有的基础上，在右上角添加了个开关，用于快速开启代理模式访问。

![snipaste](img/snipaste.png)


## 安装方法

1. 首先你要根据 [jsProxy CloudFlare Worker](https://github.com/EtherDream/jsproxy/tree/master/cf-worker#部署)
先将 cf-worker 部署到 CloudFlare Worker

2. 给你部署成功的 CloudFlare Worker 设置自定义域名（进入到 Workers & Pages 界面，在 Triggers 下的 Custom Domains 添加你的域名）

3. Fork 本项目，修改 js/index.js proxy_url 内容：
    ```js
    // 修改此处
    var proxy_url = "https:// 上面部署的域名 /-----";

    // 假如我的部署的域名是：proxy.abc.com
    // 那么这里则需填写（后面的 /----- 需保留）：
    var proxy_url = "https://proxy.abc.com/-----";
    ```

4. 创建一个 CloudFlare Pages，选择 Fork 的仓库，Production branch 设置为 main，Framework preset 设置为 None，接着一直下一步直到部署完毕

5. 给 CloudFlare Pages 设置自定义域名（部署完毕后，找到 Custom domains 填写你的自定义访问域名）

6. 到这里已经部署完毕啦，恭喜~


## 自定义导航数据

你可以配置属于你的导航链接，你只需要修改 Fork 项目中的  js/index.js comm_list 内容和 index.html 即可，举例：

index.html 相关代码：
```html
<div class="tab">
    <span class="class1">标题1</span>
	......
</div>
```

js/index.js 相关代码：
```javascript
var comm_list = [
  {
    slug: "class1",
    list: [
      {
        tag: "左侧标签",
        link: [
          { name: "网站名称", url: "网站链接" },
          { name: "谷歌", url: "https://www.google.com/" },
          ......
        ],
      },
    ],
  },
  ......
];

```
注意这里的 html class="class1" 需要和 javascript slug: "class1" 对应上，网站链接需要加上 https://


## 感谢

感谢 [EtherDream/jsproxy](https://github.com/EtherDream/jsproxy) 

感谢 [Jquery](https://jquery.com/)

感谢 [JavaScript Cookie Tools](https://github.com/js-cookie/js-cookie)

