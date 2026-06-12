---
title: "adding desktop wallpaper in 12.04"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by bookherd on 2013-11-06
I'm not new to Ubuntu, but I just upgraded to 12.04 from 10.04, and some things that were easy before are now strangely complicated, making me feel like an Absolute Beginner all over again.

I want to add some .jpgs to my folder of desktop wallpapers (usr/share/backgrounds), but the file browser won't let me.  "You are not the owner, so you cannot change these permissions."  Seems like I should just be able to enter my root password somewhere and do this simple thing, but how?  Yeah, I know I can probably move the files around from the command line with sudo, but I'd prefer a GUI-based solution if there is one.

---

### Post by monkeybrain20122 on 2013-11-06
```
sudo mv pathtoyourjpgfiles/jpgfilename /usr/share/backgrounds/
```

Or you can store the jpgs in your Pictures folder. Then right click on the desktop, choose "Change Desktop Background" and change the tab "Wall Papers"  to "Pictures Folder" by clicking the arrow and select the new wall paper from there. That way you don't need root permission.

---

### Post by deadflowr on 2013-11-06
+1 to what monkeybrainnumbernumbernumber:) stated.

Throwing the images into the /usr/share/backgrounds folder alone won't add them to the selection to choose from.
To do that they'd need to be added to the .xml file in /usr/share/gnome-background-properties.
A painstaking task.( one wrong character and you'll have to find and fix it, or no wallpapers)
You'll find it much easier to just call the image from the users Picture folder.

---

### Post by elliotn on 2013-11-06
u can also just drag the pic to the theme/background window

---

### Post by bookherd on 2013-11-06
Now that you mention it, I do have a distant memory of wrangling with this a long long time ago.  I wish there were a way to call the wallpapers from another folder (like, say, a wallpapers folder inside Pictures?), but this is essentially the fix I was looking for.  Thanks for your help, monkeybrain20122 and deadflowr!

Edit to add: thanks elliotn as well! The click-and-drag approach is more intuitive way to put the pic into the Pictures folder.

---

