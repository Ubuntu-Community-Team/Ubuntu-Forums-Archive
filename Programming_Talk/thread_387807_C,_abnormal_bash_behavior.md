---
title: "C, abnormal bash behavior"
date: 2007-03-18
forum: Programming Talk
---

### Post by nfm on 2007-03-18
Hi,

I attached an app that I have written in c, it is a cd database program, it has a makefile inside so you can compile it by typing 'make' and it also accepts 'make clean' option to clean up junk if you would recompile it. My problem is that this little app waits for you to enter some information, then you press enter or any other key. This app runs on Windows perfectly, what happens on Ubuntu is that you can clearly see when you press 'enter' key, bash receives it as you pressed 'enter' two times, but you actually pressed it only once. Quick and easy way to test that is to run this app and press '9' to quit, it will say "Press ENTER to exit the program" and you're are supposed to press enter that time and app will close. This works on Windows, however on Ubuntu when I press enter the app closes by itself and it seems like bash signalled 'enter' key two times.

So what's the big deal about this? For example, when I press '6' to enter new artist info, it skips 'title' information. Because app received 'enter' two times, now my title is an '\n' ASCII character. Best way to understand what I'm saying is to see it for yourself.

I hope somebody can help me, maybe it's a issue with gcc and how it compiles the program, maybe it's my keyboards type rate (but I tried pressing enter quickly with no effect).

Edit: Here are screenshots, notice how in bash 'title' gets skipped.
[IMG]http://img96.imageshack.us/img96/5582/bashpo0.png[/IMG]
[IMG]http://img264.imageshack.us/img264/298/cmdjq2.png[/IMG]

---

### Post by Mr. C. on 2007-03-18
Scanf does not eat the newline - you need to consume it with getc / getchar if you use scanf.  

It is generally a bad idea to use scanf to read your input values directly, as you have no control over user input ( input garbage, and your program goes into an infinite loop reading / printing ).

Instead, use gets(3) with a sufficiently sized buffer.  It will eat the newline for you.  Then, do the conversion and input validate using sscanf or similar.

MrC

---

### Post by nfm on 2007-03-18
Thank you Mr. C. :mrgreen:
anybody with similar issues can look at [http://www.faqs.org/faqs/C-faq/faq/](http://www.faqs.org/faqs/C-faq/faq/) sections 12.17+. From now on, I will try avoid using scanf.

---

