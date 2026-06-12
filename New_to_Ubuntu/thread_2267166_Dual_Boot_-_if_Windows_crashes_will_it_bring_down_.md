---
title: "Dual Boot - if Windows crashes will it bring down Ubuntu as well?"
date: 2015-02-27
forum: New to Ubuntu
---

### Post by penny3 on 2015-02-27
I have installed Ubuntu as a duel boot system. I bought my laptop used with Win 8.0 and upgraded to Win 8.1. I had a niggly suspicion that turned out to be correct in that the Windows 8.0 was ... well, not a legal copy as I started to get warning messages popping up a few days ago on Windows about license expiring, update license application, etc. and, from my research, this all seems to indicate unauthorized version of Windows. My question is ... if Windows stops working/crashes, will this affect my Ubuntu install at all? I created separate partitions for Ubuntu and Swap but, as I am totally ignorant of all things computer-ish, I don't comprehend if Ubuntu is still sharing some sort of Windows stuff or if it is absolutely and totally stand-alone. Also ... am I able to wipe the whole Windows crap off my computer now? 

Thank you for your answers.

---

### Post by yancek on 2015-02-27
It should not have any effect since they are totally separate operating systems on different partitions.  One thing you might do is boot Ubuntu and google boot repair, go to the site and download it and select the option to create bootinfo summary.  You could post that here and someone should then be able to give you a more detailed answer.  Linux and windows don't rely on each other, they are separate and no Linux system needs anything windows to run.

---

### Post by Jakey_TheSnake on 2015-02-27
If you don't need any of your own files from your Windows partition then you can wipe it, yes.

---

### Post by penny3 on 2015-02-27
Thanks for your answers! I now have some more peace of mind. I think I will do that bootinfo summary as suggested and post it here just so I can get some feedback if everything looks okay. Not being a computer technical person at all, it was quite a challenge for me so would be good to know if there is anything glaringly wrong with my installation. I assume not as it appears to be working just great but confirmation would be a bonus. So far I am loving the look and feel of Ubuntu!

Once I figure out how to get this boot information, I will post it in a separate thread.

---

### Post by JeQhdMD on 2015-02-28
There may be some risk (albeit low) in removing Windows entirely from your system . . . . depending on if you have a newer machine running UEFI (Unified Extensible Firmware Interface,  a replacement of standard BIOS).    

If your PC is pre-2010 vintage, no problem to remove all vestiges of Windows.   After that time however, things have changed and during the boot up process - the firmware on some PC's (esp. certain HP, Toshiba models) looks for certain files that can be missing if you delete all windows partitions.    

If space is not a major issue, just leave it and update it 3 or 4 times a year with the usual security and bug updates.    Also, you may sometime get and use a device that is only supported via the Windows OS (such a the Garmin Nuvi GPS & updating your maps).

---

