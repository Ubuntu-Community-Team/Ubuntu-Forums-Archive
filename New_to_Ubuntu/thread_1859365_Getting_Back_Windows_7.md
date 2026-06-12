---
title: "Getting Back Windows 7"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by djfreedom13 on 2011-10-13
So I install Ubuntu I believe 11.10 and I have been running it for over a month, but the thing is my family doesn't like the fact that they can't use iTunes and other programs like Microsoft office... So they asked me if I can change it back so I download a windows 7 ISO and burned the image on a DVD+R but it won't let me install Windows 7 again (I didn't want to dual boot it because it took too much space on my computer i do not have.) I love Linux but the family disagrees.

Please help...

---

### Post by tasticorp on 2011-10-13
Get a proper W7 cd. If you have a windows 7 license any cd appropriate to that version will do

---

### Post by djfreedom13 on 2011-10-13
I was hoping it didn't have to come to that because now i have to look for it through millions of CDs but thanks for the quick reply... much appreciated

---

### Post by djfreedom13 on 2011-10-13
Is there a way to system restore or something... since it was running windows vista when I bought it.

---

### Post by Madvil on 2011-10-13
Nope, I'm afraid not. System restore works only for when there is a partition with data.

---

### Post by KingYaba on 2011-10-14
> **djfreedom13 said:**
> Is there a way to system restore or something... since it was running windows vista when I bought it.

You can make system recovery images but you would have needed to have done that when you were originally running Windows. Your only options, at this point, is to do a clean install of Windows. Since you like Linux, is your HD space so small you can't dedicate at least 10GB to Ubuntu? Just a thought. :p

And when you say it won't let you install Windows 7, what do you mean? You're going to have to format your hard drive (which erases your data) to NTFS in order for Windows to install. You can boot up with the Ubuntu live CD and use GParted to format. Make sure you backup everything you want to keep.

---

### Post by Sisyphe.anxieux on 2011-10-14
PC manufacturers these days don't provide recovery medium to customers. Instead, they let you set up a hidden recovery partition at the very first boot. Use GParted or any other partition software to make sure you still have the partition on your hard drive. If so, make the partition bootable and reboot your PC. You will be able to go into the recovery solution.

If not, the only way you can go back to Windows 7 is doing a clean install.

---

### Post by madjr on 2011-10-14
> **djfreedom13 said:**
> So I install Ubuntu I believe 11.10 and I have been running it for over a month, but the thing is my family doesn't like the fact that they can't use iTunes and other programs like Microsoft office... So they asked me if I can change it back so I download a windows 7 ISO and burned the image on a DVD+R but it won't let me install Windows 7 again (I didn't want to dual boot it because it took too much space on my computer i do not have.) I love Linux but the family disagrees.

Please help...

just a thought:

i use **microsoft web office** right from my **Hotmail / skydrive** account.

[http://explore.live.com/windows-live-hotmail-microsoft-office](http://explore.live.com/windows-live-hotmail-microsoft-office)
[http://explore.live.com/skydrive](http://explore.live.com/skydrive)

why not do the same?

i dont miss "offline" office anymore, neither my dad, etc..

start getting use to the idea, which is more convenient, works everywhere, collaborate and **no need to install anything**, and soon almost everything will be online/web-based in the short / mid term.

also libreoffice lets you save in .doc for those with legacy msft offices. You can setup "**save to .doc**" by default in options


ps. you can also quickly setup something like windows XP on **virtualbox** for the fewer and fewer occasions you "really" need those things.

---

### Post by Rubykuby on 2011-10-14
iTunes appears to work in wine, if that helps.

---

