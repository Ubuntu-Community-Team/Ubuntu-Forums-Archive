---
title: "PHP parameters issue"
date: 2013-08-13
forum: Programming Talk
---

### Post by jairoh_ on 2013-08-13
i'm basically building a framework to test myself in and i'm starting to freak out. And might as well need a help.

i have a config file that accepts the url and get the value passed ex. "**display/jairoh/5/3**".
now i have the values (jairoh,5 and 3) in an array.
the problem is how can i call the function when the parameters are dinamic?
i mean **controller->display( 'jairoh', 5, 3 );**, it calls the **function display( $username, $id, $anotherval )**, 
does it mean i have to do **controller->display(arr[1], arr[2], arr[3] );**?and add another **arr[4] **if i add a 4th parameter in my function, or 5th or 6th?

i just want it to be dinamic. w/out passing an array of values but arguments. tnx :)

---

### Post by DarkAmbient on 2013-08-13
Why not just design the display-function to take an array?

```
controller->display($arr)
```

or pass by reference.

```
controller->display(&$arr)
```

---

### Post by jairoh_ on 2013-08-14
> **DarkAmbient said:**
> Why not just design the display-function to take an array?

```
controller->display($arr)
```

or pass by reference.

```
controller->display(&$arr)
```

are there no other ways than specifying an array? tnx

---

### Post by DarkAmbient on 2013-08-14
Another option would be
```
func_num_args()
``` returns # of parameters provided to function.

```
func_get_args()
``` returns an array holding all parameters provided to function.

Still, not much difference than supplying the function with an array from start.

Otherwise idk.. I havn't touched PHP in several years.

---

### Post by jairoh_ on 2013-08-14
> **DarkAmbient said:**
> Another option would be
```
func_num_args()
``` returns # of parameters provided to function.

```
func_get_args()
``` returns an array holding all parameters provided to function.

Still, not much difference than supplying the function with an array from start.

Otherwise idk.. I havn't touched PHP in several years.
thankyou sir for the effort trying to help. i end up using RelefectionMethod's getNumberOfParameters [http://php.net/manual/en/class.reflectionmethod.php](http://php.net/manual/en/class.reflectionmethod.php)

---

### Post by DarkAmbient on 2013-08-14
Glad it worked out for you =)

---

