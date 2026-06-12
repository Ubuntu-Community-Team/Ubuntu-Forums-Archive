---
title: "Chrooted xfce4 ubuntu 14.04 stopped working"
date: 2015-05-16
forum: New to Ubuntu
---

### Post by leeko on 2015-05-16
Hi,

I restarted my lenovo yoga II chromebook, and after restart was unable to get into my xfce4 ubuntu chroot. The error message was for X, and after googling I understood it had happened after an update. To fix it, I ran the command:

sudo sh ~/Downloads/crouton -u -n precise

But it also returns an error message:

dpkg: dependency problems prevent configuration of openjdk-7-jre:amd64:
 openjdk-7-jre:amd64 depends on openjdk-7-jre-headless (= 7u79-2.5.5-0ubuntu0.14.04.2); however:
  Version of openjdk-7-jre-headless:amd64 on system is 7u75-2.5.4-1~trusty1.

dpkg: error processing package openjdk-7-jre:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-7-jre:amd64
Failed to complete chroot setup.
Unmounting /mnt/stateful_partition/crouton/chroots/precise...

I haven't been able to figure out how to fix dependency problems in dpkg without being able to enter the chroot. My chrooted ubuntu was installed as Precise, but upgraded from within the chroot to trust 14.04. Please help! 

Thanks in advance for any help you can offer!

Lee

---

### Post by leeko on 2015-05-17
A dist-upgrade did the trick (it was having problems with linux-image-3.10.18). For whatever reason, apt-get dist-upgrade seems to have flushed whatever gremlins were stalling it. 

Thanks anyway

---

