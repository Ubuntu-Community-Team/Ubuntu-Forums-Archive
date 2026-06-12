---
title: "USB Thunderbird between Lubuntu &amp; Win7 - Password Probs"
date: 2019-10-21
forum: New to Ubuntu
---

### Post by nginmu on 2019-10-21
I'm trying to set up Thunderbird such that I can run it on either my Windows 7 desktop or my Lubuntu laptop, using a USB stick to harbour & carry the profile between machines. Ultimate aim being that I can carry my whole profile around on a keyring and use it on any Windows / Linux machine that has, or I have the ability to install, Thunderbird on.

My USB stick is formatted as FAT32

I'm starting Thunderbird on each machine as follows:

Windows command line:
"C:\Program Files (x86)\Mozilla Thunderbird\thunderbird.exe" -profile "J:\EMAIL\testprofile"

Linux terminal:
thunderbird -profile /media/my-home-directory/usbstick-label/EMAIL/testprofile

Everything seems to work fine except for the fact that whilst on Windows, the profile just loads and works totally reliably straightaway, on Lubuntu any attempt to check or send new email results in a request to enter the POP/SMTP password. When the password is provided, checking the 'use password manager' checkbox never results in the password being saved, and 9 times out of 10 an error is raised that email checking or sending failed because 'the password could not be obtained' or similar. Also, attempts to set a master password fail.

Wondering where I might be going wrong, or else is trying to use Firefox in this way inadvisable?

---

### Post by TheFu on 2019-10-21
I don't do this.

I think Unix systems want POSIX file systems - those that support proper file permissions. FAT32 does not.

You can use a / instead of \ on Windows.  It works perfectly and all cross-platform programmers know this.  Try it:
 "C:/Program Files (x86)/Mozilla Thunderbird/thunderbird.exe" -profile "J:/EMAIL/testprofile"
I don't use Thunderbird on Windows, so don't know what the "EMAIL" part you show means.  / can be used anywhere, in any program, unless the programmer goes out of their way to test for issues in the path.  The Windows OS doesn't care, of that I'm 100% positive.

BTW, /media/{userid}/{usbstick-label}/{EMAIL}/testprofile is something you can control on systems that you control, but if you use this on someone else's system, then the userid will be different anyway.

My Thunderbird profile uses a random directory where you show "EMAIL". It is a security thing that Thunderbird has used for a long time.  ~/.thunderbird/438fx5md.default/  is an example.

---

### Post by nginmu on 2019-10-21
Yes I do only plan on using this on systems I control. I've caused confusion - where I show "EMAIL" - that's just a folder name I'm using on the USB stick to contain the actual profile folder, which is still named e.g. /438fx5md.default/ as per your example

Weird thing is, in the main, both Windows & Lubuntu seem to be reading the profile just fine in 99% of respects, it's just Lubuntu's Thunderbird seems to be stumbling over passwords after loading the profile initially quite smoothly.

Tried copying the entire profile off from the USB stick & into a new directory, off my home directory, on the lubuntu machine. Am still finding the same issue, so making me think it isn't so much the USB stick or it's filesystem, as something with the files or permissions within the copied profile.

Since it's the Windows OS that seems to care less than Lubuntu, am wondering what will happen if, instead of creating the profile initially on Windows, I first create it on Lubuntu & then try loading it up on the Windows machine. Do a few send & receives & then try carting the profile back off Windows, once again onto the Lubuntu machine. That might also cover the / versus \ issue..

Wondering if the different line ending formats between Win & Unix might also be affecting things. Could I use some form of something like tofrodos [https://www.thefreecountry.com/tofrodos/index.shtml](https://www.thefreecountry.com/tofrodos/index.shtml) [http://manpages.ubuntu.com/manpages/trusty/man1/fromdos.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/fromdos.1.html) in a scripted manner to automatically flip the entire profile between line ending formats? Run one command & have it recursively search through the entire profile & convert only the appropriate files.. it's a vague idea

Maybe something like [https://superuser.com/questions/757081/how-do-i-convert-all-files-in-a-folder-to-a-different-line-ending-on-windows](https://superuser.com/questions/757081/how-do-i-convert-all-files-in-a-folder-to-a-different-line-ending-on-windows)

It'd just be really nice to be able to work email seamlessly on both machines, without getting all mixed up beween message stores, by keeping all the messages on the one single stick & just plugging it into whatever I happen to be using at the time..

Is there a better choice for a filesystem that both Win & Lubuntu can work with.. FAT16? NTFS, something else..?

---

### Post by TheFu on 2019-10-21
Mozilla files are cross-platform.  I've moved between Linux, Windows, OSX without issues.  I don't do it daily, only when a new machine shows up.  Since most addons are javascript, those are cross-platform too. Compiled program addons/plugins are NOT cross-platform.
EOL doesn't matter. Good thought, but nope.

I've also moved between 32-bit and 64-bit Linux systems in the last 2 months - no issues.

The way you've described it, I'm thinking there is a difference between the character set being used on the systems. Perhaps? That's my best guess at this point.

I don't consider Windows or OSX or Android or iOS secure enough to access email.  My email servers are all self-hosted and use IMAP. If I must have access, I can boot from a light Linux with a browser, connect with an ssh tunnel and use a SOCKS proxy into the web interface.  The email servers are only available via SMTPS over the internet. All other access has to either use a VPN or SOCKS proxy to get into the network first.  I used to see tens of thousands of hack attempts daily against my servers. So much easier to just require a VPN for client-side access.  

Some people call me paranoid.

---

### Post by nginmu on 2019-10-21
I started from scratch and created a new profile on the USB stick on lubuntu, using thunderbird's command line options for specifying profile location. Tested sending & receiving on lubuntu, all good. Took out USB key with linux-created profile, plugged it into Windows machine, Windows was happy to launch it from "C:\Program Files (x86)\Mozilla Thunderbird\thunderbird.exe" -profile "J:/PortaMail/00001.default".

Everything seems to have been all good, since.

Although, when initially plugging in the USB key on Windows, Windows did complain that it needed "scanning and fixing", whereupon it found 4 small file fragments it placed into a 'FOUND' directory. Appeared to be 2 very small chunks of email content and 2 files which simply both contained the text "version 1".

I might not have gone to the full trouble of explicitly unmounting the USB key every single time I removed it from the lubuntu machine. I think I might have just yanked it out once or twice without deliberately unmounting first, maybe erroneously thinking there was no need to make provision for 'safe removal' on linux like there is on Windows

---

### Post by TheFu on 2019-10-21
If you pull storage out from Linux, expect data loss and/or corruption.
For portable storage, I use autofs to automatically mount and umount USB storage, but we can't just pull it out when we like. It has to be unused and already umount'd first.  I think if you shutdown thunderbird 5 minutes before you need to leave, autofs will safely umount the storage.  

Honestly, if I were trying to do what you are, I'd just have a script that I ran to mount, run thunderbird, then umount the storage after thunderbird was closed.

---

