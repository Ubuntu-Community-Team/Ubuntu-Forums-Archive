---
title: "Where in the filesystem is the trash stored?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by sum janus on 2008-08-25
Hey,
Where in the filesystem is the trash stored?  I ran into that "cannot delete... directory not empty" conundrum with a folder in my trash, so I'd like to rm -r it through the CLI.  But how do I get to the trash?

Thanks,
-Eric

---

### Post by 67comet on 2008-08-25
Usually your trash is in /home/<your login>/.Trash (the . before the text makes is invisible).

Also if you mount a USB stick or what not, .Trash will be written to the stick too, so it would be /media/USB/.Trash .

Hope this helps.

To see invisible items via CLI just use ls -al or ls -alh to see them all and their size, user, group info.

---

### Post by aloshbennett on 2008-08-25
~/.local/share/Trash

---

### Post by nothingspecial on 2008-08-25
Click on Places
Click on Home Folder
Press Ctrl + H
Your hidden files including .Trash will appear.

Click on your usb stick or externel drive in Places
Press Ctrl + H

---

### Post by Crafty Kisses on 2008-08-25
-Do Alt+F2
-Type gksudo nautilus and enter your password
-You should now be in your root folder
-Navigate to your home folder and enter the hidden folder .Trash (To view hidden files and folders do Ctrl+H)
-Go back to the Root folder
-There is a .Trash in there as well if it doesn't show try Ctrl+H again


Hope this helps...

---

### Post by philinux on 2008-08-25
> **aloshbennett said:**
> ~/.local/share/Trash

There is no .Trash file in home under 8.04, it's as above.

---

### Post by nothingspecial on 2008-08-25
> **philinux said:**
> There is no .Trash file in home under 8.04, it's as above.

Sorry, still on Gutsy here.
Just trying to tell the OP that you can view hidden files gui style aswell.

---

### Post by sum janus on 2008-08-26
Thanks!  This did the trick for me.

I'm on 8.04, so that was the correct location for Trash ;-)

---

