---
title: "[SOLVED] Brightness in Ubuntu 8.04"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by ellalan on 2008-08-17
Hi
I am having problem with my brightness adjustment, I have this brightness applet in my task bar and when I increase or decrease I couldn't see any difference.
I have integrated nVidia 6150 graphics.
Could someone help me to make it work please. Thanks in advance.

---

### Post by overdrank on 2008-08-17
> **ellalan said:**
> Hi
I am having problem with my brightness adjustment, I have this brightness applet in my task bar and when I increase or decrease I couldn't see any difference.
I have integrated nVidia 6150 graphics.
Could someone help me to make it work please. Thanks in advance.

Hi and have you tried to adjust with the nvidia-settings ```
gksu nvidia-settings
``` using the alt, F2 keys

---

### Post by ellalan on 2008-08-17
Hi
Thanks for the post, I tried but I couldn't find the settings for brightness in nVidia-settings. What am I doing wrong?

---

### Post by overdrank on 2008-08-17
> **ellalan said:**
> Hi
Thanks for the post, I tried but I couldn't find the settings for brightness in nVidia-settings. What am I doing wrong?

Hi and it should be on in the X server color corretion under X screen

---

### Post by ellalan on 2008-08-17
Thank you overdrank for the help.

---

### Post by fusionisthefuture on 2008-09-01
im having this same problem with this same video card, albeit a different laptop, mine uses f7, f8 for the adjustment.  im using nvidia-glx-new, and when i input gksu nvidia-settings, first of all, tab completion does not give it as a valid option, and second, the first time i used it, it asked me for a password, then did nothing.  if i gksu nvidia, the options i get for tab completion are nvidia-bug-report and nvidia-xconfig

thanks,
-fitf

---

### Post by nickmayfield on 2008-10-28
I am having this same kind of problem. i'm new to ubuntu/linux. i have the new nvidia driver installed and working fine. my screen was really dark so i adjusted it accordingly to make it normal in the nvidia x server settings. now my problem is when i reboot it really dark again, but if i go to system/administration/nvidia x server setting and just click on it and close it everything goes back to normal. can anyone help me fix that. thanks for your time
Nick

---

