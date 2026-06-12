---
title: "Libraries are installed, but compiler fails to find them."
date: 2006-04-27
forum: Programming Talk
---

### Post by Laterix on 2006-04-27
Hi,

**SOLVED!** Sorry...

I'm new to develope C/C++ programs in linux. I have written some basic C programs, but now I would like to do something useful. The problem is that I can't get even started, because it doesn't matter what library I try to include it always fails. Below is example with gtkmm (C++ wrapper for GTK).

What am I missing here? Same thing goes with libnotify-dev etc.
The code I'm trying to compile below is the first example code from this page:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html")

```

[late@laterix mobile-notifier]$ g++ -Wall test.cc
test.cc:1:19: error: gtkmm.h: No such file or directory
test.cc: In function &#8216;int main(int, char**)&#8217;:
test.cc:5: error: &#8216;Gtk&#8217; has not been declared
test.cc:5: error: &#8216;Main&#8217; was not declared in this scope
test.cc:5: error: expected `;' before &#8216;kit&#8217;
test.cc:7: error: &#8216;Gtk&#8217; has not been declared
test.cc:7: error: &#8216;Window&#8217; was not declared in this scope
test.cc:7: error: expected `;' before &#8216;window&#8217;
test.cc:9: error: &#8216;Gtk&#8217; has not been declared
test.cc:9: error: &#8216;window&#8217; was not declared in this scope
test.cc:9: error: &#8216;run&#8217; was not declared in this scope
[late@laterix mobile-notifier]$ locate gtkmm.h
/usr/include/gtkmm-2.0/gtkmm.h

```

---

### Post by lnostdal on 2006-04-27
try using pkg-config when compiling stuff: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html#id2511507](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html#id2511507)

*g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`*

edit:
oh, solved .. right :D

---

