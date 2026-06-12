---
title: "HowTo: Speeding up X startup (nvidia cards)"
date: 2005-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by henriquemaia on 2005-05-04
**Disclaimer: **
This worked for me. You have to attend that differences in hardware or instalation may lead that this not works for you.

**Some background:**
It's just a small thing, but in my case this makes X starts much faster. Why is that I don't know.

My primary video card is a nVidia Corporation NV11 [GeForce2 MX/MX 400]. When it starts the screen shows a logo of nvidia and this just hangs there for some time. Running X from a console a noticed that there was something missing that lead to that delayed startup. (note: I know that I can turn the logo off, but even when it's off, the delay remains).

**What to do:**
You have to edit xorg.conf. For that you type, under a terminal:

```
sudo gedit /etc/X11/xorg.conf
```

There you find this:

Section "Files"
  **FontPath "unix/:7100"   # local font server**
  # if the local font server has problems, we can fall back on these

So you comment the line **FontPath "unix/:7100"** so it looks like this:

Section "Files"
  **# FontPath "unix/:7100"   # local font server**
  # if the local font server has problems, we can fall back on these

save your file. Next time you restart X, you'll notice the difference.

Hope this helps someone.

* update: I removed the nvidia cards reference in the title due to the comment of Chayyiel, who has a non-nvidia hardware and experiencied the same results with this. Thanks Chayyiel. *

---

### Post by fackamato on 2005-05-04
What does it do, really?

---

### Post by henriquemaia on 2005-05-04
[QUOTE=fackamato]What does it do, really?[/QUOTE]
 
I think it jumps searching for fonts on that path (which in my case) it is not available. 

The message it gives when it is enabled is:
 
**Could not init font path element unix/:7000, removing from list!**

Like this. So, removing it, it jumps this step, I believe.

---

### Post by Chayyiel on 2005-05-04
It not only works for nVidia cards. I have an ATI Radeon and it made X start up SUPER quick! Thanks for the tip! :)

---

### Post by RastaMahata on 2005-05-04
[QUOTE=henriquemaia]I think it jumps searching for fonts on that path (which in my case) it is not available. 

The message it gives when it is enabled is:
 
**Could not init font path element unix/:7000, removing from list!**

Like this. So, removing it, it jumps this step, I believe.[/QUOTE]
 where does it post this message?

---

### Post by claydoh on 2005-05-04
It is in /var/log/Xorg.0.log

---

### Post by professor_chaos on 2005-05-04
Sweet. Works for me on my Nvidia.
Thanks for the tip!
 \\:D/

---

