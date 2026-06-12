---
title: "usb file transfer"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by spillage2 on 2013-03-02
Hi All,

OK...All of a sudden my comp has stopped allowing me to  transfer largish files to any usb pendrives. The odd thing is that all  the pendrives are fine and work in wdz7 but when I try to transfer say a  250mb file its gets half way and then unmounts the usb drive. If I  remount the drive, format it and then try again the file operation  instantly shows that the same file is half done. So it seems it does not  reset itself back to the start if that make any sense.

I have  also formatted a usb drive on a wdz 7 system and all transfers are fine  on that system. When trying again in mint It allowed me to move some  small music files ok but again nothing large. It then changed the  permissions of all the files on the drive.

I also tried to format it to ntfs but no good.

I  have also noticed that multiple file transfer attempts get screwed up  as I just transfered 6 music file and 3 of them copied in seconds but  again at the halfway point froze.

Looked everywhere for a fix but have no ideas on a fix. Any help and advice would be welcome.



Thanks,

Spill.

---

### Post by cwsnyder on 2013-03-02
I am guessing that you are using Nautilus and have no experience using a terminal.

I have seen reports of this bug using Nautilus and Caja, but not in PCManFM or Thunar, and there is no problem using the terminal **cp** command.  I would suggest using the terminal commands, but if you are only comfortable using a GUI, I would suggest using Ubuntu Software Center to install either PCManFM or Thunar to do this type of copying.

The bug seems to have been introduced in an update from late 2012.  I haven't seen that it has been fixed for moving large files.

Edit: [http://ubuntuforums.org/showthread.php?t=2120952f](http://ubuntuforums.org/showthread.php?t=2120952f) reported a similar problem using command line utilities, so I may be wrong in my suggestions of PCManFM or Thunar, as well.

---

### Post by zrdc28 on 2013-03-02
**  cp /home/filename  /media/sdb1/filename** 

From terminal might work,  There might be a limitation on what size files you can move to a fat16 or a fat32 
partician, it seems that that it is 2 or 4 gb. I just don't remember.

---

