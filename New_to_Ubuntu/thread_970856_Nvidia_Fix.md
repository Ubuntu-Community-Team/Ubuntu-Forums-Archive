---
title: "Nvidia Fix?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Roger Gundberg on 2008-11-04
I hope this is relevant.I ran the script (sudo) nvidia x config (I may stand to be corrected) and it returned the argument CPU SSE not present. I asked myself," What the heck is a SSE"? It's an extension of the mmx arctutecture, implimented in 2004. And although the AMD Anthalon was built in 2004 it did not include the SSE flag. To verify this. I installed Sysinfo, and clicked on CPU (not GPU) then clicked on 'More Details and of the long list of flags SSE was not there. In my case I thought ,"If it's working dont' fix it. Hhope this helps. Good Luck!

---

### Post by philinux on 2008-11-04
System>admin>hardware drivers to check driver loaded.
And this.
nvidia-settings
or
nvidia-xconfig

Which you install either from terminal or synaptic. A menu item appears in Admin.

---

### Post by LowSky on 2008-11-04
to save settings that you may set in nvidia-settings or nvidia-xconfig alsway use the sudo comand when starting those applications.

What exactly is the point of this post.

BTW all Athlons from 2003and on have SSE

---

### Post by Roger Gundberg on 2008-11-05
The point is neither Nvidia or Umbutu may be the cause of the video issues rather the incapability of the CPU it self. I did not see the flag listed in my case.

---

### Post by dawynn on 2008-11-05
Yes, the Athlon classic was put out with an early subset of SSE instructions.  In my experience, this means that any applications that use actual SSE instructions will crash on my Athlon classic.  These were Athlon PC's going up to about 1.4 Ghz, without the '+' indicator.  The Athlon+ systems *have* SSE support.

The latest nVidia drivers (173, 177, etc) require SSE support, so if you use an Athlon classic, these will not work for you.

So, it really doesn't matter how recent your nVidia card is, if you are running an Athlon classic, you will have to use one of the legacy drivers, if you want OpenGL.  And up until a few days ago, the legacy drivers did not support OpenGL processing because of a conflict with the new X system.  And last I heard, they may even still have problems with the 72 series.

So, if you have a fairly recent nVidia card, but are running an Athlon Classic machine, make sure that you have the Proposed repositories enabled, and download the new 96.43.09 driver from proposed.  (You will also need to get the new jockey packages from proposed, as the jockey packages in the main directories have the legacy drivers blacklisted)

Note: 96.43.09 is the first version that fixed the conflict with X.  Later versions, I assume, will also work, but versions prior to 96.43.09 will conflict with X.

---

