---
title: "HOWTO:Typical groups that users should belong to."
date: 2006-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Bigglez on 2006-08-10
I use Kubuntu 6.06 - I hope this works on other *ubuntu releases.

**_The Problem_**
If you make a mistake with a command and find you (or another) user has lost their groups then you might find this list helpful.

**_Clues to group-loss_**
Your sound apps (like KMix) won't work
You might not be able to use sudo.

**_The Solution_**
[LIST=1]
[*]Make sure you can sudo. If not, look for a howto on regaining sudo. (Quick tip: 'addgroup username admin' from recovery mode)
[*]Use the general command:
(Replace your [COLOR="Green"]username[/COLOR] in it, and the group with *one* from the list below)
```
sudo addgroup [COLOR="Green"]username[/COLOR] group
```
Repeat this for each of the following typical groups:
```

adm
dialout
cdrom
floppy
audio
dip
video
plugdev
lpadmin
scanner
admin

```
[*]You might have to re-login to ensure that you are now in the right groups.
[/LIST]

_**Example**_
For user 'billybob'
```
sudo addgroup billybob video
```

**_The End_**
I hope this help someone out there!
Please fix any errors and add/sub groups from my list.

-- keywords to help search --
typical usual standard common groups list cannot no sound what group 
--

---

