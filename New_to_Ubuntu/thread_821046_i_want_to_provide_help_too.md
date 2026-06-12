---
title: "i want to provide help too"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by akkad on 2008-06-06
its a shame that now i have a lot of ubuntu beans where most of my posts are for asking help not providing a help :(, so i would like to start learning linux from scratch, but where shall i start from??
where here i have some questions:

- does linux(in general - not ubuntu) covers all ubuntu areas?? and does ubuntu has something that is not available in linux(in general), am interested in ubuntu distro but does learning ubuntu covers learning linux ??

- linux is open source, but is there a link for one official site that i can learn from ??

- shall i know all kind of commands? am asking this bcuz am wondering how this forum users do know all kind of commands that cover many different areas, so are these users normal users or i can call them system admins ??

so plz show me the track that i should take ...

---

### Post by spiderbatdad on 2008-06-06
Hi. You'll learn a lot just hanging around the forum.
This link will lead you to a dictionary of linux commands.
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by jimmy the saint on 2008-06-06
For linux tutorials and lessons, use goolge.  It's probably the best resource available for most computer learning tasks.  As far as commands, type "linux commands cheat sheet" that will pull up a few cheat sheets that come in handy.  As far as helping people, just watch the forums and pitch in where you can.  Often you will find folks with the same problems you had.  You can then share with them what others shared with you.  I am certainly no linux guru, in fact most of my posts are still asking what most poeple consider silly questions, but I can help people sometimes.  Just remember that as new as you are, there is always someone newer.

---

### Post by Dr Small on 2008-06-06
I found that the best method to learn from, is to read threads across the forums and try it yourself. That is how I simply began. And when you advance far enough to where you understand the fundamental basics, then you do as I do... you begin to break things just to see their effect, and to fix it :) It really helps though.

Dr Small

---

### Post by Joeb454 on 2008-06-06
Use Ubuntu (or your Linux distro of choice) - Use it, explore it, and you will learn :)

Don't be afraid of the CLI, it's powerful, but it assumes you know what you're doing, and will only do what you tell it to :) For this you may find [http://www.linuxcommand.org](http://www.linuxcommand.org) useful :)

---

### Post by maddog39 on 2008-06-06
> **akkad said:**
> 
- does linux(in general - not ubuntu) covers all ubuntu areas?? and does ubuntu has something that is not available in linux(in general), am interested in ubuntu distro but does learning ubuntu covers learning linux ??

I really don't know what you mean. Ubuntu IS Linux. It is a flavor of Linux like any other distribution which happens to be focused on the desktop user (for the most part).
> **akkad said:**
> 
- linux is open source, but is there a link for one official site that i can learn from ??

No there is no official site to get general information about linux itself. If you want to know more about the kernel (the core of the system which makes linux, linux) then you can go to kernel.org but generally online sources such as communtiy wikis, wikipedia, howto forge, etc provide plenty of information to learn the system.
> **akkad said:**
> 
- shall i know all kind of commands? am asking this bcuz am wondering how this forum users do know all kind of commands that cover many different areas, so are these users normal users or i can call them system admins ??

No, you do not necissarily need to know the commands. But for power users they tend extremely useful and time saving. However, there is nothing wrong with using the GUI if thtats what you prefer.

---

### Post by Duck2006 on 2008-06-06
> **Dr Small said:**
> I found that the best method to learn from, is to read threads across the forums and try it yourself. That is how I simply began. And when you advance far enough to where you understand the fundamental basics, then you do as I do... you begin to break things just to see their effect, and to fix it :) It really helps though.

Dr Small

Yer that a good way to learn, and a thew good books never go astray.

Any of the OReilly books

Linux Bible

ect.

---

### Post by Monicker on 2008-06-06
Another site to look at


[http://www.tldp.org/](http://www.tldp.org/)


Some of the information is a bit dated, but there is much good information there.

---

### Post by Dr Small on 2008-06-06
> **maddog39 said:**
> 
No, you do not necissarily need to know the commands. But for power users they tend extremely useful and time saving. However, there is nothing wrong with using the GUI if thtats what you prefer.

The GUI is evil! That's why I run IceWM... erm, oh wait. That is GUI! bah. But I tend to use the terminal alot to get my job done. As a matter of fact, I don't even have a GUI text editor... only Vim. :D

---

### Post by Joeb454 on 2008-06-06
GUI's aren't that bad - that said I never thought I'd use a terminal, but I use one every time I'm using my laptop now, I just love the simplicity :D

---

### Post by forger on 2008-06-06
Grab some pop corn :popcorn:

GNU/Linux doesn't cover all ubuntu areas, you'll need to read a lot to catch up... but I believe that almost everything exists in binary packages in Debian as well as Ubuntu and PCLinuxOS.
First you must find answers to these questions: What's GNU? What's Linux? Why do they exist? What do _YOU_ want to accomplish by exploring them? Should be easy enough to start a google search :)

Then, I would recommend to start expanding; use other distributions: Try Debian, see how you're going with the command line in a virtual machine (application virtualbox from [www.virtualbox.org](www.virtualbox.org) woo!)
Afterwards, try archlinux, they have a package manager similar to apt called "pacman" :) Things should be easy enough once you read about the package manager: [http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)
Next would be the almighty Fedora or CentOS (the free alternative to RedHat Enterprise), see how you do with their package manager: yum

After you've played enough with package managers, I suggest starting to browse the linux directories; Have you ever done **ls -l /** or **ls -l /etc/** ? ls -lh $HOME ?
Moreover, you should start playing around with bash scripting to explore the many possibilities of GNU/Linux commands:
[B][http://linux.about.com/od/embedded/l/blnewbie_toc.htm](http://linux.about.com/od/embedded/l/blnewbie_toc.htm)
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)
[http://www.tldp.org](http://www.tldp.org)[/B]

Now that you know a bunch of stuff about gnu/linux, why not expand to BSD as well? They're not Linux, but they're respected widely as a perfect server solution. FreeBSD should be easy to maintain/keep up-to-date (not use, to use it you need to know some more about it) if you know this ABC:
```
A) freebsd-update fetch; freebsd-update install
B) portsnap fetch update
C) pkg_version -v
```

I'm not going to explain anything, I'll leave that to you :)

FreeBSD uses ports, "kind of" like Gentoo 's portage and emerge tool. in FreeBSD the ports are by default in /usr/ports/, separated in categories (subdirectories like lang for programming languages or shells for bash, csh etc.)
For example, if you want to install perl 5.8:
```
 cd /usr/ports/lang/perl5.8/
 make install clean

```
Make fetches necessary files from the internet and compiles, installs and cleans the unnecessary files.
To remove it's also easy:
```
make deinstall clean
```

If you want to start customizing your linux kernel etc, making it a bit quicker for your machine, you could try out Gentoo! They have great wiki and documentation, read on, I won't spoil the fun :P

At the end, if you really want to get hardcore, try linux from scratch:
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Anyway, I wish you good luck, I'm taking the same "journey" as you are, just as an enthousiast :)

---

### Post by sports fan Matt on 2008-06-06
As I type this , I have reached 1,000 posts.  I started in Nov of 07 just reading forums and asking alot of questions and not being afraid, nor being snitty at the help i received.  There are numerous guides and an excellent forum here that can help! Enjoy!

---

