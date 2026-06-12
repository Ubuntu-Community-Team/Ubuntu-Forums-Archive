---
title: "Ubuntu 7.04 On Gateway MX3215 Laptop How-To"
date: 2007-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by anewguy on 2007-07-23
This how-to is a quick guide to getting Ubuntu 7.04 working on a Gateway MX3215 complete with wireless, sound and the Via 3d driver for X.  Hey, I'm very much a novice, so there is nothing "professional" to this how-to.  Also, note that everything in this how to came from somebody else's work - things I found either in the Ubuntu forums or via a Yahoo search.  I never kept track of all the posts/sites I went through, so I'm sorry I cannot directly thank those people - just know  the information provided is not original!!:)

If you plan on keeping Windows and being able to dual boot Windows or Ubuntu, you should be sure that about 35% of your hard drive is free, and defrag the disk under Windows first.

The first thing you will need to do is download the Ubuntu 7.04 LiveCD ISO image, the burn the image to a CD.  Remember this is a CD image, so you can't burn it as a data disk, instead look for an option like "burn image" in your burning software.

If you won't have wired access to the internet once Ubuntu boots up, please follow this link and download the wireless driver from Gateway,  then burn that to a separate data CD.  The link is:

[http://support.gateway.com/support/drivers/getFile.asp?id=20712&dscr=Gateway%20Broadcom%20Wireless%20Network%20DriversVersion:%203.100.64.1&uid=16644933](http://support.gateway.com/support/drivers/getFile.asp?id=20712&dscr=Gateway%20Broadcom%20Wireless%20Network%20DriversVersion:%203.100.64.1&uid=16644933)

You now have what you need to install Ubuntu, so place the LiveCD in your CD drive and reboot your computer - it should come up with a Ubuntu desktop.  One of the options on that desktop is "Install" - click on it and the installation process will start.

You will be asked for things like your time zone, your name, computer name, etc., and eventually get to a screen asking about disk usage.  If you are comfortable with working with disk partitions, you can select the manual option.  Just to make things simple, I click on the top line, which automatically resizes your Windows partition down and uses the new empty space for your Ubuntu installation.  After verifying your options, the installation process will begin.

When the installation completes, there will be a window asking if you want to continue running off the LiveCD, or if you want to restart and run your newly installed Ubuntu installation.  Click on the restart, and when prompted, remove the CD from the drive and press enter.  If you let things default from there, you will boot up you new installation of Ubuntu.

If you try it out a little, there are a few things you will notice:

- your touchpad is set of tapping
- your wireless doesn't work
- your sound doesn't work
- your screen has a strange resolution

Everything except the screen resolution are easy fixes.  For the screen resolution, I can't provide instructions for you, just a link to what I used and the warning that go with it.:)

**[COLOR="SandyBrown"]Getting Broadcom 43xx Wireless Networking To Work[/COLOR]**

In order to fix these things, it is best to get the wireless working first.  If you have your laptop hardwired to a network you will need to do step (A).  If you are not hardwired to a network you will need to do step (B).

(A)  For those with a hardwired network connection:

      - click on the following link and download Gateway's wireless driver package:

[http://support.gateway.com/support/drivers/getFile.asp?id=20712&dscr=Gateway%20Broadcom%20Wireless%20Network%20DriversVersion:%203.100.64.1&uid=16644933]("http://support.gateway.com/support/drivers/getFile.asp?id=20712&dscr=Gateway%20Broadcom%20Wireless%20Network%20DriversVersion:%203.100.64.1&uid=16644933")

     You will want to save this download to disk.  By default, my downloads went to my Desktop, which is fine for now.

(B)  For those without a hardwired network connection:

      - put the CD in the drive that contains the driver file you burned when first starting this how-to
      - click on the file on the CD and copy it then paste it to your Desktop folder

Now resuming instructions for everyone:

On your desktop you should see the Gateway driver file you downloaded.  Right click on this file and select open with another program, then select archive manager from the list

Once the archive manager opens, you will see a folder in the Window.  Double click on that folder - this will show you the files in the compressed executable file.  You only need 2 of the files in that archive:

      - find the file "bcmwl5.sys" file.  Single click on this file, then click on the "extract" button.  It will default again to saving to your desktop - this is fine, just click the "extract" button on the window that popped up.

      - repeat the above, but this time find the file "bcmwl5a.inf".  Please note there is also a "bcmwl5.inf" file, but we want only the one with the "a" in it.

This step has placed the 2 driver files we need on your desktop.

Now put your LiveCD back in the CD drive.  When it is spun up, you will get a window saying "A volume with software packageshas been detected.  Would you like to open it with the package manager?"  Click on the "Start package manager" button.  You will be prompted for the administrators' password - just enter the password you used when you logged on.  The Synaptic Package Manager window will open.  Click on the "Search" button, then enter "ndiswrapper" in the search string string and click "search".  Eventually you will see a list of the packages that have the word "ndiswrapper" either in their title or in the description.  In this list, there are 2 files you need:

     - locate the package named "ndiswrapper-common" and click on the box so the box has a check mark in it

     - locate the package named "ndiswrapper-utils-1.9" and click on the box so the box has a check mark in it

     - click the "Apply" button, and this will install the 2 packages.  You may be asked if it is okay to use "x" amount of disk space - just answer "y" and press enter.

     - when the installation has completed, click on the "X" to close out of the package manager.

This step has installed ndiswrapper and it's utilities, which you need in order to install the wireless driver.  This package lets you use Windows wireless driver packages in Linux for wireless cards that aren't supported "right out of the box" by Linux and Ubuntu.

By default, there is a non-functioning version of the driver for the wireless card already in Ubuntu.  You may have seen messages for it when you booted that included something about firmware not found for "bcm43xx".  Before you can load and actually use ndiswrapper and the correct driver, you have to tell Ubuntu to ignore the default driver.  To do this, click on "Applications", move your mouse down to "Accessories", then move your mouse over to "Terminal" and click once.  This will open up a terminal window.  In this window:

     - type "sudo gedit /etc/modprobe.d/blacklist"  and press enter (you can copy and paste everything between the quotes if you want to).  This will open up an editor window.  Scroll down to the very end of that file, press return a couple of times, then type:

# no firmware for default bcm43xx - use ndiswrapper instead
blacklist bcm43xx

then press return a couple of times again.  You can copy and paste the 2 lines above if you want to.  Click "Save" then close out of the editor window. 

For ease, reboot your laptop now.  When Ubuntu comes back up, continue with the next steps.

Click "Applications/Accessories/Terminal" again to open a terminal window.

     - type "sudo ndiswrapper -i ~/Desktop/bcmwl5a.inf" and press enter.

     - type "ndiswrapper -l" (that's a lower case "L") and press enter.  The screen should say driver and the device are installed

     - type "sudo depmod -a" and press enter.  This collects all of the module dependencies needed.

     - type "sudo modprobe ndiswrapper" and press enter.  

Now check the network icon on your upper taskbar and it should show your available wireless networks.  You should be able to click on the wireless network you want to connect to.  If that network requires a "key", you will be prompted.  Be sure to select the correct type of key, then enter in your key.  If all goes as it should, you will then be prompted for a password for a default keyring.  What this is is a file that Ubuntu holds the keys for the wireless networks you connect to.  Enter in some password you can remember and verify it.  I use the same password as I log on with, but if you're concerned about security you may want to come up with a different password.  Once you've filled this in you will be prompted for the keyring password when you reboot or change networks.

Assuming everything has worked to this point, you now need to make ndiswrapper run when Ubuntu boots up otherwise your wireless won't work again.  To do this:

     - type "sudo ndiswrapper -m" and press enter.

You should now have wireless networking working!:)

[COLOR="SandyBrown"]**_Getting Control Of The Touchpad_**[/COLOR]

You can now move on to getting you touchpad working as you want.  To do this, you will need to do a couple of things in the terminal window.  First you need to download  and install the package that lets you configure your touchpad.  This package is called "gsynaptics".  To do this:

      - type "sudo apt-get install gsynaptics" and press enter.  Again, it might ask if it is okay to use "x" amount of disk space - just press "y" and then press enter.

When the installation has finished, you next need to tell the x window system that you can use it.  To do so:

      - type "sudo gedit /etc/X11/xorg.conf" and press enter.  This is a rather long file with stuff in it that you don't need to worry about for now.  Just look for a line that says "Identifier "Synaptics Touchpad"".  Now move the mouse down to the beginning of the line that says "EndSection" and click at the very front of that line, right before the "E" of "EndSection".  Now press enter - this should give you a blank line.  In that blank line type:

        	Option		"SHMConfig"		"true"

(You can copy and paste the above line).  Then save the file and exit.

Now exit the terminal window by typing "exit" and pressing enter.

In order for the changes to the X windows configuration file you just made to take effect, you must restart X windows.  There may be other ways, but I do this as I feel it is the safest:

     - log out of Ubuntu (don't shutdown or anything, just logout)

     - when the log on screen reappears, hold down ctrl alt and press backspace and then let go of the keys.  If you edited the file correctly, the screen will blank out, maybe flash a time or 2, then the logon window will reappear.  Go ahead and log on now.

To access the configuration utility for the touchpad now, click on "System/Preferences/Touchpad".  The "General" tab allows you to enable or disable the entire touchpad.  The "Tapping" tab allows you enable or disable the ability to tap on the touchpad instead of clicking a "mouse" button.  The "Scrolling" button lets you define how you want the ability to scroll with your touchpad to work.

Okay, you've now got wireless networking to work AND can control your touchpad!:)  2 down with 2 to go.  This next one is EASY!


[COLOR="SandyBrown"]_**Turning On The Sound**_[/COLOR]
To enable the sound, double click on the speaker on your top menu bar.  This will open up the volume control panel.  Click on "File", place your mouse over "Change Device" then move over to "Via 8237 (Alsa Mixer)" and double-click.  Now click on "Edit", scroll to and click on "Preferences".  This will open another small window.  Scroll down in that window until you find "External Amplifier" double click it so there is a check mark in the box in front of it, then click "close".  You will now be back on the volume control panel.  Click on "Switches" then uncheck "External Amplifier" .  This seems counter-intuitive to me, but it works!  Now just click back on the "Playback" tab and turn all the volumes up all the way.  I went ahead and activated all of the controls and max'd out the volume on them all.  Now you can just close the volume control window.  If you want to test sound, just do the following:

     - click on "System/Preferences/Sound"
     - the sound preferences window will now open
     - click on the "Sounds" tab
     - click on the "> Play" button after "Log out" and you should hear sound now
     - you can now close the sound preferences window

Okay, so now you've got wireless networking, touchpad control and sound working.:)

Now before we move on, you should know I'm not that smart.  I found all of these things by searching either in the Ubuntu forums or via a Yahoo search.  It takes a lot of time and patience, but the answers are out there.  I just followed someone else's work - so don't give me any credit!


[COLOR="SandyBrown"]**_Video Resolution_**[/COLOR]
Now comes the more difficult of the choices - getting the video resolution you want.  You can do this in the xorg.conf file only but you can also install the 2D or 3D drivers from openchrome if you want to. 

[COLOR="SandyBrown"]Using the xorg.conf file only[/COLOR]
This option is the easiest to get working, and allows normal video playback, etc.
- 
- open a terminal window via "Applications/Accessories/Terminal"
-
- type "sudo gedit /etc/X11/xorg.conf" and press enter
-
- press the fine button for the editor, enter "Generic Monitor" in the search for string and click the "find" button.  Position your mouse to the end of the line and click, then press the return key to start a new line.  Paste in the following  These ranges are not accurate for the LCD panel, but since I cannot get a response from Gateway for the valid ones, you have to put these 2 lines in anyway.
-
        HorizSync       30-96
     	VertRefresh     30-160

-
- press the "find" button for the editor, enter "Default Screen" in the search for string and click the "find" button.  Now scroll down just a few lines.  You will see lines something like this:   Modes		"800x600"   with maybe some text after the "800x600".  What you want to do is completely replace each of these lines (there will be several following) with the following:  Modes		"1024x768" "800x600" 
-
- click save and exit the editor
-
- log out and wait for the log on screen to appear.  Instead of logging on, hold down the crtl  alt and backspace   keys and then let go.  This will reboot the windows manager so the changes will take effect.  When the log on screen comes up again just log on and you should be at 1024x768 resolution.  I have not gotten any replies from Gateway regarding the valid sync and refresh rates for each resolution.  So what that means is that for now you won't be able to successfully change resolution from the default 1024x768.
-
-
[COLOR="SandyBrown"]Using the openchrome drivers[/COLOR]
Be advised that there are a couple of things you need to know regarding the driver:

     - I have not been able to run Beryl or Compiz Fusion with it, so if you want desktop effects when you get done you are on your own!

     - there is a known bug in the driver that is introduced starting with the 2D driver.  I believe it is in one of the packages that is needed.  This bug will prevent you from watching a video in such things as the players that show under "Applications/Sound and Video".  Someplace along the line it messes up and to actually see the video you have to open **_2_** of the players and it will play in the 2nd as long as you are trying to play it in the first.  This applies to DVD's as well!  I have to thank Ubuntu user "tarek" for pointing out the 2 players thing or I would never have video!:)  I have found no work around for this other than going back to the default "VESA" video driver.  I believe this has something to do with the OpenChrome driver not supporting the "panel" option yet (and probably won't).

Okay, so you really want 2D and 3D drivers loaded??  I direct you to the following......follow it very carefully, and expect an abort as noted in the 3D section.  Follow the link it gives, then go back and finish up.  Here's a link to read first:

[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=The+Different+Unichrome+family+display+drivers]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=The+Different+Unichrome+family+display+drivers")

Still want the drivers?  Follow this link:



[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

I hope this helps someone.  If you find an error please let me know!!:)

By the way, if you decide to run a virtual machine to run Windows in Linux, I would suggest you use VMWare Server - it's free and it works great.  Just be sure you do 3 things:

     - set your mouse to type "ps/2" and the device to "psaux"
     - for ease, set the network type to "NAT".  You may need to add a network device in the virtual machine setup to use the wireless
     - you may need to edit the .vmx file that defines the virtual machine and change the line that say something like "scsi0 = enabled" to scsi0 = disabled" in order to boot Windows in the virtual machine.

---

### Post by bapoumba on 2007-07-23
Thread moved to "Tutorials & Tips".

---

### Post by xhizors on 2007-07-31
ha I hate you. Not seriously though. I was about to look for something like this yesterday... Yeah I'm rocking the MX3215 too. Thanks. *crosses fingers*

---

### Post by xhizors on 2007-07-31
ha thanks a lot though, i got some of the good stuff working.
didn't install the drivers, bleh, i just want beryl to work =[

---

### Post by maxi123 on 2007-08-04
do you know if its the same or a similar way for the MX7525

---

### Post by anewguy on 2007-08-04
Don't know, but it can't hurt much to try - just do a clean install, try this, and if it doesn't work, just re-install and try with something else later.:)

---

### Post by kevindubrow on 2007-08-19
Hey. I'll first say that this guide is very good and thanks so much for putting your time into it. I am having some issues working on the wireless though:

I have followed every step word for word and this is what happens at the terminal:

~$ sudo ndiswrapper -i ~/Desktop/bcmwl5a.inf
           driver bcmwl5a is already installed
~$ ndiswrapper -l
           bcmwl5a : driver installed
               device (14E4:4318) present (alternate driver: bcm43xx)
~$ sudo depmod -a
[B]~$ sudo modprobe ndiswrapper
          FATAL: Module ndiswrapper not found.[/B]

The replies say "already installed" because this is the log of the second time I have tried this. Both times each command I was told to put in worked except for the last command. I got both of the files from the Gateway download and both ndiswrapper files from the package manager, so that is not an issue. Every step has gone exactly as planned except for that last terminal command. Could someone tell me what is going wrong? Thanks so much.

---

### Post by anewguy on 2007-08-21
From what you have posted, it looks like it knows the wireless adaptor.  However, I have no idea why your sudo modprobe ndiswrapper doesn't seem to want to work.  I have done this many times with no problem.    If you don't mind (this seems like a lot to ask but is really quite quick), could you:
(1) do  "sudo ndiswrapper -l"
(2) for each driver that shows, do "sudo ndiswrapper -r xxx"  where "xxx" is the driver name as it shows in the ndiswrapper -l
(3) Do this until nothing shows when you do ndiswrapper -l
(4) following the instructions, re-install your driver, being very careful with the path and file name.  One small mistype can result in a "driver" showing in the ndiswrapper -l  command, but it won't be useable.
(5) Do the "sudo depmod -a"
(6) Try the "sudo modprobe ndiswrapper" again.
(7) under "Applications"/"Accessories" go to Take Screenshot and take a shot of the desktop so we can see everything for (1) thru (6), then post back again and include the image so I can see what it all actually looks like.

Thanks!:)

---

### Post by Dark Star on 2007-08-21
Nice tut there :D

---

### Post by kevindubrow on 2007-08-21
It all worked this time around! Thanks for your help. And sorry...I forgot to just take a screen shot. I hoped this helped at all.

~$ sudo ndiswrapper -l
Password:
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
~$ sudo ndiswrapper -r bcmwl5
~$ sudo ndiswrapper -r bcmwl5a
~$ sudo gedit /etc/modprobe.d/blacklist
~$ sudo ndiswrapper -i ~/Desktop/bcmwl5a.inf
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
~$ ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
~$ sudo depmod -a
~$ sudo modprobe ndiswrapper

---

### Post by anewguy on 2007-08-22
While I had no way to know for sure, I did suspect you had more than 1 entry in ndiswrapper for the adaptor - because I went nuts a few times trying to figure mine out until I decided to just clean everything out of ndiswrapper and start over.  Glad it works for you!:)

---

### Post by thedrifter on 2009-03-20
Ok, ! i installed the drivers....but now what?  how do i know my device is working?

how do i get it to detect and connect to a wireless network?

BTW, THANK YOU SO much....this was a very informative thread.

---

### Post by Shlou on 2009-07-27
first off, great wirte-up. I have the mx3215 and i'm hoping to make great use of the info
 
My issue though is i can't even get the ubuntu desktop to load. as soon as it comes up i get a "ubuntu is running in low graphics mode" message, the display tries to restart, then the error comes up again. 
 
i do get an option to configure settings at one point, and i did try to enter the resolution settings you mentioned, but that didn't seem to work. 
 
I'm a linux noob, but have always wanted to jump in and it would suck if my hardware ends up holding me back. this older gateway had seemed like the perfect canadate.

---

### Post by phoenigma on 2010-05-29
Thanks in advance for this easy to understand guide to install ubuntu on the mx3215. I know its been a while since this threat was posted but i decided to give it a shot since i don't have anymore braincells left to continue trying to solve the wireless on this notebook. I'm gonna start by saying that i'm currently dual booting Win XP and Ubuntu 10.04. I followed your steps word by word, but ultimately couldn't get anything done. I reinstalled ubuntu again and tried your steps again but no success. i took the time to do some research about the drivers and i noticed there are 3 different drivers on the gateway website [http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20XP](http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20XP) one of them is the one you posted the link for. Could it be that the drivers needed for my mx3215 is one of the other 2? and if so how can I find out which one is it? and once i find out which one it is what would be the files needed to be installed?

---

