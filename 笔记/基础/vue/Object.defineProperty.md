# Object.defineProperty
定义：Object.defineProperty() 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象,
## 1.参数
#### person
    要定义属性的对象。
#### age   
    一个字符串或 Symbol，指定了要定义或修改的属性键。
#### descriptor
    要定义或修改的属性的描述符。
## 2.get
属性的 getter 函数，当访问该属性时，会调用此函数。执行时不传入任何参数，但是会传入 this 对象（由于继承关系，这里的this并不一定是定义该属性的对象）。该函数的返回值会被用作属性的值

## 3.set
 属性的 setter 函数，当属性值被修改时，会调用此函数。该方法接受一个参数（也就是被赋予的新值），会传入赋值时的 this 对象。默认为 undefined


## 4.添加属性
```
let number = 18;
let person = {
   name:'张三'，
   sax:'男'，
}
Object.defineProperty(person, 'age', {
        value : 18,
        enumerable: true,       //当且仅当该属性在对应对象的属性枚举中出现时，值为 true。默认值为 false。
        writable: true,         //如果与属性相关联的值可以使用赋值运算符更改，则为 true。默认值为 false。
        configurable: true      //该属性的类型不能在数据属性和访问器属性之间更改，不可被删除，其描述符的其他属性也不能被更改,默认值为 false
   get() {
      return number
     },
   set(value) {
      unmber = value
    }
})

```

## 5.数据代理
```
let obj1 = {x:1};
let obj2 = {y:2}
Object.defineProperty(obj2, 'x', {
   get() {
      return obj.x
     },
   set(value) {
      obj.x = value
    }
})
p