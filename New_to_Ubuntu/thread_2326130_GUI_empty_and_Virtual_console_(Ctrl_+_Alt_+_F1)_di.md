---
title: "GUI empty and Virtual console (Ctrl + Alt + F1) displaying too large for my screen."
date: 2016-05-28
forum: New to Ubuntu
---

### Post by SageAbkatsor on 2016-05-28
Edit: Disregard all [COLOR=#d3d3d3]grey[/COLOR] text!

Hello, I've just built my first computer and want to use Ubuntu for the operating system. This has been an overwhelming process for me, but my hardware seems to be running well.

ASUS Z170-A
Intel i5 6600k
16 gb corsair ddr4
ASUS GeForce GTX970 Turbo
HDMI cable
Sony Bravia 1080p 42"
Ubuntu 16.04 LTS on an SSD 

Installed the Ubuntu 16.04 LTS ISO on a flash drive and installed it on my SSD. Install went well. I can boot Ubuntu and log in. I can get my grub menu on boot. And I can get into and out of my virtual console with Ctrl alt f1 from the desktop.

I am having some issues with displaying [COLOR=#d3d3d3]both[/COLOR] the primary desktop GUI [COLOR=#d3d3d3]and the main virtual console (Ctrl alt f1).[/COLOR]

My main problem is that I cannot get my main desktop GUI working at all. It is completely empty. Everything looks good all the way through the login process, but once I'm logged in I just have a mouse cursor, a background, and if I bring up a terminal or something then I have that blinking on and off. If I do have an error message displayed on a window on the desktop, or if I am able to open a windowed terminal, or rather anything that is displayed just blinks on and off and is just short of entirely unusable. This led me towards learning more about the command line and grub menu so I could do some digging and make changes if necessary, but I am very new and really don't know what I'm doing. I've learned quite a bit and can navigate through directories and such, but everything I'm interested in looking at to try to figure this out seems to elude me.

So now I spend a lot of time in the terminal, looking up forum posts from people who have similar issues and trying the advice I find therein. To no avail. [COLOR=#d3d3d3]Now, you can imagine how annoying that might be considering that my virtual console displays too large so I cannot read the beginning 4-5 characters of each line. I think I've reached the point where I need outside help.  If I ls a directory that has a lot of things in it, it also pushes the active command line down below the bottom edge of the screen. In the end, I don't have a working GUI, and can barely even navigate via terminal because I can't see what I'm doing or the returns I get unless I hit enter a few times to move the return up a few places, but even then I'm still missing the front 5characters off the left edge of the screen.[/COLOR]

I am not sure if it is just a driver problem with my graphics card or the TV or what. [COLOR=#d3d3d3]From the looks of it, this may not be an Ubuntu Linux issue but moreso a system issue, as writing this post gave me the idea to check the bios, and it looks like the display gets cut off in bios too. Unless it is drivers I need.[/COLOR] I don't even fully understand how drivers work... [COLOR=#d3d3d3]That said, it doesn't seem like the bios gets very much cut off, but then again the whole thing probably has a border around the UEFI, so it might just be cutting that off without cutting off any real info.[/COLOR]

Please help me troubleshoot these issues. I just want to get a baseline operating system running before I really have to delve into the nitty gritty command line stuff.
[SIZE=5]
Edit: [COLOR=#d3d3d3]Greyed[/COLOR] text indicates solved problem[/SIZE]

---

### Post by SageAbkatsor on 2016-05-28
Embarrisingly enough, the TV settings just needed to be adjusted to get everything to fit on screen. So that's one problem down...

Now the trick is to get my desktop GUI working properly.

---

