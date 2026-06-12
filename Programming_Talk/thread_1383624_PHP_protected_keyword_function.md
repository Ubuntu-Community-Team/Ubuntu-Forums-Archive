---
title: "PHP protected keyword function"
date: 2010-01-17
forum: Programming Talk
---

### Post by mvalviar on 2010-01-17
According to [this]("http://http://www.php.net/manual/en/language.oop5.visibility.php#86266").

And according to the book "Object Oriented Programming in PHP5" from Packt

> Protected: This is another modifier which has a special meaning in OOP. If any
property or method is declared as protected, you can only access the method from its
subclass.

Why am I not getting errors from this?
```

<?php
class Test {
    protected $test;
}

$t = new Test;
$t->setTest = 3;
```

1. I've accessed the variable outsite of the class. The manual said I could should not access it outside of the class.

2. I've accessed it from a member of the class itself instead of it's subclass which violates whats written on the book.

I'm confused. Could somebody please tell me what a protected variable/method is and when I should use it.

---

### Post by v8YKxgHe on 2010-01-17
You're setting the property "setTest", which is not defined anyway within the class declaration, and so will be created with the visibility of public.

Just to give an example:

[php]
class Foo {
	protected $a = 5;
}

class Bar extends Foo {
	public function getA() {
		return $this->a;
	}

	public function echoA() {
		echo $this->a;
	}
}

$foo = new Foo;
var_dump( $foo->a ); # PHP Fatal Error
$bar = new Bar;
var_dump( $bar->a ); # PHP Fatal Error
var_dump( $bar->getA(), $bar->echoA() ); # Will work just fine.
[/php]

---

### Post by mvalviar on 2010-01-17
I didn't notice that. Thanks. I originally had a public method named setTest.

---

