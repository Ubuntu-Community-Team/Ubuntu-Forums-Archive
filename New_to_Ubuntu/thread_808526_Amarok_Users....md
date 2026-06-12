---
title: "Amarok Users..."
date: 2008-05-26
forum: New to Ubuntu
---

### Post by arcarsenal on 2008-05-26
So I've been a Windows user my entire life. Just switched over to Ubuntu yesterday and I've had a pretty smooth transition thus far (still trying to get my fonts 100% right.. I've got them looking much better now, though). 

Anyway... one of the most important things for me is being able to listen to my music and connect my iPod. I've been using iTunes for a few years now but obviously I can no longer do that with Ubuntu. I installed Amarok and while I'd still much rather have iTunes, it's not all that bad. 

Here is where the problem came in, though. I snagged all of my music and dropped it into my Amarok library fairly easily (approx 7,500 songs). I eliminated all of the tabs I didn't need (directory, year, etc...) kind of tweaked it all to my liking, adjusted the EQ... all that stuff. 

I re-booted later on, opened up Amarok and all the songs in the library were a light grey. None of them would play, they all said something to the degree of "Local File not Found". Not only that, but all the tabs and EQ were back to default. I had to clear out the entire library and re-load all of it and then tweak everything once again. I haven't restarted the system or the program since, but I have a feeling it's going to happen again. Can anyone explain why the music files no longer play after a re-boot and why none of my changes are saved? I've got to figure this out before it drives me nuts. 

Sorry this is so long.. any help would be very much appreciated! :)

---

### Post by kk0sse54 on 2008-05-26
If amarok doesn't work out for you you can always try out Exaile which is pretty much just a clone of Amarok except it fits into GNOME a bit better. For me it was also a lot more stable amarok froze and crashed on me constantly but Exaile so far for me has been rock solid.

---

### Post by civillian on 2008-05-26
you might not have the right codecs for playing mp3 and wma files installed. try playing the media files usig the default 'movie player' and if that wont play thrm it will bring up a dialogue box that will try and find the right audio codecs for you.

---

### Post by Paqman on 2008-05-26
Where are you storing your music? On another partition? A network drive? The most likely reason it would fail to find your files is that something is stopping it from following the path.

---

### Post by Mike'sHardLinux on 2008-05-26
I've never had any problems with Amarok. It is my favorite Linux music player. It is much better than any other player/library software AFAIC.

Anyway, when you say you snagged all of you music and dropped it into your Amarok library, what exactly do you mean? How did you do it? Did you literally copy all the folders/files to your local hard drive? Did you drag and drop in Amarok from your iPod to Collection?

---

### Post by arcarsenal on 2008-05-26
> **C!V!NT said:**
> you might not have the right codecs for playing mp3 and wma files installed. try playing the media files usig the default 'movie player' and if that wont play thrm it will bring up a dialogue box that will try and find the right audio codecs for you.

I did that initially and installed the codecs. Like I said, the music plays fine now, but when I re-boot, that's when they no longer work.

---

### Post by arcarsenal on 2008-05-26
> **Mike'sHardLinux said:**
> I've never had any problems with Amarok. It is my favorite Linux music player. It is much better than any other player/library software AFAIC.

Anyway, when you say you snagged all of you music and dropped it into your Amarok library, what exactly do you mean? How did you do it? Did you literally copy all the folders/files to your local hard drive? Did you drag and drop in Amarok from your iPod to Collection?

Basically what I did was I went into my Windows HD which is called "70 GB Media" under the "Places" tab, went into the folder where all my music was located and then dragged and dropped it all into Amarok. Could that be the problem? 

Also.. anyone know why the settings I change in Amarok (changing the tabs, eq, etc...) keep resetting to default?

---

### Post by Paqman on 2008-05-26
> **arcarsenal said:**
> Basically what I did was I went into my Windows HD which is called "70 GB Media" under the "Places" tab, went into the folder where all my music was located and then dragged and dropped it all into Amarok. Could that be the problem? 


Dunno. I've never tried to do that, so who knows if it would work. Normally I set up my library in the configuration menu. Just set the path to your music library and let it update.

---

### Post by bwhite82 on 2008-05-26
The problem is that Amarok cannot locate your music because your Windows partition is not mounted when you first login (ie no HD icon on desktop). You need to edit your /etc/fstab to make it auto-mount upon login and you won't have this problem anymore.

---

### Post by arcarsenal on 2008-05-26
> **Soldierboy said:**
> The problem is that Amarok cannot locate your music because your Windows partition is not mounted when you first login (ie no HD icon on desktop). You need to edit your /etc/fstab to make it auto-mount upon login and you won't have this problem anymore.

Ah, I see! Alright, so right now I have the HD icon in the upper left-hand corner. I closed out of Amarok and re-opened it and everything was there the way it should be. Let me see if I can figure out how to auto-mount it and then I think I should be good to go.

---

### Post by adobrakic on 2008-05-26
I had this problem also. My music is on my windows, but im running linux. 
All i do is go to Places and scroll down to Presario (my c: on windows), and if i hover over it, it says "Mount Presario", and when I click that my music in amarok loads normally and works fine.

By the way, soldierboy, how do you make it autoomount, it'd be nice not to have to do it everytime i turn on my computer.

---

### Post by arcarsenal on 2008-05-26
soldierboy...

Can you kind of just give me a quick run-through on how to make it so that drive auto-mounts? I'm totally new to Linux so I guess as plain as you could possibly make it would be the best. 

Also, is auto-mounting now going to make any sort of difference if I plan on re-sizing my partitions later on? 

Thanks so much. :)

---

### Post by bwhite82 on 2008-05-26
[http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU](http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU)

---

### Post by Paqman on 2008-05-26
Psychocats is always a good place to look for things like that:

[How to mount a Windows partition](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by arcarsenal on 2008-05-26
Am I going to have to unmount it first? Or can I just skip that step and follow the rest to get it to auto-mount?

---

### Post by bwhite82 on 2008-05-26
No need to unmount first.

---

### Post by arcarsenal on 2008-05-26
Hmm...

When I tried to enter the sudo fdisk -l command, the terminal came up, I entered my password and then the window just disappeared. Now when I try it again, I don't even get the password prompt, the window appears for a split second and then disappears again. Anyone know why this might be happening?

---

### Post by bwhite82 on 2008-05-26
What window? That command should be run from a terminal.

---

### Post by arcarsenal on 2008-05-26
> **Soldierboy said:**
> What window? That command should be run from a terminal.

I was hitting alt+F2, pasting the command and then checking off "run from terminal". The terminal came up, prompted me for my password.. I entered it and then the terminal disappeared. Am I doing something wrong?

---

### Post by bwhite82 on 2008-05-26
> **arcarsenal said:**
> I was hitting alt+F2, pasting the command and then checking off "run from terminal". The terminal came up, prompted me for my password.. I entered it and then the terminal disappeared. Am I doing something wrong?

Yes. Open the terminal Applications>Accessories>Terminal. Then enter the command in the terminal. Running things w/ ALT+F2 is usually limited to GTK applications (ie visual apps).

---

### Post by arcarsenal on 2008-05-26
Hmm.. using the link Pacman posted, it says entering that command should give me this: 

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1911 15350076 7 HPFS/NTFS
/dev/hda2 1912 19457 140938245 5 Extended
/dev/hda5 1912 14716 102856131 83 Linux
/dev/hda6 14717 17278 20579233+ 83 Linux
/dev/hda7 17279 17404 1012063+ 82 Linux swap / Solaris
/dev/hda8 17405 19457 16490691 83 Linux

But what I got, was this: 

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Which obviously looks nothing like that. I'm kind of lost here.

---

### Post by bwhite82 on 2008-05-26
It's an l and not a 1 (el and not one).

---

### Post by arcarsenal on 2008-05-26
Well that makes a difference.

---

### Post by arcarsenal on 2008-05-26
Ack.. this is ridiculously confusing to me. 

I wish there was a way to simply opt to auto mount the drive instead of having to waddle through all of these terminal commands that are making no sense.

---

### Post by bwhite82 on 2008-05-26
> **arcarsenal said:**
> Ack.. this is ridiculously confusing to me. 

I wish there was a way to simply opt to auto mount the drive instead of having to waddle through all of these terminal commands that are making no sense.

Ack, my apologies. I'm used to doing things the old way. There is a new NTFS Config tool in the 'System Tools' menu.

---

### Post by arcarsenal on 2008-05-26
> **Soldierboy said:**
> Ack, my apologies. I'm used to doing things the old way. There is a new NTFS Config tool in the 'System Tools' menu.

That would help a lot.. if I could find it. I'm not seeing it anywhere under the "System" tab under preferences or administration. 

Thanks again for all the help, by the way. :)

---

### Post by bwhite82 on 2008-05-26
It should be under: Applications>System Tools>NTFS Configuration Tool
If it isn't install it via Synaptic, the package name is: ntfs-config

---

### Post by arcarsenal on 2008-05-26
> **Soldierboy said:**
> It should be under: Applications>System Tools>NTFS Configuration Tool
If it isn't install it via Synaptic, the package name is: ntfs-config

Ok, so I went to that and I get a window with 2 unchecked boxes. 

One is next to "Enable write support for internal device"

The other is next to "Enable write support for external device"

I can't check or uncheck the first... only enable write support for external device. And under that It has About, Cancel and OK buttons. 

Is this what I should be looking at in order to auto mount the drive?

---

### Post by bwhite82 on 2008-05-26
Wow man, I'm sorry things have been so frustrating for you. Make sure you also have the following package installed via Synaptic:

ntfs-3g

Then reboot and see if you can check the box for the other option.

EDIT: You want to make sure they're both CHECKED.

---

### Post by arcarsenal on 2008-05-27
> **Soldierboy said:**
> Wow man, I'm sorry things have been so frustrating for you. Make sure you also have the following package installed via Synaptic:

ntfs-3g

Then reboot and see if you can check the box for the other option.

EDIT: You want to make sure they're both CHECKED.

Rebooted and still the same thing. Still can't check the first box. I did notice, however, that if I mount the drive right when I boot up (which only takes 2 seconds) BEFORE I open Amarok, then Amarok loads all the songs properly. It would be nice to just have it auto-mount, but if it'll work this way, too.. it's not such a big deal. Not really sure why it's not working, though.

---

### Post by forestpixie on 2008-05-27
Firstly can you run 2 quick commands in terminal - I know, I know, but it's quickest and easiest way to get an error message if there is one and to get information, when I've finished I'll tell you what you've done.

```
sudo apt-get install ntfs-3g ntfs-config
```

It should say that both are installed

Can you post the output you get from this command here it will tell us what is being mounted at boot

```
cat /etc/fstab
```

Now if when you try to run the GUI tool the boxes are enabled you should have access to the drives when you boot, but if it's not working we need to know before you try and access the files in amarok, which is the reason to have the fstab - we can see what is going on.

Now - so you have some idea what you've done -

sudo apt-get install packages
 tels the system that you want to use apt to install (apt-get install) as root (sudo, without root rights you won't install anything) a package. 

Apt-get, aptitude and add/remove and synaptic - the last 2 being GUI frontends access the repositories which you have set up to install from - similar to installing from an .exe that you have got from bilbo on the net somewhere the difference being that the sources are checked.

Fstab is an important file - it tells the system which partitions you want to have mounted when you boot, without this file then you will not be able to access, withouit the terminal, files on your system.

---

### Post by forestpixie on 2008-05-27
Ok - hopefully you've taken a deep breath and done the two commands as I've asked - have a look at the lines that you have there

do any look at all asimilar to this 

> UUID=1408F4B94DD0B409 /media/sda6 [COLOR="Red"]ntfs-3g[/COLOR] defaults,locale=en_US.UTF-8 0 1 In particular is the bit in the middle saying ntfs-3g 

I had this a while back with another problem - it should actually say _ntfs_

If that is the case you can backup and open the file for editing - these commands will backup the file and then open in it a text editor for you

```
sudo cp /etc/fstab /etc/fstab.2808
```
copies the file to a new filename - just in case

You will need your normal password to edit the file if necessary

```
gksudo gedit /etc/fstab
```

where the file has ntfs-3g change to read ntfs, then save file, reboot and hopefully you have the drives mounted.

[COLOR="#ff0000"]This is only necessary if you have lines which say ntfs-3g, if you don't you have no need to follow this howto - but I'm off to bed shortly[/COLOR]

---

### Post by arcarsenal on 2008-05-27
> **forestpixie said:**
> Firstly can you run 2 quick commands in terminal - I know, I know, but it's quickest and easiest way to get an error message if there is one and to get information, when I've finished I'll tell you what you've done.

```
sudo apt-get install ntfs-3g ntfs-config
```

It should say that both are installed

Can you post the output you get from this command here it will tell us what is being mounted at boot

```
cat /etc/fstab
```

Now if when you try to run the GUI tool the boxes are enabled you should have access to the drives when you boot, but if it's not working we need to know before you try and access the files in amarok, which is the reason to have the fstab - we can see what is going on.

Now - so you have some idea what you've done -

sudo apt-get install packages
 tels the system that you want to use apt to install (apt-get install) as root (sudo, without root rights you won't install anything) a package. 

Apt-get, aptitude and add/remove and synaptic - the last 2 being GUI frontends access the repositories which you have set up to install from - similar to installing from an .exe that you have got from bilbo on the net somewhere the difference being that the sources are checked.

Fstab is an important file - it tells the system which partitions you want to have mounted when you boot, without this file then you will not be able to access, withouit the terminal, files on your system.

Alright, to start... the 2nd command line you asked me to post gave me this: 

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=46704370-5b62-47a0-9908-94d0377f8b02 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=365d7c31-4d54-4f7f-914c-a95d8347b7b2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by arcarsenal on 2008-05-27
Ok, and the first command gave me this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
ntfs-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

I don't see anything resembling the line you were mentioning I don't think? Hmm.

---

### Post by arcarsenal on 2008-05-27
Other problem now... 

2 times in a row I restarted and when I loaded Amarok and went to play a song, the window dimmed and the program froze. 

Man, I never would have envisioned it being such a pain in the *** to load a library of mp3's and listen to music!

---

### Post by forestpixie on 2008-05-28
Ok - I thought that you'd given us your fdisk - but I realise now you haven't. If the ntfs config tool is not working we can do it manually, but we need the result of this

```
sudo fdisk -l
```

I get a freeze sometimes, a pain but hey...

---

