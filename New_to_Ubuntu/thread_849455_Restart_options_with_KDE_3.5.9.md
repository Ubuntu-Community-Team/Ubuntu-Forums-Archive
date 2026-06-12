---
title: "Restart options with KDE 3.5.9"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by gizmobay on 2008-07-04
I have a dual boot system. In my previous distro, I had a pulldown menu with restart that gave me options to reboot into a different OS. On Kubuntu, I don't have those options. I did some searching on the forums and I read that under kcontrol logout manager and switching the shutdown to GRUB would fix this. It didn't work. Am I missing a package or anyone have a way to get this to work? I'm using grub.

---

### Post by nowshining on 2008-07-04
u can try asking this Q on kubuntuforums.net or searching there - i put up a post explaining how to remove the restart/logout, etc.. options from the menu, etc..

Maybe something in there ie: an option might work :) - but u gotta figure that out on ur own. Try diff. names, etc..

---

### Post by gizmobay on 2008-07-04
I figured out the problem. When I installed, KDE4 was installed so I had kdm for KDE4. When I installed KDE3.5.9, kdm wasn't installed. I installed kdm for KDE3 and changed the shutdown to grub and I know receive the boot options.

---

### Post by nowshining on 2008-07-04
u could of installed gdm :) but if u like kdm then k. :)

---

