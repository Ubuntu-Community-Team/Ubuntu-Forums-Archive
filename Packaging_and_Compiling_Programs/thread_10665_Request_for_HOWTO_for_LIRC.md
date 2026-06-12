---
title: "Request for HOWTO for LIRC"
date: 2005-01-10
forum: Packaging and Compiling Programs
---

### Post by ceekay on 2005-01-10
I am using Ubuntu to run a MythTV setup on a ShuttlePC, and I would really like to get the remote on my Hauppage TV Card to work, but I cannot for the life of me figure out how to get it to work with Unbuntu. 

It would be nice if I could just install lirc and have it take care of the kernel modules itself. I am a gentoo user normally, but using Unbuntu I set up MythTV in less than 10 hours (maybe you have to be a gentoo user to appreciate this  :o  ) I would normally just recompile the kernel with appropriate modules, but I am unfamiliar with how the .deb system etc. works. 

Has anyone gotten lirc to work with ubuntu that could post a quick howto?

---

### Post by jdusablon on 2005-02-04
I also would like to know this. Not so much for MythTV, but even just to control XMMS and/or Mplayer. Anyone?

---

### Post by fido on 2005-03-20
[QUOTE=jdusablon]I also would like to know this. Not so much for MythTV, but even just to control XMMS and/or Mplayer. Anyone?[/QUOTE]
 I have been trying to get it work for days following other tutorials and what not it seems as if the lirc package for ubuntu isn't working correctly. A ubuntu specific HOWTO would be awesome.

---

### Post by wilho on 2005-09-27
Definately good issue for good HOWTO, but here's something to start with:
[http://ubuntuforums.org/showthread.php?t=30612&highlight=lirc](http://ubuntuforums.org/showthread.php?t=30612&highlight=lirc)

I haven't found instructions to make it work with mythtv, but I'm just about to starting to try now so... :)

---

### Post by dhtseany on 2008-09-27
Hey,
I found this post on Google and I'd like to bump it.

I'm trying to find some sort of how-to guide myself so I can use a remote simply to map it's IR transmissions to mimic keyboard input.

I figured out I could use...
```
apt-get install lirc
```
...to use apt to install it. However, passed this point I have no idea what I'm doing or where to start.

I went to [www.lirc.org](www.lirc.org) but that really didn't get me anywhere. All it seemed to really offer was source downloads and remote config file codes?

If I could get some info on how to actually use this thing I'd be the first to jump on creating a GUI project that would be much easier to use. (And trust me, I think this is something that would be a big step towards making a Ubuntu Media Center Edition or something like that!)

[SIZE="4"]
So yeah, I second that motion for someone who knows what they're doing to please help us out and give us some sort of how-to guide!:)[/SIZE]

Peace
Sean

---

### Post by AndrewWalker on 2008-11-10
Install lirc via a shell, it's a lot easier, and do this

sudo apt-get install lirc

it should give you a menu of remotes to pick from. If not, try 

sudo dpkg-reconfigure lirc

and you definitely should get the menu. The menu is misleading, the remote option refers to not only your remote but also the way the ir receiver is connected. For example, if you select hauppauge hvr1300 it configures the remote control and the ir receiver that plugs in the card, if you try and use a different ir receiver such as a usb device it won't work. The transmitter option in the menu is irrelevant for most people, it's for sending ir signals rather than recieving them. Most ir devices receive only so this option is useless for them.
Once lirc is installed, run in a shell 

irw

and the command prompt should disappear and the shell appear to be frozen. Press a few buttons. If you press a few buttons on your remote you should get a response echoed in the shell. If not, something didn't work. You can try again by running 

sudo dpkg-reconfigure lirc 

if it went wrong. To get mythtv ir working it's quite easy once lirc is installed. Just install this

sudo apt-get install mythbuntu-lirc-generator 

and it configures all the key bindings but don't do it until lirc is running correctly. If you're using a laptop with ir built in it is a lot more tricky and I won't go into it here. You can configure it by hand by editing the following files

/etc/lirc/hardware.conf
/etc/lirc/lircd.conf

the remote drivers they refer to are in /usr/share/lirc/remotes

After editing or altering anything don't forget you need to restart the lirc daemon

sudo /etc/init.d/lirc restart

Hope this helps and if you do have trouble don't think it's just you, in my experience lirc is a dog and needs some serious work to get it up to scratch!

---

### Post by sephirothsigep on 2009-03-10
alright a good howto on LIRC. no problem 
**[https://help.ubuntu.com/community/InstallLirc/Gutsy.]("https://help.ubuntu.com/community/InstallLirc/Gutsy.") **
their is not one for intrepid ibex but the gutsy one should work just fine. also if you have an older install of ubuntu just follow this link. their are links for each of the different ubuntu versions going back to dapper.

one last note. try taking a look at **[https://help.ubuntu.com/community/TitleIndex ]("https://help.ubuntu.com/community/TitleIndex")**if you ever have a problem installing something. their is just a tone of howtos from samba swat mythtv lirc.
I would say that the first link that i gave would be the best but if that does not work give one of these two a try 
**[http://www.mythtv.org/wiki/Ubuntu_lirc_install]("http://www.mythtv.org/wiki/Ubuntu_lirc_install")**
**[https://wiki.ubuntu.com/LircHowto]("https://wiki.ubuntu.com/LircHowto")**

---

### Post by dentaku65 on 2009-03-14
After you have installed lirc, you can try this raw test to test the remote control:
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=4810578&postcount=13](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=4810578&postcount=13)

---

