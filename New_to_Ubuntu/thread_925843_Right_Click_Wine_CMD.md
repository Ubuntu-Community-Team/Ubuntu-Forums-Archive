---
title: "Right Click Wine CMD?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by RATM_Owns on 2008-09-21
In the right click menu, I have a "Terminal Here" thing, but what I'd like is a "Wine CMD Here" option.

And since I have no idea how to do that, I've come to you.

Is there a way to make it run a command on startup or use a alternate bashrc?

---

### Post by EvilDaemon on 2008-09-21
> **RATM_Owns said:**
> In the right click menu, I have a "Terminal Here" thing, but what I'd like is a "Wine CMD Here" option.

And since I have no idea how to do that, I've come to you.

Is there a way to make it run a command on startup or use a alternate bashrc?

Wine Command here? Like, a DOS command? Or just to run wine there?

---

### Post by Sycron on 2008-09-21
If you want DOS, dosbox is for you. Install it: ```
sudo apt-get install dosbox
```

---

### Post by RATM_Owns on 2008-09-21
I mean like left click and there's a option to start Wine Command Prompt.

Like normal Terminal only it runs "wine cmd" at startup.

---

### Post by EvilDaemon on 2008-09-21
> **Sycron said:**
> If you want DOS, dosbox is for you. Install it:

This post was dumb. Don't bother with this, look at the next one.

---

### Post by RATM_Owns on 2008-09-21
Nope. Sorry.
Double clicking EXEs still works fine.

I want it to run "wine cmd" and then it opens a terminal to run wine cmd.
Or if I can have another profile which loads "/etc/wine.bashrc" instead of the normal bashrc.

---

### Post by EvilDaemon on 2008-09-21
> **Sycron said:**
> If you want DOS, dosbox is for you. Install it:

Is dosemu still around?

1. Do what Sycron said.

For the right clicking, do this. Go into a terminal (Applications : Accessories : Terminal) and type in
```
gksu nautilus /home/< YOU >/.gnome2/nautilus-scripts/
```
then Right click : Create Document : New File.  Name it "Command Prompt". Double click it, and copy and paste this in.
```
#!/bin/bash
# Run Windows-style Command Prompt here.
gksu dosbox
```
Save, go back to the File Browser. Right click the file, click Properties : Permissions. Down near the bottom of the window, there should be a checkbox "Make it executable" Or something. Click it, Close out. Exit out of the file browser, close the terminal out. Done!


Now go to any file, right click. There should be a slide out box under "Create new Document", called Scripts. It'll be called Command Prompt, and should run your files.


I think this'll be what you want.

---

### Post by RATM_Owns on 2008-09-21
Never mind. I found it out.

I went to Nautilus Actions Configuration, added gnome-terminal with parameters of '-e "wine cmd"'

---

