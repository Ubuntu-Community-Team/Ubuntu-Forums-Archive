---
title: "Using an argument as variable  (PHP)"
date: 2011-06-03
forum: Programming Talk
---

### Post by Orange Kingdom on 2011-06-03
Hi,

Is it possible to use an argument in a function as a variable for the rest of the script?

function test ($a,$b) {

//do something

}
I want to use $a or $b as a variable outside of the function.

---

### Post by Reiger on 2011-06-03
If you mean references that is possible and no you shouldn't do that (explicitly) because that road ends where limbs get sacrificed on the altar of bad code.

Instead look into classes and objects with PHP5: [http://php.net/manual/en/language.oop5.php](http://php.net/manual/en/language.oop5.php)

When you grasp how they work, you will see the answer to your problem right there as well.

---

### Post by Petrolea on 2011-06-04
> **Orange Kingdom said:**
> Hi,

Is it possible to use an argument in a function as a variable for the rest of the script?

function test ($a,$b) {

//do something

}
I want to use $a or $b as a variable outside of the function.

Maybe you mean global variables. They can be accessed everywhere.

---

### Post by simeon87 on 2011-06-04
You could call test, return a value and then use it elsewhere. But using arguments outside a function (not exactly possible) is asking for messy code.

---

### Post by Orange Kingdom on 2011-06-04
Ok, thanks.  I already thought it's not good programming practice.

So i have to look in the OOP, which i did but why do it difficult i thought.  :)

---

### Post by Petrolea on 2011-06-04
> **Orange Kingdom said:**
> Ok, thanks.  I already thought it's not good programming practice.

So i have to look in the OOP, which i did but why do it difficult i thought.  :)

If you want to change value of some variable with function, you can check out SESSION variables. Create one than change its value with functions.

[PHP]
...
$_SESSION['something'] = 1;
...
function plus_one()
{
    $_SESSION['something'] += 1;
}
...
//you can access it from anywhere, even other files
...
plus_one();
echo $_SESSION['something'];
[/PHP]

---

