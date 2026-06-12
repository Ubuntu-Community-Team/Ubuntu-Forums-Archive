---
title: "how to open ubuntu image files on windows?"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by jeret on 2013-03-13
hello i have successfully installed ubuntu 12.10 along with my windows 7. I have dual boot both Os working great. I have problem opening ubuntu image files on windows 7. on windows 7 i can see the files / thumbnail but when i open it nothing happens it's like corrupt. i have not tried opening other type of files yet.

Is there a solution for this? please help. Thank you.

---

### Post by Alex.Han on 2013-03-14
What about trying Ext2explore which makes you to access Linux volumes from windows. ([http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/))
Since you have installed two OSes in dual boot mode you won't be able to see each others file system in general.

---

### Post by fantab on 2013-03-14
> **jeret said:**
> hello i have successfully installed ubuntu 12.10 along with my windows 7. I have dual boot both Os working great. I have problem opening ubuntu image files on windows 7. on windows 7 i can see the files / thumbnail but when i open it nothing happens it's like corrupt. i have not tried opening other type of files yet.

Is there a solution for this? please help. Thank you.

What do you mean by "ubuntu image files"? .jpg, .png etc image files saved in Ubuntu/Linux partitions or Ubuntu.iso? 
Is your question about Network sharing?

On a General note, you cannot access your Ubuntu/Linux partitions from Windows. Windows does not recognize Linux filesystem, like ext4. On the other hand Linux/Ubuntu does read and write on Windows filesystems, like NTFS. 
Now, when you create files in Ubuntu that you intend to share and work on in Windows, you MUST save such files on a NTFS partiton. Then you can access such files easily from Windows. Also remember, you should have as simple file names as possible because there could be issues if you use non-supported file labels. Make sure the file extension is supported in both Windows and Ubuntu.

To use a file in Windows I save it on /dev/sda2 (Win_D). To do so I mount the said partition and save the file there. And later it is easily available and accessible from Windows.

---

