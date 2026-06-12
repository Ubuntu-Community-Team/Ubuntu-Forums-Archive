---
title: "[SOLVED] gvfs-fuse-daemon - no diskspace left"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by davethomas691 on 2008-07-06
Hey all,  it seems I've run into a problem with my gvfs-fuse-daemon taking up all of my disk space.  I've searched around here and other forums but I haven't been able to find any kind of solution.  Here goes my problem.

I have a single 60gb HDD partitioned as such:
14gb - /
26gb - /home
15gb - Windows XP

I am unable to download anything write now.  There error I am given is "There is not enough room on the disk to save /tmp/iJB7_hwT.deb.part.

Remove unnecessary files from the disk and try again, or try saving in a different location"  When I input df-h into the console, I get

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              14G   14G     0 100% /
varrun               1013M  236K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   68K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda4              26G  1.7G   23G   7% /home
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon       14G   14G     0 100% /home/davidthomas/.gvfs
```

Any ideas? I've downloaded some extra apps, but not enough to fill the 10+gb of extra space I left on the / partition.  I've already tried the sudo aptget autoremove and clean commands as well as emptying my trash.

---

### Post by plucky on 2008-07-07
> Any ideas? I've downloaded some extra apps, but not enough to fill the 10+gb of extra space I left on the / partition. I've already tried the sudo aptget autoremove and clean commands as well as emptying my trash. 


Have you got a backup application running in the background?
Also check your /var/log for any log files getting too big.

try this command ```
sudo find / -type f -size +50000k
``` will search for large files on your disk.

Good Luck

---

### Post by davethomas691 on 2008-07-07
I do use SimpleBackup, but I checked for processes in the System Monitor and didn't find anything relating to that.

The console command did term up some good stuff.  I found some old backup files in the /root/.local/share/Trash/files directory.  Unfortunately, when I try to delete them, they just reappear, presumably because they are being sent to the trash.  How can I dump the files and skip the trash can process?

Thank you in advance for your help!

---

### Post by plucky on 2008-07-07
> **davethomas691 said:**
> I do use SimpleBackup, but I checked for processes in the System Monitor and didn't find anything relating to that.

The console command did term up some good stuff.  I found some old backup files in the /root/.local/share/Trash/files directory.  Unfortunately, when I try to delete them, they just reappear, presumably because they are being sent to the trash.  How can I dump the files and skip the trash can process?

Thank you in advance for your help!


Try ```
gksudo nautilus
``` and empty root trash

or ```
cd /root/.local/share/Trash/files
ls -l
sudo rm <Name of trash file>
```

The first command takes you into the right directory,the second command lists the files in that directory and the third command deletes the file.

[color=red]With both commands,you are in super user mode,so be careful to make sure you are in the right directory before deleting any files,and make sure you only delete the right files.[/color]


Good Luck

---

### Post by davethomas691 on 2008-07-07
gksudo nautilus launches properly, though when I attempt to empty the trash via right clicking on the icon in the nautilus window, it is grayed out.

I get a permission denied error when I try to execute the cd command

----EDIT----

I used gksu nautilus from a live cd and deleted the suspect files.  Problem solved.  Thanks so much plucky!

---

### Post by plucky on 2008-07-07
Well as I was looking for my root Trash file,I couldn't find it where I thought it would be,so I'll now have to go looking for it.



Cheers


:)

---

### Post by PayPaul on 2011-10-09
> **davethomas691 said:**
> gksudo nautilus launches properly, though when I attempt to empty the trash via right clicking on the icon in the nautilus window, it is grayed out.

I get a permission denied error when I try to execute the cd command

----EDIT----

I used gksu nautilus from a live cd and deleted the suspect files.  Problem solved.  Thanks so much plucky!

You were able to access your Ubuntu installation from a LiveCD? I've tried the same command from terminal while in a LiveCD session with no results at all and no ability to delete a 17gb file from the root that is the cause of a similar problem I have.

---

