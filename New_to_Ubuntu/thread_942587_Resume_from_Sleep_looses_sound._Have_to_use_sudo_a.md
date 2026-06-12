---
title: "Resume from Sleep looses sound. Have to use sudo alsa force-reload"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by philinux on 2008-10-09
This reinstates sound. Initiating this command causes the Volume control to quit. A dialogue box pops up asking to reload it. Then I get sound back. Is this a bug and is there a fix?
 ```
sudo alsa force-reload
[sudo] password for philcb: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/philcb/.gvfs
      Output information may be incomplete.
Terminating processes: 6112 6236lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/philcb/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/philcb/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/philcb/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
```

---

### Post by jukingeo on 2010-04-03
I have a similar problem with my Dell Dimension 4600 desktop computer.  I even have a special card that is KNOWN to work great with Linux.  However, I have the same problem in that I get no sound when resuming from sleep or hibernate mode.  However, after doing some reading I have found that this gets my sound back after I have lost sound on resume (without rebooting):

sudo alsa force-reload

But naturally to me this isn't good enough, I want my sound to come back when the system resumes.  After all, that is what *SHOULD* happen. 

I have seen this problem go all the way back to version 6.10 and I am on 8.04 and I STILL see people having problems with it in version 9.10.  What is up with that?  That seems like a long standing bug that isn't corrected.

Anyway, I am hoping there is some kind of fix for it so I don't have to go into the terminal and do a sudo alsa force-reload everytime my computer resumes from suspend mode.

Any permanent solutions?

Thanx,

Geo

---

### Post by philinux on 2010-04-06
> **jukingeo said:**
> 
Anyway, I am hoping there is some kind of fix for it so I don't have to go into the terminal and do a sudo alsa force-reload everytime my computer resumes from suspend mode.

Any permanent solutions?

Thanx,

Geo

Not a bug fix as such but since Intrepid this hasn't been a problem. Since you're running Hardy LTS maybe when you upgrade or reinstall Lucid Lynx the problem will be gone.

---

### Post by jukingeo on 2010-04-08
> **philinux said:**
> Not a bug fix as such but since Intrepid this hasn't been a problem. Since you're running Hardy LTS maybe when you upgrade or reinstall Lucid Lynx the problem will be gone.

I was hoping for a fix by Lucid as well.   But even when Lucid comes out I am probably going to wait a good 4 to 6 months.  Lately when Ubuntu releases a 'new' version it isn't as stable as they say it is.  And it takes a while before all the fixes come down the pike.

I remember when Hardy first came out it was a pain.  I was going to ditch it in favor of an older version.  But then I heard about LTS support and that Hardy was on the list.  So I stuck with it.

But I know that I will want to upgrade because I have Ubuntu Studio and there are some problems still under Hardy (I.E. it doesn't have FFADO support for Jack out of the box, you have to recompile Jack).

So then I take it that there is no permanent 'resume' solution and that you have to type that "fix" in every time you resume from sleep.  That does kind of suck.  But I have seen it in about 10 (or more) similar threads and it seems like there isn't a permanent solution.   There were about three different procedures I found (two were rather lengthy) and none solved the problem.

Ok, now taking this from a different approach.  Is there a way I could instruct Ubuntu to automatically run the 'sudo alsa force-reload' command upon resume?  Since I know THAT works.

Thanx,

Geo

---

### Post by jukingeo on 2010-04-22
I am surprised that as long as this problem has been around there isn't an automatic fix for this problem?

I mean I can fix it using:

sudo alsa force-reload

but it is a pain in the neck to have to do that since it is something that should be done automatically on resume.   However even that fix isn't completely without it's drawbacks.  I find that it resets my sound mixer every time I use it.

Ok, so if it is HARD to turn the sound back on upon resume, why not just have Ubuntu leave the sound on when it goes into suspend/hibernate.  Can that be done?

Geo

---

### Post by sb5551 on 2010-04-22
Forgive me more my extreme lack of using the correct terms. The fact that I have only been using Ubuntu for about a week.
 
I saw a fix for this on the HP Touchsmart Tx2's that involved adding that command:
 
sudo alsa force-reload
 
to the script that occurs when resuming from suspend/hibernate. This just means you won't have to type it in everytime. I am not sure of the exact location for the script, but I am sure someone else can chime in.

---

### Post by jukingeo on 2010-04-23
> **sb5551 said:**
> Forgive me more my extreme lack of using the correct terms. The fact that I have only been using Ubuntu for about a week.
 
I saw a fix for this on the HP Touchsmart Tx2's that involved adding that command:
 
sudo alsa force-reload
 
to the script that occurs when resuming from suspend/hibernate. This just means you won't have to type it in everytime. I am not sure of the exact location for the script, but I am sure someone else can chime in.

This is what I was figuring too.  If there is a manual way to reset, why not have the script execute automatically upon resume?

However, if it was such an easy fix like that, then how come this problem was allowed to persist through several releases of Ubuntu?

Anyhoo, I am really hoping that most issues like this will finally be solved in Lucid which will be the next LTS release. 

Thanx,

Geo

---

