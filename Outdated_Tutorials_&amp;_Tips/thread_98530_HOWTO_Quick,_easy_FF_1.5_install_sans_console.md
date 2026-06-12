---
title: "HOWTO: Quick, easy FF 1.5 install sans console"
date: 2005-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Curlydave on 2005-12-03
This tutorial explains how to quickly install the latest version of Firefox without having to use the console at all. This will greatly improve performance over the gnome-integrated version of firefox. The bolded sections are the primary steps.

1. **Download the latest version of FF from the mozilla website** [http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US) 
Save this file to your main filesystem directory, "/", or download it to a different directory and move it to your "/" directory.

2. Open a root browser (this can be done by creating a launcher with the following command: "gksudo "nautilus --nodesktop /""), right click on the firefox-1.5.tar.gz file which you have just downloaded, and select "extract here" from the drop-down menu. This will **extract firefox to the directory "/firefox"**

3. **Create a launcher on your desktop** with the following in the command field: "/firefox/firefox". After creating the launcher, right-click on it and select properties. Click the icon change button, and browse to the directory /firefox/icons, and select "mozicon128.PNG. Select ok again, and exit the properties. You may want to resize the icon by right clicking on your launcher and selecting "stretch icon". You may move a copy of your launcher on a panel if you wish

4. **Remove your old Firefox install.** Open up the Synaptec Package manager under System-Administration, and search for the "Firefox" package. uncheck the box, and Apply changes.

5. **Add your Firefox icon to the Applications-Internet menu.** Under Applications, System tool, select the Applications Menu Editor. Select "Internet" from the options on the left, and press the "New Entry" button. Enter a name such as "Firefox" or "Mozilla Firefox". Under the command field, enter "/firefox/firefox." Then click where it says "no icon", and browse to the directory "/firefox/icons" and use "mozicon128.PNG" as before. Hit OK, exit the menu editor, and you're set!


This should, among other things, greatly improve your FF performance. You're probably thinking to yourself: "Wtf do I need a tutorial for this? I could have figured all of that out on my own!" I'm posting this here to prove that you don't need to follow a 12-page tutorial and use a bazillion console commands to get nice, clean, fast version of FF1.5. :)

---

### Post by Curlydave on 2005-12-06
*Modified with more detailed information including adding your icon to the menu.

---

### Post by zoiks on 2005-12-17
You might want to add that "gksudo nautilus" will start you off in root's home directory, so you will have to go to FileSystem, then go to /home/username to get back to the user's home.

---

### Post by briancurtin on 2005-12-17
when i go into synaptic to remove firefox, is there a reason it tries to remove "ubuntu-desktop" at the same time as firefox? to me that looks a bit important, but it could be because im new to ubuntu (used suse for a while before this).

---

### Post by galderz on 2005-12-17
i've downloaded firefox and uncompressed it, but i seem to be unable to execute that command. It keeps saying that the command is not found, even though the permissions seem to be correct, x for everyone.

i'm a begineer so i might be forgetting something very silly.

---

### Post by zoiks on 2005-12-18
[QUOTE=briancurtin]when i go into synaptic to remove firefox, is there a reason it tries to remove "ubuntu-desktop" at the same time as firefox? to me that looks a bit important, but it could be because im new to ubuntu (used suse for a while before this).[/QUOTE]

FYI I went ahead and allowed synaptic to remove the 5 or 6 packages it wanted to remove after deselecting firefox.  (I figured I could always reinstall it if I had a problem).  I had no problems other than an error message or two from gnome saying an icon had disappeared or something.  But after rebooting and running FF 1.5 I've had no more error messages.  1.5 definitely runs much faster than 1.07.  I've upgraded two machines and 1.5 is happily runing on both.  (On one machine I did have to use synaptic to install libstdc++5, though, before FF 1.5 would run.)

---

### Post by zoiks on 2005-12-18
[QUOTE=galderz]i've downloaded firefox and uncompressed it, but i seem to be unable to execute that command. It keeps saying that the command is not found, even though the permissions seem to be correct, x for everyone.

i'm a begineer so i might be forgetting something very silly.[/QUOTE]

Make sure you give the full location of firefox as the command, such as /firefox/firefox.  Try

ls -a /firefox/firefox

to verify that it's where you think it is.  If it's not there, perhaps you extracted the directory to your Desktop directory?

---

### Post by TeeAhr1 on 2005-12-27
HAZARD!  DANGER!  WARNING!

Yelp, for some totally arcane and unknown reason, is dependent on firefox.  I would recommend leaving the earlier version in place if you want to retain yelp.  Just make sure all your launchers are pointing at the new version.

---

### Post by anil_robo on 2005-12-27
[quote=TeeAhr1]HAZARD!  DANGER!  WARNING!

Yelp, for some totally arcane and unknown reason, is dependent on firefox. I would recommend leaving the earlier version in place if you want to retain yelp. Just make sure all your launchers are pointing at the new version.[/quote]

Haha! I discovered it once, the hard way! Couldn't believe my eyes some program had knocked down yelp (and a host of other packages as well) without my knowledge! :)

I'd use FF 1.0.7 + Opera for the time being. FF 1.5 will be there in Dapper install anyway! :)

---

### Post by TeeAhr1 on 2005-12-27
Right now I'm reinstalling gnome, I've managed to screw all kinds of stuff up in the process of trying (and utterly failing) to get yelp back without ff1.07.  I don't think it can be done.  What I'm going to do, as mentioned, is move 1.5 over to a new directory, reinstall 1.07 (and yelp), and make sure all the widgets are pointing to the new version.  Good clean fun.  ](*,)

---

