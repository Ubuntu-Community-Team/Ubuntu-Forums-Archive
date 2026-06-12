---
title: "Download .. Could not be saved because you cannot change the contents of that folder"
date: 2016-01-29
forum: New to Ubuntu
---

### Post by terry44 on 2016-01-29
I'm new, I'm old, and I think I have messed up and deleted something important. Now when I try to download from Firefox I get the above message. Also my Apps are gone when I click A. I downloaded Chromium from the software centre and it did download and show in the panel but will not open. I got Ubantu 14.04 installed for me and I'm thrilled that I even got this far but I have overreached I think ? Thank you , Terry

---

### Post by ajgreeny on 2016-01-29
Open up Firefox and go to Edit ->Preferences ->General tab to see where you have chosen your downloads should go; by default it is to the Downloads folder in your home so there should be no problem saving anything there.

It sounds as if perhaps there are permission problems in your system so for a start open a terminal and type ```
ls -la
``` then Enter and copy the output back here by highlighting it with the mouse as normal then right clicking->copy.

You can now paste that text in a reply back here using code-tags (see my signature for a code-tags how-to).

---

### Post by oldos2er on 2016-01-29
What did you delete?

---

### Post by Habitual on 2016-01-29
Go to any site and ask for a download file.
Right mouse click in Firefox on the download link and choose a directory in your "home" directory.
/home/<user>Downloads is the usual place.
When you do this and save it, all future downloads should auto-magically download also to /home/<user>Downloads

---

### Post by terry44 on 2016-01-30
Sorry for the delay. When I checked the Firefox download to options there was no downloads option in the list. And that leads me to the fact that there is no downloads in my dash either except under bookmarks ! I've done something very wrong I think ! As regards opening the terminal and typing ls -la , when I did this the terminal closed ! Thank you for your help.

I'm sorry I don't know , I thought it was temporary file but I think it may have been the cache !

when I try to save any download now it gives the " could not be saved because.. " message ! I'm afraid the "home" folder is empty and not recognised ! Sorry !

---

