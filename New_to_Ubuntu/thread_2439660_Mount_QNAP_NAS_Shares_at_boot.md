---
title: "Mount QNAP NAS Shares at boot"
date: 2020-03-30
forum: New to Ubuntu
---

### Post by Steven_Wittwer on 2020-03-30
I am trying to auto mount some smb shares from my QNAP NAS, and I can't get it to work.  Running Ubuntu 19.10.  I can mount them fine, it just doesn't work when I put it in the fstab file.  Typical error is permission denied, or path doesn't exist (depending on how I do it).  Can anyone point me in the right direction?

---

### Post by TheFu on 2020-03-30
Perhaps if you posted the fstab line someone might be able to help?

---

### Post by Steven_Wittwer on 2020-03-30
Here is one of many variations that I have tried (this one is from the Ubuntu Wiki):

//10.1.0.140/TV/TV /media/cheweytv cifs credentials=/home/muzicman0/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

muzicman0@MrLuntz:~$ sudo mount -a
mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)
muzicman0@MrLuntz:~$ cd /media/cheweytv
muzicman0@MrLuntz:/media/cheweytv$ 

You can see from above that /media/cheweytv does in fact exist.  

I also tried specifying the username and password, but then I get a directory doesn't exist.

BUT, if I do:

sudo mount -t cifs -o username=muzicman0,password=MyPassword //10.1.0.140/TV/TV /media/cheweytv 

straight from terminal, then it works fine.

---

### Post by TheFu on 2020-03-30
.smbcredentials file is 3 lines.
```
username=thefu
password=the-raw-password

```
Always leave a blank line at the end of any Unix config file.  Not all parsers check for both EOL and EOF when reading each line.  My credentials files are owned by root with 600 permissions and stored in a directory owned by root.

The mount command that worked, didn't specify the sec=ntlm, could that be the issue?

My actual fstab 
```
//172.22.22.14/D     /misc/D     cifs x-systemd.automount,x-systemd.idle-timeout=600s,sec=ntlmv2,iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials    0     2
```

This mounts a win7 share using the systemd-automounter.  That's why the sec= and vers= are there in mine.  On your system, if the direct mount command works perfectly, you don't need those options.
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) has more details like which services need to be restarted, if you go with the systemd method. it isn't obvious.

---

### Post by Steven_Wittwer on 2020-03-30
GOT IT!  I had 2 problems actually, the credentials file had the wrong password (doh!), and the fstab line was clearly wrong.  I copied yours, and the error was thrown on the uid=tf ("tf" was an invalid something or other), so I changed uid to 1000 and gid to 1000.  not sure really what those are, but it is working now.  and it appears that I have R/W permissions, so that is good.  My final fstab line was:

```
 //10.1.0.140/TV/TV     /media/cheweytv     cifs x-systemd.automount,x-systemd.idle-timeout=600s,sec=ntlmv2,iocharset=utf8,rw,vers=2.1,uid=1000,gid=1000,file_mode=0664,dir_mode=0775,credentials=/home/muzicman0/.smbcredentials    0     2
```

Thanks a ton!  If I should change the UID and GID values, please let me know.

---

### Post by TheFu on 2020-03-31
Glad you got it working. BTW, if your NAS supports NFS, that would likely be faster. Plus Unix permissions would work for all the files and directories.  Unix to Unix storage really should use NFS.

thefu = tf.  Samba allows either the username/groupname or the uid/gid to be used.  

if you type "id" on a terminal, the numbers will be displayed.  Almost always, on every Unix system, it is the numbers that matter for permissions, not the name/group.  There are some interesting side effects because of that flexibility, but not on-topic here.

Because you are using automount now, you'll see that the storage gets mounted on-demand, automatically and after 5 min of not being used, it gets unmounted automatically.

if this is solved, please use the _THREAD TOOLS_ button to mark it that way.  Help the community not waste time.

---

