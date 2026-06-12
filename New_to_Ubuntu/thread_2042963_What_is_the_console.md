---
title: "What is the console?"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by benijenks on 2012-08-15
I've read (I think in the community documentation - sudo page), about something called the "console", which is a root shell outside of the login. I interpret it as basically a terminal with root privileges that is easy to access.

Can someone explain this to me? Or provide a link?

Googling it really didn't yield anything useful, mostly people talking about different variations of shells. I don't need to access mine, I just want to know how it's done/what it is.

---

### Post by Frogs Hair on 2012-08-15
Console is a reference to a terminal of which there are different types. Some Linux users use console based operating systems, but I prefer a GUI myself. :)[http://en.wikipedia.org/wiki/Linux_console](http://en.wikipedia.org/wiki/Linux_console)

---

### Post by audiomick on 2012-08-15
Here is a Wikipedia article. ;)

[http://en.wikipedia.org/wiki/System_console]("http://en.wikipedia.org/wiki/System_console")

Hope that helps.

---

### Post by benijenks on 2012-08-16
> **audiomick said:**
> Here is a Wikipedia article. ;)

[http://en.wikipedia.org/wiki/System_console](http://en.wikipedia.org/wiki/System_console)

Hope that helps.


:/ 

I wouldn't have asked here if I hadn't already googled and wiki'd it.

Though I found what I was looking for, after reading about non-desktop environment distros, and seeing this

[http://www.linuxmantra.com/2010/04/console-vs-terminal.html](http://www.linuxmantra.com/2010/04/console-vs-terminal.html)


Two questions, if you'd indulge me:

1) Can I access the console with a Desktop Environment  installed?

2) 

" Console users have access to the boot loader, and can gain  administrative privileges in various ways during the boot process.  For  example, by specifying an alternate init(8)  program.  Linux systems are not typically configured to be secure at the  console, and additional steps (for example, setting a root password, a  boot loader password and a BIOS password) are necessary in order to make  them so.  Note that console users usually have physical access to the  machine and so can manipulate it in other ways as well.  "

- [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What can I do to make myself more secure?

---

### Post by audiomick on 2012-08-16
Hallo.
Didn't mean to offend with the Wikipedia link. You'd be amazed how many people ask here before they have done any searching at all by themselves. ;)

Yes, you can access the console when you have a Desktop Environment installed. Installing the GUI doesn't take anything away, it just adds the graphical environment on top of what is otherwise there.

As far as security goes, I think the main thing is to stop other people getting access to the computer. That is not meant as a snide remark, but is what I have gathered from what I have seen on the subject. As the quote suggested, a root password and/ or a BIOS password would help. I don't have either, and am not that worried about it, but then I don't have anything on the computer that would really hurt if someone else got to it, at least not on my laptop. It might get sticky if someone got to the desktop, but that is unlikely to the point of not really bothering about it.

---

### Post by quadproc on 2012-08-16
> **benijenks said:**
> I've read (I think in the community documentation - sudo page), about something called the "console", which is a root shell outside of the login. I interpret it as basically a terminal with root privileges that is easy to access.

There are a few ways to gain root privilege while you are running the usual graphics display software.

It is possible to invoke a shell which is privileged; details omitted here because you should really read up on the shell before doing this.  Once you have read up on it, you will have the knowledge to use this technique.  The privilege is independent of whether you are running graphics.

It is also possible to prefix most commands with either sudo or gksudo to obtain privilege for that operation  This is the method that I have always used; it works well and is relatively safe.  And sudo works in recovery mode, when no graphics is running.

For the ambitious, you can modify the system to add the ability to log in as root.  I do not recommend this because it is work, it is insecure, and it is unnecessary.  IHMO, it is better to take the easier routes.

quadproc

---

### Post by lisati on 2012-08-16
Apologies for the late reply, life beyond the forum distracted me when I first saw this thread.

For more information about "root" and "superuser" privileges, and one of the preferred approaches here to temporarily elevating your access on your Ubuntu box, take a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bab1 on 2012-08-17
> **benijenks said:**
> I've read (I think in the community documentation - sudo page), about something called the "console", which is a root shell outside of the login. I interpret it as basically a terminal with root privileges that is easy to access.

Can someone explain this to me? Or provide a link?

Googling it really didn't yield anything useful, mostly people talking about different variations of shells. I don't need to access mine, I just want to know how it's done/what it is.
Not withstanding the answers regarding "root" and root access, the answer to what constitutes a console has not been addressed.

There are multiple ways to gain a terminal prompt and there are multiple types of shells that can be run in those terminals or in the background.  

On a GUI based install, the terminal is most likely a pseudo terminal, But if you press CNTL+ALT+f2 (0r f3 through f6) you will get the real terminal (CNTL+ALT+F7 will return you to the GUI).  No GUI windows just the terminal.  If that terminal is the machine you are physically in front of, it is considered the console.  If you have ssh'd to another machine then it is a terminal session, but you are not at the console of the machine you are working on.  The console is a terminal of the physical machine you are logged into.  Not the GUI pseudo terminal though.  Now a days its pretty blurry as to the correct terms, but back when there was no GUI it made more sense. 

Shells on the other hand cam be interactive (i.e. login or terminal) or not (spawned by applications).  There are multiple types too.  A few are: sh, bash, csh, tcsh and zsh.

Hope this helps.

---

