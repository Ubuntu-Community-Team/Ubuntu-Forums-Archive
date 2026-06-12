---
title: "PHP sharing an array between several objects of diffrent classes"
date: 2012-11-10
forum: Programming Talk
---

### Post by bluedalmatian on 2012-11-10
I want to share a single array between multiple objects (of different classes) in PHP.

Each class has a constructor function which takes a ref to the array as an argument and assigns it to a local member variable so that other methods in the class can access it later, however I think when I assign the argument to the local variable Im ending up with a copy of the array.

I dont want this, I want to store a ref to the array so that if any of the objects add or remove an element all other objects will see those changes. This is my code:

[PHP]
function MemberPaymentDAO(&$themap) //constructor
{
    $this->all_daos=$themap; //store a ref to the shared array
    $this->all_daos['MemberPayment'] = $this; //add an element
}
[/PHP]

In the class def $all_daos is simply decalred like this:
[PHP]
var $all_daos;
[/PHP]

I suspect the def and the 1st line of the constructor need changing but PHP refs confuse me I much prefer C++ pointers - you know where you stand with them:)

---

### Post by pkadeel on 2012-11-10
> **bluedalmatian said:**
> I want to share a single array between multiple objects (of different classes) in PHP.

Each class has a constructor function which takes a ref to the array as an argument and assigns it to a local member variable so that other methods in the class can access it later, however I think when I assign the argument to the local variable Im ending up with a copy of the array.

I dont want this, I want to store a ref to the array so that if any of the objects add or remove an element all other objects will see those changes. This is my code:

[PHP]
function MemberPaymentDAO(&$themap) //constructor
{
    $this->all_daos=$themap; //store a ref to the shared array
    $this->all_daos['MemberPayment'] = $this; //add an element
}
[/PHP]In the class def $all_daos is simply decalred like this:
[PHP]
var $all_daos;
[/PHP]I suspect the def and the 1st line of the constructor need changing but PHP refs confuse me I much prefer C++ pointers - you know where you stand with them:)
You need to assign a reference to your class variable like
[PHP]
    $this->all_daos=&$themap; //stores a ref to the array $themap
[/PHP]

---

### Post by bluedalmatian on 2012-11-11
thank you

---

