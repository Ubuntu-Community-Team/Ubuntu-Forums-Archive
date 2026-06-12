---
title: "Where is graphics card driver settings GUI ?!/"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by Coder88 on 2013-09-11
I am looking everywhere but i can not find the interface to set/change the graphics card driver. Ubuntu 13.04 (just installed), Gnome desktop. I swear I came across this GUI interface earlier today but I can not find it again.

---

### Post by r_avital on 2013-09-11
At a terminal prompt, enter software-properties-gtk

Or, in the launchpad, type "software & updates" (no quotes).

Either way, it will take a few seconds before it runs, might seem like a long time.  Once it opens, the last tab "Additional Drivers" will show you what (I think) you're looking for.

---

### Post by Coder88 on 2013-09-11
But shouldn't it be someone in the GUI menus, so a user does not have to know what obscure command (software-properties-gtk) to type? Okay so i just found the equivalent, but wow what a place to HIDE the graphics card settings--- I open Synaptic then Repositories (gee, who would have thought the graphics card driver setting might be in a REPOSITORIES submenu? wtf? C'mon Ubuntu let's make this one better.

So in the Synaptic: Repositories submenu: there is a tab for Additional Drivers which shows the graphics card driver choices. But wow, there really should be a clearer menu choice, like 
 Applications: System Tools: Graphics Card Driver
or something like that.

---

### Post by deadflowr on 2013-09-11
Ubuntu tries to promote free software, so is stands to reason that the would design a system that makes installing closed source drivers harder.
Though not impossible.

---

### Post by r_avital on 2013-09-11
> **Coder88 said:**
> So in the Synaptic: Repositories submenu: there is a tab for Additional Drivers which shows the graphics card driver choices. But wow, there really should be a clearer menu choice, like 
 Applications: System Tools: Graphics Card Driver
or something like that.

In a sense, I agree with you.  When I was a total newbie to Linux, coming from the Windows world, I logically expected something similar.  But this arrangement in Ubuntu makes sense, if you consider that pretty much all Linux distributions get the vast majority of their software, including drivers, from approved repositories.  It sounds limiting, but once you see the sheer wealth of software packages available, you'll really hardly ever need anything from a non-approved repository.  Approved repositories also mean you minimize the risk of getting malware (like I used to anytime I wanted some MP3 extracter or tag-editor, for instance).

I do disagree with the approach of discouraging proprietary drivers.  For anyone who wants to practice that religion, there's Debian, a truly respectable distro (upon which Ubuntu is based) that bends over backward to keep everything open-source, so much so that they almost got into a legal battle with Mozilla a few years back, over allowing Debian users to treat Thunderbird and Firefox icons/names as public-domain intellectual property (if you're curious, google-up icedove and iceweasel).  

When Ubuntu or anyone else's open-source drivers, particularly graphics drivers, equal or exceed the performance of proprietary drivers, that argument will make sense, until then, please stop hiding stuff from us.

---

### Post by QIII on 2013-09-12
If I am not mistaken, in Unity the "System Settings" icon shows by default in the Launcher.  If not, Click "Dash home" and type "System Settings", then drag the icon to the Launcher.

Click that, and look for the icon labeled "Additional Drivers".  That's how Canonical has set things up.  No different than Windows.

How it is laid out in GNOME is something you will have to discuss with the GNOME developers.

There is no attempt to make installing proprietary drivers harder.  The Linux community has no control over them.  Either the OEM makes the driver installation work, or they don't.

---

### Post by buzzingrobot on 2013-09-12
The OP is a bit unclear if he wants to install a video driver or adjust the properties of the current diver.

 the latter can typically be done via entries in the "Settings" or "System Settings" panels.

If the closed AMD or Nvidia drivers are installed, then their proprietary settings tool should also be installed.

In straight Ubuntu 13.04, new drivers are available via the "Additional Drivers" tab in Software Sources.  In Ubuntu Gnome, it is located wherever the builders of that distribution chose to put it, but I believe it's in a similar location.

Since all packages come from the repositories you configure in Software Sources, they will all be visible in any tool used to access those repos, including Synaptic.

---

