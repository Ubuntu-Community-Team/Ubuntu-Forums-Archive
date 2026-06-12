---
title: "Playing .avi files in totem-xine?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by ItecKid on 2008-11-07
I have a movie that is saved as a .avi file.  I installed totem-xine, which I was told could play any media file.  However, when I try tp play my movie through this, I recieve a message saying "There is no plugin to handle this movie."

I have downloaded the 'all plugins' package from Synaptic, and still receive this message.  Thoughts?

---

### Post by Yuki_Nagato on 2008-11-07
Try using VLC instead.

[http://www.videolan.org/vlc/]("http://www.videolan.org/vlc/")

This will play just about anything.  Regardless of license.

---

### Post by kostkon on 2008-11-07
> **ItecKid said:**
> I have a movie that is saved as a .avi file.  I installed totem-xine, which I was told could play any media file.  However, when I try tp play my movie through this, I recieve a message saying "There is no plugin to handle this movie."

I have downloaded the 'all plugins' package from Synaptic, and still receive this message.  Thoughts?
*totem-xine* does not use the *Gstreamer* plugins but its own. To be able to play almost everything (except maybe amr and some other obscure formats) you'll need to install the *libxine1-all-plugins* package. Is this the package that you have installed?

Also you'll need to install the Windows codecs package, called *w32codecs*, that is offered by the [*Medibuntu* repository]("http://medibuntu.org/") (please check the legal warning on this page, if you live in a country where software patents exist). Add this repository to your software sources list (instructions on how to do it are [here]("http://help.ubuntu.com/community/Medibuntu")) and then install *w32codecs* from *Synaptic*. 

But didn't *totem-xine* offered you to install the codecs for you (I mean the libxine codecs) when you tried to play this file?

---

### Post by mdpalow on 2008-11-07
Try the link in my signature below. QuickStart will install files for you to play movies.

Good luck

---

### Post by ItecKid on 2008-11-08
Thank you all for replying.  I have tried all of the suggestions offered with no success.

I added the Medibuntu repository, but I still did not have the option to install the w32codecs.  Can I install them directly from the terminal with wget or something similar?

---

### Post by altonbr on 2008-11-08
> **ItecKid said:**
> Thank you all for replying.  I have tried all of the suggestions offered with no success.

I added the Medibuntu repository, but I still did not have the option to install the w32codecs.  Can I install them directly from the terminal with wget or something similar?

If you right-click the file, then go to 'Properties', 'Audio/Video' what does it say under 'Video'?

e.g.> Dimentions: 720x304
Codec: XVID MPEG-4
Framerate 30 frames per second
Bitrate: N/A

---

