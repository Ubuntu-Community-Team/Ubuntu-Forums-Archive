---
title: "[SOLVED] Fixing: Update Manager"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by takuhii on 2008-05-26
My update manager seems to have lost the ability to auto matically update Hardy, and it constantly says it was uodated about an hour ago, even though my PC was switched off...

Anyone got any ideas how I can "reset" update manager??

---

### Post by kansasnoob on 2008-05-26
The only thing I can think to check is to open Synaptic, then >Settings>Repositories and click on the Updates tab.

By default Important Security Updates and Recommended Updates should be checked, but NOT Pre-released and Unsupported updates. 

Just below that in the automatic update area the "Check for Updates" box should be checked and you can select "Daily" (that's the default). And "Only Notify about available Updates" should be ticked.

In the last area the default should be "LTS releases only.

Hope this helps, if not you'll have to wait for someone less "green" than I am.

---

### Post by Inxsible on 2008-05-26
You can also try executing these commands in a terminal ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by takuhii on 2008-05-28
cheers for the help, I tried that, but now I need to wait for some updates to come out to see if it's worked...

---

### Post by Biggy on 2008-05-28
in terminal :
> sudo aptitude update
> sudo aptitude safe-upgrade

---

### Post by terabyte1 on 2008-05-28
> sudo apt-get update && sudo apt-get upgrade

Now that, Inxsible is a really cool answer and sweet to use ^_^ !

terabyte1:guitar:

---

### Post by raymondvillain on 2008-05-28
When I run update, it acts like it is trying to start, but then nothing happens.  No window, no update, no little gizmo whirling in an endless circle.  And when I try synaptics, same thing.

I have used both of these previously but now they won't cooperate.

If I open a terminal and type "sudo apt -get update && sudo apt -get upgrade" I get the response
"sudo:  apt:  command not found"

Any ideas?

Running 8.04 on a desktop.  Last couple of days I installed samba.  Does that have an affect on update or synaptics?

Thanks in advance

---

### Post by Sinkingships7 on 2008-05-28
try:
```
sudo apt-get remove --purge update-manager update-notifier
```
then:
```
sudo apt-get install update-manager update-notifier
```


EDIT: then run ```
sudo apt-get update
```

---

### Post by raymondvillain on 2008-05-28
When I try

"sudo apt-get remove --purge update-manager update-notifier"

I get

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

What is to be done?

---

### Post by Sinkingships7 on 2008-05-28
try this:
```
sudo dpkg --configure -a
```

---

### Post by Da3 on 2008-05-28
> **Sinkingships7 said:**
> try this:
```
sudo dpkg --configure -a
```

i have just typed that into the terminal to try and fix a different problem that i am having and the terminal keeps responding with "dpkg: requested operation requires superuser privilege" how do i get passed this?

---

### Post by Da3 on 2008-05-28
> **Sinkingships7 said:**
> try this:
```
sudo dpkg --configure -a
```

i have just typed that into the terminal to try and fix a different problem that i am having and the terminal keeps responding with "dpkg: requested operation requires superuser privilege" how do i get passed this?

my original problem is when trying to install updates i keep getting this error message 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i am new to Ubuntu so any help will be very appreciated

thank you

DA3

---

### Post by Sinkingships7 on 2008-05-28
The error you're getting is requesting that you put 'sudo' before 'dpkg --configure -a'. If you pasted the code I gave you, then provided your password, that error should not be there. Are you sure you typed 'sudo'?

---

### Post by Inxsible on 2008-05-28
> **raymondvillain said:**
> When I run update, it acts like it is trying to start, but then nothing happens.  No window, no update, no little gizmo whirling in an endless circle.  And when I try synaptics, same thing.

I have used both of these previously but now they won't cooperate.

If I open a terminal and type &quot;sudo apt -get update && sudo apt -get upgrade&quot; I get the response
&quot;sudo:  apt:  command not found&quot;

Any ideas?

Running 8.04 on a desktop.  Last couple of days I installed samba.  Does that have an affect on update or synaptics?

Thanks in advance

There is no space between apt and the hyphen. I see you have one there. apt-get is all without spaces in between. Try the commands again and it should work.

---

### Post by raymondvillain on 2008-05-29
Thanks for the tip.  As you suggested, I tried

sudo dpkg --configure -a

and it still didn't work, returned:

Setting up linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-generic

I'm thinking I may have to re-install Ubuntu 8.04.  Do you have any other ideas?  This is my first week ever of using Linux.  Wish I'd created some system restore points.

---

### Post by PmDematagoda on 2008-05-29
The problem is looking right at you:-
```
gzip: stdout: **No space left on device**
```

Clear the drive out and make some free space, then try again.

---

### Post by raymondvillain on 2008-06-03
> **PmDematagoda said:**
> The problem is looking right at you:-
```
gzip: stdout: **No space left on device**
```

Clear the drive out and make some free space, then try again.

Thanks for the info.

I'm new to Linux and I am mystified by the way files are organized.  If I bring up the graphical file browser and click on /boot >> properties it tells me there are only 3 megabytes of space left.  But Linux is installed on a brand new 250 gigabyte hard drive, not shared with any other OS.

Can you add some details to your suggestion?

Where is gzip trying to place it's output with stdout?

---

### Post by philinux on 2008-06-03
Use 

System> Admin>system monitor

Click the file system tab

Take a screen shot and post it.

---

### Post by raymondvillain on 2008-06-03
O. K.!

Here is my screenshot (I hope it is attached).  It says that /dev/sdc11 is the directory /boot, type ext3, total size 37.9 MiB, Free space 5.1 MiB, Available space 3.1MiB, Used space 32.8 MiB, "91%".

Is it a straightforward matter to adjust the partition sizes?  There's plenty of room for me to make /boot much larger.

---

