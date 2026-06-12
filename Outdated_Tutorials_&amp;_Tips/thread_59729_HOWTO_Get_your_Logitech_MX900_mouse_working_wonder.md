---
title: "HOWTO: Get your Logitech MX900 mouse working wonderfully without imwheel"
date: 2005-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by kaiesh on 2005-08-25
[COLOR=Red][SIZE=4]WARNING:[/SIZE][/COLOR] [SIZE=2]After testing the setup some more, it was found there is an error in this howto  ](*,)     Basically, the *evdev* driver seems slightly odd (to me anyway) - it appears that if your bluetooth mouse is not connected (i.e. paired with an active connection) prior to Ubuntu trying to launch X, it will fail to detect a mouse, and then break. And thus, not load X. A temporary hack would be to quickly connect your bluetooth mouse when you reboot/startup, but I'm not happy with that. So until a better way of handling it is found, this warning will remain here. The howto may still present some use (note the *may*) and so I'll leave all the text here too.[/SIZE]
------

\\:D/ 
Just like to say, that I managed to get my [Logitech MX900](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=3,CONTENTID=7110)  (bluetooth mouse with what linux sees as 10 buttons) working without using IMWheel. The procedure you can follow is detailed below:
1) Make a backup of your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup_conf
``` 
**[COLOR=Red]Be aware:[/COLOR]** You are making a backup of this file incase you do something (or indeed this HOWTO) breaks your X configuration. If this is the case, all you need to do is copy *xorg.backup_conf* over *xorg.conf* and restart X. That will bring it back to the point that it was when you executed the above command.

2) Find out your mouse details by executing the command:
```
cat /proc/bus/input/devices
```
You should see something like this:
```
I: Bus=0005 Vendor=046d Product=b001 Version=2201
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:62:2E:6F:38
H: Handlers=mouse3 event7 ts3
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0
```


3) I edited my xorg.conf device section to read - please note that yours should be similar but slightly different:
To begin editing, open up _*/etc/X11/xorg.conf*_ in your editor of choice (I like to use VI), then make alterations as necessary... bearing in mind of course the details given in **Step 2** by your system.
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "evdev" 
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "9 10"
        #Use: cat /proc/bus/input/devices to get YOUR 'Dev Name' and 'Dev Phys' **THEY WILL DIFFER**
        Option          "Dev Name"      "Logitech Bluetooth Mouse"
        Option          "Dev Phys"      "00:07:62:2E:6F:38"
        Option          "Resolution"    "800"
EndSection
```

4) Now you need to have your buttons properly configured. Using my MX900, I found the configuration below to work best - let's assume for now that this will work for you too...

There may or may not exist a file in the location */home/<your username/.xinit*, if there does you just need to append a line to it, **if there doesn't, you don't need to worry** - just create it with one line inside. The line you need to put into the file is:
```
 xmodmap -e "pointer = 1 2 3 6 7 9 10 8 4 5"
```

Once you have edited the file and saved it, then run the following command in a terminal:
```
chmod 755 /home/<your username>/.xinit
```

The *xmodmap* line effectively informs X as to what the keymappings are of your mouse, and *.xinit* is simply a startup script executed by X when it begins. The *chmod 755* command makes sure that the file can be executed upon startup.

*Some people* have said that when they start their session their buttons are all weird, and they need to manually execute the xmodmap command - I can't see a reason for this, but if it does happen then you can either do it manually each time, or find a different place to insert it as a startup command... but I have no idea why it doesn't work for them....  :???: 

5) **Restart X**: I recommend doing this by logging out of your current session, and at the login prompt hitting: *Ctrl-Alt-Backspace*

Now that should get all the forward/back, up/down, left/middle/right buttons working - **but** I haven't managed to map the application switching button to anything *yet*.  ;-) 

Now, if you find that you want you buttons configured differently, after you've followed the above procedure, you can play around with the xmodmap command in a terminal window. But that's for you to figure out :)

**Important note:** I found that configuring my mouse this way, resulted in my laptop trackpad being de-activated. I have no idea why this occured, and am currently trying to identify a solution. It doesn't bother me immensely as I use my MX900 most of the time, but some people may find it inconvenient. If anyone else knows a reason why, or finds a way to fix it - please post here.

Also, if this document helps you, please post to this thread (simply to bump it up for the next person).

---

### Post by dude2425 on 2005-08-26
I was told to use /dev/input/event[whatever] if you were going to use evdev, as it works when you use evtest. But, since the number is constantly changing, there needs to be a way to link it to another device whenever it decides to change.
That's why we have udev.

sudo gedit /etc/udev/rules.d/logitech-mice.rules
Add this line:

KERNEL=="event*", SYSFS{manufacturer}="Logitech", SYSFS{idProduct}="***c01b***", NAME="input/***mx310***", MODE="0644"

Change SYSFS{idProduct}="*" to whatever the "Product=" line says in cat /proc/bus/input/devices, and change NAME="input/*" to whatever logitech mouse you've got (in your case, it'd be mx900, I have an mx310 though)

I also got dbus setup to put my ipod on /dev/iPod instead of sd[a-z] so if I have something on sda already, fstab will still mount my ipod where it needs to be. dbus is quite usefull for these kinds of things once you get into it and play around.

---

### Post by PiTT on 2005-10-23
**dude2425**, can you post your settings of xorg.conf, ~/.xinit and etc? I also have an MX310 and I can't get it working... the main problem is the scroll wheel, it only works for a few minutes (i think it stops working when i open firefox, but i'm not sure). Also, the side and top buttons don't work at all...

---

### Post by dude2425 on 2005-10-23
Actually, I never really got it to work with the evdev way. I don't own the 310 anymore either (traded a gulluble sibling for a 510 ;)) I would recomend the regular imwheel way, unless you can somehow figure it all out on your own (if you do, please email me, because your a better man then I)
I wish I can help, but I'm not guru enough to figure it out (only been using Linux since FC3 Test 3 :))

Here's what I had in my xorg.conf (I think):
Section "InputDevice"
    Identifier    "MX310"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mx310"
    Option        "Protocol"        "evdev"
#    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
#    Option        "Dev Phys"        "usb-0000:00:1d.1-1/input0"
    Option        "Buttons"        "7"
    Option        "ZAxisMappig"        "4 5"
    Option        "Resolution"        "800"
EndSection

and instead of using ~/.xinit, I used /etc/X11/Xsession.d/63xmodmap,which I think went something like this:
#!/bin/bash
xmodmap -e "pointer = 1 2 3 4 5 6 7"

I may have it totaly off though, I've changed it since to accomidate for my MX510, which I still cant get to work with evdev. I might figure it out one day, but I just don't have the time to play with things for a whole day.

---

### Post by PiTT on 2005-10-23
Well, I was able to get the scroll whell working after all, but no luck yet on the extra buttons... here's my configuration files.

On /etc/X11/xorg.conf:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event1"
        Option          "Protocol"              "evdev" 
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Dev Name"      "PS2++ Logitech MX Mouse"
        Option          "Dev Phys"      "isa0060/serio1/input0"
        Option          "Resolution"    "800"
EndSection

```

On ~/.xinit:
```

xmodmap -e "pointer = 1 2 3 6 7 4 5"

```

And on /etc/udev/rules.d/logitech-mice.rules:
```

KERNEL=="event*", SYSFS{manufacturer}="Logitech", SYSFS{idProduct}="0002", NAME="input/mx310", MODE="0644"

```

If I ever get the buttons working, I'll post here... :)

---

### Post by dude2425 on 2005-10-24
The whole point of the logitech-mice.rules file is so that you can use /dev/input/mx310 instead of /dev/input/event[1-*] in your xorg.conf because /dev/input/event[1-*] is always changing to something else, and it's a real pain in the butt.

Also, try playing with the ammount of buttons you tell xorg.conf you have, and the zaxismapping, and the xmodmap.

I wish you all the luck in the world with this, because I would love to have all 8 buttons and wheel on my MX510 to work just like I tell it to. It would also be nice if I can tell the extra three buttons neer the wheel to do something, like a cammand line or something. Just something I want it to do. Maybe have an emergency pr0n exiter lol.

---

### Post by PiTT on 2005-10-24
Apparently I spoke too soon... the scroll wheel is still giving me trouble!

I use two computers with 1 keyboard + video and mouse, via a KVM switch (trendware TK200). Computer 1 is my main one, running breezy and win xp in dual boot and Computer 2 is a little server / test pc running hoary still. I've set up both of them exactly the same, using the configuration from my previous post (I just changed "dev/input/event1" with "dev/input/mx310").

The problem is that once I swith the control from one computer to the other, the scroll wheel stops working!

Before I switch, if I run "xev" in a terminal, here's how the buttons get recognized:
left button - 1
middle (clicking the wheel) button - 2
right button - 3
scroll wheel up - 4
scroll wheel down - 5
left side button - 6
right side button - 7

But after I switch the control, "xev" stops recognizing the scroll wheel up and down and both side buttons get recognized as button 2...

Now I'm really stuck!

Any thoughts?

EDIT: I forgot to tell, after I switch and the scroll wheel stops working ,the only way to make it work again is **rebootig** the computer. Just logging off and / or restarting X is not enough...

---

### Post by dude2425 on 2005-10-25
Hmm, quite an odd occurance. I really have no idea what to say to that one, other than "File a bug and wait it out."

---

### Post by Amazing Iceman on 2007-04-12
Quick Question: Did you guys figured it out? 
How to get evdev to work to support all your mouse buttons?
If you haven't please let me know. I found the solution, but it's past 4:00AM here, so I would prefer to do it in the morning.

---

