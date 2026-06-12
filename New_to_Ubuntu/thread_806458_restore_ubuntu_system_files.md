---
title: "restore ubuntu system files?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-05-25
is it possible to restore ubuntu system files without having to reformat everything on ubuntu? something is wrong with my ubuntu right now, i dont think its a virus...atleast i hope not. i think i just screwed something up. i have a panel at the top of my desktop and when i click on the little button to shut down my computer the panel disappears and i can't shut down my computer properly...is there anything on ubuntu like system restore on windows? so far everything seems to still work fine...i have avant bar at the bottom of my screen, but it takes quite a bit longer for it to appear at start up but i dont notice much else.

edit: k, i was wrong, there is something else wrong. when i try to create a new folder anywhere it tells me there is no free space on the drive. and when i open openoffice it tells me something similar about not having free space on the drive also...

---

### Post by diablo75 on 2008-05-25
Could you take a screenshot of this panel and upload it to a reply here?

Edit:  No free hard drive space... How much free space does your hard drive have?

---

### Post by hyper_ch on 2008-05-25
I think you'd rather need to delete the Gnome config files from your user home.

---

### Post by waggingwabbit on 2008-05-25
i dont think i can take a screenshot.it wont let me create any new things anywhere...the panel is just the one that came with the ubuntu install. the left side has the applications, places, and system menu, and the shut down button is at the far right. when i click on the shut down button that entire bar/panel disappears. what are my gnome config files? do you mean xorg? or is there more to it?

---

### Post by Dazed_75 on 2008-05-28
On the off chance the system is right about the lack of space, you might start by emptying your trash bin.  You could also look for any space hogs you might have lying about and either delete them or move them to another device such as a flash drive.  In any case, empty the trash can last.

You might also open a terminal and type "free -h" without the quotes to get some idea of where you do and do not have free space.  If you make that "free -h > ~/Desktop/free.txt" you should make the file free.txt on your desktop so you can show us the output here.

---

### Post by impert on 2008-05-28
It's a fair bet that you have no free space on your drive. (Surprise!) Assuming your system is not so choked that it won't run at all, try
 Applications>Accessories>Disk Usage Analyzer. Click on the tab "Search file system". Wait until it has finished - it takes a while. Study the large items there, you probably have stuff you can easily do without: inadvertent backups of the whole system, or large video or audio files for instance. Chuck out what you don't need. Note that items in Trash aren't gone until you clear Trash.
(Edit. Don't be dismayed by the top line that says " / 100% " . It just means that the percentages given for the items lower down are percentages of the space used, not of the total space available.)

---

