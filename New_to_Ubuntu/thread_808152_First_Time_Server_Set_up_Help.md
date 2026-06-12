---
title: "First Time Server Set up Help"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by jcr1 on 2008-05-26
Hello all,

Well I am still pretty fresh to the Linux world, but loving every minute of it. Wish I had more time to learn more and more...

Still I am at the inevitable point where I want to set up a home server. Now I am not sure how to do this, I get the general idea, but to be specific, its  setting it up to get the most benefit out of it that needs clarifying.

Simply I want to use an old pc, with a large HDD to basically be my store for all my data. So I can have all music, videos, documents stored on it, and let other machines on the network access these files remotely. So i don't need to store music, for example, locally on my laptop. I'm sure you all know what I am after.

Question is, do I need to install Unbuntu Server ed. on the server or is this unnecesary for a simple home server? I don't want to host websites or anything on it, just want it to be a central storage place.

I would like to set something up that enables anyone on my network to access music and play it through speakers attached by (long) wires. So that is really just remote access to the server to get music playing, not necessarily streaming as it would be just through speakers actually attached to the server. This would preferably be just through a simple web interface so you didn't need specific software installed to play music (just a web browser and network access).

Hope this isn't a too open ended question.

Thanks in advance!

---

### Post by Hospadar on 2008-05-26
Howdy!

This is really not so hard a thing to do, I used a regular old desktop ubuntu installation for my server.  The reason I did is because some applications (deluge, the bittorrent client I currently use) don't have a command-line only mode (i.e. they require gnome to be running).  Probably in retrospect, you'd be better off installing xubuntu, since it gives you the GUI, but with less overhead than gnome, but that's an unimportant detail.  You can really install any version of ubuntu you want.

Let's talk setup:

First off, while installing, I would be sure to use separate / (root) and /home (home directory) partitions.  I would make your / about 5Gb, and your /home the rest of the drive.  This will give you plenty of space for any applications you want to install, without hogging too much of your hard drive.  The advantage of seperate partitions here is that if you want to re-install ubuntu (if you fudge things up or want to try a different flavor) you can do it without touching any of your data.  For the initial installation, go to the manual partitioner, and set things up.  

First delete any partitions on the drive (Assuming there is no data there that you need to save), then create a swap (logical) partition that is about 25-50% of your ram (If you have a gig of ram, 256-512 MB swap partition).
Next make your root partition, it should be about 5 GB.  Choose ext3 for the type, and make sure it is primary (not logical).  Set the mount point to /
Now make your home partition take up the remaining space on the drive, format it to ext3 as well, also primary.  mount point will be /home

Now if you ever go to re-install, just go into the manual partitioner, find your partitions, and set the mount points to / and /home, check "format" for the root drive, and make sure format is unchecked for your home drive.
Hope that makes sense.

Now software:
Most important I suspect will be filesharing.  You want to be able to store and access files on the machine.  I think the best way to do this is with ssh.  It's very secure and very easy to set up.  All you have to do to set it up is, on a command line,  "sudo apt-get install ssh"
Now, from any other linux machine, you can get access to the machine by doing "ssh -Y <your username on the server>@<the ip address of your server>" (the -Y allows you to open up graphical applications) then type in your usual password.  This will give you remote access to control the machine and run applications.  If you are on a linux machine, try typing in some application you'd like to open up which is installed on your server, and it will open up remote style (The application runs on the server, but displays on your machine). A good example here would be opening up a music player (like rythmbox).  It would display on your remote machine, but the sound would come out of the server.
If you are on a windows machine, you can use ssh software like puTTY to get command line access, and a windows xserver like xming to allow yourself to open up graphical apps.

As for file access, you can use filezilla from any windows or linux machine to do file transfer.  If you want to mount something on the server into your normal (linux) filesystem so that any application can use files on your server as if they were on your remote machine, you can use sshfs, it's a command line tool to mount sftp (ssh) folders locally.  This would allow you also to stream movies, music, open documents on the server without having to transfer back and forth, etc.  The same kind of functionality is possible on windows if you use something like sftpdrive (it's not free, it costs like 10 bucks, but it works well).

If you want to access your machine globally (I assume you use a router at home) you can forward port 22 on your router to the server.  Exactly how you do this varies from router to router, so you'll have to consult your router's manual.  Then you can use some service like whatismyip.com to figure out your global IP address, then ssh to your machine just like above, but with the global address.

Another option for file access is samba, which will show up like a windows network share, it's not too hard to set up, and easier to access from windows machines, but it's not globally accessible like ssh, and doesn't provide any kind of remote control or applications, so I generally use ssh instead.

PM me if I totally lost you, I always forget to check up on my threads =)

Hope this helps!

---

### Post by jcr1 on 2008-05-26
Brilliant reply! Thank you very much Hospadar, thats just the sort of information I needed! My laptop is setup with seperate partitions like you describe, so I am up to speed on that aspect.

To eleborate slightly... the server pc...I think it currently has a small 8GB HDD which I would use to install say xubuntu. Then I have a second HDD (250GB) which is currently in a NAS box, which I might just remove from the box and just stick in the pc.

Would the /home directory basically be my storage space for everything? Can this be setup on a seperate disk?

I shall get on to trying it out soon and then I am sure I will have plenty more questions...

Thanks again.

---

