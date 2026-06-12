---
title: "Where do the clipboards I install go?????"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by sillyboy on 2012-07-02
Just reinstalled 10.04.  12.04 is not ready for primetime yet, for me anyway.  

I installed Klipper from the Ubuntu Software Center.  Where is it?  It shows that it is installed.

I installed Glipper from the SPM (used this file before), that one is MIA also.

I want a clipboard that has a history and copies when the word/phrase  is highlighted.  Parcellite is not what I want.  I tried it.  It's gone.

Any sugestions??

Thanks****

---

### Post by dwhite on 2012-07-02
> **sillyboy said:**
> Just reinstalled 10.04.  12.04 is not ready for primetime yet, for me anyway.  

I installed Klipper from the Ubuntu Software Center.  Where is it?  It shows that it is installed.

I installed Glipper from the SPM (used this file before), that one is MIA also.

I want a clipboard that has a history and copies when the word/phrase  is highlighted.  Parcellite is not what I want.  I tried it.  It's gone.

Any sugestions??

Thanks

Hi, I'm not familiar with clipboard managers but out of curiosity i installed **ClipIt** clipboard manager from the software center (i didn't try installing Klipper as im not running KDE, and it was noted that it doesn't work with 12.04, also clipit has more reviews and rates much higher than Klipper)  anyway ClipIt seems quite nice, i've been able to view my clipboard history, paste in links to my browser and launch websites, but as i've said i have no experience with any other managers to compare it to.

what may be relevant is this, when i start clipit is shows up in the panel, see the attached screenshot just by cursor (possible Klipper is also starting in the panel?)

just attached a screenshot showing the ClipIt menu with several clipboard items that shows up when clicking on the clipit panel item

---

### Post by sillyboy on 2012-07-02
> **dwhite said:**
> Hi, I'm not familiar with clipboard managers but out of curiosity i installed **ClipIt** clipboard manager from the software center (i didn't try installing Klipper as im not running KDE, and it was noted that it doesn't work with 12.04, also clipit has more reviews and rates much higher than Klipper)  anyway ClipIt seems quite nice, i've been able to view my clipboard history, paste in links to my browser and launch websites, but as i've said i have no experience with any other managers to compare it to.

what may be relevant is this, when i start clipit is shows up in the panel, see the attached screenshot just by cursor (possible Klipper is also starting in the panel?)

just attached a screenshot showing the ClipIt menu with several clipboard items that shows up when clicking on the clipit panel item

Clipit nor any clipboard manager is in the "Add to Panel" menu.

There used to be a clipboard in there but, the good things always seem to get lost in the change...

I can't find Clipit anywhere.

Thanks dwhite

---

### Post by dwhite on 2012-07-02
hi,

As long as you have the "indicator applet" in the panel.  Clipit shows up as an indicator.  

i switched to gnome classic and took a screenshot to show you where clipit shows up in the menu, you can also see it in the panel

i'm not sure why clipit wouldn't show up if you are trying to make  a launcher for the panel however

---

### Post by sillyboy on 2012-07-02
> **dwhite said:**
> hi,

As long as you have the "indicator applet" in the panel.  Clipit shows up as an indicator.  

i switched to gnome classic and took a screenshot to show you where clipit shows up in the menu, you can also see it in the panel

i'm not sure why clipit wouldn't show up if you are trying to make  a launcher for the panel however


It is not in there.  I did a search on the web and came up with a fix:
In terminal, type "sudo apt-get install glipper". It showed up in the Add to Panel menu.

If anyone wants a good clipboard manager, Glipper is it!!
I used it before in 8.04. It was in the Add to Panel menu with the install.

Thanks for the help

---

### Post by Rick.B9 on 2012-07-03
If you can't find where a program is installed, in terminal you can use the which command:
[FONT=Lucida Console]which [program name] or whereis [program name.]

Alternatively, go back to Synaptic, if you have it, and search the program you installed.  Highlight the program and look at "installed files" in the info box.  It will tell you where the bin file is; usually /usr/bin, but it could be somewhere else, like /opt.
[/FONT]

---

### Post by sillyboy on 2012-07-03
> **Rick.B9 said:**
> If you can't find where a program is installed, in terminal you can use the which command:
[FONT=Lucida Console]which [program name] or whereis [program name.]

Alternatively, go back to Synaptic, if you have it, and search the program you installed.  Highlight the program and look at "installed files" in the info box.  It will tell you where the bin file is; usually /usr/bin, but it could be somewhere else, like /opt.
[/FONT]

Thanks):P

---

### Post by rewyllys on 2012-07-03
> **sillyboy said:**
> It is not in there.  I did a search on the web and came up with a fix:
In terminal, type "sudo apt-get install glipper". It showed up in the Add to Panel menu.

If anyone wants a good clipboard manager, Glipper is it!!
I used it before in 8.04. It was in the Add to Panel menu with the install.

Thanks for the help
I'm also a fan of Glipper.

But there is one curious feature about installing it: In my experience, after adding it to the panel, I have to restart my computer before Glipper will actually show up in the panel.

---

