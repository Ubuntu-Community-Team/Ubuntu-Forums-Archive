---
title: "[C/C++] Command Line Downloader"
date: 2008-04-03
forum: Programming Talk
---

### Post by Pyro.699 on 2008-04-03
Hello,

I am in no way new to programming i've been doing it for quite a while and have decided to take the leap into C++ / C, Currently i know Python, Java, PHP, MySQL, Perl (there are others, these are just more relevant). I have an understanding that C++ is somewhat a combination of Java and Python. Sad enough as it is i am stuck on a connection that downloads at a maximum rate of 3kb/s (crappy eh?) and have asked several friends to download some of the files i request, although they are not the brightest people in the world because they are unable to get the correct files even though i send them the URL. So the project i have decided to indulge in is to design a program (in C++ and compile it on linux and windows) that is able to download files from a HTTP or FTP server. I have already found one online, but being a programmer i would like to have the source code so that i can modify it. [[COLOR="DarkSlateGray"]Here is a link to a project that is quite similar to what i want[/COLOR]](http://www.noeld.com/programs.asp?cat=misc#download), but again i would like to customize output and also use it as a way to help me understand the C++ language. I already have figured out how to use g++ to compile my project:

```

g++ -Wall helloWorld.cc -o helloWorld
./helloWorld

```

I would greatly appreciate any help with getting this project started and well on its way. Thanks so much for your time
~Cody Woolaver

Note:
I have created a similar project using windows shell script, and i used it to download all the updates for my system. I did this by generating a download list, and modifying it to fit the other program... so this does have extremely useful applications as it would have taken me days to download the 315 critical updates, where it only took me 1 period at school.

---

### Post by slavik on 2008-04-03
have a look into wget. :)

---

### Post by Pyro.699 on 2008-04-03
> **slavik said:**
> have a look into wget. :)

I forgot to include that i am aware of wget, its just that windows does not have this kind of application, i will be using this at peoples houses who unfortunately are not into linux and other operating systems. Thanks

---

### Post by LaRoza on 2008-04-03
> **Pyro.699 said:**
> I forgot to include that i am aware of wget, its just that windows does not have this kind of application, i will be using this at peoples houses who unfortunately are not into linux and other operating systems. Thanks

[http://pages.interlog.com/~tcharron/wgetwin.html](http://pages.interlog.com/~tcharron/wgetwin.html)

[http://www.httrack.com/](http://www.httrack.com/)

---

### Post by Pyro.699 on 2008-04-03
Thankyou for this link, although when i recieve projects like this i am unsure on how to properly compile them (i am aware that this is not the topic of this thread).

---

### Post by LaRoza on 2008-04-03
> **Pyro.699 said:**
> Thankyou for this link, although when i recieve projects like this i am unsure on how to properly compile them (i am aware that this is not the topic of this thread).

Isn't there a precompiled package?

---

### Post by ghostdog74 on 2008-04-03
> **Pyro.699 said:**
> Thankyou for this link, although when i recieve projects like this i am unsure on how to properly compile them (i am aware that this is not the topic of this thread).

there's a [binary]("http://www.interlog.com/~tcharron/wgetwin-1_5_3_1-binary.zip") of wget

---

### Post by slavik on 2008-04-03
I mean, you can look at the source or even port it to windows, but seems like someone has already done that. :)

---

### Post by Pyro.699 on 2008-04-03
Well yes there is a binary version, but again this was a project to help me learn a new language. Usually when learning something new its useful to pick a project and work from the ground up, if you rely on other sources it becomes confusing, then again that could just be me too. Thanks for all your help guys <3

---

### Post by WW on 2008-04-04
Take a look at libcurl.  The library is in the Ubuntu repositories.  The home page of curl and libcurl is [http://curl.haxx.se](http://curl.haxx.se), but I can't seem to connect to it now.  Google for examples and tutorials, such as [this one](http://curl.rtin.bz/libcurl/c/).

---

### Post by Privacy on 2008-04-04
thx cool

---

