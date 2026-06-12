---
title: "Profile-sync-daemon"
date: 2012-02-07
forum: Programming Talk
---

### Post by Psycho Game on 2012-02-07
Hello everybody.

A first comment I want to make is that I didn't program this script myself.
I just ported some scripts from Arch Linux to Ubuntu, so did minimal changes to the actual program script, only the boot script.
This script solves the problem of always having to execute some commands to synchronize the browser profiles to RAM.

The description on the Arch Linux wiki is:

Running this daemon is beneficial for two reasons:
- Reduced wear to physical discs
- Speed
Since the profile(s), browser cache, etc. are relocated into tmpfs, the corresponding onslaught of I/O associated with using the browser is also redirected from the physical disc to RAM, thus reducing wear to the physical disc and also greatly improving browser speed and responsiveness. The access time of RAM is on the order of nanoseconds while the access time of physical discs is on the order of milliseconds. This is a difference of six orders of magnitude or 1,000,000 times faster.

Link: [https://wiki.archlinux.org/index.php/Profile-sync-daemon](https://wiki.archlinux.org/index.php/Profile-sync-daemon)

Before installing the debian file you have to add one line to you're fstab file. The line is:
tmpfs /tmp     tmpfs defaults,noatime,mode=1777 0 0

Link to the debian file: [http://dl.dropbox.com/u/58201974/profile-sync-daemon.deb](http://dl.dropbox.com/u/58201974/profile-sync-daemon.deb)
Source files: [http://dl.dropbox.com/u/58201974/profile-sync-daemon.tar.gz](http://dl.dropbox.com/u/58201974/profile-sync-daemon.tar.gz)
**_After installing you need to edit the /etc/psd.conf file, and add at least one user to the list._**

I hope some people are willing to test this script themselves. When you discover some bugs feel free to mail me or leave a comment on this forum.

Greetings Psycho Game

---

### Post by Neva on 2012-02-08
Tested on Aspire One with Ubuntu netbook remix 10.04.

Works like a charm, both browsers (firefox and chromium) are swift and responsive. :D

The aspire has upgraded ram capacity too, from the original 512MB to 1,5GB so tmpfs fits there just fine.

---

### Post by Psycho Game on 2012-02-08
Thank you for you're reply.
I'm glad this program works for you.
Hopefully some other ubuntu users will also benefit from these scripts.
With chromium theres also one other tweak which is adding: --disk-cache-dir=/tmp/cache to the end of the chromium-browser command in the .desktop file and preferred applications.
This will speed up chromium even more by placing the cache folder in RAM. Only this cache will be emptied every time the computer reboots.

Greetings

Psycho Game

---

### Post by broken pipe on 2012-04-01
you're great!! i'm using it under arch and now under ubuntu too! do you know any solution to make it work within an encrypted home folder (encryptfs, no full luks partition encryption). best regards!

---

### Post by Shishimaru on 2012-04-17
Ubuntu doesn't have rc.conf and the command rc.d doesn't work... what should I do? For now I have created the first file and "seems" that it works, but I'm not sure and I'm neither sure about the commands to sync, stop and start the daemon.

---

### Post by broken pipe on 2012-04-20
just install the deb file from the first post. the package has been adjusted for ubuntu. make sure that you entered your username in the config file.

/etc/init.d/psd sync
/etc/init.d/psd start
/etc/init.d/psd stop

---

### Post by kyklops on 2012-05-01
Doesn't work very well for me. 
On startup the browsers profiles don't get loaded on RAM, so when I try to start Firefox it says it don't find the profile folder. (Indeed, the folder is not present in /tmp.) 
What I have to do is to stop psd and start it again. Then the folder /tmp/user-mozilla appears and I can start Firefox.

---

### Post by Mangus on 2012-05-04
It works very well for me.
The only "problem" is that now the sistem has become a lot slower at boot/login for it has to load the profile in cache.
But at the end firefox is faster and with a lot less disk access.

---

### Post by khosra on 2012-05-07
Thank you for posting this. It works very well both on Ubuntu 11.10 and 12.04.

---

### Post by kyklops on 2012-05-16
I removed psd via apt-get but I cannot start Firefox anymore because profile is missing (it says). (It probably still looks for the profile folder in /tmp.) How can I solve the problem?

---

### Post by bizz101 on 2012-09-03
Thanks for this deb! Works perfect on 12.04 on several computers.

---

### Post by slonlt on 2012-10-28
Works fine on 12.10 ;)

---

### Post by graysky on 2012-11-05
Thanks for porting it to Ubuntu.  I just released version 4.11 which has come a long way since version 3.0 which you have built in that deb.

[https://github.com/graysky2/profile-sync-daemon](https://github.com/graysky2/profile-sync-daemon)

---

### Post by graysky on 2013-02-03
Almost a year later and we are on v5.12.  Do you plan to update your deb package on a regular basis?

---

### Post by graysky on 2013-02-13
Finally took the law into my own hands and spun-up a PPA that will stay nice and fresh.  Please edit your first post with this info and thank you for spearheading the packaging effort!

```
$ sudo add-apt-repository ppa:graysky/utils
$ sudo apt-get update
$ sudo apt-get install profile-sync-daemon
```

---

