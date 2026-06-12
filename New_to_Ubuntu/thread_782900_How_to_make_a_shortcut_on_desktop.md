---
title: "How to make a shortcut on desktop?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-05-05
Bs'd

I downloaded Sanduhr, but the only way I can find to start the program, is to type "sanduhr" in the console.  
and when I close the console, Sanduhr is gone. 

How can I make a shortcut on my desktop for it?

---

### Post by kpkeerthi on 2008-05-05
Right-click on desktop and choose Create launcher and enter **Sanduhr** for 'Command'

---

### Post by Carnivorum on 2008-05-05
Bs'd

It worked.   Great!

Thanks.

---

### Post by Sukarn on 2008-05-05
> **Carnivorum said:**
> Bs'd

It worked.   Great!

Thanks.

By the way, what in the world is "Bs'd"?

---

### Post by Carnivorum on 2008-05-05
Bs'd

BSD means Berkely Software Distribution.

Well, in the above case, the comma in the end makes it an abbreviation.  It stands for the Aramaic expression: Ba siata desmaya, and that means: With the help of heaven.

---

### Post by Sukarn on 2008-05-05
I know what BSD is, but I had absolutely no idea what Bs'd meant. Never heard or read it before.

thanks for the information.

---

### Post by H.Callahan on 2008-05-05
While we are on the topic (OP, that is), what are the arguments in Ubuntu to pass filenames and such.

For example, if I wanted to open Firefox passing the URL, in Windows the command would be:

```
firefox.exe %1
```

That doesn't seem to work in Ubuntu...

---

### Post by avtolle on 2008-05-05
> **H.Callahan said:**
> While we are on the topic (OP, that is), what are the arguments in Ubuntu to pass filenames and such.

For example, if I wanted to open Firefox passing the URL, in Windows the command would be:

```
firefox.exe %1
```

That doesn't seem to work in Ubuntu...
Try ```
firefox %1
```

---

### Post by H.Callahan on 2008-05-06
Not quite what I intended to ask.  I was more concerned with the "%1" part of the command.  I have seen some shortcuts (Launchers?) that have something like:

```
*commandname* %f
```

I was wondering if the conventions were the same for Ubuntu as for Windows.

---

### Post by Carnivorum on 2013-01-31
Bs'd

I have now 12.04, and when I right click on the desktop, I don't get in the menu the option to make a launcher. 

How can I make a launcher?   With my own picture?

---

### Post by Frogs Hair on 2013-01-31
I have alacarte installed and don't remember if it is necessary on 12.04 . What I would do is drag the launcher icon to the desktop right click the icon to enter properties. 

In properties under basic select the icon picture on the left and navigate to the folder of the image you would like to use, select the image, and select open. If you need alacarte use the following. (I have tested this )

```
sudo apt-get install alacarte 
```

---

### Post by kurt18947 on 2013-01-31
Here's a pretty simple way if you're comfortable in the terminal, or can cut & paste;).  In a terminal, type the following:

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```Give your launcher a name, enter the command(s), and add a comment if you're so inclined, it's not necessary.   To add/change an icon, you'll want to create or import an appropriately sized graphic.  It looks like the preferred file type is *.svg but I've used .png in the past.  You could put it in the what appears to be the default location, or just in ~/Pictures or wherever.  The default location appears to be:

/usr/share/icons/hicolor/scalable/apps

 Left-click the little icon thingy on the left side of the 'Create-Launcher' window.  Navigate to your new icon, click it and you should be good.  If you put your new icon in your user account, don't delete it.  Ask me how I found out about that:oops:.  It looks a link is created, not a copy.

---

### Post by Carnivorum on 2013-02-01
> **kurt18947 said:**
> Here's a pretty simple way if you're comfortable in the terminal, or can cut & paste;).  In a terminal, type the following:

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```Give your launcher a name, enter the command(s), and add a comment if you're so inclined, it's not necessary.   To add/change an icon, you'll want to create or import an appropriately sized graphic.  It looks like the preferred file type is *.svg but I've used .png in the past.  You could put it in the what appears to be the default location, or just in ~/Pictures or wherever.  The default location appears to be:

/usr/share/icons/hicolor/scalable/apps

 Left-click the little icon thingy on the left side of the 'Create-Launcher' window.  Navigate to your new icon, click it and you should be good.  If you put your new icon in your user account, don't delete it.  Ask me how I found out about that:oops:.  It looks a link is created, not a copy.

Bs'd

I managed to make one, with my own picture.   I did have to install alacarte, but the terminal gave me the command how to do that.  There were a few hiccups, but I managed in the end.   

Thanks everybody for your input, I'm very happy with the result.

---

