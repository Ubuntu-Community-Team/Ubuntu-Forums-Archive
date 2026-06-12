---
title: "ALSA Problem"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by schmidtbag on 2008-09-27
For about a month now, I put in this different sound card.  It works fine, but every time I start up my computer the volume resets.  When I turn off the computer, it shows some alsactl failure.

I did some research and found out that typing "sudo alsactl store 0" is what is supposed to be performed to solve the issue, but when I do it shows the same error as the one when I turn off the computer, which is:

```
alsactl: relocation error: alsactl: symbol snd_tlv_parse_dB_info, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
```

So, how do I fix this?

---

### Post by Gen2ly on 2008-09-27
Here's what I do to save the sound in Gentoo (might need to be adapted for Ubuntu):

[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Setting_the_Mixer](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Setting_the_Mixer)

The first part if you just type in "alsamixer" it will choose your default card.

---

### Post by schmidtbag on 2008-09-27
That didn't work, it didn't recognize "save" as a valid function.  Besides, that wouldn't fix my error, it would just keep my volume to what I set it to last.

---

### Post by Nepherte on 2008-09-27
To store sound I do:
```
sudo alsactl store
```

---

### Post by lswb on 2008-09-27
I would make sure that you have current and compatible versions of alsactl and libasound. Search for alsa-utils in synaptic and make sure it it the latest version, and do the same for libasound.

---

### Post by schmidtbag on 2008-09-27
is there any way so ubuntu can automatically keep it up to date?  in the repositories its at version 1.0.15, the latest is 1.0.17 and is moving to 18.  also, i can't seem to reinstall the latest alsa-utils.  it gets loads of errors

---

### Post by lswb on 2008-09-27
> **schmidtbag said:**
> is there any way so ubuntu can automatically keep it up to date?  in the repositories its at version 1.0.15, the latest is 1.0.17 and is moving to 18.  also, i can't seem to reinstall the latest alsa-utils.  it gets loads of errors

libasound 1.0.15 is the latest version in the normal hardy repo. and alsa-utils is also 1.0.15 (I'm not sure if the matching version numbers are required or just a coincidence) Do you have any non-standard repositories in your sources-list, or perhaps the backports or proposed repositories included? Sometimes with the proposed repos, libraries and executables can get out of sync and possibly other problems can occur also.

What sort of errors do you get when installing alsa-utils?

As far keeping things updated, unless you've disabled it, there is a "updates available" notice that should appear from time to time in the panel notification. When there is a notification you can just run synaptic or apt-get.

---

### Post by schmidtbag on 2008-09-27
I looked on ALSA's website and the newest stuff is listed as 1.0.17, but in Ubuntu they're all different.  Some are 0.99, some are 1.0.15, some are 1.0.16.  I did manage to install the first couple packages on ALSA's site and the error doesn't show up anymore when I turn off the computer but the volume problem persists.

As far as I remember, the errors I received were mostly related to it being incapable of doing anything.  I tried installing under SU with no luck.  I was trying the 1.0.17 version btw.

I do keep everything updated, in fact, I often download pre-released updates (one of which I regretting, Pidgin has been acting up ever since)


After realizing how the error no longer shows up when shutting down, I tried "sudo alsactl store" again and it seems to have worked, but is there any way I can make it automatic?  Every time I want to change the volume I want it to stay that way without having to use the terminal to ensure its saved.

---

### Post by Nepherte on 2008-09-28
They "feature freeze" software versions in the repositories. Only bug/security fixes come into the repositories, except for some special cases I assume. They do it to ensure the compatibility with the rest of the software in Ubuntu so there's less chance your Ubuntu breaks. So you will only see a new version of alsa in the next ubuntu release (intrepid ibex) or you install it yourself. There's a script around here in the forums that installs the latest alsa for you, but I didn't find it rightaway. I wrote an article about how to install alsa yourself as well: [http://www.nepherte.be/linux/howto-compile-alsa-drivers.html](http://www.nepherte.be/linux/howto-compile-alsa-drivers.html) But since it works for you now, I suggest you just leave it be for now.

---

### Post by schmidtbag on 2008-09-28
Actually, sorry about being a pain but, the problem WASN'T fixed.  The error I get is gone but my volume still isn't saved.  I have a hunch that GDM is the cause of this, but I could be completely wrong.

---

### Post by lswb on 2008-09-28
Try this from Gnome desktop:

Main Menu/System/Administration/Services 
Make sure that audio settings management is enabled. If not, click the "unlock" button, enter password, and check it. I took a look at the scripts that this will use and it looks to me like it will save alsa settings on shutdown, but to be honest, it was difficult reading through the script to be sure.

If enabling that service doesn't save your volume settings at shutdown, post again and We'll see about installing your own script to call alsactl at shutdown

---

### Post by schmidtbag on 2008-09-28
Sorry for the delayed response i didn't notice this moved onto 2 pages.  i thought what you told me was going to be it, cause that service was off.  unforunately that somehow didn't fix my problem

---

### Post by schmidtbag on 2008-09-29
**SOLUTION**

After looking around google a bit for people who didn't find a solution, I do have one.


I noticed that in /var/lib/alsa/, i'm supposed to have 2 files, one named asound.names and another called asound.store.  There happens to be a copy of both of those files in /etc/.  These are the defaults, that the system looks for when the ones in /bar/lib/alsa/ are missing.  All you have to do is copy those files to that folder (do it via sudo nautilus) and then in terminal type "sudo alsactl store 0" and "alsactl names"

---

