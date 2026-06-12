---
title: "~/Bin for Home-brew Scripts"
date: 2018-10-08
forum: New to Ubuntu
---

### Post by electrosteam on 2018-10-08
I started with Lubuntu 17.04, 17.10 and then a new clean 18.04 LTS.

On 17.10 there was a /home/john/bin in which I held a few scripts I had written, there were no system generated files.
No sign of that folder under 18.04.

I need those scripts, so can I simply copy the ~/bin from my 17.10 backup into /home/john ?

John

---

### Post by oldos2er on 2018-10-08
Is the folder name Bin or bin? Linux is case sensitive, so it makes a difference.

I assume by "a new clean 18.04" you did a fresh installation, so did you create a new /home too? If you didn't overwrite your old /home, those files may still exist on your disk(s) somewhere.

---

### Post by electrosteam on 2018-10-08
All lower case.

I cannot remember if I copied /home/john from the backup.
What I did for sure was copy over the /home/john/documents.

I know I took the opportunity of 18.04 to start a new clean system.
Wherever possible I have done a clean install of all my applications, and this has/is causing minor irritations like these scripts.

But it does raise the possibility that a few other things are missing as well.
A quick look shows there are a number missing from the 18.04 /home/john install (boot, casper, .adobe, .disk and others).

I do have two operational problems, the desktop sometimes quits, and I get the occasional total freeze.
Could it be these issues are related to something missing ?

John

---

### Post by electrosteam on 2018-10-09
Copied the backup usb /home/john/bin to the new install.
Found the execute permission on the scripts was not set, so corrected that.
The short scripts with a desktop icon work a treat, just like they did on 17.10. [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

Went back and checked, the usb backup versions are not shown as executable.
But, they certainly worked on the machine.
Is it possible that the copy from the machine to the usb flashdrive stripped the execute permission ?

John

---

### Post by Holger_Gehrke on 2018-10-09
That depends on the filesystem of the flashdrive and the way it is mounted. Most non-Unix file systems - that includes all variants of FAT and NTFS - can't store permission bits and Linux 'fakes' them according to options set while mounting.

Holger

---

### Post by electrosteam on 2018-10-09
Holger,
The usb flashdrive reports as vfat with ~$ df -hTi .

All I did was do a copy for the backup, so your comment would indicate the execute bit was not transferred.

Note that I chose to do fresh installs of all applications for the 18.04, the files copied across were generally personal data, and these few scripts.
Is it important to do something about this in the future ?
But, it is a subject that I will be conscious of in the future.

John

---

### Post by yetimon_64 on 2018-10-11
> **electrosteam said:**
> Holger,
The usb flashdrive reports as vfat with ~$ df -hTi .

All I did was do a copy for the backup, so your comment would indicate the execute bit was **not transferred**....
The executable bit never existed on the file until you saved it on the linux file system for the first time. As it never existed it could never be transferred, rather it was created when you first copied over the file from the FAT file system to the EXT4 file system.

Linux file permissions and the executable bits DO NOT exist on the vfat file system from which the file is copied.
When you mount a Microsoft vfat or ntfs file system under linux it is the mount options in use in linux that appear to show the file as being executable or owned by the user etc.

Regards, yeti.

---

