---
title: "PHP class question"
date: 2012-05-01
forum: Programming Talk
---

### Post by emiller12345 on 2012-05-01
Trying to figure out how to grab an element from an array variable inside a class, where the array variable is labeled private. Does anyone know what I'm doing wrong?

[PHP]<?php

class GetArray {

    private var $a;

    function __construct(){
        $this->a = array_fill(0, 10, 1.0);
        for($i = 0; $i < 10; $i++){
            $this->a[$i] = $i;
        }
    }

    public function getA(){
        return $this->a;
    }

}

$new_class = new GetArray();

echo $new_class->getA()[4]."\n"; //ERROR HERE

?>[/PHP]

---

### Post by v8YKxgHe on 2012-05-02
Array dereferencing is new since PHP 5.4.0, so unless you're running 5.4.0+ then you'll get a syntax error. To work around it, simply assign the return value to a variable, and then access the array index from that variable.

---

### Post by emiller12345 on 2012-05-03
Ah, thanks.  That works.

---

