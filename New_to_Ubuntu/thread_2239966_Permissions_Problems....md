---
title: "Permissions Problems..."
date: 2014-08-16
forum: New to Ubuntu
---

### Post by BlueAZ on 2014-08-16
Greetings!   First, I have been searching and reading on this for a couple hours, but still can't figure out what to do.

I've upgraded my 64-bit AMD quad-core system to 14.04.  When I did, I copied all the folders I'd had in my 13.04 Home folder in a backup stored on the hard drive into the new Home folder.  I also created a separate 22 Gb partition where I hoped to store future backups.  Seemed smart, right?

Now I find I don't have permission to use the partition I created, and can't seem to change that.  I tried to use the built-in Backup utility.  It said I don't have permission for that partition.  Then I tried to backup to my current partition, which is huge, and it said I didn't have permission for that either.  I went into gksu Nautilus.  It shows my Home folder with only one thing in it:  Desktop.  Where are my other folders?   It also doesn't show the 22 Gb partition.

I'm scared to start messing with chmod, as I really don't know what I'm doing here.  I can use the Terminal for simple things, but mostly have to copy + paste from a reliable source.

If I've got things too screwed up already, please offer a way to create a good backup that doesn't require risking my working system.

Thanks!

---

### Post by Bashing-om on 2014-08-16
BlueAZ; Hello once more !

1st of all, do you mind working from the terminal ?
2nd, let's address one issue at a time - all my little mind can deal with -
Let's begin by looking at what the partitioning is like, 
then we get to what file systems are on those partitions, and then what files are in those file systems; where, accessibility.

post back:
```

sudo fdisk -lu
sudo blkid

``` and we have a discussion.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by BlueAZ on 2014-08-17
[COLOR=#000080]Hi Bashing,[/COLOR]   I'll paste output below.  Don't know how to make those code boxes you use...  sdb is a separate hard drive with Windows (using it hardly ever now).

```
******:~$ sudo fdisk -lu 

Disk /dev/sda: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000de26a 

   Device Boot      Start         End       Blocks   Id   System 
/dev/sda1   *        2048   559599615   279798784   83  Linux 
/dev/sda2       616755198   625141759     4193281    5  Extended 
/dev/sda3       574539776   616753151    21106688   83  Linux 
/dev/sda5       616755200   625141759     4193280   82  Linux swap / Solaris 

Partition table entries are not in disk order 

Disk /dev/sdb: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000a2c47 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT 
/dev/sdb2          206848   473751551   236772352    7  HPFS/NTFS/exFAT 
```

```
*******:~$ sudo blkid 

/dev/sda1: UUID="21675f9c-5c12-46c3-b53f-98205e41882f" TYPE="ext4" 
/dev/sda3: UUID="fafd22c8-8502-49ef-b024-a1d3d1c63b04" TYPE="ext4" 
/dev/sda5: UUID="04957b49-d18a-4170-861c-58f24d6e2487" TYPE="swap" 
/dev/sdb1: LABEL="System Reserved" UUID="F4E01C8AE01C5568" TYPE="ntfs" 
/dev/sdb2: UUID="B63E1F643E1F1D45" TYPE="ntfs" 
```

Thanks!

---

### Post by JKyleOKC on 2014-08-17
> **BlueAZ said:**
> [COLOR=#000080]Hi Bashing,[/COLOR]   I'll paste output below.  **Don't know how to make those code boxes you use**...  sdb is a separate hard drive with Windows (using it hardly ever now).

Thanks!

To make the boxes, use the button "#" in the message editor, then paste between the two commands that it inserts into your message. Here's what you'll get:
```
******:~$ sudo fdisk -lu 

Disk /dev/sda: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000de26a 

   Device Boot      Start         End       Blocks   Id   System 
/dev/sda1   *        2048   559599615   279798784   83  Linux 
/dev/sda2       616755198   625141759     4193281    5  Extended 
/dev/sda3       574539776   616753151    21106688   83  Linux 
/dev/sda5       616755200   625141759     4193280   82  Linux swap / Solaris 

Partition table entries are not in disk order 

Disk /dev/sdb: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000a2c47 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT 
/dev/sdb2          206848   473751551   236772352    7  HPFS/NTFS/exFAT 

```
```
*******:~$ sudo blkid 

/dev/sda1: UUID="21675f9c-5c12-46c3-b53f-98205e41882f" TYPE="ext4" 
/dev/sda3: UUID="fafd22c8-8502-49ef-b024-a1d3d1c63b04" TYPE="ext4" 
/dev/sda5: UUID="04957b49-d18a-4170-861c-58f24d6e2487" TYPE="swap" 
/dev/sdb1: LABEL="System Reserved" UUID="F4E01C8AE01C5568" TYPE="ntfs" 
/dev/sdb2: UUID="B63E1F643E1F1D45" TYPE="ntfs" 



```Your message pretty much held its original format; many listings though don't, so using the CODE boxes is always preferred and once you know the trick, it's quite easy to do.

---

### Post by deadflowr on 2014-08-17
[How-To Code Tags on the forums]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

I've already edited the code tags in post #3, but use this for future reference.

Also, sometimes you might accidentally click on something like quote tags and want to change it.
To do so, simply click on the button marked edit, edit the post and then click save.

---

### Post by Bashing-om on 2014-08-17
BlueAZ; Well,

So far so good. Looks fine !
Let's mount the partitions manually - one at a time - and look at what you have for access.
```

sudo mkdir /mnt/work
sudo mount /dev/sda3 /mnt/work
ls -al /mnt
ls -al /mnt/work
sudo umount /mnt/work

sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test
ls -al /mnt
ls -al /mnt/test
sudo umount /mnt/test

```
I can expect, that you as a 'user' do not have access to see, we will change that .

And once these are known we can discuss how you want to change them, who do you want to have access to these files systems ?

[INDENT][INDENT]all in the care and feeding
[INDENT][INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by BlueAZ on 2014-08-17
Hello,   I see one needs to choose Advanced Reply to use the # symbol.  I've been using Quick Reply.  So now I know!

Thanks for putting everything down in code.  I first tried pasting just the top line, then realized it was in 2 sections so I'd paste it in that way.  It shows everything as Root-owned.  I'm leaving my name in so you can see.  I'm still unclear as to why Root is different from Blue (me).  This is a one-person computer with minimal security needs.
OK, here's the Code:
```
   [FONT=Ubuntu]blue@blue-IC780M-A:~$ sudo mkdir /mnt/work [/FONT]
 [FONT=Ubuntu][sudo] password for blue:  [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ sudo mkdir /mnt/work [/FONT]
 [FONT=Ubuntu]mkdir: cannot create directory ‘/mnt/work’: File exists [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ sudo mount /dev/sda3 /mnt/work [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ ls -al /mnt [/FONT]
 [FONT=Ubuntu]total 12 [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  3 root root 4096 Aug 17 15:07 . [/FONT]
 [FONT=Ubuntu]drwxr-xr-x 29 root root 4096 Aug 14 17:21 .. [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  3 root root 4096 Jun  4 13:54 work [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ ls -al /mnt/work [/FONT]
 [FONT=Ubuntu]total 24 [/FONT]
 [FONT=Ubuntu]drwxr-xr-x 3 root root  4096 Jun  4 13:54 . [/FONT]
 [FONT=Ubuntu]drwxr-xr-x 3 root root  4096 Aug 17 15:07 .. [/FONT]
 [FONT=Ubuntu]drwx------ 2 root root 16384 Jun  4 13:54 lost+found [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ sudo umount /mnt/work [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ sudo mkdir /mnt/test [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ sudo mount /dev/sda1 /mnt/test [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ ls -al /mnt [/FONT]
 [FONT=Ubuntu]total 16 [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  4 root root 4096 Aug 17 15:09 . [/FONT]
 [FONT=Ubuntu]drwxr-xr-x 29 root root 4096 Aug 14 17:21 .. [/FONT]
 [FONT=Ubuntu]drwxr-xr-x 29 root root 4096 Aug 14 17:21 test [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  2 root root 4096 Aug 17 15:07 work [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ ls -al /mnt/test [/FONT]
 [FONT=Ubuntu]total 144 [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  29 root root  4096 Aug 14 17:21 . [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   4 root root  4096 Aug 17 15:09 .. [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Aug 14 18:29 bin [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   4 root root  4096 Aug 14 18:29 boot [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Apr  1 15:47 cdrom [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   4 root root  4096 Apr 16 18:26 dev [/FONT]
 [FONT=Ubuntu]drwxr-xr-x 143 root root 12288 Aug 17 15:09 etc [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   3 root root  4096 Jun  5 10:41 home [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   3 root root  4096 Apr  1 15:55 home_backup [/FONT]
 [FONT=Ubuntu]lrwxrwxrwx   1 root root    33 Aug 14 17:21 initrd.img -> boot/initrd.img-3.13.0-34-generic [/FONT]
 [FONT=Ubuntu]lrwxrwxrwx   1 root root    33 Jul 19 17:58 initrd.img.old -> boot/initrd.img-3.13.0-32-generic [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  24 root root  4096 Aug  8 12:46 lib [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Aug  8 12:46 lib32 [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Aug  8 12:46 lib64 [/FONT]
 [FONT=Ubuntu]drwx------   2 root root 16384 Apr  1 15:42 lost+found [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   4 root root  4096 Apr 16 18:21 media [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   4 root root  4096 Aug 17 15:09 mnt [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Jun  4 15:50 new [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Jun  4 15:49 old [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   3 root root  4096 Apr 16 18:21 opt [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Apr 10 15:12 proc [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Jun  4 16:05 recovery [/FONT]
 [FONT=Ubuntu]drwx------   9 root root  4096 Aug 16 17:08 root [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  12 root root  4096 Apr 16 18:27 run [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root 12288 Aug 14 18:28 sbin [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Jun 11  2012 selinux [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Apr 16 18:21 srv [/FONT]
 [FONT=Ubuntu]drwxr-xr-x   2 root root  4096 Mar 12 18:41 sys [/FONT]
 [FONT=Ubuntu]drwxrwxrwt   6 root root  4096 Aug 17 14:58 tmp [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  11 root root  4096 Jun 10 14:06 usr [/FONT]
 [FONT=Ubuntu]drwxr-xr-x  14 root root  4096 Jul  8 13:27 var [/FONT]
 [FONT=Ubuntu]lrwxrwxrwx   1 root root    30 Aug 14 17:21 vmlinuz -> boot/vmlinuz-3.13.0-34-generic [/FONT]
 [FONT=Ubuntu]lrwxrwxrwx   1 root root    30 Jul 19 17:58 vmlinuz.old -> boot/vmlinuz-3.13.0-32-generic [/FONT]
 [FONT=Ubuntu]blue@blue-IC780M-A:~$ sudo umount /mnt/test [/FONT]


```

Thank you so much,   Blue

---

### Post by Bashing-om on 2014-08-17
BlueAZ; Well;

UnGood!
> 
blue@blue-IC780M-A:~$ ls -al /mnt/work 
 total 24 
 drwxr-xr-x 3 root root  4096 Jun  4 13:54 . 
 drwxr-xr-x 3 root root  4096 Aug 17 15:07 .. 
 drwx------ 2 root root 16384 Jun  4 13:54 lost+found 
 Unless you are not posting the complete output, there are no accesssable files presently on that file system;
Once more mount 'sda3' to '/mnt/work' and let's dig a bit and see what is there:
```

ls -al /mnt/work/lost+found

```
see what we might be able to "recover".

Pending is digging a step deeper into sda1 ( /home) but for now 'sda3' will keep us occupied.

[INDENT][INDENT]sad when backups are not backups
[/INDENT][/INDENT]

---

### Post by BlueAZ on 2014-08-17
Oh dear, I think I mis-explained the situation!  sda3 is the partition I made to store NEW backups -- it should be empty, as I have not gotten permission to use it.  I was able to retrieve the backup from 13.04 and have them in my Home folder in 14.04.  My original question was how to gain permission to use sda3.  I was also nonplussed when gksu Nautilus showed a Home folder with none of my personal folders and files.  My guess being that in gksu Nautilus I don't have permission to access them.  But I can access them normally in the regular Nautilus screen.  Does that make better sense?

In any case, here is the code from the op you asked me to do:
```
blue@blue-IC780M-A:~$ ls -al /mnt/work/lost+found
ls: cannot access /mnt/work/lost+found: No such file or directory
blue@blue-IC780M-A:~$ 


```

With boundless gratitude,   Blue

---

### Post by nerdtron on 2014-08-17
> gksu Nautilus I don't have permission to access them
You sure about this? Can you try it again? When you run nautilus as gksu, you are effectively root, when you to any folder on the system, you should be able to delete/modify anything. On this mode, you be able to delete/copy anything you want, anywhere you want.

---

### Post by Bashing-om on 2014-08-17
BlueAZ; Well, 

No, I can be dense as a rock sometimes, and others I can have a bad case of tunnel vision.

Let's address the access to 'sda3':
Say you like my name for that mount point and decide to keep it, and we stipulate that your 'username' is "blue" :
IF you do a number such as:
```

sudo mount /dev/sda3 /mnt/work
sudo chown -R blue:blue /mnt/work
sudo umount /mnt/work

```
Then only you (blue) and root have access to the file system(s) on that device. [I prefer it that way in my system for backups].

Now, as to 'nautilus' not able to see files when invoked with elevated privileges, that you can see as a normal 'user' - I have not a clue. Totally contrary to my way of thinking, as 'gksu' is total access authority in the GUI application.

EDIT: keep in mind ALL files in your /home directory should be owned by "you".

And by the way, copying files from your /home directory, to the backup directory owned by you will not require elevated access privileges. And doing so 'might' have undesired side effects !

I am a firm believer in the KISS principal.

[INDENT][INDENT]if you do not need,
[INDENT][INDENT][INDENT][/INDENT]don't
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by BlueAZ on 2014-08-17
OK, here's what happened:  In T gksu Nautilus brings up a Home folder that only contains Desktop.  My other folders not there.  Still in gksu Nt., if I click on Computer, it opens with the Root folder highlighted.  If I click on the Home folder in the Computer folder, my regular Home folder opens.  I'll try to attach a couple screen shots.

Meanwhile, Terminal is still open when I close gksu Naut. and it finally shows some text:
```
blue@blue-IC780M-A:~$ gksu nautilus
Initializing nautilus-dropbox 1.6.1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3479): GLib-CRITICAL **: Source ID 97 was not found when attempting to remove it

(nautilus:3479): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it

(nautilus:3479): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it
blue@blue-IC780M-A:~$ 


```
[ATTACH=CONFIG]255569[/ATTACH][ATTACH=CONFIG]255570[/ATTACH]  There are the nautilus screenshots.

Still bursting with gratitude,   Blue

---

### Post by nerdtron on 2014-08-17
Bashing-om is correct on setting the permissions to your user account.

Back to nautilus.
Actually, the gksu nautilus is still correct. Click on the computer icon and you'll be in the / folder. Now go to /media or /mnt where you should normally find the folder of mounted drives.

---

### Post by JKyleOKC on 2014-08-17
> **BlueAZ said:**
> OK, here's what happened:  In T gksu Nautilus brings up a Home folder that only contains Desktop.  My other folders not there.  Still in gksu Nt., if I click on Computer, it opens with the Root folder highlighted.  If I click on the Home folder in the Computer folder, my regular Home folder opens.  I'll try to attach a couple screen shots.I hope what I'm about to say is still correct, and doesn't introduce even more confusion.

A few versions back, there were four different ways to obtain super-user privileges, and no two gave exactly the same results although for many purposes they seemed to be interchangable. The four were "su," "sudo," "gksu," and "gksudo." Of these, the first two were intended only for use at the command line, and the latter two were only for use with the various GUIs. The difference between these two groups was that the first two failed to properly set up several conditions needed by the GUI. If either was used to launch a GUI application, it could result in the user being unable to log in later because those conditions were changed.

The difference between su and sudo was mostly in the password required to gain access; su required the root password, which doesn't exist in a standard Ubunutu installation, while sudo wants the user's password. Thus sudo is the only one applicable here in most cases -- but it's not good to use it to launch a GUI application.

This brings us to gksu and gksudo; they differ in the working directory and environment that they introduce, and that's why "gksu nautilus" shows you a home directory without your files. Using "gksu" switched you to root's own home directory, which is "/root." If you use "gksudo" instead, which does not change the directory, you should see your own home area as you expected.

Both of these want the user's password, so the differences are not as clearcut as one might hope. In fact, they are so subtle that many of the regular posters here aren't fully aware of what they do.

The reason I'm not certain that this still applies is that I've read in other messages that gksu and gksudo are no longer installed by default in all versions of the system any more. If that's true, I expect many old problems to emerge from their graves -- but I've not yet confirmed the report.

I hope this helps a bit; some of the issues around permissions are extremely confusing, even to those of us who have been working with them for years!

---

### Post by BlueAZ on 2014-08-17
Wow, that does explain a lot!  I do understand the subtle distinctions.  Whether I'll remember them is an open question!  I will try.

I'm still spooked by the text from the Terminal, a couple posts ago.  What does all that mean?  Sounds bad...

Thanks,   Blue

---

### Post by BlueAZ on 2014-08-17
I tried Bashing-Om's code to gain permission to use sda3.  Here is what I got in the Terminal:
```
blue@blue-IC780M-A:~$ sudo mount /dev/sda3 /mnt/work
mount: /dev/sda3 already mounted or /mnt/work busy
mount: according to mtab, /dev/sda3 is already mounted on /mnt/work
blue@blue-IC780M-A:~$ sudo chown -R blue:blue /mnt/work
blue@blue-IC780M-A:~$ sudo umount /mount/work
umount: /mount/work: not found


```

???  Did it work?

Thanks,   Blue

---

### Post by Bashing-om on 2014-08-17
BlueAZ;

As to the notifications from nautilus, what little I observed of them is that the mount point for a samba share does not exist.
How to 'fix' depends on what you are doing with 'samba' and why it was started. That is food for another thread.

@ JKyleOKC; Great explanation, I too garnered knowledge from that one !

[INDENT][INDENT]learning is the never ending process
[/INDENT][/INDENT]

---

### Post by BlueAZ on 2014-08-17
OK, that's all right.  I think I installed samba thinking it would help the Permissions issue, but it didn't.

Since I ran the Code per post before last, the 22 Gb partition no longer appears as a Volume on the left side of my Home folder.  How do I find it?

Thanks,   Blue

---

### Post by JKyleOKC on 2014-08-17
> **Bashing-om said:**
> BlueAZ;

As to the notifications from nautilus, what little I observed of them is that the mount point for a samba share does not exist.
How to 'fix' depends on what you are doing with 'samba' and why it was started. That is food for another thread.I'm not familiar enough with Nautilus to say whether it's serious or not, but if other things work then it's something for which diagnosis can be deferred.

The reason for the "no such file" error when unmounting /mount/work is because it should have been /mnt/work. I've made similar errors far too many times myself!

> @ JKyleOKC; Great explanation, I too garnered knowledge from that one !

[INDENT][INDENT]learning is the never ending process
[/INDENT][/INDENT]I learned most of it the hard way. In the words of the great Danish poet Piet Heim, imparting the Secret of Success, "Err and err and err again, but less and less and less."

And I agree wholeheartedly with your final line. I'm now partway into my ninth decade, and still eagerly learning new things each and every day. The more I learn, the more I discover I **don't** know.

---

### Post by BlueAZ on 2014-08-17
Good grief, you're right!  I typed in the last line and put 'mount' instead of 'mnt'.  My bad.  I ran the whole string of commands in the Terminal once again, and now the 22 Gb Volume shows up again.  Whew!  Something like that could have driven me crazy.  Thank you so much for picking that up, Jim!  And thank you for the quote about erring, but less.  Wonderful!

Thanks also to Bashing-Om for expert guidance!  I think I'll wait till tomorrow to see if I can now use the 22 Gb Volume.  Then, if all goes well, I'll mark this thread SOLVED!!

Loving Ubuntu,   Blue

---

