---
title: "Reinstalling Ubuntu"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Aldtjaom on 2008-08-09
I was just wondering how to reinstall Ubuntu from a cd.

---

### Post by Ryadt on 2008-08-09
Same way you installed it...:lolflag:
Just pop in the cd and follow the instruction..

---

### Post by starcannon on 2008-08-09
***_[COLOR="Red"][SIZE="5"]FIRST[/SIZE][/COLOR]_***:
**Backup** everything in /home, or at the very least **BACKUP everything** thats important to you.

SECOND:
After, and **ONLY** after you have done the **FIRST STEP**, simply boot from the Ubuntu CD, and then, assuming you have indeed followed **STEP THE FIRST**, start the installer. This time however during the wizard, when it gets to partitioning, choose manual, set a root partition, / , at about 10gb that should be more than enough, set a Swap partition to equal to or double your ram amount(really only super important on a computer that will hibernate). Then give the rest to /home. Continue through the wizard.

P.S. the reason for putting /home on its own partition is so that in the future if you want to do a clean install, re-install, you simply format and label the root "/" partition, don't format but DO label the /home partition, and your not bothered with all the Backup drama.

P.S.S. Step One is THE MOST IMPORTANT STEP, I can not emphasize it enough, ignore it at your risk. If you have valuable personal or professional data on that partition, you should absolutely positively back it up onto a Cd, DVD, external, or other internal hdd before you do anything else!

---

### Post by Aldtjaom on 2008-08-09
I put the cd in, nothing happens, even when i reboot my pc.

---

### Post by Sirron on 2008-08-09
Make sure your CD drive is the first boot device, enter your BIOS settings to check. Also, you might have used a different CD last time, make sure this one definitely works or you might spend all day chasing a phantom hardware problem. *experience*

---

### Post by Aldtjaom on 2008-08-09
I checked my cd drive, its set at the primary boot drive and I'm using the same cd I used to install it. It still isn't installing though.

---

### Post by Sirron on 2008-08-09
To identify if it's the CD or the computer causing the problem, try an old Windows CD, or another OS install CD - just to check if anything happens. Also, listen to your CD drive, you should be able to hear it checking the CD.

---

### Post by zipperback on 2008-08-09
> **Aldtjaom said:**
> I put the cd in, nothing happens, even when i reboot my pc.

Boot your computer, go into the bios, and make sure you have the CD Rom drive set to be the first bootable drive in your system.

Save the bios changes, insert the Ubuntu cd into the cd/dvd drive, and reboot.

It should boot the cd rom.

If not, then perhaps your burned copy is bad.

Can you test your system to see if it will boot some other bootable media?

- zipperback
:popcorn:

---

### Post by Aldtjaom on 2008-08-09
Found the problem, apparently there were two sections I had to change my cd drive to the primary device. Thanks for the help.

---

