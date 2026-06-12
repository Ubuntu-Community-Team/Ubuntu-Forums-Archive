---
title: "Wont boot up"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Trojan Man on 2008-10-04
Im trying to dual boot with vista and ubuntu. I install ubuntu fine then when i restart and select it it goes into the loading bar screen fine. but then after that it goes to a black screen and it seems it trys to repeat some commands, and keeps doing it. ill get what the commands its doing in 1 min. Anyone know how to fix this?

ok this is what it says

ata2.00:exception emask oxo sact oxo serr oxo action ox2 frozen
Ata2.00 cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 p.0 36 in status {drdy}

---

### Post by Trojan Man on 2008-10-04
o yea specs are
intel core 2 duo 2.83 2.83
4 gb ram
32 bit
nvidia 8100

---

### Post by Ryadt on 2008-10-04
Can you boot in recovery mode?

---

### Post by Trojan Man on 2008-10-04
no ive tried the graphics safe mode and the other one and it says something about one of my drivers.

---

### Post by Ryadt on 2008-10-04
Try checking the md5sum of your installation cd. 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by porchrat on 2008-10-04
found this thread, deals with your problem.

They recommend installing using "irqpoll" to the install, and then adding it to the /boot/grub/menu.lst file.

[http://ubuntuforums.org/showthread.php?t=585566]("http://ubuntuforums.org/showthread.php?t=585566")

Hope that helps.

Out of curiosity are you using a Samsung CD or DVD drive of some kind?  Seems that is also a cause of this problem in some cases.

---

### Post by Trojan Man on 2008-10-04
thanks for the help ill try thoses both out 
i use a optiar dvd rw ad 2200s ata device. would that be the problem? cause the problem always had ata in front of it

---

### Post by porchrat on 2008-10-04
> **Trojan Man said:**
> thanks for the help ill try thoses both out 
i use a optiar dvd rw ad 2200s ata device. would that be the problem? cause the problem always had ata in front of it

It couldn't hurt to swap out the DVD drive for something else, but first try the "irqpoll" example in that thread as it is much easier, and it even shows you how to make the modification carry over to future kernel updates... if that solution works you won't have a problem with this again.

---

### Post by Trojan Man on 2008-10-04
ok ill give it a try

---

### Post by Trojan Man on 2008-10-04
or would it be easier if i made a parition myself then rebooted the computer and loaded ubuntu from the reboot screen? or should i have been doing that all along?

---

### Post by porchrat on 2008-10-04
> **Trojan Man said:**
> or would it be easier if i made a parition myself then rebooted the computer and loaded ubuntu from the reboot screen? or should i have been doing that all along?

Maybe it is because I'm tired but I don't really understand what you're saying.

---

### Post by Trojan Man on 2008-10-04
lol my bad. what i was trying to say was would it be better if i made my own partition instead of letting ubuntu do it from the cd when i load it into windows.
and from my own partition i load the cd when i start up my computer. if that makes any more sense. if not im still confused on where i would do the whole "irqroll" thing
sorry im kinda clueless on the stuff.

---

### Post by porchrat on 2008-10-05
As for where you use "irqpoll":  When the liveCD menu comes up (after you have selected your language) you press F6 at which point you will see a line of text.  At the end of the line you type "irqpoll".  Hopefully this will solve the problem.  However Ubuntu will probably still have issues booting after this.  In order to make the "irqpoll" change stick in Ubuntu you will need to edit the "menu.lst" located in /boot/grub/menu.lst

However more on that later.  First deal with getting it to boot.

---

### Post by Trojan Man on 2008-10-07
So far so good installing now I got it to boot hopefully the install will work

---

### Post by Trojan Man on 2008-10-07
everything works great now its up and using it right now thank u very much!!

---

