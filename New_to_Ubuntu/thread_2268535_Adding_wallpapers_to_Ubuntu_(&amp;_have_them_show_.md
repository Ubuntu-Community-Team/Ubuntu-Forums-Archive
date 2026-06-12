---
title: "Adding wallpapers to Ubuntu (&amp; have them show in selections)"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by Geoffrey_Arndt on 2015-03-09
I pasted the new Vivid wallpapers from Launchpad to /usr/share/backgrounds, (using gksu nautilus) and they are available in that folder BUT they won't display or show-up at all in the "Change Desktop Background" window.   

If I use the files manager, I can select any photo and set it as wallpaper, but it seems simpler to do using the built-in desktop tool provided by Ubuntu (via right-clicking the desktop IOW).

Any tips appreciated.

Geoffrey

---

### Post by nerdtron on 2015-03-10
Are you sure the default backgrounds are on that folder? 
I'm on xubuntu and the default backgrounds are on /usr/share/xfce4/backgrounds 
And also you can select a folder you want on the change wallpaper screen and all images on that folder should show up.

---

### Post by sotiris2 on 2015-03-10
From the second answer [here]("http://askubuntu.com/questions/272058/where-are-the-unity-desktop-wallpapers-located") 

> At the Appearence window there's a dropdown. When you select Wallpapers the images shown are get from the XML files in /usr/share/gnome-background-properties/. If you just drop files in /usr/share/backgrounds they will not be available for selection in that area.

Open /usr/share/gnome-background-properties/trusty-wallpapers.xml  (for 14.04) with a text editor and add entries there ( use previous entries as an example)

---

### Post by grahammechanical on 2015-03-10
There are three components to wallpapers in Ubuntu

1) The images and they are in /usr/share/backgrounds/
2) An xml file in /usr/share/gnome-background-properties that will be called vivid-wallpapers.xml or a similar name based on the Ubuntu release code name - utopic, trusty, etc.
3) An xml file in /usr/share/backgrounds/contest that works the slide show and will be called vivid.xml or a similar name based on the Ubuntu release code name - utopic, trusty, etc.

If we copy those files from an earlier release to a newer release and we put them in the right folders we will get more wallpapers and another slide show. This vivid wallpaper package that you downloaded as a zip file did it just contain the images or did it also contain those two xml files? 

There is nothing stopping us copying and editing the existing xml files and giving them new names. I have done this and it works. There is one thing to watch out for. Gedit will make back up copies of these files that will be hidden files but they will still be read by the OS causing duplicates to appear in the appearance utility. These backup file will be prefixed by the tilde ( ~) character.

Regards.

---

### Post by deadflowr on 2015-03-10
I would have simply extracted them into my home folder for now, and waited until the ubuntu-wallpapers-vivid package is released in a few days time.
If you extracted them into the /usr/share locations, both the backgrounds folder and the .xml files location, then when the update with the new wallpapers comes, it'll add more entries to the folder where the xml file is (by adding a new .xml file), adding duplicate entries of selectable images in the Appearance section.
Of course, though, maybe I am assuming you are trying to run vivid...

---

### Post by JeQhdMD on 2015-03-10
OK, I have a similar situation, and couldn't recall how to fix it.   This looks like the right solution.

[COLOR=#000000]Edit:  updating the xml file worked perfect . . . perhaps this thread will help others who want the default wallpapers expanded in the selection window (without navigating to other folders).


[/COLOR]

---

