---
title: "Something like this would be useful for linux noobs"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by mike941 on 2008-09-14
It would be nice if there was a guide that told you what file controlled what setting. An example of what i'm asking for is if some kind of guide that said file whatever controls shutdown, these are some problems you can run into with it; and so on and so on with every file that controls some major function of a computer. Is there a guide like that already and if there is why isn't it stickied anywhere?

---

### Post by kk0sse54 on 2008-09-14
I doubt such a guide exists for every single file system file but there most certainly can for the most important ones. This is also one of the main reasons why people recommend others to try out distros like Slackware or Arch because there's no gui tools available and everything is done by editing config files thus you learn what's under the hood.

---

### Post by mike941 on 2008-09-19
That's it? TRY SLACKWARE!!!!! come on i can't even get a list out of the legendary ubuntuforums? I'm trying to better understand linux but right now i don't even know where to start. Of coarse my thanks go out to anyone that tries to help but please don't post a link to the ubuntu wiki on the command line or the basic filesystem, i already have an above noob understanding of these.

---

### Post by namegame on 2008-09-19
The best way to learn about these is to manually look through them and maybe edit a few. I learned a lot from my experience with Arch and I feel it's the best way to learn about .conf files, daemons, etc.

---

### Post by PocketDog on 2008-09-19
Not a fashionable viewpoint in this new-fangled age of Facespace and electric lighting but your best bet is to get a book or two from the library.

---

### Post by simtaalo on 2008-09-19
maybe try going through some sites which will give you a guide? theres so many beginners linux sites

---

### Post by cariboo on 2008-09-19
You might want to have a look here:

[http://www.debian.org/doc/manuals/system-administrator/](http://www.debian.org/doc/manuals/system-administrator/)

Ubuntu is based on Debian Unstable so it is relevant

JIm

---

### Post by Liviu-Theodor on 2008-09-19
Try the following links:
[http://www.reallylinux.com/]("http://www.reallylinux.com/")
[http://ubuntuknowledge.org/]("http://ubuntuknowledge.org/")
[http://www.pathname.com/fhs/pub/fhs-2.3.html]("http://www.pathname.com/fhs/pub/fhs-2.3.html")
[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

---

### Post by simtaalo on 2008-09-19
[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

### Post by Greyed on 2008-09-19
> **mike941 said:**
> That's it? TRY SLACKWARE!!!!! come on i can't even get a list out of the legendary ubuntuforums?

Nice sarcasm.  Not to mention you are intentionally leaving out the very first part of his message:

> I doubt such a guide exists for every single file system

That's the plain truth.  Seriously, you want an all encompassing guide on a moving target.  I'm barely comfortable with /proc which has been around forever and now there's /sys to dive into.  If you don't know what a file is and want to know your best resource for the quick overview to the overall depth is at your fingertips, right now.

[http://www.google.com/](http://www.google.com/)

If you don't have a net connection, try hitting up the man pages.  In fact, maybe those should be reverse, man then google.  But as for a guide of "here's what does what in Linux" you're going to find that no such beast exists because each distribution does things differently and each version in each distribution will differ from any other version in that distribution.

Whatever works for you please, don't get snarky with people here because they had the gumption to answer your question in a manner you didn't like because you don't understand what they're telling you.

---

### Post by scorp123 on 2008-09-19
> **mike941 said:**
>  It would be nice if there was a guide that told you what file controlled what setting. Well, most of the config files are in **/etc** ... and most of the time the file controlling a program's setting is named after the program it controls. Kind of straightforward I'd say. Nothing to write a guide about. So most of those config files are named *programname***.conf** (e.g. /etc/modules.conf) or sometimes programname**rc** (e.g. /etc/wgetrc, /etc/vim/vimrc ...), and so on.

Nothing dramatic really.

> **mike941 said:**
>  An example of what i'm asking for is if some kind of guide that said file whatever controls shutdown Well, there is the **apropos** command which will spit out infos about whatever topic you might be interested in. Let's suppose you want to know what the system knows about shutdown ... so let's ask the system: ```
apropos shutdown
``` .. Result you should get:  ```
> apropos shutdown
shutdown (8)         - bring the system down
``` See that number in the brackets? That's the chapter number from the user manual ... so to see details about that topic you'd now type this into the terminal: ```
man 8 shutdown
``` ... And voila, there is your guide in all its gory details. You can navigate the manual with the cursor keys and you can press "q" to quit. The slash "/" key allows you to search for keywords, e.g. if you wanted to search for "reboot" you'd simply type ```
/reboot
``` into the window where the manual is displayed and the manual will auto-highlight all instances of that word in the entire text. It's all very easy :D

Want to know something about e.g. ACPI? Well, let's ask the system: ```
> apropos acpi
acpi (1)             - Shows battery status and other ACPI information
acpi_available (1)   - test whether ACPI subsystem is available
acpi_listen (8)      - ACPI event listener
acpid (8)            - Advanced Configuration and Power Interface event daemon
``` From here onwards e.g. ```
man 8 acpid
``` would then give you the manual of the "acpid" daemon above and explain what it does, what files it depends on, etc.

> **mike941 said:**
>  Is there a guide like that already and if there is why isn't it stickied anywhere?  
It's all already there. :)

---

