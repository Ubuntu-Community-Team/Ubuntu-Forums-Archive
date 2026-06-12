---
title: "modifying a GTK theme"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-10-22
hi everyone.i wanted to know if a GTK 2.x theme could be modified.an emerald theme can easily be modified in the emerald theme manager.but,is there a way to modify a GTK theme.presently,i am using a GTK theme called "future" which i got from gnome-look.org.and that looks pretty good to me as is clear from the screenshot.but i would like the taskbar to be glossy red,as is seen in the other screenshot,making this modification in the theme future itself retaining its other features.is this possible?

---

### Post by eternalnewbee on 2008-10-22
Shouldn't you be able to do that in Appearance > Customize?

---

### Post by stonecoldjha on 2008-10-22
nope,it can't be done that way.

---

### Post by stonecoldjha on 2008-10-22
isn't there a way out?

---

### Post by NilsE on 2008-10-22
Look in the folder where the theme is installed.  Depending on how you installed it it will be in a folder called themes in either your home folder or /usr/share/.  The folder within themes will have the name of the theme.

Then look through the graphics and see if there is one that has panel in the name or at least looks like a panel graphic.  Once you find the graphic name look in the gtkrc file and you will find where the graphic is used.  If it not a graphic look for the panel section of the gtkrc file and there you can tinker with the color choices which would be in hex.  More than likely it is a graphic which you can change or replace with anything you want of the same height and width. 

Do the same with the buttons.

Good luck

---

### Post by stonecoldjha on 2008-10-22
thank you very much,i got it done doing what you said.one more thing,i am using the hydroxygen iconset,i would like to modify a few of its buttons,like,the navigation buttons(up,back,foreward,etc.)how do i do that?

---

### Post by NilsE on 2008-10-22
> **stonecoldjha said:**
> thank you very much,i got it done doing what you said.one more thing,i am using the hydroxygen iconset,i would like to modify a few of its buttons,like,the navigation buttons(up,back,foreward,etc.)how do i do that?
Icon themes are in the same paths in a folder called icons.  Go to the icon set you are using and find the old ones that you want to change.  

They are called:

gtk-go-back, gtk-go-forward, gtk-goto-top, gtk-go-down and a few others starting with gtk-go

Once you are in the folder you can start looking in the scalable folder first then 24x24 then sub folder actions

Just replace the ones you want with ones of the same size.

---

