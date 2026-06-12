---
title: "Java Program SWT+AWT Error"
date: 2012-03-01
forum: Programming Talk
---

### Post by jamescoggan on 2012-03-01
Hi my friends

I ve been stuck on the past 2 days working on this error
Aparently old ubuntu versions and new versions have this error
Usually its related to Eclipse, but in this case im not using eclipse, its just a simple java compiled .jar
Everytime i run the program i get this error bellow
I have searched and search and aparently the AWT generates an error and X11 crashes the app when receiving that error
I tried disabling somehow the AWT error generation, but nothing solved it
I tried java Irc channel on freenode and nothing to be helped
i use ubuntu 11.10 with the latest drivers and nothing...
Please help

Thanks
Bellow the error
```
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
(Details: serial 371 error_code 98request_code 42minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by ofnuts on 2012-03-01
> **jamescoggan said:**
> Hi my friends

I ve been stuck on the past 2 days working on this error
Aparently old ubuntu versions and new versions have this error
Usually its related to Eclipse, but in this case im not using eclipse, its just a simple java compiled .jar
Everytime i run the program i get this error bellow
I have searched and search and aparently the AWT generates an error and X11 crashes the app when receiving that error
I tried disabling somehow the AWT error generation, but nothing solved it
I tried java Irc channel on freenode and nothing to be helped
i use ubuntu 11.10 with the latest drivers and nothing...
Please help

Thanks
Bellow the error
```
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
(Details: serial 371 error_code 98request_code 42minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)
```

Would you have a sufficiently reduced source code that still exhibits the problem? Which Java runtime are you using?

---

### Post by t1497f35 on 2012-03-01
You are supposed to come across errors. No one in his right mind does SWT programming, unless you don't know Swing or you've been living under a rock. SWT is full of glitches because its design is as flawed as that of AWT, that's not a secret to anyone. I keep getting for years visual glitches with azureus/vuze because it uses SWT, thankfully, that's the only SWT based app I use.

---

### Post by HotCupOfJava on 2012-03-02
Some source code would help diagnose this....

Though honestly, if it is using SWT libraries it is probably hopeless.

@t1497f35 - much of Swing inherits from AWT classes......

---

### Post by t1497f35 on 2012-03-02
> **HotCupOfJava said:**
> much of Swing inherits from AWT classes......
It's not really about how much is inherited, but who draws the stuff.
In Swing - the stuff is drawn by Java, in AWT and SWT by the native platform, hence it's hard to fix the stuff you don't control and it's hard to write a lowest common denominator that wouldn't touch problem areas you don't control.

---

