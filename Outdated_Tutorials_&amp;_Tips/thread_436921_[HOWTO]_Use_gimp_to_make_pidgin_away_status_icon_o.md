---
title: "[HOWTO] Use gimp to make pidgin away status icon orange"
date: 2007-05-08
forum: Outdated Tutorials &amp; Tips
---

### Post by khughitt on 2007-05-08
This is a really simple tutorial on modifying the look of pidgin i thought i would post  in case anyone else wanted the same kind of thing.

The new pidgin interface is nice imo because it's much easier to see at a glance who is online, and who is away. It would be even better though (for me) if the away status icons were orange (google-talk style) instead of blue.

This turns out to be quite easy to arrange using gimp!

This is what it looks like using the new images:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32089&stc=1&d=1178633374[/IMG]

Okay, so if you are still interested, here goes:

**1. Copy available icons to location of away images**

There are four sets of each of the status images- 16x16, 22x22, 32x32, and 64x64. Your system will only use one of the sizes at any given time, but for sake of ease, i replaced all of the away images.

First backup you old away icons in case you decide to change back. Open a terminal (e.g. alt+f2 -> "gnome-terminal") and type:
```

cd /usr/local/share/pixmaps/pidgin/status
sudo mv ./16/away.png ./16/away.png.bak
mv ./22/away.png ./22/away.png.bak
mv ./32/away.png ./32/away.png.bak
mv ./64/away.png ./64/away.png.bak

```Next, make a copy the available status images (available.png) for each size using the name "away.png."
```

cp ./16/available.png ./16/away.png
cp ./22/available.png ./22/away.png
cp ./32/available.png ./32/away.png
cp ./64/available.png ./64/away.png

```**2. Modify images using gimp**

First run gimp *as an admin*.. i.e. using the **sudo** command.

```
gksudo gimp
```Now, navigate to /usr/local/share/pixmaps/pidgin/status and open each of the four away images with gimp.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32090&stc=1&d=1178633457[/IMG]

Now for each image, open the color balance dialog- Click "**Layer**" -> "**Colors**" -> "**Color Balance**." Drag the top slider (cyan) all the way to the *right* to set it to 100. Drag the bottom two slider all the way to the *left* to -100. Hit "Control+S" to save the image.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32091&stc=1&d=1178633457[/IMG]

Now simply restart pidgin, and your away status icons should be nice and orange :) That's it!

There are other ways to do this I'm sure, especially if you already have some orange status images, but this doesn't take long, and is an easy way to get your feet wet with gimp if you have not tried it yet.

Hope this helps!

---

### Post by ComplexNumber on 2007-05-08
great howto! 

btw i changed the "sudo gimp" to "gksudo gimp" in your code. its not advisable to run graphical applications using sudo. best to use gksudo instead.

btw2 i can see that you store your themes in your home directory rather than /usr/share/themes :p. thats why gimp isn't themed.

---

### Post by khughitt on 2007-05-08
Cool :) I've always wondered about when to use regular sudo vs. gksudo. I will check out the gimp theming too- i'm still learning some of the nuances of gtk themes, and have been wondering why when i run certain applications using plain 'sudo' they are not themed likely they normally would be. Now it makes sense!

Thanks :)

---

### Post by wounded on 2007-05-08
I've altered the color of the away icons to a more blue-ish color but when I am away the icon in the notification area is still the little clock thing and not the blue version of the green "Online" status icon and I cannot find a little clock icon in my pidgin directory. Does anyone know what I did wrong or where to look for this icon?

---

### Post by khughitt on 2007-05-09
I think you also will need to modify  */usr/local/share/pixmaps/pidgin/tray/16/tray-away.png* and */usr/local/share/pixmaps/pidgin/tray/22/tray-away.png*. Good point though.

---

