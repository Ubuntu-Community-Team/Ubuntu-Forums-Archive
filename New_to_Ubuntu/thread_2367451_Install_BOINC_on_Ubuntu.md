---
title: "Install BOINC on Ubuntu?"
date: 2017-07-30
forum: New to Ubuntu
---

### Post by creamyicecream on 2017-07-30
Hey,

I just want to run BOINC (SETI@Home) on Ubuntu. I've downloaded boinc_7.2.42_x86_64-pc-linux-gnu.sh and extracted it with the Terminal. Now it has created a BOINC folder and told me: use /home/q1/Downloads/BOINC/run_manager to start BOINC. The file is basically that script: cd "/home/q1/Downloads/BOINC" && exec ./boincmgr $@

If I run the script with a double click or paste the command directly in the terminal nothing happens. It just closes.

So, how can I run BOINC?

And why the hell isn't it possible to just download and directly run an application with a double click or install the package into your program folder with just a double click like in macOS and Windows? Why is such a good operating system like Ubuntu not able to do such EASY tasks? How can a NORMAL not advanced user use this operating system properly without knowing what a terminal is and Unix commands do? ;)

---

### Post by oldos2er on 2017-07-30
Boinc is in the [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu"),  so you could've installed it from Software Center or with apt, e.g. ```
sudo apt update; sudo apt install boinc
```

> why the hell isn't it possible to just download and directly run an application It certainly is possible, but using the repositories with your favorite package manager front-end is preferred for security and stability reasons, among others.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Scripts are meant to be run in a terminal, and while I think it's possible to force one to run by double-clicking on it, it defeats the purpose.

---

### Post by vasa1 on 2017-07-30
> **creamyicecream said:**
> ...
And why the hell isn't it possible to just download and directly run an application with a double click or install the package into your program folder with just a double click like in macOS and Windows? Why is such a good operating system like Ubuntu not able to do such EASY tasks? How can a NORMAL not advanced user use this operating system properly without knowing what a terminal is and Unix commands do? ;)

As oldos2er pointed out, there's the easy way of installing software and that's by accessing the standard repos. You've done something different :) See [https://boinc.berkeley.edu/dev/forum_thread.php?id=10898](https://boinc.berkeley.edu/dev/forum_thread.php?id=10898) to know you aren't alone.

---

### Post by vocx on 2017-07-30
> **creamyicecream said:**
> Hey,

I just want to run BOINC (SETI@Home) on Ubuntu. I've downloaded boinc_7.2.42_x86_64-pc-linux-gnu.sh and extracted it with the Terminal. Now it has created a BOINC folder and told me: use /home/q1/Downloads/BOINC/run_manager to start BOINC. The file is basically that script: cd "/home/q1/Downloads/BOINC" && exec ./boincmgr $@

If I run the script with a double click or paste the command directly in the terminal nothing happens. It just closes.

So, how can I run BOINC?

It seems you have to open a terminal and just type
```

/home/q1/Downloads/BOINC/run_manager

```
If you don't see a particular message or another output is no indication that the program doesn't run. It may actually be running in the background. I don't know, as I have no experience with this BOINC software.

> 
And why the hell isn't it possible to just download and directly run an application with a double click or install the package into your program folder with just a double click like in macOS and Windows? Why is such a good operating system like Ubuntu not able to do such EASY tasks? How can a NORMAL not advanced user use this operating system properly without knowing what a terminal is and Unix commands do? ;)
You are assuming that because you learned to use computers in a particular way, that is the way it should always been. There is nothing fundamental about double clicking a square in a computer screen to open its contents, it is a user interface paradigm that was designed many years ago, and your brain learned to use it. But you weren't born knowing that, you had to learn it. Think about it, many older people, who did not grow up using computers, have difficulty doing computer stuff. They are certainly not "advanced" users. They probably are less efficient using computers than you are. Are they not "normal" users? Are they "subnormal"? What constitutes normality?

So, when you use a new operating system it is helpful to keep an open mind and actually learn new things about it. Staying fixed in your ways is not going to be helpful for you. If you are using a foreign system (any kind of foreign system), you should admit you are not familiar with it, and start learning more about it. In the grand scheme of things this a similar problem with integration of foreign immigrants. If the immigrant does not want to learn new ways of doing things in another country, he or she will always be at odds with the majority local population.

---

