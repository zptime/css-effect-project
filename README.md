# css-effect-project

> css效果体验

1. 准备工作
- html文件、css文件、谷歌浏览器Chrome、编辑器VSCode
- Live Sass Compiler（VSCode插件）：用于实时编译sass/scss文件为css文件
- Live Server（VSCode插件）：用于启动具有实时刷新功能的本地开发服务器，以处理静态页面和动态页面

2. 启动服务
- 打开index.scss，按F1或Cmd + Shift + P打开命令面板，输入Watch Sass监听index.scss并生成index.css；停止监听Live Sass: Stop Watching Sass
- 输入Open With Live Server启动本地开发服务器并打开浏览器

3. css效果实现
- 全屏布局：由顶部、底部和主体三部分组成，其特点为三部分左右满屏拉伸、顶部底部高度固定和主体高度自适应
  - position定位：absolute + left/right/top/bottom
  - flex布局：顶部和底部高度固定，主体flex:1让高度自适应
- 两列布局：一列宽度固定、另一列宽度自适应和两列高度固定且相等
  - float布局：float + margin-left/right
  - float/overflow实现：overflow:hidden使其形成BFC区域与外界隔离
  - flex布局：主体flex:1让宽度自适应
  - calc函数：position + calc(100% - 100px)
- 三列布局：由左中右三列组成，其特点为连续两列宽度固定、剩余一列宽度自适应和三列高度固定且相等
  - overflow + float实现
  - flex布局：主体flex:1让宽度自适应
- 经典的圣杯布局和双飞翼布局：都是由左中右三列组成，其特点为左右两列宽度固定、中间一列宽度自适应和三列高度固定且相等。
  - 相同
    - 中间列放首位且声明其宽高占满父节点
    - 被挤出的左右列使用float和margin负值将其拉回与中间列处在同一水平线上
  - 不同
    - 圣杯布局：父节点声明padding为左右列留出空位，将左右列固定在空位上
    - 双飞翼布局：中间列插入子节点并声明margin为左右列让出空位，将左右列固定在空位上
  - 圣杯布局float + margin-left/right + padding-left/right
  - 双飞翼布局float + margin-left/right
  - 圣杯布局/双飞翼布局flex
- 经典的均分布局：由多列组成，其特点为每列宽度相等和每列高度固定且相等
  - float + width：N列就用公式100 / n求出最终百分比宽度，记得保留2位小数，懒人还可用width:calc(100% / n)自动计算
  - flex布局
- 居中布局：由父容器与若干个子容器组成，子容器在父容器中横向排列或竖向排列且呈水平居中或垂直居中。
- 垂直方向的布局（sticky footer）：将页面分成上、中、下三个部分，上、下部分都为固定高度，中间部分高度不定。当页面高度小于浏览器高度时，下部分应固定在屏幕底部；当页面高度超出浏览器高度时，下部分应该随中间部分被撑开，显示在页面最底部。
  - flex布局：footer的flex设为0，这样footer获得其固有的高度；content的flex设为1，这样它会充满除去footer的其他部分。
- 粘性布局（sticky）：在页面滚动的时候保持元素在页面视图上方，也就是我们常常看到的吸附效果。
  - position: sticky;