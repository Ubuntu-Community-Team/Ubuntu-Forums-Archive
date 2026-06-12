---
title: "Installing on eeepc from USB - admin permissions?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by rikc on 2008-09-04
my Eee PC 1000h arrived in the mail today, and I'm thrilled to start playing with it.  I went to install Ubuntu 8.04 using Unetbotin, and got what seems to be a fairly common error: 

The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

I tried to install multiple times and got the same error.  I went to see if I couldn't manually partition the drives, but I wanted to play it safe and went back.  Apparently I wasn't safe enough, because when I tried to reboot the eee I could not boot back into Windows.  Oops :|

I then made a bootable USB drive and went to install Ubuntu with that, and I'm getting the same error.  I found a page [here](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908) that suggests I can edit /lib/partman/commit.d/30parted to fix it, but since I'm logged in to the live disc I am unable to edit that document.

My question is - is there a way I can give myself admin permissions on the live disc so I can edit that file?  Is there a better way to get past this?

Thanks for the help :)

---

### Post by rikc on 2008-09-04
Checking in other threads about partition/installation issues, would changing the partitions in GParted help me out?  If so, what should I do?

---

### Post by ds[de] on 2008-09-04
> My question is - is there a way I can give myself admin permissions on the live disc so I can edit that file?


With your live CD account you can use 'sudo' to perform tasks that require superuser status.

Fire up a terminal and type 
```
gksu gedit
```
for a texteditor which will let you edit said file.
After that, just save & exit gedit.


Regards,
ds[de]

---

### Post by RedPandaFox on 2008-09-04
Whenever I have problems with partition permissions, I go back to my PCLinuxOS live disk and go in root, gives permissions for anything on live disk, including existing partitions (on everything iv tried anyway)

---

