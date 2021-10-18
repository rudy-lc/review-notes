# 菜鸡前端复习笔记


## JavaScript

### 变量

- 变量可以用于保存任何类型的数据。每个变量只不过是一个用于保存任意值的命名占位符。有3个关键字可以声明变量：`var`、`const` 和 `let`。

#### 声明提升（Hoist）

- 使用`var`声明变量的时候变量会自动提升到函数作用域的顶部。
- 声明变量不赋值的情况下，变量会保存一个特殊值 `undefined`
```js
function test() { 
 console.log(name); 
 var name = '小王'; 
} 
test(); // undefined
```

#### let 

- `let` 声明的变量不会在作用域中被提升，在 `let` 声明之前的执行瞬间被称为“暂时性死区”（temporal dead zone），在此阶段引用任何后面才声明的变量都会抛出 `ReferenceError`

- `let`  跟  `var`  的作用差不多，但有着非常重要的区别。最明显的区别是，`let` 声明的范围是块作用域，而 `var` 声明的范围是函数作用域。

- `let` 不允许同一个块作用域中出现冗余声明，这样会报错 `SyntaxError`，使用`let`和`var`两个不同关键字声明同一个名字的变量也会出现冗余声明。这两个关键字声明的并不是不同类型的变量，它们只是表示变量在相关作用域如何存在的。

  ```js
  // name 不会被提升
  console.log(name); // ReferenceError：name 没有定义
  let name = '小王';
  ```


#### const

- `const` 的行为与 `let` 基本相同，唯一一个重要的区别是用它声明时必须初始化赋值，并且我们不能更改`const`原始值，否则会报错`TypeError` 但是可以修改对象的引用属性，原因是因为`const`指针指向的地址不可以改变，指向地址的内容是可以改变的。因为`const`只是保证对象的指针不改变，而对象的内容改变不会影响到指针的改变，所以对象的属性内容是可以修改的。

  ```js
  // 原始值为小王
  const name = '小王'
  // 修改原始值为小李报错
  const name = '小李' // SyntaxError
  
  // 声明一个对象初始赋值为一个空对象
  const jack = {}; 
  // 添加cnName属性
  jack.cnName = '小王'
  // 添加age属性
  jack.age = '13'
  console.log(jack) // {cnName:'小王',age:'13'}
  ```

  
