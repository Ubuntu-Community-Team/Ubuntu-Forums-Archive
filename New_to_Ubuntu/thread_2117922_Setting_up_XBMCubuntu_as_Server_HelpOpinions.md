---
title: "Setting up XBMCubuntu as Server* Help/Opinions"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by TruckNorris on 2013-02-19
Hello all, this is my first post on this forum and first server build in general. To be short and sweet I've been researching on what to install on my current setup and have a few questions as to what would work best.

Here is what I want to do:

1) Use server as HTPC on my main tv
2) Stream video and transcode to PS3
3) Connect to Windows PC for file sharing
4) Remote desktop connection to set things up, etc.

Here is what I have come up with:

1) Install XBMCubuntu as OS
2) Install PS3 Media Server in background for streaming/transcoding
3) Link to windows file share (sambia? not sure)
4) Figure out how to remotely connect. lol

Basically I am looking for criticism, opinions, etc on whether or not this will work. I'm completely new to Linux but there seems to be a lot of support out there and i'm willing to put in the time.

Your help will be greatly appreciated before I take the plunge. Right now nothing is installed on the server, it is freshly built.

Build:
Pentium G860
Gigabyte 1155 GA-B75M-HD-3
4GB Ram
60GB SSD (for OS)
2 x 2TB Seagate Barracuda drives

---

### Post by TruckNorris on 2013-02-23
So I've installed XBMCbuntu Eden and updated it to Frodo as there is an issue with installing the Frodo version on Sandy Bridge CPU's. So i'm up and running.

What is the best way to remotely connect FROM a vista pc, to the xbmcbuntu server?

---

### Post by TruckNorris on 2013-02-26
Putty and X11VNC are working well for me. I may switch from XBMCbuntu to a full OS such as ubuntu or linux mint. From what I've read they may be easier to edit and modify as I'm not using XBMC primarily. The server side of things in XBMCbuntu are annoying the hell out of me. For each problem I solve a few more arise.... such is the way of linux I gather. lol

I partitioned and mounted 2 x 2TB drives using Gparted and was able to map to them using my windows pc. Great. When the server is shut down and restarts. Samba doesn't automatically start, the drives don't mount because Gparted isn't open. Mapped network drives fail. Everything works if I putty, x11vnc and start both, but that is annoying and the whole point of the server is not not have to leave my desktop on all the time to access it and change settings.

So... tried mounting the drives within the terminal using UUID's in /fstab. Failed miserably the first time.

UUID=41c22818-fbad-4da6-8196-c816df0b7aa8  /media/Data      ntfs    defaults,errors=remount-ro 0       1

Then tried:

UUID=41c22818-fbad-4da6-8196-c816df0b7aa8  /media/Data    ntfs    errors=remount-ro 0       1

The OS was able to boot, the drives come up with an error (I forget now of course) in file manager. And the network locations in the pc pull up one error, the other drive shows up as the 60gb SSD which is wierd.

So unless someone has a solution to this I'm probably going to install ubuntu tonight and then Putty/x11vnc, then figure out the best way to Auto-mount the two HardDrives. 

ANY help would be great!

---

### Post by windscape on 2013-02-26
Hi,

I recommend installing a different distribution such as regular Ubuntu. XMBCbuntu is designed to run XBMC easily, but it probably isn't as easy to modify and maintain as regular Ubuntu.

---

### Post by TruckNorris on 2013-02-26
Thanks for the reply. I am going to install Ubuntu and go from there over the next few days and see where I get to before harassing the forum community again.

The problems could be: I'm a noob, changing to much in XBMCbuntu, and using tutorials for full Ubuntu, etc. If i'm lucky i'll be able to solve my own problems, the amount of guides/forums/how-to's for linux is incredible. It gives me hope that one day I will be able to use this paperweight to watch movies. lol

---

### Post by TruckNorris on 2013-02-27
Installed Ubuntu. I cannot believe how simple it is to use compared to XBMCbuntu. Its ridiculous, there i was in the terminal messing around and hoping my lines were correct when Ubuntu does most things in the GUI and terminal files such as fstab are editable as a seperate file! It's great, especially for someone newer and the forum support is incredible. I guess its good to know the terminal process as well as the more involved you become the more you will edit within it.

---

### Post by audiomick on 2013-02-27
> **TruckNorris said:**
>  I guess its good to know the terminal process as well as the more involved you become the more you will edit within it.

Yep. You don't have to force it. The knowledge will come of it's own accord with time, but you can also spend as much effort as you feel like learning about it. I tend to do things with a GUI for preference, but there are a few commands that I use, and the number is increasing all the time.

---

