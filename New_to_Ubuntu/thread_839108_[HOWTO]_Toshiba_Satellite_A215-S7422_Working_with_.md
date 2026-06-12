---
title: "[HOWTO] Toshiba Satellite A215-S7422 Working with Ubuntu Hardy Heron 8.04!"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by mbarvian on 2008-06-24
Hi all,

The following are the steps I took to get my Toshiba Satellite A215-S7422 laptop working completely with Ubuntu Hardy Heron 8.04.  Please note that this is my first HOWTO, and that I am a complete newb, so I may not be able to answer all of the questions you might have.  These are simply the steps that I took and worked, and will probably work with laptops with similar hardware, so if you do get this working on a laptop other than the Toshiba Satellite A215-S7422, please say so in a post and I will add the laptop's model to the supported laptops list in the bottom of this section.

Please read the entire guide and not skip to certain parts (it's not that long:))Also, before I begin, I just want to say thanks for all the great people in this community and those of you who helped me get my laptop working. :)

**Supported Laptops:**
Toshiba Satellite A215-S7422
(if this guide worked for yours, please say so in your post and I will add the model here)

[SIZE="5"]_1. Realtek 8187b Wireless_____________________[/SIZE]

When I first loaded Ubuntu onto my PC, in my extreme-newbie days (about two months ago), I thought and expected all of the hardware to work right "out-of-the-box".  I quickly realized that this wasn't the case, and I quickly gave up on Ubuntu and started a thread requesting help to remove it only after a few hours of installing it.

A few days ago, I happened to be browsing the forums to look for a possible solution to my wireless problem, and saw a potential fix for the RTL8187b wireless card (the one thing that was keeping me back from installing Ubuntu again).  You can find the fix [here]("http://ubuntuforums.org/showthread.php?t=792092&highlight=rtl8187b"), as posted by Tom--d.  I decided to give another shot at Ubuntu if this could potentially solve my wireless problems, so I did.

Unfortunately, I did not get any luck with this route, although some claimed they have, just not me.  I then turned to the hacked drivers which you can find [here]("http://www.datanorth.net/~cuervo/rtl8187b/").  I decided to revive my old thread about installing these drivers, and finally figured out the answer about 8 hours ago (thank you chili555 and tamoneya, and everyone who posted on my thread).  So, without further ado, I present the solution for the RTL8187b wireless card:

[LIST=3]
[*]**Download the Drivers:** You can download the hacked driver to use with the RTL8187b wireless [here]("http://www.datanorth.net/~cuervo/rtl8187b/").  Download rtl8187b-modified-jadams-2-1-2008.tar.gz to the desktop.
[*]**Extract the tar.gz:** First things first, you must extract the .tar.gz that you just downloaded to the Desktop.  To do this, make sure you are on your desktop and that you see rtl8187b-modified-jadams-2-1-2008.tar.gz.  Then, right-click this file and select "Extract Here".  Now, you should have a new folder on your desktop named rtl8187b-modified.  You can now right-click on rtl8187b-modified-jadams-2-1-2008.tar.gz and select "Move to Trash".
[*]**(Install?) the Driver:**  Again, I'm a newb, so the reason that "Install" is in parentheses is because I do not know if that is the right term for what I am about to show you how to do.  Anyway, now that you have rtl8187b-modified on your desktop, go to Applications > Accessories > Terminal. Once that is loaded, you are going to want to enter in this command: 

```
cd /home/your_username_here/Desktop/rtl8187b-modified/
```

"CD" means "Change Directory", so you are telling it to change the directory to rtl8187b-modified.  I have typed in "your_username_here", but make sure to substitute this with the name you use to log in on your computer.  When you are finished, hit "Enter" on your keyboard and you should get a new line that looks like this:

```
maxwell@maxwell-laptop:~/Desktop/rtl8187b-modified$ 

```

This means that you have changed directories successfully.  Please note that "maxwell" will be replaced by your name.  If it says

```
bash: No such file or directory
```

you have NOT changed directories successfully, and need to proofread the first command.

OK, now that I assume we have all changed directories into rtl8187b-modified, we can move on.


[LIST]
[*]**Make makedrv (Executable?):** Again, the reason I put "Executable" in parentheses is because I do not know if that is the right term.  Anyway, what you are going to want to do now is (once we have changed directories successfully) enter this command in this same terminal window that we used in the last step:

```
sudo chmod +x makedrv
```

It might ask you for your password.  If so, just type in the password you use to log in.  Please note that you will not see any *'s when you type in your password, and this is normal.  When you have finished typing in your password, push the "Enter" button on your keyboard.  If it did not ask you for your password, you are fine.

Well, by now our terminal window should look like this:

```
maxwell@maxwell-laptop:~$ cd /home/maxwell/Desktop/rtl8187b-modified/
maxwell@maxwell-laptop:~/Desktop/rtl8187b-modified$ sudo chmod +x makedrv
[sudo] password for maxwell: 
maxwell@maxwell-laptop:~/Desktop/rtl8187b-modified$ 

```

Notice that after you have typed in the above command, it simply goes to the next line.  This mean that it was successful, so we can now type in the following command:

```
sudo ./makedrv
```

Once you have typed in this command (and have hit "Enter" on your keyboard), you should see many lines of text write themselves in the terminal window.  You should also see many warnings, but this is fine.  After this is done, you can proceed with the next step.


[*]**Make wlan0up (Executable?):** Once you have completed the previous step, type the following into the terminal window:

```
sudo chmod +x wlan0up
```

After typing this in press "Enter" on your keyboard, and, if done successfully, you should be on a new line that looks like this:

```
maxwell@maxwell-laptop:~/Desktop/rtl8187b-modified$ 

```

If the previous command was successful, simply type in this final command:

```
sudo ./wlan0up
```

After a few seconds, it should create a new line that looks like the one shown above, and, if you followed all of the steps, you should be done!  Now click on the Network Manager > Unlock > Enter the password you use to log in to the computer > Wireless Connection, and connect!  If you still do not see Wireless as an option in the Network Manager, please review all of the steps again.  Also, please note that the Network Manager can be a bit... clumsy ...at times, so give it around 30 seconds (yes, it sometimes takes this long!) time to connect.
[/LIST]
[/LIST]

[INDENT][SIZE="4"]_Drawbacks of using this driver: ________________[/SIZE][/INDENT]

[LIST=3]
[*]Although you can connect to Wireless networks and get the full strength of the signal, the icon will only show you that you have 30% and one bar
[*]This driver works best on unsecured wireless networks, although I am pretty sure that it supports WEP, but I am waiting for somebody to confirm this
[*]This driver might not support WPA or WPA2 encryption, but I am waiting for somebody to confirm this
[/LIST]

[SIZE="5"]_2. ATI Radeon x1200 Graphics Card________________[/SIZE]

Although it may appear that your graphics card is working fine (assuming you have an ATI Radeon x1200 chip like the one that comes in a Toshiba Satellite A215-S7422), it, in fact, is not working 100%.  However, it is an easy fix, and very useful if you are looking at getting [some cool desktop effects]("http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074").  Let's get started!

[LIST=2]
[*]**Download and Install ATI Catalyst Control Center:** This one is pretty easy.  To do this, just go to Applications > Add/Remove Programs > make sure All Available Programs are listed > check (or tick) the box next to ATI Catalyst Control Center.  Then click "Apply Changes" down near the bottom.
[*]**Download and Install the Necessary Packages:** Please note: you must have a working Internet connection for this section to work, so why not use your new Wireless connection:)? Also, you must have the extra repositories enabled in System > Administration > Software Sources for this section to work.  If you are connected to the Internet in some way, go to Application > Accessories > Terminal and type in:

```
sudo apt-get update
```

This will update your software.  After that is done (it might prompt you for your password, if so, just type it in), type in:

```
sudo apt-get install linux-restricted-modules-generic

```

This will install the package we need for this driver to work: linux-restricted-modules-generic.  Once you are done with that, type in:

```
sudo apt-get install xorg-driver-fglrx

```

This will install the actual driver for the card.  Once that's finished, type in: 

```
sudo depmod -a

```

Once all of that is finished, you are going to want to edit the xorg.conf file, so please type in:

```
sudo gedit /etc/X11/xorg.conf

```

Once gedit opens up with xorg.conf, look for a section that looks like this:

```
Section "Device"
	Identifier  "whatever"
EndSection
```

Once you find it, add a new line below "Identifier" and add the following text to it:

```
Driver      "fglrx"

```

Also, please note that "whatever" is not the actual text you are going to see in the file, but I realized that the text where "whatever" is changes, so I put "whatever" in to avoid confusion.  Just to be clear, the "Device" section should now look like this:

```
Section "Device"
	Identifier  "whatever"
        Driver      "fglrx"
EndSection
```

Then click Save at the top of the program, and it will close.

Now, type this in terminal:
```
sudo aticonfig --initial -f

```

Now, restart your computer.  Once it reboots, click Applications > Other > ATI Catalyst Control Center.  If you get this window:

[IMG]http://i231.photobucket.com/albums/ee240/mbarvian/amdccclecw1.jpg[/IMG]

, you have successfully installed your graphics card!  Now you can look into some of those neat [desktop effects]("http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074").  However, if, when you try and open ATI Catalyst Control Center you get a screen like this:

[IMG]http://i231.photobucket.com/albums/ee240/mbarvian/Screenshot-Initializationerror.png[/IMG]

, it was unsuccessful and you need to review all of the steps and try again.

[/LIST]

[SIZE="5"]_3. Tips and Tricks________________[/SIZE]
[LIST=1]
[*]**Configure ./wlan0up on startup:**  If you used the above guide to install the Realtek Drivers, you might notice that you have to do "sudo ./wlan0up" from the rtl8187b-modified directory every time you restart your computer!!!  That's not fun, so, if you want it to do this automatically on startup, first right-click on the rtl8187b-modified on your Desktop and select Cut.  Then, go to Places > Home Folder > right-click > Paste.  The folder "rtl8187b-modified" should now be off of your Desktop and in your home folder.  Now, go to Applications > Accessories > Terminal and type in the following:

```
sudo gedit /etc/rc.local
```

Now, add two lines below where it says:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
```

On the second line, type in:

```
cd /home/your_username_here/rtl8187b-modified/ && ./wlan0up
```

Now save the file, and close out of terminal.  This should now load .wlan0up on startup, so you don't have to.  Just be sure that you have placed rtl8187b-modified in your home folder, and you replace "your_username_here" with your Ubuntu username.
[/LIST]

That's all for this guide, although I will be adding more to it if anyone sees fit.  If you are having trouble, please post saying so, and I will see what I can do, although please keep in mind that I have very limited knowledge on the subject, being a newb and all.  Thank you for all your help, again, and if this post helped you, please click the ribbon in the bottom-right corner of this post.

Thank you, and have fun! :)

---

### Post by RSingh on 2008-06-24
Nice HowTo. Could a forum admin move this to the "Tutorials and Tips" section.

---

### Post by mbarvian on 2008-06-24
:lolflag:yes it probably should be moved :)

---

### Post by mbarvian on 2008-06-24
UPDATED [Jun 24, 2008]

Added two images and made some minor changes to the wording.

Mods, please put this in the Tutorials and Tips section of the forum :)

---

### Post by mbarvian on 2008-06-24
Sorry for the triple post, but this page has been added to help.ubuntu.com:

[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

---

### Post by ADloser on 2008-06-29
Nice post!
Unfortunately for me it doesn't quite work..
I set up the wireless exactly as you have described and soon after I run ./wlan0up my system crashed / hard freezes. Right before it freezes though, the wireless network appears on my network manager. Any help?

Also, I'm running 64-bit if that makes a difference.

---

### Post by mbarvian on 2008-06-30
> **ADloser said:**
> Nice post!
Unfortunately for me it doesn't quite work..
I set up the wireless exactly as you have described and soon after I run ./wlan0up my system crashed / hard freezes. Right before it freezes though, the wireless network appears on my network manager. Any help?

Also, I'm running 64-bit if that makes a difference.

I'm glad you like it!

Hmm, are you using any encryption with your wireless network (such as WEP, WPA, or WPA2)?  Mine also is 64-bit:)

---

### Post by ADloser on 2008-06-30
So, I've resorted to reinstalling 7.10, where my wireless works fine (after installation through the same method you described, only using the original modified drivers instead of jadams).

I do have a WEP encryption on my network, although I can't see why that would make my system crash. I tried it once again with live boot to see if the problem was with my installation and I ended up with the same exact problem.

---

### Post by mbarvian on 2008-06-30
Well, these drivers have been known to freeze the system when trying to connect to a WEP, and (sometimes) shut down the system when trying to connect to WPA.

---

### Post by ADloser on 2008-06-30
OK that may be it then. Unfortunately I need to use am encryption to secure my router, so I guess I'm stuck with 7.10. Thanks for the help though.

---

### Post by mbarvian on 2008-06-30
You're welcome. :D

---

### Post by lrbradford on 2008-07-01
I followed your procedure on my Toshiba A215-S7414 for the wireless, and still no worky.  The ATI worked!

Any other suggestions?

---

### Post by onewithnature83 on 2008-07-20
pretty much same.

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

### Post by lrbradford on 2008-09-09
Let's bring this thread to closure.  Someone gave me the idea to upgrade my kernel from 2.6.24-something-generic to  the latest: 2.6.27-2-generic.  How?  I found a thread that suggested this command in terminal

$ gksudo "update-manager -d"

I did this, update manager opened showing Ubuntu 8.10 was available.  Someone had told me he had problems with his Toshiba A215-S7414 or something close, and he upgraded to 8.10 and his wireless started working.  I must say, mine did as well.  After entering my WPA2 password, I have been on wirelessly since.  It's great!

As soon as I find out who made the suggestion, I shall thank you!

My hope for Linux has been renewed!

LB

---

### Post by yaseer999 on 2008-10-28
Hi,

I'm trying to run fedora on vista ultimate 32-bit using virtual box
my laptop is Toshiba with processor: AMD Turion(tm)64 X2 
but when fedora starts to boot it freeze and the screean flashes, so any one knows what's the problem??

---

