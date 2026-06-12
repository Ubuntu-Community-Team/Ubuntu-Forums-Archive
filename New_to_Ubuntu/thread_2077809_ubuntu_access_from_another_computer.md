---
title: "ubuntu access from another computer"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by graphicsmanx1 on 2012-10-29
I have a second port on my main workstation and I wanted to access my old rig I switched over to ubuntu but I am unsure on how to connect both computers.  I dont want to have to add the linux box to the workgroup but if I need to I will.  What is the best way to join my workstation and ubuntu station???

---

### Post by Mark Phelps on 2012-10-29
I know you can use Samba from the Linux side to setup and access shared files and folders on a Windows PC -- which you can then access over a local network -- but I've never tried it the other way.

Since Windows can't read Linux filesystems, connecting a network cable from the Windows PC to the Ubuntu PC is not going to accomplish what you want.

---

### Post by kanikilu on 2012-10-29
Can you elaborate on what you are trying to do? "join my workstation and ubuntu station" could mean a few things. Are you trying to share files? Remote desktop? Something else??

If it's just filesharing you are trying to accomplish, samba is your best bet, and here is a how-to I came across in a search:

[http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/](http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/)

That should cover sharing to/from both computers.

If you just need to access the Ubuntu machine from Windows (and not the other way around), then the easiest option would probably be to install the *openssh-server* package and then connect to it from Windows with a sFTP client such as Filezilla.

If it's remote desktop from Windows to Ubuntu that you are after, there are a number of options (Google is your friend), but the ones I've used are VNC and FreeNX:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by graphicsmanx1 on 2012-10-29
I am starting to use ubuntu and learn how to code with bash to complete simple tasks on situations that can prove timely but repetitive.  I tried going the VirtualBox route but its proving very annoying with issues so Im thinking of taking an old mobo and cpu rig that has a 160gb HDD and running ubuntu on it.  I would like to vpn from windows and use it.  Setup I am unsure of.  I did see some tutorials on setting it to a network but Id rather just take my secondary port and run it with my workstation.  I am though very new and eager to learn so ideas and suggestions are great.

EDIT:
If i setup through my switch is easier I would possibly just go that route.

---

### Post by graphicsmanx1 on 2012-10-30
bump

---

### Post by Mark Phelps on 2012-10-30
> **graphicsmanx1 said:**
> ...Id rather just take my secondary port and run it with my workstation.
Post #3 provided you some links -- that you will have to read through.  Since MS Windows ICS does not work with Ubuntu machines, there is a LOT more involved than just connecting the two machines.

>   I am though very new and eager to learn so ideas and suggestions are great.

And ... as said ... you've already received some. If you have trouble understanding what you've read, you need to ask specific questions, not just keep repeating what you want to do.

---

### Post by kanikilu on 2012-10-30
> I would like to vpn from windows and use it. I assume you mean "remote desktop" (sometimes also referred to as "screen sharing")? Since the 2 machines will presumably be on the same network, there is no need to setup a full-blown VPN.

Once you have the Ubuntu computer connected to your home network (either via wireless or wired ethernet), then any combination of Samba, SSH and either VNC or FreeNX (links above) should provide you with pretty much every avenue of "access" you'll need.

If the question is how to *physically* connect the Ubuntu machine to your network, then you'll need to describe your current setup a little clearer. 

How do you connect to the internet? Do you have a router? An older standalone modem? What??

---

### Post by kanikilu on 2012-10-30
Oh, and I'm really struggling to undertand what you mean by this:

> Id rather just take my secondary port and run it with my workstation.

What "secondary port"? What *type* of port is it? If you mean second ethernet port or NIC, as has already been suggested, that's going to be hard to setup that way.

I don't think it's impossible - I'm pretty sure you can use a crossover cable ([http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)), but that may be a little complicated ... check out this thread (post 3 in particular) for some ideas:

[http://ubuntuforums.org/showthread.php?t=1698547](http://ubuntuforums.org/showthread.php?t=1698547)

Someone correct me if I'm wrong, but a router is probably going to be your best (and easiest) option.

---

### Post by Mark Phelps on 2012-10-31
> **kanikilu said:**
>  ... Someone correct me if I'm wrong, but a router is probably going to be your best (and easiest) option.

I've said before that using a CROSSOVER cable, to gain ACCESS to the Ubuntu machine from the Windows machine is NOT going to work -- because the Windows PC will NOT be able to read the Linux filesystem on the Ubuntu machine.

See the link below about using a CROSSOVER cable between Fedora and Windows to share INTERNET access:

[http://www.ehow.com/how_7490589_connect-windows-using-crossover-cable.html]("http://www.ehow.com/how_7490589_connect-windows-using-crossover-cable.html")

This only allows the Ubuntu machine to gain Internet access THROUGH the Windows machine.  It does not allow the Windows machine to access the Ubuntu machine.

---

### Post by kanikilu on 2012-10-31
Couldn't you still connect them, and then use any of the number of the suggestions above (Samba; SSH+sFTP client on Windows; VNC/FreeNX) to do the actual file/screen-sharing? Assuming that's in fact what the OP is trying to accomplish...

Just because Windows can't natively read Linux filesystems shouldn't really matter in that case, right?

---

### Post by graphicsmanx1 on 2012-11-01
well Im up for anything really.  This is a new rig and environment I learning in.  My main goal is to learn bash for processing files and I have a spare rig I wanted to use instead of running VM.  I thought it would be a great time to learn it.  My apologies if it would appear that Im ignoring anyone.  I just want to learn the right way and see how I can do it best.  I thought about VPN into the rig but I have an extra monitor and keyboard but I still need a hot folder on the network to drop items into it.

---

### Post by dannyboy79 on 2012-11-01
> **graphicsmanx1 said:**
> well Im up for anything really.  This is a new rig and environment I learning in.  My main goal is to learn bash for processing files and I have a spare rig I wanted to use instead of running VM.  I thought it would be a great time to learn it.  My apologies if it would appear that Im ignoring anyone.  I just want to learn the right way and see how I can do it best.  I thought about VPN into the rig but I have an extra monitor and keyboard but I still need a hot folder on the network to drop items into it.
so it sounds like you merely want a shared folder that both windows can see as well as ubuntu. Theres many ways to accomplish that as others have pointed out, easiest would be to install SAMBA on ubuntu machine and pick whatever folder you want to share so that windows can then see it, then map that folder to a drive letter in windows.
there's many guides for setting up samba which are within the ubuntuforums.
GOod luck

---

### Post by graphicsmanx1 on 2012-11-01
thanks for the help.  Guess its time for testing and seeing what I can get to work.

---

