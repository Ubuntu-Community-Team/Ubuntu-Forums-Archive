---
title: "HOWTO: Get Starcraft / Broodwar (or other games) to work without CD drive via wine."
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by the_it on 2007-05-22
**What happened:**
In the advent of the starcraft 2 announcement from blizzard, I wanted to relive my starcraft days.
So I got my old starcraft cd, and, hearing that it worked flawlessly on wine, installed it on my brother's
desktop.

**The Tiny Quirk:**
I don't want to have to eject my CD every time I run starcraft or broodwars.

**The Tiny Quirk 2:**
My hands are too lazy to leave the keyboard, and I want a text-based shortcut to start starcraft.

**The solution:**
I created an image of my Starcraft CDs on my own computer, and wrote a tiny script that mounted
and unmounted the isos when I needed them.

The advantage to this is over nocd patches, my game remains 100% pure, so I can run patched updates from blizzard.  And of course, I get to keep my game music with me all the time.

The disadvantage is that I use up extra space to store images of my starcraft and broodwars cds.

This short and simple technique should also be applicable to a number of other games that require you to keep your cd in the drive.

This tip was written on a system running feisty fawn amd64, but should be applicable to other ubuntus in general.

===

**1) CREATING THE IMAGE**
Using your favorite CD burning tool, create an iso image of your game cds.  On gnome, I use gnomebaker.  On KDE, there's k3b.  You could also generate a cd image from windows using Nero or whatever tool you are comfortable with.

*Using gnomebaker*
```
sudo aptitude install gnomebaker
```
With gnomebaker, navigate to Tools->Copy Data CD->Only Create image
set the filename of the image to SomeFileName.iso; insert your game cd and press start.  You should have a copy of CD when you finish.

*Using k3b*
```
sudo aptitude install k3b
```
With k3b , navigate to Tools->Copy CD...->Options.
Under options, you should see a group of checkboxes called Settings.
Select Only create image.
Then move to the "Image" tab and give your image a filename of SomeFileName.iso.

For the purposes of Starcraft, I made the images StarCraft.iso and BroodWar.iso.

*Previously made images*
If you've previously created an image file under windows, they may be written in the .bin/.cue format.  This isn't the format we want, because .bin/.cue doesn't natively mount under Linux.  Right now you'll have to patch your kernel with some extra stuff to do that and I didn't want to think about all of it.

Instead we should just convert the .bin image to an iso.  The program bchunk is great for that.

Install bchunk:
```
sudo aptitude install bchunk
```

according to the manual page:
> bchunk [-v] [-p] [-r] [-w] [-s] <image.bin> <image.cue> <basename>
bchunk  converts  a CD image in a ".bin / .cue" format (sometimes ".raw / .cue") to a set of .iso and .cdr tracks.

To convert an image called Starcraft.bin / Starcraft.cue into Starcraft.iso, run the following command

```
bchunk Starcraft.bin Starcraft.cue Starcraft
```
You will probably get a file called Starcraft01.iso.  Rename it to whatever you want.
```
mv Starcraft01.iso Starcraft.iso
```

For starcraft, you will probably need one image for starcraft, and one for broodwars.

**2) TELL YOUR SYSTEM WHERE THE IMAGES ARE**
Next, I placed my isos in a convenient directory where the system can access them.  In my case, I made a directory called /home/roms which is readable to all users.  You could also make a directory under /usr/share/roms or wherever.  Let's make that directory.

```
sudo mkdir /home/roms
sudo chgrp users /home/roms
sudo chmod g+swx /home/roms
```

Now when you look at the permissions of /home/roms, you will see a directory that is writeable to everybody in the "users" group.  You can selet a different group if you want

```
$ ls -ld /home/roms
drwxrwsr-x 5 root users 4096 2007-05-22 21:21 /home/roms/
```

that way, anyone in your family can make a cd copy of whatever game they wish and write it to the /home/roms folder.  Of course, if you are the sole user of the computer, or if you would like to be the only one to manage your games, you don't need to run the chgrp and chmod commands anymore.

Next, tell your system where to find the roms and how to mount them automatically.  Add the following lines to your fstab.
```
/home/roms/StarCraft.iso /media/cdrom iso9660 loop,noauto,users 0 0
/home/roms/BroodWar.iso /media/cdrom iso9660 loop,noauto,users 0 0
```

Notice that the game cds have the 'loop' option, which is needed to mount images.  It has 'noauto' so that the drive is not mounted on every restart.  It also has the 'users' option, which allows everyone to mount/unmount it when they play their games.

**3) WRITING A STARTUP SCRIPT**
Every time I install a program using wine, I write a small startup script to handle starting it up via command line.  I don't like my fingers to leave the keyboard, and I find it very convenient to have an easy shortcut to start my favorite programs when I already have terminal on (which is quite often).

Copy the script you need to a text file and save it.

For programs THAT DON'T NEED CDs MOUNTED, the script is this simple.
```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/KeyNote
wine keynote.exe
```

in my script, I change the working directory to that of the program being run, since some windows programs are very picky about their startup directory.  If you know your program isn't like that, you can make it shorter.
```
#!/bin/bash
wine ~/.wine/drive_c/Program\ Files/KeyNote/keynote.exe
```

For programs THAT NEED THE CD MOUNTED (like Starcraft or Broodwar), the script has something extra
```
#!/bin/bash

#umount the cdrom
umount /cdrom

#mount StarCraft
mount /home/roms/StarCraft.iso

#wine StarCraft
cd ~/.wine/drive_c/Program\ Files/Starcraft/
wine StarCraft.exe

#unmount cdrom when done
umount /cdrom
```

My broodwar script is exactly the same, except that the cd mounted is different.
```
#!/bin/bash

#umount the cdrom
umount /cdrom

#mount StarCraft
mount /home/roms/BroodWar.iso

#wine StarCraft
cd ~/.wine/drive_c/Program\ Files/Starcraft/
wine StarCraft.exe

#unmount cdrom when done
umount /cdrom
```

Save the starcraft script to a file called starcraft, and the broodwar script to a file called broodwar.  Then make the files executable.
```
chmod a+x starcraft broodwar
```

Finally, move the scripts to your /usr/local/bin directory so that they will be in the default path of everyone.
```
sudo mv starcraft broodwar /usr/local/bin
```

From now on, when you type starcraft or broodwar from the command line, the correct CD image is mounted and the game is launched.  Upon closing the game, the CD image is unmounted, and you get access to whatever CD was in your drive beforehand.

---

### Post by Robert98374 on 2007-05-24
Hey i am trying to make it run in a window, i went on the Winehq IRC channel and they said to add  ¨wine explorer /desktop=foo,800x600 StarCraft.exe¨ instead of ¨wine ./StarCraft.exe¨
any suggestions because this just completly restarts Gnome....

---

### Post by the_it on 2007-05-25
Could you tell me what ubuntu and wine version you have?  It seems to start okay on mine.
I'm using feisty 64bit with wine wine-0.9.37.

To get your wine version, type wine --version.

---

### Post by Enverex on 2007-05-25
> **Robert98374 said:**
> Hey i am trying to make it run in a window, i went on the Winehq IRC channel and they said to add  ¨wine explorer /desktop=foo,800x600 StarCraft.exe¨ instead of ¨wine ./StarCraft.exe¨
any suggestions because this just completly restarts Gnome....

The reason this happens 90% of the time is because of broken graphics drivers. If that's the case then run "glxinfo" to check.

the_it: Stuff should be run through Wine as "wine thing.exe" rather than "wine ./thing.exe". It's not Linux syntax.

---

### Post by Hatrist on 2007-05-25
Thanks for the script, works perfectly here. :)

---

### Post by the_it on 2007-05-25
> **Enverex said:**
> The reason this happens 90% of the time is because of broken graphics drivers. If that's the case then run "glxinfo" to check.

the_it: Stuff should be run through Wine as "wine thing.exe" rather than "wine ./thing.exe". It's not Linux syntax.
Actually ./thing.exe works, and it is Linux syntax in that I am specifying a complete relative path.

There is a very rare case that your program name will be the same as the name of another program in your windows path, and if you cd'd to the wrong path debugging could be problematic and the problem could be avoided by *shoots self* okay that IS too esoteric.

with or without the leading ./, the script should work fine, and I didn't really bother checking it for nonproblems.

:D

---

### Post by Enverex on 2007-05-25
> **the_it said:**
> Actually ./thing.exe works, and it is Linux syntax in that I am specifying a complete relative path.

There is a very rare case that your program name will be the same as the name of another program in your windows path, and if you cd'd to the wrong path debugging could be problematic and the problem could be avoided by *shoots self* okay that IS too esoteric.

with or without the leading ./, the script should work fine, and I didn't really bother checking it for nonproblems.

:D

That's not the point. Wine doesn't run things in your Linux path anyway. Wine isn't meant to be run with "./". Sure it may work, lots of things work in Wine that shouldn't, are unsupported or just flat out lucky to work. It still shouldn't be done and by putting it in how-to's you get other people into bad habits, so please don't do it.

---

### Post by the_it on 2007-05-25
Yes sir! :D

although I was referring to the windows (wine) path (drive_c/windows/ drive_c/windows/system32/), not the linux path.

---

### Post by Enverex on 2007-05-25
There are two (and only two) safe ways.

Direct: wine blah.exe 
(blah.exe is case sensitive even if the app may seem to work with the wrong case or missing extension, you MUST chdir into the folder where the exe is first)

Full Windows path: wine "C:\Games\Blah\blah.exe"
(the path in this case is NOT case sensitive at all)

Hope that clears stuff up.

---

### Post by Robert98374 on 2007-05-26
> **the_it said:**
> Could you tell me what ubuntu and wine version you have?  It seems to start okay on mine.
I'm using feisty 64bit with wine wine-0.9.37.

To get your wine version, type wine --version.

I am using wine 0.9.37 and using regular feisty (i run a P3 1ghz) if that answers your question

---

### Post by mmendez on 2007-05-26
Thanks for the howto I am having a bit of a problem with this though. When I copied your shell script for starcraft and ran it I would get a weird reaction. I can see that the cd mounts just find and then i assume it proceeds to start starcraft. But then the weird thing is that before starcraft starts up the cd is unmounted and a few second later I get a pop-up saying to insert the starcraft disc. When I comment out the umont /cdrom starcraft works just fine as you would guess. Any idea what the problem could be?

I truly have no problem keeping it this way and then opening up a terminal and unmounting the cd but as you mentioned earlier these tiny quirks have a way of messing with a person.

Thanks

---

### Post by the_it on 2007-05-27
To Robert:
Like Enverex said, it might be problem with the graphics driver, since you are already using the same version of wine as mine.  I didn't do any weird wine configs on my end and the window mode works fine with me, so I can't reproduce your error either.  I am running on an intel 945g integrated graphics card, you?

To mendez:
That also happened to me on diablo 2 (although in the end i used a nocd patch on it, but not because the cd wasn't mounted, but because of some copy protection scheme).  I think the problem is that wine somehow returns control to the shell before the program exits.  In that case, I'll have to replace the umount /cdrom part with a background process that waits for your wine to die.  I'll have to look it up, I'm actually barely passable at scripting ;p

By the way, you don't have to command line to unmount the cdrom, since I added a 'users' option in the fstab part.  You should be able to just right click on the cdrom icon on the desktop and umount it from there.

---

### Post by Robert98374 on 2007-05-28
hestly i have no idea what graphics card i am using or the chipset, all i know is that its onboard so i assume its Intel so i am not too sure after that :-)

---

### Post by the_it on 2007-05-28
> **Robert98374 said:**
> hestly i have no idea what graphics card i am using or the chipset, all i know is that its onboard so i assume its Intel so i am not too sure after that :-)

to check which graphics card you have, you can use the lspci command from the pciutils package, or you can go to System->Preferences->Hardware Information from the menu.

---

### Post by Robert98374 on 2007-05-29
82815 CGC [Chipset Graphics Controller] if that sounds about right?

---

### Post by lospo on 2007-06-24
No, it won't work!

I really execute every step of the tutorial, but:

when i launch starcraft from shell i can see only a blank screen with no audio.
System is freeze, i can't do anything, i cant restart xserver, i can't login to tty2 and the numlock led  doesn't work: ONLY HARD RESET (push th button) work.

I really want to play it on wine !!

My system:

[PHP]00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
[/PHP]

AMD 3000+ Single Core
512Mb ram
Ubuntu feisty 7.04
NVidia driver just upgraded 100.x.x

Thank you to anyone who want to reply.
I'm crying.

---

### Post by Enverex on 2007-06-24
Enable Virtual Desktop in winecfg and try again, that should let you at least see what is going on.

Are your video-drivers installed properly? (does "glxinfo | grep -i render" say Yes?).

---

### Post by lospo on 2007-06-24
I can't believe...
Now it works... in a virtual desktop...
I have imported EnableOpenGLDDraw.reg and enable the virtual deskto to 640x480

This is the console output

[PHP]

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17f9a8) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17f728)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17f728)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

[/PHP]

And this is the phrase that say that i installed properly my graphics driver:
> 
@bobogrigio:~/Desktop$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 6100 nForce 405/PCI/SSE2
 GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 



THANK YOU!!!!!
Grazie mille!!!!

---

### Post by lospo on 2007-06-24
Argh! i'ved talked too fast..

now i can play SC, but only in a windowed mode. I can't play full screen...
I like the windowed mode, but i also like fullscreen... Maybe someone want to finish he work??

---

### Post by Enverex on 2007-06-24
> **lospo said:**
> Argh! i'ved talked too fast..

now i can play SC, but only in a windowed mode. I can't play full screen...
I like the windowed mode, but i also like fullscreen... Maybe someone want to finish he work??

Is it an actual Window or is it just kinda stuck in the top left of the screen and has no border? If it's the first then run winecfg and turn off virtual desktop, if it's the latter then upgrade your video drivers, you're probably using the broken ones that ship with Edgy.

---

### Post by lospo on 2007-06-26
No, i explain: if i run winecfg and enable the virtual desktop starcraft starts and i can play it. if i disable the virtual desktop i've got a blank sceen WITH audio effect... and this is strange.

Also in the virtual desktop i've got this strange lines on my console:
[PHP]
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17f988) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17f708)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
[/PHP]

And... last but not least this is the console outup when i try to use Battle.net multiplayer:
[PHP]
wine: Unhandled page fault on read access to 0x60c7c7d7 at address 0x7bc3aa59 (thread 0009), starting debugger...
/usr/local/bin/starcraft: line 11:  5484 Segmentation fault      wine StarCraft.exe
[/PHP]

i've seen is a "v.1.00" on the bottom right of the main starcraft screen... mybe it's useful

THAKN YOU!

---

### Post by Enverex on 2007-06-26
Firstly those lines in the console are just Wine's debug output messages, they don't matter to you.

"/usr/local/bin/starcraft" is concerning because that's not where starcraft should be. Are you using a script or something?

Update Starcraft anyway, you're over 14 versions out of date.

Please also paste the output of "xrandr" when you run that from the terminal.

---

### Post by lospo on 2007-06-27
I use the script made by instruction of page one:
[PHP]#!/bin/bash

#umount the cdrom
umount /cdrom

#mount StarCraft
mount /media/download/Download/Starcraft/starcraft.iso

#wine StarCraft
cd ~/.wine/drive_c/Program\ Files/Starcraft/
wine StarCraft.exe

#unmount cdrom when done
umount /cdrom[/PHP]

And this is the output of xrandr
[PHP] SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 342mm x 270mm )  *50   53   54  
 1    800 x 600    ( 267mm x 211mm )   51   58   59   60   61   62  
 2    640 x 480    ( 213mm x 169mm )   52   67   68   69  
 3    960 x 600    ( 320mm x 211mm )   55  
 4    840 x 525    ( 280mm x 185mm )   56  
 5    832 x 624    ( 278mm x 220mm )   57  
 6    800 x 512    ( 267mm x 180mm )   63  
 7    720 x 450    ( 240mm x 158mm )   64  
 8    640 x 512    ( 213mm x 180mm )   65   66  
 9    640 x 400    ( 213mm x 141mm )   70  
 10   640 x 384    ( 213mm x 135mm )   71  
 11   576 x 432    ( 192mm x 152mm )   72  
 12   576 x 384    ( 192mm x 135mm )   73  
 13   512 x 384    ( 171mm x 135mm )   74   75   76  
 14   416 x 312    ( 139mm x 110mm )   77  
 15   400 x 300    ( 133mm x 105mm )   78   79   80   81  
 16   320 x 240    ( 106mm x  84mm )   82   83   84  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
[/PHP]

As the other times, i'm waiting your reply...
Thank you GURU !!!!! ;)

---

### Post by Enverex on 2007-06-27
Replace "wine StarCraft.exe" with "WINEDEBUG=-all wine StarCraft.exe" as that will speed things up a little. But update Starcraft first, that may be what is causing the crashes.

---

### Post by lospo on 2007-06-27
Little better...

But it isn't stable... sometimes it chash into a blank screen with audio... and battle.net won't work anymore...
reading the log i can see this when i have the blank screen.

[PHP]
Jun 27 22:58:39 bobogrigio -- MARK --
Jun 27 23:00:42 bobogrigio kernel: [ 1013.003755] loop: loaded (max 8 devices)
Jun 27 23:00:43 bobogrigio kernel: [ 1013.778772] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:43 bobogrigio kernel: [ 1013.779047] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:43 bobogrigio kernel: [ 1013.783126] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:43 bobogrigio kernel: [ 1013.783400] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:43 bobogrigio kernel: [ 1013.783892] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:43 bobogrigio kernel: [ 1013.874252] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:43 bobogrigio kernel: [ 1013.874529] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:43 bobogrigio kernel: [ 1013.924735] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:43 bobogrigio kernel: [ 1013.925001] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:43 bobogrigio kernel: [ 1013.925548] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:43 bobogrigio kernel: [ 1013.925795] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1013.959793] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1013.960056] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1013.960304] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1013.969584] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system
Jun 27 23:00:44 bobogrigio kernel: [ 1013.969765] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows
Jun 27 23:00:44 bobogrigio kernel: [ 1013.969960] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1013.970220] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows
Jun 27 23:00:44 bobogrigio kernel: [ 1013.987716] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1013.987970] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1013.988212] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1013.988481] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1013.988762] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1014.017163] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.017429] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.017671] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1014.017937] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system
Jun 27 23:00:44 bobogrigio kernel: [ 1014.018110] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows
Jun 27 23:00:44 bobogrigio kernel: [ 1014.018305] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1014.018590] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows
Jun 27 23:00:44 bobogrigio kernel: [ 1014.022261] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.022526] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.022775] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1014.023043] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1014.023304] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/windows/system32
Jun 27 23:00:44 bobogrigio kernel: [ 1014.066246] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.066510] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.099367] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.099636] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.099906] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.100151] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.174581] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.174853] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.175118] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.175353] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.233750] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.234220] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.234634] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.234877] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c/Program Files/Starcraft
Jun 27 23:00:44 bobogrigio kernel: [ 1014.312324] ioctl32(StarCraft.exe:5680): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/lospo/.wine/drive_c
[/PHP]

Maybe?

Enverex, you are like a brother (or sister, but i think a brother) if you will come to Italy i will search for everithing you need (hotel, restaurants, tickets...), and i'll pay you a lot of beer (...or coffee...:))

---

### Post by Enverex on 2007-06-27
Run the game manually from a terminal and post the output of that instead. This output isn't any use.

---

### Post by lospo on 2007-06-28
> **Enverex said:**
> Run the game manually from a terminal and post the output of that instead. This output isn't any use.

I understandbut i don't know how: when the screen is blank i only can reset my machine without reading any from console.

I tryed to do
 /usr/local/bin/starcraft > file.txt
but, after the reboot, the file was empty.

I don't know how can i read the output from console... excuse me.
This evening i'll try installing Broodwar...

Thank you.

---

### Post by Enverex on 2007-06-29
You need to run Wine normally and pipe that to a file, please see the FAQ in my sig on how to do that.

---

### Post by mokmoki on 2007-06-29
why can't my starcraft detect my cd drive? i've installed the game via wine... the cd is mounting... but it still says "unable to read required file"...

---

### Post by Enverex on 2007-06-29
Have you set the drive up correctly with the correct letter and location in winecfg?

---

### Post by Robert98374 on 2007-06-30
mokmoki
something you might need to do is add where the image is being mounted in to the Wine config as a drive

---

### Post by lospo on 2007-07-02
> **Enverex said:**
> You need to run Wine normally and pipe that to a file, please see the FAQ in my sig on how to do that.

i'm so unhappy, i've searched for all the weekend, but i can't find how to "pipe something" on a file. Please excuse me, when i reach this goal i'll post a new question.

---

### Post by Enverex on 2007-07-02
> **lospo said:**
> i'm so unhappy, i've searched for all the weekend, but i can't find how to "pipe something" on a file. Please excuse me, when i reach this goal i'll post a new question.

wine blah.exe &> ~/Desktop/blah.log

---

### Post by StifflerNewb on 2007-07-07
*First problem solved*

didn't wanna doublepost

The game is lagging ALOT, really chunky mousemoves and such. any ideas why guys?

---

### Post by Enverex on 2007-07-07
Open Regedit and import this  [http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg](http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg)

---

### Post by lospo on 2007-07-07
> **Enverex said:**
> wine blah.exe &> ~/Desktop/blah.log

Am I a stupid? Mybe yes...

It has worked for three day in fullscreen mode, this morning it won't start GRRRR!
Same scenario: black screen with audio and only hard reset work....
This is the log file:
[PHP]
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17ff48) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17fc28)->(0x10024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
[/PHP]

---

### Post by StifflerNewb on 2007-07-08
> **Enverex said:**
> Open Regedit and import this  [http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg](http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg)

that makes the game even slower, and it crashes x when I try to close wine

---

### Post by ghindo on 2007-07-09
I think I'm receiving a similar error to mmendez - I get a pop-up saying that I need to insert the CD to run the program (even when the CD is loaded into the computer).  I included an attachment to give a better idea of the error I'm running into.

---

### Post by the_it on 2007-11-13
Hi guys!

I've completely forgotten this topic already, until someone just gave me an IM asking a question about it.

cafegamer tells me he would like to have 2 different users playing starcraft at the same time via multi-seat.  I honestly don't know how this looks like: does he have two mice? two keyboards?  is this over a network display?; however, his main problem was that I unmount the cd on every startup/stop.

My solution is to add an instance count in tmp.  If starcraft is running only once, it will unmount the cd.  If not, the cd will not be unmounted.  You can replace the old starcraft or broodwar shell script with this code.

```

#!/bin/bash
#change this variable to name your app
APPNAME="Broodwar"

#change this variable to give your application full path
APPPATH='c:/Program Files/Starcraft/Starcraft.exe'

#change this variable to locate your cdrom
CDROM="/home/roms/BroodWar.iso"

# mounting logic goes here
RUN="/tmp/count${APPNAME}`
RUNCOUNT=`cat ${RUN}`

#check if runcount is at least 1
if ! [ $RUNCOUNT -ge 1 ] 2>/dev/null; then 
    #runcount doesn't exist, initialize to 1
    RUNCOUNT=1
    echo $RUNCOUNT > ${RUN}
else
    #increment the runcount by 1
    RUNCOUNT=$((RUNCOUNT+1))
    echo $RUNCOUNT > ${RUN}
fi

#mount the cdrom
if ! [ $RUNCOUNT -ge 1 ]; then
    #if the program is not yet running, try to mount the cdrom
    mount ${CDROM}
fi

#wine StarCraft
wine ${APPPATH}

#determine the runcount again
RUNCOUNT=`cat $RUN`

#check if runcount is at least 2
if ! [ $RUNCOUNT -ge 2 ] 2>/dev/null; then 
    RUNCOUNT=$((RUNCOUNT-1))
    echo ${RUNCOUNT} > ${RUN}
else
    # this is the only instance running, unmount the cdrom
    RUNCOUNT=0
    echo ${RUNCOUNT} > ${RUN}
    umount ${CDROM}
fi

```

Please report any difficulties here.

---

### Post by cafegamer on 2007-11-13
Thanks the_it for your quick reply,

I have not tried the new script. First to make sure that every thing works perfectly, i need to try the first srcipt in page 1. But you know what, surprise , it fails asking to enter the CD. Although the Image is mounted perfectly and the directory is listed in the drives Tab of winecfg as follows : D:  /media/cdrom0. 

But when i put the CD inside the drive everything works fine. 

Also if that might help, when i run winecfg, and i go on the Drives Tab, i have this error in the shell : 

fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0

Any Clue,

Thanks in advance to all for your help.

---

### Post by the_it on 2007-11-13
hi cafe.
Anyone who complains that starcraft cannot find the cd is experiencing one of a few possible problems.  Sorry I was not able to follow up everyone.

---
1) mounting level problems
the iso was not mounted correctly.  If the command "mount Broodwar.iso' fails on the command line, an error was made in configuring the mount point in /etc/fstab.  To ensure that this is the case, the following process will work.

```
sudo mount -o loop /path/of/iso/Broodwar.iso /media/cdrom
wine c:\\Program\ Files\\Starcraft\\Starcraft.exe
```
the above snippet manually mounts the iso image (without consulting fstab) and tries to run starcraft.

If the application magically works after ensuring that the cdrom is mounted, please double check the fstab entry for the cdrom to ensure that the full path of the iso and the mount point is correct, and that 'users' is one of the options.  Any user should be able to mount and unmount the cdrom.

```

/home/roms/StarCraft.iso /media/cdrom iso9660 loop,noauto,users 0 0

```

in this fstab entry, /home/roms/StarCraft.iso is the full path to the StarCraft image, and /media cdrom is the full path to the cdrom image.  everything else should remain as is.

---
2) wine configuration problems
wine was not configured to point to the correct cdrom path.  this can be remedied by checking the drive mapping in your winecfg and making sure that the cdrom drive letter, which may be d: or e: (or whatever), points to the correct mount point, which is usually /media/cdrom.

If this is the case, no amount of wine trickery will get the program to work unless the winecfg is changed.

---
3) application configuration problems
the application (broodwar) maintains (stupidly) its own registry entry that points to the cdrom, and this cdrom registry entry was not updated.  This may happen if you are trying to configure wine, you run a program once, then you change the drive mappings in wine afterward.

Some programs are smart enough to update their registry stuff to match your system every time they run.  Others aren't.  To update their registry stuff, you have to run

```

wine regedit

```

and look for the program's registry entry pointing to the cdrom and update it yourself.

In starcraft, this happens to be under
```

HKEY_LOCAL_MACHINE\Software\Blizzard Entertainment\Starcraft\StarCD

```

make sure that this registry entry correctly points to your cd drive.

===
well, that's all i could really think of that might be the possible problems.  let me know if you have any luck.  thanks.

---

### Post by cafegamer on 2007-11-13
Hi ,

Thanks the_it for your reply.
Unfortunately after step1)  i am still asked to insert the CD inside.

in step2) i have my D: drive pointing to /media/cdrom and in advance options,     
CDROM is selected. But in the shell i still have this message : 
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0

in step3) I have indeed changed the HKEY_LOCAL_MACHINE\Software\Blizzard Entertainment\Starcraft\StarCD which was pointing to drive F: to D:

and went back to redo step1) but fails with the same message : Insert CD.

do not know what to do now.

Thanks.

---

### Post by the_it on 2007-11-14
Hmm... I'll have difficulty testing this from my work comp ( :D) however, lets try pointing your CD drive to F: instead and work from there.

Maybe there's some other configuration starcraft uses that points to the cdrom, and since it originally pointed to F:, maybe that's what's missing.

try to point your winecfg to F:, then also point your StarCD entry to F.  Then reboot wine via wineboot (I'm not sure if this even does anything).

Wish you luck.

---

### Post by cafegamer on 2007-11-15
thanks the_it,
I will try it and let you know by tomorrow.

---

### Post by cafegamer on 2007-11-19
Hi the_it,

Sorry to reply so late, i have tried exactly what you said but unfortunately it is not working, still requesting for the CD.

Thanks anyway for your great help and also this great post and forum.

Ready to give up.

---

### Post by cafegamer on 2007-11-20
Hi There,

Finally got i working. I removed wine with apt-get remove wine, i remove the .wine directory, i reinstall wine with apt-get install wine, i run winecfg, first thing i added a new drive D: and make sure that in Advanced Options, this new drive D: is marked as the cdrom, and then i verify the StarCD in regedit which was already in  D:, i reinstall Starcraft and Broadwar, i run the script and it worked without asking me the CD. that's great Thank you very much the_it for your help.

Now i'm back to my multi-user system with this question before i try out your script, will it be possible to mount my other games like warcraft, far cry, all on /media/cdrom in the /etc/fstab or should i have to create virtual cdrom drives for each of them in /etc/fstab like :

for Starcraft/Broadwar       : /media/cdrom0
for Warcraft III                  : /media/cdrom1
for Far Cry         : /media/cdrom2

So that each user can play a different game at the same time.

Thank you.

cafe.

---

### Post by cafegamer on 2007-11-20
Hi the_it,

Thanks.

I have the script for a multi-seat system on page 4.

To get it running fine i have to take out the "!" after the "if" in this section of the script :

#mount the cdrom
if ! [ $RUNCOUNT -ge 1 ]; then
    #if the program is not yet running, try to mount the cdrom
    mount ${CDROM}
fi


if i leave  like it is the cdrom drive is not mounted. should i keep the script with this  modification or  should you need to update it. This script is great!!

Cafe.

---

### Post by oni5115 on 2007-11-20
For those getting the whole black screen issue when starting the game, try switching from ALSA to OSS.  I'm not sure why sound would give you a black screen, but switching the audio fixed it for me. (I wish Wine would allow sound as well as gfx to be per application :mad:)

I've also found gmount-iso to be a rather nifty tool for this.  Run the app, set which drive I want an iso as and BAM.  Done.  I liked it, since I came from windows and using Daemon Tools, it is fairly similar.  Not quite as nifty as the scripts, but for those uncomfortable doing all that they could simply install gmount-iso and use it like they did DT.  :)

---

### Post by the_it on 2007-11-27
Hi cafe, sorry for the late reply, was busy all week

> **cafegamer said:**
> 
To get it running fine i have to take out the "!" after the "if" in this section of the script :

#mount the cdrom
if ! [ $RUNCOUNT -ge 1 ]; then
    #if the program is not yet running, try to mount the cdrom
    mount ${CDROM}
fi


if i leave  like it is the cdrom drive is not mounted. should i keep the script with this  modification or  should you need to update it. This script is great!!

Cafe.

hmm this is weird to me and doesnt make much sense...  until I saw a typo in my script :(

```

# mounting logic goes here
RUN="/tmp/count${APPNAME}`
RUNCOUNT=`cat ${RUN}`

```

replace this with

```

# mounting logic goes here
RUN="/tmp/count${APPNAME}**"**
RUNCOUNT=`cat ${RUN}`

```

I tested this again on mine it should work.... <__<

sorry if it's too late.

This script should probably work on most apps that require a CD but don't do some special CD checking or something like that.  But from my understanding a wine app should not be able to detect the difference between a (correct) iso and a cdrom using this method.

---

### Post by cafegamer on 2007-12-03
Hi the_it,

No it's not too late but i made the changes as you said before you post them here but still the same if i do not to take out the "!" after the "if" in this section of the script :

#mount the cdrom
if ! [ $RUNCOUNT -ge 1 ]; then
#if the program is not yet running, try to mount the cdrom
mount ${CDROM}
fi


if i leave like it is the cdrom drive is not mounted.

Thanks.

---

### Post by Gharakh on 2007-12-11
I'm having trouble with getting this to work as well.. I've tried just about every combination of winecfg/fstab/broodwar script editing and still can't get it to work (on ubuntu gutsy, should be the latest versions of everything including Wine).

The game will launch with the actual Brood War cd in the drive but seems slow, and crashes when I try to get into battle.net.

Without the cd, whether I try to run it from the script or not it always says please insert cd, winecfg is set up correctly and so is the fstab as far as i can tell. Editing starcd in regedit accomplishes nothing.  Any ideas, do you need more info from me?  Thanks!

One thing that is weird is in winecfg, when I go to audio settings I get some ALSA errors and junk in the terminal (but i'm not using alsa) I run a Creative XMod USB audio and it works fine for music and movies and everything else I've thrown at it..

---

### Post by cafegamer on 2007-12-14
Hi there,

this is waht you shoud do >

1)
remove your . wine directory 
run winecfg
go the Drives Tab and click add
Add a D: directory

click show advanced options and and select CD-Rom drive for the new D: Directory,

Click Apply and then Ok.

2)

For the sound you should just check the Drive Emulation check-box, and then apply and after ok.

---

### Post by Gharakh on 2007-12-16
Thanks very much Cafegamer, it is all working fine to launch Brood War now, but when I go to Multiplayer - Brood War, and hit okay to try to log in to battle.net for the first time the top bar of ubuntu shows up and the game goes a funky color and to some sort of windowed mode. I can alt-tab out.. i'm starting it unpatched, should I try to get the patch elsewhere? Could someone help me out with that if so? (EDIT: Never mind on that, got it updated successfully. Still crashes when I try to launch into Battle.net, though it is definitely updated because it shows the different portals now)
Here is what shows up in my terminal when launching the broodwar script (again, script itself working fine thanks everyone for the tutorials and the help!)

```
fixme:winmm:MMDRV_EXIT Closing while ll-driver open
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12b528)->((nil),00000008)
err:ntdll:RtlpWaitForCriticalSection section 0x7d3c717c "?" wait timed out in thread 0014, blocked by 0000, retrying (60 sec)
```

I think that err shows up only after I've tried to get into bnet. And it keeps repeating that every 60 secs obviously. Thanks for any help

EDIT: So here's where I stand.. updated Brood War to latest patch, scripts all working but crashed at bnet.  I tried importing the registry that was posted a few pages back (EnableOpenGLDDraw.reg) and now I think I'm really screwed :/  Now when I try to launch the broodwar script I get a bunch of strange output in the terminal. Strange memory addresses, unable to open '/build/buildd/wine-0.9.46/dlls/wined3d/surface.c'
and then it lists a bunch of modules and their address and debug info..  any suggestions? :S  (even if someone can tell me how to undo this, that would be fantastic, thanks)

---

