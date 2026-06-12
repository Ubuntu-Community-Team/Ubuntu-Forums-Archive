---
title: "Trouble accessing Windows partition"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by Myfathersheart on 2014-01-12
I installed Ubuntu a few years back, and messed around with it a little, but I am just now coming back.  Consider me a 2 day old Ubuntuee.

I am trying to access my Windows files in Ubuntu 12.04.  I Google the problem, and found a tutorial on wikihow ([http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu)).  

However, when I get to step 6 I get this error:

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.


Now, I am stuck. 

All help is appreciated! :D

---

### Post by zeusturtle on 2014-01-12
May be a stupid question and I am also a young 'ubuntuee' like you; however, are you attempting to access these files via nautilus or cli?

---

### Post by Myfathersheart on 2014-01-12
I am not. I am in the terminal.

---

### Post by zeusturtle on 2014-01-12
Can you access the Windows partition via Nautilus?

---

### Post by westie457 on 2014-01-12
@Myfathersheart

One quick question, the last time you used Windows did you shutdown or put to computer to sleep?

---

### Post by Myfathersheart on 2014-01-12
I did a restart to leave Windows and then entered Ubunutu.

Windows was installing an update, and required a restart. So, maybe that has something to so with it.

---

### Post by westie457 on 2014-01-12
Very probably. Let Windows finish installing the updates, shut down Windows then reboot into Ubuntu and run through the tutorial you tried earlier.

Let us know if successful or if it fails post the error message if different from the first one.

---

### Post by Myfathersheart on 2014-01-12
Thanks westie457.  I am letting Windows do the updates. I will try again in the hour and get back to you.

---

### Post by Myfathersheart on 2014-01-12
Sorry, it looks like I won't be able to get to it tonight. My computer is doing 120+ updates and its taking too long.

Need to go to sleep. I'll try again tomorrow.

---

### Post by slaytons on 2014-01-12
In terminal, what is the output of 

mount

---

### Post by Mark Phelps on 2014-01-13
What Windows version is it? Asking because if it is Win8, when you shut it down, it automatically goes into a new form of hibernation which keeps the partitions mounted even when you are not using Windows.

---

### Post by dnemcanin2 on 2014-01-13
For real shut down Windows 8 you must open CMD (run -> cmd <enter>)
write shutdown /s /t 0 <enter>
After that start your Ubuntu and try to mount Windows partition. 
This is because Win8 with shut down goes to hibernate and filesystem is in use.

---

### Post by Myfathersheart on 2014-01-15
Ok, I have let windows finish it's updates, and I tried the wikihow again.  Followed is the result, and I am pasting the output of mount for slaytons too.

root@ubuntu:~# mount -t ntfs /dev/sda2 /mnt/windows -o "umask=022"
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
root@ubuntu:~# mount
/dev/loop0 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/ransomed_son/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ransomed_son)

---

### Post by Mark Phelps on 2014-01-15
> Ok, I have let windows ...But, you have not told us what Version of Windows.  That's important.

---

### Post by Myfathersheart on 2014-01-15
Sorry, I am using Windows 7. 

I didn't see your post before I posted mine.

---

### Post by plurga on 2014-01-15
type 

#fuser -km /dev/windows_partition and after that issue again step 6 from u tutorial !!

---

### Post by Myfathersheart on 2014-01-17
ignore this

---

### Post by Myfathersheart on 2014-01-17
flurga, that doesn't seem to work for me. I researched fuser some and found this.

[http://ocaoimh.ie/2008/02/13/how-to-umount-when-the-device-is-busy/](http://ocaoimh.ie/2008/02/13/how-to-umount-when-the-device-is-busy/)

I have tried these commands too, but they don't seem to work either. Here is a paste of me trying to troubleshoot the problem

ransomed_son@ubuntu:~$ #fuser -m dev/sda2
ransomed_son@ubuntu:~$ fuser -m dev/sda2
ransomed_son@ubuntu:~$ sudo -s
[sudo] password for ransomed_son: 
root@ubuntu:~# fuser -m dev/sda2
root@ubuntu:~# unmount dev/sda2
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
unmount: command not found
root@ubuntu:~# #unmount dev/sda2
root@ubuntu:~# mount -t ntfs /dev/sda2 /mnt/windows -o "umask=022"
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
root@ubuntu:~# # fuser -m dev/sda2
root@ubuntu:~# /dev/sda2: 538
bash: /dev/sda2:: No such file or directory
root@ubuntu:~# #fuser -m dev/sdc1
root@ubuntu:~# dev/sdc1: 538
bash: dev/sdc1:: No such file or directory
root@ubuntu:~# dev/sdc1 538
bash: dev/sdc1: No such file or directory
root@ubuntu:~# #fuser -km /dev/sda2
root@ubuntu:~# #fuser -km /dev/windows_partition 
root@ubuntu:~#

---

