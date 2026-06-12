---
title: "Update Manager and Copies in Grub"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Alex J. on 2008-09-02
I finally have a good connection, so I was using update manager to download some of the 230 or so possible updates. I thought it would be a good idea to update the linux headers in there (I think that's about what the updates were called). I'm pretty sure that's why I now have two identical copies of ubuntu in Grub. The annoying thing is that the first one that boots is not able to connect to the internet, while the second one does.

So I have many questions:

Is there a (safe) way to delete the first one from Grub (including all it's memory recovery stuff) to make sure the second one always boots? 
Or at least a good way to be able to switch them around in Grub?
What caused this?
And how can I make sure updates don't screw me over?

Thanks!:KS

---

### Post by echo314 on 2008-09-02
Here what I did to fix my list, to get rid of the old entries. You want to edit your config file at /boot/grub/menu.lst

The part you want to edit is right after END DEFAULT OPTIONS. Here is what mine looks like for comparison

```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3c5a5a02-0d89-4ccd-a325-de02d10e928b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3c5a5a02-0d89-4ccd-a325-de02d10e928b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I just deleted the sections I didnt want, and moved them around to the correct order I wanted. NOTE: I only moved them around in the chunks they are already in, I suggest not splitting up the chunks of rows themselves. When I rebooted everything was fine. Good luck!

---

### Post by ajgreeny on 2008-09-02
Hi Alex J.  You probably don't have two identical ubuntu entries in your grub menu.  If you look closely I think you should see that the entries are for two different linux kernels, the original 2.6.24-16 and also for the most up to date 2.6.24-19.  From what you say there is obviously a problem in your setup with the new kernel and your internet connection, which can possibly be sorted, but in order to boot by default into the old kernel you just need to edit the /boot/grub/menu.lst file.  In a terminal type ```
gksudo gedit /boot/grub/menu.lst
```and when the file appears in gedit change the 0 in the line at the bottom of this string:-

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

to 2.  This should then boot you into the older kernel each time you boot.  Then you can search into the reasons for the loss of internet connection.  Start another thread if needed, but give as much info as possible about your hardware etc etc.

---

### Post by Alex J. on 2008-09-02
Yeah, you're right, I guess I didn't read it correctly. The kernels actually ARE different. I'll boot into the old one for now and work on the newer one.

Thanks!

---

### Post by toolfan2k4 on 2008-10-21
How do we just delete the old kernal entries? I mean if we leave them there and it keeps doing this eventually I will have to scroll down a huge list to get to windows xp.:confused:Do we just delete the section of code for the older kernel?

---

### Post by toolfan2k4 on 2008-10-22
> **toolfan2k4 said:**
> How do we just delete the old kernal entries? I mean if we leave them there and it keeps doing this eventually I will have to scroll down a huge list to get to windows xp.:confused:Do we just delete the section of code for the older kernel?

OK I figured it out, I backed up my menu.lst file then deleted the 4 lines of code for each old ubuntu entry and saved the file. Rebooted and now all my old copies are gone. Excellent. Just figured I would post my results for any other newbs out there who may be wondering how to do this.

---

