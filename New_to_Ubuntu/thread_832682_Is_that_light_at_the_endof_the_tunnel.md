---
title: "Is that light at the endof the tunnel?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by collapsing wave on 2008-06-17
someone plese walk me thorough this. 
I have used the alternate CD
I have disabled the LAN cos otherwise it throws a hissy fit. I am logged in  and I have a flashing cursor after a :~$ prompt.
Am I in a happy space? Or should I just walk away now and chalk 30 plus hours of trying to get this thing to load down to experience, and run back to the cold comforts of Mr Gates.

Toshiba Satellite Pro L300 1GB ram
120 gig HDD
celerion 550 2.0GHz 533Mhz fsb
and a realtek thingy that keeps messing it all up

---

### Post by f37u5g0d on 2008-06-17
I believe that you have installed ubuntu without a window management system or any gui at all.  Your :~$ is a command prompt similar to cold Mr. Gates C:/>

---

### Post by collapsing wave on 2008-06-17
> **f37u5g0d said:**
> I believe that you have installed ubuntu without a window management system or any gui at all.  Your :~$ is a command prompt similar to cold Mr. Gates C:/>
 Is that good Or bad?
what is gui
am I asking the wrong questions.
Can I get to a windows management system from here?

Help me f37u5g0d, you're my only hope.

seriously though I am as stuck as a stuck thing in stuck land and whereas i know there is a solution I'm not altogether sure I have the smarts to recognise it when I see it.

---

### Post by cariboo on 2008-06-17
It would be nice to know what the realtek thingy is, because it probably is important.

JIm

---

### Post by ad_267 on 2008-06-17
Did you install the server version? That doesn't come with a gui (graphical user interface). Only the desktop edition does. I'm pretty sure the alternate install has a gui though.

What happens if you type "startx"

---

### Post by manimal347 on 2008-06-17
>>Am I in a happy space
Absolutely. You are sitting in Bash, a common Unix command shell. You can think of it as the DOS prompt, and it is a common Linux command line environment. From here, you can install X11, a WM or DE, and any and all programs you want. Basically, you can now build your system out of Legos- a rewarding but day-long process. I have a feeling you don't want this, so you should go back and use the alternate to do a regular install (not Server or Base). 

Also, more info on just what kind of Ethernet or Wi-Fi chip you're complaining about, and precisely what symptoms it manifests, would be helpful.

---

### Post by Inxsible on 2008-06-17
you must have installed a server instead of a desktop version. You can type in this command to get a GUI - i.e a desktop```
sudo aptitude install ubuntu-desktop
```assuming of course that you want Gnome. If you want KDE, just use this command ```
sudo aptitude install kubuntu-desktop
```
For Xfce the command would be```
sudo aptitude install xubuntu-desktop
```

---

### Post by Victormd on 2008-06-17
> **cariboo907 said:**
> It would be nice to know what the realtek thingy is, because it probably is important.

JIm

The Realtek thingy is most likely this is your network card...

As mentioned earlier, if you're in bash, you're in a happy place... :)

GUI is graphical user interface

What version of ubuntu are you trying to install? 7.10 or 8.04 (or anything prior to these) Server or desktop? 32 or 64 bit? Why did you go with the alternate CD? Didn't the live CD work?

You mentioned that you disabled your LAN so it'll be a bit hard to readily install anything...

If you could answer some of the above questions, it would be easier for us to get a feel for where you are exactly and better help you...

---

### Post by f37u5g0d on 2008-06-17
A GUI (referred to earlier as a graphical user interface) is everything you see and click on when you look at your computer screen.  All the windows, buttons, and menus are part of the gui.  Behind the gui is the command line (that's what you're sitting at).  The command line can do literally everything you can do in a gui.  Like inxsible said in the previous post if you type "sudo aptitude install ubuntu-desktop" after that little :~$ prompt the computer will download and install a gui and you will be in much more friendly territory.

---

### Post by manimal347 on 2008-06-17
I assume you're not posting to us in Lynx, so can you give us a copy of your PCI-bus cards?

Just run "lspci" at the command line. You'll need a NIC to install Ubuntu unless you only want the default software, so we may want to fix the problem so you can enable it*.

*Do explain how it was disabled. Was it done by not loading a module .etc, or with a physical switch on your laptop.

---

### Post by eriqjaffe on 2008-06-17
> **Inxsible said:**
> you must have installed a server instead of a desktop version. You can type in this command to get a GUI - i.e a desktop```
sudo aptitude install ubuntu-desktop
```assuming of course that you want Gnome. If you want KDE, just use this command ```
sudo aptitude install kubuntu-desktop
```
For Xfce the command would be```
sudo aptitude install xubuntu-desktop
```Alternately, you might try just entering "startx" and see if you get into a graphical environment first.

---

### Post by panhandle on 2008-06-18
If you want my advice and you want to save yourself weeks of heartache, forget about getting the Realtek chipset to work. Just <i>forget</i> it.

As a new user, go to Best Buy and pick up a natively supported Linksys USB dongle. Then, load Gnome and this dongle should be supported "out of the box." 

Spare yourself.

---

### Post by collapsing wave on 2008-06-18
startx gives command not found
thanks

---

### Post by cariboo on 2008-06-18
Realtek has been pretty well supported in linux for years, so it shouldn't be to much trouble to get your network card up and running.

Jim

---

### Post by kansasnoob on 2008-06-18
With those system specs you'll be much happier just getting your hands on a "live CD".

Gui is Graphical User Interface or some such thing, that means you see something other than text in front of you. But it definitely sounds like you just have a bad install.

One warning! I did a full install on one Toshiba laptop and Ubuntu is intuitive regarding hardware so it went all-out on the 3-D/Compiz thing but it got HOT .......... really really HOT! The cooling capability just didn't match the 3D capability! Once I removed Compiz that Toshiba was a happy camper!

---

### Post by collapsing wave on 2008-06-18
> **panhandle said:**
> If you want my advice and you want to save yourself weeks of heartache, forget about getting the Realtek chipset to work. Just <i>forget</i> it.

As a new user, go to Best Buy and pick up a natively supported Linksys USB dongle. Then, load Gnome and this dongle should be supported "out of the box." 

Spare yourself.

Ok
I have a usb flash thingy/dongle.
Is this natively supported or do i need a particular type of dongle?  
Its way too late for the saving-of-heartache type thingy

as to the 
sudo aptitude install ubuntu-desktop
I get told my score is -6285 
Y to accpt solution
then Need to get 0B/214MB of archives. After unpacking 738MB will be used. Y to continue
then insert hardy heron 8.04 disk which I have but it doesn't work...
 as for the realtek thingy see this link
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL300-13y](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL300-13y)

This may be the solution but I dont understand it...

Am I right in thinking thatif I can get to a desk top all wil become much clearer cos I'm losing heart

---

### Post by collapsing wave on 2008-06-18
Oh and the LAN was disabled in the BIOS

---

### Post by ad_267 on 2008-06-18
> **collapsing wave said:**
> sudo aptitude install ubuntu-desktop
I get told my score is -6285 
Y to accpt solution
then Need to get 0B/214MB of archives. After unpacking 738MB will be used. Y to continue
then insert hardy heron 8.04 disk which I have but it doesn't work...


What do you mean by "it doesn't work"? What error do you get?

---

### Post by collapsing wave on 2008-06-18
Sorry not being precise enough.

It just repeats the request as though i didn't put the disk in
[54.561708] sr0:CDROM (ioctl)error, command:Test Unit Ready 00 00 00 00 00 00

---

### Post by tysonh on 2008-06-18
sudo apt anything isn't going to work for you until you get your network card fixed. If I were you I'd download the alternate cd for ubuntu 8.04 and call it a day.

I've had good luck with some realtek chips in ubuntu so you might get lucky there.  Just save yourself a brain ache and download a different .iso.  Alternate worked great for me and does a good job is system specs or resources are in question.

Good luck

---

### Post by Victormd on 2008-06-18
If your CD doesn't work, download a new live CD ISO, burn it at 2x and use that. Start from scratch and save some headache.

---

### Post by MrWES on 2008-06-18
Gates stole MSDOS -- it's wasn't his :)

---

