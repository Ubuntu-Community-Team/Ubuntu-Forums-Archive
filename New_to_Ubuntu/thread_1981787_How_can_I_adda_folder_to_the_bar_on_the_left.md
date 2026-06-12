---
title: "How can I adda folder to the bar on the left?"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by tiamat2009 on 2012-05-17
Hello.

I'm just trying out ubuntu after my brother installed it for me.

One thing I find, is that I can't add folders to the quick launch like i did in windows.

I've tried dragging folders there, shortcuts of folders, how can I add the downloads folder to the quicklaunch thing on the left?

I've googled this for ages and just find strange blog posts saying it easy, and then what I read is anything but easy.

Why can't I just drag a folder on to it?

---

### Post by -DarkAceZ- on 2012-05-17
Is this Ubuntu 12 on Unity?

---

### Post by tiamat2009 on 2012-05-17
Yes. Ubuntu 12.04

Installed with WUBI.

---

### Post by -DarkAceZ- on 2012-05-17
What DE are you trying to do this on? Gnome 3?

---

### Post by tiamat2009 on 2012-05-17
This with the default ubuntu desktop. I think it's called unity.

There's a grey bar at the top of the screen that says unity desktop on it. And a purple bar on the right.

---

### Post by tiamat2009 on 2012-05-17
Sorry, I mean on the left

---

### Post by -DarkAceZ- on 2012-05-17
Hmmm, you **should** be able to just drag the folder... Try this:
Open the folder, and then an icon should show up on the left bar that looks like a folder. Right-click it and click "Lock to Launcher" or "Lock to Panel".

---

### Post by zach2825 on 2012-05-17
by default in ubuntu 12.04 you should be able to add/remove things to the panel by dragging it.. Maybe somehow you locked the panel. Try searching for a way to unlock the menu.. You could try installing something called "myunity" with "sudo apt-get install myunity" that gives you lots of options.

---

### Post by philinux on 2012-05-17
> **tiamat2009 said:**
> Hello.

I'm just trying out ubuntu after my brother installed it for me.

One thing I find, is that I can't add folders to the quick launch like i did in windows.

I've tried dragging folders there, shortcuts of folders, how can I add the downloads folder to the quicklaunch thing on the left?

I've googled this for ages and just find strange blog posts saying it easy, and then what I read is anything but easy.

Why can't I just drag a folder on to it?

First install this.

```
sudo apt-get install --no-install-recommends gnome-panel
```

Then from the same terminal use this.
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

This is the old right click on desktop option thats now gone.

Choose Application and in the command type nautilus /pathtoyourfolder/

You'll then have a launcher on your desktop. Drag it onto the launcher.

---

### Post by jerome1232 on 2012-05-17
You can right click the home folder icon on your launcher, and a quicklist menu will pop up with your downloads folder as an option.
This right click menu will show any bookmarks you have added to nautilus, quite nifty if you ask me.

---

### Post by tiamat2009 on 2012-05-17
There is no new icon appearing when I open a  folder. 

I can't drag anything to the bar. I tried dragging an office file to it and this doesn'T appear there either.

---

