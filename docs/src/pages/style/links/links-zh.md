---
components: Link
---
# 链接

<p class="description">Link组件允许您使用主题颜色和排版样式轻松自定义锚元素。</p>

## 简单的链接

Link组件构建在 [Typography](/api/typography/) 组件之上。 您可以利用其属性。

{{"demo": "pages/style/links/Links.js"}}

但是，Link具有与Typography不同的默认属性： - `color ="primary"` 因为链接需要脱颖而出。 - `variant ="inherit"` 因为链接将在大多数情况下用作Typograpy组件的子级。

## 无障碍功能

- 在提供链接的内容时，请避免使用“点击此处”或“转到”等常规说明。 相反，使用 [具体描述](https://developers.google.com/web/tools/lighthouse/audits/descriptive-link-text)。
- 为了获得最佳用户体验，链接应该从页面上的文本中脱颖而出。
- 如果链路不具有有意义的href， [应该使用来呈现 `<button>` 元件](https://github.com/evcohen/eslint-plugin-jsx-a11y/blob/master/docs/rules/anchor-is-valid.md)。

{{"demo": "pages/style/links/ButtonLink.js"}}

## 安全

当使用 `target="_blank"` 带链接的是 [推荐](https://developers.google.com/web/tools/lighthouse/audits/noopener) 总是设置 的`rel ="noopener"` 或 `的rel ="noreferrer"` 链接到第三方内容时。

- `rel =“noopener”` 阻止新页面访问window.opener属性并确保它在单独的进程中运行。 如果没有此页面，目标页面可能会将您的页面重定向到恶意URL。
- `rel ="noreferrer"` 具有相同的效果，但也阻止将 *Referer* 标头发送到新页面。 ⚠️删除引荐来源标题会影响分析。

## 第三方路由库

One common use case is to perform the navigation on the client only, without doing a .html round-trip with the server. The `Link` component provides a property to handle this use case: `component`.

```jsx
import { Link as RouterLink } from 'react-router-dom'
import Link from '@material-ui/core/Link';

<Link component={RouterLink} to="/open-collective">
  Link
</Link>
```

or if you want to avoid properties collision:

```jsx
import { Link as RouterLink } from 'react-router-dom'
import Link from '@material-ui/core/Link';

const MyLink = props => <RouterLink to="/open-collective" {...props} />

<Link component={MyLink}>
  Link
</Link>
```

*Note: Creating `MyLink` is necessary to prevent unexpected unmounting. You can read more about it in our [component property guide](/guides/composition/#component-property).*