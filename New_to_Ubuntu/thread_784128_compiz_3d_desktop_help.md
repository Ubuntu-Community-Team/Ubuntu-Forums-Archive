---
title: "compiz 3d desktop help"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by mills on 2008-05-06
OK, I'm running around in circles here and i cant think of anything else to do I'm sure its simple but its evading me.

cant get the 3d cube to work
i got the drivers installed and i got wobbly windows
I've installed advanced desktop effects settings
ticked the 3d cube option and turned off desktop wall
gave skydome a suitable png image checked skydome check box

and not really sure what to do now
one thing i noticed that might be a problem is that although it shows 2 desktops in the bottom left corner, i can't switch to the other one



i feel like I'm using Ubuntu for the first time its been that long

---

### Post by Bodsda on 2008-05-06
in the general settings plugin in ccsm change desktop numbers to 4, make sure 'rotate cube' is ticked aswell

---

### Post by mills on 2008-05-06
its not letting me change the number of desktops, its stuck on 1

and i cant see a "rotate cube" option, if you meant the "enable desktop cube" option on the left the its checked

---

### Post by mills on 2008-05-06
are nvidia 7900's even capable of 3d cubes?

---

### Post by Achtung on 2008-05-06
If you haven't done so already, install "compizconfig-settings-manager" through synaptic.

> **mills said:**
> its not letting me change the number of desktops, its stuck on 1
Click System/Preferences/Advanced desktop effects settings. This will open the ccsm. Under the "General" category, click the "General options" option. Click the "Desktop Size" tab. Set your "Horizontal Virtual Size" to "4" and your "Vertical Virtual Size" & "Number of Desktops" to "1".

> **mills said:**
> and i cant see a "rotate cube" option, if you meant the "enable desktop cube" option on the left the its checked
Still in the ccsm, underthe "Desktop" category, the 7th option is "Rotate cube", which you need enabled to activate the cube. Enable it if it's not enabled yet. Click the "Actions" tab. Click the black arrow to reveal the "General" actions. The first one, "initiate", tells you your key & mouse combo to activate the cube. The default is ctrl+alt+left click. 

While pressing ctrl+alt, left click and hold your click. Move the mouse around to manipulate the cube. Let go of the mouse button to switch back to normal view.

---

### Post by mills on 2008-05-06
> Click System/Preferences/Advanced desktop effects settings. This will open the ccsm. Under the "General" category, click the "General options" option. Click the "Desktop Size" tab. Set your "Horizontal Virtual Size" to "4" and your "Vertical Virtual Size" & "Number of Desktops" to "1".


still couldnt set it to more than one desktop but....

> Still in the ccsm, underthe "Desktop" category, the 7th option is "Rotate cube",

couldnt see the wood through the trees, it worked, got the 3d cube, a little puzzled as to why i cant set the number of desktops to more than 1 even though its now giving me the 4 i need but i can live with it

much appreciated

---

### Post by philinux on 2008-05-06
I've seen this - this option for number of desktops is greyed out. I wondered about this but gave up.

---

### Post by Achtung on 2008-05-06
Increasing the number of desktop would give you multiple cubes, which is not what you want. I find it's actually a pretty good thing they grayed out that option ;)

---

### Post by mc4man on 2008-05-06
> little puzzled as to why i cant set the number of desktops to more than 1 even though its now giving me the 4 i need
what your setting is the number of workspaces (sides of cube), 4 works out nicely but you can have up to 16 - another way to adjust is r.click on workspaces in lower panel->preferences-> adjust # of columns

---

### Post by Periswell on 2008-05-06
if nothing else works, get beryl instead. it what i did.

---

### Post by Paqman on 2008-05-06
> **mills said:**
> are nvidia 7900's even capable of 3d cubes?

Hell yes. I have an Nvidia 7300 and all the desktop effects are as smooth as butter.

You want to have one desktop, but in CCSM general settings set a horizontal size of 4, vertical size 1.

---

### Post by ckata on 2009-02-12
Thanks! My settings disappeared the other day, and this response helped me get my 4 desktops back again!

Thanks!

---

### Post by Khru on 2009-04-17
This worked and I am blown away! Thanks

---

