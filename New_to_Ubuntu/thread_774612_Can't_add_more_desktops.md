---
title: "Can't add more desktops"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by lintoon on 2008-04-29
Hi,  I am trying to enable more desktops so I can play about with the compiz settings (eg desktop cube).  I had it working ages ago but turned it off to gain some speed. 

I have gone to System-Preferences-Advanced Desktop Effects Settings which brings up the Compiz Settings Manager.  I then go to General options-Desktop Size and try to increase the Number of Desktops option to 4.  It will not go past 1.

Am I missing something obvious here?

I nearlly forgot to mention that I upgraded to Hardy a couple of days ago.

---

### Post by Absorbed on 2008-04-29
I add more workspaces by right clicking on the desktops next to the trash at the bottom right, and then selecting preferences. Adding further workspaces is self-evident from there. Hopefully that will solve your problem; it has worked for me in the past.

---

### Post by lintoon on 2008-04-29
Thanks for your reply Absorbed. I changed it to 4 columns and 1 row and it's worked.  Now I've got my spinny cube back.  

Cheers.

---

### Post by spacefreak86 on 2008-04-29
I did this too, but it keeps reverting back to only two desktops, and even then, I can't get the cube to work at all. Does anyone know why this might be happening?

---

### Post by forrestcupp on 2008-04-29
In the Advanced Desktop Settings in General Options in the Desktop Size tab, you need to change the **Horizontal Virtual Size** to 4 instead of trying to change the number of desktops.  Leave the number of desktops set at 1.

---

### Post by Absorbed on 2008-04-29
> **spacefreak86 said:**
> I did this too, but it keeps reverting back to only two desktops, and even then, I can't get the cube to work at all. Does anyone know why this might be happening?

I have no idea why it is reverting back to two desktops. When does it revert back? If you give a few details maybe someone else can help.

As for the cube, you need to make sure you've enabled it in the Advanced Desktop Effects Settings. You can install it using Applications -> Add/Remove... and searching for it. Once it's installed you can open it from System -> Preferences. Put a tick next to "Desktop Cube" and you should be set to go. Edit: You also need to tick "Rotate Cube".

If you haven't, you'll also need to change System -> Preferences -> Appearance. On the Visual Effects tab, you need to select Extra.

---

