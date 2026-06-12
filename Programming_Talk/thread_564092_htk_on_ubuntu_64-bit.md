---
title: "htk on ubuntu 64-bit"
date: 2007-09-30
forum: Programming Talk
---

### Post by uniqueumang on 2007-09-30
Hello
i am not very sure if this topic should be here but i think it is most appropriate place to have my topic.
We are making a speech recognizerusing TCL/TK and C. To assist this project we are allowed to use HTK. However I can't install HTK on 64-bit   Ubuntu as it can't find files such as stubs-32.h .After close instpection I realize that since my ubuntu is 64-bit it can't be installed .

Please tell me if there is a way to install HTK on ubuntu-64bit

Thanks a lot.

---

### Post by j_g on 2007-09-30
You can use 32-bit apps on 64-bit Ubuntu. But you have to make sure that (somewhere in the LIBPATH of your 64-bit OS) you have the 32-bit libraries used by a particular 32-bit app.

Here's an article about doing that with Debian. It should be applicable to Ubuntu as well:

[http://www.debian-administration.org/articles/531](http://www.debian-administration.org/articles/531)

That article also gives links to other, more complicated methods of "reproducing a 32-bit environment on a 64-bit OS".

But of course, if you're writing an app to use some 32-bit library, then your app must also be compiled 32-bit. A 64-bit app can't use a 32-bit library, and a 32-bit app can't use a 64-bit library.

Do you want to make a 64-bit app using a particular library, but you can't find a 64-bit version of that lib? In that case, grab the 32-bit source and try to compile it on your 64-bit system. The 64-bit version of gcc you installed on your system will compile the source as 64-bit. Any "long" or "unsigned long" variables in the code will be automatically promoted (by the compiler) to 64-bit. (ie, It's as if they had been declared as LONGLONG in the source). Any pointers will automatically be compiled to 64-bit as well. "int" or "unsigned int" variables will remain 32-bit, even in the 64-bit compile. Hopefully, the code will compile straight away to a 64-bit version without any issues.

NOTE: You can compile a 32-bit on your 64-bit OS running the 64-bit version of gcc. You just have to specify an extra flag to the 64-bit gcc to tell it to spit out a 32-bit executable. So you should be able to develop a 32-bit app, using a 32-bit library, on your 64-bit system, and test it there too.

---

### Post by uniqueumang on 2007-10-07
link to the article doesn't work at all

---

### Post by matrim33 on 2008-02-13
Hi, I'm hoping that someone will be able to help me with a problem I am having.  I am trying to install HTK on my 64-bit Feisty Fawn Ubuntu, but i am running into a problem.

When I ran the Make scripts (after running ./configure) I received these two errors:

/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.a when searching for -lX11

After doing some research, I found that the reason I was getting these errors was because HTK was attempting to use the 64-bit versions of libX11.so and libX11.a (HTK is a 32-bit program, so this was causing a problem).  I was able to get past the first error by creating a symbolic link in /usr/lib/ linking to the libX11.so located in /usr/lib32/

My problem is this:  it appears that I do not have a 32-bit version of libX11.a - i have run a locate on libX11.a and the only thing that comes up is the 64-bit version - there is no libX11.a in /usr/lib32/.  I have done extensive googling on this problem, but have yet to come up with a solution.

Does anybody have an idea on how i can get past this problem?  Is there a package that I am missing? Is there any way that I can compile a 32-bit version of libX11.a on my own?

Any help would be very much appreciated.  Thanks in advance.

-Matrim

---

### Post by dabraude on 2011-10-20
See this thread
[http://ubuntuforums.org/showthread.php?t=1685706](http://ubuntuforums.org/showthread.php?t=1685706)

---

### Post by sisco311 on 2011-10-20
Necro...

Thread closed.

---

