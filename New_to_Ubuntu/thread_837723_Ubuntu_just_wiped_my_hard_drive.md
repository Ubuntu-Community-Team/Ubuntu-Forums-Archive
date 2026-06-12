---
title: "Ubuntu just wiped my hard drive"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by SMA11784 on 2008-06-22
So I tried logging in this afternoon, enter my username and password, and the computer hangs.  It gets stuck between exiting the logon screen and the start up music.  So I pushed the power button thinking it was stuck and I would reset.  As I was doing this the music started.  I released the button, and the computer started to shut down.

I tried loggging in again only to find that I couldn't.  Truthfully I wasn't really paying attention, but it told me to run some program fsck manually.  It kept prompting me for "fix this?" and I just kept hitting yes.  I finally get around to logging in and all of my files are gone.  All my videos, my music, my documents, gone.

Please, there has to be something I can do to recover some of this.

---

### Post by niyonk on 2008-06-22
Sorry, mate :frown:
I dont think there is a recovery mechanic in Ubuntu

Maybe someone more experienced can shed some light into this....
Although, i dont see how it wiped your home files...:(

---

### Post by SMA11784 on 2008-06-22
Really I brought this on myself.  As soon as it gave me a command prompt, I should have just shut down and taken it somewhere, but I just sort of did what it told me and now everything's gone.  All my videos, pictures of my vacations, pictures of my niece, songs I was writing...

If anybody knows a place or a service where I can take my computer to see if they can't recover anything, please let me know.

---

### Post by KenBW2 on 2008-06-22
Don't blame yourself - I've run fsck plenty of times and, although it gets rid corrupted files, I've never seen it do anything that drastic.
Stories like this remind me that I should make a backup one day...

Sorry to hear about your situation :(

---

### Post by randy78 on 2008-06-22
Wait!

All may not be lost!

Pop in a LiveCD (Either Ubuntu/Knoppix/etc...) and navigate to your lost disk (Should say something like 200gb media or similar).

Menu>Places>Computer>(your disk)
Double click to open

At this point, you should plug in a USB external hard-drive and copy your /home directory to it.

After that, if you can't seem to get it working, you can always re-install, and you will have your /home directory to pull your files from ;)

Otherwise, there are EXCELLENT file recovery tools available for Linux, but don't give up hope yet!

Good luck!

---

### Post by Tatty on 2008-06-22
Unfortunately it sounds like your hard drive has had a major failure somewhere which resulted in large numbers of files being corrupted.

If your files appear to have been deleted then stop using your hard disk immediately, as the more you use it, the less likely it is you can recover lost data.  It may be helpful for you to boot into a live CD while you try to recover your data, as it will mostly leave your hard drive alone.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) this page may be of some help to you.  Good luck, I hope you can find your data.

---

### Post by SMA11784 on 2008-06-22
> **randy78 said:**
> Wait!

All may not be lost!

Pop in a LiveCD (Either Ubuntu/Knoppix/etc...) and navigate to your lost disk (Should say something like 200gb media or similar).

Menu>Places>Computer>(your disk)
Double click to open
No dice.  home/sean is basically empty.

Oh, my name's Sean by the way.

I just destroyed about 50 gigs of videos and music and images I made and songs I was writing, pretty much my entire life was on this box this morning and now its gone.

How does [this]("http://www.data-recovery-software.net/Linux_Recovery.shtml") work?  Tell me everything I need to know before I make this worse.

---

### Post by RATM_Owns on 2008-06-22
With a quick look, that says it is for ext2 file systems.
Ubuntu usually makes a ext3 file system.

---

### Post by subaruwrc01 on 2008-06-22
> **SMA11784 said:**
> No dice.  home/sean is basically empty.

Oh, my name's Sean by the way.

I just destroyed about 50 gigs of videos and music and images I made and songs I was writing, pretty much my entire life was on this box this morning and now its gone.

How does [this]("http://www.data-recovery-software.net/Linux_Recovery.shtml") work?  Tell me everything I need to know before I make this worse.

Don't feel too bad.

I lost 400 gigs when I forgot to unsafely eject beforing turning off my external.

---

### Post by SMA11784 on 2008-06-22
Did you have pictures of your niece?

I had pictures of my niece.  She's about three months old.  She's adorable.

I had notes on songs I was writing.  Chords, lyrics, poetry waiting to become lyrics, I had things I did in photoshop, a lot of it was silly ****, but there was a handful of what might constitute art.  I had journal entries.  Little things I jotted down, stories, days of my life, things that I didn't really have saved anywhere else.

Really, a lot of it could stand to go.  I had things I drew in paint eight years ago that weren't really worth saving.  I had a bunch of videos of when I was trying to learn to do an aerial cartwheel that I don't really need anymore.  And a lot of stuff is on the web.  Everything I posted to YouTube can be recovered.  There's only like a gig, at most, of stuff I really need back.

---

### Post by randy78 on 2008-06-22
> **SMA11784 said:**
> No dice.  home/sean is basically empty.

Oh, my name's Sean by the way.

I just destroyed about 50 gigs of videos and music and images I made and songs I was writing, pretty much my entire life was on this box this morning and now its gone.

How does [this]("http://www.data-recovery-software.net/Linux_Recovery.shtml") work?  Tell me everything I need to know before I make this worse.

Yeah, it looks like R-Linux won't cut it unless your drive was formatted using EXT2.

The link Tatty posted is as good as it gets and has all the info you're going to need to get back on your feet.

If you aren't comfortable doing this yourself, grab a friend who could help out.

Most importantly, try to remember that all is not lost until you've tried EVERYTHING.

At the very least, you could burn a Knoppix ISO, Boot it up and use Photorec to recover a large portion of your files.

You're going to need an external hard drive for this (to transfer the recovered files to).

Best advice is to not use that computer unless you're using a LiveCD, as you could lose a lot more if data is being written to the sectors where the lost files were residing.

Best of luck

---

### Post by louieb on 2008-06-22
Look in the lost+found directory. fsck should use that to place files it has found while repairing a file system.  
I've use Knoppix to recover windows file don't know how it is with ext3.
[Rescue FAQ - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Rescue_FAQ")

testdisk is available on the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") I've seen quite a few post that say it  retrieved there data. 

Good luck.

---

### Post by SMA11784 on 2008-06-22
I saw lost+found but I can't get into it.  I'm running off a Fiesty live CD and it says "You do not have the permissions necessary to view the contents of "lost+found"."

---

### Post by subaruwrc01 on 2008-06-22
You have be root in order to access lost+found.

---

### Post by SMA11784 on 2008-06-22
> **subaruwrc01 said:**
> You have be root in order to access lost+found.
Okay, how?

---

### Post by tagra123 on 2008-06-22
from a terminal

gksudo nautilus

and you can open the folder then

There might not me much that's usable but I recovered some this way.

When you are setting up your system again put home in a seperate partition and make backups -- saves a lot of grief.

---

### Post by subaruwrc01 on 2008-06-22
> **SMA11784 said:**
> Okay, how?

```

sudo cd <directory>
```

---

### Post by Happy_Man on 2008-06-22
> **subaruwrc01 said:**
> You have be root in order to access lost+found.
From a liveCD, run ```
gksudo nautilus
``` into the alt-f2 dialog and then try. Hopefully your stuff is there. **fingers crossed**

---

### Post by randy78 on 2008-06-22
You have to chown (change ownership) of the folder...

I can't remember exactly (google: ubuntu chown folder) but it's something like 

sudo chown hda1/lost+found user:user

you can also open a terminal and type: 
man chown

---

### Post by steveneddy on 2008-06-22
Sorry about your problem.

Many of us learn to back-up data after a catastrophic loss like this.

Just back-up /home to a USB stick in the future and you should be safe.

---

### Post by SMA11784 on 2008-06-22
Alright, I'm in lost+found and it looks like everything really important is still in there (including my trash, ironically).  This experience has taught me two important things.

1) I'm not smart enough to run linux.
2) External hard drives are my friend.

Thank you all for your help.

---

### Post by tagra123 on 2008-06-22
Found a page dedicated to this

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Heard good things about this one

[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

---

### Post by randy78 on 2008-06-22
Glad everything is there for you!

Be sure to mark as solved :)

---

### Post by tagra123 on 2008-06-22
Backups, backups, backups...

Here's a script I use. There might be GUIs now that do the same thing, but I like these scripts. I do not even have to think about the backups. Occasionally you should copy the backup files to CD -- just to be safe.  Mine backs up hourly for important files and dirs that change often, once a day for others and once a week the entore home partition.

Scripts can be modified to work with an external drive and do not have to be over network.

[http://www.ubuntuforums.org/showthread.php?p=1402091](http://www.ubuntuforums.org/showthread.php?p=1402091)

About once a month I use sysrescue cd to create an entire image of the home and root partition -- if something bad happens break out sysrescue and restore the images and then recover files from the most recent automatic backup.

---

### Post by SMA11784 on 2008-06-23
It looks like fcsk moved virtually *everything I have* into lost+found.  I'm going through it and it all appears to be intact, in a similar folder structure (desktop is in its own folder, as is Pictures, Documents, etc.).

Is there anything specific I have to do to move files out of lost+found?  Some command I should be using, or can I just click and drag?

---

### Post by Happy_Man on 2008-06-23
> **SMA11784 said:**
> It looks like fcsk moved virtually *everything I have* into lost+found.  I'm going through it and it all appears to be intact, in a similar folder structure (desktop is in its own folder, as is Pictures, Documents, etc.).

Is there anything specific I have to do to move files out of lost+found?  Some command I should be using, or can I just click and drag?
Clicking and dragging should do nicely.

---

### Post by xplode on 2008-06-23
> **SMA11784 said:**
> Alright, I'm in lost+found and it looks like everything really important is still in there (including my trash, ironically).  This experience has taught me two important things.

1) I'm not smart enough to run linux.
2) External hard drives are my friend.

Thank you all for your help.

don't see a reason for 1) at all - any os can lose data, any drive can fail - i've lost data on harddrives and usb sticks under windows. under linux as well. advantage on linux is i feel i have a lot more options to recover the data. if this had happened on windows, do you think you would have found a lost+found directory?

the thing you should take away from this is: BACKUP stuff that you can't stand to lose. really... it's so cheap, so easy and saves so much grief.

but i'm sure you will do that now :).

---

### Post by brons2 on 2008-06-23
Great story, glad you got your stuff back.

I need to back up my stuff TODAY!!

---

### Post by SMA11784 on 2008-06-24
Well, bad to worse, gang.  I managed to get into lost+found thanks to several people on here, and I found that everything I had on my hard drive, 45GB had been moved into lost+found in an identical directory structure.  It was all there, it was all intact, the only difference was all the folders had been given names like #23092380 etc.  I figured the easiest way to restore my files would be to change the owner of lost+found from root to myself so I can freely move files back onto my desktop and other media and whatnot.  This worked nicely for a little while; I restored everything that had been on my desktop.  But halfway through moving my .wine directory back, something happened.  Nautilus winked out of existence, my desktop icons vanished, and the system stopped responding entirely.  I tried several minutes shutting down the normal way (clicking the shut down button and hitting ctrl+alt+del did nothing) so I ended up just holding down the power button until it shut off.  I've been able to boot back up successfully exactly once, at which point the same error occured when I tried simply viewing a folder in lost+found.

I can no longer boot up without entering fsck, which moves unbearably slowly.  As I type this, it's at Pass 2, having started Pass 1 at about 11:30 (could've been earlier, I'm not really sure).  Theoretically, after it finally finishes, I'll be able to log in again at which point I'm going to try accessing lost+found as root again rather than as myself which I expect won't work because root is no longer the owner of lost+found.

Oh, and by the way...
> **xplode said:**
> if this had happened on windows, do you think you would have found a lost+found directory?
...nothing like this has ever happened to me in Windows XP.  *Ever.*  That's why some of the files I'm talking about are six years old.

---

### Post by sydbat on 2008-06-24
I think your Hard Drive is borked. If you can, backup as you can to the external HDD (maybe in fits/starts) then get a new HDD. Sorry.

---

### Post by Canis familiaris on 2008-06-24
> **SMA11784 said:**
> Well, bad to worse, gang.  I managed to get into lost+found thanks to several people on here, and I found that everything I had on my hard drive, 45GB had been moved into lost+found in an identical directory structure.  It was all there, it was all intact, the only difference was all the folders had been given names like #23092380 etc.  I figured the easiest way to restore my files would be to change the owner of lost+found from root to myself so I can freely move files back onto my desktop and other media and whatnot.  This worked nicely for a little while; I restored everything that had been on my desktop.  But halfway through moving my .wine directory back, something happened.  Nautilus winked out of existence, my desktop icons vanished, and the system stopped responding entirely.  I tried several minutes shutting down the normal way (clicking the shut down button and hitting ctrl+alt+del did nothing) so I ended up just holding down the power button until it shut off.  I've been able to boot back up successfully exactly once, at which point the same error occured when I tried simply viewing a folder in lost+found.

I can no longer boot up without entering fsck, which moves unbearably slowly.  As I type this, it's at Pass 2, having started Pass 1 at about 11:30 (could've been earlier, I'm not really sure).  Theoretically, after it finally finishes, I'll be able to log in again at which point I'm going to try accessing lost+found as root again rather than as myself which I expect won't work because root is no longer the owner of lost+found.

Do not worry mate! Root is the super user and can access anything.
And since the partition is intact, I'm sure you'll get them back.
I suggest you use Live CD to recover your files.
I hope you recover your files.

> **SMA11784 said:**
> 
Oh, and by the way...

...nothing like this has ever happened to me in Windows XP.  *Ever.*  That's why some of the files I'm talking about are six years old.
[/QUOTE]
Well data loss is not the responsible of the OS. In your case since the hard disk is this old, so it has probably developed bad sectors and hence it failing. The only difference is that Linux shows earlier symptoms of disk crash as compared to Windows.
Trust me I have lost gigabytes of data when I used Windows. And it was not Windows fault anyway, it has the hard disk's fault. But I have to say I would have beem grateful if Windows had did the same what Linux did to you I would have been able to back up my system and not lost my precious data.
Don't be drastic and do not wipe out Linux.

---

### Post by Troll_the_Great on 2008-06-24
I lost once 90 gigs of data on Vista and all I did was use "disc cleanup"...I don't think that was normal, no?So don't be too hard on linux...I use it for 3 months now and I just love it.If I manage to make my favorite games work, by by windows for good (sadly, at the moment I dual boot...).

---

### Post by SMA11784 on 2008-06-25
> **Anurag_panda said:**
> In your case since the hard disk is this old...No.  The hard disk is six months old.  Some of the files are six years old, transfered across four computers.

I am certain this is a software fault, but it's going to take a few days to prove it.

---

### Post by Canis familiaris on 2008-06-25
> **SMA11784 said:**
> No.  The hard disk is six months old.  Some of the files are six years old, transfered across four computers.

I am certain this is a software fault, but it's going to take a few days to prove it.

Six month old Hard disks can be faulty too. mate! Also it may be possible that the Linux partition got corrupted and fsck drastically moved your files to lost+found.

---

### Post by SMA11784 on 2008-06-25
UPDATE: Booted up three times.  Pretty much every time, fsck starts up, fails, I do it manually, sit through an hour of holding down Y, then when I can finally log in, the computer is in exactly the same condition it was before I shut down.

All of my files, my application data for Firefox, and everything I had in .wine are back where they belong (and remain there through repeated fsck-ings), but several folders take so long to display, the file browser basically dies when I try to view them, notably Pictures, Videos, .Trash, and humorously enough lost+found.  I can freely access subfolders within these folders through the tree view.

External hard drive is arriving today.  I'm going to move everything worth saving off the hard drive and reinstall the OS and I expect all these problems to go away.  If you don't hear from me again, it means I was right.

---

### Post by Tuxoid on 2008-06-25
SMA11784, how long have you had that hard drive (the internal)?

And it this a laptop or desktop we're talking? I ask, because laptop hard drives are more susceptible to damage (with a laptop's mobility and all).

---

### Post by Canis familiaris on 2008-06-25
> **SMA11784 said:**
> UPDATE: Booted up three times.  Pretty much every time, fsck starts up, fails, I do it manually, sit through an hour of holding down Y, then when I can finally log in, the computer is in exactly the same condition it was before I shut down.

All of my files, my application data for Firefox, and everything I had in .wine are back where they belong (and remain there through repeated fsck-ings), but several folders take so long to display, the file browser basically dies when I try to view them, notably Pictures, Videos, .Trash, and humorously enough lost+found.  I can freely access subfolders within these folders through the tree view.

External hard drive is arriving today.  I'm going to move everything worth saving off the hard drive and reinstall the OS and I expect all these problems to go away.  If you don't hear from me again, it means I was right.

If you manage to recober your data, PLZ mark the thread as solved
BTW You are not going to stop using Ubuntu? Are You? That would be hasty.

---

