---
title: "Want to reinstall 12.04, facing partition problems"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by jengyz on 2012-08-04
Hello guys, first of all I want to tell that I searched enough about this subject.


**The problem is**, I had Windows 7 on C:, and Ubuntu 12.04 on D:. Yesterday, I used the system recovery software to get rid of everything on C: and have a fresh Windows 7.

After having Windows 7 installed, **operation system selecting page did not appear and Windows 7 booted directly.** When checked the drive D:, I saw the ubuntu folder. Files were there.

Then to restore the Grub, I followed the instructions on Ubuntu.com with a Live CD. When I started the procedure there were only choices of "install" or "try". 

I clicked on "try" and then I tried to install Grub via commands. However when **I entered "sudo fdisk -l", I saw that, among the partitions, none of them were linux.** Then I tried the further commands in every partition one by one, but failed everytime.

Now what I want to do is, either removing it properly and installing Ubuntu 12.04 back, OR having the Grub back and have my Ubuntu back.

Thanks in advance.

---

### Post by ajgreeny on 2012-08-04
Was your ubuntu install done using wubi the first time?

I know almost nothing about the details of wubi except that it installs ubuntu as a "program" or virtual OS disk inside the windows OS, so maybe your system restore, depending on what exactly you mean by that, has wiped away your first ubuntu OS.

Can you show more details of the output of the fdisk command as that may help sort out what has happened, or better, using the live CD system, click on the boot-info-script in my signature, then download and run the script that you will find details of on that page.  The RESULTS.txt file from that will tell us in great detail what you have on the machine at the moment, and how best to help you.

Paste contents of RESULTS.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by jengyz on 2012-08-04
> **ajgreeny said:**
> Was your ubuntu install done using wubi the first time?

I know almost nothing about the details of wubi except that it installs ubuntu as a "program" or virtual OS disk inside the windows OS, so maybe your system restore, depending on what exactly you mean by that, has wiped away your first ubuntu OS.

Can you show more details of the output of the fdisk command as that may help sort out what has happened, or better, using the live CD system, click on the boot-info-script in my signature, then download and run the script that you will find details of on that page.  The RESULTS.txt file from that will tell us in great detail what you have on the machine at the moment, and how best to help you.

Paste contents of RESULTS.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Exactly, I installed via Wubi. I will do what you said and post the results asap.

---

### Post by oldfred on 2012-08-04
I do not know a lot about wubi. But if your wubi was in a separate NTFS partition that did not change then the root.disk should still be there.

But wubi uses the Windows boot loader to boot. You will need to add the wubi entry to Windows BCD entry. You can do it with BCDedit.

bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by jengyz on 2012-08-04
My brother deleted the Ubuntu folder on drive D: and the folder is gone. I have all my space back taken by Ubuntu. I installed 12.04 **without Wubi**. No problems so far.

Thanks for the help.

---

### Post by Bufeu on 2012-08-04
Just for reminding you, [Linux doesn't have any drive letters]("http://ubuntuforums.org/showthread.php?t=2033188").

---

