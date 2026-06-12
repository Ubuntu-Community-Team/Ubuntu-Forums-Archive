---
title: "[SOLVED] How can I Run Windows VM in workspace 2 fullscreen at startup"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Canis familiaris on 2008-06-25
My sister uses Windows primarily for work but not for gaming. However she faces lots of problem with virii, spyware, etc. I want to install Hardy on her notebook and do this such that she does her work in Windows and uses Ubuntu for surfing the net and transferring files.


[IMG]http://i168.photobucket.com/albums/u178/anurag_panda/Screenshot-1.png[/IMG]


But the problem since she primarily uses Windows for her work would hate to launch Virtualbox anytime.
Is there anyway could I configure such that the Windows VM automatically launches fullscreen on workspace 2 on startup. I would love a command because then I could create a launcher.

Also is there a way could I disable pen drives being mounted in the VM. 
Also how can files be shared b/w Guest OS and Host OS.

Thanks in advance.

---

### Post by Canis familiaris on 2008-06-25
I managed to run Virtualbox in command line with this command
```
vboxmanage startvm VirtualWindows

```
However I am wondering, is there a way it could be run on workspace 2 instead of the current workspace.

Here VirtualWindows is the name of the Virtual Machine

---

### Post by aeiah on 2008-06-25
dont know off the top of my head about your initial question, but stopping usb drives being mounted on the client vm is as simple as just disabling the usb ports being passed through. there should be an option for it in the properties of the vm. to get files shared between host and client you would set up a directory (or several) to be shared via samba and map these network drives in the windows client. i think this can be done using virtualbox so you dont have to get your hands dirty, but its been quite a while since i used it.

---

### Post by Canis familiaris on 2008-06-25
To clarify my point:
How could I run a Window in a specific workspace using command line?

---

### Post by issih on 2008-06-25
You can use one of the compiz plugins to force specific programs to always open on a specific workspace. I forget exactly which one it is...Place Windows maybe. Have a look in ccsm anyway as I'm 100% certain its there. Give me a shout if you can't find it and I'll switch os to find out.

Not exactly what you asked for I know, but it should achieve what you want.

---

### Post by Canis familiaris on 2008-06-25
> **issih said:**
> You can use one of the compiz plugins to force specific programs to always open on a specific workspace. I forget exactly which one it is...Place Windows maybe. Have a look in ccsm anyway as I'm 100% certain its there. Give me a shout if you can't find it and I'll switch os to find out.

Not exactly what you asked for I know, but it should achieve what you want.
Yes there's "Place Windows" plugin but it gives only the option of X or Y coordinates but no option for workspace. Is there any such option?

---

### Post by issih on 2008-06-25
Ok, it is the place windows plugin. Open that plugin up, and go to the "Fixed Window Placement" tab.

Then expand the "Windows with fixed viewport" section by clicking on the little arrow. Hit new, and in the little dialog box hit the + button. In the edit match dialog hit grab, then click on a window of the program you want to position.

Now choose which viewport (workspace) you want indexed from 0-3 along x (assuming you have a cube) and leave y as 0.

From now on programs of that type will open on the workspace you choose.

Note that there is no bounds checking, if you choose x = 500 it will just vanish and be utterly unreachable, so get it right :)

Hope that helps

---

### Post by Canis familiaris on 2008-06-25
> **issih said:**
> Ok, it is the place windows plugin. Open that plugin up, and go to the "Fixed Window Placement" tab.

Then expand the "Windows with fixed viewport" section by clicking on the little arrow. Hit new, and in the little dialog box hit the + button. In the edit match dialog hit grab, then click on a window of the program you want to position.

Now choose which viewport (workspace) you want indexed from 0-3 along x (assuming you have a cube) and leave y as 0.

From now on programs of that type will open on the workspace you choose.

Note that there is no bounds checking, if you choose x = 500 it will just vanish and be utterly unreachable, so get it right :)

Hope that helps
Thanks! That Worked! YOU ROCK!

---

