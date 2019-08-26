# JavaScript设计模式  Design Pattern



## 设计模式？



### 1.什么是设计模式

**在众所周知的设计书《Domain-Driven Terms》中,它被描述为:**

“设计模式是命名、抽象和识别对可重用的面向对象设计有用的的通用设计结构。设计模式确定类和他们的实体、他们的角色和协作、还有他们的责任分配。

每一个设计模式都聚焦于一个面向对象的设计难题或问题。

> 反正我不知道，W3Cschool上copy下来的

**百度的解释：**

设计模式（Design Pattern）是一套被反复使用、多数人知晓的、经过分类的、代码设计经验的总结。

**《JavaScript设计模式与开发实践》的解释：**

假设有一个空房间，我们要日复一日地往里 面放一些东西。最简单的办法当然是把这些东西 直接扔进去，但是时间久了，就会发现很难从这 个房子里找到自己想要的东西，要调整某几样东 西的位置也不容易。所以在房间里做一些柜子也 许是个更好的选择，虽然柜子会增加我们的成 本，但它可以在维护阶段为我们带来好处。使用 这些柜子存放东西的规则，或许就是一种模式



### 2.为什么要使用设计模式

使用设计模式的**目的**：为了代码可重用性、让代码更容易被他人理解、保证代码可靠性。 设计模式使代码编写真正工程化；设计模式是[软件工程](https://baike.baidu.com/item/软件工程/25279)的基石脉络，如同大厦的结构一样。

所以同时，不能为了使用设计模式而使用设计模式，不加思考只会适得其反。

*总结：高内聚，低耦合*

### 3.怎么学

> 来自知乎

每一个模式其实都是一些很简单的内容，但是为什么要这么写，哪怕你看了[GoF](https://baike.baidu.com/item/GoF/6406151?fr=aladdin)原版你也是看不明白的。你唯有亲自写一个大程序，因为没有使用设计模式被搞得焦头烂额，你才能明白为什么要那么写。

初学者我建议写一个1万行的app，你就应该可以懂一部分了。如果你没有用设计模式也把一万行的程序写出来了，那证明你可能天资聪颖，需要写更大的程序，直到你因为没有使用设计模式而根本写不出来为止。

*总结：实践出真知*



### 4.设计模式的分类

#### 创建型设计模式

创建型设计模式关注于对象创建的机制方法，通过该方法,对象以适应工作环境的方式被创建。基本的对象创建方法可能会给项目增加额外的复杂性，而这些模式的目的就是为了通过控制创建过程解决这个问题。

属于这一类的一些模式是：构造器模式（Constructor）,工厂模式（Factory）,抽象工厂模式 （Abstract）,原型模式 （Prototype）,单例模式 （Singleton）以及 建造者模式（Builder）。

#### 结构设计模式

结构模式关注于对象组成和通常识别的方式实现不同对象之间的关系。该模式有助于在系统的某一部分发生改变的时候，整个系统结构不需要改变。该模式同样有助于对系统中某部分没有达到某一目的的部分进行重组。

在该分类下的模式有：装饰模式，外观模式，享元模式，适配器模式和代理模式。

#### 行为设计模式

行为模式关注改善或精简在系统中不同对象间通信。

行为模式包括：策略模式，迭代模式，中介者模式，观察者模式和访问者模式。



### 5.补充

《JavaScript设计模式与开发实践》中介绍的十四种常用模式

- 单例模式
- 策略模式
- 代理模式
- 迭代器模式
- 发布—订阅模式
- 命令模式
- 组合模式
- 模板方法模式
- 享元模式
- 职责链模式
- 中介者模式
- 装饰者模式
- 状态模式
- 适配器模式



## 要讲的几个设计模式

> 但是由于能力和时间问题，这里只讲几个。



### 创建型

> 部分见demos



#### 1.构造器模式

> 其实就是构造函数



#### 2.原型模式

> 用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象



#### 3.构建者模式/建造者模式

> 将一个复杂的对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。



#### 4.工厂模式

> 工厂模式中，我们在创建对象时不会对客户端暴露创建逻辑，并且是通过使用一个共同的接口来指向新创建的对象，用工厂方法代替new操作的一种模式。

~~~javascript
class Creator {
    create(name) {
        return new Animal(name)
    }
}

class Animal {
    constructor(name) {
        this.name = name
    }
}

var creator = new Creator()

var duck = creator.create('Duck')
console.log(duck.name) // Duck

var chicken = creator.create('Chicken') 
console.log(chicken.name) // Chicken
~~~

**构造函数和创建者分离，对new操作进行封装**



*PS:抽象工厂模式*



#### 5.单例模式

> 保证一个类仅有一个实例，并提供一个访问它的全局访问点

**构造函数和创建者分离，对new操作进行封装**





### 结构型



#### 1.适配器模式

> ![img](https://segmentfault.com/img/remote/1460000017787541?w=1152&h=324)

举一个书中渲染地图的例子

~~~javascript
class GooleMap {
    show() {
        console.log('渲染谷歌地图')
    }
}

class BaiduMap {
    show() {
        console.log('渲染百度地图')
    }
}

function render(map) {
    if (map.show instanceof Function) {
        map.show()
    }
}

render(new GooleMap())  // 渲染谷歌地图
render(new BaiduMap())  // 渲染百度地图
~~~

但是假如BaiduMap类的原型方法不叫show，而是叫display，这时候就可以使用适配器模式了，因为我们不能轻易的改变第三方的内容。在BaiduMap的基础上封装一层，对外暴露show方法。

~~~javascript
class GooleMap {
    show() {
        console.log('渲染谷歌地图')
    }
}

class BaiduMap {
    display() {
        console.log('渲染百度地图')
    }
}


// 定义适配器类, 对BaiduMap类进行封装
class BaiduMapAdapter {
    show() {
        var baiduMap = new BaiduMap()
        return baiduMap.display() 
    }
}

function render(map) {
    if (map.show instanceof Function) {
        map.show()
    }
}

render(new GooleMap())         // 渲染谷歌地图
render(new BaiduMapAdapter())  // 渲染百度地图
~~~

**适配器模式主要解决两个接口之间不匹配的问题，不会改变原有的接口，而是由一个对象对另一个对象的包装。**



#### 2.代理模式

> 为一个对象提供一个代用品或占位符，以便控制对它的访问
>
> 当客户不方便直接访问一个 对象或者不满足需要的时候，提供一个替身对象 来控制对这个对象的访问，客户实际上访问的是 替身对象。
>
> 替身对象对请求做出一些处理之后， 再把请求转交给本体对象
>
> 代理和本体的接口具有一致性，本体定义了关键功能，而代理是提供或拒绝对它的访问，或者在访问本体之前做一 些额外的事情

代理模式主要有三种：保护代理、虚拟代理、缓存代理

以过滤字符作为简单的例子

```javascript
// 主体，发送消息
function sendMsg(msg) {
    console.log(msg);
}

// 代理，对消息进行过滤
function proxySendMsg(msg) {
    // 无消息则直接返回
    if (typeof msg === 'undefined') {
        console.log('deny');
        return;
    }
    
    // 有消息则进行过滤
    msg = ('' + msg).replace(/泥\s*煤/g, '');

    sendMsg(msg);
}


sendMsg('泥煤呀泥 煤呀'); // 泥煤呀泥 煤呀
proxySendMsg('泥煤呀泥 煤'); // 呀
proxySendMsg(); // deny
```



### 行为型



#### 1.策略模式

> 定义一系列的算法，把它们一个个封装起来，并使它们可以替换

~~~javascript
var fnA = function(val) {
    return val * 1
}

var fnB = function(val) {
    return val * 2
}

var fnC = function (val) {
    return val * 3
}


var calculate = function(fn, val) {
    return fn(val)
}

console.log(calculate(fnA, 100))// 100
console.log(calculate(fnB, 100))// 200
console.log(calculate(fnC, 100))// 300
~~~



#### 2.发布—订阅模式/观察者模式

> 定义了对象间的一种一对多的依赖关系，当一个对象的状态发 生改变时，所有依赖于它的对象都将得到通知

栗子0：比如说我在给你们讲课，我就是发布者，你们就是订阅者，多个订阅者之间相互独立，但我作为一个发布者，发布一个消息，你们都做出响应。

栗子1：最简单的观察者模式

```javascript
// 订阅者
function a(){
    console.log('aaaaa')
}
function b(){
    console.log('bbbbb')
}
function c(){
    console.log('ccccc')
}

//发布者
function all(){
    a();
    b();
    c();
}

// 发布消息
all()
```



栗子2：JS中的事件就是经典的发布-订阅模式的实现

~~~javascript
// 订阅
document.body.addEventListener('click', function() {
    console.log('click1');
}, false);

document.body.addEventListener('click', function() {
    console.log('click2');
}, false);

// 发布
document.body.click(); // click1  click2
~~~



栗子3：小A在公司C完成了笔试及面试，小B也在公司C完成了笔试。他们焦急地等待结果，每隔半天就电话询问公司C，导致公司C很不耐烦。

一种解决办法是 AB直接把联系方式留给C，有结果的话C自然会通知AB

这里的“询问”属于显示调用，“留给”属于订阅，“通知”属于发布

~~~javascript
// 观察者
var observer = {
    // 订阅集合
    subscribes: [],

    // 订阅
    subscribe: function(type, fn) {
        if (!this.subscribes[type]) {
            this.subscribes[type] = [];
        }
        
        // 收集订阅者的处理
        typeof fn === 'function' && this.subscribes[type].push(fn);
    },

    // 发布  可能会携带一些信息发布出去
    publish: function() {
        var type = [].shift.call(arguments),
            fns = this.subscribes[type];
        
        // 不存在的订阅类型，以及订阅时未传入处理回调的
        if (!fns || !fns.length) {
            return;
        }
        
        // 挨个处理调用
        for (var i = 0; i < fns.length; ++i) {
            fns[i].apply(this, arguments);
        }
    },
    
    // 删除订阅
    remove: function(type, fn) {
        // 删除全部
        if (typeof type === 'undefined') {
            this.subscribes = [];
            return;
        }

        var fns = this.subscribes[type];

        // 不存在的订阅类型，以及订阅时未传入处理回调的
        if (!fns || !fns.length) {
            return;
        }

        if (typeof fn === 'undefined') {
            fns.length = 0;
            return;
        }

        // 挨个处理删除
        for (var i = 0; i < fns.length; ++i) {
            if (fns[i] === fn) {
                fns.splice(i, 1);
            }
        }
    }
};

// 订阅岗位列表
function jobListForA(jobs) {
    console.log('A', jobs);
}

function jobListForB(jobs) {
    console.log('B', jobs);
}

// A订阅了笔试成绩
observer.subscribe('job', jobListForA);
// B订阅了笔试成绩
observer.subscribe('job', jobListForB);


// A订阅了笔试成绩
observer.subscribe('examinationA', function(score) {
    console.log(score);
});

// B订阅了笔试成绩
observer.subscribe('examinationB', function(score) {
    console.log(score);
});

// A订阅了面试结果
observer.subscribe('interviewA', function(result) {
    console.log(result);
});

observer.publish('examinationA', 100); // 100
observer.publish('examinationB', 80); // 80
observer.publish('interviewA', '备用'); // 备用

observer.publish('job', ['前端', '后端', '测试']); // 输出A和B的岗位


// B取消订阅了笔试成绩
observer.remove('examinationB');
// A都取消订阅了岗位
observer.remove('job', jobListForA);

observer.publish('examinationB', 80); // 没有可匹配的订阅，无输出
observer.publish('job', ['前端', '后端', '测试']); // 输出B的岗位
~~~



## 设计原则

**单一职责原则（SRP）**

一个对象或方法只做一件事情。如果一个方法承担了过多的职责，那么在需求的变迁过程中，需要改写这个方法的可能性就越大。

应该把对象或方法划分成较小的粒度

**最少知识原则（LKP）**

一个软件实体应当 尽可能少地与其他实体发生相互作用 

应当尽量减少对象之间的交互。如果两个对象之间不必彼此直接通信，那么这两个对象就不要发生直接的 相互联系，可以转交给第三方进行处理

**开放-封闭原则（OCP）**

软件实体（类、模块、函数）等应该是可以 扩展的，但是不可修改

当需要改变一个程序的功能或者给这个程序增加新功能的时候，可以使用增加代码的方式，尽量避免改动程序的源代码，防止影响原系统的稳定

> 开放-封闭原则是终极目的



## 友情链接

[JavaScript常用设计模式](https://segmentfault.com/a/1190000017787537?utm_source=tag-newest#articleHeader0)

[JavaScript中常见的十五种设计模式](https://www.cnblogs.com/imwtr/p/9451129.html)

[JavaScript中常见设计模式整理](https://juejin.im/post/5afe6430518825428630bc4d)

[W3Cschool的js设计模式教程](https://www.w3cschool.cn/zobyhd/j9r8eozt.html)

[W3Cschool设计模式](https://www.w3cschool.cn/shejimoshi/design-pattern-intro.html)

[菜鸟教程设计模式](https://m.runoob.com/design-pattern/)