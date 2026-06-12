---
title: "Automount/Desktop icons not working in hardy"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by linuxlizard on 2008-05-14
Hey all,
Can someone help me fix my automount/Desktop icons in Hardy?

I put a disk in my cd drive and nothing appears on the desktop.

If I click on the disk in the places menu, or if I click on one of my hard drives in the places menu, nothing happens on my desktop.

If I click again a second later, nautilus opens up.

I'd like for nautilus to open when I put a cd in the drive.

I'd like for nautilus to open when I click on one of my hard drives in the places menu.

Thanks!

PS- when I run gconf-editor it shows that the following are checked:

media-automount
media-automount-open

---

### Post by bmac on 2008-05-14
Open "File Manager"
Select: edit/preferences

On "Behavior Tab" select 
"Always open in browser windows"

On "Media Tab" select
"Open File" for all Media Handling
Check box at bottom for "Browse media when inserted"

Hope this helps...

---

### Post by linuxlizard on 2008-05-14
Now when I insert a cd, the file manager loads up properly.

That helps, thank you very much:)

But when I click on my other hard drives under places, nothing pops up until I click again a second or two later. I *think* that it's mounting them the first click, but not opening the file manager until I click again. Any way to get it to do both in one click?

Thanks much for help so far!

---

### Post by bmac on 2008-05-14
No, I don't. Hopefully, someone else might...
But I could visualize a downside to doing that. Every time you started Hardy multiple file browser windows would open as it auto mounted each device.

---

### Post by linuxlizard on 2008-05-14
Well, I don't want the hard drives to auto-open/mount into nautilus unless if I click on them first in the places menu. That's how it worked for me in gutsy out of the box. Places-the drive one click opened it in the file manager.

---

### Post by linuxlizard on 2008-05-16
No one knows eh?
:confused:

---

