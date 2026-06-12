---
title: "compiz fusion and emerald"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by CrimsonV on 2008-05-25
How do i set up compiz fusion and emerald on Ubuntu 8.04 
I have no experience with coding
but i have installed the 2 programs but idk how to start them

---

### Post by sayakb on 2008-05-25
At a terminal:
```
sudo apt-get install emerald compizconfig-settings-manager
```By default, if you have a compatible graphics card, Ubuntu should be using compiz. To change the settings, goto System->Preferences->Advanced desktop effects settings.

Plus, you might use the emerald theme manager by executing:
```
emerald --replace &
```at a terminal. Download emerald themes from gnome-look.org

---

### Post by CrimsonV on 2008-05-25
thank you
can u also please tell me how to get the cube interface working/how to make the windows shake

thanks again

---

### Post by sayakb on 2008-05-25
Open advanced desktop effects settings as indicated above. There, enable Wobbly Windows, Desktop Cube, Rotate Cube, Cube Caps and Cube Reflection :)
To rotate cube right/left, press Ctrl+Alt+right/Ctrl+Alt+Left

---

### Post by sayakb on 2008-05-25
Also, is you want a true 3D effect, click on Desktop Cube in the Advanced desktop effects settings (ccsm), and click on Appearance tab, and there, inflate Skydome. Check both of the Skydome and Animate skydome checkboxes. Then add a large image at the skydome image area. You might keep the Cube Reflection disabled so that skydome looks even better. ;)
Regards
Dave

EDIT: To hold and rotate the cube and to make the skydome even more appealing, goto Rotate cube in ccsm and slide the Zoom factor to 0.4000. Now, press Ctrl+Alt+Button1 (Left mouse button) on an empty desktop to freely rotate the cube.

---

### Post by CrimsonV on 2008-05-25
i have done as u said, but all i get when i use ctrl+alt+left/right
is the normal desk switch
and the windows so not shake when i move them:(

---

