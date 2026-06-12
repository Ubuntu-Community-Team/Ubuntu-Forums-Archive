---
title: "compiz fusion causes mednafen video to flash"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-06-24
Does anyone know a work around for running mednafen with ubuntu special effects on and not having mednafen window flash?

---

### Post by ZabiGG on 2008-06-27
Hi,

I had a similar problem with gxine and VLC and found this link

[http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/](http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/)

It doesn't include workarounds for your specific app, but it might point you in the right direction in terms of preferences so that you may select another video output.

Another tip: did you check the Unredirect full screen windows box
in the Compiz Settings Manager 
General settings tab?

Another no-fix workaround is to disable compiz when you use that app:

To disable compiz
Hit ALT-F2
Enter the command
metacity --replace&
in the command line field

To re-enable compiz after

Hit ALT-F2
Enter the command
compiz --replace&
in the command line field
Then left-click on the fusion icon and select Reload window manager

The switch is relatively fast and painless once you're used to it, and avoids having to uninstall compiz to get smooth video.

Hope this helps,

Z.

---

