---
title: "[SOLVED] Youtube  won't play.."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-24
Hello all
I removed Gutsy and installed Hardy yesterday. I did install the flashplugin-nonfree (and the entire ubuntu-restricted-modules) package. But I still just see a gray box when I ply youtube videos. Which flash player do I need? I am using Hardy 64-bit edition.

---

### Post by Steve413z on 2008-05-24
try this

sudo apt-get purge  flashplugin-nonfree ubuntu-restricted-modules
sudo apt-get install ubuntu-restricted-modules

---

### Post by Steve413z on 2008-05-24
the other possibility, is there is some weird problems with PulseAudio that are messing up flash, you might try using ALSA

---

### Post by Bubba64 on 2008-05-24
I always add all the gstreamer, ffmpeg , and vlc from add remove this should load the java you need, have you looked in FF preferences to see if your are allowing cookies and java script. On alsa I also enable alsa/oss in synaptic

---

### Post by sayakb on 2008-05-24
> **Steve413z said:**
> try this

sudo apt-get purge  flashplugin-nonfree ubuntu-restricted-modules
sudo apt-get install ubuntu-restricted-modules

Should that fix the problem? And why purge flash and restricted modules separately? :(
Though, I'll try this, in case..

---

### Post by sayakb on 2008-05-24
> **Bubba64 said:**
> I always add all the gstreamer, ffmpeg , and vlc from add remove this should load the java you need, have you looked in FF preferences to see if your are allowing cookies and java script. On alsa I also enable alsa/oss in synaptic

Well, the ubuntu-restricted-modules I mentioned installs all the gstreamer and flash modules needed to play online SWF.. But anyway, gstreamer has nothing to do with flash I think :(
The flashplugin-nonfree worked for me in Gutsy though..

---

### Post by Bubba64 on 2008-05-24
> **LinuxIsInnovation said:**
> Well, the ubuntu-restricted-modules I mentioned installs all the gstreamer and flash modules needed to play online SWF.. But anyway, gstreamer has nothing to do with flash I think :(
The flashplugin-nonfree worked for me in Gutsy though..

I don't know what any of them do but when I upgrade and add all of these I never run into anything that will not play, this is the shot gun method of killing the bird of accessibility. It is correct though that the flash is in the restricted extras I think.

---

### Post by sayakb on 2008-05-24
Yes, it is infact. And it is installed too :(

---

### Post by Bubba64 on 2008-05-24
> **LinuxIsInnovation said:**
> Yes, it is infact. And it is installed too :(

I don't know if this is helpful but there are 4 or 5 additional gstreanmer additional set ups in add remove beyond the restricted extras.

---

### Post by sayakb on 2008-05-24
I have installed all the ugly, bad, good and multiverse sets.. didn't help.. :(

---

### Post by sayakb on 2008-05-24
Looks like I sorted it out :D
I installed gnash SWF flayer and it started working fine.
:D

---

### Post by WkenCouser on 2008-05-26
Hello,
I had the same problem.
I installed/reinstalled GNASH but no change.
I installed/reinstalled SWF but no change.
I reinstalled FIREFOX and went to 'youtube' where I was prompted to install new codesc. I allowed the system to search for them and installed both 'GSTREAMERS'.
I went to 'youtube' again and all is OK.
Hope this helps.
ken :-)

---

