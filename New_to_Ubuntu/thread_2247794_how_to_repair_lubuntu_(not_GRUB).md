---
title: "how to repair lubuntu (not GRUB)"
date: 2014-10-10
forum: New to Ubuntu
---

### Post by piadex2 on 2014-10-10
Dear ForumMates,

When I was backuping my system I guess I was not copying the linux files but moved them (copy and then delete) so I deleted some important files.
So now Ubuntu after I enter the proper password accepts it and does some move but then I got back to the password entry screen.

I know that for Windows the install disks can actually repair the OS so do not have to reinstall it.

But what about Ubuntu?

Please help.
Thank You for Your help in advance.

piadex2

---

### Post by Impavidus on 2014-10-10
In Ubuntu nearly everything can be fixed. It's only because reinstalling is so easy that it's sometimes recommended instead of fixing.

So let's find out what the problem is. The password you enter, is that the disk encryption password (if you use any) or the normal login password? If you are returned to the login screen it indicated that the graphical session somehow fails to start. Usually, this can be fixed easely. Can you login using the guest account? If so, there is something wrong with the user files, not with the system.

Can you tell what you did exactly? Do you get any error messages?

---

### Post by piadex2 on 2014-10-10
Dear Impavidus,

No error messages. Guest account works. How to restore the original state of the user files? I am sure this is the problem. If I reinstall Ubuntu there is a good chance I loose personal data, is not it?
Thanks in advance.

piadex2

---

### Post by Bashing-om on 2014-10-10
piadex2; Hi !

As the guest account works, then yeah, problem in "userspace" not with the system.
Let's check and make sure "you" have authority to access the GUI, as 'something' may have changed these permissions.
At the login screen key combo ctl+alt+F1 to gain a console.
Please post back the outputs -Between code tags - of terminal commands:
```

ls -al .Xauthotity
ls -al .ICEauthority
ls -al /home
ls al /home/piadex

```
Where "piadex" I assume is the username you use also on your system, adjust as needed.
If accesses are good, we can try and start the desk top from terminal, see what errors are generated ; maybe look at the log files for an indication of failure.

[INDENT][INDENT]all in the process of fault isolation
[/INDENT][/INDENT]

---

### Post by piadex2 on 2014-10-14
Dear Bashing-om,

So, I suppose You ment this: (by the way sorry for being away for so long)
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
ls -al /home/piadex

```
instead of what You originally posted.

All of the four commands resulted in "no such file or directory" EXCEPT the third namely "ls -al /home".
The third gave:
```

total 8
drwxr-xr-x  2 root root 4096 Jan 15  2013 [COLOR=#0000ff].[/COLOR]
drwxr-xr-x 23 root root 4096 Sep 30 23:23 [COLOR=#0000ff]..[/COLOR]

```
note: the dots at the end of each row were blue

And by the way the terminal was not reached by CTRL+ALT+F1. But simply pressing "M" (manual restore).
The key combination resulted in blank screen where though I can type nothing happens. And when I say blank screen I mean blank screen screen without command prompt.

What do You think?
Thank You in advance.

piadex2

---

### Post by Bashing-om on 2014-10-14
piadex2; Yuk ....

Does not look good for the home team.
No .Xauthority and .ICEauthority files would prevent your access to /home .. but a bigger problem is evident in that you have no /home.
For reference my output:
```

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Oct  9 12:29 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 28 sysop sysop  4096 Oct 14 17:05 sysop
sysop@1404mini:~$

```
where 'sysop' is me, and I do have a "home" directory 'sysop', and you do not have a home directory.

But, let us double check.
Boot to the grub boot menu, 'e' key for edit mode with the top most entry (ubuntu) highlighted -> boot option screen.
Arrow down and across to the terms "quiet splash" and replace them with the term "text" - without the quotes .
key combo ctl+X to continue the boot process to a textual terminal (TTY1). 
Log in here with your username, followed by your pass word ( there will be no response to the screen when pass word is entered - enter password blindly).

NOW what results:
```

ls -al .Xauthotity
ls -al .ICEauthority
ls -al /home

```

Might now be a good time to consider file recovery options:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Not emphasized is 'testdisk':
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[INDENT]hope for the best
[INDENT][INDENT][INDENT]but more likely, data recovery time
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Impavidus on 2014-10-14
> **piadex2 said:**
> (...)
All of the four commands resulted in "no such file or directory" EXCEPT the third namely "ls -al /home".
The third gave:
```

total 8
drwxr-xr-x  2 root root 4096 Jan 15  2013 [COLOR=#0000ff].[/COLOR]
drwxr-xr-x 23 root root 4096 Sep 30 23:23 [COLOR=#0000ff]..[/COLOR]

```
note: the dots at the end of each row were blueNote that modification date: the /home/piadex directory was not removed recently.
> 
And by the way the terminal was not reached by CTRL+ALT+F1. But simply pressing "M" (manual restore).
That explains it &#8211; or part of it. You have (or had ...) a separate /home partition that fails to mount. Using M for manual restore gives you a root command prompt. It hadn't gone far enough in the boot process to allow login, but the guest session works because it doesn't need the /home partition.

Let's try and find that /home partition.Try these commands for some more diagnostics:```
#Show partitions
sudo blkid
sudo fdisk -l

#Show the contents of /etc/fstab
cat /etc/fstab
```
You may prefer to do it from a live disk, as that will give you a nice gui and allow easy copy-paste to a forum post. In that case, make sure you read the fstab of the installed system, not the one of the live disk.

---

### Post by piadex2 on 2014-10-19
Dear Bashing-om, dear Impavidus, dear Forummates,

As I previously mentioned I tryed to save my data. When I was saving I was trying to move (not copy) my data. So I think there is a considerable chance that I copied and then deleted (so "moved") my home directory among other files and directories. That is why I have no home directory at the moment.

Do You have an idea how repair my "unhomed" system. Windows install disks can repair Windowses. Is there a way to do so in Linux especially in Ubuntu?

Thank You for Your help in advance.

piadex2

---

### Post by Bashing-om on 2014-10-19
piadex2; Ummphhpp ..

Impavidus' last still applies .
By definition a 'mv' command does just that, and the data that was moved no longer exist where it was moved from.
So the question now is where was the data moved to, and how do we establish links to it.
What would be very helpful presently is the commands you used to move the data - after a week these commands may no longer be available, but, one can look.
The terminal maintains a 'history' file, to see this history in terminal execute:
```

history

```
do you see the exact command you used to move the files ?

With the info provided from Impavidus' request, we may be able to find the files and depending on what you still want to do .. redirect.

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-10-19
>  So I think there is a considerable chance that I copied and then deleted (so "moved") my home directory 

Moving files with the mv command or whichever method you used doesn't delete anything it does exactly what it says, that is what you told it to do.  Move the files from one location to another.  I'm not getting the problem.  Why don't you just move the files back to your /home/ directory?  Did you forget where you moved them?

How did you try to move these files?  You mention moving but also copying and deleting, what exactly did you do?

---

### Post by piadex2 on 2014-10-23
Dear Bashing-om, dear yancek, dear Forummates,

The moving was:
I took out the drive from the laptop. Put it in an other PC running Ubuntu on it. Then I used GUI to select and move the data.

Thank You.

piadex2

ps: BTW is there a way to quick fix my Ubuntu with no home in it? There were no files. I just want to see it running without an messages.
Thank You again.

---

### Post by Impavidus on 2014-10-24
Let's get this straight. You get a "press s to skip or m for manual restore" question. This comes after the "unable to mount a partition" error message. In post #3 you didn't mention any error messages, but you must get some message, or there wouldn't be a "press m for manual restore" message.

Now everything points to either a missing /home partition, a /home partition that has changed UUID or a corrupted /etc/fstab file. In post #7 I suggested some commands to find out what exactly is the case.

I think that most file managers default to moving when you drag and drop within a partition, but default to copying and keeping the original when you drag and drop from one partition to another. But even if you did move and delete the original files, that doesn't explain the mount failure. And it would be trivial to restore the backup by just reversing the operation.

One other possibility is that your /etc/fstab doesn't use UUIDs, but old fasioned partition IDs. If the laptop has multiple drives, then upon putting the drives back in, the drive IDs might have swapped, replacing sda1 with sdb1 and vice versa. This could also explain the mount problem as a result of taking the hard drive out. So I'd still like to see the results from the commands I posted in post #7.

It is possible to simply create a new home directory, but that would still leave the error message at boot and you may miss a lot of disk space.

---

### Post by piadex2 on 2014-10-24
Dear Impavidus, dear Forummates,

I suppose the easiest way to solve my problem would be reinstalling Ubuntu.
Is there a way keep the current personal folders and stuff?
What do You think about this idea?

Thank You!

piadex2

---

### Post by Impavidus on 2014-10-24
The personal folders and stuff is exactly the part that is missing right now, so if you want to keep them, we'll have to find them first – or a backup. But with a little information on your current partitioning and fstab file solving this problem might be trivial. This information can be provided by the commands I suggested in post #7.

---

### Post by piadex2 on 2014-11-01
Dear Forummates,

First of all who helped me or planned to help me: thank You.
I needed a solution quick so I lacalized all valuable data then saved it. After backing up I started installation. It detected that I already have systems and there is an Ubuntu system as well. There was an option to quasi reinstall Ubuntu. After that everything was working fine.
I admit it was a brutal solution (or brute force) but is worked. Sorry again I was out of time.
Thank You again.

piadex2

---

