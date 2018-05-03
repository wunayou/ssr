## react 16 ssr 解决问题
- 同构的理解
- API的理解
- CSS的处理
- 数据的理解

### 同构的理解
所谓同构，简单的说就是客户端的代码可以在服务端运行，好处就是能极大的提升首屏时间，避免白屏，另外同构也给SEO提供了很多便利。

React 同构得益于 React 的虚拟 DOM。虚拟 DOM 以对象树的形式保存在内存中，并存在前后端两种展现形式。

在客户端上，虚拟 DOM 通过 ReactDOM 的 render 方法渲染到页面中，形成真实的 dom。
在服务端上，React 提供了另外两个方法： ReactDOMServer.renderToString 和 ReactDOMServer.renderToStaticMarkup 将虚拟 DOM 渲染为 HTML 字符串。
在服务端通过 ReactDOMServer.renderToString 方法将虚拟 DOM 渲染为 HTML 字符串，到客户端时，React 只需要做一些事件绑定等操作就可以了。

在这一整套流程中，保证 DOM 结构的一致性是至关重要的一点。 React 通过 data-react-checksum来检测一致性，即在服务端产生 HTML 字符串的时候会额外的计算一个 data-react-checksum 值，客户端会对这个值进行校验，如果与客户端计算的值一致，则 React 只会进行事件绑定，如果不一致，React 会丢弃服务端返回的 dom 结构重新渲染。


