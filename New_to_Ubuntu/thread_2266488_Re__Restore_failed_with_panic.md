---
title: "Re:  Restore failed with panic"
date: 2015-02-23
forum: New to Ubuntu
---

### Post by soundgeek on 2015-02-23
I backed up the system to an external drive. I used the backup GUI included in the installation. I backed up from /
An install of a windows Java on Wine 1.6.2 failed, leaving a partial install, so I decided to restore the system to a state prior to this.

I used the same backup GUI to attempt a restore to original locations.
The restore started, but failed shortly afterwards with a panic; see attached picture.

I rebooted from an SD card. I tried restoring to original locations and also to a specified folder ("941GB volume"), but both failed with "no space left".

I want to restore to a known state with good integrity. Help please!

Am I doing something wrong or should I submit this as a bug?

---

### Post by sandyd on 2015-02-24
> **soundgeek said:**
> I backed up the system to an external drive. I used the backup GUI included in the installation. I backed up from /
An install of a windows Java on Wine 1.6.2 failed, leaving a partial install, so I decided to restore the system to a state prior to this.

I used the same backup GUI to attempt a restore to original locations.
The restore started, but failed shortly afterwards with a panic; see attached picture.

I rebooted from an SD card. I tried restoring to original locations and also to a specified folder ("941GB volume"), but both failed with "no space left".

I want to restore to a known state with good integrity. Help please!

Possibly [https://bugs.launchpad.net/deja-dup/+bug/332500](https://bugs.launchpad.net/deja-dup/+bug/332500)

Can you boot up to a livecd, and run
```

df -h
```
in a terminal

---

### Post by soundgeek on 2015-02-25
Hi Sandyd. I tried df -h and got: [ATTACH=CONFIG]260211[/ATTACH] (Sorry, I don't know how to cut & paste text fromTerm).

Should I be able to run restore from the installed Linux? Or should I boot another CD or USB system to run restore?

Maybe the problem is something to do with the encryption of the Ubuntu partition?

A strange result of the failed restore, is that although most of the system seems to work, DOSbox files, although they are listed in the directory correctly, have scrambled contents as though encrypted. E.g. asimple .TXT file is unreadable in Notepad, and .EXE files fail to execute.

---

### Post by sandyd on 2015-02-25
> **soundgeek said:**
> Hi Sandyd. I tried df -h and got: [ATTACH=CONFIG]260211[/ATTACH] (Sorry, I don't know how to cut & paste text fromTerm).

Should I be able to run restore from the installed Linux? Or should I boot another CD or USB system to run restore?

Maybe the problem is something to do with the encryption of the Ubuntu partition?

A strange result of the failed restore, is that although most of the system seems to work, DOSbox files, although they are listed in the directory correctly, have scrambled contents as though encrypted. E.g. asimple .TXT file is unreadable in Notepad, and .EXE files fail to execute.

Interesting.

Can you post the output of```

sudo fdisk -l
sudo parted -l
```

Just need to make sure which partition is which since I can only see a drive named sdc there

---

### Post by soundgeek on 2015-02-27
That resulted in:  
[ATTACH=CONFIG]260413[/ATTACH]


How should I go about a Restore?



How should I go about a Restore to an encrypted partition?

I tried running a restore of only the my home directory & this completed fine.

However, one directory has alot of files, which though they are listed correctly, the contents are rubbish.

The backup/restore utility I am using is the one packaged with Ubuntu. I don't feel confident about using it again!

---

