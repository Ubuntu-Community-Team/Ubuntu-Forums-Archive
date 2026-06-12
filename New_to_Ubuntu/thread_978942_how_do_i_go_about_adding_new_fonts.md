---
title: "how do i go about adding new fonts"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-11
the system font that came with firefox are killing me

be detail as possible

---

### Post by laptoplinux on 2008-11-11
There's probably another way to do this, but here is one way that works:

1.)  If there isn't already a .fonts folder in your home directory, make one.  Note the period out front.  Also note that, due to the period, it will be considered a "hidden" folder.  It will only show up if you have Nautilus set to show hidden files (View -> Show Hidden Files), or if you use "ls -a" from command line.

2.)  Put the new font in the .fonts folder.

3.) Refresh your font cache:
    run "sudo fc-cache -fv" in a terminal.

That should do the trick.

---

### Post by Kellemora on 2008-11-11
Hi aszxcv

It looks like you are looking for where to get more fonts, rather than where to put them.

But I'll start with where to put them just the same.
If you are talking about TrueType Fonts, like as used in Winders
It's best to keep them in a folder where everyone can use them and each user don't have their own separate fonts folders.

The TrueType fonts currently installed on your computer are located in
/usr/share/fonts/truetype
this is NOT a hidden folder by the way.

You don't have to INSTALL fonts, you can just copy and paste them from your windows folder over to your Ubuntu Truetype folder if you want or have access to fonts that way.

If not and you need to download new fonts, the easiest way to do this is go into Synaptic and place a checkmark on msttcorefonts and hit the Apply button.

I see you are fairly new.  So, this is done by going to the top of your screen under System, when that drop down opens go to Administration and in the drop down for administration, you will find a line that reads Synaptic Package Manager.
By clicking on that, all the programs available to download through Synaptic will open up.  Just scroll down the list until you find msttcorefonts and place the checkmark in front of it.  hit Apply and it will download for you.  After that, you will see the box will be green, indicating that is an installed feature from Synaptic.

TTUL
Gary

---

### Post by laptoplinux on 2008-11-11
Thanks for the info, Kellemora!  I wasn't aware of that method.

aszxcv, go with Kellemora's method, but you'll still probably want to refresh the font cache after copying the fonts over.

---

