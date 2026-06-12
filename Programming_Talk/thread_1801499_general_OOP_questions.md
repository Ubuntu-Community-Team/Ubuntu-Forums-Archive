---
title: "general OOP questions"
date: 2011-07-10
forum: Programming Talk
---

### Post by DLGandalf on 2011-07-10
hi all, I'm really confused, I know a fair bit of programming, heck, my major is Computer Science, yet I'm stuck with a fairly fundamental problem, I've never come across this during my past professional and/or educational programming. Here is some pseudo code, which in essence is the same as my problem:

```

class A{
  int port = 1

  public void useField()
  {
    Sysout(port);
  }
}

class B extends A{
  int port = 2

}

```

Now, strangely I expected b.useField() to print 2, but it uses the super's method including it's call to the field. 
I can of course override the method in B, but that would defeat the purpose and reason of this question and.. more code duplication.

Where am I going wrong, I could of course rewrite useField() to useField(var) and override in B with a simple call to super.useField(bVar), but in my case in the problem domain, it makes much more sense to have the data in the field and to have a sub class use the exact same method, invoked on the sub's field.

I hope it's clear, somehow I really got the idea I'm overlooking something incredibly simple as a solution.

---

### Post by dwhitney67 on 2011-07-10
Why is class B redeclaring 'port'?  It should use the variable that is in the base-class.

Make your code something like:
```

class B extends A{

   // constructor
   B() {
      port = 2;
   }
}

```

---

### Post by DLGandalf on 2011-07-10
aah, making the field in A protected makes it work in PHP, java really needs your way using the constructor.

My mistake in essence was indeed making a re-declaration where I meant a definition statement. However changing the field to protected (or public) an redeclaration in B overwrites the value in A in PHP. defining fields outside of methods (or constructors) is prohibited in Java. 

Using the constructor way works among both languages and seems like best practice.

/edit, as I thought, I was thinking way too complicated, curse you PHP for your dirty OOP implementation and thank you dwhitney67

---

### Post by slavik on 2011-07-11
> **DLGandalf said:**
> aah, making the field in A protected makes it work in PHP, java really needs your way using the constructor.

My mistake in essence was indeed making a re-declaration where I meant a definition statement. However changing the field to protected (or public) an redeclaration in B overwrites the value in A in PHP. defining fields outside of methods (or constructors) is prohibited in Java. 

Using the constructor way works among both languages and seems like best practice.

/edit, as I thought, I was thinking way too complicated, curse you PHP for your dirty OOP implementation and thank you dwhitney67
rough flow of OOP objects:

calling new on a class:
object = malloc(sizeof class);
object.object(my params);
return object;

an object going out of scope:
object.~object();
delete(object);

---

