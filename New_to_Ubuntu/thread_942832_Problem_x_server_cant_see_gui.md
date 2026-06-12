---
title: "Problem x server cant see gui"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by pgar23 on 2008-10-09
hey all.
So i was finally able to install ubuntu on my system but I still am unable to view any GUI or anything on ubuntu for that matter. I am curious as to what my next steps should be. I read a few threads and I am getting a hunch that I will need to use the recovery mode command line and possibly install some drivers..if anyone has useful advice, please share. Thanks in advance.

---

### Post by NullHead on 2008-10-09
What model and manufacturer of your graphics card?

---

### Post by pgar23 on 2008-10-09
BTW, I dont receive any errors or anything, I just cannot view anything on the screen. I receive a blank brown or black screen and when I move the mouse i can see vertical lines but nothing more. that is y it leads me to beleive that maybe i need some graphic drivers installed..

---

### Post by pgar23 on 2008-10-09
> **NullHead said:**
> What model and manufacturer of your graphics card?
Mobile Intel Graphics Media Accelerator X3100, 128-358MB shared memory

---

### Post by Nasaki on 2008-10-09
Well if it boots successfully, then type startx. 

Also, could you give us the specs and model of your system. Also, is there any errors during boot?

---

### Post by pgar23 on 2008-10-09
> **Nasaki said:**
> Well if it boots successfully, then type startx. 

Also, could you give us the specs and model of your system. Also, is there any errors during boot?
Toshiba Satellite m305-s4848
intel core2 duo T5800 cpu
4GB ram
64-bit OS
and there are 0 errors on boot

---

### Post by kwacka on 2008-10-09
Is this of any use?

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=674123](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=674123)

---

### Post by pgar23 on 2008-10-09
so i want to make things simple for everyone to understand.
I start my laptop.I see grub. choices are ubuntu generic, ubuntu recovery, and memtest. when I choose ubuntu generic it will boot no prob.I see splash screen and all is well until I reach the login screen(or at least I think its the login screen,cuz I cant see it). I reboot and I chose the recovery mode and chose to fix x server(xfix)..but this did nothing and I tried to boot normal after that but still no such luck. anything else I should try??

---

### Post by NullHead on 2008-10-09
ok, go to recovery again in grub, and when it gets to the prompt with "xfix" in it, select the one that says "drop to terminal" or what ever it says ... (can't remember). Now what you want to do, is open up your configuration file for your xserver. That's called xorg.conf, it's located in /etc/X11/xorg.conf and you can open it and edit the file on the command line with a command line text editor called nano. 

I've properly explained what you're doing with this next command; lets get to it then! ```
nano /etc/X11/xorg.conf
```
You'll see a bunch of text rambling about stuff ... you want to look for the [configured video card] section and look and see what's inside the tags []. If there's really nothing to speak of, put in right underneath it, four spaces and the word "Driver" with a capital "D"; put in four more spaces then put the work "vesa" in **with the quotes!** You **need** those quotes in there otherwise it won't work.

Save the file by pressing Ctrl + x and say yes, then press enter to save over the file. Restart the computer with this command: ```
shutdown -r now
``` and then start again with your generic kernel. 

If you do manage to see the display, you can do some research into the proper driver that you'll need for your intel card. 

If I'm thinking correctly, intel cards are very well supported and it just needs some configuration similar to what you just did. 

Hope all that helps ;)

---

### Post by pgar23 on 2008-10-09
ok thanks alot nullhead. I tried your advice and it partially worked to my surprise..I got to see a glimps of the ubuntu login screen then I got the same thing as before..I get a blank brown screen and its mixed when I move the mouse..

---

### Post by NullHead on 2008-10-09
What happens if you change the section that says "vesa" to "intel"? That's of course in /etc/X11/xorg.conf

---

### Post by pgar23 on 2008-10-11
> **NullHead said:**
> What happens if you change the section that says "vesa" to "intel"? That's of course in /etc/X11/xorg.conf

nothing even changed..im starting to get scared. I have never had a problem that couldnt be solved while installing ubuntu..anything else i should try?? does anyone have a link or thread that would be useful??

---

### Post by pgar23 on 2008-10-12
bump

---

### Post by pgar23 on 2008-10-12
attached are a few snapshots of my screen. for a better understanding ;)
splash screen loads and whatnot..but afterwards is a different story...womp womp

---

### Post by pgar23 on 2008-10-12
Okay so i found another thread that has the same problem and has yet to be fixed..(BUMMER) guess i will be using Vista for now until they fix the bugs..btw its a problem with the graphics driver of course..

[http://ubuntuforums.org/showthread.php?t=923817&page=2](http://ubuntuforums.org/showthread.php?t=923817&page=2)

---

