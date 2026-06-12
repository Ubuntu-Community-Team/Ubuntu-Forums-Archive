---
title: "kernel log daemon error and stalls for 5 mins during startup"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by macvr on 2008-11-02
hi all,

i recently upgraded from ubuntu 8.04 to 8.10

every time i start in the normal mode the splash screen changes to this line>>>
> starting kernel log daemon
chown:changing ownership of 'var/run/klogd': read only file system
mkfifo:cannot create file 'var/run/klogd/kmsg': file exists
chown:changing ownership of 'var/run/klogd/kmsg': read only file system
start-stop-daemon:Unable to open pidfile '/var/run/klogd/kmsgpipe.pid' for writing : read only file system (read only file system)
_

prompt just keeps blinking and nothing happens for **5 mins**, after which i get [[COLOR="DarkRed"]failed[/COLOR]] and the boot continues...

this does not occur in the recovery mode...

how do i correct this... this is driving me crazy...:(

---

### Post by macvr on 2008-11-02
looks like it is a rare error found ONLY 3 such instances via google, one is a french, chinese , german ubuntu forums , all during the upgrade... , they seem to have same kernel log error , they also are able to access via recovery mode... but they dont seem to have a solution!

 so if anyone has any other ideas,???? u'd probably be a genius!

---

### Post by macvr on 2008-11-03
i have filed a bug report>>>
[https://bugs.launchpad.net/ubuntu/+bug/293220]("https://bugs.launchpad.net/ubuntu/+bug/293220")

---

### Post by GunnarKj on 2009-01-01
Had the same problem the following worked for me.

mount -n -o remount,rw /
sudo dpkg --configure -a
sudo dpkg-reconfigure xserver-xorg

---

### Post by macvr on 2009-01-01
> **GunnarKj said:**
> Had the same problem the following worked for me.

mount -n -o remount,rw /




when should i run this command? from the prompt? when it shows error or from the live cd?

is this a permanent solution or do i have to do this every time i start the system?

---

