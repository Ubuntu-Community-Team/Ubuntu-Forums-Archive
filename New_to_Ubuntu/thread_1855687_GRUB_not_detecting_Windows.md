---
title: "GRUB not detecting Windows"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by QuentinK on 2011-10-06
I posted this in another thread, but I couldn't change the title.
			 		   		 		 		[SIZE=1][SIZE=2][COLOR=Black]I  recently put Linux on one a 10g partition after I messed up the BOOTMGR  for my windows 7. I was hoping that GRUB would be able to detect  Windows 7 and act as a boot manager, but I'm only seeing Linux and the  Memtests on the list, and when I run sudo update-grub, I'm not seeing W7  on the list.
All the files are still there, I just cant run it. Any ideas?[/COLOR][/SIZE][/SIZE]

---

### Post by Rusky on 2011-10-06
Assuming GRUB2 (the default in newer releases), press 'c' to go to a command prompt. Assuming Windows is on the first partition, type ```
set root=(hd0,1)
chainloader +1
boot
``` Adjust the 1 in (hd0,1) to match Windows' partition (the X in /dev/sdaX). You may need to skip a recovery partition or something like that.

If this boots Windows, it means GRUB just isn't detecting it. You can add it yourself by editing /etc/grub.d/40_custom and adding
```
menuentry "Windows" {
    set root=(hd0,1)
    chainloader +1
}
``` Again, fix the (hd0,1) to match Windows' partition. Then run update-grub.

If it doesn't boot Windows (e.g. it bluescreens) you'll probably need to do a Windows repair install and then reinstall GRUB from a Live CD.

---

### Post by Quackers on 2011-10-06
If Windows wouldn't boot before you installed Ubuntu it won't boot after installation.
Have you run ```
sudo update-grub
``` in a terminal?

Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2011-10-07
I've responded in your other thread -- please don't create duplicate threads.  It just makes responding very difficult and confusing.

---

### Post by doobieboobie on 2012-08-12
Someone please help with this report, I'm about to use boot repair to fix my partitions, Windows 7 won't boot...I picked the dual boot option on a Live CD installation of Backtrack 5 instead of "erase disk" I thought it would successfully add both backtrack and windows 7 but instead has caused an error, I've already searched numerous hours on the BT forums, but no help, PLEASE guys I need your assistance very fast.  [http://paste.ubuntu.com/1142517/](http://paste.ubuntu.com/1142517/)

---

