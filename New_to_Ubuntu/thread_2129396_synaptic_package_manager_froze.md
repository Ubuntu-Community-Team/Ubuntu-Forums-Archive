---
title: "synaptic package manager froze"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by Darkishjace on 2013-03-26
K so here i sit with synaptic stuck at the same spot on the loading bar after successfully installing > lubuntu-restricted-extras (finally) as my first package and then moving on to install the broadcom package > bcwml-kernel-source the reason i decided to install this package is because i was informed that my netgear wifi usb stick would in fact be recognized as soon as it happened to be installed i think this is the 6th time ive re-installed lubuntu on my flash drive over the last 5 days underneath the loading bar it says > running post-installation trigger initramfs-tools.  

in the dialog box the last two things to happen in it happened to be: 

> cryptsetup: WARNING: failed to detect canonical device of overlayfs. 
cryptsetup: WARNING: could not determine root device from /ect/fstab 

thank you in advance

---

### Post by carl4926 on 2013-03-26
I would close it and try doing

```
sudo apt-get update
```
Report any strange feedback

---

### Post by Darkishjace on 2013-03-26
when i try and press [close window] on both synaptic package manager and applying changes it happens to not close them

---

### Post by carl4926 on 2013-03-26
Open a terminal and run: top

Look for the PID on the left side for synaptic - Eg; It might be 1330, just an example

to kill it

```
sudo kill -9 1330
```

---

### Post by Darkishjace on 2013-03-26
k so when i did that it made changes applied say changes successfully applied you may close window now. 
does it mean it was fixed

---

### Post by Darkishjace on 2013-03-26
oh nvm the next thing to pop up was this
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: _cache->open() failed, please report.
also im not clear if that is the reason the usb wifistick isnt working just yet or if it had happend to get to the point where it would show results

---

### Post by schragge on 2013-03-26
This error usually means that either two applications are simultaneously trying to access package management database (e.g. doing *sudo apt-get update* while synaptic is running) or you have not enough permissions to do it (e.g. running *apt-get update* without sudo). It has nothing to do with Wi-Fi not working.

Does *pgrep synaptic* show you anything?

---

### Post by Darkishjace on 2013-03-26
i dont know what pgrep synaptic is could you explain please also i restarted my computer and ran > sudo apt-get update and it ran till it seemed finished and it now says > E: dkpg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Darkishjace on 2013-03-26
also when i try and run synaptic package manager this comes up in the dialog > E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


---

### Post by schragge on 2013-03-26
In a terminal window, try
```

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

```

PS. *pgrep synaptic* is a console command that shows all running instances of synaptic. You don't need it after reboot.

---

### Post by Darkishjace on 2013-03-26
delete

---

### Post by Darkishjace on 2013-03-26
k so about 15 mins ago (right after i saw your post) i did exactly as you said the dialog says
> lubuntu@lubuntu:~$ sudo rm /var/lib/dpkg/lock
lubuntu@lubuntu:~$ sudo dpkg --configure -a 
Setting up initramfs-tools (0.103ubuntu0.2) ...
update-initramfs: deferring update (trigger activated) 
my computer started to run louder and it hasnt done anything since that came up also

---

### Post by schragge on 2013-03-26
An interrupted dpkg run had left* /var/lib/dpkg/lock* in place that prevented any further updates. After removing the lock, dpkg seems to work. I hope your problem is solved by now.

---

### Post by Darkishjace on 2013-03-26
so is it safe to close the terminal

---

### Post by schragge on 2013-03-26
It is safe if dpkg has finished its job and the last line you see in the terminal is the prompt:
```
lubuntu@lubuntu:~$
``` If not, then something is going wrong. Do you have a synaptic window open?

---

### Post by Darkishjace on 2013-03-26
nope but after i closed even tho> [COLOR=#000000][FONT=Ubuntu Mono]lubuntu@lubuntu:~$[/FONT][/COLOR] didn't come up it i restarted my computer and then tried opening synaptic package manager and this came up > Unable to get exclusive lock


This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first. 
im so confused

---

### Post by Darkishjace on 2013-03-26
also whenever i install a new lubuntu it comes without some folders i found this out when i tried to mount my 1TB harddrive (i dont know wich ones) but i had a error that popped up saying something (i forget) but i googled it and found the command that fixed it (i was missing > /media/lubuntu could the fact that im missing folders that should be on my lubuntu be the cause of all my troubles

---

### Post by Darkishjace on 2013-03-26
i had downloaded my copy of lubuntu from the link at the top of the page

---

### Post by Darkishjace on 2013-03-27
still really need help here

---

