---
title: "php OOP question."
date: 2013-08-02
forum: Programming Talk
---

### Post by jairoh_ on 2013-08-02
Good day everyone! I'm currently learning things up i have a question about extending a class. 

On a file called MyClass.php there are two classes **MyClass **and the **OtherClass** that extends the Myclass and it works fine inheriting the superclass attributes.
```

<?php


class MyClass {
    const CONST_VALUE = 'A constant value';


    public function __construct () {
    }
    
    function index () {
        return 'index';
    }


    function hello () {
        return 'Hello';
    }






}


class OtherClass extends MyClass {    
     
     function __construct() {
         parent:: __construct();
     }
    
    function index () {
        echo 'Other class index';
    }    
}


$OtherClass = new OtherClass();
echo $OtherClass->hello();

``` Output: "Hello"


but when i tried transferring the **OtherClass **into another module that extends the **MyClass**, it throws a server error. I don't wanna put it in the same module.

MyClass.php:
```

class MyClass {
    const CONST_VALUE = 'A constant value';


    public function __construct () {
        //echo 'loaded constructor<br />';
    }
    
    function index () {
        return 'index';
    }


    function hello () {
        return 'Hello';
    }






}

```
OtherClass.php:
```

class OtherClass extends MyClass {    
     
     function __construct() {
         parent:: __construct();
     }
    
    function index () {
        echo 'Other class index';
    }    
}


$OtherClass = new OtherClass();
$OtherClass->hello();

```

any help will be greatly appreciated from a beginner like me. thankyou. :)

---

### Post by lykwydchykyn on 2013-08-05
You need to "require" or "include" MyClass.php in OtherClass.php, so that the contents will be available to it.

See [http://www.php.net/manual/en/function.include.php](http://www.php.net/manual/en/function.include.php)

---

### Post by jairoh_ on 2013-08-06
> **lykwydchykyn said:**
> You need to "require" or "include" MyClass.php in OtherClass.php, so that the contents will be available to it.

See [http://www.php.net/manual/en/function.include.php](http://www.php.net/manual/en/function.include.php)


thankyou sir.

---

