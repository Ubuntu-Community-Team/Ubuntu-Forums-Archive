---
title: "[SOLVED] no trash"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by davarse on 2008-06-12
hi everyone, i had a funny annoying question, i run hardy for couple of months already, i have compiz run in too. 
anyway, my question is, i dont have a trash logo on right bottom corner, as it used to be, it just gone, it wasn't like that before... i've tried to "add to panel" option and click on "garbage bin" but it didn't make any different, it just don't appear. after a while i notice, that there is one vertical line, and that is the garbage bin. does anyone how to bring back my trash logo??
it's funny, but it's important...

cheers'

---

### Post by perlluver on 2008-06-12
> **davarse said:**
> hi everyone, i had a funny annoying question, i run hardy for couple of months already, i have compiz run in too. 
anyway, my question is, i dont have a trash logo on right bottom corner, as it used to be, it just gone, it wasn't like that before... i've tried to "add to panel" option and click on "garbage bin" but it didn't make any different, it just don't appear. after a while i notice, that there is one vertical line, and that is the garbage bin. does anyone how to bring back my trash logo??
it's funny, but it's important...

cheers'

Try a Ctrl-Alt-Backspace.  And log back in, seems to fix mine when it breaks.

---

### Post by davarse on 2008-06-13
it doesn't work, still the same. i've tried it few times

---

### Post by alienexplorers on 2008-06-13
Do you have the file home/username/.gnome/gnome-vfs/.trash_entry_cache......  Mine was misssing and so was my trashcan.  rebuilt that directory and the trash can came back.

---

### Post by forestpixie on 2008-06-13
There might be another way to get it back but when I had to do same I opened ```
gconf-editor
``` from Alt+F2 - navigated to apps - nautilus - desktop - enabled trash on desktop and then dragged it to the panel.

---

### Post by davarse on 2008-06-13
> **forestpixie said:**
> There might be another way to get it back but when I had to do same I opened ```
gconf-editor
``` from Alt+F2 - navigated to apps - nautilus - desktop - enabled trash on desktop and then dragged it to the panel.

i've tried that but it doesn't work, trash icon on panel still invisible

---

### Post by davarse on 2008-06-13
> **alienexplorers said:**
> Do you have the file home/username/.gnome/gnome-vfs/.trash_entry_cache......  Mine was misssing and so was my trashcan.  rebuilt that directory and the trash can came back.

i dont have home/username/.gnome/gnome-vfs/.trash_entry_cache, mine is /.gnome2, 
and how do you rebuilt that missing directory???

cheers'

---

### Post by SunnyRabbiera on 2008-06-13
the trashicon has a bug it seems.
I found that if you restart it usually comes back.
But I used gconf editor to just make a desktop shortcut to the trash bin.

---

### Post by _sphinx_ on 2008-06-13
I also don't have garbage icon on my right-buttom corner after I have updated to Hardy and I am sure that it was there in previous version. Any ways I usually go through the nautilus' left bookmarks way though it would be great if I can fix it.

---

### Post by TeoBigusGeekus on 2008-06-13
I had a problem in Gutsy (or was it Hardy?) once, where the trash icon wouldn't appear on desktop no matter what I tried. It was after a little experiment with screen resolutions I remember.
What I did was to delete all the contents of the ~/.nautilus folder and then reboot the pc: everything was then back to normal.
Try it and post us what happened.

---

### Post by _sphinx_ on 2008-06-13
Nope..I deleted /.nautilus. No help..

---

### Post by Hutom on 2008-09-02
Is there any solution? I too have the same problem. My trash icon is missing from the lower panel. How to bring it back? I am using Hardy.

---

### Post by porchrat on 2008-09-02
you know that if you right-click on the bottom panel you can go to "add to panel" and then select the trash icon...does that not work for any of you?

---

### Post by davarse on 2008-09-04
this problem is solved for me... i just update and it appear again...

---

### Post by RGPerson on 2009-02-17
> **porchrat said:**
> you know that if you right-click on the bottom panel you can go to "add to panel" and then select the trash icon...does that not work for any of you?

It doesn't work for me.  I can also NOT add icons to the Desktop. I tell them to go there and nothing shows up.

I don't know when the problem started.  We added some software.  Real Player 11 and then a couple of radeo programs.  Then we noticed we couldn't open Computer anymore.  Can't say it started then. Just that we noticed it then.  In another thread, it was suggested to get the source files for Nautilus.  I did that through a .deb file someone offered.  I then watched Nautilus uninstall.  It apparently never reinstalled.  So we were without completely.  We got another File Manager to get us through in the meantime and I kept looking.  Eventually found a threat on reinstalling Nautilus. I did that and most of it is back in business.

I'm just left with these two problems.  No Trash icon and no icons on the desktop.

I've looked in my home\username\.gname\gnome\gnome-vfs folder.  While ls does not show me anything when I try to add trash-entry-cache or whatever it was, I'm told it already exists. 

I still have no trash. 

Gabrielle

---

### Post by RGPerson on 2009-03-01
We did get this fixed. I'm sorry to stay that because I didn't post that right away, I've forgotten how we fixed it.  I found it in rounabout ways through bug reports and such.  It had to do with something, a service, I think, not stopping properly with log out.  I followed instructions to edit some conf file to make sure it did so and voila, after a restart, my trash and desktop icons were back.

Gabrielle

---

