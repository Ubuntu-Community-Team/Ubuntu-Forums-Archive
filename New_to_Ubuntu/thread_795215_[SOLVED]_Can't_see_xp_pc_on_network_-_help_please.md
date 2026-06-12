---
title: "[SOLVED] Can't see xp pc on network - help please"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by naggis on 2008-05-15
My laptop is dual booted with Hardy and xp. The xp boot can see my xp desktop and share files with it. 
At one stage in the last couple of days, Hardy has been also able to see the desktop and share files. But not any longer. If I try to connect the laptop using Place > Network, I can see Windows Network which contains a workgroup called Workgroup which has as its only part, the dual boot setup on the xp part of the laptop. The workgroup containing the desktop is called HOME and there seems to be no way to get to it. 
Using System > Network Tools, I can't trace a route to the desktop.
As you can imagine, having the setup running and now not running is very frustrating. It just points to the fact that I did not know what I was doing and was fortunate in the first case to stumble on something that worked. What I need to know is how the system works so that I can follow things through.
Can you throw any light on the situation or possibly point to a tutorial which shows how to do it, preferably without using too much terminal work - its a bit confusing for an almost ex Windows newbie.
Thanks in anticipation

---

### Post by Kobalt on 2008-05-15
Did you try connecting to your shared folder using this tool: Places > Connect to a server > Windows Share ? You can use your desktop IP address to connect rather than the machine *name*.

---

### Post by naggis on 2008-05-15
Hi,
Yes I did try this and the error message was - Can't display location "smb://192.168.0.2/" "Location is already mounted"
This would make me think that it is all setup and it is just me who doesn't know how to see the mounted location
Does it make any sense to you?
EDIT
I tried this yet again and the second message this time was that there was no application registered to handle this

---

### Post by naggis on 2008-05-15
Having tried this a number of times, there seems to be no particular pattern regarding which error message comes back. Has anyone any idea why the error should not be constant?

---

### Post by naggis on 2008-06-03
Just to finalise this post. The problem was caused by xp on the desktop. Despite having switched off the Windows firewall and checked it a number of times, I found that it was still active on the network. This conflicted with NOD firewall and stopped all operations - nice one Bill!

---

