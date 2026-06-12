---
title: "Gutsy freezing on login screen--caused by printer?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by madmogs on 2008-06-26
This isn't a new installation for me, but I know so little about Linux in general that it might as well be, and I have no idea at all how to solve it.

I have a dual-boot XP/Gutsy box, with the two operating systems on two physically seperate hard disks (XP on primary HD, Ubuntu on slave HD, installed after XP), and I've been using it fine for about four months until things went spectacularly pear-shaped.

About six weeks ago I installed a new printer (HP Laserjet 1100) on Ubuntu, and it appeared to go on without a hitch.  However, last week I had to print out pages from a number of web sites (using a reasonably up-to-date Firefox) and a couple of emails on Evolution (no idea what version), and the computer froze midway through.  Mouse wouldn't respond, keyboard wouldn't respond, nothing, so in the end I was forced to press the reset button. 

When the computer restarted, I logged in to my account again and the computer immediately froze in exactly the same way as before.

After restarting a second time, on logging in I got a brief glimpse of some very worrying-looking error messages (something about the kernel being corrupted?) in the top left-hand corner of the screen, which promptly whited out when I clicked for more details, and froze again.

Subsequently, the computer has frozen shortly after I've reached the Ubuntu login screen every time, before I can log in.  The odd thing is, every time I reach the login screen, the printer starts to churn out all the documents I was trying to print when the problem began.

I have no idea what this is or how to solve it, and am reluctant to fiddle for fear of making things worse.  Can it be fixed? And if not, how do I retrieve my data without making matters worse?

---

### Post by unutbu on 2008-06-27
I don't know how to fix your freezing problem, but perhaps I can help you save your data on another disk.

Boot into Gutsy Recovery mode. Hopefully the machine does not freeze here. Log in at the console.

```
cd /home/madmogs  # change madmogs to whatever your username is.
ls -lRa | less   # This is to see if your data is still there.

```

Post the output of
```

sudo fdisk -l
cd /home/madmogs
du -sh .
```

Also post how much space you have available on the XP drive.

If you haven't encountered the freeze while in recovery mode, then I think we can help you save your data onto another medium. Please tell us how you want to save your data. Here are a few options:

1) save your files to your other (XP) hard drive (assuming you have enough space), 
2) save your stuff onto CD or DVD
3) save your stuff onto a USB jump drive
4) hook up a second linux box to this machine and transfer the data over an ethernet crossover cable.

---

### Post by madmogs on 2008-06-27
Thanks for the advice, Unutbu.

Okay, my data is definitely all still there, which is good.

The du command came up with '18G' as the response.  The Fdisk command has a rather copious response as I'm afraid I partition like mad. I don't know how much of it you need (I didn't write down the blocks) but here goes:

```
DEVICE    BOOT  START  END  BLOCKS ID SYSTEM
/dev/hda1  *        1  2549        7  HPFS/NTFS   
/dev/hda2        2550 14946        f  W95 Ex'd (LBA)  
/dev/hda5        2550  3824        7  HPFS/NTFS  
/dev/hda6        3825  5099        7  HPFS/NTFS  
/dev/hda7        5100 12430        7  HPFS/NTFS  
/dev/hda8       12431 14946        7  HPFS/NTFS  

DEVICE    BOOT  START  END  BLOCKS ID SYSTEM
/dev/hdb1        6110 60801        f  W95 Ex'd (LBA)  
/dev/hdb2  *        1  6109        83 Linux 
/dev/hdb5        6376 12750        7  HPFS/NTFS  
/dev/hdb6        6110  6375        82 Linux swap / Solaris  
/dev/hdb7       12751 22439        7  HPFS/NTFS  
/dev/hdb8       22440 47936        7  HPFS/NTFS  
/dev/hdb9       47937 60801        7  HPFS/NTFS  
```

Space on any of my Windows drives isn't a problem.  The biggest piece of empty space I've got is 139 GB.

As for what to do with the data, XP, the CD/DVD-ROM and the USB drive are all viable options, though I'm leaning slightly towards the USB drive.  Unfortunately, I don't have another Linux machine to play with, though, but everything else should be a go.

Thanks for taking the time to help!

---

### Post by unutbu on 2008-06-27
Below I chose hdb8 as the partition in which to save your data. If you'd prefer a different partition, just change the one spot where you see hdb8 (below) to whatever partition you want.

I also assumed your username is madmogs on the machine. If that is wrong, change the "export user=madmogs" line as well.

Now then, here are the instructions:

Boot once again into recovery mode. 

```
export device=/dev/**hdb8**
export user=**madmogs**

mkdir /Win
mount $device /Win
mkdir /Win/$user

cd /home/$user
find . -print0 | cpio --null --sparse -pvd /Win/$user
```

This should copy everything in /home/madmogs into a directory called madmogs in /dev/hdb8.

If nobody can come up with a way to fix the freezing problem, you 
could then reinstall Ubuntu and then port your data back with these commands:

Boot into Ubuntu (regular, not recovery mode).
Log in as madmogs
Open a terminal.
```

export device=/dev/hdb8
export user=madmogs

sudo mkdir /Win
sudo mount $device /Win

cd /Win/$user
find . -print0 | cpio --null --sparse -pvd /home/$user

sudo chown -R $user:$user /home/$user
sudo chmod -R 755 /home/$user
```

Note: NTFS does not record ownership and file permissions the same way ext3 (Ubuntu's) filesystem does. Therefore, when you save all your home data to /dev/hdb8, you will lose any special ownership or file permission settings you might have had. I'm hoping this is not important to you. If it is, I can give you slightly different instructions that will save your /home/madmogs as a whopping huge 18GB archive file which you can save over on /dev/hdb8, and which will preserve ownership/permissions. The only problem is you wouldn't be able to read/access/modify those files while in Windows. You would be able to extract it after you reinstall Ubuntu, and all your onership/permission settings would be preserved, however. If you want instructions for this, just post.

---

### Post by madmogs on 2008-06-30
Cool! Thank you! I have retrieved all my data now.

In terms of fixing versus reinstalling, googling the problem has come up with a huge blank.  Is there anywhere particular I should be making enquiries about the freezing problem before I just bite the bullet and wipe and reinstall?

Thanks again!

---

### Post by unutbu on 2008-06-30
Madmogs, I have one idea which *might* stop your freezing problem. It's easy to do and easy to undo (if it doesn't work). 
```

Boot into recovery mode.
cd /etc/rc2.d
mv S19cupsys K19cupsys
exit

```
Reboot into regular mode. See if the freezing has stopped. If the freezing stops, then next we'll have to work on removing and then reinstalling cupsys. That should be pretty simple as long as your internet connection is working.

Explanation: The files in rc2.d are scripts that are run at boot time. The ones that begin with an S are started at boot time. The ones that begin with a K are stopped at boot time. The above change stops cupsys from running.

Of all the services in rc2.d, cupsys is the only one that deals with printing (that I am aware of).

If that doesn't work, then I'm back to square one without a good idea how to stop the freezes.

How to undo the above change:

```
Boot into recovery mode.
cd /etc/rc2.d
mv K19cupsys S19cupsys
shutdown -h now            # To turn off the machine
exit                       # To reboot the machine

```

PS: Good news: If you can boot into recovery mode without freezing, then there is probably nothing wrong with your kernel, since it is the same kernel that runs in recovery mode that runs in regular mode.

Given that you can run in recovery mode with no problem, I'm pretty confident that there should be a way to fix your machine without reinstalling, the only question is how long it would take for me, you or someone else to find the solution. If the above attempt does not work, you'll have to weigh how long you are willing to wait against how long it takes to reinstall Gutsy + reinstall extra packages.

---

### Post by madmogs on 2008-07-11
Sorry about the delay in replying -- I've been away, but I've now managed to have a go at this.

It didn't solve the problem, but it has given me a clear sight of a number of error messages which should possibly be helpful.  That or I could always wipe it and start again--I'm getting tired of XP.

Okay, I deleted that file without any problem -- thanks for that.  However, when it then went and started Ubuntu I got a string of error messages: 
```
An error occurred while loading or saving configuration info for X_session_manager. 
Some of your configuration settings may not work properly.
```

The same appeared for gnome_panel and nautilus.  In all cases, clicking the Details button produced the following, usually repeated several times:

```
Adding client to server's list failed: CORBA error 
IDL:omg.org/CORBA/COMM_FAILURE:1.0
```

After these three errors, I got a further box saying
```
GConf Error: Adding client to server's list failed: CORBA error
```

Once I got past that I got the same set of errors for nm_applet, vino_session, evolution_alarm_notify and update_notifier.   I also, briefly, got an error message like so, but it vanished of its own accord. 

```
Install problem
The configuration defaults for Gnome power manager have not been installed correctly. 
Please contact your computer adminstrator
```

After that I was kind of in Ubuntu, but with a blank black background and no bars at the top and bottom of the screen, so couldn't really do an awful lot.

It sounds to me like there's a single problem behind it all that ought to be fixable.  Is it something that can be repaired?

---

### Post by unutbu on 2008-07-11
This is just a hunch. It may work, but then again, it may not.

Try the instructions here:

[http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)

Explanation: It sounds like the problem now begins only after you log in. (Is this true?) If that's the case, then it is probably a GNOME configuration file in your /home/USERNAME directory which is causing the problem. All GNOME configuration files (at least the ones I know about) live in 1 of 4 directories:
.config, .gconf, .gnome, and .gnome2. 

The instructions above moves these directories to new locations. Then when you try to next login, GNOME will detect that these directories are missing and it will create new versions -- the default versions! -- for you. It should be like when you started Gutsy the first time. You'll have to re-do all your GNOME configurations of course, but that is hopefully a minor task compared to the current problem.

If it doesn't work, there are instructions on the same page for how to undo the changes.

---

