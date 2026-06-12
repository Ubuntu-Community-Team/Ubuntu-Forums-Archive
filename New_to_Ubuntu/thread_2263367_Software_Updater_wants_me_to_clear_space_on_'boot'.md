---
title: "Software Updater wants me to clear space on '/boot'"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2015-01-31
I am using 14.04 and after getting this message from 'Software Updater':
 
"The upgrade needs a total of 93.4 M free space on disk '/boot'. Please free at least an additional 6,442 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I have run both[HTML] sudo apt-get autoclean[/HTML] and [HTML]sudo apt-get clean[/HTML] with no results.

Can someone help me out here, please.

---

### Post by oldos2er on 2015-01-31
Is /boot on its own partition? ```
df -h
``` You might need to uninstall old kernels to free up some space: [http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by ajgreeny on 2015-01-31
Show the output in terminal of 
**ls /boot | grep vmlinuz**

---

### Post by kindafunnylookin on 2015-01-31
peter@TosTec-Ubuntu-14:~$ ls /boot | grep vmlinuz
vmlinuz-3.13.0-40-generic
vmlinuz-3.13.0-40-generic.efi.signed
vmlinuz-3.13.0-43-generic
vmlinuz-3.13.0-43-generic.efi.signed
vmlinuz-3.13.0-44-generic
vmlinuz-3.13.0-44-generic.efi.signed

peter@TosTec-Ubuntu-14:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  454G   35G  397G   8% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        387M  1.2M  386M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G   23M  1.9G   2% /run/shm
none                         100M   52K  100M   1% /run/user
/dev/sda2                    237M  142M   83M  63% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi

---

### Post by deadflowr on 2015-01-31
What does 
```
sudo apt-get autoremove
```
show?
Does it list those older kernels?
(We can be hopeful, as this would be ideal)

---

### Post by kindafunnylookin on 2015-01-31
peter@TosTec-Ubuntu-14:~$ sudo apt-get autoremove
[sudo] password for peter: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
peter@TosTec-Ubuntu-14:~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
peter@TosTec-Ubuntu-14:~$

---

### Post by deadflowr on 2015-01-31
Do you have anything, like the software updater, or the software center, or synaptic open?
If so, close them(it).

---

### Post by kindafunnylookin on 2015-01-31
Synaptic wasx open, closed now.

---

### Post by deadflowr on 2015-01-31
Now, does the autoremove command show anything?

---

### Post by kindafunnylookin on 2015-01-31
Closing Synaptic did the trick. All updates installed right off. Thank you for the help, it is greatly appreciated.

---

