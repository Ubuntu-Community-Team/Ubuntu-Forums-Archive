---
title: "Realplayer won't work"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-09-01
I installed RealPlayer and there is an icon in the launch but, when I click on it nothing happens.

Did I install it wrong?

What should I do?

---

### Post by drs305 on 2008-09-01
Try selecting the icon again. You can check to see running processes by typing:
```
ps -ef | grep realplay
```

If realplay or realplay.bin is displayed on 2 or more lines, it is running. (one of the lines will include "grep", which is the search process).

If you think you may have installed it incorrectly, you can follow my instructions in this post. It goes through step-by-step, with corrections made to the user's errors along the way.

If you are in the same directory as the downloaded .bin file, you can probably start at post #17:
[http://ubuntuforums.org/showthread.php?p=5285631#17]("http://ubuntuforums.org/showthread.php?p=5285631#17")

2 Observations:
1. Are you sure you really need Realplayer? You can search to see if any of the other linux players can play rm files. It would be easier to install a plugin than another whole player.

2. Save the folder created during the installation. It will contain a folder called "postinst" and within that folder is a file called "postuninst". This is the uninstaller, and without it you won't be able to cleanly remove RealPlayer since it isn't registered with dpkg, apt or synaptic.

---

### Post by saskatchewan on 2008-09-02
I will try your suggestions.

The reason why that I am trying realplayer is that I have been having problems playing things from websites that use either RealPlayer or Windows Media.

Do you have any suggesions of alternative software?

I have tried mplayer but I get no video.  Only Audio.

And as for Kaffine, it is always poor video quality and I use VLC for instead.

---

### Post by paletti on 2008-09-08
Have you tried going to the Realplayer directory and execute realplay manually (right click - open in terminal)? that worked for me anyway...

---

