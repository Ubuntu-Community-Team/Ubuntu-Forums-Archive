---
title: "[SOLVED] fstab - how do I modify it to get permissions?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Bruce M. on 2008-07-06
Hi Folks,

Sorry to bother you but I simply cannot remember how to do this.
I have 3 partitions on two hard drives I want to "steal" from root ownership and have them automounted for me to have read/write access.

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=237535d9-7efe-4179-9ed6-2d22f13d7a21 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=ffa7de04-35c6-4018-8c51-0600d877aef8 /BruLoo1        ext3    relatime        0       2
# /dev/sda8
UUID=6305bc57-bc45-4359-9dff-c4f0d4d163a4 /BruLoo2        ext3    relatime        0       2
# /dev/sdb1
UUID=2f2d9020-d444-40f3-9afa-341a2a5da89c /BruLoo80       ext3    relatime        0       2
# /dev/sda6
UUID=ba82a043-df62-4ddd-9f69-9f7d6664f275 /home           ext3    relatime        0       2
# /dev/sda1
UUID=1EEB-E360  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=a96dbddd-143b-44ee-b438-36311df4bcf5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

**EDIT:**
The partitions in question: **BruLoo1, BruLoo2, and BruLoo80**

**BruLoo1 & BruLoo2** are two partitions for personal use on my main 200G HD

**BruLoo80** is my old 80G HD I want for personal use.
**/EDIT**

Can someone point me in the right direction for the answer please.

Second question (or thought)
How come when installing Ubuntu one can't setup a partition and have it for the user by default?

**EDIT:**
And just so you know: That /windows partition is reserved for Windows ***if*** I ever need it. My ISP does not support Linux, and in 11 months and one week of using Linux (Ubuntu 6.06.1 - Xubuntu 8.04) I've not needed it. So when I installed 8.04 on the new drive last weekend, I gave it space but didn't waste my time installing it.
**/EDIT:**

**[COLOR="Red"]EDIT #2:[/COLOR]** Not quite finished ... now look what happened: ["Root" reclaimed my Partitions - files are missing!]("http://ubuntuforums.org/showthread.php?p=5352602#post5352602") :cry: 


Thanks, have a nice day.
Bruce

---

### Post by caljohnsmith on 2008-07-06
All you have to do is add a "rw" as an option, so put it before or after the "relatime". That won't make the partition owned by you, but it will make it read-writable, which I assume is what you are really after. For instance:

```
#/dev/sda7
UUID=ffa7de04-35c6-4018-8c51-0600d877aef8 /BruLoo1        ext3    relatime,[COLOR="Red"]rw[/COLOR]       0       2

```

---

### Post by bab1 on 2008-07-06
try looking at```
man chown
```and```
man chmod
```

---

### Post by Bruce M. on 2008-07-06
> **caljohnsmith said:**
> All you have to do is add a "rw" as an option, so put it before or after the "relatime". That won't make the partition owned by you, but it will make it read-writable, which I assume is what you are really after. For instance:

```
#/dev/sda7
UUID=ffa7de04-35c6-4018-8c51-0600d877aef8 /BruLoo1        ext3    relatime,[COLOR="Red"]rw[/COLOR]       0       2

```

No, this didn't work.
Thanks
Bruce

---

### Post by Bruce M. on 2008-07-06
> **bab1 said:**
> try looking at```
man chown
```and```
man chmod
```

OK, I have to run out for the moment, but I think this is it.
I'll try later and let you know.

Thanks
Bruce

---

### Post by Vivaldi Gloria on 2008-07-06
1) You may not have the ownership of the mountpoint and/or you don't have the permissions to read/write to mountpoint. Look into chown & chmod as sugessted above. Or press Alt+F2 and start

```
gksudo nautilus
```

and then right click the mountpoint and/or the folders below the mountpoint to change their owners/permissions.

2) It's customary in linux to leave the root (/) alone and mount the partitions to /mnt/mountpoint or /media/mountpoint. Note that mounting a partition to /media/mountpoint generated desktop icons in ubuntu automatically. 

3) If you want to be able to mount an unmounted partition as a user (rather than a superuser) with the mount command then add the "user" flag to the partition as follows:

```
UUID=???????? /mountpoint     ext3    relatime,user        0       2
```

4) To see the other flags you can use in fstab see 

```
man mount
```

What fstab does is to pass these options to mount with -o option of mount. So read that section of man mount.

5) To learn more about fstab read the howto in this forums (search it) and also

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bab1 on 2008-07-06
Bruce,

This may be long winded, but I hope it will help others.

I believe an explanation of mounting (auto or not) is in order.  One mounts partitions (/dev/sdaX or /dev/hdaX).  The ownerships of the files is another matter.  BruLoo1 and BruLo2 are the mount points and as such are directories and thus are "owned" by their creator.  The command "chown" changes ownership and the command "chmod" grants or denies read, write and executable permissions.  Root owned directories can be transfered to another user with the command: sudo chown xxxxx xxxxx.

Auto mounting partitions to mount points via the file /etc/fstab is pretty simple.  The command "mount" is used by /etc/fstab.  Read the man pages to understand the terms used in /etc/fstab.  This  should clear up most of what is going on.  In essence, fstab mounts a block device (partition) to a mount point (directory).

columns in the /etc/fstab are:
# <file system> 
/dev/sda8 (UUID=ffa7de04-35c6-4018-8c51-0600d877aef8 is an alias)


<mount point>   
/BruLoo1 (this is a directory in the root filesystem (/dev/sda5)) and the ownership is what you want to change.

<type>
 ext3 (this is the linux filesystem type)


<options>       
relatime (Update inode access times relative to modify or change time (i copied this from the mount man page)

I usually use "defaults" here.

<dump>
This is used to force a dup from ram if there is a failure (for diagnostics), 0 means no dump.  

<pass>
Used by the fsck program to  determine what filesystems to check after a failure

---

### Post by caljohnsmith on 2008-07-06
Bruce,

Setting up your fstab the way I gave should give the partition read-write capability; but if for instance you try to write to a directory in that partition that is owned by root and does not allow group/others to write to that directory, then the only way you can write to that directory will be as root user (not as your usual non-root user). And the only way you can make the directory writable for your non-root user would be to change the permissions or change ownership (chmod and chown as pointed out earlier).

---

### Post by bodhi.zazen on 2008-07-06
Ubuntu now defaults to "relatime" in the options.

Anyways, use options :

relatime,auto,users

Now with the partitions mounted :

```
sudo chown user.users /mount/point
sudo chmod 770 /mount/point/
```

So for sda7 use :

Fstab :
```
# /dev/sda7[FONT=monospace]
[/FONT]UUID=ffa7de04-35c6-4018-8c51-0600d877aef8 /BruLoo1        ext3    relatime        0       2
```

Then :
```
sudo mount -a
sudo chown user.users /BruLoo1
sudo chmod 770 /BruLoo1
```

*Change "user" in chown "user.users" to your log in name :)

Repeat for the other partitions

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by caljohnsmith on 2008-07-06
bodhi.zazen, when I upgraded from Gutsy to Hardy, my fstab was not updated to use "relatime" in the options, so thanks for pointing out that this is the new default. So is "rw" not a necessary option when mounting a partition anymore to get read-write access? Is read-write access the default or something?

---

### Post by bodhi.zazen on 2008-07-06
> **caljohnsmith said:**
> bodhi.zazen, when I upgraded from Gutsy to Hardy, my fstab was not updated to use "relatime" in the options, so thanks for pointing out that this is the new default. So is "rw" not a necessary option when mounting a partition anymore to get read-write access? Is read-write access the default or something?

You can use rw if you like, I have had mixed results and prefer to specifiy options.

With vfat / ntfs this is : auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8

With linux native systems just use chown and  chmod (to the mount point) with the partition mounted. This is a one time set of commands and does not have to be set with each mount.

For info on relatime : [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

---

### Post by bab1 on 2008-07-06
Remember guys, sometimes "mount" is used in the terminal.  Not all options are needed at all times.  The needs of fstab and a manual "mount" may be different.

---

### Post by Bruce M. on 2008-07-07
> **bodhi.zazen said:**
> Then :
```
sudo mount -a
sudo chown user.users /BruLoo1
sudo chmod 770 /BruLoo1
```

*Change "user" in chown "user.users" to your log in name :)

Repeat for the other partitions

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

OK, I'm looking at chown.txt ( I made a text file but I see: )
```

       Owner is unchanged if missing.  Group  is  unchanged  if  missing,  but
       changed  to login group if implied by a â€˜:â€™ following a symbolic OWNER.
       OWNER and GROUP may be numeric as well as symbolic.
```
so I'm going slow and careful.

Now I see:
```
EXAMPLES
       chown root /u
              Change the owner of /u to "root".

       chown root:staff /u
              Likewise, but also change its group to "staff".

       chown -hR root /u
              Change the owner of /u and subfiles to "root".
```
Which indicates that:
```
sudo chown bruloo /BruLoo1
```
should work, as you stated above.  **Thank you!**

and from chmod.txt I see:
```
       A  numeric  mode  is  from  one  to four octal digits (0-7), derived by
       adding up the bits with values 4, 2, and 1.   Any  omitted  digits  are
       assumed  to  be leading zeros.  The first digit selects the set user ID
       (4) and set group ID (2) and sticky (1) attributes.  The  second  digit
       selects  permissions  for  the  user who owns the file: read (4), write
       (2), and execute (1); the third selects permissions for other users  in
       the  file’s group, with the same values; and the fourth for other users
       not in the file’s group, with the same values.
```
But I see nothing that indicates what the "7" in 770 represents?
For that matter what a 1, 2, 3, 4, 5, 6 or 7 would represent.

Any insight?
Thank you
Bruce

---

### Post by Elfy on 2008-07-07
I could be completely wrong here - I'm not sure how it works for the first 7 but after that I think

7 - is the sum of read, write and execute - 4 + 2 + 1
0 - other users have no permissions

---

### Post by Vivaldi Gloria on 2008-07-07
Simple permissions:
```

400 - read by owner
040 - read by group
004 - read by other
200 - write by owner
020 - write by group
002 - write by other
100 - execute by owner
010 - execute by group
001 - execute by other
```


You add to get complex permissions:

644 (6=4+2, 4, 4) - read/write by owner and read by everyone else.

777 (sum of all) read/write/execute by all

755 (7=4+2+1, 5=4+1, 5=4+1) Read/execute for everone but edit (write) only for owner. 

Examples:

chmod 666 text.txt (read/write by everyone)
chmod 700 script.cgi (all rights for user, no rights for others)

---

### Post by Elfy on 2008-07-07
so 770 is owner and onwers group can r,w,x and everybody else can do nothing?

Does the first digit relate to the user, the second to the users group, the third to everyone else?

Sorry for the quick hijack bruce :)

---

### Post by Vivaldi Gloria on 2008-07-07
> **forestpixie said:**
> so 770 is owner and onwers group can r,w,x and everybody else can do nothing?

Does the first digit relate to the user, the second to the users group, the third to everyone else?

Sorry for the quick hijack bruce :)

Yep, you got it. ;)

---

### Post by Elfy on 2008-07-07
> Yep, you got it.Wouldn't got overboard though :) - so if I did chmod on / with 000 I would have serious problems 

I have used chmod and chown in the past, but it really went over my head and I used it without really understanding.

---

### Post by Vivaldi Gloria on 2008-07-07
> **forestpixie said:**
> Wouldn't got overboard though :) - so if I did chmod on / with 000 I would have serious problems 

Why don't you try it and report back? Just kidding. :-)

> **forestpixie said:**
> I have used chmod and chown in the past, but it really went over my head and I used it without really understanding.

There isn't much else to learn about chmod. If I remember correctly there is also something called sticky bit which lets only the creator of the file to delete it. It's used for /tmp. It's used as follows:

```
mkdir share
chmod 1777 share
```

That 1 at the beginning turns the sticky bit on. The rest 3 digits is the regular permission.

There is also umask. That sets the default permission value of a new file. 

```
umask
```

gives the default permission of a new file but there is a catch, umask shows the permission the users DON'T have. For example if umask gives 0022 then then it means that group and others cannot write a newly created file. 

Hey, aren't you the famous forestpixie btw?

[http://matthewhelmke.net/wordpress/2008/07/04/an-interview-with-forestpixie/](http://matthewhelmke.net/wordpress/2008/07/04/an-interview-with-forestpixie/)

Honored to be at your presence.

---

### Post by Elfy on 2008-07-07
:bow: - THAT was completely unexpected, but good all the same - still bean image less :)

I've got a xubuntu in a vm I can massacre just to see if it's more fun than the other - "you really don't want to do that " command :lol:

---

### Post by Vivaldi Gloria on 2008-07-07
> **forestpixie said:**
> :bow: - THAT was completely unexpected, but good all the same - still bean image less :)

I've got a xubuntu in a vm I can massacre just to see if it's more fun than the other - "you really don't want to do that " command :lol:

Have fun. :-)

---

### Post by bodhi.zazen on 2008-07-07
LOL

For basic permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[uhelp]community/FilePermissions[/uhelp]

When using 4 digits, the first digit is a "sticky bit". It causes all kinds of interesting things :twisted:

[http://www.codecoffee.com/tipsforlinux/articles/028.html](http://www.codecoffee.com/tipsforlinux/articles/028.html)

To make matters "worse" you can also use "ACL" or access control lists. This basically allows you more options for permissions.

[http://www.onlamp.com/pub/a/bsd/2003/08/14/freebsd_acls.html](http://www.onlamp.com/pub/a/bsd/2003/08/14/freebsd_acls.html)

That article is for "FreeBSD" but you can ACL on Ubuntu :lolflag:

---

### Post by unutbu on 2008-07-07
Wow, I never knew Linux had ACLs. I just thought they were something designed to torture VMS users :)

---

### Post by Bruce M. on 2008-07-07
> **forestpixie said:**
> Wouldn't got overboard though :) - so if I did chmod on / with 000 I would have serious problems 

I have used chmod and chown in the past, but it really went over my head and I used it without really understanding.

That would be computer suicide ... however I can see a use:

chmod 000 /windows     :lolflag:

> **forestpixie said:**
> so 770 is owner and onwers group can r,w,x and everybody else can do nothing?

Does the first digit relate to the user, the second to the users group, the third to everyone else?

Sorry for the quick hijack bruce :)

What hijack! Everything is on topic here, especially that sentence, and I quote you:

> **forestpixie said:**
> Does the first digit relate to the user, the second to the users group, the third to everyone else?

because the answer is: **YES!** I just learned that today, here. :)

Have a great day.
Bruce

---

### Post by sisco311 on 2008-07-07
> **Bruce M. said:**
> That would be computer suicide ...
Bruce
With the -R option it is.
Otherwise you can restore the permissions from the live cd.(0755)

---

### Post by Elfy on 2008-07-07
Good for learning here I think :)

I'm going to toss a coin tomorrow 15 times - because I can't be bothered to do it for longer, heads I do a chmod on my xubuntu vm, tails I do rm - etc on the /

You're call :D


> What hijack!I don't like to jump in the middle - quite happy to tack on the end :) Although as you say it was all related

---

### Post by Bruce M. on 2008-07-07
> **sisco311 said:**
> With the -R option it is.
Otherwise you can restore the permissions from the live cd.(0755)

I never would have thought of that ... I would have re-installed.
Good to know.

Bruce

---

### Post by Bruce M. on 2008-07-07
> **forestpixie said:**
> Good for learning here I think :)

I'm going to toss a coin tomorrow 15 times - because I can't be bothered to do it for longer, heads I do a chmod on my xubuntu vm, tails I do rm - etc on the /

You're call :D


I don't like to jump in the middle - quite happy to tack on the end :) Although as you say it was all related

I thought I'd help, I just flipped 8 times:
first seven - heads
8th toss - tails

any volunteers?

I really should mark this tread [Solved] but ... maybe tomorrow, after you report your chmod results. After all it is related to the topic.

CHIMO!
Bruce

---

### Post by unutbu on 2008-07-07
**Masterpiece Theatre presents: tales of tupidity**
```
tanker@suez:~% cd /
tanker@suez:/% ls -ld /
drwxr-xr-x 21 root root 4096 2008-07-07 06:06 /
tanker@suez:/% echo "Hehehe... I am tupid!"
bash: !": event not found
tanker@suez:/% echo "hehehe... i am tupid\!"
hehehe... i am tupid\!
tanker@suez:/% echo hehehe... i am tupid say it dammit!
hehehe... i am tupid say it dammit!
tanker@suez:/% sudo chmod 0000 /
[sudo] password for tanker:
tanker@suez:/% ls -ld /
bash: /bin/ls: Permission denied
tanker@suez:/% echo Uh oh...
Uh oh...
tanker@suez:/% sudo chmod 755 /
bash: /usr/bin/sudo: Permission denied
tanker@suez:/% echo hehe, now I'm fried :)
> bash: unexpected EOF while looking for matching `''
bash: syntax error: unexpected end of file
tanker@suez:/% echo hehe, now I'm fried :\)
> bash: unexpected EOF while looking for matching `''
bash: syntax error: unexpected end of file
tanker@suez:/% echo "hehe, now i'm fried :) say it dammit"!
hehe, now i'm fried :) say it dammit!
tanker@suez:/% sudo -i
bash: /usr/bin/sudo: Permission denied
tanker@suez:/% ummm...
bash: /usr/bin/python: Permission denied
```
```

Alt-SysRq R
Alt-SysRq E
Alt-SysRq I
Alt-SysRq S
Alt-SysRq U
Alt-SysRq B
```

Reboot into recovery mode
```

root@suez:~# chmod 755 /
root@suez:~# 


```

---

### Post by bodhi.zazen on 2008-07-07
> **sisco311 said:**
> With the -R option it is.
Otherwise you can restore the permissions from the live cd.(0755)

No you can not. The permissions are much more complex then that.

If you change permissions on / (with chmod -R) you are looking at re-installation.

Root ALWAYS has access, even with permissions of 0000 :

```
root@hardy:~#cd

root@hardy:~#mkdir test
root@hardy:~#echo "I have always been mad" > test/mad

root@hardy:~#chmod -R 0000 test/
root@hardy:~#ls -lA | grep test
[color=red]d--------- 2 root root 4096 2008-07-07 15:25 test[/color]

[color=red]root@hardy:~#ls test[/color]
[color=blue]mad[/color]

[color=red]root@hardy:~#cat test/mad[/color]
[color=blue]I have always been mad[/color]

[color=red]root@hardy:~#echo "LOL" >> test/mad[/color]

[color=red]root@hardy:~#cat test/mad[/color]
[color=green]I have always been mad
LOL[/color]

root@hardy:~#
```

---

### Post by sisco311 on 2008-07-07
> **bodhi.zazen said:**
> No you can not. The permissions are much more complex then that.

If you change permissions on / (with chmod -R) you are looking at re-installation.

Root ALWAYS has access, even with permissions of 0000 :

```
root@hardy:~#cd

root@hardy:~#mkdir test
root@hardy:~#echo "I have always been mad" > test/mad

root@hardy:~#chmod -R 0000 test/
root@hardy:~#ls -lA | grep test
[COLOR=red]d--------- 2 root root 4096 2008-07-07 15:25 test[/COLOR]

[COLOR=red]root@hardy:~#ls test[/COLOR]
[COLOR=blue]mad[/COLOR]

[COLOR=red]root@hardy:~#cat test/mad[/COLOR]
[COLOR=blue]I have always been mad[/COLOR]

[COLOR=red]root@hardy:~#echo "LOL" >> test/mad[/COLOR]

[COLOR=red]root@hardy:~#cat test/mad[/COLOR]
[COLOR=green]I have always been mad
LOL[/COLOR]

root@hardy:~#
```
Sorry, perhaps I wasn't clear enough.
If you change the permissions _without_ the -R option, then you can restore it
with the live(???or from single user mode???).

---

### Post by bodhi.zazen on 2008-07-07
> **sisco311 said:**
> Sorry, perhaps I wasn't clear enough.
If you change the permissions _without_ the -R option, then you can restore it
with the live(???or from single user mode???).

lol, I think I misunderstood what you were saying too :redface:

Yes, without the -R I think you would be fine.

---

### Post by Elfy on 2008-07-09
> maybe tomorrow, after you report your chmod resultsWell that was an anti-climax - no bells or sirens just

unable to start /sbin/klogd: Permission denied (Permission denied)   [[COLOR="Red"]fail[/COLOR]]

and some other fails I didn't catch, then when it had got to tty1 and I tried to login it couldn't cd to the correct directory

But there you go - wish I'd done rm -Rf / or whatever it is instead :) - I wish I'd used your coin results Bruce

---

### Post by Vivaldi Gloria on 2008-07-09
> **forestpixie said:**
> Well that was an anti-climax - no bells or sirens just

unable to start /sbin/klogd: Permission denied (Permission denied)   [[COLOR="Red"]fail[/COLOR]]

and some other fails I didn't catch, then when it had got to tty1 and I tried to login it couldn't cd to the correct directory

But there you go - wish I'd done rm -Rf / or whatever it is instead :) - I wish I'd used your coin results Bruce

Sir, you are formally nominated for the 2008 Golden Penguin Awards in the System Destruction category.

---

### Post by Elfy on 2008-07-09
:D got to keep doing something, now I can reinstall xubuntu, although I might just play with it as a livecd along with kubuntu 

Wouldn't have been quite so amusing if I'd been running vbox in seamless mode and got my terminals confused

---

### Post by gaslightjoe on 2008-07-09
Caljohnsmith,

I'm new to ubuntu, but not linux. and ubuntu/gnome operates a little different than pclinuxos/xfce.  

I have a usb drive that I wanted to delete files from, but I didn't seem to have ownership or permissions.  I used the gnome right-click to the usb drive properties where I added 'rw' to the mount options.  I umounted the usb drive and when I tried to remount, it failed. 

Any ideas how I can get my usb drive to load again and be read/write for me each time?

Thanks.

---

### Post by Bruce M. on 2008-07-09
> **forestpixie said:**
> Well that was an anti-climax - no bells or sirens just

unable to start /sbin/klogd: Permission denied (Permission denied)   [[COLOR="Red"]fail[/COLOR]]

and some other fails I didn't catch, then when it had got to tty1 and I tried to login it couldn't cd to the correct directory

But there you go - wish I'd done rm -Rf / or whatever it is instead :) - I wish I'd used your coin results Bruce

Well, you can't say I didn't give you a *heads*-up. :lolflag:

> **Vivaldi Gloria said:**
> Sir, you are formally nominated for the 2008 Golden Penguin Awards in the System Destruction category.

I'll *Second that Nomination*, and give him 10 points for guts!

---

### Post by Elfy on 2008-07-09
> Well, you can't say I didn't give you a heads-upHe he he - nearly blamed you, then I re-read your post - and realised it was all my own fault :D

---

### Post by Bruce M. on 2008-07-09
> **forestpixie said:**
> He he he - nearly blamed you, then I re-read your post - and realised it was all my own fault :D

Well, come on now, forest, you have to admit, you knew something was going to happen. :popcorn:

---

### Post by Elfy on 2008-07-09
No, no you misunderstand me - yes of course I knew that on the one hand I would end up needing a reinstall, but on the other hand I would only end up needing a reinstall :D

I 'nearly blamed' you because - 
Me - > I'm going to toss a coin tomorrow 15 times - because I can't be bothered to do it for longer, heads I do a chmod on my xubuntu vm, tails I do rm - etc on the /

You - > I thought I'd help, I just flipped 8 times:
first seven - heads
8th toss - tails

So I SHOULD have done the rm -Rf (or whatever) - but I didn't, I chmodded instead, and it was boring :)

So as I said I nearly blamed you, then re-read your post and it's my fault I did chmod :)

---

### Post by Bruce M. on 2008-07-09
Hi Folks,

For those who are still following this thread, please take a look at my new one:

:cry: ["Root" reclaimed my Partitions - files are missing!]("http://ubuntuforums.org/showthread.php?p=5352602#post5352602")

Thanks folks,
CHIMO!
BRUCE

---

