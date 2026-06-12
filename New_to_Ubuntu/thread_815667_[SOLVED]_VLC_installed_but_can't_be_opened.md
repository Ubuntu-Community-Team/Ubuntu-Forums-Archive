---
title: "[SOLVED] VLC installed but can't be opened"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Sirchristopher on 2008-06-01
I have deleted VLC and re installed it but I can't find it to add it back to my menu.  It is in my home directory but I don't know how to get it to launch.  I have tried to add it to my menu but I do not have a choice for it.  Please help.

---

### Post by Joeb454 on 2008-06-01
How did you reinstall it? Did you do it through APT/Synaptic?

If not ```
sudo apt-get install vlc
``` from a terminal should do it all for you :)

---

### Post by JoshuaRL on 2008-06-01
How did you delete and reinstall?  What do you mean by "it's in my home folder"?  Are you able to get it to launch from the terminal by trying:
```

vlc

```

---

### Post by Sirchristopher on 2008-06-01
I installed it through synatpic. I deleted it the same way.  I was playing around with skins, trying to add them and couldn't get them to work when I installed them in the skins2 folder.  That started all the mess.

If I type 'vlc' in terminal it brings up the video viewer but it wont allow me to open a video or change the skin

---

### Post by JoshuaRL on 2008-06-01
What errors does it throw when you try to open a media file?

If they aren't graphical errors, check the terminal to see what it says.

---

### Post by Sirchristopher on 2008-06-01
I don't get an error, when I click on the eject button, nothing happens.

---

### Post by JoshuaRL on 2008-06-01
Okay.  Can you try opening a video file on your hard drive or on a mounted DVD?

---

### Post by Sirchristopher on 2008-06-01
If I right click a video file I don't have the option to open with VLC.  And if I choose 'Open With Other Application'  VLC is not there.

---

### Post by JoshuaRL on 2008-06-01
Can you select to open it through VLC?  It's an option in the File menu.

---

### Post by Sirchristopher on 2008-06-01
Nope, It's not an option and I can't add it through the main Menu option through System>Preferences>Main Menu

---

### Post by Joeb454 on 2008-06-01
Type ```
which vlc
``` and you should see the path of vlc, you should also then be able to add that as a shortcut to the menu :)

---

### Post by Sirchristopher on 2008-06-01
SWEEEEEET!!!!  Thanks!!!  That worked!!

---

### Post by Joeb454 on 2008-06-01
*Evil Laugh*

Glad it worked though ;) You can mark your thread solved from thread tools at the top of this page :)

---

### Post by cariboo on 2008-06-01
So I think you are saying you can open **vlc** from a terminal, but you can't find it on your menu. The way to do it, if it isn't in the list of programs in **Main Menu**, is to click on the **New item button** type a name for the program, click on the **browse** button, in the window that comes up double click on **file system** in the left hand panel. Navigate down to **usr** in the right hand panel. Double click on **usr**, then double click **bin**, then scroll down to **vlc** double click on it. In the create launcher window you should see beside the word command /usr/bin/vlc. Click OK and your good to go.

---

