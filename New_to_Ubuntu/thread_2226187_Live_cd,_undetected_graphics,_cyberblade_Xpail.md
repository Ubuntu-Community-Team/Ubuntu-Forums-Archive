---
title: "Live cd, undetected graphics, cyberblade Xpail"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by crip720 on 2014-05-25
I have a Toshiba A20 satellite laptop that Lubuntu 12.04 works very well.  I am trying to upgrade to 14.04 with a clean install, but am having problems with the graphic card not being detected.  live cd wants to go into low graphics mode, but seems to hang and go to black srceen with blinking cursor.  lspic[?] says that vga controller is a Trident Microsystems CyberBlade XPail.  Memory has been increased to 1256MBs.  I do not want install[can dual boot] till I know how to fix this.  CPU is pae capable.  The 12.04 install went very well with no problems, but upgrade to 12.10 by update manager left me blank screen on reboot, reinstalled 12.04.  Do have error at begiining of live cd loading saying something like to update Bios or to force something, then it goes the TRY or INSTALL screen.  After clicking on Try, it say graphics not detected going to low graphic mode.  Laptop does not have capablly to boot from USB  I imagine that this a graphic driver missing problem,  but do not have the know how on trying to fix this.  Any help would be appeciated.  Colin

---

### Post by squakie on 2014-05-26
It may be that it simply needs a driver.  While changes aren't remembered across boot of live media, you may want to try looking at Additional Drivers (System Settings/Software and Updates/Additional Drivers) and see if anything shows there as available.  If it does, install it in your live session and see if you are able to set things to a more likable situation.

---

### Post by squakie on 2014-05-26
You may want to look at post #9 in [this]("http://ubuntuforums.org/showthread.php?t=1509556&highlight=Trident+Microsystems+Cyberblade") thread.  Be forwarned that it is a VERY old post for a VERY old version of Ubuntu.  The thing I would check into is where it shows a xorg.conf that apparently worked.  I know there hasn't been a default xorg.conf file for several releases, and I'm not sure it's supported anymore.  I would need to search but it's possible there are now config files that will need to be updated.

I'll let you know if I find and learn anything.

EDIT:  it appears that xorg.conf is still placed in /etc/X11 - not sure what the ownership is supposed to be - but I would assume it needs to be root, so you may need to:

sudo chown root xorg.conf
sudo chgrp root xorg.conf

Can't promise that's correct, as I haven't had a need to touch xorg since release 10 of Ubuntu.

---

### Post by crip720 on 2014-05-26
Hi, some more info.  Some of the error message at first is force_addr=0xaddr, and something about ALI15x3 not detected.  there is another error mentioned that has something like 0xfffffffffff.  I am trying to do a dual boot install now, so maybe with some help I can try to add the stuff I need to fix this.  thanks.  Colin  This also is on the Ubuntu install.

---

### Post by squakie on 2014-05-27
Did you try copying the xorg.conf file from the link I posted, then pasting it to a new file /etc/X11/xorg.conf?

---

### Post by crip720 on 2014-05-27
Hi, I ended up installing Ubuntu 14.04 in a dual boot on this laptop, since the Lubuntu installer did not work[ went to black screen].  The install went very well except at end were it asks to be restarted.  shutdown gave warning of , could not acquire 'org.freedesktop. modern manager 1' service name.  I did a hard shutdown.  It now wants to go into low graphics mode, so I guess I will have to do everything by the comdand line.  Should I use the conf you pointed to, or could I find/copy the conf in Lubuntu 12.04 that never gave me problems?  I will probaly need exact instructions on using the comand line for this work.  Thanks.  Colin.

---

### Post by crip720 on 2014-05-27
I am going to need some help since I am am getting a no such file for xorg,  will also need help accessing /etc/X11 the proper way, so I can try to add the xorg.conf file to it.  Colin

---

### Post by crip720 on 2014-05-27
I can get into /ect/X11 for 14.04 from 12.04, but have no idea how or which one of the files to add the xorg.conf file to.  Thanks.  Colin.

---

### Post by squakie on 2014-05-28
All you should have to do is this:

- copy the xorg.conf file from the link and save it as xorg.conf in your home folder
- sudo cp xorg.conf /etc/X11/xorg.conf
- reboot

See if it makes any difference or not.  Like I said when I posted the link, it's VERY old thread.

---

### Post by crip720 on 2014-05-28
Before I copy this xorg file into 14.04, do you know if Lubuntu 12.04 would have a file in it that would do the same thing.  12.04 has always worked well with the laptop, so it should have the right file/s.  Also do you know how to find the file in Lubuntu,  I am not sure, because I am used to Ubuntu's file system/names and GUI more than Lubuntu's.  Thanks.  Colin

---

### Post by squakie on 2014-05-28
It's quite possible 12.04 had a driver for xorg that isn't delivered with 14.04.  I know some place along the line, but not exactly sure how long ago, some things changed in X11,   Since what I have read on the net regaring your hardware is almost entirely old posts, it is quite possible the xorg driver isn't installed.  That much I don't know, but I can try to look around.  In the mean time, given that the sample xorg.conf in the link supposedly worked for someone, why not try it??  The worst that can happen is that it doesn't work, you have to login via the recovery console or a terminal session and rm /etc/X11/xorg.conf.

---

### Post by squakie on 2014-05-28
[This]("http://manpages.ubuntu.com/manpages/gutsy/man4/trident.4.html") link says Gutsy, but also lists 14.04 across the top, so it must still apply.  Note it lists the driver file you may need to install:

sudo apt-get install  xserver-xorg-video-trident

Should install it, but it might already be installed.

After that, the link shows the relavent xorg.conv section (device) information.  I don't know if not specifying an entire xorg.conf file will work or not, but you could try the following:

sudo gedit /etc/X11/xorg.conf  (it should be empty unless you've already done something)

Put the following in the file:

EDIT:  I REVISED THE INFORMATION BELOW  - PLEASE BE SURE YOU ARE USING IT


Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "record"
	Load  "dri2"
	Load  "glx"
	Load  "extmod"
EndSection



Section "Device"
Identifier  "Card0"
    Driver      "trident"
    VendorName  "Trident Microsystems"
    BoardName   "CyberBlade XPAi1"
    BusID       "PCI:1:0:0"
EndSection

Save the file.

Reboot.

That is just a portion of the xorg.conf that I think is relavent.  Note that in the complete xorg.conf file in the link, there are other options (subsections) within the device section that you might need (screen, monitor display).  It also possible the BusID will need to change as yours might be different.

---

### Post by crip720 on 2014-05-28
Hi I am having trouble trying to copy the xorg.conf file into 14.04.  I had 12.04 running so I could copy the link you gave me, but after I mounted 14.04, I could not seem to paste or move the conf file into it.  I did open the 14.04 files as root.  I do not know how to do any copy/pasting in 14.04 since I can only open up a CLI shell in it.  The only graphics I can get on it is screen asking if I want to go into Low graphics mode and that one just sits there doing nothing till I shut down.  Do you know how I can get the xorg.conf into 14.04?  I do have a USB flash drive I can use.  Colin.

---

### Post by squakie on 2014-05-28
Are you able to go to low graphics mode??  How are you running 12.04?  From a DVD?  From a USB stick?  If worse comes to worse:

- copy the file - you are doing a copy and trying to paste, right? - to a USB flash drive
- boot 14.04
- type:

sudo df -h

Note the disks that show.

- insert the USB flash drive
- type:

sudo df -h

There should be a new "disk" now - that would be your flash drive.  It's probably mounted in /media/your userid>.

- type:

cd /media/<your userid>/<the folder>
sudo cp xorg.conf /etc/X11/xorg.conf

reboot

---

### Post by crip720 on 2014-05-28
Two problems, first 14.04 won't do an apt-get because of one 'not useing locking, two unable to write, three package lists ... not parsed or open.  Second problem does see the USB drive, and I think that the root shell promt that I am using is set to read only.  I am running 12.04 and 14.04 as a dual boot on the laptop.  Low graphics mode not working, just the screen that asks if I want to go into low graphics mode.  Basicly all I can use is root shell promt on the recovery section.  14.04 did have access to wifi during install, and the graphics during the install session seemed to be normal[ all the screens that usually come on during an install came on].  I am going to leave this for now and come back to work on it tomorrow night.  Thanks for your help.  Colin.

---

### Post by squakie on 2014-05-29
Right now I've exhausted what I think needs to be done.  I can see you are having problems getting there, and I don't know enough to guide you further.  I'll leave it up to someone with more knowledge to try help you.

---

### Post by jakke1975 on 2014-05-29
I've had similar issues with a friends computer.... black screen on the latest ubuntu and older ubuntu versions did work.
It turned out to be the monitor and NOT the GPU driver. You may want to check if you have another monitor that you can use to check it out...
Always try to diagnose what exactly isn't working before trying to find a solution for something that may not be an issue ;)

You may simply have to edit your X configuration files to get the monitor to work properly.

---

### Post by squakie on 2014-05-29
Read post #1 - it's a laptop - so another monitor is only good for testing - but does nothing in regards to the problem:  the video adapter requires entries in the device section of xorg.conf.   If you follow the links in my posts and read them completely, you'll see this has been a common problem with these adapters.  In addition, the link to Ubuntu manpage show the trident driver as needing to be declared in xorg.conf.

---

### Post by crip720 on 2014-05-29
I probaly need the USB mount command for 14.04 to see the USB flash drive, hopefully the root shell promt will use it,  maybe also the wifi command to turn on wifi.  Thanks,  Colin

---

### Post by sudodus on 2014-05-29
Lubuntu 12.04 worked well but has passed end of life. But there are several re-spins promising support until April 2017 based on Ubuntu 12.04 LTS, ***Bento, Bodhi ***and*** LXLE***. I suggest that you try them and stay with the one that works best for you.

(I think there is a problem between the graphics driver in Lubuntu 14.04 LTS and your graphics card.)

---

### Post by crip720 on 2014-05-29
Reply to  Sudodus's post.  Thank you for your imput, I haved used LXLE before on my main laptop that is an Acer, and did like it, except the Deepin software centre did not work to well, had to use synpactic.  I do not know if I just got exemly  lucky with Lubuntu 12.04 or if any of the lite 12.04s would have worked.  This Trident card has given proplems to other people before according to what I have google.  I think that Sqaukie has an answer to my porplem, but there is a picnic or ID error trying to get it to work.  Anyway your solution will only put it off for three years.  Can you explain the surrport for Lubuntu 12.04.  I think that only what Lubuntu added to the Ubuntu base is not supported any more, as in the Lubuntu desktop and what comes with it.  I am still recieving updates to some of software on it.  Thanks,  Colin.

---

### Post by crip720 on 2014-05-29
To squakie I have got the usb mounted, and I also was able to change the read only file system to read/write.  Cannot use gedit, because Gtk-warning cannot open display.  I am also having problem cd ing into the usb.  probaly not using the right syntac.  Colin

---

### Post by crip720 on 2014-05-29
df -h lists usb as /dev/sdb1[size and used] /media/external.  My user name drip, and the only folder on the usb is xorg.conf.Can you give me the correct cd command so I can get into this, I keep getting No such file or directory error so I must be doing something wrong.Thanks  Colin.

---

### Post by sudodus on 2014-05-30
> **crip720 said:**
> Reply to  Sudodus's post.  Thank you for your imput, I haved used LXLE before on my main laptop that is an Acer, and did like it, except the Deepin software centre did not work to well, had to use synpactic.
Once you get used to ***Synaptic***, it will work very well for you :-)
 >  I do not know if I just got exemly  lucky with Lubuntu 12.04 or if any of the lite 12.04s would have worked.  This Trident card has given proplems to other people before according to what I have google.  I think that Sqaukie has an answer to my porplem, but there is a picnic or ID error trying to get it to work.  Anyway your solution will only put it off for three years.
Lubuntu 14.04 LTS end of life is the same year and month, April 2017.
>   Can you explain the surrport for Lubuntu 12.04.
Lubuntu was so new, that it was not ready to get long time support. It had only the standard version support, which was 18 months at that time. Now the standard version support is reduced to 9 months, which means that it is much preferred to stick to the long time support (LTS) versions.
>   I think that only what Lubuntu added to the Ubuntu base is not supported any more, as in the Lubuntu desktop and what comes with it.  I am still recieving updates to some of software on it.  Thanks,  Colin.

This is correct. The program packages specific to the Lubuntu desktop have no support, not even security updates. But the Ubuntu engine under the hood receives updates until April 2017. So you are on your own security-wise, when you continue to run Lubuntu 12.04.

---

### Post by mörgæs on 2014-05-30
> **crip720 said:**
> Anyway your solution will only put it off for three years.

That's long in computer context. A lot of interesting distros will be born during that period of time, for example Lubuntu 16.04.

---

### Post by crip720 on 2014-05-30
I used to use the Ubuntu Software centre just to install synpactic because I found the software centre to be slow.  I now use App Grid and it is much faster.  We are kind getting off topic here, so I would like to ask if someone could help with post 23.  I copy the xorg.conf file to the flash drive using a computer with the user name crip. and do I need to use sudo in root promt.   Thanks  Colin.

---

### Post by sudodus on 2014-05-30
> **crip720 said:**
> df -h lists usb as /dev/sdb1[size and used] /media/external.  My user name drip, and the only folder on the usb is xorg.conf.Can you give me the correct cd command so I can get into this, I keep getting No such file or directory error so I must be doing something wrong.Thanks  Colin.

```
cd /media/external
```

brings you to the 'root' directory of the external drive. Do you mean that there is a folder with your name 'drip'? In that case

```
cd /media/external/drip
``` brings you there. Or you mean that there is a folder with the name 'xorg.conf'? In that case

```
cd /media/external/xorg.conf
``` brings you there.

If this is confused or confusing, I suggest that you post the output of the following command within code tags, and we can help from there.

```
sudo find /media/external
```

---

### Post by crip720 on 2014-05-30
Hi, I was able to add the xorg.conf files mention above to 14.04.  One per reboot.  I have the second partial xorg.conf file in /ect/X11 now.  Neither one seems to help.  14.04 keeps asking to go low graphics mode, but I get struck one the second screen that has the four options.  options are; run in low, reconfigure, troubleshoot, and exit to console.  I can change the option by using the up/down key then the enter key,  but I cannot find how to use the OK / cancel buttons at the bottom right.  left/right keys do nothing or the enter key.  How do I use the ok button to go to low graphics mode?  Thanks, Colin

---

### Post by crip720 on 2014-05-30
Question I have been getting ali1535 errors on startup, as mention in post #4, was just googling and from this post at [http://lxr.free-electrons.com/source/drivers/i2c/busses/i2c-ali1535.c](http://lxr.free-electrons.com/source/drivers/i2c/busses/i2c-ali1535.c)  .  Seems to be  a driver for similar? chipsets.  It mention Acer labs chipsets, do not know if the Tosbiba uses it.  Would something like this/or this help me.  If you need more info, please mention what and how to use it.  I can access 14.04 by root shell prompt or by booting 12.04 and mounting 14.04.  Thanks, Colin.

---

### Post by squakie on 2014-05-31
Did you try the suggestion I posted earlier about checking to be sure you have the driver installed?  Just do the command there.  If you've read one of the links, it talks about those exact error messages and the solution has been the things I've been telling you:

- be sure the xorg driver for Trident is installed
- update xorg.conf

If you've done that and it doesn't work, then try copying the entire xorg.conf that is listed in one of those links as well.

---

### Post by crip720 on 2014-05-31
I did the apt-get for trident and it said it was already the newest.  I did have a lot of trouble trying to paste the xorg.conf to X11 in 14.04, but that because 14.04 kept opening in read only mode.  I now know how to remount it to read/write.  I first pasted in the xorg.conf file that was in post#9 you mentioned early on, did not seem to help, same low graphics mode.  I then moved that one to trash and replaced it with the short one you wrote.  same thing.  I only pasted the files into X11 into the xorg.conf folder, maybe I need to do something else also.  I did open the file after pasting to check on them and they looked the same as the ones you told me to copy.  I did read another post suggesting to change lightdm to gdm, but when I tryed apt-get I was getting not found errors, probaly was in read only mode at the time.  Would the ali1535 driver help as mentioned my post above, and you help with the problem I have getting into low graphics mode, see above also.  Thanks, Colin.

---

### Post by squakie on 2014-05-31
There should be no "xorg.conf folder" in X11.  You need to create the FILE xorg.conf in /etc/X11.

---

### Post by crip720 on 2014-05-31
I am probably doing something wrong, but from 12.04 I mount 14.04,  go to etc, go to X11, and in X11 there are ~ 10[didn't count] blue  pictures that look like file folders with names like Xsession, Xinit and the like.  I made new one and name it xorg.conf and place the copy in it.  Let me know what I should have done[learning as I go].  sorry for being a dufus should know more of this stuff by now.  Thanks for helping.  Colin.

---

### Post by squakie on 2014-05-31
Copy the xorg.conf *FILE* to just the /etc/X11 FOLDER.

Then DELETE the /ect/X11/xorg.conf *FOLDER*.

That should leave you with an xorg.conf *FILE* in /etc/X11.

If need be, put what I posted originally for the portion of xorg.conf that appeared relavent to your video in that xorg.conf *FILE* - you need all the "stuff" for device including the driver as trident.

Remember - this is a *FILE* in /etc/xorg,  **NOT** a folder in /etc/X11.

---

### Post by squakie on 2014-06-03
It's been a couple of days - what's the status?

---

### Post by crip720 on 2014-06-03
Hi, I did copy of xorg and pasted it to the etc/X11 folder, did not work, maybe I should have opened the X11 folder and pasted it to one of files.  I was thinking of just deleting the whole X11 folder in 14.04 and copying the working X11 from 12.04, if X11 is problem, can't break the system any better.  I did do a delite of 14.04 and tried a Lubuntu 14.04 dvd but it doesn't install, seems like only Ubuntu 14.04 been able to do a working installer.  Did burn an dvd of LXLE 12.04, and that is working well as a live dvd, so I do have a fallback cheat if needed. I have been using Ubuntu since 10.04 and tried other Linuxs, but this is the first major problem I have had, and would like to fix it if possible.  It's fun also.  Thanks  Colin.

---

### Post by squakie on 2014-06-06
Please don't just remove everything and shoot in the dark.

If you feel you may have messed things up, reinstall Ubuntu.  After doing so, select and copy the xorg.conf file I showed, then open a terminal (ctrl/alt/F1) and do the following:

sudo gedit /etc/X11/xorg.conf 

paste in what you selected/copied from my post

delete any other existing content

save the file

exit

reboot

If that doesn't help, DON'T try other things - post back instead.  All of us who might try to help need to be sure things are done as we ask, and then we know what the status is.  We may have you back something out, then try something new again.  Just don't go shooting in the dark.  Read the links I showed and search the net for general linux help with that adapter.  All the error messages you mentioned are in those posts.  The solutions (like I said, OLD) are what worked.

---

### Post by crip720 on 2014-06-06
I did do a new clean install of Ubuntu 14.04 since that is the only one that will do the installer completely.  gedit does not want to work because of no GUI.  I seem to only have the root shell to work with, and I cannot seem to be able to connect to the net, but the D-Link wireless card does have both lights blinking.  I do have a working DVD of LXLE 12.04.  I cannot get the Low Graphics to work either.  The second screen of Low Graphics will only change the options, cannot seem to make the Cancel or OK buttons work.  Did look into X11 folder after copying of xorg file but could not find it.  Was looking from 12.04. After I did the copy from the usb to X11 cp came back saying "omitting directory 'xorg.conf' ".  I am using the first xorg conf, that you pointed to post #9 of the old answers.   Thanks for putting up with me.  Colin

---

### Post by sudodus on 2014-06-07
I suggest that you keep trying according to the advice of *squakie*. Good luck :-)

-o-

But at some point you must be prepared to give up 14.04 LTS and install LXLE, which works for you and which promises long time support until April 2017. Some compatibility with old hardware is lost in the process to make the kernel work with new hardware.

---

### Post by squakie on 2014-06-07
It can't be saying "omitting directory 'xorg.conf'"  IF you have followed what I said.  Any such folder would have been deleted if you had followed those instructions.

At this point I don't think I can help any further.  The answer has been given.  The links I posted show those answers.

Good luck!

---

### Post by crip720 on 2014-06-09
I would like to thank all the people who have tried to help me, especially Squakie and Sudodus .  I have installed LXLE instead and it is working fine.  I think that help and instructions probably might have fixed  my problem, but these fine people were trying to help, but I was an idiot with the coding.  I might look into 14.04 later when I have some time and understand how to type the commands better.  Thank you for your help.  Colin.

---

### Post by mörgæs on 2014-06-09
Good, please mark the thread 'solved'.

---

### Post by squakie on 2014-06-09
We're just glad you've got a working system now, regardless of what you used!  This can help others in the future who may run into the same problem.

---

### Post by sudodus on 2014-06-10
Good luck with LXLE *crip720, *and welcome back with questions whenever you need help :-)

---

