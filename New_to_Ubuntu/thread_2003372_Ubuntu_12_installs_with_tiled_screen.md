---
title: "Ubuntu 12 installs with tiled screen"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by flashsplash on 2012-06-14
I'm new to Ubuntu - just installed Ubuntu 12.04 as a virtual OS in VMware running on a MacPro OS 10.6.8. The other OS in VMware is Windows XP, which is running fine. 
When installing Ubuntu, its background screen showed up as tiled (see screenshot). 
With a great deal of squinting I finished the install.
With Ubuntu now installed, the screen is one tile but still 'zoomed out' so I can hardly read anything on it.
Can anyone help?!

---

### Post by SilentMute on 2012-06-19
you should be able to edit the resolution from system settings/screens, however I'm not certain if that is the root of the problem. It sounds like it could also be arising from VMware, however I cannot help you there, sorry!

for the time being though, adjusting the screen resolution should allow you to use ubuntu normally
--

---

### Post by flashsplash on 2012-06-26
Thanks for the reply! I tried to adjust the screen resolution at "Settings" in VMware as well as in the Mac System Preferences - no luck! The screen remains tiny and difficult to read ... no change.
One thing I'm wondering about: I'm not able to install VMware tools. I tell it to go ahead and Install VMware tools while in Ubuntu, it proceeds and then just seems to sit there. Nothing happens any further. I let it sit for 3 hours but no tools installed.
Could this be related?
Many thanks in advance!

---

### Post by c0rnmuffin on 2012-06-29
Hello,
I have a similar problem.  I am trying to install Ubuntu 12.04 through VMware Fusion on a Macbook with OS 10.6.8 (Snow Leopard).  VMware is able to run Windows 7 fine.  To install Ubuntu, I pointed the installer to my iso file, and then I have tried it both accepting and declining the Linux Easy Install.  After that it boots up and then I see this tiled desktop with a tiny cursor that seems able to click on some buttons in the corner.  There are no screens to finish the install and I can't read anything.  Any ideas?

I have trouble with the VMware tools as well.  the first time it asked me after I picked my iso file if I wanted to install it, and I said yes.  Now it just says it's not installed and if I try to do so, it gives me weird error messages and/or hangs.

Thanks!

---

### Post by c0rnmuffin on 2012-07-05
For anyone else that runs into this problem, just wanted to mention that I fixed mine by upgrading to VMware Fusion 4 (I was formerly running 3.1.3).

---

### Post by byte64 on 2012-10-08
I had the same problem (13" macbook pro + VM Fusion 3.01), but instead of upgrading to VM Fusion 4, I magnified the Mac screen (using cmd =) until I was able to spot the system settings icon and then the display setup in the hardware section, changed the resolution to a 1152x864 and that made the trick.

Now I am trying to figure out where they put the terminal application in the new release (I'coming from 8.04) but this is another story.

---

