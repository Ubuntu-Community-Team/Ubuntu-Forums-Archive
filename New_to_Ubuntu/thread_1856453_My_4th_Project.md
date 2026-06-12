---
title: "My 4th Project"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by Nyght on 2011-10-08
Installing programs in deb pkgs w/o using synaptic?:


I really didn't want to get into the Gnome (I could of sworn it was spelled Knome back in the day) Terminal and command line this early but it is a very basic and essential aspect of installing programs not native to Lee-nooks. Z/Z

I guess I should give an example. Suppose I wanted to install vlc w/o using synaptic. Granted it has already been installed by a friend who apparently thinks I can learn to do Lee-nooks tasks while I am a kilometer away from my lappy :) or asleep or abducted by extra terrestrials. Z/Z

---

### Post by ajgreeny on 2011-10-08
If you have a .deb package in your home folder you can run ```
sudo dpkg -i *filename*.deb
``` If the .deb is elsewhere you must either give the full path to the .deb, or navigate to that folder first.  Have a long look at ```
man dpkg
``` for all the possible options and what you can do with it.

Synaptic, Ubuntu-software-center aptitude and apt-get are all applications that use dpkg as the program that does the work.

---

### Post by thatguruguy on 2011-10-08
> **Nyght said:**
> I could of sworn it was spelled Knome back in the day
No, it wasn't.  Not ever.

 > **Nyght said:**
> but it is a very basic and essential aspect of installing programs not native to Lee-nooks

If it's a program that isn't native to Linux, there won't be a .deb for it.  Installing .debs by simply double-clicking on them and then allowing the system's package manager to do its thing works just fine, unless there's a particular problem with the package you're trying to install.

<snip>

---

### Post by QLee on 2011-10-08
> **Nyght said:**
> ...
...

I guess I should give an example. Suppose I wanted to install vlc w/o using synaptic. ...

Well, you would open a terminal window and use one of the command line front-ends to the package manager. For example, for the package you mention, vlc. I would enter the command, apt-get update (which updates the packages list), then I would enter, apt-get install vlc and shazammm, things would start to happen if I had an Internet connection. It is possible to read the manual page for commands by entering, man <commandname> in a terminal window, in this example, man apt-get.

Or, you might choose to use aptitude which has both a command line and an ncurses interface. You could use the command line similar to the above and you could read the manual page in a similar fashion too.

If you don't favor my methods you could search with the keywords, install software ubuntu terminal, either in the forum search or with your favorite search engine, there will be plenty of things to read.

[Edit] Oops, I forgot you aren't familiar with Ubuntu yet. In order to use the commands that make changes to your system (like installing software) you need to use the command sudo in front of things like apt-get.

---

### Post by Nyght on 2011-10-08
Thanks everybody that is very helpful. The last entry is very detailed. I have seen a friend use the command line like that before but dude has stuff on the go so i don't like to bother him with every little thing. Those four projects got me up to speed for most linux tasks that are relevant right now. If I have an issue I will post a 5th project later.

See you on the other side... Z/Z

---

### Post by QLee on 2011-10-08
[QUOTE=Nyght]...I have seen a friend use the command line like that before but dude has stuff on the go so i don't like to bother him with every little thing. ...[/QUOTE]
Hey, that's what the forums are for, you can find someone to bother here 24/7/365. ;-)

---

