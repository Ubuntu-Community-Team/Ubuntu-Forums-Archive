---
title: "NVIDIA X Server Settings"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by Alan Bradley on 2012-11-04
For some reason my changes to my NVIDIA settings always reset back to the default after a re-boot. What am i doing wrong that they dont save?

---

### Post by resruta on 2012-11-04
Have you tried the "Save to xorg.conf" option?
If you have some special configurations or even created a xorg.conf, I would suggest ```
$ mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
``` before trying the option, so that you can easily restore the old status.
If there ain't no xorg.conf, you can restore the old status by deleting the one created by the nVidia-tool. Just in case things got worse…

---

### Post by Alan Bradley on 2012-11-11
Its seems to be working now. But a strange thing happens, sometimes I see the NVIDIA splash screen at startup and sometimes I dont. Not quite sure what that means.

---

### Post by Bashing-om on 2012-11-11
Alan; Hi !

Do you have an /etc/X11/xorg.conf file ? If so there is an option that can be edited in to not show the Nvidia splash screen. Right off the top of my head I do not recall where the option goes, google/search will find it .

Remember to back up files prior to editing !!
[INDENT][INDENT]try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by mag1strate on 2012-11-11
> **Alan Bradley said:**
> Its seems to be working now. But a strange thing happens, sometimes I see the NVIDIA splash screen at startup and sometimes I dont. Not quite sure what that means.

It should show up every time. Are you settings resetting when it doesn't show it?

---

### Post by Bartender on 2012-11-12
I have a document on our PC called "PCNotes.odt".  Every time I run across some problem, then you guys help me find the answer, I try to remember to make an entry into that document.

So, let me see, where is it?  OK, here we go...

[I]Easier way &#8211; Alt+F2, then type in 

gksudo nvidia-settings

Changes will be saved to xorg if you click apply then save to x configuration  [/I]

If you don't go into nVidia settings using the above command, it doesn't save the settings.  See if that helps.

---

