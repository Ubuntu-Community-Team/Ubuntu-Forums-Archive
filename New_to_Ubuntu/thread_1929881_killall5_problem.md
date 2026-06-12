---
title: "killall5 problem"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by mebss on 2012-02-22
Hi all !
 
I have Kubuntu 11.10 (all updated) and I was using gparted to resize a  disk. I couldn't because of programs using the disk so I called killall5  in order to allow gparted to proceed, but this command killed  EVERYTHING, including graphic interface.
Even when I reboot, all I get (after the Kubuntu loading screen, with the dots) is a tty prompt to login.
I tried startx but doesn't work.
I first thought I had to reset the runlevel, but this is not the problem.
I definitely don't have the level yet to use linux in command line [IMG]http://www.linuxforums.org/forum/images/smilies/icon_razz.gif[/IMG]
This is not the first time it happens; the first time, I just  reinstalled Kubuntu, but I don't want to reinstall everything so I ask  you for help [IMG]http://www.linuxforums.org/forum/images/smilies/icon_smile.gif[/IMG]
 
I tried this : [http://ubuntuforums.org/showthread.php?t=1725350&highlight=killall5](http://ubuntuforums.org/showthread.php?t=1725350&highlight=killall5)
but the xorg.conf file doesn't exist on my system :s

Thanks in advance ^^

---

### Post by matt_symes on 2012-02-23
Hi

From the man page of killall5

> DESCRIPTION
       killall5 is the SystemV killall command. It sends a signal to all processes
       except kernel threads and the processes in its own  session,  so  it  won't
       kill  the  shell that is running the script it was called from. [B]Its primary
       (only) use[/B] is in the rc scripts found in the /etc/init.d directory.

Don't use it again.

The easiest way may be to back up your data and reinstall. If you do, create a separate root and home partition so if you need to reinstall you can install in the root partition and still have your home partition intact.

A tip for you. Resize a hard drives partitions from a LiveCD/USB. Then you will only have to worry about swap being mounted.

Kind regards

---

### Post by mebss on 2012-02-23
Yes, it was a mistake and I'll learn from it.
I'll wait one or two days more, maybe someone has the solution. If not I will reinstall.
Thank you for your answer and the tip.
Thanks to all readers too.
Have a nice day.

---

### Post by matt_symes on 2012-02-24
Hi

I am not a Kubuntu user so i will stay well away.

Just a thought though, have you posted on the Kubuntu forums ?

Kind regards

---

### Post by mebss on 2012-02-24
Yes, I did. Is the difference between Kubuntu and Ubuntu so big? Don't they have the same kernel?
If I find the solution elsewhere, I'll post it here.

---

### Post by oldos2er on 2012-02-24
To run partitioning operations, a given partition needs to be unmounted. If it's your root partition, you need to boot from LiveCD or LiveUSB to accomplish what you need to.

Before reinstalling, try this. It will delete all customizations you might have made to Kubuntu, so fair warning. From within your home folder (where you should be after logging in) ```
rm -rf .kde/
```
Then reboot, and let us know what happens.

You can also visit kubuntuforums.net for Kubuntu support.

---

### Post by matt_symes on 2012-02-24
Hi

> Yes, I did. Is the difference between Kubuntu and Ubuntu so big? Don't they have the same kernel?

Same kernels and similar init scripts but different desktops and applications (although you can use gtk applications in a qt environment if you have the libraries installed).

Try Ann's suggestion. I believe she is a Kubuntu user (you are yes ?).

Kind regards

---

### Post by oldos2er on 2012-02-24
> **matt_symes said:**
> Try Ann's suggestion. I believe she is a Kubuntu user (you are yes ?).


Yep.

---

