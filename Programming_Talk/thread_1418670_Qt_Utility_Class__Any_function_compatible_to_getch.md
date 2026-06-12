---
title: "Qt Utility Class : Any function compatible to getch() or getche()"
date: 2010-02-28
forum: Programming Talk
---

### Post by madmax.santana on 2010-02-28
I was working with Qt utility classes and I came to a position where I need a function in Qt libraries which does the same thing as getch() or getche().

To elaborate, I don't care if the character is echoed to screen or not. All I care about is, the user should not have to press return after he has input a value.

Such as in

```
.
.
.
QChar aChar
QTextStream out(stdout)
out<<"Please enter any character"
aChar = theFunction();     // Could have been theFunction(aChar);
.
.
.
```


The point is user sees "Please enter any character" and hits a key on the keyboard. Immediately after he has hit the key, the value of key he has pressed gets stored in the variable without user having to have pressed the return key.

Does any such function exist in Qt libraries? Have searched all the QTextStream and QString section in QtAssistant/Qt Manual, haven't found one yet! Please help here.

Or do I have to write a function of my own for this purpose?

---

### Post by mdurham on 2010-03-01
Have a look at QIODevice. It has a method bool QIODevice::getChar ( char * c )

Reads one character from the device and stores it in c. If c is 0, the character is discarded. Returns true on success; otherwise returns false.

This might be what you need???

---

### Post by madmax.santana on 2010-03-01
But how would I call it?

Tried calling it using

> char a;
QTextStream in(stdin);
in.getChar(a);

But it says that getChar() is not a member of QTextStream. It says this very right. But how else could I call it?

Also tried defining a QIODevice object and calling the function through that... Does't work either...

---

### Post by madmax.santana on 2010-03-04
Bumpooooooooooooooo!!!

No replies???

---

### Post by madmax.santana on 2010-03-04
C'mon guys!!! Nobody knows?

---

