---
title: "Build Application for Ubuntu"
date: 2008-11-12
forum: Programming Talk
---

### Post by mugen on 2008-11-12
Hello,

I need to build an application that uses system information, like network status, network card in use.

What is the most appropriate programming environment for Ubuntu? Java and Eclipse? Is there any extra stuff I need to install, what packages should I use, is there a tutorial somewhere for me to start from?

Lots of questions, please help!

---

### Post by mugen on 2008-11-12
All right, I just read the stickies.

Please delete this thread.

---

### Post by mugen on 2008-11-12
Actually it does not answer my question:

What is the best language and best building environment for Ubuntu?

*[SIZE="1"](sorry about my monolog)[/SIZE]*

---

### Post by gnusci on 2008-11-12
You mean something like **GKrellM**

[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

**Conky**

[http://conky.sourceforge.net](http://conky.sourceforge.net)

Just give a look to their projects, you will find good information.

Edit: You can also give a look to **lm_sensors**

[http://www.lm-sensors.org](http://www.lm-sensors.org)

---

### Post by jespdj on 2008-11-12
> **mugen said:**
> Actually it does not answer my question:

What is the best language and best building environment for Ubuntu?

*[SIZE="1"](sorry about my monolog)[/SIZE]*
There is no single best programming language for Ubuntu. Programming languages that are used frequently for Ubuntu programs are Python, C, C++, C# (with Mono), Java and others. We have had countless discussions on the forum here about the question "what is the best language for ....?".

---

### Post by mugen on 2008-11-13
Ok, thanks for the answers.

I guess I will stick with Java and Eclipse.

---

### Post by nvteighen on 2008-11-13
There's no best programming language for any operating system but for some specific task (e.g. you don't code webpages in C++, though you could in theory).

But if you ask for the "preferred" language, then some ideas:
0. GNU/Linux strongly relies on C. The kernel is in C and the GNU system uses it almost in all cases.

1. GNU/Linux systems support a lot of shell scripting languages as "auxiliary" languages. Bash, awk, Bourne-shell, etc. These are the languages preferred to automate system administration tasks.

2. GNOME/GTK+ also mainly relies on C (maybe because it started as part of the GNU project), though it supports other languages like Python, C++, C#. Lately, GNOME has been increasing their C# support through cooperation with the Mono project (a project that aims to port MS .Net technology to GNU/Linux) and apps like F-Spot use it.

3. KDE/Qt, in turn, relies on C++. Though bindings exist for Python and other languages.

4. Ubuntu has a strong bias towards Python for applications (maybe is this partly inherited from Debian?). For example, the Update Manager is written in that language.

5. Java is an issue. You can use it in GNU/Linux, but you'll have to choose between being 95%-Free Software (Sun JDK) or 100%-Free Software but not 100%-perfect (Sun OpenJDK)... GNU Classpath doesn't even count. Setting up Java (either for development or just usage) is a hassle... though the advantages of Java are clear and depending on what your project is maybe it's the way to go.

About environments... usually GNU/Linux programmers tend to use text editors like Emacs, vi, GVim, even Gedit (hey, it's quite good) rather than IDEs... but there's a shift in the trend and people are starting to use them specially for Java. I don't know any, but people here will surely have an informed opinion on this.

---

### Post by directhex on 2008-11-13
> **nvteighen said:**
> There's no best programming language for any operating system but for some specific task (e.g. you don't code webpages in C++, though you could in theory).

But if you ask for the "preferred" language, then some ideas:
0. GNU/Linux strongly relies on C. The kernel is in C and the GNU system uses it almost in all cases.

1. GNU/Linux systems support a lot of shell scripting languages as "auxiliary" languages. Bash, awk, Bourne-shell, etc. These are the languages preferred to automate system administration tasks.

2. GNOME/GTK+ also mainly relies on C (maybe because it started as part of the GNU project), though it supports other languages like Python, C++, C#. Lately, GNOME has been increasing their C# support through cooperation with the Mono project (a project that aims to port MS .Net technology to GNU/Linux) and apps like F-Spot use it.

3. KDE/Qt, in turn, relies on C++. Though bindings exist for Python and other languages.

4. Ubuntu has a strong bias towards Python for applications (maybe is this partly inherited from Debian?). For example, the Update Manager is written in that language.

5. Java is an issue. You can use it in GNU/Linux, but you'll have to choose between being 95%-Free Software (Sun JDK) or 100%-Free Software but not 100%-perfect (Sun OpenJDK)... GNU Classpath doesn't even count. Setting up Java (either for development or just usage) is a hassle... though the advantages of Java are clear and depending on what your project is maybe it's the way to go.

About environments... usually GNU/Linux programmers tend to use text editors like Emacs, vi, GVim, even Gedit (hey, it's quite good) rather than IDEs... but there's a shift in the trend and people are starting to use them specially for Java. I don't know any, but people here will surely have an informed opinion on this.

Pretty good, but Debian's bias is towards Perl, not Python

---

### Post by pmasiar on 2008-11-13
> **nvteighen said:**
> 4. Ubuntu has a strong bias towards Python for applications (maybe is this partly inherited from Debian?).

It's because sabdfl has bias for Python 8-)

---

