---
title: "Success!!! and a couple of questions"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Darbre on 2008-07-16
Hi fellas. 

This is a First Post "Howdy". And a question. First of all, I installed Ubuntu last night on an older Dell laptop. I'm getting so tired of Windows, and I had this notebook lying around and took the plunge.To say that I'm a little confused right now would be an understatement. But I'll figure it out. This forum is an amazing place. 

Anyway, my install went much better than I thought it would. I had problems with my Broadcom wireless adapter, got that ironed out. Installed my HP network printer. Screen resolution is good. All the things that I read about didn't happen. All is good right now. One question though. (Well, maybe several:) ) 

How does Ubunto interact with Windows Shares? I had no problem finding my 2 NAS drives in Ubuntu, had no problems playing MP3's that were on the shares. However after some period of time, the NAS's were no long accessible. They had disappeared. To get to them, I opened....some app (sorry), clicked the Network icon on the left side of the window. This opened my network. Clicked on my network, and the names of the NAS drives came up, clicked on the NAS drive icon and got in with not problem. Sometime later, that album has finished and I wanted to start another one. This time when I clicked on the Ubuntu network icon nothing happened. Ubuntu couldn't find my network. Internet access still worked, but my internal network was gone. Rebooted Ubuntu and all was well again. 


Having to reboot when silly s**t happened was one thing that I really wanted to leave behind. Any clue about why Ubuntu refused to "see" my network?

Do I have to do anything special to save a file from Ubuntu to the NAS drive?

Is there a Ubuntu equivalent to Device Manager? I don't find anything.

Thanks

dkilleen

---

### Post by carandraug on 2008-07-16
Welcome to Ubuntu dkillen. I hope you enjoy your stay here.> **Darbre said:**
> Is there a Ubuntu equivalent to Device Manager? I don't find anything
Ope the terminal and enter```
lshw
```which comes from "LiSt HardWare" (makes it easier to remember).

I looked for a graphical interface of it but I couldn't find it. I'm pretty sure there was one at least in Ubuntu 7.10 but they probably removed it or placed it somewhere else.

---

### Post by a0u on 2008-07-16
In Hardy, gnome-device-manager replaces hal-device-manager.

To install via the repos, open the terminal (Applications > Accessories) and enter:
```
sudo apt-get install gnome-device-manager
```This will give you a GUI frontend.  It should be accessible in the System > Management menu.  If not, launch it with ```
sudo gnome-device-manager
```

I hope you are enjoying Ubuntu! :)

---

### Post by Darbre on 2008-07-18
Ok, great. That worked. But it also brings up another problem I've been having. I had to use the second command to start the program. No entry was made in System menu. How do I add the program to the menu?

Thanks

---

### Post by hyper_ch on 2008-07-18
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by nothingspecial on 2008-07-18
To start things at boot go to system > preferences > sessions.
Click add
Fill in the boxes
Done

---

### Post by a0u on 2008-07-19
> **Darbre said:**
> Ok, great. That worked. But it also brings up another problem I've been having. I had to use the second command to start the program. No entry was made in System menu. How do I add the program to the menu?

Thanks
For some reason, the menu entry configuration file has a mistake. Open gedit or some other text editor:
```
gksu gedit /usr/share/applications/gnome-device-manager.desktop
```Copy and paste the following text over the existing content, and then save the file:
```

[Desktop Entry]
Encoding=UTF-8
Name=Device Manager
Comment=Manage devices
Exec=gnome-device-manager
Icon=gnome-device-manager
Terminal=false
Type=Application
X-GNOME-DocPath=gnome-device-manager/gnome-device-manager.xml
Categories=GNOME;GTK;System;Settings;

X-Ubuntu-Gettext-Domain=gnome-device-manager
```
The crucial addition is appending "Settings;" to "Categories".  You should now be able to access Device Manager under "System > Administration".  If you still don't get a proper entry, I suggest you reinstall just to make sure all the files are in the right locations.

There's also a GUI menu editor at System > Preferences > Main Menu in case you need to create custom entries.

---

