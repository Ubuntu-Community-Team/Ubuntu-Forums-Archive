---
title: "Very basic External Harddrive Help"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by michaelbogardus on 2008-10-21
I just bought a 750 gig Lacie external harddrive, and mainly want to use it to put my media files on (my main Harddrive is 200 gigs). 
I got a message, when I plugged it into my computer, saying:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdf1': Operation not supported Mount is denied because NTFS is marked to be in use.
I expected as much, seeing as it supports Windows and Mac off the bat, and I figured it would be formatted as such.
Basically, I want to format this drive, and use it as separate harddisc. I've never attempted to do such a thing in Ubuntu, and if someone could walk me through it, it would be much appreciated.

---

### Post by shifty_powers on 2008-10-21
bring up a terminal and use this command:

```
sudo mount -t ntfs-3g /dev/sdf1 /media/disk -o force
```

this should force your system to mount it properly.

sounds like it is already formatted as ntfs.

you could use gparted to reformat it to ext3 but i see no reason not to use it as is.

if you don't have gparted installed

```
sudo apt-get install gparted
```

---

### Post by michaelbogardus on 2008-10-21
Thanks for the help, but unfortunately I had a problem. It gave me this when I ran the sudo command:

$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory

---

### Post by dcstar on 2008-10-21
The drive has probably just been unplugged without a proper disconnect, you should install the **ntfsprogs** package, it contains **ntfsfix** which you should use to fix the drive:

```
sudo ntfsfix -y /dev/sdf1
```

---

### Post by michaelbogardus on 2008-10-21
Unfortunately, the terminal tells me that the command is not found.

I'm on Ubuntu 8.04.1 if that helps...

---

### Post by michaelbogardus on 2008-10-21
Now I have the HD at 698 gigs of unallocated space and 1 kilobyte call /dev/sdf.
Can I just format this somehow and make it all ext3?
If I do this, can I just move files from one harddrive to the other?

---

### Post by michaelbogardus on 2008-10-21
I managed to format the Exteral Harddrive into a 700gig ext3 filesystem, but I can't copy things from say, the Music folder on my internal drive to the new drive. I'm creating a linux-swap partition on the Lacie drive, but I don't think that is the case.

Basically, I'm trying to make a 750 gig USB stick. Am I going about it the wrong way?

---

### Post by michaelbogardus on 2008-10-22
Bump... just a giant USB stick, in theory. Should I go Fat32 so I can save and access from both Windows or Ubuntu?

---

### Post by AFarris01 on 2008-10-22
you could re-format it again as NTFS, or FAT32 if you intended to use it under windows, but if you are only going to be using it with linux, and have already formatted it as an ext3 filesystem, then there wouldn't really be a point.  

But, you say you can't copy files from your HDD to the external drive... odd indeed.

Is it giving you any kind of pop-up error message?  please post that message if so.

if you're not getting any kind of error pop-ups, then create an empty file, or pick an arbitrary file on your harddrive, and copy it via the terminal to see if any errors pop up.  for example, to copy a file from the desktop to my flash drive, I would do this:

cp ~/Desktop/arbitrary_filename.txt /media/sdg1

try this and post back what happens!

Hope this is helpful!

Andrew

---

### Post by michaelbogardus on 2008-10-22
I can't create or transfer any files on the Hard Drive. Tried it via terminal, and via the UI.

It says I don't have permission. Should I change something?

---

### Post by AFarris01 on 2008-10-22
Ah, theres something then!

its telling you that you don't have permission because the filesystem is mounted with root permissions, or so it would seem.  to see if thats true, repeat the copy experiment i mentioned above, but with the "sudo" prefix, like this:

sudo cp ~/Desktop/arbitrary-filename.txt /media/sdg1

inserting your paths where appropriate of course.  if this works, then you have to change the mount permissions for the drive.  if not, then the write permission needs to be changed, then the experiment repeated.  either way, to facilitate doing so, open a terminal and type in:

sudo apt-get install pysdm ntfs-config

this will install the Storage Device Manager, found via: "System>Administration>Storage Device Manager"
and the NTFS configuration tool, found via "Applications>System Tools>NTFS Configuration Tool"

The former is the more useful tool here, and the latter is really just to easily enable/disable write support for NTFS filesystems easily.  id recommend having both, just in case.

now, go launch the Storage Device Manager, "System>Administration>Storage Device Manager," and you will see a window with a list of partitions listed there in a bar on the left.  Pick your partition (i believe it was sdf# ?) and it will as if you want to configure it.  say yes, and then you will be presented with a bit of info on the right side of the screen in 2 tabs.  most of this can be ignored for right now.  There should be a button there that says "Assistant"... click that, and you get another new window.  this one lets you select your mounting options.  select whichever ones you deem appropriate, then hit 'Apply' and you're all set!  As for which options to have checked, i'd suggest the following:

[v] Allow a user to mount/unmount the file system
[v] The owner of the device can mount it
[v] Owner of the filesystem:  uid= <your username here>
[v] Owner group of the filesystem  uid=<your group here(usually also your username)>

lemme know if that doesnt work, and we'll figure it out!

Hope this helps!

Andrew

---

### Post by michaelbogardus on 2008-10-22
I am getting ready to flip out. I've tried everything under the sun and still no results.

Can someone walk me through from the beginning? I want a backup drive for Ubuntu, so I can transfer all my files before updating from 8.04.1 to 8.10.
It is a 750 gig Lacie External Harddrive. Ext 3 is fine. I have Gpart and Storage Device Manager.

I need a step by step guide, right from the beginning, because I have tried absolutely everything in this thread, and am starting to pull my hair out.

---

### Post by earthpigg on 2008-10-22
> **michaelbogardus said:**
> I am getting ready to flip out. I've tried everything under the sun and still no results.

Can someone walk me through from the beginning? I want a backup drive for Ubuntu, so I can transfer all my files before updating from 8.04.1 to 8.10.
It is a 750 gig Lacie External Harddrive. Ext 3 is fine. I have Gpart and Storage Device Manager.

I need a step by step guide, right from the beginning, because I have tried absolutely everything in this thread, and am starting to pull my hair out.

it sounds like the hard drive is just fine (now), but you have it mounted as root.

simplest way to solve that, i think, would be to unplug it and plug it back in.

if it doesn't automount then go to places -> computer and double click on it.

---

### Post by michaelbogardus on 2008-10-22
Invalid mount option.

---

### Post by earthpigg on 2008-10-22
wait... 

>  I'm creating a linux-swap partition on the Lacie drive, but I don't think that is the case.


you didn't format that as a 700 gig *linux-swap *partition did you?

---

### Post by michaelbogardus on 2008-10-22
Right now, it is a 750 gig ext 3 filesystem. Whenever I try to open it, or move something to it, I get the invalid mount option.

---

### Post by earthpigg on 2008-10-22
probably beyond my capabilities to help :\

that doesn't mean much tho, see my sig.

last thing i'd try is using gparted to see if it has any crazy flags  ('sudo apt-get install gparted' if you dont have it, 'sudo gparted' to start it... pure GUI) and so on... basically, i'd find a thumb drive and seeing if anything on the external HD was different than on my thumb drive (aside from ext3 and FAT32 and size, obviously) - asking myself 'why?'.

if that didn't yield any answers, id post a thread on the forums...

---

### Post by michaelbogardus on 2008-10-22
I do appreciate the help earthpigg.
I just hope to have this all sorted out within 8 days...

---

### Post by m_duck on 2008-10-22
Is this disk going to be connected all/most of the time, or just occasionally for when you want to perform the backups?

---

### Post by michaelbogardus on 2008-10-22
All the time. Basically, whenever I download a large multimedia file, I will move it there. I want to be able to access it there though, as I would my normal hard drive or a thumbdrive.

---

### Post by prematurebaby on 2008-10-22
Have you ever been able to use the USB ports without problems.

---

### Post by m_duck on 2008-10-22
OK then, from a terminal type:
```
sudo mkdir /media/Lacie
```To create a mount point for the disk, substituting Lacie for whatever you want the mount folder to be called.

Then backup your current fstab file (where filesystem mount points are stored) by doing:
```
sudo cp /etc/fstab /etc/fstab.BAK
```Now open fstab for editing,
```
gksu gedit /etc/fstab
```At the bottom of this file, add a line like the following (assuming your disk is still at /dev/sdf1):
```
/dev/sdf1 /media/Lacie ext3 defaults 0 0
```Then save and exit the editor. Now go back to terminal and type:
```
sudo mount -a
```And *hopefully* it will mount and give no errors! If not post the errors here and someone will help if I can't.

---

### Post by earthpigg on 2008-10-22
> **prematurebaby said:**
> Have you ever been able to use the USB ports without problems.

it started because it was origionally partitioned NTFS and whoever had it before him (OEM?) didn't do the little 'properly remove drive' thing in xp/vista... then he formatted it ext3... some part of that partitioning process went awry, i suspect.

assuming he doesn't still have it mounted as root - is there some weird fstab thing that can alter how a drive is automatically mounted or anything crazy like that?

he physically unplugged it earlier and plugged it back in, so i would **think **it would automount **not **as root.

edit: i **knew **it was an fstab thingie!

---

### Post by AFarris01 on 2008-10-22
I understand you're frustration, and sympathize deeply...ive gone through similar things many times.  Lets take this from the top then, just to be sure everything is set up right (I'm actually going to reformat my external drive at the same time, to be sure that I give you the right instructions):

since you haven't created any files, or copied anything then it should be safe to try recreating the partition, if it didnt work right the first time for some reason.

Here we go-------------------

1) First, make sure that the drive is plugged in tightly, and has its appropriate power cord plugged in, and the drive is turned on.

     If the drive fails to mount, or you get an error as it tries to mount, thats ok, dont worry.  We're repartitioning it anyway, and it only has to be present for the tools to detect it.

2) Next, we have to remove the old partition, and create a new one.  to do this, we will need the tool called GParted, and can be accessed by going to "System > Administration" and clicking on the "Partition editor" link.

3) After clicking on "Partition Editor," a window will pop up with a bouncing progress bar at the bottom, indicating that the program is detecting your partitions.  This may take a moment.

4) After the progress bar completes, the main window will fill with some information about the drives and partitions on your computer.  The default thing to be displayed is your primary hard disk.  Ignore this readout, because it's not the one you need right now.

5) Next, if you look in the top right-hand side of the screen, you will see a drop-down menu with a path and disk size displayed on it (for me it looks like this:
"[icon]/dev/sda  (232.88GiB)")
Click this menu, and a drop-down list will appear of drives detected on your computer.  Select the appropriate drive from the menu, and click to select it. (in you're case, it will be the drive with a size somewhere in the range of 750GiB.  for my external 500GiB drive, the label says: "[icon]/dev/sdg  (465.76GiB)")

6) Now, in the main window you should see a colored graph, and a list of partitions below it, most likely something like this:

Partition                 Filesystem             Size
unallocated    [colored square] unallocated    ##.## MiB
/dev/sdg1      [colored square] ext3           ##.## GiB  

if it's different, dont worry, because again...we are reformatting after all


7) Now, Right-click on any partitions that you see there, and select 'Delete' from the menu.  in the end, the only thing that should be displayed in the list is this:

Partition                 Filesystem             Size
unallocated    [colored square] unallocated    ##.## GiB

8) Once the partition-deleting is done, right click on the 'unallocated space' entry, and select 'New,' and a dialog box should pop up, prompting you for some information on the new partition you are trying to create. my recommendation would be to set it up as follows:

   Free Space Preceding(MiB): "16"
   New Size (MiB): "<leave whatever number is here alone>"
   Free Space Following (MiB): "8" **this will take 8MB off the 'preceeding' leaving you an 8MB buffer on either side of the partition**
   Create As: "Primary Partition"
   Filesystem: "ext3" ***You can also select NTFS or FAT32 here***

After you've entered the information above in, click the "Add +" button, and you should see the partition you want to create appear in the partitions list, and a small popup at the bottom of the window will inform you of the new partition as a 'Pending Operation'

9) Now go to the toolbar at the top of the window and click "Apply".  This next bit will take a little while as you already know.  Once it completes, you can exit out of GParted.    

10) Now, go to "Places > Computer" and see if you're drive is listed there.  If it is, click it and it should open up in a new window. If it does, then go on to the next step.  if you get some sort of error, proceed to step 12.

11) Right in the empty space in the drive, select 'Create Folder'.  Name the folder any arbitrary thing you want, it doesn't matter.  Now, you should have a folder of your chosen name sitting in the empty space, and you should be done.  To set up for mounting at boot time, follow the steps in my previous post, with the addition of checking the box in front of 'Filesystem Mounted at Boot Time".  this will save any extraneous mucking about with the command line.  If you get an error, go to step 13.

12) If you got an error when trying to mount the partition that says something like 'invalid permissions' or something, then open up the Storage Device Manager "System > Administration > Storage Device Manager" and follow the instructions as listed in my previous post, then try to mount the partition again.  If it does not work, then please post back with the specific error message you are getting, and any other relevent information.  If this works, then you're all set.

13) For an error with creating the 'test' folder, re-try the instructions in my previous post.  if this does not work, post back and i can walk you through adding special permissions to your user, so you don't have write-protect issues.  If you formatted as an NTFS filesystem, then launch the ntfs-config tool via "Applications > System Tools > NTFS Configuration Tool" and check the boxes to enable write support.  if they're already checked, uncheck them, apply, then relaunch and re-check them.


Hopefully this set of instructions is useful, and not a complete waste of time...but above all, i hope this helps you get your drive working!

Andrew

---

### Post by michaelbogardus on 2008-10-22
Alright, now we are cooking with fire, however, I still **can't** add files. It says I have to be logged in as root. Now my limited knowledge of the terminal tells me that when I am using a sudo command, it is a root command, so do I need to use a sudo command to enable any user permissions, or do I go back to the removable storage drives?


EDIT: Can't bolded because it sounds like everything is hunky dorry.

---

### Post by m_duck on 2008-10-22
What happens if you edit the line you just added to fstab, and change it to look like:
```
/dev/sdf1 /media/Lacie ext3 users,rw,auto 0 0
```Then I think it is necessary unmount the disk, then mount it again by:
```
sudo umount /media/Lacie
```Though I'm not certain the "umount" command works with fstab'd partitions, but failing that a restart will work. Then
```
sudo mount -a
```Which should mount the partition with the correct permissions.

Note: if you have restarted then the partition should mount automatically on boot.

---

### Post by michaelbogardus on 2008-10-22
I still can not create a file inside of it. It says permission is given to the root.

---

### Post by AFarris01 on 2008-10-22
ok... i had some similar problems a long time ago with my flash drive, and if it's still saying that, and if you tried the Storage Device Manager fix i listed, then its time to edit some permissions...


go to System > Administration > Authorizations.
   you will have to enter your password for this one...
you will see one of 2 things, either a single entry called 'org' or an expanded tree of entries.  either way, the navigation is pretty much the same:
go through the tree in the following order:
org > freedesktop > hal > storage

under the storage entry there should be several storage-related events, such as mount/unmount media, etc... go to each of the first 4 (the ones that refer to mount, unmount, and eject), and click "+Grant" with the following options:

pick your user from the dropdown menu under beneficiary
under constrains, select "Must be in active session"

do that same thing for those first four entries, close it and reboot with the disk connected/powered on.  hopefully that will do it... if not, then i'll get back to you tomorrow, because it's late and im in need of sleep  (been reading for about 8 hrs now)

good luck, and I Hope this works for you!

Andrew

---

### Post by michaelbogardus on 2008-10-23
Once again, it says my permissions aren't available. 
Would it be the filesystem? Or the company, Lacie?

---

### Post by earthpigg on 2008-10-23
what if he tried running gparted off a live CD? live cd's are less likely to give crap about permissions and root and all that...

---

### Post by marco123 on 2008-10-23
This has happened to me a few times.

I always use the command: > sudo chown name /path/to/device

e.g. > sudo chown mark /media/disk

name is your username.

---

### Post by michaelbogardus on 2008-10-24
The problem has been solved. Thank you to everyone for your help!

---

### Post by Tiganu on 2008-11-05
> **AFarris01 said:**
> Ah, theres something then!

its telling you that you don't have permission because the filesystem is mounted with root permissions, or so it would seem.  to see if thats true, repeat the copy experiment i mentioned above, but with the "sudo" prefix, like this:

sudo cp ~/Desktop/arbitrary-filename.txt /media/sdg1

inserting your paths where appropriate of course.  if this works, then you have to change the mount permissions for the drive.  if not, then the write permission needs to be changed, then the experiment repeated.  either way, to facilitate doing so, open a terminal and type in:

sudo apt-get install pysdm ntfs-config

this will install the Storage Device Manager, found via: "System>Administration>Storage Device Manager"
and the NTFS configuration tool, found via "Applications>System Tools>NTFS Configuration Tool"

The former is the more useful tool here, and the latter is really just to easily enable/disable write support for NTFS filesystems easily.  id recommend having both, just in case.

now, go launch the Storage Device Manager, "System>Administration>Storage Device Manager," and you will see a window with a list of partitions listed there in a bar on the left.  Pick your partition (i believe it was sdf# ?) and it will as if you want to configure it.  say yes, and then you will be presented with a bit of info on the right side of the screen in 2 tabs.  most of this can be ignored for right now.  There should be a button there that says "Assistant"... click that, and you get another new window.  this one lets you select your mounting options.  select whichever ones you deem appropriate, then hit 'Apply' and you're all set!  As for which options to have checked, i'd suggest the following:

[v] Allow a user to mount/unmount the file system
[v] The owner of the device can mount it
[v] Owner of the filesystem:  uid= <your username here>
[v] Owner group of the filesystem  uid=<your group here(usually also your username)>

lemme know if that doesnt work, and we'll figure it out!

Hope this helps!

Andrew

This worked very well for me using an USB enclosure with and ext3 partition. 
I used pydsm as above, but set the username & group in the section specific to the hdd I have, so that it does not change the mounting of other disks I might connect.

One observation is that after configuration it did not change the permissions right-away, so I did
```
sudo chown userX.userX /media/disk
```
to get the result I wanted immediately.

On a subsequent reboot, new kernel image, it mounted with all the right permissions. I think doing ```
kill -HUP hald
``` and logging out will give the same result for those who don't want to go through a reboot.

---

