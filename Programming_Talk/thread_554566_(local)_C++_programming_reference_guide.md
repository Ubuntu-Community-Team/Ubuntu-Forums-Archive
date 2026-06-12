---
title: "(local) C++ programming reference guide"
date: 2007-09-19
forum: Programming Talk
---

### Post by keenlearner on 2007-09-19
Hello I hope this will not be the third of my first three posts that nobody answers. I used to have MSDN library as my favourite reference guide on C++ programming. I just switch to Ubuntu for few weeks and looking for a good programming (specifically C++) documentation/reference guide which I can refer it locally instead of searching internet. I tried to install MSDN in linux using wine, but I got error asking me to install "Internet Explorer" first, so i successfully installed IE 6 in linux. I tried to install MSDN library again, but still get the same error, I think it can't detect my installation. So is there a way I can install MSDN library in ubuntu ? or is there an alternative to MSDN library for linux ? Thank you.

---

### Post by twistedtwig on 2007-09-19
I have a few links at home (not sure how good they are as just getting info together for when I have time to start to learn C++), but I wlil post them when I get home

---

### Post by keenlearner on 2007-09-19
Thanks finally got you answer. Also note that I prefer offline reference. Hope you get home soon.

---

### Post by bunker on 2007-09-19
My favourite is the reference at [http://www.cplusplus.com/](http://www.cplusplus.com/).  Whenever you need a function just site search with Google.  It is a good source with examples for the standard C and C++ libraries.  For linux/posix-specific stuff, look for the GNU library documentation.  It is also very thorough.

---

### Post by aquavitae on 2007-09-19
I generally find the best documentation is in the source code itself.  If I need something specific I just search through the include files for what I want.  At some stage a also used doxygen to compile them into html -never used it though and I think I deleted it.  For any stuff outside the core libs, I look at the docs for whatever lib I'm using.  All offline.

---

### Post by keenlearner on 2007-09-19
> **bunker said:**
> My favourite is the reference at [http://www.cplusplus.com/](http://www.cplusplus.com/).

I have use to have that as well, but I prefer offline if possible. I can read it while waiting for school bus, or while in travelling.  I just downloaded GNU C, wow 999 pages.

---

### Post by keenlearner on 2007-09-19
I just couldn't find something like MSDN library that's very well documented. When I encounter a function that I never seen before I can just write the function name in the index and most of the time I will get a thorough explanations about the functions. when I enter index for basic_string, first they show the member functions like c_str, insert, length, compare, and the short explanation respectively in tables, then up to you want to lookup the full explation of those functions. I have just downloaded and installed in Windows but can be use in Windows only. Missed it...

---

### Post by artoj on 2007-09-19
There's a package which contains documentation about the standard C++ library.

You can install it with:

```

$ sudo apt-get install libstdc++6-4.1-doc

```

Then you can browse the documentation in:

```

/usr/share/doc/gcc-4.1-base/libstdc++/html_user/index.html

```

From the documentation you can for example click "Class list" -> "basic_string".

---

### Post by ryno519 on 2007-09-19
I have a reference book called "The C++ Standard Library". It comes in handy, but is a pain to lug around everywhere. :)

There's always the GNU C++ Standard Library. That's free and... big.

Edit: I see Artoj already supplied you with a method for receiving the GNU C++ Standard Library references. Although I believe the newest version is 4.2.

---

### Post by samjh on 2007-09-19
The C++ standard library is pretty huge.

My preferred site for C++ and C library references is [www.cppreference.com](www.cppreference.com)

You get get a local archived copy of the site here (tar.gz file):
[http://www.cppreference.com/cppreference-files.tar.gz](http://www.cppreference.com/cppreference-files.tar.gz)

If you want to print all of that out... good luck! :p

---

### Post by gnusci on 2007-09-19
Here a couple of nice references:

[http://www.sourcepole.com/sources/programming/cpp/cppqref.html](http://www.sourcepole.com/sources/programming/cpp/cppqref.html)
[http://www.cppreference.com/](http://www.cppreference.com/)

---

### Post by keenlearner on 2007-09-19
Thanks for alll the reply, I have downloaded libstdc++6-4.1-doc and using it. Everything is quite complete. But I still prefer MSDN library much, if you guys have use MSDN library before. It's so nice, documented like wikipedia. Each class has tables of inherited class, public functions, operators, see also. Each member function will have sections of prototype, parameters, return value, descriptions, include header, see also. MSDN is free to download now. I have lots of book reference online using [www.safaribooksonline.com](www.safaribooksonline.com) provided by my  college. But I just prefer something like MSDN library installed. Thanks.

---

### Post by pmasiar on 2007-09-19
Is info for C++ in sticky not enough? If not, can you add summary from this thread, "to help the next guy (tm)"?

---

### Post by twistedtwig on 2007-09-19
well... I think everyone has said way more than I could.. i just have two links that might be of help.. but anywho looks like you have some stuff to look at :)

[http://ubuntuforums.org/showthread.php?t=113849](http://ubuntuforums.org/showthread.php?t=113849)
[http://ubuntuforums.org/showpost.php?p=1983565&postcount=2](http://ubuntuforums.org/showpost.php?p=1983565&postcount=2)

---

