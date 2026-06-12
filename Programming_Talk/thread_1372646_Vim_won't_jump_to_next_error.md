---
title: "Vim won't jump to next error"
date: 2010-01-04
forum: Programming Talk
---

### Post by kogger on 2010-01-04
For some reason I can't get Vim to jump to the next error in a list. I'm testing this with Java, and to compile I write:

```
:compiler javac
:make HelloWorld.java
```

If I have one error, it works fine. I type :cc, and the cursor jumps to the line the error is on and displays it. But if there's more than one error, then typing :cn displays the next one, but the cursor won't jump to it. Every :cn, :cp, and :cc command causes the cursor to jump to the first error, not the next, previous, or current (despite the fact that they are displayed correctly).

This wouldn't bother me as much if the errors printed bothered to display the line the error is on, since I could just jump to it, but it would be a lot easier if Vim just jumped to the correct error for me.

Is this a bug, or is there a way to fix this?

---

### Post by dwhitney67 on 2010-01-04
Personally, I have never used the features you describe, however I figured I would try something new and gave it a shot with the following Java program, which produced 3 errors.  For each error, the :cc, :cn, and :cp worked as expected.  I followed your steps to specify the compiler and to make the application.
```

public class Error
{
   public static void main(String[] args)
   {
      Foo f = new Foo();   // 2 errors on this line
      System.out.println("Foo = " + f.toString());
      int i = new Foo();   // 1 error on this line
   }
}

```
Btw, I am running the following version of Vim on Ubuntu 9.10:
```

vim --version
VIM - Vi IMproved 7.2 (2008 Aug 9, compiled Sep 21 2009 11:19:54)
Included patches: 1-245

```

---

### Post by kogger on 2010-01-04
Well, I'm glad you tried something new, because apparently it does actually work. Both errors were listed as being on the same line, so I guess javac didn't notice the second error I made.

---

