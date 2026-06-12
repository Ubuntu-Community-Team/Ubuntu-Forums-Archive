---
title: "icon creation program"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by nynoah on 2008-11-26
I have a whole bunch of themes that I have on my computer.  I want to take some icons from all the different ones and make a theme that is my own.  Is there a program that lets me do that.  Or does anyone know where a tutorial is on the net?

Thanks

---

### Post by gjoellee on 2008-11-26
I dont know about some software made for making icons only, but you can make icons using GIMP or Photoshop

---

### Post by nynoah on 2008-11-26
well I really don't want to create my own icons.  I have several themes from Gnome look that I want to combine to make a really good one.

---

### Post by fenian on 2008-11-26
I don't know of any programs hat would dmake them automatically but there is a rough guide on making Gnme Icon themes [here]("http://live.gnome.org/GnomeArt/Tutorials/IconThemes").In the past I have copied a them folder to my home directory and manually replaced the icons this is rather time consuming but it works.

---

### Post by nynoah on 2008-11-26
I planned on doing a lot of copying I figured it would take a long time no matter what.  But I just noticed there were some things inside of the packages when I unpacked them.  Things like "installing before read" files and "customizing instructions" which neither of which I can open up to figure out what it says in them.

---

### Post by JohnLM_the_Ghost on 2008-11-26
In simple icon them is a folder of icons...
go see /usr/share/icons/ and ~/.icons
make (or copy) a folder and put all your icons there
there is also index.theme file, what changes settings for theme
it can't be edited by gedit, though you should use nano (in terminal) for that

---

### Post by nynoah on 2008-11-26
what I am hoping to make is a "super" icon theme that I could share with the community on Gnome look.  I will try to give all credit.  I just see so many good icons out there and just want to cherry pick the ones that look the best to make a really great looking theme package.  So I have to be able to make a tar.gz file out of it after that will work for others.

---

### Post by JohnLM_the_Ghost on 2008-11-26
Go for it!
I also tried to make a few themes like that, but nothing spectacular.
You may check [gnome-look.org]("http://gnome-look.org/") for nice icons.

---

### Post by nynoah on 2008-11-26
Yeah it will be a lot of copying.  But I am sure it is still WAY less time than creating them.  I just hope I can do this right.  LOL  But there is only one way to learn.

---

### Post by nynoah on 2008-11-26
I notice that some of my icon themes have scalable stuff and some have stuff with actually dimensions like "128x128".  what should I do to bridge that gap.  Should I take the largest icon and drop that into the scalable file from the one that I am using as a basis.  I figure doing scalable would be easier.  Less work.  Am I thinking right or am I wrong?

---

### Post by JohnLM_the_Ghost on 2008-11-26
Well I think you should copy available variants. Or at least largest or scalable one.
Then optionally you can resize largest to sizes you think would be most used. You don't have to make all sizes. Gnome should use and resize the missing sizes if required. (of course it doesn't save those)

Oh yes! .svg always goes to scalable, and .png goes to whatever size it is. I think that's pretty obvious.

---

### Post by nynoah on 2008-11-26
what does it mean when there is a little arrow in the corner of the pic.  and how do I add that to some of the icons that do not have it?

---

### Post by nynoah on 2008-11-26
Also when I try to open up Icons with Gimp, it does not open up the correct Icon.  It chooses another from some other place.  What?

---

### Post by Bölvaður on 2008-11-26
The arrow you are talking about is a link to a different file (you will discover that if you would check the files properties and see where it is pointing). This is often done to safe space, as links take less space than images. So when you have an icon that is needed for multiple instances, you would use links.

Also you might want to check out /home/user/.icons/gnome-wine/**index.theme** as that file contains what directories are used for icons, very useful I would think.

Btw in the future if you are going to try make your own icon try inkscape.

---

### Post by CatKiller on 2008-11-26
> **nynoah said:**
> I notice that some of my icon themes have scalable stuff and some have stuff with actually dimensions like "128x128".  what should I do to bridge that gap.  Should I take the largest icon and drop that into the scalable file from the one that I am using as a basis.  I figure doing scalable would be easier.  Less work.  Am I thinking right or am I wrong?

The scalable icons are [SVG]("http://en.wikipedia.org/wiki/SVG") files. These are not the same as image files as you might imagine them; they can be displayed at any size without a loss of detail because they are really definitions of regions. There is a slight performance penalty to using scalable icons, but in many cases this is compensated for by their utility for different size displays and flexibility in being used for many parts of the interface.

Some icons, especially "busy" ones with lots of information crammed into a small area, are difficult to discern at smaller sizes. In these cases, a simpler icon is used - generally this has been especially crafted to show the important aspects of the image such as shape and colour, without much by way of embellishment.

Many themes will include icons in both scalable and fixed-size form. The theme engine will pick an appropriate icon based on criteria that I can't recall at the moment.

If you're creating a mix-and-match icon theme, you can use both without any problems.

If you want to only produce one set of icons yourself, and you already know how to use Inkscape, a fully-scalable set is fine.

If you're more comfortable with raster-graphics editors, or you want specific icons for different viewing sizes, you can create them in the GIMP and put the differently-sized icons in directories particular to their size.

If you are very comfortable with using both types of image, you could create your icons using both Inkscape and the GIMP (Inkscape is able to import/export raster graphics files that you can edit in the GIMP) to have a full set of icons customised to look the best at specific sizes with scalable icons to fill in the gaps.

The [Tango Desktop project]("http://tango.freedesktop.org/Tango_Desktop_Project") has some guidelines on good icon creation that you might find useful.

Good luck with your endeavours. You might find that starting with something fairly simple like compiling a theme of nice icons reveals some latent graphical design leanings.

---

