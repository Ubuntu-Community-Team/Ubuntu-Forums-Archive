---
title: "[SOLVED] Editing boot options"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by 843 on 2008-06-08
I have both Windows and Linux in dual boot on my laptop. I use the Grub bootloader, so when I boot the laptop, the boot options that appear are Ubuntu, Recovery Mode, Memory Test and Windows XP. What I want to know is if it's possible to hide the Windows XP option, not unlike modifying the boot.ini file in Windows XP. Of course I want the process to be reversible. Thanks in advance.

---

### Post by aysiu on 2008-06-08
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo nano -B /boot/grub/menu.lst
``` Find the line that says ```
#hiddenmenu
``` and change it to ```
hiddenmenu
``` and then save (Control-X, Y, Enter).

---

### Post by drs305 on 2008-06-08
> **843 said:**
> I have both Windows and Linux in dual boot on my laptop. I use the Grub bootloader, so when I boot the laptop, the boot options that appear are Ubuntu, Recovery Mode, Memory Test and Windows XP. What I want to know is if it's possible to hide the Windows XP option, not unlike modifying the boot.ini file in Windows XP. Of course I want the process to be reversible. Thanks in advance.

View this HOWTO and look at the section on modifying menu.lst with the comment symbol (and lots of other things).
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by balachandarlinks on 2008-06-08
Ya..It is Possible.....
  Try to install **QGrubEditor**....You can find it in synaptic packet Manager...
  Use the Back up file option to back up your current settings and delete windows XP entry...
  Later you can use restore option to get windows XP.....:popcorn:

---

### Post by Fixman on 2008-06-08
Alternatively, you can install QGRUBEditor for a GUI.

---

### Post by Yuki_Nagato on 2008-06-09
Do you want the entire GRUB menu hidden or do you just want Windows XP hidden, to be launched with command line commands when you want it?

hidden menu for hiding the entire thing, "#" out the whole block of XP options for just XP.

---

### Post by 843 on 2008-06-09
I used the startup manager and it works like a charm. I tried modifying with the terminal but it doesn't seem to work, maybe I edit the wrong line (is it the one with # or ##?) For some reason I cannot download the package via Synaptic, I think the local server is corrupted.

Thanks for the help, guys! The swift replies in this forum is astonishing, almost makes it... addicting to post questions :)

EDIT: Thanks Yuki_Nagato, for the clarification

---

### Post by fidamehran on 2008-06-09
I am sorry to barge in with a newbie question at this point of the thread. My Ubuntu received update on Kernel and now "Ubuntu 8.04, kernel 2.6.24-18-generic" or something has been the latest one. By default it boots there, and it's a text based interface. I need the GUI.

So, I need to know one thing. Is there any such thing that, a Gnome update will come to cover the new kernel, so that the new updated kernel also shows GUI/desktop? It is really awkward to have the OS updated and not get a desktop for that...

---

### Post by spiderbatdad on 2008-06-09
> **fidamehran said:**
> I am sorry to barge in with a newbie question at this point of the thread. My Ubuntu received update on Kernel and now "Ubuntu 8.04, kernel 2.6.24-18-generic" or something has been the latest one. By default it boots there, and it's a text based interface. I need the GUI.

So, I need to know one thing. Is there any such thing that, a Gnome update will come to cover the new kernel, so that the new updated kernel also shows GUI/desktop? It is really awkward to have the OS updated and not get a desktop for that...

When there is a kernel upgrade the package manger asks "What do you want to do about menu.lst?" The default option is: "keep the current version." At least my update manager behaves that way.

drs305 has posted a link to a guide above, for repairing menu.lst

---

### Post by fidamehran on 2008-06-09
I am sorry. My Update Manager did not notify me anything, rather just installed the new kernel.

I read drs305's posted link. I think I somewhat understood that. So, the bottom line is that nothing will happen automatically to cover the new kernel and give it a GUI, right?

I don't want to cure the headache by chopping off the head, if you know what I mean...

Sorry for all the trouble. You must be thinking, why do these losers start using Linux? Can't they stick to lame OSs like Windows, for God's Sake?

---

### Post by fidamehran on 2008-06-09
I am sorry. My Update Manager did not notify me anything, rather just installed the new kernel.

I read drs305's posted link. I think I somewhat understood that. So, the bottom line is that nothing will happen automatically to cover the new kernel and give it a GUI, right?

I don't want to cure the headache by chopping off the head, if you know what I mean...

Sorry for all the trouble. You must be thinking, why do these losers start using Linux? Can't they stick to lame OSs like Windows, for God's Sake?

---

### Post by 843 on 2008-06-09
fidamehran, I think it's better if you start a new thread, since this thread has been marked 'solved'.

---

