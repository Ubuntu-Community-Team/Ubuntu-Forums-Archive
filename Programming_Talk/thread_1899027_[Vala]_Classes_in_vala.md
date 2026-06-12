---
title: "[Vala] Classes in vala"
date: 2011-12-22
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-12-22
Hi-I'm helping translate a project from python to vala (let's not go there, it's a nightmare). Anyway, I've got a bit of a problem. The actual code is a lot more complicated, but I can get the same errors with the following code:

```

//test.vala

//test class for example
public class mytestclass : GLib.Object {
    //constructor, so I understand
    public mytestclass() {
        int testint = 5;
    }
}

void main() {
    //instance of class
    var mytest = new mytestclass();
    //print integer here-problem here!
    stdout.printf(mytest.testint);
}

```

Output:

```
michael@michael-desktop:~$ valac test.vala
test.vala:13.19-13.32: error: The name `testint' does not exist in the context of `mytestclass'
    stdout.printf(mytest.testint);
                  ^^^^^^^^^^^^^^
Compilation failed: 1 error(s), 0 warning(s)
michael@michael-desktop:~$ 

```

I'm a little confused. I can't put things outside the constructor as they are "outside the root namespace" and therefore "not allowed" by valac. 

Can I do anything, or does the code need rewriting?

Thanks!

PS This is what I have, we're working with a "copy and paste from python, compile, fix errors, rewrite where necessary" approach. We're down from 900 errors to 200. :D

---

### Post by Petrolea on 2011-12-22
You should declare the 'testint' outside the constructor and then change it's value with it.

Right now you are trying to access a value in your class, but 'testint' is actually in constructor. You can't access that.

[PHP]
//test.vala

//test class for example
public class mytestclass : GLib.Object {
    //constructor, so I understand
    int testint; // <------------------------- added this
    public mytestclass() {
        testint = 5; // <--------------------- modified this
    }
}

void main() {
    //instance of class
    var mytest = new mytestclass();
    //print integer here-problem here!
    stdout.printf(mytest.testint);
}
[/PHP]

I think it should work now.

---

### Post by MG&amp;TL on 2011-12-23
Thanks, that works brilliantly!

Weird piece of syntax, that.

---

### Post by Petrolea on 2011-12-23
> **MG&TL said:**
> Thanks, that works brilliantly!

Weird piece of syntax, that.

It might be weird if you've never done this before. But it is completely normal.

---

### Post by MG&amp;TL on 2011-12-23
> **Petrolea said:**
> It might be weird if you've never done this before. But it is completely normal.

I realise. :P

Thanks for the hint, I've done a little C (which doesn't really use classes) and a little C++, which has classes, but not in the same way. And python. Which is just python. So yeah, I guess I have never done it before.

Thanks. :)

---

