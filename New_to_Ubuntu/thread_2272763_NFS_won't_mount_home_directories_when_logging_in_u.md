---
title: "NFS won't mount home directories when logging in using GUI"
date: 2015-04-08
forum: New to Ubuntu
---

### Post by acpuck1 on 2015-04-08
Hey all. I have a strange problem that has popped up suddenly. I oversee a linux lab that uses a server for network logins and mounts the home directories. This has worked fine for years. Over spring break, we had a scheduled power outage. All machines were shut down properly. When everything came back up, the workstations in the lab would not log in. They show a log in screen, you enter your network username and password and the login screen goes away. Sometimes it shows your wallpaper but it never loads the Unity desktop. If I pre ctl+alt+F2, I am able to log in with full functionality using the terminal. Upon further testing, I have found that if you change fstab to mount the home directories somewhere that is now /home, the machine will boot and mount properly. I have been going through log files and can't seem to find any abnormalities. 

Anyone have any idea what my problem is here? I have tried imaging the computers with a known good image that worked before spring break but it sees the same behavior. Please let me know if you need any of the log file output. Thanks in advance.

---

### Post by dino99 on 2015-04-08
there are some nfs-utils  bugs around   [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bugs?orderby=-date_last_updated&start=0](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bugs?orderby=-date_last_updated&start=0)

maybe a systemd related issue; try to boot with upstart instead, to let you know

---

### Post by acpuck1 on 2015-04-08
Thanks for the quick reply 9d9!

After some tinkering I decided to stop forcing nfsv3. I just took the "vers=3" out of fstab and that worked for some reason.

---

