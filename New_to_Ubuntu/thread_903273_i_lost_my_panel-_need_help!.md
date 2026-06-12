---
title: "i lost my panel- need help!"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by kunala05 on 2008-08-28
I recently lost my panel which is on top of the screen. It is the one with application-places-system. The entire bar is missing. How do i get it back?

I also want to know if i accidentally remove the buttons like Application-Places-System. How could I get it back.

Please help me. I would really appreciate any help. 
Thank You
Kunal A.

---

### Post by Ryadt on 2008-08-28
Try ```
sudo apt-get install gnome-panel
```

---

### Post by robert shearer on 2008-08-28
This thread may be of help..

[http://ubuntuforums.org/showthread.php?t=899313](http://ubuntuforums.org/showthread.php?t=899313)

---

### Post by drs305 on 2008-08-28
> **kunala05 said:**
> I also want to know if i accidentally remove the buttons like Application-Places-System. How could I get it back.

Once you get the panel set up to your liking, you can save (most of) the settings by running the following commands. The first one will save the settings in a file called *panels* on your desktop. You can alter the name and location to anywhere you wish. The second command will restore the panel by reading the *panel* file you saved earlier and then refresh the desktop.
Save panel settings:
```

gconftool-2 --dump /apps/panel > **~/Desktop/panels**

```

Restore panel settings:
```

gconftool-2 --load **~/Desktop/panels** && killall gnome-panel

```

---

### Post by ExWindowsDude on 2008-09-02
> **drs305 said:**
> Once you get the panel set up to your liking, you can save (most of) the settings by running the following commands. The first one will save the settings in a file called *panels* on your desktop. You can alter the name and location to anywhere you wish. The second command will restore the panel by reading the *panel* file you saved earlier and then refresh the desktop.
Save panel settings:
```

gconftool-2 --dump /apps/panel > **~/Desktop/panels**

```

Restore panel settings:
```

gconftool-2 --load **~/Desktop/panels** && killall gnome-panel

```

I'm trying to RESTORE to "out of the box" settings for my Xubuntu desktop, and tried to run the 2nd command given and received the following error:

```
bender@bender-desktop:~$ gconftool-2 --load ~/Desktop/panels && killall gnome-panel
I/O warning : failed to load external entity "/home/bender/Desktop/panels"
Failed to open `/home/bender/Desktop/panels': No such file or directory
bender@bender-desktop:~$ gconftool-2 --load ~/Desktop/panels && killall gnome-panel
I/O warning : failed to load external entity "/home/bender/Desktop/panels"
Failed to open `/home/bender/Desktop/panels': No such file or directory
bender@bender-desktop:~$ 

```

Looks like I might have "deleted" Control panel 2. (when I was trying to come up  with a layout I lilked, I was adding/deleting settings).

any suggestions on going back to "out of the box" settings?

Thanks!

---

### Post by 7raTEYdCql on 2008-09-02
just type  "gnome-panel" in terminal (without quotes)

if this doesnot work....

then go to usr/bin  - > ten find gnome-panel
may be in /bin also......
then also add it in startup....

---

### Post by drs305 on 2008-09-02
> **ExWindowsDude said:**
> I'm trying to RESTORE to "out of the box" settings for my Xubuntu desktop, and tried to run the 2nd command given and received the following error:

The command will only work if you had previously run the first command to back up the settings and the filename chosen still resides in the same location to which it was saved. Otherwise you would have to update the file path in the command.

As to Control panel 2, I don't run Xubuntu and don't know which panel you are referring to. Normally you can restore settings by deleting/renaming the applicable folder/file in your home directory - in one of the . folders.

---

### Post by ExWindowsDude on 2008-09-02
> **i.mehrzad said:**
> just type  "gnome-panel" in terminal (without quotes)

if this doesnot work....

then go to usr/bin  - > ten find gnome-panel
may be in /bin also......
then also add it in startup....

Thanks!
I've run gnome-panel, and it "kind of works", what I mean is that it rebuilds as desired.
I get one error message (if I want to delete a trash applet), I say "no"

Everything looks as desired (back to original settings).
However, I have the following error message in my Term Window

```
bender@bender-desktop:~$ gnome-panel



(gnome-panel:6827): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8





** (gnome-panel:6827): WARNING **: panel-applet-frame.c:1270: failed to load applet OAFIID:GNOME_Panel_TrashApplet:

(null)

Unable to open desktop file file:///usr/share/applications/yelp.desktop for panel launcher: No such file or directory


```

If I keep my Term window open (everything is fine). Once I close the Term window, I go back too the "bad" settings I do not want.

Any advice?  THANK YOU!!

---

### Post by ExWindowsDude on 2008-09-02
> **i.mehrzad said:**
> just type  "gnome-panel" in terminal (without quotes)

if this doesnot work....

then go to usr/bin  - > ten find gnome-panel
may be in /bin also......
then also add it in startup....

THANKS, THAT SOLVED IT!
(I ran again and said "Yes" to delete the Applet , was able to close Term Window and it works fine now!!

(how do I mark this "Solved" :-)
still new at "discussion" threads.....

---

