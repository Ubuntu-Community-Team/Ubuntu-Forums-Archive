---
title: "Screwed Up Somewhere: 'grub rescue'"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by ReticentGrace on 2013-10-15
Okay- I'm going to write down exactly what I did and hope for the best, because I am a little bit out of my depth here. I had a computer with both Ubuntu and Windows 7 home on it; I decided I didn't use the linux partition enough on it, so I deleted it, and used a program to add the unallocated space to my Windows 7 partition. It appears, though, that in doing this I've messed up the boot-loader. Now, it won't load windows, and simply has a prompt stating 'grub rescue'. Not only do I have NO clue what that is, but now I can't boot at all into windows.

I just want to be able to boot into Windows 7 again- I know it's there. Any help would be greatly appreciated. ](*,)

---

### Post by fantab on 2013-10-16
So you removed Ubuntu/Linux partitions which has OS on it, right? If true, then you must fix the Windows Boot... you will need Windows Repair Disk, or Windows Install Disc to do so... [**Read Here**]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html").

---

### Post by ReticentGrace on 2013-10-16
I calmed down and fixed it- I used bootrec.exe from the Windows 7 repair command prompt. I think things are going sailingly now- I just panicked! :( No one is comfortable when their computer doesn't start!

---

### Post by fantab on 2013-10-16
I am glad you fixed it.

---

