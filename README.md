# ES6notes
the notes wrote down when reading the ES6 grammar
# ES6 语法笔记



### 字符串拓展

1 加强了Unicode的支持，允许使用 '\uxxxx' 表示一个字符，其中 xxxx 表示字符的码店

2 字符串的遍历器接口



字符串新增方法

1 String.fromCodePoint()

2 String.raw()

3 codePointAt()

4 normalize()



### 数值的拓展

1 二进制和八进制分别用前缀 0b 或者 0o 表示，其中八进制明确要使用前缀 0o 表示

2 数值分隔符，ES6中允许使用 _ 作为数值分隔符，可以隔一个以上的位数添加一个

	- 其中不能放在最前面和最后面
	- 不能两个或者以上的分隔符放在一起
	- 小数点的前后不能有分隔符
	- 科学技术法里面的e 或者 E 前后不能有分隔符

3 使用 `Number.isFinite()`, `Number.isNaN()` 用来检查一个数值是否为有限的或者是`NaN`

4 `parseInt` 和 `parseFloat` 方法移植到 Number 类上

5 `Number.isInteger` 用来判断一个数值是否为整数

6 `Number.EPSILON` 用来表示 1 和 大于1 的最小浮点数之间的差

7 安全整数和 `Number.isSafeInteger`

8 `Math.trunc` 方法用于去除一个数的小数部分，返回整数部分

9 `Math.sign` 方法判断一个数到底是正数、负数还是正零或者负零

10 `Math.cbrt` 方法用于计算一个数的立方根

11 `Math.clz32` 方法将参数转为 `32` 位无符号整数的形式，然后返回这个 `32` 位值里面有多少个前导 `0`

12 `BigInt` 解决了 `64` 位存储的限制，必须要加上n后缀

13 可以使用`Boolean()`、`Number()`和`String()`这三个方法，将 BigInt 可以转为布尔值、数值和字符串类型

### 函数的拓展

#### 参数默认值

1  允许为函数的参数设置默认值，即是直接写在参数定义的后面

2 可以和解构赋值默认值结合使用

3 参数默认值的位置

4 函数的 length 属性

5 一旦设置了参数的默认值，函数进行初始化时候，参数会形成一个单独的作用域 context

#### rest 参数

ES6 引入 rest 参数（形式为`...变量名`），用于获取函数的多余参数，这样就不需要使用`arguments`对象了

#### name属性

函数内部引入name属性返回函数名

ES6 引入 rest 参数（形式为`...变量名`），用于获取函数的多余参数，这样就不需要使用`arguments`对象了



### 数组拓展

1 使用拓展运算符 

	- 实现了Iterator的对象
	- Map 和 Set 结构，Generator 函数

2 Array.from() 用于将 类似数组的 和 可遍历的对象转化为真正的数组：其中所谓类似数组的对象，本质上是拥有 `length` 属性的对象

3 Array.of() 将一组值转换为数组

4 数组实例的copyWithin()：修改当前数组，将指定位置的成员复制到其他位置

​	Array.proptotype.copyWithin( target, start = 0, end = this.length )

5 数组实例的 find() 和 findIndex() ：

	- find 方法用于找出第一个符合条件的成员
	- findIndex() 方法用于返回第一个符合条件的成员的位置

6 数组实例的 fill()

​	使用给定值填充数组

7 数组实例的 entries() , keys() 和 values()

​	唯一区别是 keys() 是对键名的遍历，values() 是对键值的遍历，entries() 是对键值对的遍历

8 数组实例的 includes() 方法

​	返回一个布尔值，表示该数组是否包含给定的值

9 数组实例的 flat() 和 flatMap() 

​	其中 flat() 用于将嵌套的数组拉平变为一维的数组，本质上是把数组的为数拉低一层

​	想要拉平多维的数组，需要传入参数，参数为需要拉平的维度数

10 ES6默认把Array 数组的空位处理为 undefined

11 sort() 排序算法必须是稳定的

### 对象的拓展

1 属性的简洁表示法

2 ES6允许用字面量定义对象，即是属性名表达式：属性名表达式和简洁表示法不能同时使用，且属性名表达式如果是一个对象，默认情况下会自动将对象转换为字符串 [object Obecjt]

3 如果对象的方法使用了取值函数和存值函数，则 name 属性不是在该方法上面，而是该方法的属性的描述对象的 get 和

set 属性上面，返回值是方法名前加上 get 和 set

4 函数的每个属性都有一个描述对象 `Descriptor` 用来控制该属性对象的行为，`Object.getOwnPropertyDescriptor` 方法可以获取该属性的描述对象。

5 属性的可枚举性和遍历，有四个操作会忽略 `enumerable` 属性，称为可枚举性

​	目前有四个操作会忽略 `enumerable` 为 false 的属性

​	`for...in` 循环, `Object.keys() `, ` JSON.stringify()`,  `Object.assign()`

6 拓展运算符的解构赋值，不能复制继承自原型对象的属性



### 对象的新增方法 

​	Object.is() 与 === 基本一致，其中有两处不同，+0 不等于 -0，还有 NaN 等于自身

​	Object.assign() 用于对象的合并，1 是浅拷贝，2 同名属性会替换，3 可以处理数组但是会把数组当作对象处理，4 取值函数的处理，如果是取值函数则会先取值再复制

​	Object.assign() 方法的常见用途，1 为对象添加属性， 2 为对象添加方法，3 克隆对象只能克隆自身不能克隆继承的属性和值， 4 合并多个对象，5 为属性指定默认值

​	Object.getOwnPropertyDescriptors() 方法会返回某个对象属性的描述对象

​	\__proto__属性 Object.setPrototypeOf() 和 Object.getPrototypeOf()

​	`Object.keys(), Object.values(), Object.entries()` 分别返回参数对象自身的属性名字、属性键值和属性的键值对数组

​	`Object.fromEntries()` 是方法 `Object.entries()` 的逆操作，用于将一个键值对数组转换成为对象



`指数运算符`

​	** 是右结合的指数运算符

链判断运算符

​	?. 用来简化链判断的安全写法

Null 判断运算符

​	??  只有在运算符左侧为 null 或者 undefined 值时，才会返回右侧的值

逻辑赋值运算符

​	先进行逻辑判断在进行赋值

### Set 和 Map

#### Set 对象

​	Set 结构的实例有以下属性。

- `Set.prototype.constructor`：构造函数，默认就是`Set`函数。
- `Set.prototype.size`：返回`Set`实例的成员总数。

Set 

​	实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。下面先介绍四个操作方法。

- `Set.prototype.add(value)`：添加某个值，返回 Set 结构本身。
- `Set.prototype.delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
- `Set.prototype.has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。
- `Set.prototype.clear()`：清除所有成员，没有返回值。

#### Map 对象

​	size() 返回 Map 结构成员的总数

​	set() 设置键名 key 对应的键值

​	get() 读取 key 对应的键值

​	has() 返回一个布尔值

​	delete() 删除某个键

​	clear() 清除所有成员

WeakMap 是弱引用，防止内存泄漏

WeakRef 是基于弱引用的数据结构

FinalizationRegistry

​	

Proxy 支持的拦截操作

- **get(target, propKey, receiver)**：拦截对象属性的读取，比如`proxy.foo`和`proxy['foo']`。
- **set(target, propKey, value, receiver)**：拦截对象属性的设置，比如`proxy.foo = v`或`proxy['foo'] = v`，返回一个布尔值。
- **has(target, propKey)**：拦截`propKey in proxy`的操作，返回一个布尔值。
- **deleteProperty(target, propKey)**：拦截`delete proxy[propKey]`的操作，返回一个布尔值。
- **ownKeys(target)**：拦截`Object.getOwnPropertyNames(proxy)`、`Object.getOwnPropertySymbols(proxy)`、`Object.keys(proxy)`、`for...in`循环，返回一个数组。该方法返回目标对象所有自身的属性的属性名，而`Object.keys()`的返回结果仅包括目标对象自身的可遍历属性。
- **getOwnPropertyDescriptor(target, propKey)**：拦截`Object.getOwnPropertyDescriptor(proxy, propKey)`，返回属性的描述对象。
- **defineProperty(target, propKey, propDesc)**：拦截`Object.defineProperty(proxy, propKey, propDesc）`、`Object.defineProperties(proxy, propDescs)`，返回一个布尔值。
- **preventExtensions(target)**：拦截`Object.preventExtensions(proxy)`，返回一个布尔值。
- **getPrototypeOf(target)**：拦截`Object.getPrototypeOf(proxy)`，返回一个对象。
- **isExtensible(target)**：拦截`Object.isExtensible(proxy)`，返回一个布尔值。
- **setPrototypeOf(target, proto)**：拦截`Object.setPrototypeOf(proxy, proto)`，返回一个布尔值。如果目标对象是函数，那么还有两种额外操作可以拦截。
- **apply(target, object, args)**：拦截 Proxy 实例作为函数调用的操作，比如`proxy(...args)`、`proxy.call(object, ...args)`、`proxy.apply(...)`。
- **construct(target, args)**：拦截 Proxy 实例作为构造函数调用的操作，比如`new proxy(...args)`。

ES6 原生提供了 Promise 对象，所谓的 Promise 就是一个容器，

​	Promise 对象有两个特点：

		- 对象的状态不受外界影响， Promise 对象有三种状态分别是： pending（进行中）、fulfilled（已成功）、rejected（已失败）。只有异步操作的结果可以决定当前的状态。
		- 一旦状态改变就不会变化，任何时候都是这个结果。Promise 对象改变，只有两种可能：从 pending 变成 fulfilled 和 从 pending 变成 rejected 。只要有两种情况发生，状态就会凝固并且不会发生改变，一直保持这个结果，这时候的状态称之为 resolved 。

Promise 对象是一个构造函数，用来生成 Promise 实例。Promise 构造函数接受一个函数作为参数，该函数的两个参数分别是 resolve 和 reject ，它们是两个函数，由JavaScript引擎提供，不用自己部署。

resolve 函数的作用是，将 Promise 对象的状态从 “ 未成功 ” 变为 “ 成功 ” ，在异步操作成功时调用。

Promise 实例方法生成之后可以用then 方法分别指定 resolved 状态和 rejected 状态的回调函数。第一个回调函数是在状态变为 resolved 时调用的，第二个回调函数是 Promise 对象的状态变为 rejected 时调用的。

Promise.all() 方法用于多个 Promise 实例，包装成一个新的 Promise 实例

```javascript
const p = Promise.all([p1, p2, p3])
```

​	其中 p 的状态是由 p1, p2, p3 决定，分为两种情况

​		1 只有 p1 p2 p3 的状态都变成 fullfilled，p 的状态才变成 fullfilled，此时 p1 p2 p3 的返回值组成一个数组，传递给 p 的回调函数

​		2 只要 p1 p2 p3 的其中一个状态变为 rejected 此时第一个 rejected 的实例的返回值会被传递给 p 的回调函数

Promise.race()

​	Promise.race()方法同样是将多个 Promise 实例，包装成一个新的 Promise 实例。方法中只要有一个参数实例率先改变状态，返回对象的状态就会随之改变。那个率先改变的 Promise 实例的返回值，就传递给p的回调函数。

Promise.allSettle()

​	Promise.all()方法只适合所有异步操作都成功的情况，如果有一个操作失败，就无法满足要求。

Promise.any()

​	any()方法只要参数实例有一个变成fulfilled状态，包装实例就会变成fulfilled状态；如果所有参数实例都变成rejected状态，包装实例就会变成rejected状态。

Promise.resolve()

（1）参数是一个 Promise 实例

​		如果参数是 Promise 实例，那么Promise.resolve将不做任何修改、原封不动地返回这个实例。

（2）参数是一个thenable对象

​		Promise.resolve()方法会将这个对象转为 Promise 对象，然后就立即执行thenable对象的then()方法。

（3）参数不是具有then()方法的对象，或根本就不是对象

​		如果参数是一个原始值，或者是一个不具有then()方法的对象，则Promise.resolve()方法返回一个新的 Promise 对象，状态为resolved。

（4）不带有任何参数

​		Promise.resolve()方法允许调用时不带参数，直接返回一个resolved状态的 Promise 对象。如果希望得到一个 Promise 对象，可以直接调用Promise.resolve()方法。

Promise.reject()

​	Promise.reject(reason)方法也会返回一个新的 Promise 实例，该实例的状态为rejected。



​	Iterator 迭代器的概念

​		JavaScript 原有的表示“集合”的数据结构，主要是数组（Array）和对象（Object），ES6 又添加了Map和Set。

​		ES6 规定，默认的 Iterator 接口部署在数据结构的Symbol.iterator属性，或者说，一个数据结构只要具有Symbol.iterator属性，就可以认为是“可遍历的”（iterable）。

​		Symbol.iterator属性本身是一个函数，就是当前数据结构默认的遍历器生成函数。执行这个函数，就会返回一个遍历器。对于原生部署 Iterator 接口的数据结构，不用自己写遍历器生成函数，for...of循环会自动遍历它们。除此之外，其他数据结构（主要是对象）的 Iterator 接口，都需要自己在Symbol.iterator属性上面部署，这样才会被for...of循环遍历。

​	for...of 循环

​		数组结构、Map和Set结构、计算生成的数据结构（比如entries()、keys()、values()等方法返回的对象）和 类似数组的对象 以及 对象



Generator 函数的语法

​		执行 Generator 函数会返回一个遍历器对象，也就是说，Generator 函数除了状态机，还是一个遍历器对象生成函数。返回的遍历器对象，可以依次遍历 Generator 函数内部的每一个状态。

​		形式上，Generator 函数是一个普通函数，但是有两个特征：

​			一是，function关键字与函数名之间有一个星号；

​			二是，函数体内部使用yield表达式，定义不同的内部状态（yield在英语里的意思就是“产出”）。

​		Generator 函数的调用方法与普通函数一样，也是在函数名后面加上一对圆括号。不同的是，调用 Generator 函数后，该函数并不执行，返回的也不是函数运行结果，而是一个指向内部状态的指针对象，也就是上一章介绍的遍历器对象（Iterator Object）。

​		调用Generator函数之后，该函数并不执行，返回的也并不是函数运行结果，而是一个指向内部状态的指针对象，接下来必须调用遍历器对象的`next`方法，使得指针移向下一个状态。也就是说，每次调用`next`方法，内部指针就从函数头部或上一次停下来的地方开始执行，直到遇到下一个`yield`表达式（或`return`语句）为止。换言之，Generator 函数是分段执行的，`yield`表达式是暂停执行的标记，而`next`方法可以恢复执行



yield 表达式

​		由于 Generator 函数返回的遍历器对象，只有调用`next`方法才会遍历下一个内部状态，所以其实提供了一种可以暂停执行的函数。`yield`表达式就是暂停标志。

​		遍历器对象的next方法的运行逻辑如下。

​		（1）遇到yield表达式，就暂停执行后面的操作，并将紧跟在yield后面的那个表达式的值，作为返回的对象的value属性值。

​		（2）下一次调用next方法时，再继续往下执行，直到遇到下一个yield表达式。

​		（3）如果没有再遇到新的yield表达式，就一直运行到函数结束，直到return语句为止，并将return语句后面的表达式的值，作为返回的对象的value属性值。

​		（4）如果该函数没有return语句，则返回的对象的value属性值为undefined。

需要注意的是，yield表达式后面的表达式，只有当调用next方法、内部指针指向该语句时才会执行，因此等于为 JavaScript 提供了手动的“惰性求值”（Lazy Evaluation）的语法功能。

​		yield表达式和return语句有相似之处，也有区别，相似之处在于都可以返回

​	gennerator函数是实现状态机的最佳结构，因为generator函数本身就包含一个状态信息即是目前是否处于暂停态

​	generator 和 协程(coroutine) 

​		传统的“子例程”（subroutine）采用堆栈式“后进先出”的执行方式，只有当调用的子函数完全执行完毕，才会结束执行父函数。协程与其不同，多个线程（单线程情况下，即多个函数）可以并行执行，但是只有一个线程（或函数）处于正在运行的状态，其他线程（或函数）都处于暂停态（suspended），线程（或函数）之间可以交换执行权。也就是说，一个线程（或函数）执行到一半，可以暂停执行，将执行权交给另一个线程（或函数），等到稍后收回执行权的时候，再恢复执行。这种可以并行执行、交换执行权的线程（或函数），就称为协程。

​		不难看出，协程适合用于多任务运行的环境。在这个意义上，它与普通的线程很相似，都有自己的执行上下文、可以分享全局变量。它们的不同之处在于，同一时间可以有多个线程处于运行状态，但是运行的协程只能有一个，其他协程都处于暂停状态。此外，普通的线程是抢先式的，到底哪个线程优先得到资源，必须由运行环境决定，但是协程是合作式的，执行权由协程自己分配。



### Generator 的异步应用

​	在 ES6 之前，异步编程的方法大概有四种：

- 回调函数

- 事件监听

- 发布/订阅

- Promise 对象

  

  所谓异步，简单来说就是一个任务不是连续完成的，可以理解为一个任务被人为地分成两段，先执行一段，转而执行其他任务，等到操作系统返回文件，再接着执行任务的第二段。这种不连续的同步就叫做异步。

#### 回调函数

​	JavaScript 对于异步编程的实现，就是回调函数。所谓回调函数就是把任务的第二段单独写在一个函数里面，等到重新执行这个任务的时候，就直接调用这个函数。回调函数的英文名字是 callback ，直接翻译就是：重新调用。

​	例如，读取文件进行处理的时候，JavaScript 的代码是这样写的：

```Javascript
fs.readFile('/etc/passwd', 'utf-8', function (err, data) {
  if (err) throw err;
  console.log(data);
});
```

​	上面这段代码中， readFile 函数的第三个参数，就是回调函数，也就是任务的第二段。等到操作系统返回了 /etc/passwd 这个文件后，回调函数就会执行。

​	为什么 Node 约定，回调函数的第一个参数，必须是错误对象 err ？

​	原因是执行分成了两段，第一段执行完成后，任务所在的上下文环境就已经结束了。在这以后抛出的错误，原来的上下文环境就已经无法捕捉了，只能当作参数传入第二段。

#### Promise

​	回调函数本身没有问题，问题在于如果出现多个回调函数嵌套，就会造成代码横向拓展的问题，原因在于多个嵌套函数形成了强耦合，只要有一个操作需要修改，它的上层回调函数和下层回调函数可能都要跟着修改，变成了“回调函数”地狱。

​	而 Promise 对象就是为了解决“回调函数地狱”而提出的新的写法，Promise 允许回调函数的嵌套改为链式调用。采用 Promise 连续读取多个文件，Promise 提供 then 方法加载回调函数， catch 方法捕捉执行过程中抛出的错误。Promise 的写法只是对于回调函数的改进，使用了 then 方法之后，异步任务的两段执行看的更加清楚了，除此之外别无新意。

#### Generator 函数

##### 协程的 Generator 函数实现

​	Generator 函数是协程在 ES6 的实现，最大特点就是可以交出函数的执行权（即是暂停执行）。

​	整个 Generator 函数就是一个封装的异步任务，或者说是异步任务的容器。异步操作需要暂停的地方，都用 yield 语句进行注明。Generator 函数的执行方法是通过 next() 方法进行分阶段执行。

```JavaScript
function* gen(x) {
  var y = yield x + 2;
  return y;
}

var g = gen(1);
g.next() // { value: 3, done: false }
g.next() // { value: undefined, done: true }
```

​	上面代码中，调用Generator函数会返回一个内部指针`g`。这是Generator 函数不同于其他函数的一个地方，即是执行它不会返回结果，返回的是指针对象。调用指针`g`的 next 方法会移动内部指针，指向第一个遇到的 yield 语句。

##### 协程的 Generator 函数实现

​	Generator 函数是协程在 ES6 的实现，最大特点就是可以交出函数的执行权。

​	整个 Generator 函数就是一个封装的异步任务，或者说是异步任务的容器。

​	异步操作需要暂停的地方都用 yield 语句注明。next 方法的作用是分阶段执行 Generator 函数。每次调用 next 方法，会返回一个对象，表示当前阶段的信息（value 和 done）。value 属性是 yield 语句后面的表达式的值，表示当前阶段的值；done 属性是一个布尔值，表示 Generator 函数是否执行完毕，即是否还有下一个阶段。

##### Generator 函数的数据交换和错误处理

​	Generator 函数可以暂停执行和恢复执行，这是它能封装异步任务的根本原因，除此之外还有两个特性，使它可以作为异步编程的完整解决方案：函数体内外的数据交换和错误处理机制。

​	next 返回的 value 属性是 Genrator 函数向外输出数据；next 方法还可以接受参数，向 Generator 函数体内输入数据。

```javascript
function* gen(x){
  var y = yield x + 2;
  return y;
}

var g = gen(1);
g.next() // { value: 3, done: false }
g.next(2) // { value: 2, done: true }
```

​	第一个 next 方法的 value 属性，返回表达式 x + 2 的值 3 。第二个 next 方法带有参数 2 ，这个参数传入 Generator函数，作为上一个阶段异步任务的返回结果，被函数体内的变量 y 接受。因此，这一步的 value 属性返回的就是 2。

​	Generator 函数的内部还可以部署错误代码，捕获函数体外抛出的错误。

```javascript
function* gen(x){
  try {
    var y = yield x + 2;
  } catch (e){
    console.log(e);
  }
  return y;
}

var g = gen(1);
g.next();
g.throw('出错了');
// 出错了
```

​	上面代码的最后一行，Generator 函数体外，使用指针对象的 throw 方法抛出的错误，可以被函数体内的 try catch 代码捕获。这意味着，出错的代码与处理错误的代码，实现了时间和空间上的分离，这对于异步编程无疑是很重要的。

#### 异步任务的封装

​	

#### Thunk 函数

​	Thunk 函数是自动执行 Generator 函数的一种方法。

##### 函数的求值策略

​	求值策略有两种方法，分别是：

1. 传值调用，即是在进入函数体之前就计算参数的值，再将这个计算结果传入函数，C语言采用这种策略；
2. 传名调用，即是直接将表达式传入参数体内，只在用到它的时候求值。Haskell语言采用这种策略；

##### Thunk 函数的含义

​	传名调用的实现往往是将参数放在一个临时函数之中，再将这个临时函数传入函数体，这个临时函数就叫做Thunk函数

##### JavaScript 的 Thunk 函数

​	JavaScript 是传值调用，它的 Thunk 函数含义有所不同。在 JavaScript 语言中，Thunk 函数替换的不是表达式，而是多参数函数，将其替换成一个只接受回调函数作为参数的单参数函数。

```javascript
// 正常版本的readFile（多参数版本）
fs.readFile(fileName, callback);

// Thunk版本的readFile（单参数版本）
var Thunk = function (fileName) {
  return function (callback) {
    return fs.readFile(fileName, callback);
  };
};

var readFileThunk = Thunk(fileName);
readFileThunk(callback);
```

​	任何函数，只要参数有回调函数，就能写成 Thunk 函数的形式。

```javascript
// ES5版本
var Thunk = function(fn){
  return function (){
    var args = Array.prototype.slice.call(arguments);
    return function (callback){
      args.push(callback);
      return fn.apply(this, args);
    }
  };
};

// ES6版本
const Thunk = function(fn) {
  return function (...args) {
    return function (callback) {
      return fn.call(this, ...args, callback);
    }
  };
};
```

使用上面的转换器，生成 `fs.readFile`的`Thunk`函数	

```javascript
var readFileThunk = Thunk(fs.readFile);
readFileThunk(fileA)(callback);
```

​	下面是一个完整的例子

```javascript
function f(a, cb) {
  cb(a);
}
const ft = Thunk(f);

ft(1)(console.log) // 1
```

##### Thunkify 模块

​	生产环境的转换器，建议使用 Thunkify 模块。使用方式如下：

```javascript
var thunkify = require('thunkify');
var fs = require('fs');

var read = thunkify(fs.readFile);
read('package.json')(function(err, str){
  // ...
});
```

​	Thunkify 函数只允许回调函数只执行一次。

##### Generator 的函数管理

​	在ES6中有了 Generator 函数，Thunk 函数就可以用于 Generator 函数的自动流程管理。Generator 函数可以自动执行。

```javascript
function* gen() {
  // ...
}

var g = gen();
var res = g.next();

while(!res.done){
  console.log(res.value);
  res = g.next();
}
```

​	上面代码中，Generator 函数 gen 会自动执行完所有步骤。但是这不适合异步操作，如果保证前一步执行完成，才能执行后一步，上面的自动执行就不可行。这时 Thunk 函数就能够派上用场。

```javascript
var fs = require('fs');
var thunkify = require('thunkify');
var readFileThunk = thunkify(fs.readFile);

var gen = function* (){
  var r1 = yield readFileThunk('/etc/fstab');
  console.log(r1.toString());
  var r2 = yield readFileThunk('/etc/shells');
  console.log(r2.toString());
};
```

​	上面代码中，变量`g`就是 Generator 函数的内部指针，表示目前执行到哪一步。next 方法负责将指针移动到下一步，并返回该步的信息（value 属性和 done 属性）

​	仔细查看上面的代码，可以发现 Generator 函数的执行过程，其实是将同一个回调函数，反复传入 next 方法的 value 属性。这使得我们可以用递归来自动完成这个过程。

##### Thunk 函数的自动流程管理

​	Thunk 函数的真正威力，在于可以自动执行 Generator 函数。下面就是一个基于 Thunk 函数的 Generator 执行器。

```javascript
function run(fn) {
  var gen = fn();

  function next(err, data) {
    var result = gen.next(data);
    if (result.done) return;
    result.value(next);
  }

  next();
}

function* g() {
  // ...
}

run(g);
```

​	上面代码的 run 函数，就是一个 Generator 函数的自动执行器。内部的 next 函数就是 Thunk 回调函数。 next 函数先将指针移到 Generator 函数的下一步，然后判断 Generator 函数是否结束，如果没结束，就将 next 函数再传入 Thunk 函数，否则就直接退出。 

### async 函数

​	async 函数就是 Generator 函数的语法糖。

```javascript
const fs = require('fs');

const readFile = function (fileName) {
	return new Promise(function (resolve, reject) {
    fs.readFile(fileName, function(error, data) {
    	if (error) return reject(error);
    	resolve(data);
    });
	});
}
```

​	上面代码的函数 gen 可以写成 async 函数，就是下面这样。

```javascript
const asyncReadFile = async function () {
  const f1 = await readFile('/etc/fstab');
  const f2 = await readFile('/etc/shells');
  console.log(f1.toString());
  console.log(f2.toString());
};
```

​	async 函数对于 Generator 函数的改进，体现在下面四点

1. 内置执行器

   async 函数自带执行器，async 函数的执行，只要一行。

2. 更好的语义

   async 和 await ，比起星号和 yield，语义更加清楚了。

3. 更广的适用性

   yield 命令后面只能是 Thunk 函数或者 Promise 对象，而 async 函数的 await 命令后面，可以是 Promise 对象和原始类型的值（数值、字符串和布尔值，但是会转换成立即resolved 的 Promise 对象）。

4. 返回值是 Promise

   async 函数的返回值是 Promise 对象，这比 Generator 函数的返回值是 Iterator 对象方便多了，你可以用 then 方法指定下一步的操作。

#### 基本用法

​	async 函数返回一个 Promise 对象，可以使用 then 方法添加回调函数。当函数执行的时候，一旦遇到 await 就会先返回，等到异步操作完成，再接着执行函数体内后面的语句。

​	

```javascript
async function getStockPriceByName(name) {
	const symbol = await getStockSymbol(name);
	const stockPrice = await getStockPrice(symbol);
	return stockPrice;
}
```

​	上面代码是一个获取股票报价的函数，函数前面的 async 关键字，表明该函数内部有异步操作。调用该函数时，会立即返回一个 Promise 对象。

​	下面是另一个例子，指定多少毫秒后输出一个值。

```javascript
function timeout(ms) {
  return new Promise((resolve) => {
    setTimeout(resolve, ms);
  });
}

async function asyncPrint(value, ms) {
  await timeout(ms);
  console.log(value);
}

asyncPrint('hello world', 50);
```

​	上面代码指定50毫秒后，输出 hello world。

​	由于 async 函数返回的是 Promise 对象，可以作为 await 命令的参数。所以，上面的例子也可以写成下面的形式。

```javascript
async function timeout(ms) {  await new Promise((resolve) => {    setTimeout(resolve, ms);  });}async function asyncPrint(value, ms) {  await timeout(ms);  console.log(value);}asyncPrint('hello world', 50);
```

​	async 函数有多种形式。

```javascript
// 函数声明async function foo() {}// 函数表达式const foo = async function () {};// 对象方法let obj = { async foo() {}}obj.foo().then(...)
```

#### 语法

​	async 函数的语法规则总体上比较简单，难点是在于错误处理机制。

##### 返回 Promise 对象

​	async 函数返回一个 Promise 对象

​	async 函数内部 return 语句返回的值，会成为 then 方法回调函数的参数。

```javascript
async function f() {	return 'hello world'; }f().then(v => console.log(v));
```

​	上面代码中，函数 f 内部 return 命令返回的值，会被 then 方法回调函数接收到。

​	async 函数内部抛出错误，会导致返回的 Promise 对象变为 reject 状态。抛出的错误对象会被 catch 方法回调函数接收到。

```javascript
async function f() {	throw new Error('出错了')；}f().then(	v => console.log('resolve', v);	e => console.log('reject', e);)
```

##### Promise 对象的状态变化

​	async 函数返回的 Promise 对象，必须等到内部所有 await 命令后面的 Promise 对象执行完，才会发生状态改变，除非遇到 return 语句或着抛出错误。也就是说，只有 async 函数内部的异步操作执行完，才会执行 then 方法指定的回调函数。下面是一个例子

```javascript
async function getTitle(url) {  let response = await fetch(url);  let html = await response.text();  return html.match(/<title>([\s\S]+)<\/title>/i)[1];}getTitle('https://tc39.github.io/ecma262/').then(console.log)
```

​	在上面代码中，只有 await 和 return 语句都执行完了之后，才会执行 then 里面的方法。

##### await 命令

​	正常情况下，await 命令后面是一个 Promise 对象，返回该对象的结果。如果不是 Promise 对象，就直接返回对应的值。另一种情况是 await 命令后面是一个 thenable 对象，那么 await 会将其等同于 Promise 对象。

```javascript
class Sleep {  constructor(timeout) {    this.timeout = timeout;  }  then(resolve, reject) {    const startTime = Date.now();    setTimeout(    	() => resolve(Date.now() - startTime),      this.timeout    );  }}(async () => {  const sleepTime = await new Sleep(1000);  console.log(sleepTime);}) ();
```

​	这个例子还演示了如何实现休眠效果。JavaScript 一直没有休眠的语法，但是借助 await 命令就可以让程序停顿指定的时间。下面给出了一个简化的 sleep 实现。

```javascript
function sleep(interval) {  return new Promise(resolve => {    setTimeout(resolve, interval);  })}// 用法async function one2FiveInAsync() {  for(let i = 1; i <= 5; i++) {    console.log(i);    await sleep(1000);  }}one2FiveInAsync();
```

​	await 命令后面的 Promise 对象如果变为 reject 状态，那么 reject 的参数会被 catch 方法的回调函数接收到。

```JavaScript
async function f() {
  await Promise.reject('出错了');
}

f()
.then(v => console.log(v))
.catch(e => console.log(e))
// 出错了
```

注意，上面代码中，`await`语句前面没有`return`，但是`reject`方法的参数依然传入了`catch`方法的回调函数。这里如果在`await`前面加上`return`，效果是一样的。

任何一个`await`语句后面的 Promise 对象变为`reject`状态，那么整个`async`函数都会中断执行。

```javascript
async function f() {
  await Promise.reject('出错了');
  await Promise.resolve('hello world'); // 不会执行
}
```

上面代码中，第二个`await`语句是不会执行的，因为第一个`await`语句状态变成了`reject`。

有时，我们希望即使前一个异步操作失败，也不要中断后面的异步操作。这时可以将第一个`await`放在`try...catch`结构里面，这样不管这个异步操作是否成功，第二个`await`都会执行。

##### 错误处理

​	如果 await 后面的异步操作出了错，那么等同于 async 函数返回的 Promise 对象被 reject 。

```javascript
async function f() {
  await new Promise(function (resolve, reject) {
    throw new Error('出错了');
  });
}

f()
.then(v => console.log(v))
.catch(e => console.log(e))
// Error：出错了
```

​	上面代码中，async 函数 f 执行后，await 后面的 Promise 对象就会抛出一个错误对象，导致 catch 方法的回调函数被调用，它的参数就是被抛出的错误对象。那么防止出错的方法， 也是把它放在了 try...catch 方法块之中。

​	如果有多个 await 命令，可以统一放在 try...catch 语句当中。

​	下面的例子使用`try...catch`结构，实现多次重复尝试。

```javascript
const superagent = require('superagent');
const NUM_RETRIES = 3;

async function test() {
  let i;
  for (i = 0; i < NUM_RETRIES; ++i) {
    try {
      await superagent.get('http://google.com/this-throws-an-error');
      break;
    } catch(err) {}
  }
  console.log(i); // 3
}

test();
```

上面代码中，如果`await`操作成功，就会使用`break`语句退出循环；如果失败，会被`catch`语句捕捉，然后进入下一轮循环。

##### 使用注意点

1. await 命令放在 try...catch 代码块之中
2. 多个 await 命令后面的异步操作，如果不存在继发关系就让它们同时触发
3. await 命令只用在 async 函数之中，如果用在普通函数中就会报错

##### async 函数的实现原理

​	async 函数的实现原理，即是把 Generator 函数和自动执行器，包装在一个函数里面。

```javascript
async function fn(args) {
  // ...
}

// 等同于

function fn(args) {
  return spawn(function* () {
    // ...
  });
}
```

所有的`async`函数都可以写成上面的第二种形式，其中的`spawn`函数就是自动执行器。

下面给出`spawn`函数的实现，基本就是前文自动执行器的翻版。

```javascript
function spawn(genF) {
  return new Promise(function(resolve, reject) {
    const gen = genF();
    function step(nextF) {
      let next;
      try {
        next = nextF();
      } catch(e) {
        return reject(e);
      }
      if(next.done) {
        return resolve(next.value);
      }
      Promise.resolve(next.value).then(function(v) {
        step(function() { return gen.next(v); });
      }, function(e) {
        step(function() { return gen.throw(e); });
      });
    }
    step(function() { return gen.next(undefined); });
  });
}
```

### Class 的基本语法

#### 	类的由来

​	JavaScript 语言中生成实例对象的传统方法是通过构造函数

​	ES6 提供了更加接近传统语言的写法，引入了Class 这个概念，作为对象的模板。通过 class 关键字，可以定义类。

​	基本上，ES6 的`class`可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的`class`写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。上面的代码用 ES6 的`class`改写，就是下面这样。

```js
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}
```

​	ES6 的类完全可以看作构造函数的另一个写法。

```js
class Point {
  // ...
}

typeof Point // "function"
Point === Point.prototype.constructor // true
```

​	上面代码表明，类的数据类型就是函数，类本身就指向构造函数。

​	使用的时候，也是直接对类使用 new 命令，跟构造函数的用法一样。

```js
class Point {
  constructor() {
    // ...
  }

  toString() {
    // ...
  }

  toValue() {
    // ...
  }
}

// 等同于

Point.prototype = {
  constructor() {},
  toString() {},
  toValue() {},
};
```

上面代码中，`constructor()`、`toString()`、`toValue()`这三个方法，其实都是定义在`Point.prototype`上面。	

##### 属性表达式

​	类的属性名可以用表达式

#### 静态方法

​	类相当于实例的原型，如果一个方法前加上 static 关键字，表示直接通过类来进行调用，就称之为“静态方法”。实例中不可以调用静态方法。

​	如果静态方法中包含 this 关键字，这个 this 指的是类，不是实例。

```js
class Foo {
  static bar() {
    this.baz();
  }
  static baz() {
    console.log('hello');
  }
  baz() {
    console.log('world');
  }
}

Foo.bar() // hello
```

​	上面代码中，静态方法`bar`调用了`this.baz`，这里的`this`指的是`Foo`类，而不是`Foo`的实例，等同于调用`Foo.baz`。另外，从这个例子还可以看出，静态方法可以与非静态方法重名。

​	父类的静态方法，可以被子类继承。

##### 实例属性的新写法

​	实例属性除了定义在 constructor() 方法里面的 this 上，也可以定义在类的顶层。

​	上面代码中，实例属性 this._count 定义在 constructor() 方法里面。另一种写法，这个属性也可以定义在类的顶层，其他都不变。	

```js
class IncreasingCounter {
  _count = 0;
  get value() {
    console.log('Getting the current value!');
    return this._count;
  }
  increment() {
    this._count++;
  }
}
```

##### 静态属性

​	静态属性指的是 Class 本身的属性，即是 Class.propName，而不是定义在实例对象上的属性。

​	ES6 明确规定，Class 内部只有静态方法，没有静态属性。现在有一个题案提供了类的静态属性，写法是在实例属性的前面，加上 static 关键字。

#### 私有方法和私有属性

​	其中一种做法是在命名上加以区别，在方法名字前面加上下划线 `_` 表示这是一个只限于内部使用的私有方法。

​	另一种方法即是所行将私有方法移除类，因为类内部的所有方法都是对外可见的。

### Module 的语法

​	ES6 模块不是对象，而是通过 export 命令显式地指定输出的代码，再通过 import 命令输入。

```js
// ES6模块
import { stat, exists, readFile } from 'fs';
```

​	上面的代码的实质是从 fs 模块加载 3 个方法，其他的方法不加载。这种加载被称之为“编译时加载”或者静态加载，即是 ES6 可以在编译时就完成模块加载。

#### export 命令

​	模块的功能主要由两个命令组成： export 和 import ， export 命令用于规定模块的对外接口，import 命令用于输入其他模块提供的功能。

​	一个模块就是一个独立的文件。该文件内部的所有变量，外部无法获取。如果你希望外部能够读取内部的某个变量，就必须使用 export 关键字输出该变量。

```js
// profile.js
export var firstName = 'Michael';
export var lastName = 'Jackson';
export var year = 1958;
```

​	`export`的写法，除了像上面这样，还有另外一种。

```js
// profile.js
var firstName = 'Michael';
var lastName = 'Jackson';
var year = 1958;

export { firstName, lastName, year };
```

​	上面代码在`export`命令后面，使用大括号指定所要输出的一组变量。它与前一种写法（直接放置在`var`语句前）是等价的，但是应该优先考虑使用这种写法。因为这样就可以在脚本尾部，一眼看清楚输出了哪些变量。

​	`export`命令除了输出变量，还可以输出函数或类（class）。

```js
export function multiply(x, y) {
  return x * y;
};
```

​	上面代码对外输出一个函数`multiply`。

通常情况下，`export`输出的变量就是本来的名字，但是可以使用`as`关键字重命名。

```js
function v1() { ... }
function v2() { ... }

export {
  v1 as streamV1,
  v2 as streamV2,
  v2 as streamLatestVersion
};
```

上面代码使用`as`关键字，重命名了函数`v1`和`v2`的对外接口。重命名后，`v2`可以用不同的名字输出两次。

需要特别注意的是，`export`命令规定的是对外的接口，必须与模块内部的变量建立一一对应关系。

```js
// 报错
export 1;

// 报错
var m = 1;
export m;
```

上面两种写法都会报错，因为没有提供对外的接口。第一种写法直接输出 1，第二种写法通过变量`m`，还是直接输出 1。`1`只是一个值，不是接口。正确的写法是下面这样。

```js
// 写法一
export var m = 1;

// 写法二
var m = 1;
export {m};

// 写法三
var n = 1;
export {n as m};
```

上面三种写法都是正确的，规定了对外的接口`m`。其他脚本可以通过这个接口，取到值`1`。它们的实质是，在接口名与模块内部变量之间，建立了一一对应的关系。

同样的，`function`和`class`的输出，也必须遵守这样的写法。

```js
// 报错
function f() {}
export f;

// 正确
export function f() {};

// 正确
function f() {}
export {f};
```

另外，`export`语句输出的接口，与其对应的值是动态绑定关系，即通过该接口，可以取到模块内部实时的值。

```js
export var foo = 'bar';
setTimeout(() => foo = 'baz', 500);
```

上面代码输出变量`foo`，值为`bar`，500 毫秒之后变成`baz`。

最后，`export`命令可以出现在模块的任何位置，只要处于模块顶层就可以。如果处于块级作用域内，就会报错，下一节的`import`命令也是如此。这是因为处于条件代码块之中，就没法做静态优化了，违背了 ES6 模块的设计初衷。

```js
function foo() {
  export default 'bar' // SyntaxError
}
foo()
```

上面代码中，`export`语句放在函数之中，结果报错。

#### Import 命令

​	使用 export 命令定义了模块的对外接口之后，其他的 JS 文件可以通过 import 命令加载模块。

```js
// main.js
import { firstName, lastName, year } from './profile.js';

function setName(element) {
  element.textContent = firstName + ' ' + lastName;
}
```

​	上面代码的 import 命令，用于加载 profile.js 文件，并从中输入变量。import 命令接受一对大括号，里面指定要从其他模块导入的变量名字。大括号里面的变量名，必须被导入模块（profile.js）对外接口的名称相同。

​	如果想要为输入的变量重新取一个名字，import 命令就要使用 as 关键字，将输入的变量重新命名。

```js
import { lastName as surname } from './profile.js';
```

​	`import`命令输入的变量都是只读的，因为它的本质是输入接口。也就是说，不允许在加载模块的脚本里面，改写接口。输入模块的属性可以成功改写，并且其他模块也可以读到改写后的值。不过，这种写法很难查错，建议凡是输入的变量，都当作完全只读，不要轻易改变它的属性。

​	`import`后面的`from`指定模块文件的位置，可以是相对路径，也可以是绝对路径。如果不带有路径，只是一个模块名，那么必须有配置文件，告诉 JavaScript 引擎该模块的位置。

​	不同的方法或者函数或者对象在两个语句中加载，但是它们对应的是同一个`my_module`模块。也就是说，`import`语句是 Singleton 模式。

#### 模块的整体加载

​	除了指定加载的某个输出值，还可以使用整体加载，即用星号指定一个对象，所有的输出值都加载在这个对象上面。

#### export default 命令

​	该命令是为了为模块指定默认输出。

​	比较一下默认输出和正常输出

```js
// 第一组
export default function crc32() { // 输出
  // ...
}

import crc32 from 'crc32'; // 输入

// 第二组
export function crc32() { // 输出
  // ...
};

import {crc32} from 'crc32'; // 输入
```

​	`export default`命令用于指定模块的默认输出。显然，一个模块只能有一个默认输出，因此`export default`命令只能使用一次。所以，import命令后面才不用加大括号，因为只可能唯一对应`export default`命令。

​	本质上，`export default`就是输出一个叫做`default`的变量或方法，然后系统允许你为它取任意名字。所以，下面的写法是有效的。

```js
// modules.js
function add(x, y) {
  return x * y;
}
export {add as default};
// 等同于
// export default add;

// app.js
import { default as foo } from 'modules';
// 等同于
// import foo from 'modules';
```

​	正是因为`export default`命令其实只是输出一个叫做`default`的变量，所以它后面不能跟变量声明语句。

```js
// 正确
export var a = 1;

// 正确
var a = 1;
export default a;

// 错误
export default var a = 1;
```

​	上面代码中，`export default a`的含义是将变量`a`的值赋给变量`default`。所以，最后一种写法会报错。

#### export 和 import 的复合写法

​	如果在一个模块之中，先输入后输出同一个模块，import 语句可以和 export 语句写在一起。

```js
export { foo, bar } from 'my_module';

// 可以简单理解为
import { foo, bar } from 'my_module';
export { foo, bar };
```

​	上面代码中，`export`和`import`语句可以结合在一起，写成一行。但需要注意的是，写成一行以后，`foo`和`bar`实际上并没有被导入当前模块，只是相当于对外转发了这两个接口，导致当前模块不能直接使用`foo`和`bar`。

模块的接口改名和整体输出，也可以采用这种写法。

```js
// 接口改名
export { foo as myFoo } from 'my_module';

// 整体输出
export * from 'my_module';
```

默认接口的写法如下。

```js
export { default } from 'foo';
```

具名接口改为默认接口的写法如下。

```js
export { es6 as default } from './someModule';

// 等同于
import { es6 } from './someModule';
export default es6;
```

同样地，默认接口也可以改名为具名接口。

```js
export { default as es6 } from './someModule';
```

ES2020 之前，有一种`import`语句，没有对应的复合写法。

```js
import * as someIdentifier from "someModule";
```

[ES2020](https://github.com/tc39/proposal-export-ns-from)补上了这个写法。

```js
export * as ns from "mod";

// 等同于
import * as ns from "mod";
export {ns};
```

#### 跨模块常量

本书介绍`const`命令的时候说过，`const`声明的常量只在当前代码块有效。如果想设置跨模块的常量（即跨多个文件），或者说一个值要被多个模块共享，可以采用下面的写法。

```js
// constants.js 模块
export const A = 1;
export const B = 3;
export const C = 4;

// test1.js 模块
import * as constants from './constants';
console.log(constants.A); // 1
console.log(constants.B); // 3

// test2.js 模块
import {A, B} from './constants';
console.log(A); // 1
console.log(B); // 3
```

如果要使用的常量非常多，可以建一个专门的`constants`目录，将各种常量写在不同的文件里面，保存在该目录下。

```js
// constants/db.js
export const db = {
  url: 'http://my.couchdbserver.local:5984',
  admin_username: 'admin',
  admin_password: 'admin password'
};

// constants/user.js
export const users = ['root', 'admin', 'staff', 'ceo', 'chief', 'moderator'];
```

然后，将这些文件输出的常量，合并在`index.js`里面。

```js
// constants/index.js
export {db} from './db';
export {users} from './users';
```

使用的时候，直接加载`index.js`就可以了。

```js
// script.js
import {db, users} from './constants/index';
```

#### Import()

​	引擎处理`import`语句是在编译时，这时不会去分析或执行`if`语句，所以`import`语句放在`if`代码块之中毫无意义，因此会报句法错误，而不是执行时错误。也就是说，`import`和`export`命令只能在模块的顶层，不能在代码块之中（比如，在`if`代码块之中，或在函数之中）。

​	ES2020 引入 import() 函数，支持动态加载模块。

​	import 函数的参数 specifier 指定所要加载的模块的位置。import命令能够接受什么参数，import() 函数就能够接受什么参数，两者的区别在于后者为动态加载。

​	import() 返回一个 Promise 对象。

```js
const main = document.querySelector('main');

import(`./section-modules/${someVariable}.js`)
  .then(module => {
    module.loadPageInto(main);
  })
  .catch(err => {
    main.textContent = err.message;
  });
```

​	`import()`函数可以用在任何地方，不仅仅是模块，非模块的脚本也可以使用。它是运行时执行，也就是说，什么时候运行到这一句，就会加载指定的模块。另外，`import()`函数与所加载的模块没有静态连接关系，这点也是与`import`语句不相同。`import()`类似于 Node 的`require`方法，区别主要是前者是异步加载，后者是同步加载。

##### 适用场合

1. 按需加载
2. 条件加载
3. 动态的模块路径

### Module 的加载实现

#### ES6 模块和 CommonJS 模块的差异

​	它们有三个重大差异

- CommonJS 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用。
- CommonJS 模块是运行时加载，ES6 模块是编译时输出接口。
- CommonJS 模块的`require()`是同步加载模块，ES6 模块的`import`命令是异步加载，有一个独立的模块依赖的解析阶段。

#### Node.js 的模块加载方法

##### 概述

​	JavaScript 目前有两种模块，一种是 ES6 模块，简称 ESM ；另一种是 CommonJS 模块，简称 CJS。

​	CommonJS 模块是 Node.js 专用的，与 ES6 模块不兼容。语法上，两者最明显的差异就是，CommonJS 模块使用 require() 和 module.exports ，ES6 模块使用 import 和 exports。

##### package.json 的 main 字段

​	package.json 文件有两个字段可以指定模块的入口文件: main 和 exports 。比较简单的模块，可以只使用 main 字段，指定模块加载的入口。		

```js
// ./node_modules/es-module-package/package.json
{
  "type": "module",
  "main": "./src/index.js"
}
```

​	上面代码指定项目的入口脚本为`./src/index.js`，它的格式为 ES6 模块。如果没有`type`字段，`index.js`就会被解释为 CommonJS 模块。

​	然后 import 命令就可以加载这个模块了。 

### Decorator

#### 类的装饰

​	装饰器可以用来装饰整个类。

```js
@testable
class MyTestableClass {
  // ...
}

function testable(target) {
  tTestableClass.isTestable // true
```

​	上面代码中，@testable 就是一个装饰器。它修改了 MyTestableClass 这个类的行为，为它加上了静态属性 isTestable。testable 函数的参数 tartget 就是类 MyTestableClass 本身。

​	基本上，装饰器的行为就是下面这样。

```js
@decorator
class A {}

// 等同于

class A {}
A = decorator(A) || A;
```

​	也即是说，装饰器是一个对类进行处理的函数。装饰器函数的第一个参数，就是所要装饰的目标类。	

```js
function testable(target) {
  // ...
}
```

​	上面代码中，testable 函数的参数 target 就是被装饰的类。

​	如果觉得一个参数不够用，可以在装饰器外面再封装一层函数。

```js
function testable(isTestable) {
  return function(target) {
    target.isTestable = isTestable;
  }
}

@testable(true)
class MyTestableClass {}
MyTestableClass.isTestable // true

@testable(false)
class MyClass {}
MyClass.isTestable // false
```

​	装饰器对于类行为的改变，是在代码编译时发生的，而不是在运行时。这意味着，装饰器能在编译阶段运行代码。也就是说，装饰器本质就是编译时执行的函数。

​	实际开发中，React 与 Redux 库结合使用时，常常需要写成下面这样。

```js
class MyReactComponent extends React.Component {}

export default connect(mapStateToProps, mapDispatchToProps)(MyReactComponent);
```

有了装饰器，就可以改写上面的代码。

```js
@connect(mapStateToProps, mapDispatchToProps)
export default class MyReactComponent extends React.Component {}
```

相对来说，后一种写法看上去更容易理解。

#### 方法的装饰

​	装饰器不仅仅可以装饰类，还可以装饰类的属性。

```js
class Person {
  @readonly
  name() { return `${this.first} ${this.last}` }
}
```

​	装饰器函数`readonly`一共可以接受三个参数。

```js
function readonly(target, name, descriptor){
  // descriptor对象原来的值如下
  // {
  //   value: specifiedFunction,
  //   enumerable: false,
  //   configurable: true,
  //   writable: true
  // };
  descriptor.writable = false;
  return descriptor;
}

readonly(Person.prototype, 'name', descriptor);
// 类似于
Object.defineProperty(Person.prototype, 'name', descriptor);
```

​	装饰器第一个参数是类的原型对象，上例是`Person.prototype`，装饰器的本意是要“装饰”类的实例，但是这个时候实例还没生成，所以只能去装饰原型（这不同于类的装饰，那种情况时`target`参数指的是类本身）；第二个参数是所要装饰的属性名，第三个参数是该属性的描述对象。

​	下面的`@log`装饰器，可以起到输出日志的作用。

```js
class Math {
  @log
  add(a, b) {
    return a + b;
  }
}

function log(target, name, descriptor) {
  var oldValue = descriptor.value;

  descriptor.value = function() {
    console.log(`Calling ${name} with`, arguments);
    return oldValue.apply(this, arguments);
  };

  return descriptor;
}

const math = new Math();

// passed parameters should get logged now
math.add(2, 4);
```

​	如果同一个方法有多个装饰器，会像剥洋葱一样，先从外到内进入，然后由内向外执行。

```js
function dec(id){
  console.log('evaluated', id);
  return (target, property, descriptor) => console.log('executed', id);
}

class Example {
    @dec(1)
    @dec(2)
    method(){}
}
// evaluated 1
// evaluated 2
// executed 2
// executed 1
```

​	上面代码中，外层装饰器`@dec(1)`先进入，但是内层装饰器`@dec(2)`先执行。

​	除了注释，装饰器还能用来类型检查。所以，对于类来说，这项功能相当有用。从长期来看，它将是 JavaScript 代码静态分析的重要工具。

#### 为什么装饰器不能用于函数

​	
