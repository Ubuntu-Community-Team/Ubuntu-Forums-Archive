---
title: "'rm' command not working"
date: 2019-07-01
forum: New to Ubuntu
---

### Post by tsinghuaboiler on 2019-07-01
Hi all,

I am new to linux. I find that most of the common commands work well except 'rm'. Nothing happens when I use this command, and there are no responses when I type 'rm --help'.

Could anybody tell me how can I fix this problem?

Best,
Zengrong

---

### Post by TheFu on 2019-07-01
Are you new to Ubuntu? New to Linux? Or new to all Unix-like OSes?  At this level they all behave the same - iOS, OSX, any Unix, Android ... same-same for the 'rm' command.

**man rm** is where you'd get help for any command on Unix systems (cough, except AIX).

To get help here, from me, you'll need to post the output from 3 commands (to start).
```
ls -al {file}
ls -al {directory where file is located}
id
```

The first lets us see the file permissions, ownership and group.
The 2nd lets us see the directory permissions for where the file is stored.
The 3rd lets us see what your userid, groupids and alternate groupids are.

All three of these are critical for file permissions.

BTW, you cannot try to 'rm' a directory.  Use **rmdir** for that.

Those are the standard issues, but there could be a few other possible things that aren't normally used like file attribs or ACLs which could prevent rm on a file.  These are seldom used.  
And the file system might be mounted read-only.  Sometimes this happens on purpose (I do it for static websites to prevent being hacked) and sometimes the file system will do it to prevent damage.  There would be messages in the mtab or **dmesg** output about this.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a free PDF book, no-hassle download and multiple languages that is a good place to learn working through each chapter, in order, so you don't miss important prior-knowledge.

---

### Post by tsinghuaboiler on 2019-07-01
Thank you so much for your detailed reply. I am new to all these things. Now I am trying to remove the entire installing folder 'MATLAB':
"
root@CIVILGORLE:/usr/local# ls -al MATLAB
total 16
drwxr-xr-x  4 root root 4096 Apr 30 10:21 .
drwxr-xr-x 14 root root 4096 Oct 24  2015 ..
drwxr-xr-x 22 root root 4096 Apr  8  2016 R2015a
drwxr-xr-x 22 root root 4096 Apr 30 10:31 R2018b
root@CIVILGORLE:/usr/local# id
uid=0(root) gid=0(root) groups=0(root)
root@CIVILGORLE:/usr/local# rm -rf MATLAB
root@CIVILGORLE:/usr/local# 
"
Then the entire folder 'MATLAB' is still there and unharmed.

For any files or folders, the 'rm' command never works, and never return any information.

Could you let me know if my description is clear?

Best,
Zengrong

---

### Post by QIII on 2019-07-01
Hold on a moment!

How did you install Matlab?  Just deleting a directory can play havoc with package management.

---

### Post by tsinghuaboiler on 2019-07-01
Thank you so much for your detailed reply. I am new to all these things.  Now I am trying to remove the entire installing folder 'MATLAB':
"
root@CIVILGORLE:/usr/local# ls -al MATLAB
total 16
drwxr-xr-x  4 root root 4096 Apr 30 10:21 .
drwxr-xr-x 14 root root 4096 Oct 24  2015 ..
drwxr-xr-x 22 root root 4096 Apr  8  2016 R2015a
drwxr-xr-x 22 root root 4096 Apr 30 10:31 R2018b
root@CIVILGORLE:/usr/local# id
uid=0(root) gid=0(root) groups=0(root)
root@CIVILGORLE:/usr/local# rm -rf MATLAB
root@CIVILGORLE:/usr/local# 
"
Then the entire folder 'MATLAB' is still there and unharmed.

For any files or folders, the 'rm' command never works, and never return any information.

Could you let me know if my description is clear?

---

### Post by The Cog on 2019-07-01
That's an interesting one. 
* The directory you are trying to remove must exist, or you wouldn't see the listing of contents.
* You are operating as root, so you would normally have the rights to remove the files.

I am interested in the fact that you don't get any output from **rm --help**. On my system, that prints almost a page of help text. Can you please try these commands and post the results (I'm fishing for oddities - version of Ubuntu, are you using the normal rm program, is the directory on a read-only mount):
```
lsb_release -a
which rm
alias | grep rm=
lsblk
```

---

### Post by tsinghuaboiler on 2019-07-01
I am also a little confused. This official website of MATLAB seems to say that we only have to delete the installing folder: [https://www.mathworks.com/help/install/ug/uninstall-mathworks-products.html](https://www.mathworks.com/help/install/ug/uninstall-mathworks-products.html)

---

### Post by QIII on 2019-07-01
If you installed it via a script you got from them, it is safe to remove it the way they suggest.  I only ask because we often get support requests from people who have simply removed directories and have made messes.

---

### Post by tsinghuaboiler on 2019-07-01
I follow your advice and the information on the screen is like this:
"
root@CIVILGORLE:/usr/local# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
root@CIVILGORLE:/usr/local# which rm
/bin/rm
root@CIVILGORLE:/usr/local# alias | grep rm=
root@CIVILGORLE:/usr/local# lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   477G  0 disk 
&#9500;&#9472;sda1   8:1    0   350M  0 part 
&#9500;&#9472;sda2   8:2    0     3G  0 part 
&#9492;&#9472;sda3   8:3    0 473.6G  0 part /
sdb      8:16   0   1.8T  0 disk 
sr0     11:0    1  1024M  0 rom  
root@CIVILGORLE:/usr/local#
"

---

### Post by The Cog on 2019-07-01
It's probably right. It's deleting the folder that's the problem.
Some more commands for you to try and post the results of:
```
echo Hello > hello.txt
cat hello.txt
rm hello.txt
cat hello.txt
getenforce
```

---

### Post by tsinghuaboiler on 2019-07-01
The results of the code are:
"
root@CIVILGORLE:/usr/local# echo Hello > hello.txt
root@CIVILGORLE:/usr/local# cat hello.txt
Hello
root@CIVILGORLE:/usr/local# rm hello.txt
root@CIVILGORLE:/usr/local# cat hello.txt
Hello
root@CIVILGORLE:/usr/local# getenforce
Disabled
root@CIVILGORLE:/usr/local# ls
bin  etc    hello.txt  lib  MATLAB  share  tecplot360ex
doc  games  include    man  sbin    src    tecplotchorus2015r1
"
So 'rm' doesn't work for either files or folders...

---

### Post by tsinghuaboiler on 2019-07-01
Therefore, the problem seems to have nothing to do with whether I delete files or folders.

So could anybody help me?

---

### Post by #&amp;thj^% on 2019-07-01
[S]Very Odd can you show us this:
```
which rm
```[/S]
I see that has an answer.

---

### Post by QIII on 2019-07-01
Would you please provide the exact full text of the command you are issuing?

---

### Post by The Cog on 2019-07-01
* rm --help doesn't print help
* mount doesn't show the mount options
Maybe it's just because this version of Ubuntu is so old (12.04 is 2 years out of support) but things look strange to me.

There is another command that should be able to delete files: unlink. Please can you try 
```
unlink hello.txt
cat hello.txt
```
to see if that can remove files. 

But I admit I am running out of ideas here.

P.S. it would be good if you could put your quoted text in code quotes. While editing the reply, click Go Advanced and then you can highlight the quoted text and click the # button above the edit window.

---

### Post by richard378 on 2019-07-01
It is a permissions problem. It is installed as root root. You need "sudo rm -rf MATLAB" from another standard user account just to see if it works. You should not be running a root account in Ubuntu. You can also try /bin/rm -rf MATLAB

Also, you can try to "apt-get install --reinstall coreutils" then try again but you wont need to if you run from a standard user account. If you can still install packages on a distro that old? Perhaps you can install from the package from the CD. But I expect /bin/rm to work or if not run sudo from a standard user account. It is an issue with running a root account that I encountered when trying long ago. I tried Ubuntu many times in the past, but due to usefulness for me, I did not stay with it. I stayed with Windows for a long time. I recently switched to Linux, specifically Ubuntu after many years of testing usability. My first try was when Grub became available as GUI.

---

### Post by tsinghuaboiler on 2019-07-01
> **The Cog said:**
> * rm --help doesn't print help
* mount doesn't show the mount options
Maybe it's just because this version of Ubuntu is so old (12.04 is 2 years out of support) but things look strange to me.

There is another command that should be able to delete files: unlink. Please can you try 
```
unlink hello.txt
cat hello.txt
```
to see if that can remove files. 

But I admit I am running out of ideas here.

P.S. it would be good if you could put your quoted text in code quotes. While editing the reply, click Go Advanced and then you can highlight the quoted text and click the # button above the edit window.

Thank you. I tried 'unlink'. It worked for files although not for folders...

---

### Post by tsinghuaboiler on 2019-07-01
> **richard378 said:**
> It is a permissions problem. It is installed as root root. You need "sudo rm -rf MATLAB" from another standard user account just to see if it works. You should not be running a root account in Ubuntu. You can also try /bin/rm -rf MATLAB

Also, you can try to "apt-get install --reinstall coreutils" then try again. If you can still install packages on a distro that old? Perhaps you can install from the package from the CD. But I expect /bin/rm to work or if not run sudo from a standard user account. It is an issue with running a root account that I encountered when trying long ago. I tried Ubuntu many times in the past, but due to usefulness for me, I did not stay with it. I stayed with Windows for a long time. I recently switched to Linux, specifically Ubuntu after many years of testing usability. My first try was when Grub became available as GUI.

I tried "apt-get install --reinstall coreutils" as you advised, and it works! Thank you so much.

So my problem was that the package 'coreutils' had not been installed appropriately... Was that right?...

---

### Post by The Cog on 2019-07-01
How odd. This might get rid of all the regular files - find and unlink them 1 by 1. 
```
find MATLAB -type f -exec unlink '{}' \;
```
Then remove the empty directories with ths (may need several goes because it doesn't do them in the right order)
```
find MATLAB -type d -exec rmdir '{}' \;
```

But it might be that richard37's suggestion of "sudo rm -rf MATLAB" from a non-root but sudo-capable account might do it. The fact that SELinux has been installed (even though disabled) has changed some things in odd ways. I'm not that familiar with SELinux.

---

### Post by TheFu on 2019-07-01
I happen to have a 1204 server that I spun up:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

$ rm --help
Usage: rm [OPTION]... FILE...
Remove (unlink) the FILE(s).

  -f, --force           ignore nonexistent files, never prompt
  -i                    prompt before every removal
....

```

So, what that tells me is that this isn't a standard Ubuntu on your machine.  Lots of things don't seem to be working and since it it so out of support if it has been on the internet at all (or a college network anywhere), then it is probably hacked and has **at least** 1 rootkit, perhaps more.  There are many of other things it might be, but none of that really matters ... because 

**There's only 1 answer.**

**Wipe it.  The entire OS, the entire disk.**

Stay on supported releases of any OS you run if it is connected to **any** network and patch as prescribed by the release team.  I patch Ubuntu weekly. Today, if you don't have a really good reason, then Ubuntu {something} 18.04.2 is what should be installed.  "Something" would depend on the CPU, RAM, and GPU.  A machine with 12.04 on it could be from 2009 or older, so xubuntu or ubuntu-mate would be the first guesses.

Since support ended for 12.04, there have _at least_ 3 remote access attacks possible that have been fixed in newer releases, but not in 12.04, that is assuming your company isn't paying Canonical for extended support of that release.  If you are, I'd love to know the price.  I've never seen it posted anywhere.

If you still want to look deeper ... I wouldn't bother ... but feel free:
**lsattr** is a command to see file attributes.  Sometimes it is a fun joke to change these on friends, enemies, and hackers.

12.04 didn't have ACLs enabled by default, at least not on my systems, but **getfacl** is how you'd check those.  Back then, I doubt to was compiled into the file system, so if someone enabled it, they'd have to build the file system themselves.

Nobody asked about running overly file systems or containers or sandboxes or chroot setups or anything else would would let files appear to be writable, but actually not permit it.  The fact that /usr/local/ allowed file creation didn't test that MATLAB does.  It is probably fine, but we can't really tell.

It is really poor form to use the root account directly in Unix.  99.999999% of the time, we use normal user accounts and use sudo (from approved accounts) to elevate privileges for specific commands.  DO NOT USE ROOT OR SUDO WITH GUI PROGRAMS, until you can fix the problems that WILL arise is you do that.  

Did I mention there's only 1 viable answer?  Wipe everything on that machine?  Anything less could leave the rootkit behind, if one exists.

---

### Post by tsinghuaboiler on 2019-07-01
> **The Cog said:**
> How odd. This might get rid of all the regular files - find and unlink them 1 by 1. 
```
find MATLAB -type f -exec unlink '{}' \;
```
Then remove the empty directories with ths (may need several goes because it doesn't do them in the right order)
```
find MATLAB -type d -exec rmdir '{}' \;
```

But it might be that richard37's suggestion of "sudo rm -rf MATLAB" from a non-root but sudo-capable account might do it. The fact that SELinux has been installed (even though disabled) has changed some things in odd ways. I'm not that familiar with SELinux.

Thank you. I tried 'sudo rm -rf MATLAB' from a non-root account but it failed. However, after I tried "apt-get install --reinstall coreutils", the 'rm' command worked again, and thus it seemed that my problem was solved. So I was wondering whether my problem was that I had not installed the package 'coreutils' well...

---

### Post by The Cog on 2019-07-01
Thanks for posting the solution rather than keeping us wondering. Makes me wonder how rm got modified though. Was it the installation of SELinux, or something more nefarious, I wonder.
I think it is probably time you installed a later version of the OS.

EDIT: I just noticed TheFu's reply. I agree. Burn it and start again with the latest LTS. Don't upgrade - wipe it.

---

### Post by tsinghuaboiler on 2019-07-01
> **TheFu said:**
> I happen to have a 1204 server that I spun up:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise
jp@xen41:~$ rm --help
Usage: rm [OPTION]... FILE...
Remove (unlink) the FILE(s).

  -f, --force           ignore nonexistent files, never prompt
  -i                    prompt before every removal
....

```

So, what that tells me is that this isn't a standard Ubuntu.  Lots of things don't seem to be working and since it it so out of support if it has been on the internet at all (or a college network anywhere), then it is probably hacked and has at least 1 rootkit.  There are many of other things it might be, but none of that really matters ... because 

**There's only 1 answer.**

**Wipe it.  The entire OS, the entire disk.**

Stay on supported releases of any OS you run if it is connected to **any** network and patch as prescribed by the release team.  I patch Ubuntu weekly. Today, if you don't have a really good reason, then Ubuntu {something} 18.04.2 is what should be installed.  "Something" would depend on the CPU, RAM, and GPU.  A machine with 12.04 on it could be from 2009 or older, so xubuntu or ubuntu-mate would be the first guesses.

If you still want to look deeper ... I wouldn't bother ... but feel free:
**lsattr** is a command to see file attributes.  Sometimes it is a fun joke to change these on friends, enemies, and hackers.

12.04 didn't have ACLs enabled by default, at least not on my systems, but **getfacl** is how you'd check those.  Back then, I doubt to was compiled into the file system, so if someone enabled it, they'd have to build the file system themselves.

Nobody asked about running overly file systems or containers or sandboxes or chroot setups or anything else would would let files appear to be writable, but actually not permit it.  The fact that /usr/local/ allowed file creation didn't test that MATLAB does.  It is probably fine, but we can't really tell.

It is really poor form to use the root account directly in Unix.  99.999999% of the time, we use normal user accounts and use sudo (from approved accounts) to elevate privileges for specific commands.  DO NOT USE ROOT OR SUDO WITH GUI PROGRAMS, until you can fix the problems that WILL arise is you do that.  

Did I mention there's only 1 viable answer?  Wipe everything on that machine?  Anything less could leave the rootkit behind, if one exists.

Thank you very much for your suggestion. This Ubuntu version 12.04 does have some other unexpected problems (e.g. it often displayed that the disk was full and no files could be saved; but after I reboot the computer, the disk became free again...) I think I will reinstall the new version you suggested.

---

### Post by tsinghuaboiler on 2019-07-01
Thank you everybody! My problem has been solved. All your advices are very helpful.

---

