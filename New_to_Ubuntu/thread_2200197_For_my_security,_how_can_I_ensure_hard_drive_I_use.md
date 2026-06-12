---
title: "For my security, how can I ensure hard drive I used is NOT undelete-able?"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by palawanbeach on 2014-01-17
Someone lent me a 1 TB external USB hard drive for me to temporarily place my personal files. I plan on deleting all my personal files, of course. But how can make sure that my personal files cannot be recovered or undeleted?

---

### Post by DuckHook on 2014-01-18
The app you want is called *shred*. It is included by default in any typical Ubuntu install. Read its man page for usage. Be very very careful with it as defining the wrong drive is guaranteed to result in disaster. A properly shredded drive is absolutely unrecoverable, even by forensic tools (that's the point).

---

### Post by palawanbeach on 2014-01-18
DuckHook,

Thank you for your reply. 

Question 1: Could I run  shred off of my internal hard drive?

Q2: If so, would my internal hard drive be safe from any potential accidental shredding?

---

### Post by DuckHook on 2014-01-18
1.yes,* shred* is a command line app that can be run within your current session, and
2. no, nothing is safe from it just because it is being run from your internal HDD. In general, Linux assumes that users know what they are doing and will allow you to shred any file you want including, say, your kernel file.

Also note that *shred* will not be effective with a journaled file system if you are shredding individual files. You should therefore make sure your external USB is formatted using ext2, or, if you want ext4, that it be mounted for the purposes of shredding with the data=ordered or data=writeback modes. See man page for details. Also [this]("http://www.howtoforge.com/how-to-securely-destroy-wipe-data-on-hard-drives-with-shred") link.

---

### Post by palawanbeach on 2014-01-18
DuckHook,
Thank you for your response.

I installed [Shredder]("https://code.google.com/p/shredder/"), a GUI for shred, to make it harder for me to make mistakes.

---

### Post by DuckHook on 2014-01-18
> **palawanbeach said:**
> ... [Shredder]("https://code.google.com/p/shredder/"), a GUI for shredWasn't aware this existed, but if you feel more comfortable with GUI, by all means.

Please mark thread "solved" using thread tools at head of page.

Good luck and Happy Ubuntuing!

---

### Post by Dave_L on 2014-01-18
> **palawanbeach said:**
> Someone lent me a 1 TB external USB hard drive for me to temporarily place my personal files. I plan on deleting all my personal files, of course. But how can make sure that my personal files cannot be recovered or undeleted?

The external drive is only for data storage, not for a Ubuntu installation?

Personally, I would use encryption for this.  For example, create a Truecrypt volume on the external drive, and only place your personal files within that volume. Use a strong passphrase for the volume.

If for some reason you are unable to delete the Truecrypt volume when returning the drive, your personal data will still be protected.

---

### Post by sandyd on 2014-01-18
> **Dave_L said:**
> The external drive is only for data storage, not for a Ubuntu installation?

Personally, I would use encryption for this.  For example, create a Truecrypt volume on the external drive, and only place your personal files within that volume. Use a strong passphrase for the volume.

If for some reason you are unable to delete the Truecrypt volume when returning the drive, your personal data will still be protected.

+1

---

### Post by palawanbeach on 2014-01-23
Dave_L & Sandyd,
Yes, I used the exetrnal USB hard drive for data storage only.

Next time, I'll try using a Truecrypt volume. But now, it's too late to do that, because I already stored files on the external USB hard drive without truecrypt.

---

### Post by palawanbeach on 2014-01-23
DuckHook,
So I ran Shredder, I selected the external USB hard drive folder. I put a check mark for both Zero-ing and for Remove. I then clicked the Shred button. But it was done in less than one second. I was expecting the shredding to take many hours! 
> 
==========
Target File: /media/external1
Iterations: 5, Zero-ing: True, Remove: True.
Here we go! Pray that it doesn't take anything bad out!
Shredding: /media/external1
Done with all the shredding! 
You may proceed to exit or shred more stuff again.
==========


What am I doing wrong?

---

### Post by Dave_L on 2014-01-23
It's possible that it the process was quick. It depends on various factors, such as the CPU speed, drive speed and quantity of data to process. How much space did the files occupy?

I don't know anything about "Shredder", but the man page for "shred" describes the options to control its behavior.

Other choices are the commands "wipe" (secure file deletion) and "srm" (secure remove, included in the package "secure-delete").  These probably need to be installed if you want to use them. If the files have already been deleted, there's another command "sfill" (also in the package "secure-delete") that wipes free space on a device.

These are all documented on man pages, either viewed with the "man" command or at [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

---

### Post by 3rdalbum on 2014-01-23
> **palawanbeach said:**
> DuckHook,
So I ran Shredder, I selected the external USB hard drive folder. I put a check mark for both Zero-ing and for Remove. I then clicked the Shred button. But it was done in less than one second. I was expecting the shredding to take many hours! 


What am I doing wrong?

There's no way it should be that quick, of course. Zero'ing a drive takes minutes, not seconds.

A couple of things to check:

1. Do you have the 'shred' command installed? The GUI should ideally have installed it automatically, or checked that it was installed, but there's a possibility it didn't.
2. Are you expected to select /media/external1, being the mount point of the drive; or were you supposed to select the actual device corresponding to the drive? (/dev/sdb or something similar to that; starting with /dev/).
3. How old is the GUI compared to the backend? If 'shred' has changed options since 'shredder' was last released, then 'shredder' might be passing invalid options to 'shred'.

If I was you I would just use 'shred' on the command-line. How hard can it be? And you'll have more of an idea what's going on rather than being kept totally in the dark by a badly-written GUI frontend.

Personally, I go even more old-school - I use 'dd' - but using 'shred' on the command-line will be easier for you.

---

### Post by palawanbeach on 2014-01-25
3rdalbum,
I went with shred. Made it "shred" with five passes. I started about 2 days ago. I expect it to be done in 4 more hours.

---

