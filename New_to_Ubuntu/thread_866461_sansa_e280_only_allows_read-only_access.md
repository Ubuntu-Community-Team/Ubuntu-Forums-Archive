---
title: "sansa e280 only allows read-only access"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by limberlegs on 2008-07-21
Hi, all.

After hours of searching and getting nowhere, I'm hoping a post of my own can help me with my dilemma.  

When I connect my Sansa e280 mp3 player, Ubuntu will not allow me to add files to the drive. It tells me that the filesystem is "read-only."  

Under MSC mode I have tried numerous things:

- mount and unmount, reset the computer, reconnect
- put the Sansa into recovery mode, mount/unmount, reconnect
- updated the firmware, tried both steps above
- I have also tried to connect the drive in MTP mode (which allegedly works in Hardy?) to no avail.

The strange thing is I have had success with this player when using earlier versions of Ubuntu.  I have installed Hardy after a several-month Ubuntu hiatus, and I cannot get this thing to work!  

Any help is greatly appreciated.

---

### Post by phidia on 2008-07-21
See if [this thread]("http://ubuntuforums.org/showthread.php?t=771952&highlight=E280") is of use to you. Hope that helps.

---

### Post by limberlegs on 2008-07-21
Thanks for the reply.  I tried what the link above suggests, and it seems to cause Rhythmbox to crash.  I ran rhythmbox before selecting the plugin, selected the plugin, connected the Sansa, and Rhythmbox froze.  I did a force quit on Rhythmbox and tried to reload it, but it wouldn't even start.  

Any thoughts?

---

### Post by NewDisciple on 2008-07-22
Here are two links that might help:[ubuntuforums.org/showthread.php?t=713834&highlight=Sandisk]("ubuntuforums.org/showthread.php?t=713834&highlight=Sandisk")& [ubuntuforums.org/showthread.php?t=713834&highlight=Sandisk]("ubuntuforums.org/showthread.php?t=713834&highlight=Sandisk")I think these help with syncing playlists etc.  If you have installed nautilus scripts it is very easy to right click select scripts & then rootilus.  Once you are root right click, properties, permissions and give your self write priviledges or do the same thing from the command line- 
> sudo passwd root
 > sudo chmod 777 -R /media/PATHTO
 Do this while it is mounted.
I believe that Sansdisk would be the media name.  Maybe someone else can verify or not.  Maybe its just media, not sure.  Hope this helps.  I can read & write on mine but its been a while so I don't remember exactly.

---

### Post by limberlegs on 2008-07-22
Thanks for the suggestion.  When I tried to force write access through the command-line as you suggest, a very strange thing occurs.  It says that 'Sansa e280' (the name given to the device) does not exist, even though it lists it when I run the command 'ls' on /media.  

Another thing:

I tried to use the Sansa on an installation of Xubuntu 7.10, and it worked perfectly.  It seems that this problem is something specific to Hardy Heron.

---

### Post by NewDisciple on 2008-07-22
Two more links (don't know if that helps or not):[ubuntuforums.org/showthread.php?t=713834&highlight=Sandisk]("ubuntuforums.org/showthread.php?t=713834&highlight=Sandisk") &  [http://ubuntuforums.org/showthread.php?t=312196&highlight=sansa]("http://ubuntuforums.org/showthread.php?t=312196&highlight=sansa")
The only other thing I can think of trying, is open the media file & then sansa e280.  Take each file in that, right click, pick properties & then permissions tab.  Maybe it will let you change them without being root???
Are you using gnome?  I find that for me it is much easier to do this stuff with nautilus scripts.  I'm not really a command line guy as I don't often have a need for it.  Rather than waste time looking for bash commands I just rely on the scripts.
Regarding the link about adding a script to your Sansdisk for Banshee & Rhythm Box; I think it no longer applies to Banshee.  Rhythm Box works fine however.  Wish I could be of more help but thats all I got.

---

### Post by limberlegs on 2008-07-22
Thanks for the reply.  I have indeed read both of those posts, and unfortunately neither addresses my specific problem.  

In my case, the drive seems to mount just fine, but it only allows me read-only access.  

Perhaps I'll grant myself root access BEFORE mounting the drive, and see if that works.

Again, to all: any help is greatly appreciated.

---

### Post by limberlegs on 2008-07-22
OK, I gave myself superuser access by going to Terminal and typing "sudo su".  Unfortunately, the player still says "the filesystem is read-only".  I also tried right-clicking on the MUSIC folder and editing the permissions.  It says that I (the owner) have permission to "create and delete files" under "folder access", and under file access it says "---".  When I try to change the root user's permissions, it returns this:

"Sorry, couldn't change the permissions of "MUSIC": Error setting permissions: Read-only file system"

Any thoughts?

---

### Post by koenbeek on 2008-08-30
Maybe there are some error on the Sansa drive

sudo fsck.msdos -a /dev/sdf1

can correct this

/dev/sfd1 is the device corresponding to your Sansa (use df when the Sansa is mounted to see whether it is the same)

---

### Post by kellingt on 2009-03-19
Well, that certainly helped me.  Thanks for the tip koenbeek!!!

---

