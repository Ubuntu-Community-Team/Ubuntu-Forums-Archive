---
title: "Firefox crashes from the start"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by tibellus on 2008-04-28
A few days ago, I updated my Xubuntu 7.10 to 8.04. Everything went fine until I started Firefox. It just gets stuck, and goes into a non responsive state. I've tried to start it a few times but I gave up, due to this problem. I had to install epiphany, which works fine and I have no problems with it. I've read on a few posts that some compositing effects might make Firefox go into this non-responsive state, so I stopped the effects, but there was no change.

Is there a way I could fix this?

---

### Post by f37u5g0d on 2008-04-28
I once had a problem where firefox would get very slow and sometimes crash because of the theme I was using.  Try switching out your theme.

---

### Post by tibellus on 2008-04-28
I've switched a few themes, went through all the appearance thingies and stuff, but nothing changed. Is there a parameter I could pass on to firefox, and start in safe mode or something similar?

---

### Post by oskar2000 on 2008-04-28
Could you start it from the command line and say what the output is?

If you don't have any important bookmarks or passwords that you don't want to loose, you could do a "complete uninstall" from synaptic - make sure that the .firefox and/or .mozilla folders are gone, if not delete them. (if you have thunderbird, it might have files in the .mozilla folder, so beware) - and re-install.

---

### Post by enigmaniac23 on 2008-04-28
I had a similar problem after upgrading.  I think it ended up being some of the extensions and plugins I had.  They were not compatible with Firefox 3.

I ended up uninstalling everything related to Firefox 3 through Synaptic, removing my ~/.mozilla folder and then installing Firefox 2.

---

### Post by tibellus on 2008-04-28
I made the greatest mistake ever:) I didn't get any output from Firefox, by running it from the terminal, so I used strace. It froze my entire system:)) Could it be something related to one of the extensions I have? I only have a few, one for weather, scribefire and stumbleupon. I had them before the upgrade, and AFAIK, they are compatible with FF 3b5. So... should I shoot myself or my computer?!:confused:

---

