---
title: "/home/.shadow taking up lots of disk space"
date: 2016-11-21
forum: New to Ubuntu
---

### Post by angusmc on 2016-11-21
Hi

I've recently started using Linux on a Chromebook (acer c720p). All going well so far except that I seem to be using up memory in my downloads directory and I can't work out where this memory is being used up. Using df -h provides the following:

(trusty)angus@localhost:~$ df -h
Filesystem                                                    Size  Used Avail Use% Mounted on
/dev/sda1                                                      11G  8.1G  2.0G  81% /
devtmpfs                                                      938M     0  938M   0% /dev
shmfs                                                         939M   44M  896M   5% /dev/shm
tmp                                                           939M  1.6M  938M   1% /tmp
tmpfs                                                         188M   88K  188M   1% /run
tmpfs                                                         5.0M     0  5.0M   0% /run/lock
run                                                           939M  464K  939M   1% /var/host/dbus
/dev/mapper/encstateful                                       3.1G   94M  3.0G   3% /var/host/timezone
/dev/root                                                     1.2G  1.2G   71M  95% /lib/modules/3.8.11
media                                                         939M     0  939M   0% /var/host/media
/home/.shadow/c8b6b34217db6386a30f9508076548544b186a99/vault   11G  8.1G  2.0G  81% /home/angus/Downloads
none                                                          939M   48K  939M   1% /sys/fs/cgroup


where you can see that there is a filepath /home/.shadow/c8b6b34217db6386a30f9508076548544b186a99/vault which is taking up a lot of memory, but I can't access this file anywhere in order to see what it is and clean it up if possible. It just seems to slowly be increasing in size and it won't be long before I run out of memory because of it. I've spent a lot of time googling to try to work out what I can do here but to no avail. Can somebody help me identify what this filepath is and what I can do about it?

Thanks
Angus

---

### Post by kingneutron on 2016-11-29
--Have you seen these:

[https://github.com/dnschneid/crouton/issues/2527](https://github.com/dnschneid/crouton/issues/2527)

[https://www.reddit.com/r/chromeos/comments/2tkwzh/directories_named_shadow_seem_to_be_taking_up/](https://www.reddit.com/r/chromeos/comments/2tkwzh/directories_named_shadow_seem_to_be_taking_up/)

/ Found by googling " linux home .shadow vault "

---

