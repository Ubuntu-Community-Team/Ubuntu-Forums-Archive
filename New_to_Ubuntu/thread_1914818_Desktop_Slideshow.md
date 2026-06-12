---
title: "Desktop Slideshow?"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by BruceCM on 2012-01-25
One thing I don't like about Ubuntu, sorry! It doesn't seem to have any way to do a slideshow desktop, like W7 & I'd really like to be able to set all my windows wallpapers into a slideshow here as well as when I do use W7. Is there some software that I can get for that, please?

---

### Post by Double.J on 2012-01-25
Hi there!

Try giving [wallch]("https://launchpad.net/wallpaper-changer") in the [repo's]("https://apps.ubuntu.com/cat/search/oneiric/?q=wallch") a go?

hope it helps :)

---

### Post by lechien73 on 2012-01-25
I believe that there are programs, such as wallch or CREBS that will do what you want.

If you want, though, it's not too difficult to create your own slideshows manually.

To do this, you need to create a folder in /usr/share/backgrounds to hold your pictures. I created one called mattpix:

```
sudo mkdir /usr/share/backgrounds/mattpix
```

I then copied my pictures in there, and added an xml file called background-1.xml, which is attached. The settings in the file are fairly self-explanatory, but feel free to post back if you have any questions. The <duration> tag is in seconds.

Finally, I did the following:

```
gksudo gedit /usr/share/gnome-background-properties/ubuntu-wallpapers.xml

```
and added the following section between the <wallpapers> tags:

```
<wallpaper deleted="false">
    <name>Shever</name>
    <filename>/usr/share/backgrounds/mattpix/background-1.xml</filename>
    <options>zoom</options>
  </wallpaper>
```

When you go back to change your screensavers, you'll notice your new one has appeared.

---

### Post by BruceCM on 2012-01-25
Thanks, I found Wallch in the software centre & installed that. I found that easy to set up & it's working now! Thought there'd have to be some program for it, just needed to find out what it was called. Many thanks for the rest of your answer, though.

---

