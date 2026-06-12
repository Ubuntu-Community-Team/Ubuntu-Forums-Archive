---
title: "[SOLVED] Last Kernel update--did it bork sound?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-06-14
for anyone else?  I started a thread that hasnt reached a solution but im wondering with the latest kernel 19, did sound quit for anyone else?

---

### Post by avtolle on 2008-06-14
I thought it did on my AMD-64 install, but just booted it for the first time today since the kernel upgrade, and have sound (system and otherwise).

---

### Post by Bubba64 on 2008-06-14
I had to do 2 restarts to get things working but I didn't check sound it was the close and minimize buttons that weren't working for me. Also you know how to restart and how to change the restart to your old kernel every time I assume.

---

### Post by alienexplorers on 2008-06-14
My sound is working fine since the update to version 19.  Only problem I have is sound stuttering while playing streaming video's or streaming audio.

---

### Post by avtolle on 2008-06-14
> **alienexplorers said:**
> My sound is working fine since the update to version 19.  Only problem I have is sound stuttering while playing streaming video's or streaming audio.
Wonder if that's a function of the buffering time that's set in the application? You didn't mention which one(s) you are using, but something to check.

---

### Post by sports fan Matt on 2008-06-14
Yeah I do, But I think I accidently deleted all my old Kernels and their headers (I had from 17 to 19 and I think I deleted them all):(

---

### Post by sports fan Matt on 2008-06-14
Here is my exact issue: note the greyness with the volume control: as per last night...The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Now, could a kernel upgrade break the access to opening the volume control?

---

### Post by markbuntu on 2008-06-14
No, but a pulseaudio update could.

---

### Post by sports fan Matt on 2008-06-14
Interesting find when I tried to run "volume control" in a terminal: bash: volume: command not found

---

### Post by sports fan Matt on 2008-06-14
just an fyi the newest kernel does break sound but since i booted into the 18 kernel, i have sound again

---

