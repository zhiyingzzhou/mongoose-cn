## 开始

首先确保你已经安装了[Mongodb](#)和[Node.js](#).
下一步在命令行中使用npm安装mongoose：

`
    $ npm install mongoose
`

现在说我们喜欢毛绒绒的小猫并且想记录我们在mongodb遇见的每一只小猫.第一件事我们需要在我们的项目中导入mongoose然后连接到我们在本地运行的MongoDB实例中的test数据库.
```js
    //getting-started.js 
    const mongoose = require('mongoose');
    mongoose.connect('mongodb://localhost/test')
```
我们已经有了一个挂起到test数据库的本地连接.我们现在需要在连接成功或连接失败的时候得到通知:
```js
    const db = mongoose.connection;
    db.on('err',console.error.bind(console,'connection error:'));
    db.once('open',function(){
        //我们已经连接成功了
    });
```
一旦我们连接成功,我们的回调函数将会被调用.为了简洁,我们将会把下面的代码写在这个回调函数中.
使用Mongoose,一切都是从Schema开始的.