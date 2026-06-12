---
title: "initramfs - the root filesystem on /dev/sda1 requires manual fsck (ATA bus error)"
date: 2016-07-26
forum: New to Ubuntu
---

### Post by diogovmm on 2016-07-26
Hello, this is my first time using linux and I am running a xubunto. I read how to do things and got xubunto running good yesterday.
Today I noticed all icons on desktop had a lock symbol and searched on web figuring out it would have something to do with permissions.

I followed some posts saying I should use 
```
sudo chown -R $USER: $HOME" and "sudo chmod 777 -R /path to folder
``` 
but I didnt notice any change so I restarted the pc. 
Since then I cant get past what seems to be initramfs saying that "the root filesystem on /dev/sda1 requires manual fsck".

Again I searched on web how to fix it and ended up using commands like "sudo fsck /dev/sd1" etc. but in all my attempts to fix it in the end I get a message saying:

```
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 171285/15007744 files (0.1% non-contiguous), 1910197/60001024 blocks

..."failed command:WRITE DMA" ... "Emask 0x10 (ATA bus error)"
```

As you can guess I don't understand half what is happening and can't figure it out alone.
Can someone please help me understanding and fixing whats happening?

Thank you for your time and help on the issue.

---

### Post by QIII on 2016-07-26
Without knowing exactly which directories you applied a recursive chmod to, we can't really have any idea what you may have changed.

Linux depends on specific permissions applied to many directories.  It is not a good idea for those who are just starting with Linux to chmod directories - especially recursively.  Much worse still to do so based on random recommendations from the web.

There are about two reasons why I ever recommend the nuclear option of reinstalling:  a compromised system and a system where permissions or ownership have been randomly changed.

I would highly suggest that in the future you ask here first before doing something so dangerous.

---

### Post by yancek on 2016-07-26
It's difficult to come up with a scenario in which one would 'need' 777 permissions and certainly not outside a user /home directory.  You're basically giving anyone who has any type of physical access to the computer permission to modify anything in that/those directories including deleting everything.  So to start, posting the directory concerned as suggested would be a good starting point.

---

### Post by diogovmm on 2016-07-26
I understand that now. I only did this so reckless because I am using a sowhat old pc that I can "break" abit in order to get used to xubunto before using on my main pc. It woun't happen again I hope.

When I try to reinstall, deleting everything in the disk it all goes well until I get a message:
"failed to create a files system"
"the ext4 file system creation in partition #1 of SCSI4 (0,0,0)(sda) failed."

After that I get the same errors >.<

---

### Post by diogovmm on 2016-07-27
Today after trying to reinstall linux again I got a message at the end saying it crashed and was probably because of hardware being in bad shape or cables not being well connected. Do you think it could be it? indeed the pc does not seem to be in that good shape and e error messages seem irregular.

About what directory I think I only used on home directory but can't be 100% sure. I think I tried using on root but to no effect.

---

### Post by Bashing-om on 2016-07-27
diogovmm; Hello; My Welcome to the forum.

As you are now having such difficulties re-installing, I would be concerned about the health of the hard drive.
A quick check can be done to see the assessment:
From the live installer - 
booted to a terminal, run terminal commands:
```

sudo apt install smartmontools

```
to install the tool.

Now run the diagnostic routine: For for sure identify the target drive
```

sudo parted -l

```
And run the short test:
```

sudo smartctl -a /dev/sda

```
If required change 'sda' as the target.

Deeper analysis could be called for.
see:
[https://en.wikipedia.org/wiki/S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T).
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)
[https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results](https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results)

If the hard drive is failing.
[INDENT][INDENT]no point in beating on the software
[/INDENT][/INDENT]

---

