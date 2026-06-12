---
title: "Installed Dolphin and it looked good, then after a restart it never comes up again"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by Giant_Dragon on 2014-01-28
I installed Dolphin through the Software Center and it seemed to work great.  But, after a restart I haven't seen it since...  I then uninstalled and reinstalled, but still don't see it.  Can you tell me what I'm doing wrong?

Thanks!

---

### Post by ibjsb4 on 2014-01-28
Try pulling it up in terminal.

```
dolphin
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by Giant_Dragon on 2014-01-28
Well, that definitely brought it up.  Do I have to do that every time?    Might be a problem for other users of the machine. :)  They don't want  to mess with the terminal, etc.
thanks for your help!

---

### Post by Giant_Dragon on 2014-01-28
I basically want to make it the default desktop if I can....

---

### Post by Giant_Dragon on 2014-01-29
Guess there's no way to make dolphin come up by default?.....

---

### Post by RadicaX on 2014-01-30
What version of Ubuntu are you using? If it is the one with Unity, it is a bit of a problem, if it is any other version, you should be able to make a shortcut without much issue. You should also be able to find it with the dashboard with no problem if it is the Unity DE.

---

### Post by echotech2 on 2014-01-30
In Ubuntu 13.10 and Unity I use Dolphin as my file manager.  I just placed it on the Launchbar and it works great (aside from all the dependencies it brings in).

---

### Post by Giant_Dragon on 2014-01-30
Oh, I thought maybe I could make it my default file manager somehow...  I guess putting it on the launch bar is the next best thing.  :)
I have the latest version...I think.  I just downloaded and install 5 days ago....  I'll check.

---

### Post by RadicaX on 2014-01-31
I see, in XFCE, you just go to preferred applications, and pick it as the preferred file manager. Unity, I would imagine would let you do that too. I am very sorry, I have no clue why I thought you wanted to set up a shortcut.

---

### Post by newb85 on 2014-01-31
Ubuntu Unity: Default Application under System Settings has defaults for Web, Mail, Calendar, Music, Video, and Photos.  There's no setting for file browser.  I've always been very satisfied with Nautilus, but I still think the option should be there.  I would say this is a design oversight, but I'm sure the Ubuntu devs will say it was intentionally left out in order to make things less confusing or something, once again supporting my theory--Steve Jobs didn't die...he disguised himself as Mark Shuttleworth...

---

### Post by Giant_Dragon on 2014-02-01
Ok, I'll stop complaining about it and be happy.  Thank you for your help!!!  :P

---

### Post by RadicaX on 2014-02-01
Sorry, it is a bummer Unity would not let you do that. I guess you should mark this thread as solved then. Of course your friendly *Buntu users will reply to other threads for other questions too if you need help.

---

### Post by stinkeye on 2014-02-01
> **Giant_Dragon said:**
> I basically want to make it the default desktop if I can....
Don't use KDE but I don't believe dolphin handles the desktop.
By this do you mean your default file browser?

This is the method I use for making nemo default, I'm assuming you can do the same with dolphin.
Check default file manager(terminal)....
```
xdg-mime query default inode/directory
```

Set dolphin as default file manager...
```
xdg-mime default kde4/dolphin.desktop inode/directory application/x-gnome-saved-search
```

If you want to revert back to nautilus....
```
xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
```

---

### Post by cigtoxdoc on 2014-02-01
The problem is that Firefox defaults to Nautilus for saving files from the Internet.  Nautilus apparently does not want you to use programs that are listed in subfolders and sub-subfolders that are in your .wine or other hidden directories.  This is a real pain as I need to use Adobe Reader XI for some of my work.  Adobe Reader XI works very nicely under WINE 1.6 and Ubutu 12.04.

John

---

