---
title: "running scripts (csh, tcsh, etc.) under ubuntu"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by statmech on 2008-05-10
I have been using Fedora Core (FC), and to run a csh script under FC,
say, script.csh, you don't need to prepend the script filename with
csh.  Under Ubuntu, I had to prepend the script filename with csh.

For example, I have a script called "test1" with the content
as follows:

   #! /bin/csh
   #
   /bin/date

To run this script, under FC, I just need to type:

   test1

Under Ubuntu, the above gives an error:

   test1
   test1: Permission denied.

I had to prepend the script filename with "csh", i.e.,

   csh test1
   Sat May 10 04:10:13 CDT 2008

Actually, I could prepend the script filename with bash, tcsh,
etc., and it all worked, even though the first line of the script
says to run csh:

   #! /bin/csh

Here are the results:

   bash test1
   Sat May 10 04:13:02 CDT 2008
   tcsh test1
   Sat May 10 04:12:59 CDT 2008
   csh test1
   Sat May 10 04:13:05 CDT 2008

Question: How to avoid having to prepend csh (or bash, or tcsh) in
front of a script's filename to run that script (just like under FC)?

Thanks.

---

### Post by hyper_ch on 2008-05-10
you need to make it first executable... by default no new files are.

---

### Post by statmech on 2008-05-10
Yes, my script had the execute permission for user, group and others: 

ls -l test1
-rwxr-x--x 1 vql thn 24 2008-05-10 06:53 test1*

That was my first reaction: Check the execute permission.
But it seems that you have to prepend test1 with csh, dash, bash, 
tcsh, to execute the script.  There should be a way to avoid doing 
this.

---

### Post by hyper_ch on 2008-05-10
then run it with:
```

./script1

```

---

### Post by statmech on 2008-05-10
Yes, I did that too:

vql@rc0224: tcsh 85> test1
test1: Permission denied.
vql@rc0224: tcsh 86> ./test1
./test1: Permission denied.

But if I prepend any of the following (csh, dash, tcsh, bash),
then the script can be executed:

vql@rc0224: tcsh 87> csh test1
Sat May 10 08:01:00 CDT 2008
vql@rc0224: tcsh 88> dash test1
Sat May 10 08:01:04 CDT 2008
vql@rc0224: tcsh 89> tcsh test1
Sat May 10 08:01:08 CDT 2008
vql@rc0224: tcsh 90> bash test1
Sat May 10 08:01:12 CDT 2008
vql@rc0224: tcsh 91>

---

### Post by hyper_ch on 2008-05-10
why this shell and not bash?

---

### Post by Monicker on 2008-05-10
Strange. Something else must be going on with your system.  The script works for me.

```
arkaic@purgatory:/tmp$ cat foo.sh
#! /bin/csh
#
/bin/date


arkaic@purgatory:/tmp$ ls -lh foo.sh
-rwxr-xr-x 1 arkaic arkaic 24 2008-05-10 06:12 foo.sh

arkaic@purgatory:/tmp$ uname -a
Linux purgatory 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

arkaic@purgatory:/tmp$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

arkaic@purgatory:/tmp$ ./foo.sh
Sat May 10 06:13:31 MST 2008
arkaic@purgatory:/tmp$
```

---

### Post by statmech on 2008-05-10
Here is the info on the linux kernel and the ubuntu version that I 
am using:

vql@rc0224: tcsh 101> uname -a
Linux rc0224 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

vql@rc0224: tcsh 102> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
vql@rc0224: tcsh 103>

---

### Post by statmech on 2008-05-10
> **hyper_ch said:**
> why this shell and not bash?

I am used to tcsh, and thus prefer to work under tcsh.

Let me exit the tcsh shell, and use bash shell; same problem:

vql@rc0224: tcsh 103> bash
vql@rc0224:~/bin$ 
vql@rc0224:~/bin$ dirs
~/bin

vql@rc0224:~/bin$ test1
bash: ./test1: /bin/csh: bad interpreter: Permission denied

If I prepend either csh, dash, tcsh, or bash, then the script executed:

vql@rc0224:~/bin$ csh test1
Sat May 10 08:16:54 CDT 2008
vql@rc0224:~/bin$ dash test1
Sat May 10 08:17:15 CDT 2008
vql@rc0224:~/bin$ tcsh test1
Sat May 10 08:17:22 CDT 2008
vql@rc0224:~/bin$ csh test1
Sat May 10 08:17:25 CDT 2008
vql@rc0224:~/bin$

---

### Post by statmech on 2008-05-10
> **Monicker said:**
> Strange. Something else must be going on with your system.  The script works for me.

```
arkaic@purgatory:/tmp$ cat foo.sh
#! /bin/csh
#
/bin/date
arkaic@purgatory:/tmp$ ls -lh foo.sh
-rwxr-xr-x 1 arkaic arkaic 24 2008-05-10 06:12 foo.sh
arkaic@purgatory:/tmp$ uname -a
Linux purgatory 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
arkaic@purgatory:/tmp$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
arkaic@purgatory:/tmp$ ./foo.sh
Sat May 10 06:13:31 MST 2008
arkaic@purgatory:/tmp$
```

Yes, there must be something not right in my installation that I don't know.  I am trying to find out.  Several web pages that I searched about "Ubuntu csh scripts" also mentioned to prepend csh in front of the script filename to execute.  But apparently your system works normally.  Que pasa?

---

### Post by hyper_ch on 2008-05-10
very strange indeed.

---

### Post by Monicker on 2008-05-10
I didn't do anything special.  After reading your post, I installed csh since it was not there already.  I still have bash as my default shell.

---

### Post by hyper_ch on 2008-05-10
isn't the default shell dash?

---

### Post by Monicker on 2008-05-10
Bash is the default for my user, but /bin/sh is linked to dash.

```
arkaic@purgatory:/tmp$ env
TERM=xterm
SHELL=/bin/bash

arkaic@purgatory:/tmp$ ls -lsh /bin/sh
0 lrwxrwxrwx 1 root root 4 2008-05-02 21:21 /bin/sh -> dash
```

---

### Post by Catalyst2Death on 2008-05-10
> **Monicker said:**
> Strange. Something else must be going on with your system.  The script works for me.

```
arkaic@purgatory:/tmp$ cat foo.sh
#! /bin/csh
#
/bin/date


arkaic@purgatory:/tmp$ ls -lh foo.sh
-rwxr-xr-x 1 arkaic arkaic 24 2008-05-10 06:12 foo.sh

arkaic@purgatory:/tmp$ uname -a
Linux purgatory 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

arkaic@purgatory:/tmp$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

arkaic@purgatory:/tmp$ ./foo.sh
Sat May 10 06:13:31 MST 2008
arkaic@purgatory:/tmp$
```

could I point out that the same symptoms are present here?
```

arkaic@purgatory:/tmp$ ./foo.sh
```

he added .sh, which is not what the OP is trying to do with his scripts... If it were going to be like the OP, then it would have read:

```
arkaic@purgatory:/tmp$ ./foo
```

furthermore, this is a csh script with a .sh extension... shouldn't it be foo.csh??

unless you put this script in a commonly searched path (/usr/bin?)  I think you have to refer to it explicitly.  ie full file name.  You might try a test script with csh only syntax, like:

```
#!/bin/csh
#Playing with CSH
setenv TEST /bin/date
echo `$TEST`
```

if you try:
```
$ bash test.csh
```

you should get some kind of error (for sure a syntax error...)

---

### Post by Monicker on 2008-05-10
> **Catalyst2Death said:**
> could I point out that the same symptoms are present here?
```

arkaic@purgatory:/tmp$ ./foo.sh
```

he added .sh, which is not what the OP is trying to do with his scripts... If it were going to be like the OP, then it would have read:

```
arkaic@purgatory:/tmp$ ./foo
```

furthermore, this is a csh script with a .sh extension... shouldn't it be foo.csh??



The extension is irrelevant.  The interpreter, /bin/csh, is what matters.

But to humor you:

```
arkaic@purgatory:/tmp$ mv foo.sh  foo

arkaic@purgatory:/tmp$ ./foo
Sat May 10 06:55:47 MST 2008
```


Same script with a different name.  Same result.

---

### Post by Catalyst2Death on 2008-05-10
so here's what happens with my script (trivial modification of OP's example):

```
dave@ophelia:~$ bash test.csh
test.csh: line 3: setenv: command not found

dave@ophelia:~$ tcsh
ophelia:~> csh test.csh
Sat May 10 10:00:26 EDT 2008
ophelia:~> csh test
test: No such file or directory.
ophelia:~> ./test.csh
./test.csh: Permission denied. 
ophelia:~> source test.csh
Sat May 10 10:00:54 EDT 2008
ophelia:~> bash
dave@ophelia:~$ csh test.csh
Sat May 10 10:02:59 EDT 2008

```

---

### Post by Catalyst2Death on 2008-05-10
My apologies, I didn't realize that the original script was named "test1"  I assumed it was "test1.csh,"  I realize that name is independent, but I thought the original problem was running a script with a .csh extension just using the script's name ie:

```
test1.csh
$csh test1
<date>
```

again, I apologize.

---

### Post by statmech on 2008-05-10
> **statmech said:**
> I have been using Fedora Core (FC), and to run a csh script under FC,
say, script.csh, you don't need to prepend the script filename with
csh.  Under Ubuntu, I had to prepend the script filename with csh.

For example, I have a script called "test1" with the content
as follows:

   #! /bin/csh
   #
   /bin/date

To run this script, under FC, I just need to type:

   test1

Under Ubuntu, the above gives an error:

   test1
   test1: Permission denied.

I had to prepend the script filename with "csh", i.e.,

   csh test1
   Sat May 10 04:10:13 CDT 2008

Actually, I could prepend the script filename with bash, tcsh,
etc., and it all worked, even though the first line of the script
says to run csh:

   #! /bin/csh

Here are the results:

   bash test1
   Sat May 10 04:13:02 CDT 2008
   tcsh test1
   Sat May 10 04:12:59 CDT 2008
   csh test1
   Sat May 10 04:13:05 CDT 2008

Question: How to avoid having to prepend csh (or bash, or tcsh) in
front of a script's filename to run that script (just like under FC)?

Thanks.

I solved the problem.  

First, to make the story short, the problem was that the filesystem
where my home directory and scripts were located was mounted without
the "exec" option that allows one to execute the binaries located
in that filesystem.

Summary of the fix: edit the file /etc/fstab, add the option "exec"
to the mount command of the appropriate filesystem mentioned above,
log out, relog in as root, unmount that filesystem, and remount
this filesystem, switch user to myself, run the script without
prepending csh; it worked.

Details of the fix:

In the file /etc/fstab, the filesystem /media/sda6 where my home directory was
located was mounted with the following options:

```

   UUID=c1beb6f6-859a-408b-ab2c-d2d7c703fe17 /media/sda6     ext3    defaults,auto,user,rw, 0 1

```

There was no "exec" option.  So add the "exec" option:

```

   UUID=c1beb6f6-859a-408b-ab2c-d2d7c703fe17 /media/sda6     ext3 defaults,auto,user,rw,exec 0 1

```

Save the file /etc/fstab; log out as current user; relog in as root and check
the filesystems with command df:

```

   root@rc0224:~# df
   Filesystem           1K-blocks      Used Available Use% Mounted on
   /dev/sda14             9076364   2850476   5764828  34% /
   varrun                  512536       104    512432   1% /var/run
   varlock                 512536         0    512536   0% /var/lock
   udev                    512536       128    512408   1% /dev
   devshm                  512536         0    512536   0% /dev/shm
   lrm                     512536     34696    477840   7% /lib/modules/2.6.22-14-generic/volatile
   /dev/sda1                48052      7990     40062  17% /media/sda1
   /dev/sda10             5124700     27964   5096736   1% /media/sda10
   /dev/sda11             5124700     27964   5096736   1% /media/sda11
   /dev/sda2             21711844   7503648  14208196  35% /media/sda2
   /dev/sda5             10241404     54388  10187016   1% /media/sda5
   /dev/sda7              5124700     27964   5096736   1% /media/sda7
   /dev/sda8              5124700     27964   5096736   1% /media/sda8
   /dev/sda9              5124700     27964   5096736   1% /media/sda9
   /dev/sda6              5044156    397332   4390592   9% /media/sda6
   /dev/sda12             5044156    141220   4646704   3% /media/sda12
   root@rc0224:~# 

```

Unmount /media/sda6:

```

   root@rc0224:~# umount /media/sda6
   root@rc0224:~# df
   Filesystem           1K-blocks      Used Available Use% Mounted on
   /dev/sda14             9076364   2850476   5764828  34% /
   varrun                  512536       104    512432   1% /var/run
   varlock                 512536         0    512536   0% /var/lock
   udev                    512536       128    512408   1% /dev
   devshm                  512536         0    512536   0% /dev/shm
   lrm                     512536     34696    477840   7% /lib/modules/2.6.22-14-generic/volatile
   /dev/sda1                48052      7990     40062  17% /media/sda1
   /dev/sda10             5124700     27964   5096736   1% /media/sda10
   /dev/sda11             5124700     27964   5096736   1% /media/sda11
   /dev/sda2             21711844   7503648  14208196  35% /media/sda2
   /dev/sda5             10241404     54388  10187016   1% /media/sda5
   /dev/sda7              5124700     27964   5096736   1% /media/sda7
   /dev/sda8              5124700     27964   5096736   1% /media/sda8
   /dev/sda9              5124700     27964   5096736   1% /media/sda9
   /dev/sda12             5044156    141220   4646704   3% /media/sda12
   root@rc0224:~# 

```

Remount /media/sda6:

```

   root@rc0224:~# mount -t ext3 /dev/sda6 /media/sda6
   root@rc0224:~# df
   Filesystem           1K-blocks      Used Available Use% Mounted on
   /dev/sda14             9076364   2850480   5764824  34% /
   varrun                  512536       104    512432   1% /var/run
   varlock                 512536         0    512536   0% /var/lock
   udev                    512536       128    512408   1% /dev
   devshm                  512536         0    512536   0% /dev/shm
   lrm                     512536     34696    477840   7% /lib/modules/2.6.22-14-generic/volatile
   /dev/sda1                48052      7990     40062  17% /media/sda1
   /dev/sda10             5124700     27964   5096736   1% /media/sda10
   /dev/sda11             5124700     27964   5096736   1% /media/sda11
   /dev/sda2             21711844   7503648  14208196  35% /media/sda2
   /dev/sda5             10241404     54388  10187016   1% /media/sda5
   /dev/sda7              5124700     27964   5096736   1% /media/sda7
   /dev/sda8              5124700     27964   5096736   1% /media/sda8
   /dev/sda9              5124700     27964   5096736   1% /media/sda9
   /dev/sda12             5044156    141220   4646704   3% /media/sda12
   /dev/sda6              5044156    397332   4390592   9% /media/sda6
   root@rc0224:~# 

```

Switch user and execute the script test1:

```

   root@rc0224:~# su vql

   vql@rc0224: tcsh 22> test1
   Sat May 10 08:47:19 CDT 2008
   vql@rc0224: tcsh 23>

```

It worked.

Recommended web pages that led me to solve and understand the problem:

   bad interpreter: permission denied
   [http://ubuntuforums.org/showthread.php?t=27138](http://ubuntuforums.org/showthread.php?t=27138)

The above web page was where I learned about the missing "exec" option.

See also:

   Understanding fstab
   [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

There is an explanation of the "exec" option and other options.

   problems understand fstab options
   [http://ubuntuforums.org/showthread.php?t=496756](http://ubuntuforums.org/showthread.php?t=496756)

which leads to the following web page, which explains clearly the
options in fstab:

   How to edit and understand /etc/fstab - 1.1
   [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

where the "exec" option is explained as follows:

> 
   exec and noexec exec lets you execute binaries that are on that partition, whereas noexec
   doesn't let you do that. noexec might be useful for a partition that contains binaries you
   don't want to execute on your system, or that can't even be executed on your system. This
   might be the case of a Windows partition.

   exec is the default option, which is a good thing. Imagine what would happen if you
   accidentally used the noexec option with your Linux root partition...


But apparently, "exec" was NOT a default option under Ubuntu...

(actually, by using the "defaults" option, you would have "exec" 
by default.)

That was the big problem solved...

Hope the above detailed documentation would be helpful for the community.

Cheers.

---

### Post by Monicker on 2008-05-10
Ahh.  I'm sure I have seen it referenced here before about checking if the filesystem has exec enabled.  It didn't even come to my mind today.  I'll have to make an effort to remember that for the future.

Glad its sorted out for you now.  :)

---

### Post by glennric on 2008-05-10
You have obviously modified your fstab to begin with and you have conflicting values there.  The "defaults" option includes all off the options "rw, suid, dev, exec, auto, nouser, and async."  However, since you specified "rw" without "exec" that overrides the "defaults" options and sets the drive to read and write only without executable.  Most people will only have the "defaults" option and so things will work as they should.  If you are using Hardy you will only have the "relatime" option for an ext3 partition.

---

### Post by statmech on 2008-05-10
you are right; I modified /etc/fstab by hand without paying close attention to the options.  Actually, I made /etc/fstab look similar to what I have under my older Fedora Core or RedHat system; obviously things work differently under Ubuntu.

I changed the line /etc/fstab related to the filesystem in which
I have my home directory from

```

   UUID=c1beb6f6-859a-408b-ab2c-d2d7c703fe17 /media/sda6     ext3 defaults,auto,user,rw,exec 0       1

```

to

```

   UUID=c1beb6f6-859a-408b-ab2c-d2d7c703fe17 /media/sda6     ext3    defaults,gid=46 0 1

```

Everything worked as expected.

Actually, now that I understand better about the options in /etc/fstab, I may be able to fix some anomalies that I observed under Fedora Core 5 on my laptop.

Thanks for your comment and of everyone else in this thread.

---

