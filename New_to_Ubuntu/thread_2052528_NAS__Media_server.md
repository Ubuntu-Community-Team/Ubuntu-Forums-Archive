---
title: "NAS / Media server"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by chadwell on 2012-09-03
Total noob here- I have a spare laptop with 1TB hdd that I want to set up as a home NAS for my photos etc, but also be able to stream video to my PS3.

I tried freeNAS but couldn't get miniDLNA to work and the plugins were confusing.

I have read that Ubuntu would be a good option for this.  Should I run it from a 16GB USB stick - how would I do this?

Can I close the laptop lid and leave this set up and running 24/7?

What do I need to install? Mediatomb / Serviio / Plex/ PS3 media server.

I would want to run SABnzbd also from the NAS.  Could you drop a NZB into a folder and it would download and extract on the NAS.

I want to be able to access the share from windows PCs too.  Does this require anything special to be done?

Thanks for any help/suggestions.

---

### Post by bootedguy on 2012-09-03
Plex is cross-platform and easy to set-up. And, if you have a Roku on your TV, you can view your photos, videos, etc on your TV.

---

### Post by chadwell on 2012-09-03
Thanks - so do you know how to install a persistent copy of Ubuntu onto a usb stick.
I don't even know how to install stuff in Ubuntu - I take it you don't double-click an exe like windows.

I read something about SAMBA - is this something I need to install so I can access my shares from a windows PC and darg and drop files over to it.  I want to map my 1TB HDD as a network drive.

Thanks

---

### Post by Bashing-om on 2012-09-03
chadwell;

  Hi ! welcome to the forum.

Be advised that ubuntu server is an excellent choice, Ready for service instantly upon installations.
  Do a google search on "nas server ubuntu". You will find that there is a huge amount of support for server applications. May take some doing to get it operational with a closed lid situation....others can better advise.
[INDENT]hth <==BDQ

edit: installation=> Download .iso, burn to cd, set bios to boot from cd, insert install cd(called a Live CD), install ..it is that simple// partitioning and set up before hand may be advisable (depending on your needs) ..simple answer/way,=> do a simple install: look at what you have, determine what you would prefer different: and re-install.. (be advised that with ubuntu and GOOD BACK-UPS one can not mess up too bad)

[/INDENT]

---

### Post by chadwell on 2012-09-03
But the server edition does not have a GUI so for a noob like me I'm not sure how I would be able to set it up and configure it, and install software like Plex etc!

Thanks

---

### Post by Paqman on 2012-09-03
> **chadwell said:**
> But the server edition does not have a GUI so for a noob like me I'm not sure how I would be able to set it up and configure it, and install software like Plex etc!

Thanks

It doesn't start with a GUI, but you could add one. Or you could use something like Webmin to administer it remotely through a browser.

To install software in Ubuntu:
[LIST]
[*]On the desktop version: open Ubuntu Software Centre and search, then click install
[*]On the server, type:
```
sudo aptitude
```
then enter your password to get yourself a reasonably friendly command-line package manager
[/LIST]

---

### Post by chadwell on 2012-09-04
So :

1. any ideas how to install and run off a usb stick?  Can you use one of the programs of pendrive linux, but will this be a dedicated install

2. Will this see my 1TB drive?

3. How do I share it across windows and network?

---

### Post by mastablasta on 2012-09-04
> **chadwell said:**
> So :
 
1. any ideas how to install and run off a usb stick? Can you use one of the programs of pendrive linux, but will this be a dedicated install

 
as mentioned before you run install and when you come to where you want to install it you choose USB drive/stick. You need to also put the grub boot manager on it.
 
```
 
sudo apt-get install *programme*

```
enter password. and that's it. its that easy to install in ubuntu CLI.
as mentioned you can add desktop to it but that is a bit unusal for a nas device. if oyu need it use somehting light on resources such as IceWM, jwm or LXDE.
 
it would make more sense to administer it from other maschines via web interface.
 
> 
2. Will this see my 1TB drive?

yes.
>  
3. How do I share it across windows and network?
 
you install samba and configure it (if necessary).
as in 
 
```
 
sudo apt-get install samba

```
afetr that you should be able to see the shares from windows. make sure you are in the same user group.
 
 
 
also since you like GUI and preconfigured stuff you might want to give Openmedia vault a try. it's based on Debian (on which Ubuntu is also based) and preconfigured for NAS.
 
as in ubuntu it's preety easy to add stuff to it.
 
BTW notebook hard disks aren't made for durability. they seem to break even more often that desktop disks.

---

### Post by Paqman on 2012-09-04
> **chadwell said:**
> So :

1. any ideas how to install and run off a usb stick?  Can you use one of the programs of pendrive linux, but will this be a dedicated install


There are instructions for this on the download page.

> 
2. Will this see my 1TB drive?


Yup. Of course.

> 
3. How do I share it across windows and network?

The easiest way to share to Windows machines is to use the Microsoft networking protocol SMB/CIFS. Both Linux and Windows can use it.

You'll need to install [Samba]("https://help.ubuntu.com/community/Samba") on your server. If you've got a GUI you can do this from a right click on the appropriate folder, if you're running a a server then you woudl configure it by [editing the /etc/samba/smb.conf file]("https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html").

---

### Post by chadwell on 2012-09-04
Thank you both - assuming I do not have a cd drive on my laptop - then how do I install to usb>?

Could I have 2 usbs, one a bootable linux drive and use it to install to the other USB>?

---

### Post by nothingspecial on 2012-09-04
1. see here [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

2. Yes

---

### Post by chadwell on 2012-09-04
Thanks I had spent a ot of time setting up FreeNAS and finally got it all working, only to find out that miniDLNA does not auto refresh when new media is added, so you have to restart the plugin - makes no sense to me.

Surely when you add new media you want it to be available immediately for streaming to PS3 whatever.

Hopefully will try Ubuntu - havent decide on which streaming software yet though - Serviio, Meditomb, PS3 media server, Plex etc

Anyone I think I am going to try this guide here:

[http://www.howtoforge.com/the-perfect-media-server-ubuntu-11.10-sabnzbd-sickbeard-couch-potato-headphones-serviio](http://www.howtoforge.com/the-perfect-media-server-ubuntu-11.10-sabnzbd-sickbeard-couch-potato-headphones-serviio)

Finally: Can I remotely maintain Ubuntu desktop, and does this need anything special.  Any sort of web GUI?

---

### Post by Paqman on 2012-09-04
> **chadwell said:**
> 
Finally: Can I remotely maintain Ubuntu desktop, and does this need anything special.  Any sort of web GUI?

You can, but if you're going to be maintaining it remotely there's not much point in running the desktop version. You could use [VNC]("https://help.ubuntu.com/community/VNC") to remote into a desktop, but it would be more efficient to use the server version and a proper server remote admin tool like [Webmin]("http://www.webmin.com/"). Webmin will give you a nice web browser GUI for managing Samba, btw.

---

### Post by chadwell on 2012-09-04
Thanks - I was looking at the server version but I have no idea how to install software like samba, Serviio using it.

Does Webmin allow you to install software, from the repository for example?

---

### Post by Paqman on 2012-09-04
> **chadwell said:**
> Thanks - I was looking at the server version but I have no idea how to install software like samba, Serviio using it.

Does Webmin allow you to install software, from the repository for example?

Yep. However, using apt-get or aptitude (like I suggested above) isn't hard.

From the command line, to install a package (say samba) using apt-get:
```
sudo apt-get install samba
```
or to use aptitude, you can do:
```
sudo aptitude
```
Which then gives you a little interface to search for and install packages.

The only real stumbling block is that you need to know the name of the package you want. The desktop has more user-friendly tools for searching the repos, but tbh you're not likely to be installing or removing much on your server once it's set up, and any guides you follow to set up various things will tell you what you need.

---

### Post by chadwell on 2012-09-04
Thanks for the help here.

Is it easy to share my Ubuntu HDD on the home network?  What would you se to drop in files from windows?  Would you drag and drop from a shared drive - or is there a better way?

Using freenas - when moving video files from within the mapped drive,  I thought because I was moving a folder into another folder on the same HDD on the NAS that it would be quick. It was really slow. Is there a better way to do this?

So just to be clear - I basically have 1 HDD on my NAS - I was dragging a folder into another folder, but doing it from a windows pc.

I just tried deleting 2 of the videos and it is also very slow. Again I am doing this through windows vista mapped drive.

---

### Post by Paqman on 2012-09-04
> **chadwell said:**
> 
Is it easy to share my Ubuntu HDD on the home network?  What would you se to drop in files from windows?  Would you drag and drop from a shared drive - or is there a better way?


A Samba share will work fine for this.

> 
Using freenas - when moving video files from within the mapped drive,  I thought because I was moving a folder into another folder on the same HDD on the NAS that it would be quick. It was really slow. Is there a better way to do this?


If you move the files locally on a Linux machine, it'll be blink-of-an-eye fast as nothing gets copied, the system just updates the location for that file. On Windows and over network protocols it'll stupidly try and copy the whole file to the new location, which can be really slow if it's big.

The fastest thing to do would be log into the other machine and move the files locally from there. From Windows you could use a client like Putty and log in over SSH to use the command line, or again this is something Webmin can do through a browser.

---

### Post by chadwell on 2012-09-04
Thanks for this information, now I know how to move files about within my NAS from another PC.

Would it be quick to FTP  files from my windows PC to the NAS, or is drag and drop fine through the samba mapped drive? Just if I have nearly 1TB worth of photos, videos etc - it will take some time to move.

---

### Post by Paqman on 2012-09-04
Quickest way to move 1TB of data is to take the drive out of the target machine, temporarily put it in the source machine and copy it through the nice fast SATA bus. Going through the network is always going to be slow.

---

### Post by chadwell on 2012-09-04
OK I am installing Ubuntu 64bit version as we speak.

I had 2 USB drives, one empty (FAT32) and the other had the Ubuntu boot Live cd on it.

So I boot into the options screen and choose Install Ubuntu.

I am able to choose "other" where I can select which partition etc.  I choose my Empty USB drive as the target for bootloader from the dropdown.

I also choose the same USB drive for the installation.

But I create a new partition table on it, ext4 with a mount of /.  But it complains about having no swap.

I created a swap **and **an ext4, but it would not let me go forward to install - it was like the install button would not work as if something was missing.

So the only way I could do this was just with an ext4 and no swap.  I was able to continue installation with no swap - Just a full 16gb ext4 - is this a terribly bad idea>?

Any ideas why it would not let me continue when I created both a swap and an ext4 (8GB each in size).  What did I do wrong and what should I have done?

Also when this installs and boots (hopefully) - can I/should I install a swap with gparted>?

---

### Post by chadwell on 2012-09-04
well the install didnt go too well.

It worked, but was incredibly slow to boot - could be the usb drive is on its way out.  Its not the fastest.

So I am installing it on my 1TB HDD - but I forgot to make any partitions!  I just installed UBUNTU on the whole internal harddrive.

Should I have made any partitions or can I just create a folder called "MEDIA" and share it and store and stream my media from there?

If I do need to make a paritition (with gparted) - how much should I make from the 1TB and should it be ext4 or FAT32 or what?

Many Thanks!!

---

### Post by chadwell on 2012-09-04
Well installing to the HDD didnt go so well either - it will now only boot when the USB stick is inserted. No idea what I did wrong - I am pretty sure I installed to the system.
"this is a freenas data disk and cannot boot system. system halted"

Looks like freenas is messing up my HDD - I thought the ubuntu install would delete everything?

If you try to boot without the usb - you get an error saying that it is a data disk and cannot boot.

Edit: I am trying to partition my HDD when reinstalling ubuntu - I have created a swap and a 15GB ext4 "/".  I have no idea if this is right.  The rest of the HDD is "free space" so hopefully it can be used as the NAS share.  I don't mind losing 20GB of the HD space as long as I have the rest.

I am not hopeful I have done this right - I have been searching guides everywhere but can't find anything.

---

### Post by Paqman on 2012-09-04
Ug, sounds like you're having a bit of a nightmare. Stick with it, it sounds like you're on the home stretch! You can't go too far wrong with a nice basic install to a hard drive.

> **chadwell said:**
> Well installing to the HDD didnt go so well either - it will now only boot when the USB stick is inserted. No idea what I did wrong

Sounds like you told it to put the boot loader (Grub) on the USB stick instead of the drive.

> 
Edit: I am trying to partition my HDD when reinstalling ubuntu - I have created a swap and a 15GB ext4 "/".  I have no idea if this is right.

Sounds good.

> 
The rest of the HDD is "free space" so hopefully it can be used as the NAS share.

You'll need to format it as something to use it. You can go back any time and format it as ext4, so don't sweat it. You can use Gparted or Disk Utility to do that.

---

### Post by chadwell on 2012-09-04
Ok looks like I did it ok in the end.

It booted fine so I used Gparted to format the remaining freespace as NTFS - hope this is ok.  I called it NAS.

I installed samba, java through the software manager.

I am trying to share NAS so I can see it on my network on my windows PC.  I can right click on it, go to properties and then share.  Is that the way to do it?

As I rebooted and it did not seem to hold these settings?

I loaded samba and added the NAS drive as I called it.  Gave users permission to access it.  I can see it from Windows but when I try to open it I get access denied?

---

### Post by chadwell on 2012-09-04
Arggh every step there is something!

I can see the folder on my PC but access is denied.

In ubuntu I try right clicking and changing permissions but they do not hold.  If I change a drop down it immediately changes back!  

Do I share using SAMBA OR share by right clicking and choosing sharing options?
How do I allow access from my PC so I can copy over files?

Please help as I am almost finished here :)

---

### Post by chadwell on 2012-09-05
Can anyone help with this? Thx


I have tried 3 different ways to share the drive:
Right click on the drive folder, then sharing options

Using samba gui

Terminal, loading admin-shares.

All with the same results, so is this a permissions issue? 

I have another laptop with ubuntu on it and I just tested and I can access the nas share no problem.

It's just Windows Vista giving me an issue

---

### Post by mastablasta on 2012-09-05
> **chadwell said:**
> Ok looks like I did it ok in the end.
It booted fine so I used Gparted to format the remaining freespace as NTFS - hope this is ok. I called it NAS.

 
No that's actually a bad idea. NTFS is a windows disk format. it will get fragmented in time and become slower. Ext4 won't have much fragmentaiton. in additon it will handle linux file permissions better (user, admin, guest, executable etc.)
 
which brings us to...
 
> **chadwell said:**
> All with the same results, so is this a permissions issue? 
 
I have another laptop with ubuntu on it and I just tested and I can access the nas share no problem.
 
It's just Windows Vista giving me an issue
 
yes it's a permisison issue. Samba GUI gave me nothing but troubles as it's defaults were strange. i configured samba config using text editor. instructions under configuration in terminal: [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
 
however none of this should be necessary in Ubuntu.
 
make sure that user in windows group is also in the same group you shared to. 
 
even if everything is ok in the config file it could happen that windows user wasn't detected or somethig. in short just liek in your case i can see from winxp maschine the samba share but i asks me for password and i can't access it. 
 
sometimes restarting samba helps
```
sudo service smbd restart

```
 
more info on samba...
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
 
as mentioned before i belibve it might be easier for beginners to use a distro that is already preconfigured for NAS such as Openmediavault. using GUI (desktop) install for media server will unnecessary use resources.

---

### Post by chadwell on 2012-09-05
Thanks for your help- since I haven't tried to copy any files over yet I am going to delete the NTFS partition and format it as EXT4.

> make sure that user in windows group is also in the same group you shared to. 

1. I'm not sure I have any users in my windows pc (Administrator??)- but will have to find out, but the group is called WORKGROUP and this is what I have used in SAMBA.
On ubuntu the user is called: chadwell - but its definately not this on my windows PC.  Does that matter?  Do they both have to be the same user?  I will find out on my windows PC by using "whoami" in cmd.

2. Whats the difference between right-clicking on the drive and choosing "sharing options" and by using the Samba GUI - do they both do the same thing?

3. The partition I created is called NAS. It appears in Ubuntu as a mounted drive.  But it also seems to be in /mnt/media.  Which should I share?

---

### Post by chadwell on 2012-09-05
Will have a look at the smb.conf and see if there is anything in there, but if anyone can help in the meantime would be great!

---

### Post by chadwell on 2012-09-05
Ok I formatted as ext4. But my partition owner was root so I couldn't do anything like create folders or share.

I Found some terminal command with chown user:user type of thing, and this worked ok and I could create and share folders.

I could now access folders from my Windows pc.

But I could not create folders from my Windows pc, so I changed the smb.conf to have 775 in a couple of places.

Two problems now exist.

1. If I create a folder in the share using Windows, I cannot access it from ubuntu. It's owner is nobody.

2. If I create a new folder in ubuntu, I can access it from Windows, but it seems to be read only.

I want read and write access to the entire folder structure from both places.  Is this possible?

---

### Post by mastablasta on 2012-09-07
> **chadwell said:**
>  
Two problems now exist.
 
1. If I create a folder in the share using Windows, I cannot access it from ubuntu. It's owner is nobody.

well, you can access it running nautilus with gksu, but that's not how it should be. what group has access to the folder? if you check it's propperties from Ubuntu.... Ubuntu user needs to be part of same group to be able to access it. 
 
btw if you have FTP installed then you can change permissions form window susing a FTP client such as filezilla.
>  
2. If I create a new folder in ubuntu, I can access it from Windows, but it seems to be read only.

 
same problem as above. users in the share workgroup need to be in same group on the OS to be able to access folder and have read& write privileges.
 
i am not sure what the default group is in windows but i believe in my case it was MSHOME (WinXP). if it's still like that, then linux users also have to be part of MSHOME group. if it's workgroup then workgroup.
 
as i get it there are two groups, one is share group and one is usert group in system (which has certain access). i could be wrong here, but that's how i interpreted it.

---

### Post by kentish on 2012-10-17
Hi chadwell

Bit late coming to this thread but have you considered Open Media Vault - [http://www.openmediavault.org/]("http://www.openmediavault.org/")

I've installed it on an old IDE harddrive as it uses all the space on the drive, it could also be install on a compact flash card or USB pen which may suit a laptop install.

Supports SAMBA, NFS by default so easy to share to windows and linux machines. Nice web UI and a few plug ins including miniDLNA

As for the SABNZB install, quite easy over SSH and then try using [NZBd Status/]("https://addons.mozilla.org/en-US/firefox/addon/nzbdstatus/")

Can't comment on running off a laptop as I've never tried.


Kentish

---

