---
title: "HOWTO: Setup express keys on a wacom tablet"
date: 2006-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by jujoje on 2006-11-13
I've been trying to get the buttons on my wacom tablet for ages, and I've finally managed to get them all working. This is the process I went through te get it working, hopefully someone will find it useful. 

This worked on edgy with an Intuos 3.


**1. Install some packages**
First you need to install some packages. 
```

sudo aptitude install xlibs-dev
sudo aptitude install wacom-tools

```

**2. Install Expresskeys**
Next get the latest expresskeys package from here:
[http://web.comhem.se/~u46139352/wacom/index.html]("http://web.comhem.se/~u46139352/wacom/index.html")
Extract the folder and go to it and compile it:
```

./configure
make
make install

```

**3. Configure Xorg**
Finally you need to configure xorg. The lines that I added were:

 ```

Section "InputDevice"
   Driver        "wacom"
   Identifier    "pad"
 #c~b  Option        "Device"        "/dev/ttyS0"         
   Option        "Device"        "/dev/input/event1"   
   Option        "Type"          "pad"
   Option        "USB"           "on"                
 EndSection

```

and under the "Server Layout" section:
```

InputDevice "pad"    #c~b Intuos3

```

Remember to change the event number to the correct one. 

I'm not to sure what these two lines:
```

#c~b  Option        "Device"        "/dev/ttyS0"

```
and
```

InputDevice "pad"    #c~b Intuos3

```
Actually relate to. I tried removing them and the express keys stopped working. Unfortunately I can't find where I originally nabbed those two lines from. Any explaination would be most welcome :-)

**4. Testing**
Restart X with <alt>+<ctrl>+<backspace> and log back in. Go to a terminal and run expresskeys
```

expresskeys

```
And then go to a programme to test them out :-) I've tested it in maya and everything works fine on my Intuos 3, even the little zoom strip thingie :)

Ive attatched my xorg.conf for reference.

---

### Post by samba on 2006-11-16
By express keys I suppose you mean the buttons next to the screen on a tablet, right? Do you think if that expresskeys package should work on other tablet PCs? I have a Toshiba Portege m405 tablet PC, and I would love to get these keys working... :-)

Thanks
vincent

---

### Post by jujoje on 2006-11-16
yeah the buttons next to the tablet (the zoom bar and other 4 buttons on the wacom tablet). Unfortunately the expresskeys programme is, from what I can tell from the web site, only for wacom tablets, and only specific tablets at that.

To get the keys working I guess you'll have to find out the key codes for the keys and then map them. There's an entry on the wiki for it:
 [https://help.ubuntu.com/community/MultimediaKeys]("https://help.ubuntu.com/community/MultimediaKeys")

Sorry I couldn't be more help,

Julian

---

### Post by samba on 2006-11-16
Well the problem is that the keys are somehow recognized by gnome-keybindings-properties, so in principle I can set them up using Deskto->Preferences->Keyboard Shortcuts . But in practice, the most important key is the little "joystick" next to the screen that one can use to scroll up and down when reading in tablet mode. But from the Keyboard Shortcuts it looks like I can't assign such a shortcut to this express key. So I don't really know what to do... :confused: Anyone?

vincent

---

