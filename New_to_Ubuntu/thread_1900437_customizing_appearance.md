---
title: "customizing appearance"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by DGINSD on 2011-12-26
Clicking on appearance in system settings pulls up a window that doesn't allow you to change much, less than 11.04 and way less than 10.10. Am I missing something here, one of the things I liked about using ubuntu was how much you could make your interface your own. I like the unity interface and am getting use to it but being able to put in your own icons at least would be nice, does anyone know of a way to do this? Have I simply overlooked something?

---

### Post by Frogs Hair on 2011-12-26
See the link for help with theme / icon  installation . [http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml)

---

### Post by BC59 on 2011-12-26
> **DGINSD said:**
> Clicking on appearance in system settings pulls up a window that doesn't allow you to change much, less than 11.04 and way less than 10.10. Am I missing something here, one of the things I liked about using ubuntu was how much you could make your interface your own. I like the unity interface and am getting use to it but being able to put in your own icons at least would be nice, does anyone know of a way to do this? Have I simply overlooked something?

There are 2 major tools of tweaking Unity. Unfortunately they are not installed from the box. You have to install them through Ubuntu Software Center:
Advanced Settings (or Gnome Tweak Tool)
and Compiz Config Settings Manager (you can tweak Unity from the Unity plugin)

---

### Post by DGINSD on 2011-12-26
The advance settings helped a little, How can I install my own icons where do I place the folder? How do I make the side and icons in it smaller, when I see screen shots of other peoples set up it looks a lot smaller?

---

### Post by BC59 on 2011-12-26
To install new icons, themes, fonts, just create those three folders in home. So you have to create .fonts .icons .themes
The dot in front makes them hidden and to see them you have to press CTRL+H.
After this you search for new themes and icons. The best place is Devian Art [http://hhhorb.deviantart.com/](http://hhhorb.deviantart.com/)
or here [http://art.gnome.org/](http://art.gnome.org/)
A very good theme is here:
[http://www.webupd8.org/2011/12/executive-beautiful-theme-pack-with.html](http://www.webupd8.org/2011/12/executive-beautiful-theme-pack-with.html)
When you download the theme, open the zipped file and copy the ingredients inside the corresponding folder, e.g. themes or icons.
Now to use it you have to open Advanced Settings and choose your theme.
To change the icon size on Unity, open Compiz Config--Ubuntu Unity Plugin--Experimental--Launcher Icon Size, set it to 32 it's the smaller.

---

### Post by Frogs Hair on 2011-12-26
You will have to create a .themes and .icons folder in home hidden folders or install in usr/share/icons or themes .

If using file stytem user/share/themes or icons use gksudo nautilus in the terminal so you have permission to move items into folders in the file system .

---

### Post by DGINSD on 2011-12-26
Excellent thank you so much. How can one determine the names of various icons, for example the icon in the top right corner of the default unity desktop what would I need to name an icon for it to be used there? There use to be a site that gave instructions for putting together an icon theme and all the names of everything but I put the one I use together in 10.10 so I'm sure a lot has changed, the fact that some of my icons have changed and others haven't guarantees they have :D

---

### Post by Frogs Hair on 2011-12-26
Icon sets are set up differently so there is no single rule that works with every set . You can learn where the icons are located by looking in the folders. Things like battery and network are often filed under status .

---

### Post by lolpenguin on 2011-12-26
Basically, you put icons and cursors in ~/.icons/ and themes in ~/.themes, or if you need to, /usr/share/icons/ and /usr/share/themes/.

---

### Post by bodhi.zazen on 2011-12-27
> **lolpenguin said:**
> Basically, you put icons and cursors in ~/.icons/ and themes in ~/.themes, or if you need to, /usr/share/icons/ and /usr/share/themes/.

both locations will work

~/.icons and ~/.themes are per user

If you have root access, and you want the themes / icons to be available to all users, the "best practice" would be to put them in /usr/share/themes and /usr/share/icons .

Yes you can share ~ , but some people use more private settings or an encrypted home, so ~/.icons are not as reliable as /usr/share/icons

---

### Post by DGINSD on 2011-12-27
Thank you all things are lookin much better. The change icon size in CCSM Unity plug in isn't working, my graphics chip is an older one that doesn't support Opengl 1.3 so I'm running unity 2D I think, is there another way to change the size, Gconf editor perhaps, or changing the icon sizes that are being pulled to use in the launcher?

---

### Post by Frogs Hair on 2011-12-27
This application will give you some more settings options in Unity 2D . [http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/)

---

### Post by DGINSD on 2011-12-27
Great, I,ll give it a whirl tonight thanks for the tip. 
Have there been many instances of malicious content from PPA's?

---

### Post by Frogs Hair on 2011-12-27
> **DGINSD said:**
> Great, I,ll give it a whirl tonight thanks for the tip. 
Have there been many instances of malicious content from PPA's?

I have never had any problem with content at Launch Pad . I would be using that application if I only had Unity 2D .

---

### Post by DGINSD on 2011-12-27
Do you happen to know what the purpose of the new compiz requiring OpenGL 1.3? Cause all my graphics extras worked great in 10.10 but now I'm pretty limited. I wonder how hard it would of been to have an older version of comiz that used 1.2 for us folks with beat up old machines.

---

### Post by DGINSD on 2011-12-27
Strangely the "My Unity" application isn't working to change the launcher icon sizes either? In fact none of the items seem to change anything, I gotta be doing something wrong, no?

---

