---
title: "SSH - Full Screen"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by Tropicalbound on 2013-09-27
Good day everyone,

Occasionally, I like to run the terminal window in full screen.  This works fine and the text utilizes the full screen window.  However, when I SSH to a Windows server in full screen, the text will only occupy the upper left quadrant.  Does anyone know of a way to utilize the full screen in SSH?

Thanks as always!

TB

---

### Post by Kirboosy on 2013-09-27
Can you explain your setup further. You mentioned SSH to a Windows server. How did you set that up?


~Caboose

---

### Post by The Cog on 2013-09-27
Is the windows screen 80*24 characters in size? That's the default size for the windows cmd.exe so I'm guessing that's it. Maybe the ssh server on windows can't change the size to match the client window. cmd.exe is really astonishingly clunky.

---

