---
title: "Ubuntu Server"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by mskchn on 2013-03-13
Hi- I had installed Ubuntu server in one of my harddrive and was working fine and was playing around but unfortunately today morning i was not able to boot the system properly. I have some important data on the harddrive which i need to retrieve, I tried connecting the HDD to another ubuntu server and was unsucessful in mounting it.
Please help me with step by step instructions to retrieve the datas.
I would appreciate an early reply.

MSK

---

### Post by RoosterHam on 2013-03-13
have you got a Linux live image? If you are only interested in  retrieving the data you could boot from an live image, or follow the  below steps from the system you tried to connect the drive to. If you  would like to boot up the broken system, we'll need more information  such as what you did before it stopped booting and any error messages.

Either boot the system from a live image or plug the drive into the other ubuntu server host.
From  there use "fdisk -l" to show what partitions fdisk can see on which  disks. If adding drive to working ubuntu server it helps if you know  what drives are mounted on the live system, if you don't know what disks  are already there and which is the added one, use "fdisk -l" or "mount"  before plugging the recovering drive in.

When you have  determined what partitions are your recovery target, mount it manually,  perhaps create a subdirectory in /mnt/ first.

Can you discribe how your attempt to mount failed last time?

---

### Post by mskchn on 2013-03-13
Thanks Rooster, I was trying to install the desktop environment for ubuntu ([http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)) but unfortunately it stopped halfway. So when i rebooted the machine after checking the networking it just goes blank.

I will also provide the details what is the error i found while i was trying to mount the drive.

Thanks for your time.

Thanks
MSK

---

### Post by RoosterHam on 2013-03-13
Okay, so the guide you provided a link to describes how to install ubuntu-desktop and webmin...

Please don't take this as being rude, but do you really need the desktop? Webmin is a pretty good tool for a server, but what do you expect the desktop to do for you on a server? Webmin allows configuring the system graphically from any workstation in your network, and logging into your machine via ssh allows you to configure every single aspect of the server. To do anything a little more than completely basic on your server via it's own desktop, you'll likely need to start up a terminal emulator (putting you into the same environment that you'd have without a desktop at all) or a browser window to the webmin page on localhost (putting you in the same environment webmin allows you to access from a dedicated desktop machine on your network).

But if that is what you require, you may need to do some tinkering to get it working.

Now as you boot (before the pretty ubuntu picture with the 'configuring network' writing) hit the escape key and watch the messages that should be scrolling by. take note of where it hangs. when it stops, try Ctl+Alt+F2 and see if you are dumped on the cli.

If the errors just say things about xorg/x11 or you get a login console by this, do a reverse of what you did to install the desktop (ie "sudo apt-get remove --purge blahblahblah)

If you don't get any of these, you may need to use the alternate installer to repair a broken system... let us know how you go, and provide as much detail as possible.

---

