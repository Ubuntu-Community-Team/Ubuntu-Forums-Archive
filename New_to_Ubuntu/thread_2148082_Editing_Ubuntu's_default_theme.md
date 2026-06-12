---
title: "Editing Ubuntu's default theme?"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by czgirb on 2013-05-23
As title.
Currently I'm using 12.04 Pangolin and I like the **Ambience** theme.
But I do hope to make the **Bar** and **Window's frame** to be an **absolutely black**
Is there anyway to do that?
Please guide me or show me the URL ... thank you.

**PS:**
**12.04 Pangolin** is the first Ubuntu that I used more than 5 months
Previously, I'm with **10.04 Lucid** ... but it was last not more than 1 month.

---

### Post by deadflowr on 2013-05-23
The themes are located in /usr/share/themes folder.

I think that stuff is in the metacity folder.

You can install gimp and then deepen the blackness for all the many images you want.

There are usually a ton of images.

Good luck

I would copy the theme into a place in my home folder, so I wouldn't have to be in root the whole time, do my editings and copy the theme back into the theme folder (as root).
I'd also rename the new theme folder something else. Doesn't matter what.

---

### Post by Dennis N on 2013-05-23
This may be helpful:

[http://askubuntu.com/questions/136044/how-do-i-change-the-background-color-of-the-menu-bar](http://askubuntu.com/questions/136044/how-do-i-change-the-background-color-of-the-menu-bar)

---

### Post by czgirb on 2013-05-24
**@ deadflowr**

GIMP ... I have it already

> ... and copy the theme back into the theme folder (as root)
To be a root, what should I do???
*** SORRY ... SOLVED already

**@DennisN**

Thank you very much for the guidance ...

---

### Post by czgirb on 2013-05-24
**@ deadflowr**

Would you ind to guide me how to get into** /usr/share/themes** folder?
And I unable to reach **the metacity** folder, a folder that you mentioned in my Pangolin

---

### Post by Frogs Hair on 2013-05-24
To change file content in the file system you need to open nautilus as root. ```
gksudo nautilus
```   

The path in 12.04 as I remember is File System > usr > share > themes > ambiance > matacity.  

You may want to give these themes a try.   [http://gnome-look.org/content/show.php/TLS?content=152961](http://gnome-look.org/content/show.php/TLS?content=152961)

[http://gnome-look.org/content/show.php/Bambiance?content=152943](http://gnome-look.org/content/show.php/Bambiance?content=152943)

---

### Post by czgirb on 2013-05-24
> **Frogs Hair said:**
> To change file content in the file system you need to open nautilus as root. ```
gksudo nautilus
```   

The path in 12.04 as I remember is File System > usr > share > themes > ambiance > matacity.  

You may want to give these themes a try.   [http://gnome-look.org/content/show.php/TLS?content=152961](http://gnome-look.org/content/show.php/TLS?content=152961)

[http://gnome-look.org/content/show.php/Bambiance?content=152943](http://gnome-look.org/content/show.php/Bambiance?content=152943)

Thank you for the guidance ...
And thank you also for the recommendation themes ... I love it and used **Bambiance** now

---

### Post by deadflowr on 2013-05-24
> **czgirb said:**
> **@ deadflowr**

Would you ind to guide me how to get into** /usr/share/themes** folder?
And I unable to reach **the metacity** folder, a folder that you mentioned in my Pangolin

Open nautilus and go to the file system sidebar option.
Then go to usr, then to share, then to themes, then to the theme you want.
Typically, the theme folder will have 3, or 4 folders and an index file.
The folders will be gtk-2.0, gtk03.0, metacity-?, unity(if a unity built theme)
the metacity folder is the metacity folder.
The metacity folder contains all the border files.

Some theme folders will only have a metacity folder, or a gtk-# folder and an index file.
If you look in the index file, in it there will be a list of the parts it uses. 
like this from highcontrastinverse
```
GtkTheme=HighContrastInverse
MetacityTheme=Adwaita
IconTheme=gnome
CursorTheme=Adwaita
CursorSize=24
``` 

Even though highcontrastinverse only has two folders for gtk-2.0 and gtk-3.0.
The index points out that it uses the adwaita metacitytheme.

Don't know if me ramblings make sense, but somehow it does to me.

Added: Of course the best thing to do is to copy the them and/or parts you want to play around with into the users hidden theme folder
/home/user/.themes.
Then you can play around and tweak it as you want.
Since it's in a themes folder, you'll be able to try it out.
Without having to move it back into the system folder /usr.

But, have fun. Play around, figure out what parts do what.
Once you know where the themes are, it's up to you to dewcide what you want.

---

### Post by czgirb on 2013-06-01
I copied a folder named **Ambiance** and placed in **Downloads**.
Within the folder, there are 4-folder (**gtk-2.0**, **gtk-3.0**, **metacity-1**, **unity**) and 1-file (**index.theme**)
I opened the **metacity-1** folder, as the given instruction ... but found **no** word incld. **frame**.
All is the **X** (**exit/closed**) or **Box** (**Maximized**) and** line **(**minimized**) sign.

The only differ are 3-file named:
> 
trough_unfocused_left.png
trough_unfocused_middle.png
trough_unfocused_right.png


Are they the files that I should edit?

---

### Post by deadflowr on 2013-06-01
> **czgirb said:**
> I copied a folder named **Ambiance** and placed in **Downloads**.
Within the folder, there are 4-folder (**gtk-2.0**, **gtk-3.0**, **metacity-1**, **unity**) and 1-file (**index.theme**)
I opened the **metacity-1** folder, as the given instruction ... but found **no** word incld. **frame**.
All is the **X** (**exit/closed**) or **Box** (**Maximized**) and** line **(**minimized**) sign.

The only differ are 3-file named:


Are they the files that I should edit?

No, those are just for the buttons.

Unfortunately, unlike other themes, which I've experienced tweaking, ambiance uses a different way, where as instead of actual png files for all the various pieces, all the frames and such are written to the metacity.xml file in the metacity folder.
If you study that file, you might figure out what part is what.

---

