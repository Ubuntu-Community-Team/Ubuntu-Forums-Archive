---
title: "Cant play / move / delete files. I/O error when transferring files."
date: 2013-10-20
forum: New to Ubuntu
---

### Post by GGMkrAR on 2013-10-20
Hi,

I am new to Ubuntu, i installed Ubuntu 13.04 and XBMC with the help of a lot of googling and reading guides. Please note all references to moving / accessing data are done via a win7 machine over the network, i havent logged into the ubuntu user on the machine due to not having a mouse/kb setup for it at this point.

I have a quad core 775 machine setup with a small hdd that has ubuntu and xbmc on it, i then have 2 Seagate 2TB NAS drives for storing data. The intention is to use the box as a file server to share all the content across my home network while using XBMC as a media player front end. Hopefully that is enough background info.

Now all has been good for the last 3 weeks since setting it up. Until yesterday, while using XBMC to play media files the video files would randomly freeze and it would exit back to the folder in which the file was contained, if i tried to open the file again it would play the file up until roughly that point again then do the same thing. Any other files would not would not be able to be opened either. Restarting the device fixed it temporarily before it would repeat the process.

Accessing the shared hard drives from my Windows 7 machine and from the WD TV Live would result in the same problems. Two things had changed before the problem started, a tv show was added to the hard drive that XBMC was having scraping problems with (doubt this will be the cause) and i added fusion to xbmc as a means to utilise the 'install from zip file' option, this has since been removed.

When trying to copy the tv show folder that was recently added (just to make sure this is not the issue) i get this error 
> error 0x8007045D the request could not be performed because of an I/O device error

I am a bit stumped on this one, as it seems what i have searched is all windows based solutions but xbmc and the wd tv live are having access issues. The drives are brand new and purchased for the linux box.

---

### Post by TheFu on 2013-10-20
Could be anything.
Loose cable, failing PSU. 
Failing HDDs
broken ethernet port, cable, switch, router, router port.
Corrupt programs.

What do the log files show?
From windows, you can remote into the xbmc machine using putty, if you installed and enabled ssh-server.

---

### Post by GGMkrAR on 2013-10-20
Thanks for the reply.

I logged into the default ubuntu user on the box and tried to play some of the files on the machine itself to rule out network issues. It comes up with a read error when i try to play any of the files.

Interestingly though, i have 2 - 2tb drives in the box, 1 for TV shows and 1 for movies/music/photos etc. I can play files on the 2nd drive but anything on the first just gets the read error. 

Is there a seagate diagnostic tool for linux? Will be might annoyed if a 3 week old drive is already failing.

---

### Post by nerdtron on 2013-10-20
> **GGMkrAR said:**
> 

Interestingly though, i have 2 - 2tb drives in the box, 1 for TV shows and 1 for movies/music/photos etc. I can play files on the 2nd drive but anything on the first just gets the read error. 


Looks like a failing hard drive to me. Have you tried rebooting? Does the filesystem check automatically start after the reboot?

---

### Post by GGMkrAR on 2013-10-20
rebooted multiple times. files are accessible for a short period of time after a reboot. basically after a reboot i can play a video file, how far it actually gets through the file seems pretty random.

I might try transferring the files to the 2nd hard drive and then running a diagnostic on my win 7 machine if there is no tool available for linux

---

### Post by TheFu on 2013-10-21
A failing HDD happening sooner than later DOES happen. I'd try swapping the SATA cable and plugging into a different SATA port on the MB first. Could just be a bad cable.

Linux has **badblocks** as a tool. Or you could buy **spinrite**-HDD vendors seem to trust that when it comes to returns too. I suspect any HDD vendor tools run under an MS-Dos environment, so a boot floppy/flash/CD will be created, but I haven't used those in years.

---

### Post by GGMkrAR on 2013-10-21
> **TheFu said:**
> A failing HDD happening sooner than later DOES happen. I'd try swapping the SATA cable and plugging into a different SATA port on the MB first. Could just be a bad cable.

Linux has **badblocks** as a tool. Or you could buy **spinrite**-HDD vendors seem to trust that when it comes to returns too. I suspect any HDD vendor tools run under an MS-Dos environment, so a boot floppy/flash/CD will be created, but I haven't used those in years.

First plan was to swap the sata cable and port and then look into running a diagnostic tool.

Well aware that an HDD failing can happen early on, just very frustrated as i have had 2 WD drives die on me in the last 2 months, one of them was a replacement for a failed drive. So i am a little bit over dealing with failing drives atm.

---

