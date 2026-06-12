---
title: "How do I adjust the number of workspaces in Unity?"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mmasroorali on 2011-10-07
The question says it. I tried the approach at [http://ubuntuforums.org/showthread.php?t=1723321](http://ubuntuforums.org/showthread.php?t=1723321), but Compiz Config Settings Manager is not there.

I have even installed CompizConfig Settings Manager, logged out and logged in. Still it is not there.

Any help will be appreciated.

---

### Post by cariboo on 2011-10-07
You can set the number of workspaces using the Genral Options->Desktop Size.

---

### Post by arpanaut on 2011-10-07
ccsm is not in system settings anymore.
Open dash and type ccsm and it will appear.
launch it from there.
then you can change your settings in ccsm

---

### Post by mmasroorali on 2011-10-07
> **cariboo907 said:**
> You can set the number of workspaces using the Genral Options->Desktop Size.

Perhaps I am missing something here, Desktop Size is not in there. Please see the attached image.

---

### Post by cariboo on 2011-10-07
If you have compizconfig-settings-manager installed, open the dash by clicking on the icon at the top of the launcher and type:

```
ccsm
```

then click the icon.

---

### Post by mc4man on 2011-10-07
If using unity (3d) then re-read post 3
In ccsm the setting is in the general options - see screen
The 1st. 2 options are valid. leave the 3rd one alone

If using unity-2d then say so.

---

### Post by thatguruguy on 2011-10-07
> **mmasroorali said:**
> Perhaps I am missing something here, Desktop Size is not in there. Please see the attached image.

You're right, you're missing something.  You're looking in the wrong place.

Open CCSM, click on General Options.  Click on the "Desktop Size" tab.  Set the Horizontal Virtual Size and Vertical Virtual Size however you see fit to create the number of workspaces you want.

---

### Post by mmasroorali on 2011-10-07
Thanks. ccsm worked for me. Though it froze everything in the first try. I had to move to basic terminal mode using Ctrl-F1 and killed ccsm. That did not help. Then I had to reboot. In the second time ccsm helped me setting the number of workspaces.

---

