---
title: "Changing scope in c++"
date: 2009-06-22
forum: Programming Talk
---

### Post by tjd_maximum on 2009-06-22
Hello,

Sorry if this is a stupid question, but it's something I always just worked around because I never really new the answer. Say I have the following:

[PHP]
/*some code that gets an int i from the user, doesn't matter what it is*/
if(i > 5) //these numbers are just for an example and don't matter at all
{
  //Make some object
}
else
{
  //Make some other object
}
[/PHP]

The problem is that these objects only exist in their respective {brackets}. What if I want them later? Is there any way to keep them around? Thanks for any feedback and I hope the example made sense even though it was abstract.

-Tony

---

### Post by Arppa on 2009-06-23
It's not a stupid question. As far as I know there is no way to change scopes in c++, when you leave the if-statements scope it's contents become inevitably unaccessible. You should change your program structure to work around this problem. If there is no other possibility you could try some pointer hack, but a good programmer should always be able to work around this.

---

### Post by supirman on 2009-06-23
When you use an auto variable, it's placed on the stack.  When a variable is placed on the stack, it only lives until it goes out of scope.  If you want something to remain alive, you create it dynamically on the heap with *new*.  The general idea would be like this:

[PHP]
FirstObject *first;
SecondObject *second;

if(i > 5)
{
  first = new FirstObject();
}
else
{
  second = new SecondObject();
}

...

// when done with objects
delete first;
delete second;
[/PHP]

---

### Post by fr4nko on 2009-06-23
You should just declare the object outside the if-else blocks and just do un assignment inside the 'if' branch. You could do something like that
```
MyObject *obj = NULL;

if (i > 5) {
  obj = new MyObject();
  /* etc. */
} else {
  obj = new MyObject("different init");
  /* etc. */
}

```but in the following code you are responsible of disposing of the object when you've finished or to give the object as returning value, if applicable.

Note that in this case you are just working with pointers. You can work with objects allocated on the stack by doing something like the following:
```
MyObject obj; /* implicit constructor MyObject() is called. */

if (i > 5) {
  MyObject local_obj =  MyObject(i);
  /* some code */
  obj = local_obj;
  /* etc. */
} else {
  MyObject local_obj =  MyObject(i, "more initiliazers");
  /* some code */
  obj = local_obj;
  /* etc. */
 }

```In this latter case 'obj' will be automatically disposed when you're outside of the block where it is declared. The drawback is that more objects are created on the fly and one copy is done with the assignment operator, when we write 'obj = local_obj'.

I hope that helps.

Francesco

---

### Post by Zugzwang on 2009-06-23
Additionally to the posts above, keep in mind that it might be more efficient to use "inlined ifs" when applicable:

```

Shape s = (i==0)?Triangle(x):Circle(y);

```

This of course requires that Triangle and Circle inherit Shape and have assignment operators defined (and Shape must have a virtual destructor in most cases).

---

### Post by hessiess on 2009-06-23
Abstract the if statement into a function which returns a polymorphic object.

---

### Post by monkeyking on 2009-06-23
Depending on the context,
but my approach would be to split the declaration from the assignment
some thing like

[PHP]
object a;
if(i>5){
  
}else{

}
[/PHP]

Or depending on your strictness of your scope requirement


[PHP]
{
  object a;
  if(a>6){

  }else{

  }
}
[/PHP]

---

