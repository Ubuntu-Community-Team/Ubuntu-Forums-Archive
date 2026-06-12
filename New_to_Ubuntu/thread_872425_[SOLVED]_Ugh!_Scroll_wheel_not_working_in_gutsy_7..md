---
title: "[SOLVED] Ugh! Scroll wheel not working in gutsy 7.10"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Racecar56 on 2008-07-28
Hi! I have a acer laser mouse, here are the stats...
 ____________________
|(P/N)MS.N1204.001   |
|(S/N)344102808145   |
|(MFG YEAR)2007      |
|____________________|

Using VMware Workstation 6.0.4 build 93057 on a Windows Vista Home Premium.
VMware tools 7.2.9 build 93057, any help? Thanks! :)

EDIT: D'oh! I found a solution! Maybe I should use Google search before I post...

EDIT 2: For people stumbling on this thread wondering how I did it heres the link...

[http://www.tipstrs.com/tip/89/Enable-mouse-scroll-under-VMware-guest](http://www.tipstrs.com/tip/89/Enable-mouse-scroll-under-VMware-guest)

If you can't get to that page here is what it says...

_________________________________________________________________________________________________________________
In case where using guest Linux under VMware, mouse scroll does not work.
To fix this, open terminal and type the following:
sudo gedit /etc/X11/xorg.conf
Then find "InputDevice" section with Identifier "Configured Mouse"
Change Option "Protocol" "ps/2"
to Option Option "Protocol" "IMPS/2"
Last restart X using Ctrl + Alt + Backspace. [COLOR="Red"]NOTICE: This restarts without confirmation.[/COLOR]
_________________________________________________________________________________________________________________

---

