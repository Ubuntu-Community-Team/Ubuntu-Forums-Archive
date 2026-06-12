---
title: "Nemo Slow - use Nautilus instead?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by kellyvotrenom on 2014-04-26
Hi

I have installed Xubuntu and then installed the Cinnamon desktop and am having file manager problems.  Nemo is sometimes very slow to open directories, 20-30 secs.  It seems that there are other file managers opertating at different times on my system as well.  When I launch a file manager from my Menu icon, it’s Nemo.  When I open from applications it seems to be another file manager (I can’t identify it, there is no ‘about’ in the menu)

If I execute ‘xdg-open $HOME’ Thunar opens. If I run ‘xdg-mime query default inode/directory’ I get ‘nautilus-folder-handler.desktop’.

Not sure what is going on.  Which file manager is preferable, especially since all my data is on external network drives that the current set up seems to have trouble seeing occassionally?


Thanks

Mark Springer
industrial arts

---

### Post by LastDino on 2014-04-26
This is what happens when you install too many of them. Xubuntu comes with default Thunar and obviously it's set as default and will handle everything by default unless you change the settings and use some other File manager. I strongly suggest sticking with Thunar only as it also has easy to access ''brows network'' option and its a good practice not to remove things which come with default package.  Nemo is definitely powerful file browser, but do you really need it? The one you see in applications is also Nemo (if my memory serves me right, I could be wrong since I'm not using Nemo since I shifted to Xubu)

Anyway, that's just me. 
The file manager choice is handled by a file in ~/.local/share/applications. I don't remember if it is mimeapps.list or mimeapps.cache, but deleting both of those files will reset your file manager to the default.
This is official documentation
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

### Post by ibjsb4 on 2014-04-26
I have ran Nemo and Nautilus (default) without issue, but you also have Thunar and with a   Cinnamon/XFCE desktop.  I have never tried that mix, but I also think you have too much going on.

[http://ubuntuforums.org/showthread.php?t=2219780&p=13002387#post13002387](http://ubuntuforums.org/showthread.php?t=2219780&p=13002387#post13002387)

---

### Post by Frogs Hair on 2014-04-26
In my experience with the XFCE session I found that it preforms best with Thunar as default . There was conflict with nautilus for example when opening photos because each desktop had its own image viewer applications. As much as like leaning about and trying new desktops I have limited myself to Unity & Gnome because they share a file manager. XFCE didn't behave the same way with Nautilus as default and I even lost the context menu options for Thuner in one case.

---

