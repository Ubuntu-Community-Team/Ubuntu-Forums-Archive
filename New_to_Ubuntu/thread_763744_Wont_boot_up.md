---
title: "Wont boot up"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by has3o on 2008-04-23
In  the boot menu if i select running ubuntu 8.04 it just goes to a black screen and does nothing.
I run the restore thing in the boot menu and it loads a bunch of things cheacking stuff i guess and this comes up

An automatic file system cheak(fsck) of the root filesystem failed.A manual fsck should be preformed, then the system restarted.
The root filesystem is currently mounted in read-only mode.A maintenance shell will now be started.
After preforming system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
Bash:nojob control in this shell
bash:groups: command not found 
bash:lesspipe: command not found
bash:Command: command not found
bash:The:command not found
bash: dircolors:command not found
bash:Command: command not found
bash: The: command not found
then it gives my the root@mycomputer:`# shell thing
What does this mean and what do i do to fix it?Sorry for my newbyness i know very little to nothing about ubuntu.

---

### Post by smartboyathome on 2008-04-23
You have to type restart at that prompt. Unfortunately, your fix cannot fix itself, and will always do that at bootup (with my experience).

---

### Post by hermes0710 on 2008-04-23
You should try checking your root file system as suggested...

```
fsck /dev/rootdevice
```

where "rootdevice" should be replaced with the disc hosting your os.

---

### Post by has3o on 2008-04-23
What do you mean by that i have to have the ubuntu cd in or something im a complete newb.

if i try to start it normaly it says
starting up...
loading please wait...
kinut:trying to resume from /dev/disk/by-uuid/dcc06d4f-bla bbla bla
kinit:No resume image, doing normal boot..
{ 27.680377} intel_rng: FWH not detected

Is there any posible way to flash my whole hard drive aka restoring to factory defaults(id have to get the cd)but is it posible to even do that in the bios?

---

### Post by has3o on 2008-04-23
I put in that code 
fsck /dev/rootdevice
it says 
fsck 1.40.8 (13l-mar-2008)
e2fsck 1.40.8 (13-mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/roodevice

The superblock could not be read or does not escribe a correct ext2 filesystem. If the device is valid and i really contains an ext2 filesystem(and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

if that makes any sence help plox

---

### Post by has3o on 2008-04-23
Could i restore to factory defaults somehow start over fresh?

---

### Post by hermes0710 on 2008-04-23
Hi... Let me understand:

    Does your system start (even in text mode so that you are able to execute commands)? If yes, then type ```
cat /etc/fstab
```
and post here the output. In the command fsck /dev/rootdevice you are supposed to replace the word "rootdevice" with the correct name of the device on which ubuntu was installed. Give me the results of the command i wrote you above and i will help you more

---

### Post by has3o on 2008-04-23
it wont let me go on it normaly i can only go on the  recovery mode

I put that thing in  after the recovery mode thing finished loading stuff it says
#/etc/fstab: static file system information
#
# <file system> <mount point>  <type>  <options>  <dump> <pass>
    proc             /proc      proc     defaults   0      0
# /dev/sda4
UUID=b82ebc70-1519-4648-b90d-9793076c17db/         ext3    defaults,error
s=remount-ro 0         1
# /dev/sda7
UUID=dcc06d4f-21be-4edd-81ba-da2c5ee06291 none      swap     sw
  0     0
/dev/scd0      /media/cdrom0      udf,iso966 user,noauto,exec 0    0

---

### Post by hermes0710 on 2008-04-23
Ok, select recovery mode and run the command ```
cat /etc/fstab
``` and post the output.

("cat" is a command that prints the content of a file. "fstab" is the configuration file where linux keeps info about which devices will mount and where)

---

### Post by hermes0710 on 2008-04-23
OK. Now execute this command ```
sudo fsck /dev/sda4
```

and post the output

---

### Post by has3o on 2008-04-23
after i put in sudo fsck /dev/sda4
it says
Command'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH enviroment variable.
bash: sudo: command not found

---

### Post by has3o on 2008-04-23
> **hermes0710 said:**
> Hi... Let me understand:

    Does your system start (even in text mode so that you are able to execute commands)? If yes, then type ```
cat /etc/fstab
```
and post here the output. In the command fsck /dev/rootdevice you are supposed to replace the word "rootdevice" with the correct name of the device on which ubuntu was installed. Give me the results of the command i wrote you above and i will help you moreI put that thing in after the recovery mode thing finished loading stuff it says
#/etc/fstab: static file system information
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=b82ebc70-1519-4648-b90d-9793076c17db/ ext3 defaults,error
s=remount-ro 0 1
# /dev/sda7
UUID=dcc06d4f-21be-4edd-81ba-da2c5ee06291 none swap sw
0 0
/dev/scd0 /media/cdrom0 udf,iso966 user,noauto,exec 0 0

---

### Post by hermes0710 on 2008-04-23
ok, try it without sudo. just ```
fsck /dev/sda4
```

---

### Post by has3o on 2008-04-23
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda4 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found. Fix<y>?

---

### Post by hermes0710 on 2008-04-23
As you can understand, there are errors on the drive where ubuntu is installed. Press y to let fsck fix the error. (Any chance your harddrive needs replacement??? I recommend backup...). It might show "Fix<y>?" again if it finds more errors. Let me know what happened.

---

### Post by has3o on 2008-04-23
My laptop has already died in the past lol im suprized its still kicking but yeh i press y and it says
Inode 590159 was part of th orphaned inode list. FIXED.
Deleted inode 1081373 has zero dtime. fix<y>?

---

### Post by hermes0710 on 2008-04-23
Ok then. Let fsck try fixing all errors and see what's going on next. I wouldn't be that optimistic though :P. The root filesystem has errors... Anyway, good luck with that. Bye

---

### Post by twin_57103 on 2008-04-23
This all sounds eerily similar to when I had a hard drive fail...I'd highly suggest backing up anything you were working on (if necessary, boot from your Ubuntu CD).  

Most newer hard drives have SMART self-monitoring built in.  You can check the manufacturer's web site to see if they have any tools that can help, and I know that there's a package called smartmontools that's available in the Ubuntu repositories (sorry, I haven't used it enough to be able to offer any help with it).  If you dual-boot, you can use a Windows tool called Speed Fan (search for it on the internet).  You can install it on a live session (booted from the CD) if necessary in order to use it for diagnostics.

[Here is a link]("http://ubuntuforums.org/showthread.php?t=711697") to my thread when my drive failed.

Good luck - I can't help much with the hardware end; I just wanted to offer a warning since it sounds so much like my own hard drive failure.

---

### Post by has3o on 2008-04-23
Lawl sorry to take up ur time so much but thankts for the help its greatly apreciated.
Onto the next person who wants to help xd i think its dead but this is what iget^^
Could not start the x serve(your graphical enviroment) due to some internal error.Please contact your system administrator or cheak your syslog to diagnose.Inthe meantime this dispay will be disabled.Please restart GDM when the problem is corrected.

---

### Post by has3o on 2008-04-23
> **twin_57103 said:**
> This all sounds eerily similar to when I had a hard drive fail...I'd highly suggest backing up anything you were working on (if necessary, boot from your Ubuntu CD).  

Most newer hard drives have SMART self-monitoring built in.  You can check the manufacturer's web site to see if they have any tools that can help, and I know that there's a package called smartmontools that's available in the Ubuntu repositories (sorry, I haven't used it enough to be able to offer any help with it).  If you dual-boot, you can use a Windows tool called Speed Fan (search for it on the internet).  You can install it on a live session (booted from the CD) if necessary in order to use it for diagnostics.

[Here is a link]("http://ubuntuforums.org/showthread.php?t=711697") to my thread when my drive failed.

Good luck - I can't help much with the hardware end; I just wanted to offer a warning since it sounds so much like my own hard drive failure.
Acutalythats exaclty what i got lol

---

### Post by twin_57103 on 2008-04-23
> **hermes0710 said:**
> I wouldn't be that optimistic though :P. The root filesystem has errors... 

Agreed...by the time I got to that point on my own failing hard drive, the entire operating system was toast.

---

### Post by has3o on 2008-04-23
After doing all that stuff i restarted and  it let me log back in regular sesion......how do i repair this i got back on lol

---

### Post by twin_57103 on 2008-04-23
Again, I'll suggest that the first thing you do is backup anything important.  Is the computer doing anything strange?  When mine died, the performance got very poor (like a Windows 98 box that's been on web sites of ill repute).

Are there any files in the lost & found folder?  If so, would you post the contents of that directory?  I never got to trying to recover these because my drive was so quickly dying, but you can find a link to help with this by following the link I posted - someone had suggested that to me.

I hope I'm just being paranoid and that it isn't the drive.  Maybe there are other causes to the trouble you're having (a hard shutdown or a bad hard drive cable could also cause similar behavior).  Good luck!

---

### Post by has3o on 2008-04-23
it says the content of the files cant be displayed.you do not have permissions nessisary to view the contents of "lost+found".
on the top right of the folder there is a orance circle with a box and an x going threw it.

---

### Post by twin_57103 on 2008-04-23
Are you sufficiently comfortable with the command line to navigate to the directory from the terminal (under the accessories menu)?  If so, I'd try that.  use "cd .." to move up a directory, "ls" to display the contents of the current directory, and "cd [directory name]" to change into another directory.

If not, go to a terminal and type "gksudo nautilus" - that will get you a nautilus (file navigation) window with sudo access (be careful not to change or delete any files as that could cause further damage to the system).

Sorry, I'm in the middle of a huge download in Windows...I'd reboot and try to walk through it with you, but I don't want to lose the download :(  It's only got 15 minutes left.

---

### Post by has3o on 2008-04-23
> **twin_57103 said:**
> Are you sufficiently comfortable with the command line to navigate to the directory from the terminal (under the accessories menu)?  If so, I'd try that.  use "cd .." to move up a directory, "ls" to display the contents of the current directory, and "cd [directory name]" to change into another directory.

If not, go to a terminal and type "gksudo nautilus" - that will get you a nautilus (file navigation) window with sudo access (be careful not to change or delete any files as that could cause further damage to the system).

Sorry, I'm in the middle of a huge download in Windows...I'd reboot and try to walk through it with you, but I don't want to lose the download :(  It's only got 15 minutes left.well i used that gksudo nautilus and i could open the folder and inside was a #590317 couldnt open it thou lol

---

### Post by twin_57103 on 2008-04-23
Well, that's nowhere near as bad as mine was.  Here is a link that I got about recovering these files:
[]("http://users.bigpond.net.au/hermanzone/p10.htm#Recovering_files_from_lostfound")

I'd still try some hard drive diagnostics when you get a chance (mine was Western Digital, and they had a Windows utility and a bootable CD that could be used for diagnostics, both downloadable).

Good luck!

---

### Post by has3o on 2008-04-23
yeh those do seem to take a while so whats the lost n found thing for is it fixable or what not lol

---

### Post by twin_57103 on 2008-04-23
Sorry - it looks like something funny happened with the link!

Here it is: [http://users.bigpond.net.au/hermanzone/p10.htm#Recovering_files_from_lostfound](http://users.bigpond.net.au/hermanzone/p10.htm#Recovering_files_from_lostfound)

I didn't get that far, so I won't be able to offer any advice beyond providing the link.  At that point, I decided it was time to replace the entire computer! It was a lemon from day 1 and I didn't want to see what would go wrong next :)

---

### Post by has3o on 2008-04-23
haha thanks so much for our help and everyone elses xd ill probly start another thread right after Xd my ac adapter for my laptop when its turned off wont charge the battery anymore but it will use the ac adapter for power its odd aswell as adding more desktops for the cube ^^:P:lolflag:

---

