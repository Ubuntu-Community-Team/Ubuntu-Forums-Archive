---
title: "Desktop off Limits"
date: 2011-05-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-05-31
Have been seeing this behavior for a couple of days and wanted to make sure that this is the normal at this point in time. Nothing will stick to the desktop and the normal right click on it does not bring the usual drop down menu. With all the changes of gnome 2 to gnome 3 was not sure if that was the reason or a bug needed to be filed.

Thanks Bill

---

### Post by Joe of loath on 2011-05-31
That is correct, Gnome 3 places less emphasis on the desktop, more on maximised windows.

---

### Post by SevenMachines on 2011-05-31
try running 'gnome-tweak-tool'
and switch 'file manager->have file manager handle the desktop' on

the desktop is apparently doomed! i guess it was deemed a little too much of the fear at the one time though :)

---

### Post by teh603 on 2011-05-31
> **SevenMachines said:**
> try running 'gnome-tweak-tool'
and switch 'file manager->have file manager handle the desktop' on

the desktop is apparently doomed! i guess it was deemed a little too much of the fear at the one time though :)Things still stick to the desktop in Kubuntu...

---

### Post by Joe of loath on 2011-05-31
> **teh603 said:**
> Things still stick to the desktop in Kubuntu...

Only if you have the 'Desktop' applet enabled, though ;)

---

### Post by SevenMachines on 2011-05-31
think gnome and canonical have both come to the same conclusion with all their gui testing and research stuff (hazily remembered, not a fact!) so it may way come to pass eventually over years to come. with windows not easily minimised/maximised in unity i've been getting used to using the file manager to fiddle on the 'desktop' directory and have now much less of the fear...

---

### Post by teh603 on 2011-05-31
> **Joe of loath said:**
> Only if you have the 'Desktop' applet enabled, though ;)Its called Folder View. Although I've had a fair bit of luck dragging icons out of Dolphin onto the desktop itself- for example, I keep a firefox icon on the parents' desktop, and I've been able to drop folder icons as well.

---

### Post by sparker256 on 2011-05-31
> **SevenMachines said:**
> try running 'gnome-tweak-tool'
and switch 'file manager->have file manager handle the desktop' on

the desktop is apparently doomed! i guess it was deemed a little too much of the fear at the one time though :)
Tried that and got the following error when trying to run it in terminal. 

My bigger issue is how do I get a bash script into the unity launcher? Before I could make a launcher on the desktop and move it to the unity launcher. Now that this is gone, how do you do this? If there was a drop down menu selection from a right click called "copy to> unity launcher" all this would be mute.

 Thanks for reading my attempts at making sense of all this. I love windows and that is not MS version but multiple windows on a desktop. If I have lost that I will be looking for another option but also love Ubuntu so I am looking for a better solution.

Bill

---

### Post by SevenMachines on 2011-05-31
think you need gnome-shell installed to sort out the tweak error(?) i had it before but cant remember sadly. not too sure about the best way to get scripts into the launcher, i havent had much time to look up some of the more advanced things you can do with it, i've just right-click->'keep in launcher' whatever. i'm with you on the multiple windows thing, window management is the oddest thing to adapt to with unity i'm finding.

[EDIT] just checked, yes you need gnome-shell installed for tweak

---

### Post by sparker256 on 2011-05-31
> **SevenMachines said:**
> think you need gnome-shell installed to sort out the tweak error(?) i had it before but cant remember sadly. not too sure about the best way to get scripts into the launcher, i havent had much time to look up some of the more advanced things you can do with it, i've just right-click->'keep in launcher' whatever. i'm with you on the multiple windows thing, window management is the oddest thing to adapt to with unity i'm finding.

[EDIT] just checked, yes you need gnome-shell installed for tweak
You were right I did not have gnome-shell installed but now do and error is gone. Will report back what I find.

Ps it was already on I just could not see it..

Bill

---

### Post by el_koraco on 2011-05-31
> **teh603 said:**
> Its called Folder View. Although I've had a fair bit of luck dragging icons out of Dolphin onto the desktop itself- for example, I keep a firefox icon on the parents' desktop, and I've been able to drop folder icons as well.

You can make the whole desktop act as the "Folder view" style, and have a "normal" desktop in KDE. Drag and drop icons works the same as in Windows or the old KDE then.

---

### Post by mc4man on 2011-05-31
> **sparker256 said:**
> T

My bigger issue is how do I get a bash script into the unity launcher? Before I could make a launcher on the desktop and move it to the unity launcher. Now that this is gone, how do you do this? 
Bill
Create a .desktop,(~/.local/share/applications is a good place),  for the Exec= use scriptname or /path/to/scriptname
or
add a quicklist entry to an existing .desktop or create a .desktop and add script(s) as quicklists
(quicklists can do locations, scripts, binaires, modded binaries, and straight commands inc. env's if desired

Or for gnome-shell use that tweak tool to allow desktop launchers

---

### Post by sparker256 on 2011-06-01
> **SevenMachines said:**
> think you need gnome-shell installed to sort out the tweak error(?) i had it before but cant remember sadly. not too sure about the best way to get scripts into the launcher, i havent had much time to look up some of the more advanced things you can do with it, i've just right-click->'keep in launcher' whatever. i'm with you on the multiple windows thing, window management is the oddest thing to adapt to with unity i'm finding.

[EDIT] just checked, yes you need gnome-shell installed for tweak

My mistake I did not have it on but when I finally did the desktop icons are back and the right click drop down menu is back also. My next issue is to get rid of the extra default desktop icons (Home, ??, Trash) but sure there is some way to do that. If I can not find it will make a new thread for that and also why the "del" key does not work either. Thanks for your input and now on to more testing. I will mark this thread as solved.

Bill

---

### Post by SevenMachines on 2011-06-01
Have a look at the new dconf settings
$ dconf-editor
In 'org->gnome->nautilus->desktop' you should see checkboxes for home-icon-visible, trash-icon-visible etc. I *think* these are what you are looking for hopefully

---

### Post by Joe of loath on 2011-06-01
For some reason you have to use ctrl-del to delete stuff. Don't ask me why.

---

### Post by PaulW2U on 2011-06-01
> **Joe of loath said:**
> That is correct, Gnome 3 places less emphasis on the desktop, more on maximised windows.
I just hate maximised windows.

In the workplace I often have over 10 applications open at any one time. In order to prepare a letter to a client it is often necessary to use information from several applications. If very application was maximised it would be a nightmare toggling between three or four maximised windows trying copy and paste information from one window to another.

At the risk of being misquoted, yes [@!$^%&@] you know who you are, may be this really is a good time to think about moving away from Ubuntu/Unity for good?

I'll certainly boot into the latest build of Ubuntu from time to time to see how development is progressing but for now I think Kubuntu/KDE is the direction in which I wish to go.

---

### Post by Joe of loath on 2011-06-01
> **PaulW2U said:**
> I just hate maximised windows.

In the workplace I often have over 10 applications open at any one time. In order to prepare a letter to a client it is often necessary to use information from several applications. If very application was maximised it would be a nightmare toggling between three or four maximised windows trying copy and paste information from one window to another.

At the risk of being misquoted, yes [@!$^%&@] you know who you are, may be this really is a good time to think about moving away from Ubuntu/Unity for good?

I'll certainly boot into the latest build of Ubuntu from time to time to see how development is progressing but for now I think Kubuntu/KDE is the direction in which I wish to go.

You can use the 'aero snap' feature, I believe you can make Gnome 3 behave like a tiling window manager, too, with any number of windows taking up the whole screen.

Also, window switching is a breeze, much easier than anything else I've used. Try Gnome 3 for an hour or two, see what you think.

---

