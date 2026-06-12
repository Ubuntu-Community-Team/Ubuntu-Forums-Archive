---
title: "Blurred text after reboot, NVidia and others."
date: 2008-09-13
forum: New to Ubuntu
---

### Post by The_Marlboro_Man on 2008-09-13
Hello!.

I just came with this problem today:

Let's see, I have this Belkin wireless adapter that always keeps on disconnecting when working with Ubuntu. No big deal and not the subject for this topic: most times I can just unplug and plug it and it will keep connected for a little while... But well, sometimes I am just forced to reboot.

I did that today and when the login screen should appear I saw a message of "Input not supported" at my Acer 1916W monitor. After doing my research I found out it had something to do with the video system so I tried "sudo dpkg-reconfigure xserver-xorg" and after a couple of tries I got it working again... Mostly.

It took a while to find the correct resolution and when I found it I could see that all text was blurry: in web sites, in applications, in taskbars, in the desktop, all text. I tried different resolutions and messing with the fonts dialog to no avail. Since I had installed compiz-fusion (but had disabled it) I tried to uninstall it with no results. What seemed to work was to disable the restricted controller for my NVidia GForce 7400...

So, well, without the controller I can see regular text but once I install it again all text becomes blurry. I would like to be able to have the controller installed in case I want to mess with 3d applications but I can't without being unable to read the text on screen. I would also swear that since I disabled the controller there's a certain amount of "overdraw" when opening, closing and moving windows around.

Any ideas or hints?. Thanks a lot in advance.

Edit: Just remembered, I am using Ubuntu 7.10 here.
Edit 2: I also remembered: since disabling the controller I have experienced certain problems with missing window frames (title, minimize, maximize and close buttons missing along with its bar, as happens with certain problems with compiz).

---

### Post by aimpau on 2008-09-13
For all of your Nvidia needs, open a terminal and type:
```

sudo apt-get install envyng-gtk

```

After the installation, it will appear in your systems menu.

---

### Post by bumanie on 2008-09-13
Try this code in terminal. I know it often fixes nvidia cards that are not showing minimize/maximize buttons etc on the windows. > sudo nvidia-xconfig --add-argb-glx-visuals -d 24


---

### Post by The_Marlboro_Man on 2008-09-15
Thanks a lot to both: the "envy" thing solved my problems but the hardest part was to get it: couldn´t find it through Synaptics at all but once I got it running it was smooth :).

Now the open question would be "Why does that happen?". My Ubuntu has been stable since I installed it with little problems here or there, but nothing like that.

Again, thanks a lot :).

---

