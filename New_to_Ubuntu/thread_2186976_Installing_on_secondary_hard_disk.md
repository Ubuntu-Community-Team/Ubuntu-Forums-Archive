---
title: "Installing on secondary hard disk"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by andres.andres_ on 2013-11-10
First of all, I´m spanish, so if I have some mistakes, please, forgive me.
I have a very paricular problem. Until a few months ago, I was using an old computer. I bought one new, with windows 7 and from I´m tipping. The old computer has broken, it has windows XP and I need the CD to repair it (I loosed it). So, I thought to install ubuntu in it. The problem is that the BIOS is too old, so it can´t boot from USB. Also, for make it cheaper, the new computer hasn´t got CD-writer, only reader. I have taken the hard disk from the old computer (SATA) and plugged it into the new computer. 
Now, I´m trying to install ubuntu directly in the hard disk. For that I have downloaded both ubuntu 12 and ubuntu 13. I also have downloaded unetbooting, but it doesn´t recognizes the secoundary hard disk, e/, only, c/ (If you have the solution for that it also can be usefull). Ubuntu was a ISO image, so I used Daemon tools to assemble it. That worked for ubuntu 12. I could install perfectly ubuntu and it worked in the new computer, but when I put the hard disk in the new computer it says "Missing bootmgr".
What can I do? I have come here because everybody says is the best forum, an I couldn´t find a solution
If I have expressed bad something, please say me and i try to explain, is a complex problem and I don´t dominate english
Thanks a lot

---

### Post by fantab on 2013-11-10
Let me see if I have understood you clearly:
You have an old computer with very old BIOS which does not support USB booting. So you pulled out the old HDD and plugged it into the New computer but the new computer does NOT recognize your old HDD, am I right so far?

1. Doesn't the old computer have a CD/DVD drive?
2. Did you format the old HDD with Linux filesystem? What did the Ubuntu installer say while you were installing Ubuntu to the OLD HDD? Any error messages?
3. What are the hardware specifications of both your computers? Especially the Graphics Cards?

When you plug in the Old HDD in the new computer what SATA Port is it being connected to? When you connect the SATA cable on the motherboard look carefully on the board for SATA0, SATA1, etc. You New HDD must be on the SATA0 or SATA1, and the older HDD should be connected to the next SATA number.
I suspect that you are connecting your OLD HDD to an earlier SATA and hence its becomming the First HDD, when connected.

Also It should not matter 'bootmgr missing' if you are booting from USB. After pluging the OLD HDD to the new computer boot from USB, Tell the BIOS to do so.

---

### Post by oldfred on 2013-11-10
Bootmgr missing is a Windows boot error, or you did not get grub installed to MBR of hard drive.

Also new computer will support just about any version of Ubuntu, but if old computer does not have much RAM or older video system then Lubuntu or other lightweight system may be all you can install.

You have to use Something else or manual install when installing as grub defaults to install to sda. Or you may have grub installed on your new computer? With something else you have to define partitions, format (ext4) and mount like / (root) and /home  and swap. And in the combo box at bottom choose hard drive for install of grub2 boot loader. Example below is still at default of sda.

---

### Post by andres.andres_ on 2013-11-11
Sorry for the delay, I have been doing tests. Finally, I think the problem was in the graphic card. The computer does a sound like piiiiiiiii pi pi, and that means that the graphic card is wrong. I associated that with a windows error because it wasn´t the first time that the computer did that sound and I always fixed that with the windows CD, but this time it looks like the graphic cards has definitely dead, because a friend gave me a ubuntu CD and it neither worked. So, I´m gonna recicle the parts I can (Problably I will install Ubuntu in the other HDD) and throw up the broken ones.
Thank you for the help, you were who best answered me.

---

### Post by sha1sum on 2013-11-11
Putting the hard drive from one computer into another computer can cause problems. Especially if it´s from an old computer, I have had bad experiences with that. (I'm like you, I also like to experiment). If you don't have a cd writer, maybe there is another way to get an Ubuntu cd. For example buy one ([here]("http://shop.canonical.com/product_info.php?products_id=976")) or have a friend make you an install cd.

Good luck!

---

