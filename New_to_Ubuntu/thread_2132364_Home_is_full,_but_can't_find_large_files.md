---
title: "Home is full, but can't find large files?"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by eappell on 2013-04-04
I'm running Ubuntu 12.04LTS with Amahi.  I'm having a problem I can't figure out how to resolve and hoping to get some help here...  My /home partition is reporting that it's full.  It's got 327GB of space, 311GB is used, and it's saying about 4kb is available.  Keep in mind, yesterday I had about 89% free on that partition.  So I [went to this article]("http://ubuntuforums.org/showthread.php?t=1122670") for help in finding the files that are growing out of control, but every command I run tells me that there is no large files.  If I can't find the problem files, I can't free up any space...  Here are the results of my analysis:
```
homeserver@homeserver-Z68MA-D2H-B3:~$ df -Th | grep -v "fs" | sort
/dev/sda2      ext4       42G  8.9G   31G  23% /
/dev/sda4      ext4      327G  311G  4.0K 100% /home
/dev/sda6      ext4      1.5T  1.2T  177G  88% /var/hda/drives/BigData
/dev/sdb1      fuseblk   932G  737G  195G  80% /var/hda/drives/internal_1
/dev/sdc1      ext4      917G  850G   21G  98% /var/hda/drives/internal_3
/dev/sdd1      fuseblk   932G  820G  112G  88% /var/hda/drives/external_5
/dev/sde1      fuseblk   1.9T  1.6T  226G  88% /var/hda/drives/external_4
/dev/sdf1      fuseblk   1.4T  1.4T   62G  96% /var/hda/drives/external_3
/dev/sdg1      fuseblk   1.9T  1.1T  767G  59% /var/hda/drives/external_2
/dev/sdh1      ext4      917G  421G  451G  49% /var/hda/drives/external_1
Filesystem     Type      Size  Used Avail Use% Mounted on
```

```
homeserver@homeserver-Z68MA-D2H-B3:~$ sudo du -h /home --max-depth=1
28K     /home/eddie
16K     /home/lost+found
28K     /home/jeanne
4.0K    /home/gh
48K     /home/sadmin
du: cannot access `/home/homeserver/.gvfs': Permission denied
3.1G    /home/homeserver
3.1G    /home
```

```
homeserver@homeserver-Z68MA-D2H-B3:/$ sudo du -h --max-depth=1 / | grep '[0-9]G\>'
du: cannot access `/proc/8077/task/8077/fd/4': No such file or directory
du: cannot access `/proc/8077/task/8077/fdinfo/4': No such file or directory
du: cannot access `/proc/8077/fd/4': No such file or directory
du: cannot access `/proc/8077/fdinfo/4': No such file or directory
3.2G    /usr
du: cannot access `/home/homeserver/.gvfs': Permission denied
3.1G    /home
```

See, nothing so large that it would take up nearly 300GB...  I ran baobab and it shows the partition is full, but when I go to /home the details don't show any large files.  It's weird.  I'm at a loss, and given my extreme inexperience with Linux, I'm not sure what to do at this point.  I just know that if I reboot I probably won't be able to get back in, so I'm hoping for some guidance.

Thanks!

Eddie

---

### Post by r-senior on 2013-04-04
Pressing "Scan Home" on Disk Usage Analyzer (baobab) should show you where the space is being used.

Alternatively, try:

```
cd ~
du -sBG .[!.]* * | sort -rn | head -10
```

That is a du command that looks at normal and hidden files, sorts into size order and displays the top ten directories or files in GB.

---

### Post by sudodus on 2013-04-04
What about this one:

```
du: cannot access `/home/homeserver/.gvfs': Permission denied
```

Will it ring any bells?

---

### Post by eappell on 2013-04-04
Thanks for the quick replies!  I did do a scan home this morning (I'm at work now and can only access via terminal) and it didn't show any major files or folders, which confused me.

I ran the command you suggested and got this:
```
homeserver@homeserver-Z68MA-D2H-B3:/$ cd ~
homeserver@homeserver-Z68MA-D2H-B3:~$ du -sBG .[!.]* * | sort -rn | head -10
2G      Public
1G      .Xauthority
1G      .thumbnails
1G      Templates
1G      .sickbeard
1G      .sabnzbd
1G      .rpmdb
1G      .remmina
1G      .pypar2
1G      .pulse-cookie
```
Which looks like it's not really using up that space, so I'm still confused.

@sudodus - Thanks, it did raise an alarm, but I don't know what .gvfs is for, and there are a few folders that I get that on, so I wasn't sure if it was supposed to be that way.  How can I get more info on that?  I tried to find the space being used by that but wasn't successful...  Any advice?

---

### Post by sudodus on 2013-04-04
> **eappell said:**
> 
@sudodus - Thanks, it did raise an alarm, but I don't know what .gvfs is for, and there are a few folders that I get that on, so I wasn't sure if it was supposed to be that way.  How can I get more info on that?  I tried to find the space being used by that but wasn't successful...  Any advice?

Browse the internet for ***.gvfs*** in general and look at this link in particular. Maybe it's a bug.

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=1909971[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1909971")[COLOR=#ff0000]

[/COLOR][[COLOR=#ff0000]http://forums.opensuse.org/english/get-technical-help-here/applications/387162-permission-denied-gvfs.html[/COLOR]]("http://forums.opensuse.org/english/get-technical-help-here/applications/387162-permission-denied-gvfs.html")[COLOR=#ff0000]

[/COLOR][COLOR=#ff0000]



[/COLOR]

---

### Post by eappell on 2013-04-04
Thanks for the links!  I checked them out, and they basically recommended unmounting .gvfs, so I did that.  Unfortunately it looks like home is still full though.  Do I need to reboot to see the change?  Here's my results now after unmounting .gvfs:
```
homeserver@homeserver-Z68MA-D2H-B3:~$ df -Th | grep -v "fs" | sort
/dev/sda2      ext4       42G  8.9G   31G  23% /
/dev/sda4      ext4      327G  311G  4.0K 100% /home
/dev/sda6      ext4      1.5T  1.2T  177G  88% /var/hda/drives/BigData
/dev/sdb1      fuseblk   932G  737G  195G  80% /var/hda/drives/internal_1
/dev/sdc1      ext4      917G  850G   21G  98% /var/hda/drives/internal_3
/dev/sdd1      fuseblk   932G  820G  112G  88% /var/hda/drives/external_5
/dev/sde1      fuseblk   1.9T  1.6T  226G  88% /var/hda/drives/external_4
/dev/sdf1      fuseblk   1.4T  1.4T   62G  96% /var/hda/drives/external_3
/dev/sdg1      fuseblk   1.9T  1.1T  767G  59% /var/hda/drives/external_2
/dev/sdh1      ext4      917G  421G  450G  49% /var/hda/drives/external_1
Filesystem     Type      Size  Used Avail Use% Mounted on

homeserver@homeserver-Z68MA-D2H-B3:~$ sudo du -h /home --max-depth=1
4.0K    /home/apache
28K     /home/eddie
16K     /home/lost+found
28K     /home/jeanne
4.0K    /home/gh
48K     /home/sadmin
3.1G    /home/homeserver
3.1G    /home

homeserver@homeserver-Z68MA-D2H-B3:~$
```

---

### Post by sudodus on 2013-04-04
And the other thread suggested to remove it.

It is always good to reboot.

---

### Post by eappell on 2013-04-04
Yep, after reboot I've got 307GB available now.  Thanks for the help!!

---

