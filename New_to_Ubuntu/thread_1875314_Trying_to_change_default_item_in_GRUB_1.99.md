---
title: "Trying to change default item in GRUB 1.99"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by ask_ on 2011-11-04
Hello , I am very new to Ubuntu. This may be asked in this forum several times . But I wanted to make sure I am not messing up anything in particular.

I want to change the default item in my GRUB.
The version of my GRUB is 

> grub-install (GRUB) 1.99-12ubuntu5I am using Ubuntu 11.10 on a 32-bit computer.
The other OS that I have is WIndows Vista.

I wish to make Windows Vista as the default item which is highlighted in the GRUB menu.Currently the default item is the 1st item in the menu.

I read parts of this webpage - [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) .

I could assimilate some of it.
I gather that grub.cfg file should be left alone. And what needs to be edited is the grub file present in etc/default/  folder.

Now when I go to the folder there is a text file called 'grub'  . I have to edit this isn't it? (it has the GRUB_DEFAULT variable set to 0 currently).

Trouble is it is a read-only file and I don't know how to change it's permissions. I am stuck on this point.
Is it okay to change this file so that I get the desired result.

Note - I wish to use the method in which we set the variable to a string value. I.e my OS name in the GRUB menu is "Windows Vista (loader) (on /dev/sda2)" . Can I set this as the value of variable GRUB_DEFAULT ?


Thanks.


*edit :- *
Found the solution on this thread - [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743) after a bit of searching. :oops:  . Will search more from next time onwards.

Anyways thanks to the forum in genral for providing such great help on all the threads.

---

### Post by little_penguin on 2011-11-07
Another easy, graphical way to do this is to use Grub Customizer, see:
 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by ask_ on 2011-11-07
Thanks.

---

