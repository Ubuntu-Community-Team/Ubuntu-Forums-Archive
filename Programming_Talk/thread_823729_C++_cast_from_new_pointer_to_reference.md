---
title: "C++ cast from new pointer to reference"
date: 2008-06-09
forum: Programming Talk
---

### Post by kung fu buntu on 2008-06-09
I have a function that takes a refence:
```
int fun (vector<string> &list);
```

And in my code I would like to create the object in the heap instead of the stack, that is why I'm trying to use new:

```
my_fun (...)
{
  vector<string> &list = new vector<string>();

  fun (list);
}
```

The compilation error is that I'm trying to convert from pointer to reference.
I want to allocate memory in the heap instead of the stack because it makes a difference with large objects!


err... this is (not) funny: I tought it would compile fine this way:
```
my_fun (...)
{
  vector<string> list;

  fun (&list);
}
```
But it doesn't as well. Saying:
"invalid initialization of non-const reference of type ...& from temporary type ...*"




Thank you.


grr... my C++ is soooooo rusty... 5 years or so have passed :(

---

### Post by Npl on 2008-06-09
This

```
my_fun (...)
{
  vector<string>* list = new vector<string>();

  fun (*list);
}
```

and this
```
my_fun (...)
{
  vector<string> list;

  fun (list);
}
```

should complie fine, you pass reference-arguments to funtions as if they where plain variables, dont take the adress of them (which is what the & on the left side does)

---

### Post by KingTermite on 2008-06-09
I'm trying to understand your problem. The reference takes a normal variable and grabs it by reference itself. That is you don't have to do anything special.

If I'm undestanding correctly, you probably want something like:

```
my_fun (...)
{
  vector<string> list;

  fun (list);
}
```

---

### Post by aks44 on 2008-06-09
> **Npl said:**
> ```
my_fun (...)
{
  vector<string> &list = new vector<string>();

  fun (*list);
}
```

Duh?


Didn't you mean
```
my_fun (...)
{
  vector<string>* list = new vector<string>();

  fun (*list);
}
```

or

```
my_fun (...)
{
  vector<string>& list = *new vector<string>();

  fun (list);
}
```



<insert usual rant about using smart pointers here>

---

### Post by Npl on 2008-06-09
Whoops, copy-and-paste mistake :)

Meant the first one of course

---

### Post by kung fu buntu on 2008-06-10
Thank you all for the explanations.


> **aks44 said:**
> 
```
my_fun (...)
{
  vector<string>& list = *new vector<string>();

  fun (list);
}
```

I have googled and don't see what's problem with smart pointers. This seems to be the best solution to me.
Care to explain?

---

