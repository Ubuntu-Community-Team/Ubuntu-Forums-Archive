---
title: "java programming?"
date: 2008-11-12
forum: Programming Talk
---

### Post by aszxcv on 2008-11-12
i am a windows users but i am trying linux

i need to installed java 6 jdk update 10

and jvm and netbeans ide

how do i go about this on linux

---

### Post by jonofan on 2008-11-12
You should be able to find any java packages you need through Synaptic. (System>Administration>Synaptic Package Manager)

You can download netbeans from [_here_]("http://bits.netbeans.org/download/trunk/nightly/latest/") - That is a 6.5 development version, I always find them much more stable and less buggy on linux. But you can get 6.1 from [_here_]("http://www.netbeans.org/downloads/index.html").

It's very easy to install, just open a terminal and run an sh command on the downloaded file and the GUI installer will open up. Or if you aren't familiar with the terminal, you should be able to right click on the downloaded file and select "run in terminal" (I think).

---

### Post by tinny on 2008-11-12
> **aszxcv said:**
> i am a windows users but i am trying linux

i need to installed java 6 jdk update 10

and jvm and netbeans ide

how do i go about this on linux

Ubuntu Intrepid ships with Java 6 update 10

Install

```

sudo apt-get install sun-java6*

``` 

Netbeans 6.1 is also available in the repositories (Ubuntu Intrepid)

```

sudo apt-get install netbeans

```

---

