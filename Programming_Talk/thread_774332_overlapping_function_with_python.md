---
title: "overlapping function with python"
date: 2008-04-29
forum: Programming Talk
---

### Post by tsic on 2008-04-29
Hello,
Can we make overlapping functions in python???
if yes,how to do it ??
I tryed:

def fct2(self):
...
return rep

def fct1(self):
....
rep=fct2(self)

But it announced that there is no fct2
Thank you

---

### Post by WW on 2008-04-29
I think you want
```

    rep=self.fct2(self)

```
in fct1().


EDIT: Oops, that should be
```

    rep=self.fct2()

```
as Can+~ explains below.

---

### Post by tsic on 2008-04-29
This message appear:
fct2() takes exactly 1 argument (2given)
it blocks my interface QT and then when I choose "NO" in the message box error the interface is no more blocked

---

### Post by Can+~ on 2008-04-29
When calling methods from a class, the self statement is passed implicitly. So what WW said is right, but without the (self).

---

### Post by tsic on 2008-04-29
It's Ok.
But Do you have an idea why my interface is still blocking??
It's an interface for chating between a server and a client with QT4.
thank u for help.

---

### Post by Can+~ on 2008-04-29
How could I know? I have never seen your application, nor it's code.

Notice that GUI's usually lock up when there's a long task going, that pauses the interface main loop.

---

### Post by tsic on 2008-05-13
Greeting,
I program an interface customer with PYTHON2.5 AND QT4.In my interface there is a button to send messages.In the debuginning I put it: " self.ui.button_send.setEnabled (False) " As soon as the customer is connected to the server (from a menu) the button changes : " self.ui.buton_send.setEnabled (True) " This action causes me an interuption of connection. I don't know why???? 

How to fix it?
Thank you for help

---

