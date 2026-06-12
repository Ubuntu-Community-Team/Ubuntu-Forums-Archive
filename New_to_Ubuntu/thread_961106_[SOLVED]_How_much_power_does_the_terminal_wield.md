---
title: "[SOLVED] How much power does the terminal wield?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by I wanted to leave on 2008-10-28
After installing a fresh copy of Hardy on my drive my thoughts turned to installing codecs. Then I had this thought... Is there a terminal command that can search through the freshly installed software on the drive and then download only the codecs that are required as per the software list? 
I'm still new to Linux and always feel like I'm downloading lots just to get the music and video support required

---

### Post by pofigster on 2008-10-28
If I understand right, you want to scan your whole computer, detect what media types there are and then install only the codecs needed to play those media types?

Seems like it might be faster, easier and only potentially a little more bloat to install:
gstreamer0.10-fluendo-mp3, gstreamer0.10-plugins-bad/good/ugly

---

### Post by acirilo on 2008-10-28
I would go to linuxmint. It is the sweetest, smoothest distro i've used yet. It installs most used codecs by default.

---

### Post by sdennie on 2008-10-28
> **bra10n said:**
> After installing a fresh copy of Hardy on my drive my thoughts turned to installing codecs. Then I had this thought... Is there a terminal command that can search through the freshly installed software on the drive and then download only the codecs that are required as per the software list? 
I'm still new to Linux and always feel like I'm downloading lots just to get the music and video support required

You could probably do this but, as the codecs are lumped into just a handful of packages, it would probably be more painful than just installing all the codecs.  For several releases Ubuntu has had this sort of functionality via nautilus though.  In a fresh install, if you double click on a file that has a known but uninstalled codec, it generally prompts you to install the codecs you need.  If you have a library of, for example, .mp3 and .avi files, you are just a few clicks away from having all the codecs installed the first time you open the files.

---

### Post by I wanted to leave on 2008-10-28
> **vor said:**
> You could probably do this but, as the codecs are lumped into just a handful of packages, it would probably be more painful than just installing all the codecs.  For several releases Ubuntu has had this sort of functionality via nautilus though.  In a fresh install, if you double click on a file that has a known but uninstalled codec, it generally prompts you to install the codecs you need.  If you have a library of, for example, .mp3 and .avi files, you are just a few clicks away from having all the codecs installed the first time you open the files.


I always have a drama with internet radio codecs; it offers to search and download required codecs, I do, and rhythmbox still says codecs are missing. By the time I have everything working I just wonder about how much I've downloaded. That's the reason for my question. It would be nice to just get all you needed and no more though. Clean and lean

---

### Post by CloudFX on 2008-10-28
Rather than bother with codecs, use VLC Media Player.  It run's all major audio and video formats, no codecs required.  It's prepackaged in Ubuntu, and can be installed through Add/Remove.

---

### Post by Paqman on 2008-10-28
The other easy option is the package ubuntu-restricted-extras. Besides codecs, it includes Flash, Java, fonts, etc. It's always one of the first packages I install on a fresh system.

---

### Post by Xiong Chiamiov on 2008-10-28
> **CloudFX said:**
> Rather than bother with codecs, use VLC Media Player.  It run's all major audio and video formats, no codecs required.  
...which is why it's both great and terrible at the same time.

Anime fansub groups *despise* VLC, because it tends to do terrible things with x264 and Matroska files.  However, it will play *anything*, including corrupted files, so it's well worth having around.  I am fond of SMPlayer, myself.

---

