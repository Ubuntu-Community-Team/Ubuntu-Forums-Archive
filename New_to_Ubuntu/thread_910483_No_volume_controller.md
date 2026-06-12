---
title: "No volume controller"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-09-04
I do not have a volume controller on my comp. I have installed all the gstreamer packages.

Earlier my laptop speakers never used to work, but the external speakers were working just fine. Someone recommended me to download and install the linux-backports-generic package.
I installed it, and eversince my sound is all messed up.

Can someone please help me.

The volume control icon on the top menu bar seams to perpetually be on zero, and when i try to change i get the following error.

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

---

### Post by 7raTEYdCql on 2008-09-05
Please can someone help. I am suffering without sound. I need it badly. I installed AlsaMixer again, but there doesn't seem to be any improvement.

---

### Post by jbrown96 on 2008-09-05
1. Remove backports and reboot. I imagine you have already done this.
2. go into the sound preferences on the system menu and try changing the playback device. 
3. try messing with alsamixer to see if a channel is muted (not likely).
sorry I can't be of more help

---

### Post by 7raTEYdCql on 2008-09-05
It doesn't seem to work. I changed to all the available options. And everytime i wanted to test i get this error message:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

And as i said the alsamixer command does not work in terminal.

---

### Post by jbrown96 on 2008-09-05
> **i.mehrzad said:**
> It doesn't seem to work. I changed to all the available options. And everytime i wanted to test i get this error message:


And as i said the alsamixer command does not work in terminal.

I'm not sure if I have had that exact error, but I have had one related to the sin wave. Try reinstalling all of the alsa packages in synaptic. You will need to reboot to get the modules loaded. Hopefully that will work. If sound was ever working, try an older kernel when grub is loading.
I think the best bet would be to install alsa from source. I had a thread about how to do this. Don't use the links in the guide. Go to alsa's website and download the three tarballs (alsa-driver, alsa-lib, alsa-utils) for the current version. You will need to reboot and possibly reinstall alsamixer (not sure).

---

### Post by 7raTEYdCql on 2008-09-06
I think the best bet will be to do a clean format of my root dirctory.

But anyway will try to do what you suggested.

---

### Post by cariboo on 2008-09-06
In a terminal type:

```
sudo alsa reload
```

This will reload your sound drivers, make a note if there are any errors and let us know.

Jim

---

### Post by 7raTEYdCql on 2008-09-06
This was my output
```

mehrzad@mehrzad-laptop:~$ sudo alsa reload
[sudo] password for mehrzad: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mehrzad/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
mehrzad@mehrzad-laptop:~$ 

```

---

### Post by 7raTEYdCql on 2008-09-06
Please can someone help??

---

