---
title: "How to find out the command line of a program?"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by 171742 on 2014-08-12
Hello,

I would like to set a program up as autostart, namely overdrive. But I need the terminal command line. I only know how to start it from the dashboard, how to find out the line?

Thanks!

---

### Post by whitesmith on 2014-08-12
For Gnome DT under 14.04: Applications->System Tools->Preferences->Startup Applications. A cron job could be setup on the terminal if this doesn't work for you. BTW you should always specify your release and version, preferably so that it reads under your bean count like mine. Knowing something of your configuration helps us work with you.

---

### Post by Habitual on 2014-08-12
terminal > ```
whereis overdrive
```

---

### Post by tgalati4 on 2014-08-12
Many programs are in /usr/bin:

```
which overdrive
```

---

### Post by vasa1 on 2014-08-12
Does "overdrive" need Wine?

---

### Post by whitesmith on 2014-08-12
@Habitual:
@tgalati4:

I think we read the OP's question differently. He states, "I would like to set a program up as autostart..." I interpret that to mean he wants an installed program to run automatically when the OS starts. I don't think he wants to find out where the program lives. But of course his posting is hardly an exemplar of clarity, so perhaps I am wrong.

@vasa1:

If it does, we're all wrong!

---

### Post by vasa1 on 2014-08-12
> **whitesmith said:**
> ...
@vasa1:

If it does, we're all wrong!
I didn't know of a program called "overdrive" and the top few Google hits involved Wine. So I asked. I don't know whether programs run through Wine would be in */usr/bin*. I'm sure OP will clarify unless ...

---

### Post by whitesmith on 2014-08-12
@vasa1: Good call! You were the only one who thought he might be talking about a Windows program. I wasn't even thinking of that. But now I'll stop cluttering up the thread with personal opinion and speculation.

---

### Post by llamabr on 2014-08-12
Overdrive will not run in linux.  It is a drm to manage things like library books, and audible downloads, adobe epub books, and things.  It appears that it may work with wine:

[http://blogs.overdrive.com/devices/2013/04/26/overdrive-media-console-compatibility-for-linux-users/](http://blogs.overdrive.com/devices/2013/04/26/overdrive-media-console-compatibility-for-linux-users/)

But wine is rarely the correct solution.  Try buying products from a company that respects open source software, and if you like that company, call them and tell them that they're neglecting a large constituent of clients.

---

### Post by 171742 on 2014-08-13
Hello,

sorry, I misspelled: its overgrive. Furthermore I have got ubuntu 14.4lts. It does not need wine. I know where the startup window is, but my question is what the command is that has to be typed in the second column of the sartup window to make a program run at startup. Just writing overgrive does not workl. But he solutions do not work as well :

o@o-HP-Compaq-6910p-KL536AV:~$ which overgrive
o@o-HP-Compaq-6910p-KL536AV:~$ what overgrive
No command 'what' found, did you mean:
 Command 'wcat' from package 'sac' (universe)
 Command 'chat' from package 'ppp' (main)
 Command 'jhat' from package 'openjdk-6-jdk' (universe)
 Command 'jhat' from package 'openjdk-7-jdk' (main)
what: command not found
o@o-HP-Compaq-6910p-KL536AV:~$ whereis overgrive
overgrive:
o@o-HP-Compaq-6910p-KL536AV:~$ 



Any other ideas?

---

### Post by coldraven on 2014-08-13
Try experimenting.
Open a terminal (Ctrl+Alt+T) and type overgrive. Does it run?
If so. open Startup Applications and make a new entry "overgrive".

---

### Post by 171742 on 2014-08-13
no, it does not run then.Can only start it via desktop.

---

### Post by steeldriver on 2014-08-13
You can start it from the dash and then use the 'ps' command to see what new process(es) start

```

ps -fu *username*

```

---

### Post by chris272 on 2014-08-13
> **steeldriver said:**
> You can start it from the dash and then use the 'ps' command to see what new process(es) start

```

ps -fu *username*

```

That is what I would try.

---

### Post by whitesmith on 2014-08-13
Alright, these are my final thoughts:

1-According to the application's site ([http://www.thefanclub.co.za/overgrive/installation-instructions-ubuntu](http://www.thefanclub.co.za/overgrive/installation-instructions-ubuntu)) it does not support Ubuntu 12.10 or later, which may be your problem. If such is the case a workaround if provided by the vendor. Uninstall the existing program. (Details are on the product's webpage).
2-Make sure you update the json-c and yajl packages before **reinstalling** Grive and overGrive, And then you should:
3-Download the Debian package, which is Ubuntu-compatible.
4-Double click on the downloaded .deb to install via the Software Center.
5-Once you have it installed, if you want to enable autostart, follow my instructions in the answer immediately following your original post.
6-If it really matters where the SC installed overgrive just do```
which overgrive
```or```
whereis overgrive
```
Please don't attempt a manual install. Let the SC do all the work. That way, the installation can be tracked later. Manual installs are evil (where avoidable) because they work behind the curtain and thus make it impossible to do any kind of installation tracking via dpkg. I hope we were helpful. If so, please do others a favor and use Thread Tools at the top of this page to mark the thread closed.

---

