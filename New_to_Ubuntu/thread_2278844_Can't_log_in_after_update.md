---
title: "Can't log in after update"
date: 2015-05-19
forum: New to Ubuntu
---

### Post by jmadsenee on 2015-05-19
Hi All,

I know that there are tons of posts about this.  I think I read them all and tried everything I could find.  

Yesterday, I did a sudo apt-get udate and sudo apt-get upgrade.  One of the things that got updated was the Linux kernel.  It was 3.16.0-30 and upgraded to 3.16.0-37.  Then I could no longer log in.  I enter my password, press enter, the screen goes blank, then the login screen reappears.  I tried:
[LIST]
[*]Logging in for a guest session - same result 
[*]adding a new user - same result 
[*]ctrl + alt + f1 - I can log in from the terminal 
[*]sudo chmod -R ug+rwx - did not fix 
[*]chown -r user:user /home/user - did not fix 
[*]sudo apt-get remove ubuntu-session  sudo apt-get install ubuntu-session - did not fix 
[*]recovery mode - dpkg repair -  did not fix 
[*]deleting .Xauthority & .ICEauthority - did not fix 
[*]my home directory is 90% free 
[*]I can use the advanced options and log in using the old kernel, but that's not the way it's supposed to be... 
[/LIST]
Any help anyone can give would be greatly appreciated!

John

---

### Post by dino99 on 2015-05-19
when you get the grub menu, choose the 'recovery mode', then activate the network and open a terminal. Now run:  > sudo dpkg-reconfigure lightdm and continue booting 'normally'. If that fails again, then redo the first steps, and when reconfiguring lightdm, switch to gdm

---

### Post by jmadsenee on 2015-05-19
Hi dino99,

Thanks for your reply.  Booting into recovery mode and doing 'sudo dpkg-reconfigure lightdm' had no effect - still just loops to the login screen.  Installing and switching to gdm also did not work.  After switching to gdm, I get only a blank screen when booting into 3.16.0-37.  I do see the different login screen when booting into the old version - 3.16.0-30.

John

---

### Post by jmadsenee on 2015-05-27
Hi again,

I just updated to 3.16.0-38 and still cannot log in!  Please help!

---

### Post by Bashing-om on 2015-05-27
jmadsenee; Hello;

What pops to mind:
> 
Yesterday, I did a sudo apt-get udate and sudo apt-get upgrade. One of the things that got updated was the Linux kernel. 

is that there is a proprietary graphics driver at play here. And when the kernel was upgraded the driver that was built against the old kernel got broke with the new kernel.

What does the log file relate in this respect ?
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]let's see what tale 
[INDENT][INDENT][INDENT]gets told
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jmadsenee on 2015-05-27
Hi Bashing-om,

Ah, yes, you hit the nail on the head!  There is a proprietary graphics driver!  Looking at the file you mentioned, there are many lines referring to NVIDIA...  Being a noobie, I don't really understand it all, but I've attached it.  So, what do I do??

Thanks SO much!  This has been driving me crazy!

John

---

### Post by Bashing-om on 2015-05-27
jmadsenee; Hey;

I have no means to uncompress the .tar on this my work station. Rather than re-booting my system to a different install will you be so kind as to upload the file to our pastebin site ?
```

sudo apt-get install pastebinit
cat /var/log/Xorg.0.log | pastebinit

```
Will result in a URL returned;
Pass that complete URL back to this thread and we can examine the contents of the file.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by sandyd on 2015-05-27
Hi, can you boot to a working kernel, run and post output.
```

sudo /usr/lib/dkms/dkms_autoinstaller start 3.16.0-38-generic
```

Try booting with 3.16.0-38-generic again.

---

### Post by jmadsenee on 2015-05-28
Hi sandyd,  

Thanks for your reply.  Unfortunately, what I got when running the command was:  sudo: /usr/lib/dkms/dkms_autoinstaller: command not found.  Seems I don't even have a /usr/lib/dkms directory.  I saw a dkms_autoinstaller script on an mit website.  Do I want that?

John

---

### Post by jmadsenee on 2015-05-28
Hi Bashing-om,

[http://paste.ubuntu.com/11411749/](http://paste.ubuntu.com/11411749/)

Thanks!

---

### Post by tristan16 on 2015-05-28
> **jmadsenee said:**
> Hi Bashing-om,

Ah, yes, you hit the nail on the head!  There is a proprietary graphics driver!  Looking at the file you mentioned, there are many lines referring to NVIDIA...  Being a noobie, I don't really understand it all, but I've attached it.  So, what do I do??

Thanks SO much!  This has been driving me crazy!

John

Where did you install the proprietary graphics driver? I believe the Ubuntu Software Center is supposed to automatically update the driver with the kernel, but if you manually installed it from a .run file, you will have to reinstall the driver after every kernel update.

---

### Post by Bashing-om on 2015-05-28
jmadsenee; Shucks;

I see no faults in the Xorg.0.log file. Do I read the file correctly that you have 3 displays active ?
And also in respect to "/usr/lib/dkms/' directory; I also DO NOT have/use this directory .

I do not now know where the fault may lie. You have done all I can think of .
Perhaps one might (RE-)install the graphics driver on general purposes, but I do not know that it will be effective.

[INDENT][INDENT]there are those times
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jmadsenee on 2015-05-29
Thanks Bashing-om and tristan16!

Seems the problem was the graphics driver.  I went into recovery mode on 3.16.0.38, reinstalled nvidia-346 in the terminal and now I can boot into it.  Oh, happy day!:p  Now I know to update it every time the kernel is updated...

I appreciate all your help!

And, yes I do have 3 displays; doing hardware and software design I tend to have a lot of open windows...

John

---

### Post by Bashing-om on 2015-05-29
jmadsenee; Great;

Pleased it has worked out, and we know what to do the next time .

As this matter is now concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and just
[INDENT][INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

