# Hoisting 1

Before executing your code, JavaScript engines do an initial parse.  In this initial parse they scan through your whole file and declare certain variables ahead of time.  This is "hoisting".


```js
let let_variable = "let";

var var_variable = "var";

function named() {}

let let_anonymous = function() {}

var var_anonymous = function() {}

```

[PythonTutor Link](https://goo.gl/6FkoZr)

---

## Step 0

__Predicted Happenings:__  
* __Global Context__  
  * _Primitives_    
    a. var_variable: undefined  
    b. let_variable: undefined  
  * _Objects_  
    a. named: Function  
    b. var_anonymous: Funciton  
    c. let_anonymous: Function  
* __Other Contexts__  
  * no other contexts  
* __Behaviors:__
  * variables defined and hoisted, functions defined

__Actual Happenings:__  
* __Global Context__  
  * _Primitives_    
    a. var_variable: undefined  
    b. var_anonymous: undefined  
  * _Objects_    
    a. named: Function  
* __Other Contexts__  
  * no other contexts  
* __Behaviors:__
  * variables defined and hoisted, only the named function was created

Turns out variables declared with "let" are not hoisted.

Named functions are hoisted. But if you put an anonymous function behind a variable JS doesn't care about the function, only the variable (at least for the initial parse).  This is why "var_anonymous" is in primitives, at the initial parse it is set to undefined which is a primitive.  Eventually it'll move to "Objects", but not yet.

---

## Step 1

__Predicted Happenings:__  
* __Global Context__  
  * _Primitives_    
    a. var_variable: undefined  
    b. var_anonymous: undefined  
    c. let_variable: "let"  
  * _Objects_    
    a. named: Function  
* __Behaviors:__
  * the let variable is created, since they aren't hoisted but are made just in time

Got this one right.

---

## Step 2

__Predicted Happenings:__  
* __Global Context__  
  * _Primitives_    
    a. var_variable: "var"  
    b. var_anonymous: undefined  
    c. let_variable: "let"  
  * _Objects_    
    a. named: Function  
* __Behaviors:__
  * "var_variable" is assigned a value

Got this one right.

---

## Step 3

__Predicted Happenings:__  
* __Global Context__  
  * _Primitives_    
    a. var_variable: "var"  
    b. var_anonymous: undefined  
    c. let_variable: "let"  
    d. let_anonymous: undefined  
  * _Objects_   
    a. named: Function 
* __Behaviors:__
  * "let_anonymous" will be created but not defined

__Actual Happenings:__  
* __Global Context__  
  * _Primitives_    
    a. var_variable: "var"  
    b. var_anonymous: undefined  
    c. let_variable: "let"  
  * _Objects_    
    a. named: Function  
    b. let_anonymous: Function  
* __Behaviors:__
  * "let_anonymous" was created and defined


Turns out "let" variables are constructed __and__ given values in the same step.  In other words: "let" variables are not created until they are defined in the file.

___

## Step 4

__Predicted Happenings:__  
* __Global Context__  
  * _Primitives_    
    a. var_variable: "var"  
    c. let_variable: "let"  
  * _Objects_    
    a. named: Function  
    b. let_anonymous: Function  
    c. var_anonymous: Function  
* __Behaviors:__
  * "var_anonymous" will be created and defined

Got this one right.


___
___
### <a href="http://elewa.education/blog" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/34921062-506450ae-f97d-11e7-875f-6feeb26ad72d.png" width="100" height="40"/></a>











