---
title: "Automatic file system check failed- libext2fs.so not found"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by mobio on 2008-08-09
Hi, 

I have problem that I can't solve. I tried different things it seems they don't give result. 

On the old laptop IBM think pad t23 of my gf I installed Kubuntu 7.04. I didn't want to update it to new version, since I had 
problem with graphic card driver and I had problems with graphic drivers when updating Kubuntu versions on other laptop so I decided to stick to Kubuntu 7.04. I also have windows partition there that came originally with laptop.
Ok so what is the problem? Recently after she rebooted her laptop Kubuntu failed to start, giving the following error 

fsck.ext3: error while loading share libraries : libext2fs.so.2: cannont open share object file: No such file or directory
fsck died with exit status 127

*An automatic file system check(fsck) of the root filesystem failed. 
A manual fsck should be performed in maintenance mode with root filesystem mounted in read-only mode. 
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started. ....

Than it tries to start maintenance mode but it gives me bunch of bash errors, like bash: no job control in this shell
bash: groups: command not found etc.
and finally it sends me to some kind of prompt mode # where none of the command works except fsck, but it again give me the same message like fsck.ext3: error while loading share libraries : libext2fs.so.2: cannont open share object file: No such file or directory.

What I tried?
I rebooted Kubuntu using live cd and doing e2fsck -f /dev/sda3 (sda3 is where my Linux is installed). This gave me few errors that I fixed, but than when I restarted system I again got the same error message.
Somehow I managed to switch from this mode to tty1 (by typing reboot in this "prompt mode", and than login screen showed up so I quickly typed adimin login, and I managed to enter linux in text mode(it also had $ instead #). Than I browsed trough directories, and I managed to go to lib folder and I tried sudo nano /lib/libext2fs.so.2 but the file was completely empty when opened like this. 

Also I tried to boot in Windows to see if Hdd is dead, and it seems it is working OK. 

So I don't have clue what to do, and since she has some important data that she didn't backup (I told her to do so, but you know...) and since I had problems setting up graphic driver and wireless driver than I would like to save the current installation if it is possible, rather than reinstalling from scratch. So I would highly apreciate if anyone has any idea how to help me? Please... 

Thank you in advance.

---

### Post by llamakc on 2008-08-09
```

ken@llamakc 08:25:03:~$ dpkg -S libext2fs.so.2
e2fslibs: /lib/libext2fs.so.2
e2fslibs: /lib/libext2fs.so.2.4

```

The package "e2fslibs" contains the file you need. Try reinstalling that package.

---

### Post by wpshooter on 2008-08-09
IMMEDIATELY, if not sooner, get the hard drive diagnostis software from the hard drive manufacturer's website and test the integrity of your hard drive by running a LONG-TERM complete hard drive testing.

If possible might want to backup any important information ASAP, even before running hard drive diagnostics.

---

### Post by mobio on 2008-08-10
I decided to go for reinstalling library files. But the problem is that I downloaded library but there is no way to copy it on the "problematic" laptop

---

### Post by mobio on 2008-08-10
So I sloved the problem. In the windows partition I installed the driver so I could mount the linux drive. Than I copied the file libext2fs.so.2.4 from another laptop with Kubuntu on USB stick, and than I copied that file to the lib folder via Windows partition. Supprisingly for me it worked though Kubuntu is booting up slower, but I guess now it will be easier for me to fine tune while I am in linux. I should defenietly check up her HDD because I don't know what happened and why this hapened. Might be some bad sectors. 

Thank you guys for your help I am happy that I at least partially solved this problem. :)

---

