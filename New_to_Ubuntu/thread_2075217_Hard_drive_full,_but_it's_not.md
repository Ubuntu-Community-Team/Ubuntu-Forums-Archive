---
title: "Hard drive full, but it's not?"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by Old_Brewer on 2012-10-23
Hi all  System monitor says I have total 35.3 GB in /dev/ds1, 5.7 GB free, 3.9 GB free, 29.6 GB used.  I think that I do not have much data stored on the computer.  Also:
 root@joebelle-laptop:/# du -h --max-depth=1
4.7G    ./var
du: cannot access `./proc/12247/task/12247/fd/4': No such file or directory
du: cannot access `./proc/12247/task/12247/fdinfo/4': No such file or directory
du: cannot access `./proc/12247/fd/4': No such file or directory
du: cannot access `./proc/12247/fdinfo/4': No such file or directory
0    ./proc
840K    ./dev
100K    ./tmp
277M    ./opt
0    ./sys
4.0K    ./mnt
12K    ./media
16K    ./lost+found
22M    ./etc
du: cannot access `./home/joebelle/.gvfs': Permission denied
4.7G    ./home
6.6M    ./bin
4.5G    ./usr
4.0K    ./selinux
222M    ./boot
7.8M    ./sbin
1.6G    ./lib
200K    ./srv
14G    ./root
2.9M    ./ndiswrapper
4.0K    ./initrd
30G    .
The last line (30G  .) really confuses me.  
When I do:  gksudo nautilus, and look at /, I get:  Contents:  564,077 items, totalling 15.2 GB  Free space: 3.9 GB
I cut & paste my backup data every week or two to an external drive, but I rarely have more free space that 5 GB.  Where am I using most of my HD space, and how can I recover some of it.  Thanks!  PS Ubuntu 10.04 Kernel 2.6.32-44 generic GNOME 2.30.2  Thanks again

---

### Post by philinux on 2012-10-23
This should help.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by Cheesemill on 2012-10-23
30GB is the total size of everything in /, in other words everything stored in your filesystem.
14GB is a large amount of stuff to have in /root, do you know what's in there?
```
sudo ls -lha /root
```

---

### Post by Old_Brewer on 2012-10-23
> **Cheesemill said:**
> 30GB is the total size of everything in /, in other words everything stored in your filesystem.
14GB is a large amount of stuff to have in /root, do you know what's in there?
```
sudo ls -lha /root
```

I hope this helps.  I ran it after I got this message, and installed "total"
The program 'total' is currently not installed.  You can install it by typing:
apt-get install radiance

joebelle@joebelle-laptop:~$ sudo ls -lha /root
[sudo] password for joebelle: 
total 144K
drwxr-xr-x 23 root root 4.0K 2012-10-08 06:35 .
drwxr-xr-x 23 root root 4.0K 2012-10-11 06:14 ..
-rw-r--r--  1 root root   36 2011-04-15 10:55 *a
-rw-r--r--  1 root root   37 2011-04-15 10:56 *-a
drwx------  2 root root 4.0K 2011-08-26 15:38 .aptitude
-rw-------  1 root root 7.3K 2012-10-23 08:27 .bash_history
-rw-r--r--  1 root root 2.2K 2007-05-15 11:07 .bashrc
drwx------  3 root root 4.0K 2012-08-05 12:22 .cache
drwx------  6 root root 4.0K 2012-04-07 07:48 .config
drwx------  3 root root 4.0K 2010-07-22 20:54 .dbus
-rw-------  1 root root  353 2011-07-05 11:29 dead.letter
drwxr-xr-x  2 root root 4.0K 2011-08-26 15:38 .debtags
drwxr-xr-x  2 root root 4.0K 2011-07-04 17:17 Desktop
-rw-------  1 root root   16 2011-05-19 16:34 .esd_auth
-rw-r--r--  1 root root  934 2011-07-04 21:54 .fstab.log
drwx------  3 root root 4.0K 2012-10-23 06:48 .gconf
drwx------  2 root root 4.0K 2012-10-23 06:49 .gconfd
drwx------  7 root root 4.0K 2012-08-05 12:22 .gnome2
drwx------  2 root root 4.0K 2008-04-28 19:44 .gnome2_private
drwxr-xr-x  2 root root 4.0K 2012-04-07 09:11 .gstreamer-0.10
-rw-r--r--  1 root root  286 2011-09-07 06:56 .gtk-bookmarks
drwx------  2 root root 4.0K 2011-05-28 17:12 .gvfs
drwx------  3 root root 4.0K 2011-05-19 16:19 .kde
drwxr-xr-x  3 root root 4.0K 2011-05-19 15:47 .local
drwx------  2 root root 4.0K 2010-07-22 20:54 .mozilla
drwxr-xr-x  2 root root 4.0K 2011-07-04 17:17 .nautilus
-rw-r--r--  1 root root  141 2007-05-15 11:07 .profile
drwx------  2 root root 4.0K 2011-12-08 11:28 .pulse
-rw-------  1 root root  256 2010-08-27 13:36 .pulse-cookie
-rw-------  1 root root  965 2012-10-08 06:35 .recently-used.xbel
-rw-------  1 root root 1.0K 2008-05-15 18:31 .rnd
drwx------  4 root root 4.0K 2012-10-14 09:36 .synaptic
drwx------  3 root root 4.0K 2011-07-05 11:16 .thumbnails
drwxr-xr-x  2 root root 4.0K 2010-08-27 10:26 .ure
drwxr-xr-x  2 root root 4.0K 2009-09-15 15:01 .wapi
joebelle@joebelle-laptop:~$ pwd
/home/joebelle

---

### Post by Old_Brewer on 2012-10-23
> **philinux said:**
> This should help.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Thanks for the guide.  I'll start working on this after morning "chores".

---

### Post by Wim Sturkenboom on 2012-10-23
Rather run du -h --max-depth=1 /root. I don't think ls -lha shows the full details ;)

And please use code tags
[noparse]```

paste results here

```[/noparse]

```

wim@i3-2120:/mnt$ sudo du -h --max-depth=1 /root
452K	/root/.synaptic
12K	/root/.config
4,0K	/root/.pulse
8,0K	/root/.cache
12K	/root/.dbus
28K	/root/.gnupg
536K	/root
wim@i3-2120:/mnt$ 

```

---

### Post by Old_Brewer on 2012-10-23
[QUOTE=Wim Sturkenboom;12313442]Rather run du -h --max-depth=1 /root. I don't think ls -lha shows the full details ;)

And please use code tags
[noparse]```

paste results here

```[/noparse]

[code]
4.0K    /root/Desktop
8.0K    /root/.ure
4.0K    /root/.mozilla
4.0K    /root/.gvfs
284K    /root/.gconf
4.0K    /root/.wapi
4.0K    /root/.gnome2_private
840K    /root/.synaptic
4.0K    /root/.aptitude
316K    /root/.thumbnails
604K    /root/.gstreamer-0.10
4.0K    /root/.nautilus
36K    /root/.config
4.0K    /root/.pulse
72K    /root/.gnome2
4.0K    /root/.debtags
12K    /root/.gconfd
14G    /root/.local
16K    /root/.cache
12K    /root/.dbus
12K    /root/.kde
14G    /root

---

### Post by 3dmatrix on 2012-10-23
Try emptying your root Trash !

---

### Post by Wim Sturkenboom on 2012-10-24
> **Old_Brewer said:**
> 
```

4.0K    /root/Desktop
8.0K    /root/.ure
4.0K    /root/.mozilla
4.0K    /root/.gvfs
284K    /root/.gconf
4.0K    /root/.wapi
4.0K    /root/.gnome2_private
840K    /root/.synaptic
4.0K    /root/.aptitude
316K    /root/.thumbnails
604K    /root/.gstreamer-0.10
4.0K    /root/.nautilus
36K    /root/.config
4.0K    /root/.pulse
72K    /root/.gnome2
4.0K    /root/.debtags
12K    /root/.gconfd
14G    /root/.local
16K    /root/.cache
12K    /root/.dbus
12K    /root/.kde
14G    /root

Nearly there ;) You forgot the closing [noparse]
```[/noparse]

OK, check the .local directory. You can drill down further
```

du -h --max-depth=1 /root/.local

```
till you find the culprit.

The suggestion by 3dmatrix might do the trick. Question remains how you got that much in there? An correct copy? Or an extensive (and not necessary) use of *_gksudo nautilus_* or even an enabled root account?

---

### Post by Old_Brewer on 2012-10-24
> **Wim Sturkenboom said:**
> Nearly there ;) You forgot the closing [noparse][/code][/noparse]

OK, check the .local directory. You can drill down further
```

du -h --max-depth=1 /root/.local

```till you find the culprit.

The suggestion by 3dmatrix might do the trick. Question remains how you got that much in there? An correct copy? Or an extensive (and not necessary) use of *_gksudo nautilus_* or even an enabled root account?

I've looked up code tags, unfortunately I do not understand them.  Here is some additional info:
root@joebelle-laptop:~# du -h --max-depth=1 /root/.local
14G    /root/.local/share
14G    /root/.local
root@joebelle-laptop:~#

---

### Post by Wim Sturkenboom on 2012-10-24
OK, don't worry; if you quote a post that contains a code block, you can see how it is done.
[LIST]
[*]type [noparse]```
[/noparse]
[*]after the word [noparse][code][/noparse], paste the result of the command.
[*]goto the end of the pasted result and type [noparse]
```[/noparse]
[/LIST]
From your results, there is only one directory called 'share'. You need to drill down a level further into that one
```

du -h --max-depth=1 /root/.local/share

```
And possibly drill down a bit further again into the biggest directory.

---

### Post by Old_Brewer on 2012-10-24
> **Wim Sturkenboom said:**
> OK, don't worry; if you quote a post that contains a code block, you can see how it is done.
[LIST]
[*]type [noparse]```
[/noparse]
[*]after the word [noparse][code][/noparse], paste the result of the command.
[*]goto the end of the pasted result and type [noparse]
```[/noparse]
[/LIST]
From your results, there is only one directory called 'share'. You need to drill down a level further into that one
```

du -h --max-depth=1 /root/.local/share

```And possibly drill down a bit further again into the biggest directory.

Thank you!  I think we are getting somewhere.  Here are some results:

root@joebelle-laptop:~# du -h --max-depth=1 /root/.local/share
```

4.0K    /root/.local/share/ubuntuone
28K    /root/.local/share/webkit
8.0K    /root/.local/share/applications
14G    /root/.local/share/Trash
16K    /root/.local/share/rhythmbox
14G    /root/.local/share

```root@joebelle-laptop:~# du -h --max-depth=1 /root/.local/share/Trash/files
```

240M    /root/.local/share/Trash/files/2012-06-23_18.30.03.093180.joebelle-laptop.inc
446M    /root/.local/share/Trash/files/2012-06-20_18.30.03.221521.joebelle-laptop.inc
455M    /root/.local/share/Trash/files/2012-06-21_18.30.03.203523.joebelle-laptop.inc
450M    /root/.local/share/Trash/files/2012-06-15_18.30.02.755488.joebelle-laptop.inc
3.1G    /root/.local/share/Trash/files/2012-06-02_18.30.03.518514.joebelle-laptop.ful
385M    /root/.local/share/Trash/files/2012-10-04_18.30.04.840961.joebelle-laptop.inc
372M    /root/.local/share/Trash/files/2012-10-05_18.30.03.213895.joebelle-laptop.inc
440M    /root/.local/share/Trash/files/2012-06-19_18.30.02.973563.joebelle-laptop.inc
327M    /root/.local/share/Trash/files/2012-09-30_18.30.03.586243.joebelle-laptop.inc
456M    /root/.local/share/Trash/files/2012-06-22_18.30.03.833874.joebelle-laptop.inc
237M    /root/.local/share/Trash/files/2012-10-03_18.30.03.186161.joebelle-laptop.inc
358M    /root/.local/share/Trash/files/2012-09-28_18.30.04.048463.joebelle-laptop.inc
359M    /root/.local/share/Trash/files/2012-09-29_18.30.02.856955.joebelle-laptop.inc
427M    /root/.local/share/Trash/files/2012-06-17_18.30.02.643101.joebelle-laptop.inc
332M    /root/.local/share/Trash/files/2012-10-02_18.30.02.652512.joebelle-laptop.inc
436M    /root/.local/share/Trash/files/2012-06-18_18.30.03.817690.joebelle-laptop.inc
352M    /root/.local/share/Trash/files/2012-10-06_18.30.04.564142.joebelle-laptop.inc
3.4G    /root/.local/share/Trash/files/2012-06-13_18.30.03.819940.joebelle-laptop.ful
222M    /root/.local/share/Trash/files/2012-06-16_18.32.56.450925.joebelle-laptop.inc
436M    /root/.local/share/Trash/files/2012-06-14_18.30.10.482826.joebelle-laptop.inc
246M    /root/.local/share/Trash/files/2012-09-27_18.30.03.222151.joebelle-laptop.inc
331M    /root/.local/share/Trash/files/2012-10-01_18.30.02.792582.joebelle-laptop.inc
14G    /root/.local/share/Trash/files

```The above files seem to have the same structure as my backup files.  Can I delete the above files?

root@joebelle-laptop:~# cd /var/backup
Here is the structure of my current backup files that I have not yet moved to the external HD:

root@joebelle-laptop:/var/backup# du -h --max-depth=1 /var/backup
```

277M    /var/backup/2012-10-16_18.30.05.195639.joebelle-laptop.inc
279M    /var/backup/2012-10-17_18.30.02.502022.joebelle-laptop.inc
289M    /var/backup/2012-10-21_18.30.02.949648.joebelle-laptop.inc
270M    /var/backup/2012-10-18_18.30.02.832056.joebelle-laptop.inc
283M    /var/backup/2012-10-22_18.30.04.840339.joebelle-laptop.inc
252M    /var/backup/2012-10-20_18.30.03.081201.joebelle-laptop.inc
2.3G    /var/backup/2012-10-15_18.30.02.868882.joebelle-laptop.ful
254M    /var/backup/2012-10-23_18.30.03.020718.joebelle-laptop.inc
245M    /var/backup/2012-10-19_18.30.02.574972.joebelle-laptop.inc
4.4G    /var/backup

```Thanks for your help!  Also thanks for the help with "code", that's cool stuff.

I also found this link:  [http://ubuntuforums.org/showthread.php?t=2033770](http://ubuntuforums.org/showthread.php?t=2033770)
With this information:  July 27th, 2012 			 			 		 		 			  			#[**10**]("http://ubuntuforums.org/showpost.php?p=12132951&postcount=10") 			 		 	   	  			 				 				[Bufeu]("http://ubuntuforums.org/member.php?u=1675569") 				 				 			
  			Gee!  These Aren't Roasted!
 			[IMG]http://ubuntuforums.org/images/rank_4.png[/IMG]
 			  			  			 				 
				Join Date: Jun 2012
 				Location: Sweden
 				 	  					Beans: 170 				
 			       Ubuntu 12.04 Precise Pangolin  				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Re: Missing hard drive space...** 			
 			 			 		   		 		 		The path to the Trash is **/home/username/.local/share/Trash**. If you deleted something as root (e.g. deleted a file using Nautilus invoked via gksu), it's at: **/root/.local/share/Trash**.

So, I think I see what is going on now.  I was deleting some backup files with the command line, & I'm sure I had to be root to do it.  I'll keep checking to see if "gksudo nautilus" has the same effect.  Now I am using "gksudo nautilus" to cut & paste the backup info to the external drive.  I'll keep monitoring.  I think we have a solution.  Thanks for all of the help.  I'll wait a bit & then consider this problem solved.

---

### Post by Wim Sturkenboom on 2012-10-24
If you have a setup where you have enabled root login into the graphical environment, you can simply empty the trash by login' in as root.

If not, you can safely delete the whole trash folder. Safest is to use *_gksudo nautilus_*

PS
you need to make hidden files visible in nautilus ( shortcut <ctrl>H ) else you will not see the '.local' directory.

---

### Post by Old_Brewer on 2012-10-24
[QUOTE=Wim Sturkenboom;12315418]If you have a setup where you have enabled root login into the graphical environment, you can simply empty the trash by login' in as root.

If not, you can safely delete the whole trash folder. Safest is to use *_gksudo nautilus_*

PS
you need to make hidden files visible in nautilus ( shortcut <ctrl>H ) else you will not see the '.local' directory.[/QU

I'm using gksudo nautilus, but the files seem to be going into the trash with .trashinfo appended to them.  I've done this several times, now I'm really concerned that I have no disk space.  Is there another way, or what am I doing wrong?

I finally did this:
If you use 'gksudo nautilus', the deleted files end up in root's trash  and cannot be deleted by normal users. And use SHIFT-DELETE to delete  the actual Trash files or the files might just be deleted to ... the  trash folder!  :wink:
# du -h --max-depth=1 /root/.local/share
```

4.0K    /root/.local/share/ubuntuone
28K    /root/.local/share/webkit
8.0K    /root/.local/share/applications
48K    /root/.local/share/Trash
16K    /root/.local/share/rhythmbox
108K    /root/.local/share

```

Thanks for your patience & help!




edit follows:
# du -h --max-depth=1 /root/.local/share
```

4.0K    /root/.local/share/ubuntuone
28K    /root/.local/share/webkit
8.0K    /root/.local/share/applications
14G    /root/.local/share/Trash
16K    /root/.local/share/rhythmbox
14G    /root/.local/share

```

---

### Post by Elfy on 2012-10-24
If you are in nautilus and are sure you are in the right place - then shift+delete to completely delete them

---

### Post by Old_Brewer on 2012-10-24
> **Elfy said:**
> If you are in nautilus and are sure you are in the right place - then shift+delete to completely delete them

Yes!  The shift+delete did it.  Thank you

---

### Post by Elfy on 2012-10-24
> **Old_Brewer said:**
> Yes!  The shift+delete did it.  Thank you

Welcome - just bear in mind how easy it was to delete those - you could do the same in a gksu nautilus to any of the system files and be posting "Whoops" thread :)

---

### Post by Old_Brewer on 2012-10-24
> **Elfy said:**
> Welcome - just bear in mind how easy it was to delete those - you could do the same in a gksu nautilus to any of the system files and be posting "Whoops" thread :)

Yes!  Thanks.   I am also familiar with rm -r * :)

---

### Post by Elfy on 2012-10-24
Just making sure :)

You can mark this solved in Thread Tools.

---

### Post by Wim Sturkenboom on 2012-10-24
Now just keep an eye on it. As those were all backups, did you delete them yourself (as root) or do you use an application that moves it to the trash. In the first case, use <shift><delete> in future; in the second case, check of you can change the behaviour.

> **Old_Brewer said:**
> Yes!  The shift+delete did it.  Thank you
In my 10.04 system that was not necessary; 'deleting the trash' told me that it could not be done and would permanently delete. This was with a normal user, though I don't think it makes a difference.

> **Old_Brewer said:**
> Yes!  Thanks.   I am also familiar with rm -r * :)
I did not want to suggest that as one mistake could have wiped your system. But I indeed would have used rm -rf

---

### Post by Old_Brewer on 2012-10-24
> **Wim Sturkenboom said:**
> Now just keep an eye on it. As those were all backups, did you delete them yourself (as root) or do you use an application that moves it to the trash. In the first case, use <shift><delete> in future; in the second case, check of you can change the behaviour.


In my 10.04 system that was not necessary; 'deleting the trash' told me that it could not be done and would permanently delete. This was with a normal user, though I don't think it makes a difference.


I did not want to suggest that as one mistake could have wiped your system. But I indeed would have used rm -rf

Thanks for all of your help and tips.  I have saved this link, and additional notes into my Read.Me file that I use when I am copying my backup to the external drive.

---

