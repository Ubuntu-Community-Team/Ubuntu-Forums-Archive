---
title: "Google Earth Problem"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by kolhoznik on 2008-08-16
I am having trouble installing the Google Earth for Linux.  When I tried to open the file it gave this message.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Any ideas?

Thanks.

---

### Post by jualin on 2008-08-16
Why are you trying to open Google earth with Gedit? After you download Google earth navigate to that directory using the terminal and then execute the installer using > sh GoogleEarthLinux.bin. You can also follow [this guide]("http://ubuntuforums.org/showthread.php?t=195382"). Good luck!

---

### Post by drs305 on 2008-08-16
You should be able to install GoogleEarth via synaptic.

For Hardy:

If you haven't already, enable the Medibuntu Repository from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Install Google Earth (this is a metapackage, no version number required. current version 4.3):
```
sudo apt-get install googleearth
```

---

### Post by nicedude on 2008-08-16
You should first install the Medibuntu repositories and then install google earth from there, works great for me :-)

You can just google Medibuntu and their homepage has good directions for how to do this. This is where you can also download all the codecs you need to watch avi's and the libdvdcss library to decode DVD's with.

hope this helps

DRS you beat me to the punch LOL

---

### Post by kolhoznik on 2008-08-16
I tried to follow the directions in the guide and got this response in the terminal.

HTTP request sent, awaiting response... 404 Not Found
19:39:17 ERROR 404: Not Found.

---

### Post by jualin on 2008-08-16
Sorry about that, the link was dead. Try this one, I can confirm is working 
[HTML]wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin[/HTML]

---

### Post by kolhoznik on 2008-08-16
Ok, I have installed Google Earth but now when I try to open it, it logs me out of Ubuntu.  Any ideas why?

---

### Post by jualin on 2008-08-16
Can you describe the "logging you out situation" a little more detailed. Does it restart your computer, or does it take you to the Login window?

---

### Post by kolhoznik on 2008-08-16
It restarts where I have to retype my username and password to get back to desktop.

---

### Post by jualin on 2008-08-16
In that case I would suggest you to uninstall Google Earth following [this link]("http://ubuntuforums.org/showthread.php?t=208254"). And then install the latest Google Earth (beta version) typing this on the terminal 

wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin) 
sh GoogleEarthLinux.bin

If this doesn't work I suggest you to try the medibuntu method.

---

### Post by kolhoznik on 2008-08-16
It takes me to the log in window.

---

### Post by kolhoznik on 2008-08-16
I am having trouble with the uninstall.  Sorry with a noob question, could someone walk me though this?

---

### Post by jualin on 2008-08-16
No problem just follow [this link]("http://ubuntuforums.org/showthread.php?t=208254"). And feel free to ask if you get stuck

---

### Post by kolhoznik on 2008-08-16
I am having trouble with how to wipe a directory.

---

### Post by nicedude on 2008-08-16
Just install Google Earth via Medibuntu if you want it to work, it is as simple as it gets in life.

---

### Post by kolhoznik on 2008-08-16
This will reveal how new I am: How do I find Medibuntu?

---

### Post by nicedude on 2008-08-16
This page will explain what you need to do and how to do it. This will add all the medibuntu sources to your synaptic sources. This is a needed bunch of stuff contained in the medibuntu repositories.


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Go here and read what to do.

---

### Post by drs305 on 2008-08-16
> **kolhoznik said:**
> This will reveal how new I am: How do I find Medibuntu?

Go back to post #3.  ;-)

---

### Post by kolhoznik on 2008-08-16
ok, I followed those instructions and got a box with the user rules for Google Earth.  It had an ok button at the bottom that did nothing.  I also have not uninstalled the other download of Google Earth from earlier.  I have an icon on my desktop that still takes me back to the login screen.  Any ideas?

---

### Post by drs305 on 2008-08-16
> **kolhoznik said:**
> ok, I followed those instructions and got a box with the user rules for Google Earth.  It had an ok button at the bottom that did nothing.  

If I remember correctly, at that point I think you have to use the tab key to move the cursor to highlight OK and then hit Enter. It's been a while ...

---

### Post by kolhoznik on 2008-08-16
Ok, that worked with the Tab key.  Now when I still open it, I am kicked back.  Should I uninstall the old Google Earth 1st?

---

### Post by drs305 on 2008-08-16
> **kolhoznik said:**
> Ok, that worked with the Tab key.  Now when I still open it, I am kicked back.  Should I uninstall the old Google Earth 1st?

Yes. Did you first try to install it with a bin file? If so, there should be a folder that was created during the install. Within it should be an uninstall script or something that will uninstall it.

Synaptic doesn't track apps not installed via bin or rpm files, but you could run this just to make sure:
```
sudo apt-get purge googleearth
```

I'm leaving my computer, so I'll have to just wish you good luck from here. :-)

---

