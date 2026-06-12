---
title: "Help with permissions"
date: 2008-09-20
forum: Programming Talk
---

### Post by JRaz on 2008-09-20
Hi, I'm trying to adjust the back-light brightness of my laptop from a script. The script echos a value into /proc/acpi/video/VGA/LCD/brightness. How can I make it so that the script has the necessary permissions to echo there and a normal user can execute the script without password prompt.

Any help would be appreciated.

---

### Post by mssever on 2008-09-20
Look at the source of the brightness applet to see how they handled it. The path you mentioned doesn't exist on my machine, so there's probably a more portable way to handle it. (The path that works for me is /proc/acpi/video/VID1/LCD0/brightness)

---

