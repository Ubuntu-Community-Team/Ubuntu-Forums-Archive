---
title: "Open files 12.04"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by evdama on 2012-08-10
How do I get applications such as VLC or audacity to load files from my windows server?
In Windows they will have My Network Places listed  in the 'Open File..' menus.

Ubuntu 12.04 is fully installed and knows about the server,can browse the network from the Home folder, and has printed a test page on the printer attached to it.

Is there a way without having to type gobbledeygook (this is why windows wins every time..:(.)

---

### Post by llamabr on 2012-08-10
Probably you won't have to type gobbledygook (note: not the official nomenclature).  But if you tell is exactly what you're trying to do, we can probably help.

If you have programs installed, and running in windows, even over a shared partition, those programs will probably not run in linux.  You must install the native linux version of those programs.

For example, to run vlc, you should do:

```
sudo apt-get install vlc
```

and then type your password.  Then, open a terminal, and type the following gobbledygook:

```
vlc
```

Please report any errors.

---

### Post by mastablasta on 2012-08-11
> **evdama said:**
> How do I get applications such as VLC or audacity to load files from my windows server?


you need to have Samba installed first then the "places" should be shown in network.
make sure you are in the same workgroup as windows server.

[https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html)

someitmes samba needs to be restarted after boot to recognise the windows server.

> **evdama said:**
> 
Is there a way without having to type gobbledeygook (this is why windows wins every time..:sad:.)

sorry, no Linux wins here as you don't need to type anything since you can copy paste the command line into terminal. another thing is it can be done in GUi but instructions are porvided in command line since same commands work in all GUI (KDE, GNOME, XFCE, LXDE, IceWM, Openbox, E17...).

---

### Post by Paqman on 2012-08-11
> **evdama said:**
> How do I get applications such as VLC or audacity to load files from my windows server?


Easiest thing to do is set the shares from that server up so that they are mounted automatically at boot. That way your machine sees them as local files.

Your windows shares will be being shared over the Windows networking protocol, which is called SMB/CIFS. If it's capable of using the Linuxy protocol called NFS then you should probably use that, as I find it's a lot quicker than SMB.

You don't need all of the SAMBA server to mount an SMB/CIFS share, just the client part: [smbfs]("apt:smbfs").

With that installed, all you need to do is create some folders as mount points and add an entry to /etc/fstab for each share you want to mount. 

[Full instructions here]("http://ubuntuforums.org/showthread.php?t=288534").

That link looks like loads of work but essentially the only bits you need are:
[LIST=1]
[*]Install smbfs
[*]Create mount points
[*]Add lines to /etc/fstab
[*]Set up credentials
[*]sudo mount -a
[/LIST]

I believe there's a GUI tool called [gigolo]("apt:gigolo") that you can use to do this, but I've never used it so don't know if it's any good.

---

### Post by evdama on 2012-08-11
Thanks guys -

The applicatons are linux versions automatically  installed from ubuntu software centre

The linux machine can see and access the files and the printer on the windows shares perfectly when I go to the Home folder and "Browse Network.
The windows server can also see the linux machine wen I "View Workgroup Computers"

But 
when using ,say VLC , I go to open one of those files.
Any file on the local machine is visible from the list of places that VLC gives me to select from.
My problem is that the list does not include the other computers on the network.
On a Windows machine this would be called My Network Places.

I need that option in the  Linux applications
Something I can just click on and make the problem go away.....

I normally use an nlit-ed corporate version of XP 
It just asks me which partition to use, then performs a complete unattended install which is fully functional out of the box -windows wins.:(
That said
Im actually very  impressed as this is the first distro I have tried in 10 years that  has got close to ticking all the boxes without having to mess about -this is the only way linux can gain ground 
I will have to try to do  the workaround -my puny brain just cries wtf when it is presented with fstab etc

---

### Post by daimaru on 2012-08-11
have you tried VLC's "Open Network Stream" ctrl+n ? maybe that plays them

---

### Post by evdama on 2012-08-11
I personally could use that option however the idea behind using Ubuntu is to wean the rest of the tribe (who have a fraction of my tolerance level) off windows-this issue is the main obstacle.

---

