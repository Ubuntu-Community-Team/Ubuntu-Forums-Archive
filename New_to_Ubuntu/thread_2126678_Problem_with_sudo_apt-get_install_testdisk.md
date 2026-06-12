---
title: "Problem with sudo apt-get install testdisk"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by Maggie900 on 2013-03-17
Sorry,  I know this is terribly basic.
I have a Dell laptop with a corrupted hard disk. I am trying to use testdisk with Ubuntu 12.10 to try to recover at least the recovery partition, if not the entire disk.
I succeeded in recovering the very small [dell-diagnostic] (or something like that) partition. To celebrate my success, I booted the computer off that partition. Now I've inserted my Ubuntu boot CD and the thumb drive on which I put  testdisk and restarted the PC in Ubuntu.
Alas, I was unable to get testdisk to work again. So I deleted the directory into which I'd extracted it, and re-extracted it. I then renamed the directory into which it had been extracted "tdisk" (without the quotes obviously). I made the name tdisk in case the problem was from having both the executable file and directory named the same. (I had the problem described below several times in a row, and started from scratch each time --- that is, by deleting the files I'd extracted, re--unpacking the archive and then renaming the directory, whose default name was much longer and included the version number)
Then I typed
  cd /media/SANDISK/tdisk
(pwd now reporting /media/SANDISK/tdisk for the rest of my terminal session both to save on typing and make sure any errors weren't from leaving out the path)
  sudo apt-get install testdisk
Unfortunately, it came back with
  E: unable to locate package testdisk
So of course sudo testdisk resulted in an error message.
  sudo ls -l testdisk *
shows me that the file is indeed in the current folder

I am pretty sure I did it this way the first time when it worked.

So I need to know:
(1) What did I do wrong and how should I be doing this?
(2) Trial and error the first time showed me that 'sudo apt-get install testdisk' is a necessary step to be able to run testdisk. The only part of this command that I understand is the 'sudo' part. A *brief* explanation would be greatly appreciated -- I've had about enough of man pages today to last a lifetime <g>
(3) Note that testdisk is on a thumb drive, as I didn't want to write this to the hard disk, possibly resulting in a lower chance of recovery -- my Ubuntu boot device is a DVD. If I restart the computer after successfully using testdisk, how can I use it again without having to restart with sudo apt get-install testdisk? Not that this is all that hard, but I imagine that the testdisk executable persists if I understood what I was doing.
(4) As a result of reading the instructions and luck, I was able to get back that small [dell-diagnostic] partition. What I'm really interested in is the restore partition. I would like to save that on an external drive, put a new drive in this machine and then use the saved restorre partition data to reinstall Windows and whatever else came with the machine. Is it likely that, if I succeed in recovering the restore partition, that I can use it to make a fresh installation on the new drive? I don't necessarily feel compelled to put a restore partition on the new drive, as the user has never bothered to try this route or create restore disk. (I also have a two month old Windows 8 laptop here to repair that she dropped while it was running. I can't even make that one go into setup, give me the option to boot of an external drive or its built-in optical drive. The current laptop in question is less than a year old.)

I would like to apologize again for the simple question that's been answered 10,000 times already. This is very humbling because I am a Windows and OS X expert; before that I was a DOS expert. That came after CP/M. My unix/linux skills have always been weak at best. I'd really appreciate a good resource for learning basic unix/linux command-line stuff that goes beyond cd, mkdir, rm and chmod, which along witith pico and nn are all I know how to do in this environment. Reading man pages doesn't work well with me, and I think a real dead-tree or kindle book would be the best way for me to learrn in an orderly fashion. (Over 20 years ago, when I subscribed to my current mail and website provider, which also provides access to all the common unix shells via ssh, I inadvertently started a months-long flame war by asking if I should learn emacs or vi. When I later asked for a book recommendation, folks still remembered my emacs vs. vi question and the flame war started again, so I never got a good recommendation. So I am still using pico and generally helpless at a unix command-line.)

Finally, I feel compelled to admit that this isn't my PC. A client is paying me to do this; -- obviously I'm not charging by the hour. Otherwise I wouldn't bemoan the loss of Office and Norton.
Thanks for the help and apologies for the unrelated ranting above!

---

### Post by tgalati4 on 2013-03-17
It looks like you booted a Live DVD of Ubuntu 12.10 and installed *testdisk*.  When you run a live disk, you are running in RAM and anything you install stays in RAM, until you reboot, then it is gone.

Typically, you would get a large, external disk, at least the size of the internal disk, then use *testdisk* to work its magic.  You should not have to reboot, but keep the live session up as long as possible, until all of the data is recovered.  If *testdisk* can't recover the file/directory structure completely, then use *photorec* (part of testdisk) to recover individual files.  

Sudo is simply "Super User Do"  or a way to execute super user commands.  The root account in Ubuntu is disabled for security reasons, so *sudo* is a way to for the primary user to administer his machine.  It's similar to the annoying Windows User Access Control.

You should not reboot, nor do anything that causes additional hard drive stress, until after all of the data is recovered.  You may only have an hour of life left on the drive or 10 minutes.  Do you really want to spend that time booting Windows?

---

### Post by Paqman on 2013-03-17
> **Maggie900 said:**
> 
(2) Trial and error the first time showed me that 'sudo apt-get install testdisk' is a necessary step to be able to run testdisk. The only part of this command that I understand is the 'sudo' part. A *brief* explanation would be greatly appreciated -- I've had about enough of man pages today to last a lifetime <g>


I feel your pain, man pages suck. I avoid them as much as possible.

As for the command, it's what you do to automatically download and install a package on Ubuntu:

sudo = Super User Do = elevate the user's privileges high enough to (in this case) install something

apt-get = Tells the Advanced Packaging Tool to get something

install testdisk = tells APT to connect to the online repositories, grab the latest version of testdisk and install it.

On Linux you don't have to manually download and unpack things liek you do on Windows. We have package managers that can handle downloading, installing, upgrading and removing tens of thousands of software packages. Package managers are the best thing about Linux IMO.

As long as you're connected to the internet you should be able to get testdisk, but you may need to update your package lists first, please do:
```
sudo apt-get update
```
then
```
sudo apt-get install testdisk
```
and post back any errors if you get them.

> (3) Note that testdisk is on a thumb drive, as I didn't want to write this to the hard disk, possibly resulting in a lower chance of recovery -- my Ubuntu boot device is a DVD. If I restart the computer after successfully using testdisk, how can I use it again without having to restart with sudo apt get-install testdisk? Not that this is all that hard, but I imagine that the testdisk executable persists if I understood what I was doing.

Running off a DVD means that all your changes are lost when you reboot. Testdisk would be installed into RAM and run from there. You're right to not write anything to the disk you want to recover, but you will need to have somewhere to recover the files TO. Your USB stick seems like the best place for this, or maybe you could use a network location?

But first things first, let's get testdisk installed and go from there.

---

