---
title: "Problem with my second HDD"
date: 2018-01-07
forum: New to Ubuntu
---

### Post by mac187 on 2018-01-07
Hi people !

I have Ubuntu 16.04 installed alongside with Windows 10.

On my Intel HDD i have 2 partitions, one with ubuntu and one with windows.
Then i have another Samsung HDD, here i store all my projects, media and etc.

I ran this command -> sudo ntfsfix /dev/sda1 , and i can now acsess my hdd without getting error message -> "Unable to acsess hdd "bla bla volume"

But then i have this issue -> Every time i reboot Ubuntu, without logging to Windows, just rebooting Ubuntu, i see the HDD on my "Files" user interface, i click in there and viola i have acessed my HDD. 
BUT.. before i do that i check if i can acsess my hdd from terminal and type this -> /media/username , i cant find my HDD.

BUT THEN , when i dont find it in terminal, i go into "Files" user interface, click on my hdd, i see all my folders, THEN i go to terminal and voila there is it on -> /media/username/ ..

So my problem is, how can i fix so i can acsess in terminal without go into "Files" user interface , click on my hdd, and then i can acsess from terminal.

Was i clear or do i need to specifiy more ?

Thanx for all the help !

---

### Post by oldfred on 2018-01-07
Did you label your partition(s) or do you end up seeing the very long UUIDs?

I have a 64GB flash drive plugged in, so I labeled the two partitions.

```
fred@Z170N:~$ cd /media/$USER
fred@Z170N:/media/fred$ ls
data64  xenial64
fred@Z170N:/media/fred$ 
#or
fred@Z170N:/media/fred$ ll
total 16
drwxrwxr-x+  4 fred fred 4096 Jan  2 19:38 ./
drwxr-xr-x   4 root root 4096 Jan 31  2017 ../
drwxrwxr-x  15 fred fred 4096 Jan  2 10:48 data64/
drwxr-xr-x  24 root root 4096 Dec 13 12:07 xenial64/

```

---

### Post by Dennis N on 2018-01-07
In the terminal, the partition on another disk needs to be mounted to see it or access it. The file manager shows unmounted partitions as well as mounted ones in the side pane.

Once you click on the icon of an unmounted partition in the file manager, it gets mounted and then is accessible from the terminal as well.

---

### Post by leunam12 on 2018-01-08
Basically you want the hard drive to be mounted at boot time. To do that you have to modify your 
/etc/fstab file and specify the drive that you want to mount at boot time or you can use the Disks 
utility if you prefer a GUI method.

[https://askubuntu.com/questions/966706/17-10-how-to-auto-mount-drives-on-startup](https://askubuntu.com/questions/966706/17-10-how-to-auto-mount-drives-on-startup)

---

### Post by mac187 on 2018-01-09
leunam12 , thanx ! That helped me! Thanx a lot !

---

### Post by leunam12 on 2018-01-09
You are welcome.

---

