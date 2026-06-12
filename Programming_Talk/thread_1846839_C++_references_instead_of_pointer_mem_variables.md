---
title: "C++ references instead of pointer mem variables"
date: 2011-09-19
forum: Programming Talk
---

### Post by muteXe on 2011-09-19
Hiya,
Probably a really simple question, just not exactly sure how to go about it.

I've written a couple of classes for my boss. contents not really important, but something like this:

```

class CPointerClass
{
   // some variables and data here
};

```

Then in the other class definition i have:
```

class MainClass
{
public:
// stuff

private:
    CPointerClass* m_pPtrClass;
};

```

and in the implementation file I initialise and destroy as normal:

```

MainClass::MainClass() :
m_pPtrClass(NULL)
{
    m_pPtrClass = new CPointerClass;
}

MainClass::~MainClass()
{
    if(m_pPtrClass != NULL)
    {
        delelte m_pPtrClass;
    }
    m_pPtrClass = NULL
}

```

He says this is fine, but wants it implemented with references. Now i know how to use references, how to pass by reference and so forth, but am really not sure exactly how to go about implementing my "CPointerClass" as a reference member variable inside "MainClass".

Does anyone have any thoughts please?
Many thanks in advance,

mute

---

### Post by al1x on 2011-09-19
Wouldn't be better to post this issue to this forum? [http://forums.devshed.com/c-programming-42/](http://forums.devshed.com/c-programming-42/)
I would really like to help you but I study classes and oop just for a few days, so I'am new...

---

### Post by Senesence on 2011-09-19
> **al1x said:**
> Wouldn't be better to post this issue to this forum? [http://forums.devshed.com/c-programming-42/](http://forums.devshed.com/c-programming-42/)

This is a general programming forum, so it's just as good (if not better in certain cases).

**@muteXe**

This should work:

[PHP]
class Main{
    public:
    Main() : ref(*(new CPointerClass)){}

    private:
    CPointerClass& ref;
};
[/PHP]

---

### Post by HarrisonNapper on 2011-09-19
Probably talking about this: [http://www.newty.de/fpt/index.html](http://www.newty.de/fpt/index.html)

---

### Post by karlson on 2011-09-19
> **muteXe said:**
> He says this is fine, but wants it implemented with references.


I am not exactly sure why implementing what appears to be a smart pointer of sorts using a reference.  May be some context would be in order. 

> Now i know how to use references, how to pass by reference and so forth, but am really not sure exactly how to go about implementing my "CPointerClass" as a reference member variable inside "MainClass".

Does anyone have any thoughts please?
Many thanks in advance,

mute

secondly, I don't see any reason to allocate the new CPointerClass here.  If you want it allocated I think that doing:
```

class CPointerClass
{
};

class MainClass
{
private:
    CPointerClass var;
public:
    MainClass() {}
    CPointerClass &get_var() { return var; }
};

```

I am assuming that CPointerClass is a class storing a pointer so if you are allocating something that you later store in variable of class CPointerClass you will simply call:

```

<MainClassVar>.get_var().<manipulate_internals>()

```

Beyond this you might want to provide more context of what you are doing and why your boss wants reference vs. pointers other then just because....

---

### Post by karlson on 2011-09-19
> **HarrisonNapper said:**
> Probably talking about this: [http://www.newty.de/fpt/index.html](http://www.newty.de/fpt/index.html)

Not sure what functors and function pointers have to do with this.

---

### Post by muteXe on 2011-09-20
Thanks for the replies.

@ al1x:  Eh?
@ HarrisonNapper: Nothing to do with function pointers, but thanks.
@ Senesence: cheers, i'll give this kind of method a go,although I'll try it without new'ing up the class.
@ karlson: I dont think context is that important. It just seems to be the way my new place of work operates.  If you can do something with pointers or references they seem to like things implented with references.  I can see why I guess.  The only context-specific information needed probably is that the object within my MainClass just has to live for as long as MainClass lives for.

Thanks again for all the replies,

mute

---

### Post by nvteighen on 2011-09-20
For me, replacing pointers by references is not a very radical change... all you get is nicer dereferencing syntax, because everything else (leaks) can also happen with references... but if your new boss tells you to that... *sigh*... do it...

---

### Post by muteXe on 2011-09-21
Indeed :)
I'm the newboy at the moment, so I won't rock the boat!

---

