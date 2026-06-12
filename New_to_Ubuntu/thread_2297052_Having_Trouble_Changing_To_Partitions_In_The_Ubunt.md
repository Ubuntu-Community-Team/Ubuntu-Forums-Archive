---
title: "Having Trouble Changing To Partitions In The Ubuntu Terminal"
date: 2015-09-30
forum: New to Ubuntu
---

### Post by brian98 on 2015-09-30
Below is my attempt to change to the mounted partition  /media/brian/Music Drive/ in the Ubuntu terminal but to no avail as you  can see I still can't access the music drive partition.:sad::sad:
What am I doing wrong?
Thank you in advance!
Brian K

```
brian@brian-Lenovo-G770:/$ 
brian@brian-Lenovo-G770:/$ df

df: &#8216;/root/.gvfs&#8217;: Permission denied
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda5       45796992  4454228  38993300  11% /
none                   4        0         4   0% /sys/fs/cgroup
udev             3016088        4   3016084   1% /dev
tmpfs             605356     1184    604172   1% /run
none                5120        0      5120   0% /run/lock
none             3026760       80   3026680   1% /run/shm
none              102400       36    102364   1% /run/user
/dev/sda3       69443740 19703004  49740736  29% /media/brian/Music Drive
/dev/sda2      121496572 28025844  93470728  24% /media/brian/F4EA80D3EA809390
```

```

brian@brian-Lenovo-G770:/$ ls

bin    dev   initrd.img  lost+found  opt   run   sys  var
boot   etc   lib         media       proc  sbin  tmp  vmlinuz
cdrom  home  lib64       mnt         root  srv   usr
```

```

brian@brian-Lenovo-G770:/$ cd /media/brian/Music Drive
bash: cd: /media/brian/Music: No such file or directory
```

```

brian@brian-Lenovo-G770:/$ cd /media/brian/MusicDrive
bash: cd: /media/brian/MusicDrive: No such file or directory
```

```
brian@brian-Lenovo-G770:/$ cd /media/brian/
brian@brian-Lenovo-G770:/media/brian$ ls
F4EA80D3EA809390  Music Drive
```

```
brian@brian-Lenovo-G770:/media/brian$ cd /media/brian/Music Drive/
bash: cd: /media/brian/Music: No such file or directory
```

---

### Post by Geoffrey_Arndt on 2015-09-30
Just trying to decipher & understand your post.  Are you asking why you can't access your music "directory" on a usb-flash stick or other portable media?   

What does the file manager (nautilus) show?   Is the device not showing up where you can navigate to it and manage the files?   Are you wanting to copy the files to your /home/music folder?

What happens if you use a music manager (like banshee or vlc) - - will the scan function display the music files?   If you post a thumbnail from the file manager, of your media directory, maybe we can see if your syntax is wrong (linux is case sensitive).

---

### Post by yancek on 2015-09-30
> brian@brian-Lenovo-G770:/$ cd /media/brian/Music Drive
bash: cd: /media/brian/Music: No such file or directory

Note the second line above from your post.  It is looking for a directory named Music.  You have spaces in the name which won't work in a terminal.  You either need to put quotes around the command:

> cd "/media/brian/Music Drive"

or make directories without spaces.

---

### Post by brian98 on 2015-10-01
I am currently running ubuntu 14.04 and the drive that I seek to explore through the terminal is a sata drive that has two partitions in it. The drives as you can see from the "df" command are mounted and are as follows;


File System           1K-Blocks                Used                     Available           Use%             Mounted on

/dev/sda3                       69443740            19703004            49740736            29%    /media/brian/Music Drive
/dev/sda2                 121496572           28025844            93470728           24%          /media/brian/F4EA80D3EA809390

I am assuming that the "df" command is retrieving drive mount information......
So what I would like to do is be able to, through the terminal, explore the drive or in other words switch to the drive "aka directory" but as you can see from the above attempts I am just getting the following;

brian@brian-Lenovo-G770:/$ cd /media/brian/MusicDrive
bash: cd: /media/brian/MusicDrive: No such file or directory

I can't figure out why the terminal won't let me move to that directory???

Thank you in advance
Brian  K

---

### Post by yancek on 2015-10-01
Did you read my last post?  If the directory is named Music Drive, you need to put quotes around the command.  Or you could rename it to MusicDrive with no spaces.

---

### Post by steeldriver on 2015-10-01
... because 

```

MusicDrive

```

is not the same thing as

```

Music Drive

```

As another poster has noted, when file or directory names contain spaces, you must surround them in quotes to prevent the shell from splitting the name into two "words"

e.g.
```

cd /media/brian/"Music Drive"

```

or
```

cd "/media/brian/Music Drive"

```

(single quotes will also work). Alternatively, you can *escape *the space using a backslash

```

cd /media/brian/Music\ Drive

```

---

### Post by brian98 on 2015-10-01
That's it!!! The secret is out!
Thank you!!!

---

### Post by HermanAB on 2015-10-02
Yup, using uppercase and delimiters inside file and directory names is eeeevull and a major pain in the derrier.

If you are wondering why, try to read someone a file path over a phone.

---

