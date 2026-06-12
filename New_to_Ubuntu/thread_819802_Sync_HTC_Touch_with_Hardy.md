---
title: "Sync HTC Touch with Hardy?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Zavie A. on 2008-06-05
Is there a way that i can sync my HTC touch with hardy?
so far I've had to use Windows and ActiveSync to add or remove files from it.

Thanks in advance :)

---

### Post by Stefanie on 2008-06-05
have a look at this site [http://www.synce.org/moin/](http://www.synce.org/moin/)  Synce works like active sync, but without the GUI and the crashes ;-) it's not always easy to set up, but if you have a clean hardy install and you follow the guide to the letter everything should work. you have to copy-paste a lot of commands into the terminal, though.

note that, once the installation is done, you will always have to open two terminal windows. the first terminal is running sync-engine (you'll see), this sync-engine process never stops and if you're new it seems like it's stuck, but it's not. while sync-engine is running in the first terminal you need to run the commands to do the syncing (or to create partnerships and groups) in the second terminal. to me this was quite confusing in the beginning, but once you've done it a few times it becomes really easy.

if you're stuck, feel free to ask, i'm quite new myself but i've been using synce for almost a month now (with a very stubborn device apparently) so maybe i can share my experience.

---

### Post by Zavie A. on 2008-06-05
thanks for the info.
but i did run into a little problem.
when I type "sudo rmmod rndis_host cdc_ether usbnet" into the terminal
I get this error:

> zavie@zavie-desktop:~$ sudo rmmod rndis_host cdc_ether usbnet
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules


any thoughts?

---

### Post by aeiah on 2008-06-05
you dont need to worry if they dont exist. it says "Unload the current modules:" and tells you to run that command you ran to unload them. if your computer is telling you they dont exist, then they're obviously unloaded already :guitar:

---

### Post by aeiah on 2008-06-05
```
sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,usbnet}.ko
```

this will probably spit you an error too, since you dont seem to have the modules anyway

---

### Post by Stefanie on 2008-06-06
i think i had the same error the first time i tried to setup synce. don't worry, the most important part is where you load the new modules, as long as that works you'll be fine.

---

### Post by maxpathan on 2008-06-09
Hi, I have an HTC Kaiser. I follwed the wiki pages. I opened to terminal sessions and did what you mentioned above.

Sync seems to work, but when  I check evolution, the new contacts are not sync??

---

### Post by Stefanie on 2008-06-09
i don't know about contact syncing. the first times i tried synce i had enabled contacts and calendar, but i always had problems. so i set up a new partnership which only syncs the calendar, and this works fine. so i guess there is a bug in the contacts option, or maybe it isn't compatible with all kinds of phones...

---

### Post by Avinash.Rao on 2008-09-12
I have a HTC touch with Windows CE version 6.0.  and I am trying to setup synce as per the instructions given in the website **[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)** but i am stuck at core libraries step. I have installed the libraries, but when i execute synce-pls

root@human:~# synce-pls
synce-pls: symbol lookup error: synce-pls: undefined symbol: rapi_connection_from_name

I have installed Multisync and enabled the advanced network functionality on my PDA. My Hardy is detecting the PDA coz the output of lsusb is 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 009: ID 0bb4:0b0c High Tech Computer Corp. 

All i want is to import export my contacts to my laptop.

Any ideas?
Avinash

---

### Post by Avinash.Rao on 2008-09-13
Can anyone help me with this?

---

### Post by tgyorgyi on 2008-09-13
You could try posting to the SynCe mailing list for these queries, more likely that there is a higher concentration of synce-knowing people active there:

[https://lists.sourceforge.net/lists/listinfo/synce-users]("https://lists.sourceforge.net/lists/listinfo/synce-users")

---

### Post by shantanubhadoria on 2008-09-15
Does anyone here know if we can install UBUNTU MID on HTC Touch 64/64 ?? I am sick of wm6

---

### Post by Avinash.Rao on 2008-09-15
Thanks


> **tgyorgyi said:**
> You could try posting to the SynCe mailing list for these queries, more likely that there is a higher concentration of synce-knowing people active there:

[https://lists.sourceforge.net/lists/listinfo/synce-users]("https://lists.sourceforge.net/lists/listinfo/synce-users")

---

