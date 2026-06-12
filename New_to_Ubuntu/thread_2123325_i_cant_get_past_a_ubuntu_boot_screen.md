---
title: "i cant get past a ubuntu boot screen"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by delicae on 2013-03-07
i installed ubuntu from my usb along side windows however when i boot ubuntuit wont boot past a screen with a list off actions and all oks and the list ends with stopping save kernal acttion

---

### Post by Lisiano on 2013-03-07
Could you please do this, boot the PC and in Grub (The menu where you pick what OS to boot), select the topmost line and press e, then scroll down using the arrow keys down to a line that starts with linux for example ```
linux   /boot/vmlinuz-3.7.0-7-generic root=UUID=c4db4ecf-5983-4e04-a2ce-ef49ca20fdda ro   quiet splash vt.handoff=7
``` and remove everything past ro, like this ```
linux   /boot/vmlinuz-3.7.0-7-generic root=UUID=c4db4ecf-5983-4e04-a2ce-ef49ca20fdda ro
```After you are done, press Ctrl+X. You will see a lot of text scroll by, when you see that it is "stuck" for a while (Longer than 30 seconds), take a picture of the whole text using a camera or preferably type up what you see about 5-10 lines from the bottom.

---

### Post by delicae on 2013-03-08
[ATTACH=CONFIG]239893[/ATTACH][ATTACH=CONFIG]239894[/ATTACH]

---

### Post by NikTh on 2013-03-08
Hi , 
read here , about some parameters that you can apply. 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Hope it helps. 

Thanks

---

### Post by Lisiano on 2013-03-08
Hmm... Could you try doing the same process again, but also add "verbose nomodeset" after ro?
```
linux   /boot/vmlinuz-3.7.0-7-generic root=UUID=c4db4ecf-5983-4e04-a2ce-ef49ca20fdda ro verbose nomodeset
```

---

