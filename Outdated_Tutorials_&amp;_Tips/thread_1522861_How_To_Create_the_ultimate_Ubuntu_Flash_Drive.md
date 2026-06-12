---
title: "How To: Create the ultimate Ubuntu Flash Drive"
date: 2010-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by max.goedjen on 2010-07-02
Hey Guys,

I've spent a while perfecting my ideal bootable Ubuntu flash drive setup. I've received a few inquiries about how I have mine set up, so I figured I'd post a guide detailing the process I used.

Just a couple notes for reference. For my flash drive, I'm using a Cruzer Contour 8GB flash drive, mainly for speed.I 'm also using an OS X machine with an Ubuntu Virtual Machine running in VMWare Fusion (though there's no reason you couldn't do the same thing in Ubuntu and Virtualbox. I'm setting it up in a virtual machine as it makes it much easier to update and make changes to your bootable linux install than having to do it all inside the virtual machine (you can still do this on the go, but I find for maintenance and tweaks, it's easier to do in a VM).

So: without further ado, the tutorial:

**_Step 1: Setup your VM/Ubuntu install_**
Create a virtual machine with your Ubuntu mix of choice. I'm using the standard desktop 10.4, but if you wanted to use the netbook mix or XUbuntu or the like, that should work fine as well. Alternately, if you'd just like a mobile version of your current Ubuntu setup, you could just skip the virtual machine and work in your production environment. I like to keep a lighter setup for my flash drive, so I'm gonna use the VM.

**_Step 2: Customize your install_**
Do things like set backgrounds, install programs, themes, etc now.

I have my flash drive set up to operate on insecure networks, so I establish an SSH tunnel and use a SOCKS proxy to pipe all of my network traffic though that tunnel. This is also nice for bypassing web filters and the like. You don't have to do this part, but in my experience, it's convenient to have.
**_Step 2.1:_**
To do this: go to System>Preferences>Startup Applications, and add a startup item that runs the command
```
ssh -D LOCALPORT -Nf ADDRESS_TO_YOUR_SSH_SERVER
```
replacing LOCALPORT and ADDRESS_TO_YOUR_SSH_SERVER with the appropriate values. (Obviously, you're going to need to have your ssh server set up, but if you have a ubuntu box at home, it's pretty trivial to do, and there's plenty of other tutorials that can do that better than I.)
**_Step 2.2:_**
Go to System>Preferences>Network Proxy, and select Manual proxy configuration. Type in localhost for socks host, and whatever value you entered for LOCALPORT into the port field.Hit "Apply System-Wide."

**_Step 3: Image your system_**
Ok, now that you've got your virtualized Ubuntu install to how you like it, it's time to get it onto your flash drive. To do this, we're going to use a tool called Resmastersys, which basically images the operating system you're running it from. Installation instructions are located here ([http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)).
**_Step 3.1:_**
Open up Remastersys (System>Admistration>Remastersys Backup). If you've run it before, you should hit "Clean" first, this'll clear out any old isos or working files that Remastersys created last time. You can customize Remastersys to exclude certain directories (for example, I exclude my downloads folder and my desktop), this is under the "Modify" option.
**_Step 3.2_**
Ok, time to do the imaging. In Remastersys, hit "Backup," and go grab a cup of coffee, because this might take an hour or two.

**_Step 4: Prep your flash drive_**
Ok, this is another thing that took me forever to get right. Most of us need to use our flash drives with Windows machines on a semi-frequent basis. Windows, obviously, can't read the files you store in your bootable flash drive install. To complicate matters, all versions of Windows XP and below can only recognize the first partition of the flash drive, and will completely ignore any partitions beyond the first. So how do we get around this and allow Windows to view data on your flash drive? We make the first partition for data, and the 2nd for Ubuntu to boot off of. You can divvy up your flash drive as you like in GParted (I have my flash drive (8GB) split up roughly 6GB data/2GB Ubuntu (my actual Ubuntu data only needs about 1GB of space, but I leave extra room for persistence so it can breathe and do things like update itself,etc)).
So, what's the end effect of this? We have a flash drive with 2 partitions. Windows only sees the first one, which is used for data, but most PCs are able to boot into the 2nd partition, which is our Ubuntu install.

**_Step 5: Install Ubuntu on the 2nd partition of your drive._**
Just what is says. Go to System>Administration>Startup Disk Creator. Select the image you created with Remastersys (by default, it's located in /home/remastersys/remastersys/). For the destination drive, select the 2nd partition of your disk. Hit go.

**_Step 6: You're done._**
Enjoy your new flash drive linux install. You can store files so that both Ubuntu and WIndows can see them, operate securely on insecure networks, easily bypass web filters, and have your own customized work environment only a reboot away.

If anyone needs any assistance, I'll help to the best of my abilities here.

---

### Post by Duncan J Murray on 2011-07-25
Thanks!  I was just googling around for this, after struggling with my usb drive...  This is very useful.

All best,

Duncan

---

### Post by Duncan J Murray on 2011-07-30
Ran into a few problems with the above advice - the biggest difficulty was trying to get the .iso image off the VM!  I did manage it, and tried writing it to a usb drive, but although the .iso worked when run in a VM, it wouldn't boot from the memory stick.  I would have persisted further, but realised what I actually wanted was this:

[http://askubuntu.com/questions/32484/how-to-boot-from-ubuntu-live-usb-with-try-ubuntu-directly](http://askubuntu.com/questions/32484/how-to-boot-from-ubuntu-live-usb-with-try-ubuntu-directly)

And installed ubuntu from a memory stick onto an 8GB cruzer flashdrive.  I don't need to use it to install ubuntu onto computers - I just need it to run my set-up with the software I need.  I partitioned it 1GB/7GB, the former as a fat partition to function as a flash-drive, and a way to get things on and off the ubuntu installation.

D

---

