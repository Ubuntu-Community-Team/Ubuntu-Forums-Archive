---
title: "won't boot"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by rebelrouser9 on 2008-05-27
Hello everyone,

I have a IBM computer with plenty of stuff that is on the hard drive and I fear that this might be a reason why it won't boot...

Actually I had the same prob with my laptop and managed to fix this by doing this : 

apt-get clean

Now the problem with my desktop (my new computer) is that the command line doesn't even recognize the apt-get command, saying that it's not currently installed. "you can install it by typing : apt-get install apt...doing so just gives me the exact same response (it's not installed, you can install...bla bla bla)

Anyway what do you guys think of this?
Carlos

---

### Post by Sarah L on 2008-05-27
You seem to be describing two different problems here.

Is your problem that your computer will refuse to boot? In that case please elaborate on your issue. In the meantime, if you want to access your files, boot up from a LiveCD and copy the files you need onto a flashdrive.

If your problem is that aptitude doesn't seem to be installed, download the .DEB package from the Ubuntu website [here]("http://packages.ubuntu.com/search?searchon=names&keywords=apt"). Once downloaded, install it using ```
sudo dpkg -i *.deb
```

---

### Post by iaculallad on 2008-05-27
Try reinstalling the apt utility on your Desktop using Synaptics.

System->Administration->Synaptic Package Manager and search for apt.

---

### Post by rebelrouser9 on 2008-05-27
**This is what the screen says when i try to boot ubuntu : **
> *An automatic file system check (fsck) of the root filesystem failed.
A manual fsck mush be performed, then the system restarted. 
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read only mode. 
A maintenance shelle will now be start.
After performing system maintenance, press control-d to terminate the maintenance shelle and restart the system. 
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe : command not found 
bash:The: command not found
The program "apt-get is currently not installed.You can install it typing: apt-get install apt

Now the problem is that I have no clue on how to transfer a file from the flash drive and install it in the command line *Doh!* ](*,):x

---

### Post by iaculallad on 2008-05-27
The solution to your problem is just to manually run the fsck command as described in the error message. Try to use your LiveCD when doing this to ensure that your main filesystem isn't mounted. The you can issue the command on the terminal: **fsck /dev/hda1** (or whatever it is in your system).


By default, apt utility is installed on your system.

---

### Post by rebelrouser9 on 2008-05-28
I think it's gonna work
Thanks a lot!

I'm going to put stuff on dvd so that there is more room on my computer

Is there a rule of thumb to determine how much minimum free room one should have on their hard disk...

Also is there a way of making sure that it doesn't go past that limit?

---

### Post by rebelrouser9 on 2008-05-28
Actually, I think that I may have spoke too soon ; (

the fsck seemed to have worked and I somehow managed to get into my normal ubuntu graphics server...i tried copying files to a dvd...but when i start back up it's the same problem.

I think I might not understand the command you are proposing
fsck /dev/hda1

actually, how do you know with is the right partition to check...
what i mean is...how to determine which hda = home

Basically what I am saying is that I have never used the live CD to fix problems on my own and I have trouble making the LIVE CD analyse my DESKTOP

---

### Post by spiderbatdad on 2008-05-28
fdisk -l will list partition tables

df -h will show disk space available

```
man fdisk
man df
```for more options

---

### Post by rebelrouser9 on 2008-05-28
**df -h**
This option is just giving me what is on the LIVE CD and not what is on my hard drive

**fdisk -l**
This option does nothing

---

