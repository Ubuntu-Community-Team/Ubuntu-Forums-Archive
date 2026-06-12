---
title: "Hardy Heron Slow Boot Problem"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by doninsa on 2008-07-12
Ubuntu boot time is slower than Windows XP.  I know there's a problem with my installation because boot times have been faster on other computers.  Recovery mode shows that some of the slowdowns are as follows:

ata6.00 Status {DRDY}
ata6.00 Port is slow to respond, please be patient (status 0xd0)
device not ready (errno = -16), forcing reset

This message is repeated several times.  

I also get the following message

Drive 'SR' needs updating - please use buss type methods.

How do I do that??

Motherboard is an ASUS M2NPV-VM if that helps.  
Other Ubuntu installs have gone well without these kinds of problems.  So I suspect the problems I'm seeing are particular to this computer.  Any help would be appreciated.  

Late entry: I used Startup Manager to turn on text during the boot process. When the delay occurs the message is as follows:
  Loading Hardware Drivers...
It ends with a failed notice.

Regards,
Don

---

### Post by Mister.Vash on 2008-07-12
This may help - looks like it was an issue with one of the drivers being loaded and blacklisting took care of

[http://forums.fedoraforum.org/printthread.php?t=169283](http://forums.fedoraforum.org/printthread.php?t=169283)


Before trying this, review your /var/log/dmesg file to see it mentions the pata_marvell like in post.  If it doesn't, then post the section from /var/log/dmesg that includes the details with the errors and the messages from just above the errors

---

### Post by doninsa on 2008-07-13
> **Mister.Vash said:**
> This may help - looks like it was an issue with one of the drivers being loaded and blacklisting took care of

[http://forums.fedoraforum.org/printthread.php?t=169283](http://forums.fedoraforum.org/printthread.php?t=169283)


Before trying this, review your /var/log/dmesg file to see it mentions the pata_marvell like in post.  If it doesn't, then post the section from /var/log/dmesg that includes the details with the errors and the messages from just above the errors

Thanks for the reply.  I've attached the dmesg file as you suggested. I had to zip it to get past the file size limit.  From what I can see this is not the same problem that others were having with the pata_marvell.  You can search on errno=-16 to see where the system is timing out over and over again.   

Thanks,
Don

---

### Post by doninsa on 2008-07-13
Testing update on the slow boot problem:
I turned off the pata ports in bios and the problem went away.  But I have my CD player attached to pata 2 master.  From reading the boot log it looks like a new driver is required for the CD drive.  How do I update that driver?  I'm hoping that the driver update will solve the slow boot problem.  I still need help.
Regards,
Don

---

### Post by spiderbatdad on 2008-07-13
You might try editing the file /boot/grub/menu.lst as follows:
```
gksu gedit /boot/grub/menu.lst
```scroll down the the section under ###END DEFAULT OPTIONS##

change the line beginning with the word "kernel" as follows:

```
root=UUID=3167dc15-f5f7-4343-8e50-662bef762b60 ro pci=routeirq
```
not sure why you have vga=771, but if you did that, you can leave it of course. If that fails you might try pci=nomsi vga=771

---

### Post by doninsa on 2008-07-13
> **spiderbatdad said:**
> You might try editing the file /boot/grub/menu.lst as follows:
```
gksu gedit /boot/grub/menu.lst
```scroll down the the section under ###END DEFAULT OPTIONS##

change the line beginning with the word "kernel" as follows:

```
root=UUID=3167dc15-f5f7-4343-8e50-662bef762b60 ro pci=routeirq
```
not sure why you have vga=771, but if you did that, you can leave it of course. If that fails you might try pci=nomsi vga=771

Greetings Spiderbatdad,

I made the changes you suggested but the only effect they had was to change the boot screen from the ubunto logo to a terminal display with each step in the boot process shown.  I don't think this is where the problem is coming from.

I've discovered that my DVD/CD player recorder is also not operating.  It appears when I select Places - Computer, but I can't mount it.  I think the slow boot problem is the result of trying to set up the player over and over again during the boot process.

AS I said in an earlier post, turning off all the pata ports clears up the slow boot problem, but then the DVD/CD player is not even seen in Places - Computer.  Turning off all the pata ports is a less than optimal solution.   Any more ideas how I can fix this?

Thanks,
Don

---

