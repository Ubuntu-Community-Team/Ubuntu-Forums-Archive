---
title: "/ and /home same disk usage"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by fourthofjuly on 2008-09-22
re-installed ubuntu and restored my home and root files using this guide to get all my settings back... i have a triple boot of XP, Ubuntu & openSuSE...

[http://ubuntuforums.org/showthread.php?t=35087&highlight=system+backup]("http://ubuntuforums.org/showthread.php?t=35087&highlight=system+backup")

conky shows same disk space of 4.97 G / 9.24 GB for / and /home

du command shows something different:

> devang@systemd $ sudo du -sk /
du: cannot access `/proc/7577/task/7577/fd/3': No such file or directory
du: cannot access `/proc/7577/task/7577/fdinfo/3': No such file or directory
du: cannot access `/proc/7577/fd/3': No such file or directory
du: cannot access `/proc/7577/fdinfo/3': No such file or directory
du: cannot access `/home/devang/.gvfs': Permission denied
9673588	/

> devang@systemd $ sudo du -sk /home
du: cannot access `/home/devang/.gvfs': Permission denied
2350144	/home

output of df command:

> devang@systemd $ df
Filesystem           1K-blocks      Used Available Use% Mounted on
varrun                  516880       120    516760   1% /var/run
varlock                 516880         0    516880   0% /var/lock
udev                    516880        64    516816   1% /dev
devshm                  516880        72    516808   1% /dev/shm
lrm                     516880     38176    478704   8% /lib/modules/2.6.24-16-generic/volatile
df: `/home/devang/.gvfs': Transport endpoint is not connected
/dev/scd0              4578364   4578364         0 100% /media/cdrom0



is something wrong with the /proc and ~/.gvfs folders?

please help...

thanks...

---

### Post by vanadium on 2008-09-22
du shows the used space, not the total space. df should list all mounted file systems. However strangely, I do not find any regular disk partition (even not root) in the output of your df command. For your information, this is how mine looks:
```

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             74527228  47447932  23323304  68% /
varrun                  517636       132    517504   1% /var/run
varlock                 517636         0    517636   0% /var/lock
udev                    517636        60    517576   1% /dev
devshm                  517636        12    517624   1% /dev/shm
lrm                     517636     39760    477876   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      74527228  47447932  23323304  68% /home/vanadium/.gvfs

```

You see /dev/sda1, mounted on / as the only disk volume currently on my laptop.

---

### Post by t0p on 2008-09-22
> **fourthofjuly said:**
> 
du command shows something different:




output of df command:






You need to run *du* with root privileges: ie, you should type

```
sudo du
```

You get an easier-to-read output from *df* if you use the *-h* flag (the *h* stands for *"human"*): ie, you should type

```
df -h
```

As for your main concern, I haven't applied my mind to it fully yet.  But I will now. :)

**EDIT:** I concur with vanadium - it is very odd that no directory is shown as mounted at /.  Have you done something out of the ordinary when setting up this filesystem?

To give you some more idea of what I and vanadium would expect to see, I'll show you the output of *df -h* on my system:

```
t0p@ubunty:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   13G  4.3G  75% /
varrun                125M  184K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   44K  125M   1% /dev
devshm                125M   24K  125M   1% /dev/shm
lrm                   125M   39M   86M  32% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       18G   13G  4.3G  75% /home/t0p/.gvfs
t0p@ubunty:~$ 

```

You can see that the first filesystem listed, */dev/sda1*, is shown as mounted on /.  */dev/sda1* is my hard drive - everything else listed is contained in */dev/sda1*.

---

### Post by fourthofjuly on 2008-09-22
well, i had a working ubuntu system with my settings, themes, files ... i deleted these partitions (root & home) & made a fresh installation with the same size as earlier (10G for root & 20G for home)...

i had a working system backup of root (rootbackup.tgz) and home (homebackup.tgz) & using the guide i mentioned above i restored these .tgz files from my / directory using tar...

actually the first time i tried to restore, i accidently restored homebackup.tgz to / folder instead of /home but i terminated midway using Ctrl-C...

---

### Post by fourthofjuly on 2008-09-22
the first time i rebooted after the above, at the time of login, it said it could not locate /home...

i went in failsafe terminal, deleted the home directory and did a fresh restore of /home from my / folder using tar...

---

### Post by amd-64 on 2008-09-22
After restoring home, did you change permissions on your home folder so you can read it without root access privileges. I would do

sudo chown -R username:groupname /home/devang

in your case, replace user and group names with devang if that is what you have.

---

### Post by fourthofjuly on 2008-09-22
not sure, but see if you can make out...

> devang@systemd $ ls -l /home
total 8
drwxr-xr-x 53 devang users 4096 2008-09-22 19:41 devang
drwx--x--x  2 root   root  4096 2008-08-14 05:30 lost+found

actually under "users and groups" devang user is not there! only root user shows...

---

### Post by amd-64 on 2008-09-22
Your permissions are okay for the folder, no guarantee all the files are owned by devang. Going back to your first post, 

du: cannot access `/home/devang/.gvfs': Permission denied

In anycase you can run the chown line and add your user name under "users and groups"

---

### Post by fourthofjuly on 2008-09-22
there is a group devang under "users and groups"...

ok, it gives permission denied...

> devang@systemd $ sudo chown -R devang:devang /home/devang
[sudo] password for devang: 
chown: cannot access `/home/devang/.gvfs': Permission denied

---

### Post by amd-64 on 2008-09-22
did you also create a user devang. You said it was missing
Make sure the user belongs to users group or to devang group.

---

### Post by vanadium on 2008-09-22
* "du" must not be run as a root user
* There is no need to try to change permissions of the .gvfs folder. When running du as a user, you will not see the permission denied error for .gvfs

---

### Post by fourthofjuly on 2008-09-23
system doesn't allow saying user devang already exists...

anyways, i am escaping through the easiest route here, re-installing ubuntu and re-storing my / and /home files...

thank ya all...!!!

---

