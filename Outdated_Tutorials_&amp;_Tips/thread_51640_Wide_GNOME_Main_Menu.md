---
title: "Wide GNOME Main Menu"
date: 2005-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2005-07-24
I've figured out how to make a sensational GNOME Main Menu.

You might think, hey, just use gconf-editor and put an icon there (Google for that if you're a noob), but you can make this even better than that! With the technique below, you can:

* Make your GNOME main menu appear wider than it allows.
* Make your GNOME main menu icon look fantastic, not squooshed like when you load an Ubuntu logo icon via gconf-editor.
* Improve the look of the Ubuntu logo in the main menu beyond anything anyone else has ever dreamed could go there.

Here's how:

1. Download this image:

[http://people.ubuntulinux.org/~mako/docteam/images/IconUbuntu.png](http://people.ubuntulinux.org/~mako/docteam/images/IconUbuntu.png)

(Or use the official one here:

[https://wiki.ubuntu.com/UbuntuArtwork?action=AttachFile&do=get&target=UbuntuLogo.png](https://wiki.ubuntu.com/UbuntuArtwork?action=AttachFile&do=get&target=UbuntuLogo.png)

...and shrink it down to size)

2. The circle logo is pretty, but I've seen some people make it even better by leaning it to the back a little, turning it, and adding 3D effect. Therefore, download one of the examples here from "greven":

[http://ubuntuforums.org/gallery/files/1/7/1/5/4/UbuntuI.png](http://ubuntuforums.org/gallery/files/1/7/1/5/4/UbuntuI.png)

**(BTW, I heap lots and lots of praise on this user "greven". Sensational 3D images that I know I couldn't possibly do in a gazillion years.)**

3. Now, combine the 3D lean back version of the Ubuntu logo in # 2 with the "ubuntu" of # 1. Use Gimp to scale it down to about 110x24.

4. Take a measurement of your desktop width. For instance, mine is 1024. Make your bottom panel 24 pixels high. Consider switching your controls to "Glider" and your window border to "Clearlooks" in your theme. Take a snapshot of that and in Gimp find out the color of your GNOME panel. Mine, for instance, was #efebe7.

5. Using Gimp, make a rectangle that is 24 pixels high and the width of your desktop. Fill it with the color of your current GNOME panel.

6. Now, with a bit of skill and practice, you can make a transparent background version of the image you made in # 3 and paste it into the new "panel" you made in # 5. I pasted it on the far-left side. Save this image as "ubuntupanel.png".

7. Before you shut down Gimp, make a 32x32 transparent background PNG file and save it as "mainmenu.png".

8. Now right click your bottom panel, ensure it is 24 pixels high, and then set the background image of it to "ubuntupanel.png".

9. Now use gconf-editor and find your main menu icon, use custom icon, and set it to the 32x32 transparent PNG icon you made in # 7.

Voila! Now you have a GNOME main menu that has the appearance of being 110 pixels wide (although clicks on the word "ubuntu" do nothing unless you add a launcher there with a transparent PNG icon). Instead, clicks on the logo make the main menu appear. However, the main menu icon is much larger and wider now than GNOME permits, using this sneaky trick with the transparent PNG.

By explaining all of this, you can adapt it and make it to just your tastes, such as making a "glass-like" logo, or blue logo, or whatever, for your GNOME main menu with Ubuntu. 

**I've attached my version of the Ubuntu panel if you want to use that. If you have a wider than 1024 pixel screen, then you'll need to use Gimp to extend the right side of it.**

P.S. I dream that someday the GNOME team will figure out a way to make the Main Menu just as wide as the icon file you pick for it, and perhaps even provide a way to set the pressed-in version of the icon too. But until that day comes, this is a good second bet.

---

### Post by charlieg on 2005-07-24
To start with, I'll say 'congrats' on finding the right way to do essentially what this howto does (but it does it in a hackish manner):
[http://www.ubuntuforums.org/showthread.php?t=26854](http://www.ubuntuforums.org/showthread.php?t=26854)

However...

[QUOTE=SuperMike]9. Now use gconf-editor and find your main menu icon, use custom icon, and set it to the 32x32 transparent PNG icon you made in # 7.[/QUOTE]
Well when I search in GConf for 'menu', it brings up:
/apps/panel/objects/menu_bar_screen0
/apps/panel/default_setup/objects/menu_bar

Setting [use_]custom_icon in either or both of these doesn't work. :(

Could you be more specific?

---

### Post by SuperMike on 2005-07-24
[QUOTE=charlieg]To start with, I'll say 'congrats' on finding the right way to do essentially what this howto does (but it does it in a hackish manner):
[http://www.ubuntuforums.org/showthread.php?t=26854](http://www.ubuntuforums.org/showthread.php?t=26854)
However...
Well when I search in GConf for 'menu', it brings up:
/apps/panel/objects/menu_bar_screen0
/apps/panel/default_setup/objects/menu_bar
Setting [use_]custom_icon in either or both of these doesn't work. :(
Could you be more specific?[/QUOTE]

My technique improves upon showthread.php?t=26854 by:

* Providing a wider main menu that is previously allowed in GNOME. It does it with a kludge, but heh, it's attractive and it's a start.

* Providing a taller and wider icon than the main menu in GNOME permits for a certain size gnome panel.

As for how to replace the icon without having to copy files around, I use gconf-editor, which is here:

1. Foot, System Tools, Configuration Editor. (This is a menu link to gconf-editor.)
2. Expand /apps/panel/objects.
3. Click on each object beneath that such as "object_0" and so on until you see the one that says, "tooltip: Main Menu" or something like that. That's the one you want to work with.
4. Check off "Use Custom Icon".
5. Doubleclick "Custom Icon" and type in the path to your custom icon, such as something you may have dropped into /usr/share/icons.
6. As soon as you change this, Ubuntu uses it instantly. No need to killall gnome-panel or anything like that.

---

### Post by Magneto on 2005-07-31
thanks for this - makes it a lot easier to change my gnome menu icons too and no need for three menus to use em

---

### Post by Mikebgr on 2006-05-02
cool little mod! will do!

---

### Post by motin on 2007-04-28
Here is the updated src to the UbuntuI.png image: [http://ubuntuforums.org/gallery/data/5/UbuntuI.png](http://ubuntuforums.org/gallery/data/5/UbuntuI.png)

Or grevens gallery in whole: [http://ubuntuforums.org/gallery/showphoto.php/photo/318/ppuser/27686](http://ubuntuforums.org/gallery/showphoto.php/photo/318/ppuser/27686)

---

