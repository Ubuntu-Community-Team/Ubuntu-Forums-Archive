---
title: "Transferring everything from 1 PC to another, but rather a script?"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by vaalir on 2013-09-11
This may be a 2 part question......

I'm fairly non-advanced in linux, but have decided to desert windows all togheter (i lie.. my HTPC, is still windows, really tried on this one)

After alot of tinkering with ubuntu 12.04 these last days, i'm starting to realise i dont wanna lose all this, and furthermore, i want what i have on my desktop reflected to my laptop.

so..

1. 
Can i make some sort of image file from my desktop that i can install to my laptop\other pc's?

2.
if its required that i go down to 32bit for the install, i assume i cannot just install an image of the OS, script to auto-make repositorys and commands for downloads and stuff? or do i now have to take the step to go ****ing balls deep in something i dont fully understand yet?

Bonus question:
I love dropbox, love love love... so far my home folders point to the respective folders in dropbox, any more tips on deep integration? would love to leave my 64bit desktop and pick up where i left on my 32 bit laptop


Look forward to some knowlegde!

---

### Post by Mark Phelps on 2013-09-11
If your current install is 64-bit, there is no way to convert that to 32-bit; you would have to install 32-bit fresh.

You can use Clonezilla to make image files, but that would only allow you to "clone" your current install.

---

### Post by scbingham on 2013-09-11
As Mark said, you can't convert Ubuntu 64 bit to 32bit, so you'll have to do a fresh install & install 32 bit versions of any programs you have added. Then point your home folders to your dropbox folders.

As far as your HTPC goes, have you looked into xbmc?

---

### Post by sudodus on 2013-09-11
> **vaalir said:**
> This may be a 2 part question......

I'm fairly non-advanced in linux, but have decided to desert windows all togheter (i lie.. my HTPC, is still windows, really tried on this one)

After alot of tinkering with ubuntu 12.04 these last days, i'm starting to realise i dont wanna lose all this, and furthermore, i want what i have on my desktop reflected to my laptop.

so..

1. 
Can i make some sort of image file from my desktop that i can install to my laptop\other pc's?

It depends ...

If the other computer can run 64 bit systems, you can. It is easy to find out. Try to boot that other computer with the 64-bit Ubuntu boot CD/DVD/USB drive. If it does not work, try to find the specification of the CPU to make sure if it is a 32-bit or 64-bit system. That should be possible from the control panel in Windows.

Please let us know the specifications of both computers: brand name, model, cpu, ram (size) and graphics chip! It will make it easier to give good advice :-)
> 
2.
if its required that i go down to 32bit for the install, i assume i cannot just install an image of the OS, script to auto-make repositorys and commands for downloads and stuff? or do i now have to take the step to go ****ing balls deep in something i dont fully understand yet?

Bonus question:
I love dropbox, love love love... so far my home folders point to the respective folders in dropbox, any more tips on deep integration? would love to leave my 64bit desktop and pick up where i left on my 32 bit laptop

Look forward to some knowlegde!

> **Mark Phelps said:**
> If your current install is 64-bit, there is no way to convert that to 32-bit; you would have to install 32-bit fresh.

You can use Clonezilla to make image files, but that would only allow you to "clone" your current install.

+1

Clonezilla will give you a good image of the present 64-bit system, that can be used to restore it '100%'.

If the other computer has 32-bit hardware (CPU etc), the best alternative might be to have 32-bit systems in both computers, because then you can have the same system in both computers and even in an external USB 2 or 3 or eSATA disk. Because if you avoid proprietary drivers (for graphics and wifi), Ubuntu and Ubuntu based flavours and distros are ***portable*** between different computers. The drivers are selected at boot time. This is a big advantage compared to operating systems with a paid license, that are locked to one particular computer.

So if you make the same or similar tweaks to a system that works in the other computer, it should also run in the 64-bit computer. Maybe one of the computers needs a boot option (that you add at the grub menu).

If you want to try this concept, you can read about the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") and try it.

---

### Post by vaalir on 2013-09-11
one button installer eh? thanks! gonna look at that in the late nights :)

the choice is clear... abandon the 32bit computer! most pc's are 64bit anyways and i'm looking to upgrade anyways.. maybe about time then.

you mention to avoid proprietary drivers? i use that on my desktop now, will that affect my future  64bit laptop?

> [B]Backup

You want a simple method to backup (and restore) your whole installed linux system. The One Button Installer combines installation, backup and restore in one set of tools. 

[B]Your own portable Ubuntu based linux system

You want to make your own linux system portable and port it to a USB pendrive or to be installed in another computer to be used by yourself, or to be uploaded to the internet for sharing with other people. The One Button Installer can do it in a simpler way than to remaster the code and make an own iso file. [/B][/B]

is what i want! 
so how about now: i install my desktop OS to my new laptop. only need to fight with propriatry drivers. can dropbox be set to be synced with root? or would both my PC's need to be the exact same config? i want as much "cloud" as i possibly can

---

### Post by sudodus on 2013-09-11
I suggest that you get a fast USB 3 pendrive (I think  Sandisk Extreme 32 GB is the best one right now, [see this link]("https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites")) and use it with a portable installed system, that you can easily move from one computer to the other.

To keep it generally portable you should stick to the built-in drivers. But if you 'only' want it portable between your own computers, and you have the same or similar graphics chips, for example nvidia of about the same age, you can test and find an nvidia proprietary driver, that works in both computers. The same method might be suitable or necessary for wifi.

I think it is a bad idea to sync the root file system '/' with dropbox, because it is live (changing all the time, so that the syncing will probably be very busy and the result inconsistent anyway). But you can sync several of the directories in /. It is better to make a complete backup of the root file system when you have booted from another drive. It could be done with a Clonezilla live drive, or an OBI live drive, or any of many other systems for cloning or backup. Such a backup will be fairly easy and fast, if you have an own data partition or drive for your personal files, photos, video-clips, documents, presentations etc.

---

### Post by vaalir on 2013-09-12
yeah, you'r totally right, syncing the root folder would probably only cause havoc. :P

The plan is now:
install a 32bit ubuntu on my laptop and set it up the way i like it, "my clean slate" sort of.

now, i use OBI to make that clean slate portable?
what to use to make an install CD of my setup?


so far thanks alot! you are being most helpful

on a sidenote:
that one button thing, doesnt look so straightforward as i'm used to. anything particular here?

---

### Post by sudodus on 2013-09-12
> **vaalir said:**
> yeah, you'r totally right, syncing the root folder would probably only cause havoc. :P

The plan is now:
install a 32bit ubuntu on my laptop and set it up the way i like it, "my clean slate" sort of.

now, i use OBI to make that clean slate portable?
what to use to make an install CD of my setup?


so far thanks alot! you are being most helpful

on a sidenote:
that one button thing, doesnt look so straightforward as i'm used to. anything particular here?

The One Button Installer has a simple text interface, no fancy graphics. But it is simple anyway (not beautiful but simple). Read the document files and ask me here or via an Ubuntu Forum message if you wish :-)

1. Create a USB drive with the OBI. The instructions how to do it are in the README.pdf file.

2. Boot from the OBI and use it to make a tarball. It is deliberately made simple and assumes that you have only one partition for the file system and one swap partition. So you make a tarball containlng an image of the file system.

2a. If you wish, exit to the bash shell and rename the tarball [FONT=courier new]**ball.tar.gz**[/FONT] to another name (with the ***mv*** command).

2b. sudo poweroff

3. Boot another computer from the OBI, and use it to install the system from the tarball, that you made in step 2.

3a. sudo poweroff

4. Remove the OBI drive and boot this second computer. It should start running the system, that you ported via the tarball.

---

### Post by vaalir on 2013-09-12
there is no thank you system here? :P you are most helpful sir! making it portable AND installable is super nice :D

ok, while i have someone with some knowledge here..
how can i change my home folder to reflect to another users home folder?

i want user 2 and 3 to have user 1's home folder, if you understand. since i'm syncing with ubuntu one and dropbox, i see no point in having multiples of everything. i use different users for different workflows

changing /etc/passwd only results in me not being able to log in... this perhaps because of config files i guess.

nothing changes when trying to use users-dirs.dirs
edit*
yes it does! sort of.. clicking pictures for instance, in nautilus takes me to where i want to be, but entering a the pictures folder still takes me to that users pictures...

---

### Post by sudodus on 2013-09-13
> **vaalir said:**
> there is no thank you system here? :P you are most helpful sir! making it portable AND installable is super nice :D
 You are welcome :-)> 
ok, while i have someone with some knowledge here..
how can i change my home folder to reflect to another users home folder?

i want user 2 and 3 to have user 1's home folder, if you understand. since i'm syncing with ubuntu one and dropbox, i see no point in having multiples of everything. i use different users for different workflows

changing /etc/passwd only results in me not being able to log in... this perhaps because of config files i guess.

nothing changes when trying to use users-dirs.dirs
edit*
yes it does! sort of.. clicking pictures for instance, in nautilus takes me to where i want to be, but entering a the pictures folder still takes me to that users pictures...

If the three users share the same home folder, they will also share most settings (everything that is stored in the home folder, typically in its hidden files and subdirectories). Then I don't see the benefit of having separate user accounts.

Anyway, I did a quick test with a symbolic link for the home directory and changed some permissions, but it did not work. Maybe someone else can help you.

---

