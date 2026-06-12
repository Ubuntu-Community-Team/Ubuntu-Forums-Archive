---
title: "having shut-down errors and system errors"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by jjclonker on 2013-12-08
When I try to shut-down my commputer stays in the ubuntu shut-down loading screen and never shuts-down, I even left it over night to see if it would and it didn't.

So I have been shutting down my system with the manual shut-down button, which is not good on the commputer.:(

I also have been getting "System program problem detected" errors that don't seem to do anything, but get very anoying.

---

### Post by jdeca57 on 2013-12-08
> **jjclonker said:**
> 
So I have been shutting down my system with the manual shut-down button, which is not good on the commputer.:(

I also have been getting "System program problem detected" errors that don't seem to do anything, but get very anoying.

Actually shutting down the computer manually isn't bad for the computer, only for the file system and your data. 
But the first thing that springs to mind (aside from the question what OS version and what computer, is it a virtual environment or not) is did you do an upgrade?
You know, in a terminal
sudo apt-get update
sudo apt-get upgrade

---

### Post by Bashing-om on 2013-12-08
jjclonker; Good afternoon ;

As much as it can be when your system is problematic !

As there is insufficient info at this time to make a guess, may I suggest to run a file system check 1st to preclude file system problems ?

#From liveCD so everything is unmounted, swap off if necessary, change example shown with partition sda1 to your partition(s);
To see the partitioning: Terminal code:
```

sudo fdisk -lu

```
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required; This terminal command as a 1st approximation;
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see:
```

man e2fsck

```
```

sudo e2fsck -f -y -v /dev/sdb1

```

Post back the output if errors are detected. We will give our best advise !

[INDENT][INDENT]gotta start gathering info somewhere
[/INDENT][/INDENT]

---

### Post by asus-user on 2013-12-08
> **jjclonker said:**
> When I try to shut-down my commputer stays in the ubuntu shut-down loading screen and never shuts-down, I even left it over night to see if it would and it didn't.

Please provide some informations about your ubuntu version.
in any case try to run this command from terminal:
```
shutdown -h now
```
this is supposed to shut the system down immediately.

---

### Post by andrej1741 on 2013-12-08
Hello**, jjclonker.** Which version of Ubuntu do you use? How do you shut-down PC?
Try to open terminal and
```
sudo shutdown -h now
```
If it will write some errors, paste it here.
Or you can try
```
dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```
If it will not turn off your PC, write about it here.
PS
Sorry, for my bad English.
PPS
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by jjclonker on 2013-12-09
[**[COLOR=#000000]jdeca57[/COLOR]**]("http://ubuntuforums.org/member.php?u=275746"): Your guess is right, all the problems seem to happen right after I update my system.

asus-user: My ubutnu version is 12.04.

Bashing-om: Sorry for once I'm not sure I understand your instructions?:confused:   Are you wanting me to put in my ubuntu CD and boot from CD then input these commands?


Question: Is ubuntu 13 more stable?

---

### Post by jjclonker on 2013-12-09
I am going to re-install ubuntu 12.04 and start from there if I run into more problems I will post them here.:-\"

---

### Post by asus-user on 2013-12-10
> **jjclonker said:**
> 

Question: Is ubuntu 13 more stable?

No, it is not.
for more details to understand the difference between Ubuntu versions see: 
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by jjclonker on 2013-12-15
Thanks asus-user I will stick with ubuntu 12 then!

---

### Post by jjclonker on 2013-12-15
I re-installed ubuntu 12.04 and updated it and it worked no shut-down errors!! The updates must have corupted the first 2 times I updated my system. So it's SOLVED!!! :biggrin:

---

### Post by Bashing-om on 2013-12-15
jjclonker; Good Deal !

If at first you do not succeed ->
[INDENT][INDENT][INDENT]try again (sky diving excepted)
[/INDENT][/INDENT][/INDENT]

---

