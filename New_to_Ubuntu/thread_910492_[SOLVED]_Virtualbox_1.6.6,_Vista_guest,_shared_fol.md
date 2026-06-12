---
title: "[SOLVED] Virtualbox 1.6.6, Vista guest, shared folders?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-09-04
I have looked around, and I can't find the answer to my question.

My question is, how can I set up folder sharing with host Ubuntu 8.04 and guest Vista Business? I have no idea how to network anything together, so please step by step. I want to share the folder /home/username/. I want Vista to be able to have access to my home directory.

---

### Post by meborc on 2008-09-04
first off you need to define a folder as shared folder in the settings tab in VB (the yellow ring-thingy)

if that is done read this: (copied from an old howto i found, author unknown)

[COLOR="DarkRed"]this worked with my XP, don't know if it works with vista[/COLOR]

> **[COLOR="DarkRed"]IN WINDOWS[/COLOR]**
You can also map the network drives now, so your VM has access to your real disks. They are available through windows networking. Just create a new network location through the windows wizard and browse to the VirtualBox shared folders (assuming you set them up earlier):

You can also open a command prompt (yes windows has them too! and type:

Code:

net use x: \\vboxsvr\sharename

where x: is the drive letter you want to assign, and sharename is the name you gave to the location in VirtualBox configuration earlier.

---

### Post by slughappy1 on 2008-09-04
Awesome Thanks! It worked perfectly first try. The steps I used are:
[LIST=1]
[*]BEFORE LOADING OS, Click on the yellow gear icon ( Settings )
[*]Click on the Shared Folders Icon
[*]Click on the folder with a green plus sign on it, "Adds a new shared folder definition."
[*]Click browse and find the folder you want to share
[*]Give it a name in "Folder Name"
[*]Click the "OK" button
[*]Start Windows Vista
[*]Open cmd.exe
[*]type in "net use x: \\vboxsvr\"Folder Name You Gave"
[*]DONE! Now it is in My Computer
[/LIST]

---

### Post by meborc on 2008-09-04
glad that helped you... i can now mark that howto to also work with vista :)

---

### Post by jbrisko on 2008-09-22
Hey Guys,
         I just wanted to post here to give a more accurate fix for this problem. I come from a long background of Windows Administration. You are all correct the problem stems from Vista's UAC. However, what happens is Vista runs the Normal users, and Administrators totally separate. I ran into a problem like this setting up Login Scripts for some of my clients. So an easy fix, that will allow you to keep your UAC on, which is recommended follows.

Go into your Registry Editor in your Guest OS Vista. (Hit start, and type regedit)

Navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System

Check to see if there is a DWORD value for EnableLinkedConnections, if there is be sure to set it to 1, otherwise add this variable, and set it to 1, and your Vista installation will allow linked connections between the Admin and the Normal users. Hope this helps, I just ran across this problem and wanted to help anyone else who may be in my boat.

Thanks,
        Jeremy

---

