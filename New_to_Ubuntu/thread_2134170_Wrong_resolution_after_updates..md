---
title: "Wrong resolution after updates."
date: 2013-04-10
forum: New to Ubuntu
---

### Post by fernetekhd on 2013-04-10
[SIZE=2][FONT=arial]Soooo about an hour ago Ubuntu started bothering me about 17 or so updates and, realizing that I wasn't really doing anything important anyways, I decided to simply install them. The install went fine, rebooted aaaaaand...

Suddenly my 1920x1080 display was using a laptop's display size. No warning, no idea what happened.

So first I began by uninstalling Nvidia, figuring that maybe the software update had a conflict with it (I did so by using sudo apt-get remove --purge nvidia -* and, with a few other lines of code, reinstated the nouveau drivers as the primary). 

This did a jolly boatload of nothing, so I turned to Google and found the xrandr command.

However, whenever I'd try and re-set the resolution to 1920x1080 (although I also tired 800x600 just to try and fix it) I'd get a message of 'Can't open display'.

So then I stumbled on this thread [http://ubuntuforums.org/archive/index.php/t-867506.html](http://ubuntuforums.org/archive/index.php/t-867506.html)

Using a command listed there ([COLOR=#000000]sudo DISPLAY=:0.0 xrandr --screen 0 -s 800x600) I got it to stop shouting that it couldn't open the display and got it to start shoutng about how the resolution I chose was not in available modes.

I was able, after a bit of hair-ripping, to coax Ubuntu into opening the display settings (which I could barely use since 50% of the window was taking up 90% of the screen) and found that apparently it's decided my monitor is a laptop, and as such only has one laptop resolution (640x480) available.

So...any suggestions?

Edit: Edited topic name since Nvidia isn't a factor at this point.[/COLOR][/FONT][/SIZE]

---

### Post by pinballwizard on 2013-04-10
> **fernetekhd said:**
> [SIZE=2][FONT=arial][COLOR=#000000]

So...any suggestions?[/COLOR][/FONT][/SIZE]


Try: [http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)

---

### Post by oldfred on 2013-04-10
What version of Ubuntu? 12.10 & maybe 1204.2 need headers.
Did you install the headers? Not sure if then you have to reinstall on every kernel update (you should not have to). But maybe something was not quite right?

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by fernetekhd on 2013-04-10
> **pinballwizard said:**
> Try: [http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)

I got stuck on Step 2 because my the computer is so screwed up that I couldn't even highlight the output; along with that, while in Gnome (I can't even get to the terminal because the sidebar's cut off) if I move the mouse around the blackscreen wipes away until the desktop appears.

@oldfred Ubuntu v12.10

Trying that command netted no results. Did it, rebooted, and still ended up with jack diddily squat.

Using the commands from that post didn't help either. Then again, I wasn't having trouble with Nvidia- it was already long gone and uninstalled.

Also, apparently if I do an install (ex. installing the generic headers) I can't enter any new commands until I reboot the computer.

I'm so frustrated that I'm about to just Boot n' Nuke (FOR THE THIRD TIME THIS WEEK) and reinstall Ubuntu (FOR THE FIFTH TIME THIS WEEK).

---

### Post by pinballwizard on 2013-04-10
Slow down tiger. If you run the live environmentr from the disc you would install from, do you get all you resolutions?

---

### Post by dfpd62 on 2013-04-10
Hi Folks, just installed recommended updates to 12.10 64bit, and rebooted as required.
After reboot the dashboard and app bar on the left of screen (set to autohide) and the status bar top are missing,
Screen resolution seems ok, firefox looks all right, CTRL + and - works ok.
Also have no window controls (minimise, maxamise, x).

fortunatly I remember the keyboard shortcut to start a terminal, otherwise I cannot start programmes.

Seems that I am not the only one to have this trouble.

Regards, Donald.

AMD 6 Core
Ubuntu 12.10 64bit. (2 weeks old and all updates applied.)
Radeon HD6450
8gb Ram

---

### Post by fernetekhd on 2013-04-10
Glad to hear others suffer as I do!

@pinball Yes, if I boot via the usb that I use to install Ubuntu the resolution is completely normal (i.e. 1920x1080 for me).

EDIT: That's what you meant for me to do, right?

---

### Post by fernetekhd on 2013-04-11
Ok, update. I tried that link you sent again Pinball, and turns out I was able to put the code in since the output of my code in Step 2 was exactly the same as the one in the post.

However, all commands I entered returned "Can't open display".

Also, for whatever reason Gnome now opens in the correct display.

-_-

I love Ubuntu.

...okay another edit. Although my display settings still show my screen as being a laptop, I do have a 1024x768 option now which is...better, I guess. But I can't do anything with my computer, more or less.

Ok, final edit. I give up, I'm just boot n' nuking, as I think it'll be easier.

---

