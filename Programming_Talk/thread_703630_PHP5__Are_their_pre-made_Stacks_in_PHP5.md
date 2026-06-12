---
title: "PHP5 : Are their pre-made Stacks in PHP5?"
date: 2008-02-21
forum: Programming Talk
---

### Post by thenetduck on 2008-02-21
Hi
I am writing a program with PHP5 and was wondering if there are pre-built Stacks with PHP5 or do I need to make my own stack class ? 

The Net Duck

---

### Post by LaRoza on 2008-02-21
The arrays in PHP have the stack methods.

[http://www.w3schools.com/php/php_ref_array.asp](http://www.w3schools.com/php/php_ref_array.asp)

You could write a wrapper for them if you wanted...

---

### Post by supirman on 2008-02-21
[PHP]class Stack {
 
	private $itsStack = array();
 
	public function __construct() {
	}
 
	public function push($data) {
		array_push($this->itsStack, $data);
	}
 
	public function pop() {
		return array_pop($this->itsStack);
	}
 
}
 
$s = new Stack();
 
$s->push("Sunil");
$s->push("Bhatia");
 
echo $s->pop();
echo "\n";
echo $s->pop();[/PHP]


Taken from: [http://www.sunilb.com/php/php-tutorials/stack-implementation-in-php5-stack-class](http://www.sunilb.com/php/php-tutorials/stack-implementation-in-php5-stack-class)

---

### Post by thenetduck on 2008-02-21
Why does it use "$this" not understanding the reason for having a $this also, eveything is using the "->" symbol. Is this because it's just a pointer? Little confused on this and am rusty on my programming so please forgive me. 

Thanks for the help

The Net Duck

---

### Post by supirman on 2008-02-22
$this is used in classes, to denote that it's a class member that's being used.  And yes, the -> is used to follow the pointer.  You really needn't concern yourself with the stack class code, just how to use at at the bottom of the previous example.

To learn more of PHP 5 OOP, you can start at [http://us3.php.net/manual/en/language.oop5.basic.php](http://us3.php.net/manual/en/language.oop5.basic.php)

---

