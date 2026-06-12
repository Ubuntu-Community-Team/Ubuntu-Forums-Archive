---
title: "Why do I have a grub menu now after running a boot repair?"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by 577 Jersey on 2012-11-16
Hi guys,,
 I made a live DVD of the redo backup([http://redobackup.org/](http://redobackup.org/)) and ran boot repair just to see what would happen,,and now my grub menu appears when I boot up.I guess this is a good thing as I can choose an older kernel to boot into...also,,how can I make the grub menu disappear so the computer goes strait to loggin screen after boot like it is supposed too?

Did I make a mistake buy doing this?

I like to tinker,,but it gets me good at doing clean installs as of lately.

BTW-12.04 is the only OS on this machine.

 Thanks Tommy

---

### Post by Aaron Christianson on 2012-11-16
I've never tried exactly what you are talking about, but it is possible that grub repair added additional options to your boot menu, which caused the menu to load by default (whereas it normally doesn't if there aren't any important options, unless it detects a reason to do so).

If you wish to remove the grub menu, it is easy to do so.

hit ALT+F2 or open a terminal and type:
```
gksu gedit /etc/default/grub
```near the top of the file there is a line that says:
```
GRUB_TIMEOUT=5
```The number may be different than five on your system. This is the number of seconds before grub automatically selects the first option. If you don't want to see the boot menu, you can set it to `0`. You can also set it to one or two seconds if you want to see it only for a very short time.

After setting the desired value, save and exit gedit (aka "Text Editor"). After this run this command in a terminal for your changes to take effect:
```
sudo update-grub
```Hope this tells you something you want to know, even if it does not provide a direct answer to your question.

edit: by the way, you can mess things up badly by changing the wrong thing in /etc/default/grub, so be careful and don't mess with it too much without reading the documentation for Grub2 unless you are comfortable fixing your system from a recovery console (like, with just the command line for working, and limited access to your stuff, in case you don't know what the recovery console is).

---

### Post by 577 Jersey on 2012-11-16
Thank you very much,,
 That was the problem,,it changed my default to 10,,so I put it to 5 and now I like it better!!

 Ive been learning so much from you guys,,really appreciate it!!


I have no idea what the recovery console is,,only have been playing around with linux and ubuntu for a few weeks,,but trying to learn as much as possible.Just starting to use terminal a little,,I was scared of it at first,,but now Im getting tired of doing clean installs so Im trying to learn how to fix things from the terminal.

I really like ubuntu 12.04 so far,,very solid!!!

 Tom:guitar:

---

### Post by Aaron Christianson on 2012-11-16
Cool!
Last step: go to the top of the page and click on "thread tools" to mark the thread as solved. This makes it easier for other users who have the same question to find the answer.

---

### Post by lindsay7 on 2012-11-16
look to see if you have "startup manager" installed, if not go to your package manager and get it. You can change the time the start menu is displayed from there and also set other things up.

---

### Post by Aaron Christianson on 2012-11-16
Yeah, I guess I'm old-school. :D

---

### Post by oldfred on 2012-11-16
If you look at your boot repair it should have told you this among a whole lot of other things. :)

Additional repair would be performed: unhide-bootmenu-10s

So it edited grub for you and set it to 10 sec and made sure it showed.

---

### Post by 577 Jersey on 2012-11-16
Thank you,,thank you,,and thank you guys!!

Great forum we have here!!!

---

### Post by 577 Jersey on 2012-11-17
> **lindsay7 said:**
> look to see if you have "startup manager" installed, if not go to your package manager and get it. You can change the time the start menu is displayed from there and also set other things up.
I could not locate"startup manager"in synaptic or software??

But I am interested in using it!

 Tom

---

### Post by YannBuntu on 2012-11-17
hello
> **577 Jersey said:**
>  I made a live DVD of the redo backup([http://redobackup.org/](http://redobackup.org/)) and ran boot repair

For information, RedoBackup is based on an obsolete version of Ubuntu, and includes an obsolete version of Boot-Repair.
[http://sourceforge.net/p/redobackup/discussion/1169663/thread/326f1ac6/](http://sourceforge.net/p/redobackup/discussion/1169663/thread/326f1ac6/)

If you want to use Boot-Repair, please follow these instructions: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lindsay7 on 2012-11-20
it is listed as startupmanager all one word

---

### Post by 577 Jersey on 2012-11-20
Thanks!!!:guitar:

---

### Post by YannBuntu on 2012-11-21
StartupManager is DEAD. Its developper recommends to use [GRUB-Customizer]("https://launchpad.net/grub-customizer") instead.
See [https://launchpad.net/startup-manager/+announcement/8300](https://launchpad.net/startup-manager/+announcement/8300)

---

