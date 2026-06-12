---
title: "Xfce and Gnome"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-06-26
Hi all,

I'm using XFCE desktop as my primary desktop interface, but its default browser doesn't allow me to access Windows share **easily** like Nautilus does by using "smb://LAN_IP" in the browser. 

Since I'm lazy ( :D ) and I don't know much about making Thunar to work with shares, I just install Nautilus alone in order to access Windows shares from other PCs in the LAN. But I reckon there's some conflict between these two, especially when I copy from USB flash, drivers etc. At that time, all the icons (folders, files) on the desktop disappear, I cannot do anything with the desktop but I still can use the PC normally (surf, listen to music etc). 
*EDIT*: The copy process still carry on but when it's done, the icons still don't come back.

This problem can be solved by restarting the computer, but then again, when I plug in the USB driver, this tends to happen again and it's really bugging me to have to restart the PC in order to get the icons back on desktop.

Does anyone know how to solve this problem properly?
Thanks in advance :D

---

### Post by Dani Filth on 2008-06-26
Anyone?

---

### Post by dizee on 2008-06-27
I haven't heard of thunar and nautilus conflicting with each other like that before. Try running ```
nautilus --no-desktop
``` when you use it and see if that helps.

if there's still problems you could try using konqueror to access your shares instead, or setup thunar to do it [http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

---

### Post by Dani Filth on 2008-06-27
Hi dizee, thanks for your reply!

Do you mean I should Alt+F2 or open a terminal and type "nautilus --no-desktop" when the problem (no icons on desktop) occurs? 
Or whenever I wanna access Windows shares from the LAN via Nautilus then I need to do like that? (In fact, after installing Nautilus, it seems like the default browser is Nautilus instead of Thunar, because I double-click a folder on the desktop and its "Help/About" says that's Nautilus)

I've seen that method to make Thunar to work with shares before but as I said, I'm too lazy :P. But now if I can't solve this, maybe I will do as the instruction. In this case, I want to ask if I follow that topic, do I have to change the workgroup everytime I want to mount/access Windows shares? (You know, some people use "MSHOME" as their workgroup, some use "WORKGROUP")

Cheers! :D

---

### Post by dizee on 2008-06-28
i mean whenever you need to run nautilus to access your shares, use the "nautilus --nodesktop" command. might be a good idea to add an application launcher with this. i think nautilus is trying to take over, this should stop it misbehaving ;)

is the default browser always nautilus?  even when you restart? if so go to the menu, click on Settings and then open the Settings Manager. go to Desktop and make sure the box "Allow Xfce to manage the desktop" is ticked.

---

### Post by jw5801 on 2008-06-28
It's not nautilus and Thunar 'conflicting' per se. But whenever you run nautilus it insists on controlling the desktop, unless you specifically tell it not to. Short answer, don't use nautilus, long answer start it with 'nautilus --no-desktop'. You can even alias 'nautilus' to 'nautilus --no-desktop' if you so choose, that way all your menu items will obey as well.

---

