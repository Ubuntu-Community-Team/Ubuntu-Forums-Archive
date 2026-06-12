---
title: "redirecting rsync errors to text file"
date: 2012-03-29
forum: Programming Talk
---

### Post by JeremySchubert on 2012-03-29
I am copying *.* from one USB1 to USB2.  If I just drag and drop, I end up having to click on 'skip' or skip all' to jump over errors/files that cannot be copied.  So I want to create a shell script that looks like

> rsync -avz /usbdisk1 /usbdisk2/

Can I add a line that instructs the computer to 
1.  ignore/skip files/folders that can't be copied
2.  pipe the names of those files/directories to a text file

---

### Post by ajgreeny on 2012-03-29
Not sure about the txt file of the errors, but I think you need a trailing / at the end of both source and destination folders, with full pathway, eg
```
rsync -avz /media/usbdisk1/ /media/usbdisk2/ 
```
Perhaps that will stop some of the errors, if not all.

Sorry if I misunderstood you.

---

### Post by papibe on 2012-03-29
Hi JeremySchubert.

> **JeremySchubert said:**
> 1.  ignore/skip files/folders that can't be copied
That is the default behaviour. You can test this by changing the permissions to a sub directory. Rsync will report the error but it will continuing syncing (note that if those disks are ntfs that test won't work. Test that on a ext4 filesystem) 

> **JeremySchubert said:**
> 
2.  pipe the names of those files/directories to a text file
```
rsync -avz /usbdisk1 /usbdisk2/   2>  /path/to/logfile
```

Is that what you need? Let us know if you need more details.
Regards.

---

