---
title: "My Computer Icon In Desktop"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by balachandarlinks on 2008-06-08
Hai,
  I want to put the My Computer icon in my desktop.....I m using ubuntu hardy....I tried with create launcher...But i dont know the command....Please give me the command for my computer in create launcher...

  Every time when i click an windows drive..automatically its shortcut icon appears in desktop...I want to avoid it...Give me the help for it too...
  
   Thanks in advance..

---

### Post by TalioGladius on 2008-06-08
> **balachandarlinks said:**
> Hai,
  I want to put the My Computer icon in my desktop.....I m using ubuntu hardy....I tried with create launcher...But i dont know the command....Please give me the command for my computer in create launcher...

  Every time when i click an windows drive..automatically its shortcut icon appears in desktop...I want to avoid it...Give me the help for it too...
  
   Thanks in advance..You can install ubuntu tweak, go to personal section and select show computer icon on desktop.

---

### Post by ad_267 on 2008-06-08
Press Alt+F2 and run gconf-editor. Go to apps - nautilus - desktop and then tick the box "computer_icon_visible"

To prevent drives from showing up on the desktop untick "volumes_visible"

---

### Post by fenian on 2008-06-08
open a terminal and enter...

> gconf-editor

in the window that opens click the arrow next to apps then scroll down to nautilus and click that arrow then click the desktop folder in the window  there should be an option to show home folder check it and you're set.

---

