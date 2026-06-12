---
title: "Netbeans 6.0 - Cannot type any character in the editor"
date: 2007-12-08
forum: Programming Talk
---

### Post by kingmanowar on 2007-12-08
Hello,

I have just installed netbeans 6.0, but I cannot type anything in the editor !  I had the same problem with v5.5. I guess it is a JAVA problem but how to fix it ? Thanks a lot

---

### Post by tyoc on 2007-12-08
which java do you have?, java from sun?, you can type things in other places of NB (like the dialog, etc?


My only suggestions, install and select java-sun and perhaps try disabling effects to None.

---

### Post by Elegorod on 2007-12-08
What is the keyboard language when you type the text? English or other? And what is the system language (locale)? I had problems when typed russian text.
Does the cursor move?

---

### Post by kingmanowar on 2007-12-08
Yes I have java (1.6.0.03) from sun. Sometimes it works when I restart netbeans, but after using it for a while, the issue is back. (Simply displaying a dialog box, like Tools->Options then Cancel for example).
My keyboard is set to English. The problem is only with the editor, I can type text in any other box.

---

### Post by vasilis34 on 2008-02-23
Hello

I have the same problem. Did anyone get to a solution ?

---

### Post by xlinuks on 2008-02-24
There's a NetBeans 6.0.1 version, perhaps it works for you. A short video demonstrating this would be fine

---

### Post by pleger on 2008-04-24
I have Netbeans 6.0.1 and 6.1 and i have the same problem. I think the problem is JVM 6.0

Please.... I need a solution.

---

### Post by alesi_27 on 2008-07-16
Same issue here, isn't there a fix for this ?

I have the same issue in netbeans 6.1, on ubuntu 8.04 (wubi installation) and sun java 1.6.0_06.

I notice the issue appear as soon as you type a "dot" in the code editor, causing the code completition popup to appear. When popup for code completition appear, in my case, I cannot type anymore in the code editor, but I can type elsewhere. If I close and restart netbeans everything works again. It also works if I maximize the code editor and minimize it again.

---

### Post by tinny on 2008-07-16
Delete please

---

### Post by tinny on 2008-07-16
Not sure how reliable IO is in a wubi installation???

Anyway one thing I have noticed with a new NetBeans install is that the first time you start to use it it is busy scanning the JDK class lib to build all the auto code completion and tool tips stuff (auto code complete will not work properly until this has finished).

Maybe on a slower machine this can give the impression that NetBeans is not working?

Do you have some sort of process continuously running in the bottom right hand corner of the NetBeans window (saying something like scanning ???.jar)? If so go have a cup of coffee and come back to it later.

---

### Post by alesi_27 on 2008-07-18
Well, regarding IO i think it's quite reliable, at least up to the moment.

Anyhow I investigate a little more on this and it turned out to be an issue

[http://www.netbeans.org/issues/show_bug.cgi?id=119617]("http://www.netbeans.org/issues/show_bug.cgi?id=119617")

It seems that using sun JDK 1.5 (changing jdk in nb6.1/etc/netbeans.conf) instead of sun JDK 6 resolve the problem, even if with jdk5 it is impossible to have native GTK Look And feel like in java6, so now I'm stuck with swing metal look and feel.

The workaround, for now, is to use jdk 5 to run netbeans, and java 6 to compile .java files.

see you

---

### Post by tinny on 2008-07-19
> **alesi_27 said:**
> Well, regarding IO i think it's quite reliable, at least up to the moment.

Anyhow I investigate a little more on this and it turned out to be an issue

[http://www.netbeans.org/issues/show_bug.cgi?id=119617]("http://www.netbeans.org/issues/show_bug.cgi?id=119617")

It seems that using sun JDK 1.5 (changing jdk in nb6.1/etc/netbeans.conf) instead of sun JDK 6 resolve the problem, even if with jdk5 it is impossible to have native GTK Look And feel like in java6, so now I'm stuck with swing metal look and feel.

The workaround, for now, is to use jdk 5 to run netbeans, and java 6 to compile .java files.

see you

:confused:

I have NetBeans 6.1 and Sun JDK 6 working perfect. Im running Ubuntu Hardy.

---

### Post by bjoersa on 2008-09-29
i have the same issue. Ubuntu Hardy. JDK6. Tried Netbeans 6.0 Netbeans 6.1. No luck

---

### Post by tinny on 2008-09-30
> **bjoersa said:**
> i have the same issue. Ubuntu Hardy. JDK6. Tried Netbeans 6.0 Netbeans 6.1. No luck

Have you tried my suggestion from post #10?

[http://ubuntuforums.org/showpost.php?p=5395477&postcount=10](http://ubuntuforums.org/showpost.php?p=5395477&postcount=10)

---

