---
title: "Finding existing files on C drive in Windows when booted into Ubuntu"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by gerald2 on 2013-08-24
Sorry if this question has been asked (many times) before.

I have just installed Ubuntu.  All OK there.  But, how do I find my existing files (WORD, EXCEL, Music, etc.) which I used from Windows 7?  Also the Thunderbird address files (LDIF) which are also on the C drive.   I have both OS installed and select either when the computer boots up, though it defaults to Windows if no choice is made.  If I try to Import addresses in Thunderbird I cannot get to the file.  

Thanks to all for any advice which is forthcoming.

---

### Post by GwL3eNC on 2013-08-24
Hello,

when i use dolphin as file explorer i see my other drives on the right side of the window. 
Ubuntu mount this drives automaticly. Possible you have to mount your drives using 
the mount command or add some line in /etc/fstab

Here you can find information [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
If you have problems just come back.

---

### Post by Impavidus on 2013-08-25
In your file manager (there are several) you should see the available partitions somewhere in the side of the screen (in my case, on the left). They may not have an obvious name. Your windows C partition should be amongst them. Click the partition to mount it and then you can browse it.

Keep in mind that it's not always save to write to the windows C partition. Reading is never a problem.

---

### Post by gerald2 on 2013-08-28
Many thanks for your advice.  I have now found the files.  In the HOME folder there are 2 directories, the first is "System reserved" and 2nd is "309 GB Filesystem".  It is this one which has all the WINDOWS files and I can open them in their various Ubuntu applications, such as LibreOffice.  At the moment I am working from the "try Ubuntu without installing" option.  I hope the files are still there if I install it!

---

### Post by newb85 on 2013-08-28
> **gerald2 said:**
> At the moment I am working from the "try Ubuntu without installing" option.  I hope the files are still there if I install it!

Which files?  The ones on your Windows partition?  Are you planning to install alongside Windows, or over the top of it?

---

### Post by eternal243 on 2013-08-28
> **gerald2 said:**
> At the moment I am working from the "try Ubuntu without installing" option.  I hope the files are still there if I install it!

I'm assuming you are running from a Live USB or CD, and then depending on how you install it you might or might not be able to use all your files. What you need to do is to make sure you are installing with a dual-boot setup, that means you will need to create your partitions manually and not just use the recommended option during the install. But it is not really that hard to do and you should be able to figure it out with help from the Ubuntu Wiki as well as google.

**EDIT: ** If you fail at creating the correct partitions during the install, you might end up overwriting your Windows installation, making it hard and maybe impossible to recover your files. Make sure you backup everything that is important on your Windows drive before attempting the install.

---

