---
title: "Other hard drive folders on desktop?"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by baker-quin on 2013-08-28
I'm using 12.04 and when I mount my other drive it only shows up on the launcher. I would like to put it on the Desktop but I don't see any way. I would also like to make folders on the desktop that is linked to the other hard drive that does not have linux installed on it. I have it so I can share files between Linux and Windows in my dual boot. 
       So, question 1: How do I get my other drive to be an icon on the desktop when mounted?

From what I can tell I would have to have it be a link type thing on the desktop so the storage is not on my linux drive. I'm not even sure if it's possible. 
      And question 2: Can I make folder/link to folders in my other drive on my linux desktop for shortcuts without the data being on the linux drive and how?

---

### Post by dhunt84971 on 2013-08-28
Did you try using the File Browser and then right-clicking on the folder, clicking on Make Link and then dragging the link onto your desktop?

---

### Post by deadflowr on 2013-08-28
If on 12.04, install myunity.
```
sudo apt-get install myunity
```
or just install from the software center.

Then launch it and go to desktop.
You can have your home folder and other "devices" show up on the desktop.

---

### Post by Frogs Hair on 2013-08-28
MyUnity has been removed from the repository since the first release of 12.04 . It can be built from a tar.gz though. The Gnome Tweak Tool has a show mounted volumes setting. 


    [https://launchpad.net/myunity](https://launchpad.net/myunity)

---

### Post by SweetAurora on 2013-08-28
install this:
```
sudo apt-get install gconf-editor dconf-editor
```
Open dconf-editor and navigate the menus as follows org<gnome<nautilus<desktop. Now tick the "volumes-visable" checkbox and close.

Edit: I misspelled "editor" ::redface:: try the command again if it failed before.

---

### Post by deadflowr on 2013-08-28
> **Frogs Hair said:**
> MyUnity has been removed from the repository since the first release of 12.04 . It can be built from a tar.gz though. The Gnome Tweak Tool has a show mounted volumes setting. 


    [https://launchpad.net/myunity](https://launchpad.net/myunity)

Only if they pulled it within the last two weeks, as I did a fresh install of precise two weeks ago and myunity was still there then.

---

### Post by baker-quin on 2013-08-29
Okay, I just installed unity using the code: sudo apt-get install myunity and it is working well. I am now able to see the device on the desktop. This was very helpful. Thank you.

Now for the second question: 

@dhunt: yes, I did try to [COLOR=#000000]use the File Browser and then right-click on the folder, click on Make Link and then dragging the link onto your desktop but this didn't appear to work as after clicking on the folder following this process it reads: location as, "[/COLOR]/home/quinton/Desktop" yet wait... maybe I was just reading it incorrectly. I see it saying Link target /media/5CAF52E16359F4C9/torrentdownloads. 5CAF52E16359F4C9 being the mounted device. It also shows the correct amount of free space. So yes, my bad this does work.

Side question: How would I change the name on the mounted device 5CAF52E16359F4C9? This is all from my one harddrive partitioned for dual boot windows and linux with space for both to access.

---

### Post by Frogs Hair on 2013-08-29
> **deadflowr said:**
> Only if they pulled it within the last two weeks, as I did a fresh install of precise two weeks ago and myunity was still there then.

Whoops! You are correct it was 12.10 and it has come back for that release. 
[https://apps.ubuntu.com/cat/applications/precise/myunity/](https://apps.ubuntu.com/cat/applications/precise/myunity/)

---

### Post by oldfred on 2013-08-29
I like to label every partition. Then a default mount uses the label instead of UUID.

I normally try to remember to label when I create partitions with gparted, but when I forget use Disk Utility or Disks in new versions. I have not done it with Disks yet as they moved some things around. 

And new gpt partitioned drives can have two labels. One for partition and one for gpt partition. I think the gpt one is not normally used, but I label both.

---

