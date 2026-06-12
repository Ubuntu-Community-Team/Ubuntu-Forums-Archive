---
title: "quiz!! what is wrond with the code"
date: 2005-09-22
forum: Programming Talk
---

### Post by seiflotfy on 2005-09-22
class Number
{
  Number (int n)
  {
  ...
  }
 
  Number (const Number& n)
  {
  ...
  }
 
  Number& operator = (const Number& n)
  {
  ...
  }
};
 
Number n1 (123);
 
Number n2 (n1);
 
Number n3 = Number (456);

---

### Post by thumper on 2005-09-22
[QUOTE=seiflotfy]class Number
{
  Number (int n)
  {
  ...
  }
 
  Number (const Number& n)
  {
  ...
  }
 
  Number& operator = (const Number& n)
  {
  ...
  }
};
 
Number n1 (123);
 
Number n2 (n1);
 
Number n3 = Number (456);[/QUOTE]
 The default visibility of a class is private, so none of your constructors are visible.

---

### Post by LordHunter317 on 2005-09-22
Also, why are you declaring a copy constructor and assignment operator?  Unless you're planning on doing deep copies, there is no need.  Also, if you're creating a constructor that takes an argument, make sure to use initialization lists to initialize your data.

---

### Post by thumper on 2005-09-22
[QUOTE=LordHunter317]Also, why are you declaring a copy constructor and assignment operator?  Unless you're planning on doing deep copies, there is no need.  Also, if you're creating a constructor that takes an argument, make sure to use initialization lists to initialize your data.[/QUOTE]
We could also point out that there is nothing in your methods and no main  :p

To provide reasoning for the copy stuff that **LordHunter317** mentioned, the default is to do a memberwise copy of the member variables, so as long as there are defined copy constructors that have the semantics that you mean, then you don't need to explicitly generate them as the compiler generated ones are normally sufficient.  The deep copy mentioned is where you have a pointer, and you want to make a copy of the value being pointed to, not of the pointer itself.

Agree about initializer lists, definately best practice to use them (and necessary at times).

---

### Post by LordHunter317 on 2005-09-22
[QUOTE=thumper]We could also point out that there is nothing in your methods[/quote]Actually, I was going to post that it would be nice to post the entire class definition, then thought better of it for some reason and deleted it.

> and no main  :pNot needed :p

---

### Post by ReiKn on 2005-09-23
[QUOTE=LordHunter317]Also, why are you declaring a copy constructor and assignment operator?  Unless you're planning on doing deep copies, there is no need.  Also, if you're creating a constructor that takes an argument, make sure to use initialization lists to initialize your data.[/QUOTE]

One might also just want to prohibit copying and assignment for the class by declaring those operators private. But that clearly isn't the case here because operator = is used in the code...

---

### Post by thumper on 2005-09-23
[QUOTE=ReiKn]One might also just want to prohibit copying and assignment for the class by declaring those operators private. But that clearly isn't the case here because operator = is used in the code...[/QUOTE]
BTW if you are interested in doing this look at boost::noncopyable

---

