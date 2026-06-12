---
title: "configure eclipse for C programming"
date: 2008-02-03
forum: Programming Talk
---

### Post by fredscripts on 2008-02-03
Hi!!

I've just installed Eclipse (sudo apt-get install eclipse) , and  I'm wondering what packages should I install and if I need to configure something  in order to be able to write compile and run C programs using all the advantages that Eclipse has for java.

Thank you very much!!!

---

### Post by xlinuks on 2008-02-03
In case no one answers your question, you could try NetBeans, it comes prepackaged with different extensions depending on your needs, for your purpose there is also NetBeans with the ability to use C/C++ without configuration (right out of the box), 11MB:
[http://download.netbeans.org/netbeans/6.0/final/](http://download.netbeans.org/netbeans/6.0/final/)

---

### Post by LaRoza on 2008-02-03
I don't know anything about eclipse, but for C you need the "build-essential" package.

If you don't know how to compile and run C programs at all, learn how before having an IDE do it for you. [http://ubuntuprogramming.wikidot.com/C](http://ubuntuprogramming.wikidot.com/C)

---

### Post by fredscripts on 2008-02-03
Thanks for answering!!! I'll take a look on working on C without any IDE and the Netbeans.

But as I'm more or less used to working in eclipse with Java, I'd like some plugin or something that once installed, in eclipse, i could do something like: File->New...(here I could choose Java or C programming) and I have the same features when writing C code that I have when doing it on Java (you know refractoring, control+spacebar,...).

---

### Post by bobrocks on 2008-02-03
Install CDT from the Europa Discovery update site thingy in the Software Updates - Find and install thing.  Damn, that is a great description.

I haven't been using it long enough on my C development to comment on which of the Java features it is missing, but it definetly does not have "all" the cool Java stuff.

---

### Post by Jessehk on 2008-02-03
I believe eclipse-cdt is in the repositories. 
```

sudo aptitude update
sudo aptitude install eclipse-cdt

```

It's a specialized plugin for C and C++ programming in eclipse and it's quite good.

---

### Post by fredscripts on 2008-02-03
Thanks.

I should have the package eclipse already installed and installing eclipse-cdt eclipse will get configured to work with C? or are like 2 different programs? 

Do you think working in C with eclipse is worthy? (I'm trying to get it because I liked the way eclipse helps on java development thinking on a similar level of help in C)

---

### Post by Jessehk on 2008-02-03
Installing eclipse-cdt from the repositories (like I described above) will allow you to create C and C++ projects from within eclipse. It is a plugin to eclipse, so there is only one executable.

CDT has code completion for things like struct members and will also generate makefiles if you'd like. It also lets you define a custom indentation scheme that it will automatically adhere to when you're writing code.

---

### Post by fredscripts on 2008-02-08
Hi again! 

I've been using the gcc compiler so now I know how to compile and run C programs.

Right now I've installed the eclipse-cdt plugin and I'm trying to run the "hello world" C program to test it.

I have two questions:

- When I run eclipse on terminal to use it, some extrange message appears like some stuff is missing:
```

fredgl@fredglab:~$ eclipse &
[4] 7209
fredgl@fredglab:~$ searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found


```

Do you know how I can solve it?


- Trying to compile-run the "hello world" program, I've done: File -> New -> Project -> Standard Make C Project (I've named it "foo"). Then right click on the project (foo) and New -> Source File, and I've coded the classical hello world C program (I've named hello.c).

So right now I'm trying to compile it and then run it, but I haven't realized how because in Java I remember that automatically compiles after saving and then Run->Run as Java Application, but in C seems that is different.

Can you help me on that?


Thank you very much!!!!

---

### Post by Shin_Gouki2501 on 2008-02-08
apperntly u need not a java but C RUN configuration.. use google .. is ur friend..

---

### Post by hod139 on 2008-02-08
> **fredscripts said:**
> 
- When I run eclipse on terminal to use it, some extrange message appears like some stuff is missing:
```

fredgl@fredglab:~$ eclipse &
[4] 7209
fredgl@fredglab:~$ searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found


```Do you know how I can solve it?

This terminal output is not a problem.  If you really want to fix it you can edit "/etc/eclipse/java_home" and move 
"/usr/lib/jvm/java-6-sun" to the top of the file.

I don't know about your second question.

---

### Post by fredscripts on 2008-02-08
Thanks for answering.

What do you mean exactly? I've edited the file /etc/eclipse/java_home and put on the first like "/etc/eclipse/java_home" and the messages still appear.

I've been googling on that but I've only found a tutorial with a C++ project and didn't understand the most because I don't know about what "makefiles" are.

Some newbie introduccion to "code-compile-run" a hello world program in eclipse-cdt?

Thanks again!

---

### Post by Majorix on 2008-02-08
@hod
There is no need to do that, actually I would prefer things the way they are set up on his computer. He has sun-java to work with and not some unofficial java. I don't know why, but I like sun-java even if it is not "free".

---

### Post by hod139 on 2008-02-08
> **fredscripts said:**
> 
What do you mean exactly? I've edited the file /etc/eclipse/java_home and put on the first like "/etc/eclipse/java_home" and the messages still appear.

Sorry, there was a bug in my previous post.  I meant edit the file "/etc/eclipse/java_home" and put 
"/usr/lib/jvm/java-6-sun" at the top of the file.  

This file lists the jvm search order that eclipse uses.

> **Majorix said:**
> @hod
There is no need to do that, actually I would prefer things the way they are set up on his computer. He has sun-java to work with and not some unofficial java. I don't know why, but I like sun-java even if it is not "free".
I think you misunderstood my previous post (there was a bug in it).  I want him to use Sun's java as well.  In fact, I want him to make it the first jvm eclipse finds.

---

### Post by fredscripts on 2008-02-09
Thank you! I've done it and now only appears one "not found" message:
```

fredgl@fredglab:~$ eclipse &
[4] 5588
fredgl@fredglab:~$ searching for compatible vm...
  testing /usr/lib/jvm/java-6-sun...found

```

On the other hand, I give up trying eclipse for C programming, so which IDE do you recommend for C programming with good newbie tutorials?

Thanks!

---

### Post by mimada on 2008-02-09
I recently installed Eclipse and ran into a lot of problems. I finally got everything working by installing the latest version (Europa) from the Eclipse website. The repository version broke on the welcome and help screens for me. If you have already installed the repository version, make sure you uninstall the repository version completely before attempting to install the new version.

Once you get Eclipse running, you can add the CDT through the Help-->Software Upgrades menu option. If you have the repository version of Eclipse, do not install the Europa version of the CDT or you will break Eclipse.

A makefile is a script that automates compiling and linking your code. It's pretty essential for big projects and you should learn how to write them. Eclipse can automatically create a makefile for you but you need to enter the libraries and files you are using into the project properties.

If you are thoroughly put off on Eclipse, you can try Anjuta. An older version is available in the repositories but I haven't been able to get the help feature working.

Good Luck!

---

### Post by prijilps on 2010-01-22
can anyone help me with............ writing n compiling c wit eclipse!!!!:confused:

---

