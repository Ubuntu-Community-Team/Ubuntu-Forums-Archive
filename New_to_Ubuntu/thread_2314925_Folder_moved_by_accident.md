---
title: "Folder moved by accident"
date: 2016-02-24
forum: New to Ubuntu
---

### Post by neil37 on 2016-02-24
Hi,

I'm running Ubuntu 14.04.3 LTS minimal (x64)
While I was in WinSCP I accidentally dragged a folder into another folder. And I can't seem to see what folder it was exactly.
WinSCP log was not enabled at the time for me to check that so I was hoping someone on here might be able to see if anything is missing.

I spotted a "lib" folder in "lost+found" and thought it might be that. So I put it back at the root. But I'm not 100% sure as I'm new to Linux.

```
drwxr-xr-x 23 root root  4096 Feb 25 00:49 ./
drwxr-xr-x 23 root root  4096 Feb 25 00:49 ../
drwxr-xr-x  2 root root  4096 Feb 25 00:19 bin/
drwxr-xr-x  3 root root  4096 Feb 25 00:19 boot/
drwxr-xr-x 15 root root  4080 Feb 18 20:32 dev/
drwxr-xr-x 85 root root  4096 Feb 25 00:19 etc/
drwxr-xr-x  4 root root  4096 Feb 18 00:42 home/
lrwxrwxrwx  1 root root    32 Jan 21 11:10 initrd.img -> boot/initrd.img-4.2.0-25-generic
-rw-r-----  1 root root   502 Jan 30 00:42 installimage.conf
-rw-r-----  1 root root  7444 Jan 30 00:42 installimage.debug
drwxr-xr-x 20 root root  4096 Feb 25 00:18 lib/
drwxr-xr-x  2 root root  4096 Feb 25 00:18 lib32/
drwxr-xr-x  2 root root  4096 Feb 25 00:18 lib64/
drwx------  2 root root 16384 Feb 25 00:49 lost+found/
drwxr-xr-x  3 root root  4096 Mar 17  2014 media/
drwxr-xr-x  2 root root  4096 Feb 27  2014 mnt/
drwxr-xr-x  2 root root  4096 Mar 13  2014 opt/
dr-xr-xr-x 98 root root     0 Feb 18 20:32 proc/
drwx------  6 root root  4096 Feb 17 22:04 root/
drwxr-xr-x 17 root root   640 Feb 25 00:21 run/
drwxr-xr-x  2 root root 12288 Feb 25 00:19 sbin/
drwxr-xr-x  2 root root  4096 Mar 13  2014 srv/
dr-xr-xr-x 13 root root     0 Feb 18 20:32 sys/
drwxrwxrwt  2 root root  4096 Feb 25 01:17 tmp/
-rw-r--r--  1 root root   244 Feb 18 02:16 tmp.txt
drwxr-xr-x 11 root root  4096 Feb 16 19:59 usr/
drwxr-xr-x 13 root root  4096 Feb  8 20:56 var/
-rw-r-----  1 root root   423 Feb 18 20:17 ventrilo_srv.log
lrwxrwxrwx  1 root root    29 Jan 21 11:10 vmlinuz -> boot/vmlinuz-4.2.0-25-generic
root@Ubuntu-1404-trusty-64-minimal /
```

Can anyone spot anything missing from the folder list above? Or was I right that in fact that "lib" folder should not have been in "lost+found"?

Thank you.

---

### Post by HermanAB on 2016-02-25
Well, you can try ls and sort by date.

Read the man page and look for -c and -d I think.

---

### Post by neil37 on 2016-02-25
Can you explain what that is suppose to tell me please so I can understand what I'm looking at from the output?

Does it show me folders that was there and no longer that have been deleted or moved?

---

### Post by howefield on 2016-02-25
If you are sure it was only the one folder that you moved, then you have probably caught it, your lib folder wouldn't normally be inside the lost+found folder.

You would generally hope that lost+found folder is empty as files are put there as a result of a problem with the file system but in this case it is a fair bet that the lib folder is there because you put it there.

Is the system functioning as it should ?

---

### Post by neil37 on 2016-02-25
Hi,

Seems to be ok. I risked a reboot about an hour ago. The system come back online so I think everything is ok.

Is there no way to enable a basic log system for ubuntu 14.04?
From my understanding there is nothing in place by default that does this?

---

### Post by QLee on 2016-02-25
> **neil37 said:**
> Hi,
Is there no way to enable a basic log system for ubuntu 14.04?
From my understanding there is nothing in place by default that does this?

There are already logs enabled, you just need to learn where they are and how to see them.

This documentation from the Ubuntu community might get you started and help you figure out what questions you want to ask for clarification.[
[Edit: the URL I meant to include] [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by neil37 on 2016-02-25
Hi,

So there in the var/log folder.


Would syslog have logs of folder moves done by WinSCP?
Or would that be another log file?

---

### Post by QLee on 2016-02-25
> **neil37 said:**
> Hi,
  Would syslog have logs of folder moves done by WinSCP?
Or would that be another log file?

I don't know anything about WinSCP, presumably you did that from Windows so if there is a WinScp log it likely would be on Windows. I don't use Windows so I can't help with that.

---

### Post by Geoffrey_Arndt on 2016-02-25
If you access the linux root file system via any standard file manager, you should be able to easily find the missing folder . . . by doing what HermanAB suggested.    In Ubuntu Nautilus (aka Files), there is a "modified" field - - which shows the month/day/year/time the folder was changed.    Also, a standard nautilus search by keyword should find sub-folder names, file names, etc.

---

