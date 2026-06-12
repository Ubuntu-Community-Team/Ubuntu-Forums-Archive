---
title: "[SOLVED] ubuntu will not start up at all"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-08-22
I have had Ubuntu running on my laptop for about 3 weeks now. I am not a total beginner, but still a newbie.

I will tell the whole story of how this happened.

I work on a ship. This ship has internet access via satellite.
My laptop was running and I plugged in an ethernet cable from the ships router to try to get an internet connection. It worked but when I was in gmail it misbehaved. I put it down to the slow connection. I shut down the browser, but then something looked strange. The quickstart icon for firefox had changed and in fact firefox had vanished from the applications pulldown menu!

I restarted the system.

The starup seems to going normally up unitl I enter my user name and then my password to log in.
After than the screen just stays blank.

Mouse moves around, but that is it.
The only way to shut it down is to pull the power.
I tried to log in using the user name 'root' and the appropriate password, but the result is the same.
I tried starting up in 'safe mode', and even chose 'repair broken packages' in teh options that I had.
Still the same result at startup.

I do not have my Ubuntu installation disc with me and I am not permitted to download large amounts of data for personal reasons.
I do have the parted magic utility boot disc with me which will allow me to at least access the data on the HDD, and maybe some other things.

Is there anything I can do? :-(

---

### Post by Troll_the_Great on 2008-08-22
You can try booting in recovery mode. When to computer boots up, at GRUB menu, choose "recovery mode".There choose "Xfix". GRUB menu should look like this:
Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode
Memtest86
If you don't usually see GRUB menu at start-up press ESC several times when you start the computer.
If this doesn't work, in "recovery mode" choose "drop to root shell" , log in and then type:
```
sudo dpkg-reconfigure xserver-xorg
```
Post back any results.
Hope this helps.
Cheers!

---

### Post by Thingymebob on 2008-08-22
or try a gnome failsafe (its in the options at the login prompt)
Try creating a new user (one of your conf files may be broken) 
in a terminal (ctrl+f1 to get to one) enter
```

sudo adduser testuser

```
replace testuser with whatever username you want and see if that user can log in,

---

### Post by steinzeitmensch on 2008-08-22
Thanks Troll_the_Great and Thingymebob
I have tried all these things and still no startup

In fact now (following the *sudo dpkg-reconfigure xserver-xorg* step ) I seem to be running in reduced graphics mode!

Any other ideas?

---

### Post by Troll_the_Great on 2008-08-22
It might be a problem with your display manger and your video drivers.Let's try to take care of your display first.Log in and then when you see that black screen press Ctrl Alt F1 and you should see something that looks like your terminal.There, we will remove and install again the display manager.First, we remove it
```
sudo apt-get remove gdm
```
Then reinstall it
```
sudo apt-get install gdm
```
Hope I will be more helpful then last time :(
Cheers!

---

### Post by steinzeitmensch on 2008-08-22
I just tried it but it did not work.
At the end it said that I had to log out of all xsessions, and somthing or other failed.

Should I do it again and write down manually what the output was. This could take some time since I would have to do it manualy.

I did this without an internet connection, is that why it did not work?

BTW, the screen is not BLACK after loggin, it is brown. The colour that I configured as my theme colour.

---

### Post by niccholaspage on 2008-08-22
The gdm package will remove ubuntu-desktop,So I think you will need to do a
sudo apt-get install ubuntu-desktop.  You will need to be connected to the internet.
If this fixed your problem,Than open a terminal (Applications>Accessories>Terminal) and type sudo apt-get install fast-user-switch-applet.

---

### Post by steinzeitmensch on 2008-08-22
I have just run the install for the ubuntu-desktop amd there was a confirmation that after this operation there would be 158Mb of space used.
Is this the size of the download?
I do have an internet connection on this ship but it is slow and there are restrictions on the use of it.

I have not run this in the end.

---

### Post by niccholaspage on 2008-08-22
Hm...When you use the command it will say how much you need to download.If the size is too big you might be able to just install a little desktop environment with all the applications you need.

---

### Post by Thingymebob on 2008-08-22
If you have the install cd perhaps you could re-install ubuntu-desktop from there, disable all the other repositories and leave only the cdrom enabled
this should help [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") and have a read of section 8

although I think finding what's broke and fixing it is going to be a better solution for you. If you can, can you post
```

dmesg >> dmesg.log

```
find the file dmesg.log it will be in your home directory and upload it for us, if not have a scan through (dmesg | less) and write down any errors and post them.

also see if you can get a copy of /var/log/Xorg.0.log up for us

---

### Post by Thingymebob on 2008-08-22
Just found this one which probably explains better how to install packages without an internet connection was written for gutsy but should work for hardy to;
[https://help.ubuntu.com/7.10/add-applications/C/offline.html]("https://help.ubuntu.com/7.10/add-applications/C/offline.html")

---

### Post by steinzeitmensch on 2008-08-22
Now bear with me since I am still a newbie to Linux. I started up my machine with the PartedImage boot disc. This way I could use the command line and surf the file structure and copy stuff to a USB stick.
I opened up the command line and typed in the code in your post. but it just ignored this.
Instead what I did was searched the file system for the dmesg.log and found it. It is attached.

I also found the Xorg.0.log and found not only it but a Xorg.0.log.old.log.
I have also attached them here.

*****Please note. I had to do some creating file naming to get the attachment system of this forums to accept the upload of these files.
The  dmesg.log is named now dmesg.log.txt
The Xorg.0.log is named Xorg.0.log.doc
The Xorg.0.log.old is named Xorg.0.log.old.doc

(ouch 8-[, I had to used an MS file extension but it gave me the size limit I required to get the file uploaded ;-))

Hope these logs will shine a light on the problem.

---

### Post by steinzeitmensch on 2008-08-22
I just read your post about installing packages without an internet connection. Problem is I do not have the install disc with me.
I only have the ParteMagic disc. Would this help.
It is not that I have no internet connection, I only have restriction on this connection. Say I would not be able to download more than about 10-20Mb. It is not a finite limit but definitely 150Mb is not going to pass.

---

### Post by Thingymebob on 2008-08-23
Looks like your Nvidia drivr is failing to load glx if you ctrl+alt+f1 at the login prompt to get a terminal then stop gdm with
```

sudo pkill -u root gdm

```
then startx with
```

startx

```

you'll probably get an error like the following when you switch back to the terminal again
```

NVIDIA(0): Failed to initialize the GLX module; please check in your X 
log file that the GLX module has been loaded in your X server, and that 
the module is the Nvidia GLX module. If you continue to encounter 
problems, Please try reinstalling the NVIDIA driver.

Fatal Server Error:
 Caught signal 11. Server aborting.

xinit: connection to x server lost.

waiting for x server to shutdown.

```

if this is the case then you need to reinstall your NVidia drivers (should be a smaller download)

I'm no expert on Nvidia so hopefully if you run into further problems someone else can help

---

### Post by steinzeitmensch on 2008-08-23
Dont know what has happened now.

I did went into the terminal as you instructed, and logged in as root.
Then I entered the 2 commands as you have shown
After the startx command, the screen flickered a bit and now is stuck like before with the working mouse, but the background is not brown anymore, but a checkerplate pattern.

Is that good or not?

---

### Post by maniheer on 2008-08-23
Is your mouse pointer in a X shape as well? If yes, then in terminal type

```

startx && xterm

```

see if xterm comes up

---

### Post by steinzeitmensch on 2008-08-23
When I have logged in, the mouse is a pointer not a cross.

---

### Post by alienexplorers on 2008-08-23
Have you tried resetting grub. There is information about in on this page:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by steinzeitmensch on 2008-08-23
Thanks for the tip mate, but I do not have access to the Ubuntu disc. If you read earlier posts, I am on a ship and I have only limited internet access. I cannot download large amounts of data.

Considering these constraints, are there any more ideas?

---

### Post by steinzeitmensch on 2008-08-23
Hi Thingymebob,
After re reading you post I did no do the last step which was to go back to the terminal to see what came up.
I did this now and this the result.
(excuse any typos since I am writing this out long hand)

```
Module loader preset
Markers: (--) probed, (**) from config file, (==) default settings,
(++) from command line, (!!) notice, (II) information, (WW) warning,  (EE) Error, (NI) not implemented, (??) unknown
(==) Log file: "/var/log/Xorg.0.log", Time: xxxxxxx
(==)Using conf file "/etc/X11/xorg.cong"
(II) Module "ddc" already built-in
(EE) Failed to initialize GLX extension (Comptadible NVIDIA X driver not found)
extected keysym, got XF86KbdLightoff: Line 70 of pc
extected keysym, got XF86KbdBrightnessDown: Line 71 of pc
extected keysym, got XF86KbdBrightnessUp: Line 72 of pc
Atom 4, CARD32 4, unsigned long 4
extected keysym, got XF86KbdLightOnOff: Line 70 of pc
extected keysym, got XF86KbdBrightnessDown: Line 71 of pc
extected keysym, got XF86KbdBrightnessUp: Line 72 of pc
The XKEYBOARD keymap compiler (XKBCOMP) reports:
>Warning     Type"ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>            Ignore extra symbols
Errors from xkbcomp are not fatal to the x server
```

Phewwww. That took some time

Does it mean anything to you?

---

### Post by steinzeitmensch on 2008-08-24
> **niccholaspage said:**
> The gdm package will remove ubuntu-desktop,So I think you will need to do a
sudo apt-get install ubuntu-desktop.  You will need to be connected to the internet.
If this fixed your problem,Than open a terminal (Applications>Accessories>Terminal) and type sudo apt-get install fast-user-switch-applet.

hehehehehehehehehehehe it worked .....sort of :roll:

I decided to try the above idea again and see what the actual size of the download realy was. It was actually only 20 Mb or so.
I t still took over half an hour but it worked. I have my screen back after but the resolution is stuck at 640x480.
Cannot even see the bottom of the 'Monito resolution settings' dialogue.

I will set this post to rest now and try to solve the screen resolution issue in a new thread if I cannot fine an existing one that will do.
Thanks

---

