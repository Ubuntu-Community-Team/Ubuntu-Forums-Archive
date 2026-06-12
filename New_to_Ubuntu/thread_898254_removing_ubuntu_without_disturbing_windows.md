---
title: "removing ubuntu without disturbing windows"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by bbala2020 on 2008-08-23
have a comp with both windows and ubuntu.
but need to uninstall ubuntu and use it as another drive in windows
will this work without creating any boot problems if ubuntu partition is just deleted from windows by using tools like partition magic???

---

### Post by thebigbluecan on 2008-08-23
I think if you wipe the Ubuntu partition it will get rid of the bootloader.. Therefore you wont be able to boot into windows. I think that if you do delete it and you have your windows disk you can do a repair to get the windows bootloader on there... Im prettysure there is more options out there.. but I dont know off the top of my head.

---

### Post by livestockPimp on 2008-08-23
I have never done this but it should be as simple as removing the partition ubuntu is installed on (you can do this with the Windows disk management tools) and then booting from your windows cd and there is a tool for re-installing the boot sectors from the repair console I think it is fixmbr or something.

---

### Post by thebigbluecan on 2008-08-23
Yup thats right ^^^ Above.. look into it. "FIXMBR"  Google it or something.

---

