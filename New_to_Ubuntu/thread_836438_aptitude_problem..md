---
title: "aptitude problem."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by DrMilo on 2008-06-21
I used "sudo aptitude install alsa-oss" and I must confess that I aborted it early when I saw what was going on. Now I have no sound in vlc, the volume control is disabled in totem movie player, rhythmbox won't play any files and my Hardy desktop sounds are gone. I've tried reinstalling some things, all of the recommended adds for vlc, totem and rhythmbox, to no avail.

I'd be grateful for any suggestions.

---

### Post by drs305 on 2008-06-21
Start by going to System, Preferences, Sound and see what settings are listed in Devices. There is a "test" button next to each setup so you can experiment to see if you can get your sound back there.

Curious to know what was going on during the alsa-oss install that scared you ;-)

---

### Post by DrMilo on 2008-06-21
> **drs305 said:**
> Start by going to System, Preferences, Sound and see what settings are listed in Devices. There is a "test" button next to each setup so you can experiment to see if you can get your sound back there.

Curious to know what was going on during the alsa-oss install that scared you ;-)

Thanks.

That 'install' was removing some 160 files! I did something similar from the sound problems thread when I used dapper and I couldn't reboot! 

I've attached a screenshot of the failed sound test. I will be out for a while and will check when I come back.

---

### Post by the_doc on 2008-06-21
> **DrMilo said:**
> 
That 'install' was removing some 160 files!


Not meant to be sarcastic, but that's obviously the problem.  Is there any log files that might keep track of what was removed during an aptitude install?  Might be the quickest way to restore what was lost?

---

### Post by DrMilo on 2008-06-21
> **the_doc said:**
> Not meant to be sarcastic, but that's obviously the problem.  Is there any log files that might keep track of what was removed during an aptitude install?  Might be the quickest way to restore what was lost?

I'm sure there is but I was hoping that someone could tell me which one. There's a few logs!

---

### Post by bapoumba on 2008-06-21
Have you been using aptitude all the time, or just this time and synaptic/apt-get usually ?

alsa-oss does not [have many dependencies]("http://packages.ubuntu.com/hardy/alsa-oss") and does not conflicts with any, so I'm not quite sure where removing that many packages is coming from.

---

### Post by DrMilo on 2008-06-21
> **bapoumba said:**
> Have you been using aptitude all the time, or just this time and synaptic/apt-get usually ?

alsa-oss does not [have many dependencies]("http://packages.ubuntu.com/hardy/alsa-oss") and does not conflicts with any, so I'm not quite sure where removing that many packages is coming from.

Just this time. If you want things in context here's the thread that I got it from.

[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

---

### Post by DrMilo on 2008-06-21
> **DrMilo said:**
> Just this time. If you want things in context here's the thread that I got it from.

[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

I seem to have all the dependencies.

---

### Post by avtolle on 2008-06-21
From the context you provided, I infer you were having/still have problems with sound in Firefox when running flash applications. I see from your first post that you are using 8.04. Are you running the 64-bit or 32-bit version?

EDIT: Had you tried```
sudo aptitude update && sudo aptitude install libflashsupport
``` prior to trying to install alsa-oss?

---

### Post by DrMilo on 2008-06-21
> **avtolle said:**
> From the context you provided, I infer you were having/still have problems with sound in Firefox when running flash applications. I see from your first post that you are using 8.04. Are you running the 64-bit or 32-bit version?

EDIT: Had you tried```
sudo aptitude update && sudo aptitude install libflashsupport
``` prior to trying to install alsa-oss?

323 bit. No I haven't used aptitude on Hardy for anything before that.

---

### Post by avtolle on 2008-06-21
Some folks have had success with the above-posted application in resolving their Flash sound problems in Firefox (which, of course, doesn't need to be installed via aptitude; one could use Synaptic for this purpose), and I was just curious if it didn't help you. Thanks for the response.

---

### Post by DrMilo on 2008-06-21
> **avtolle said:**
> Some folks have had success with the above-posted application in resolving their Flash sound problems in Firefox (which, of course, doesn't need to be installed via aptitude; one could use Synaptic for this purpose), and I was just curious if it didn't help you. Thanks for the response.

I'm sure I had that package before all this. Of course I started this upgrade to see if FF 3 would fix my flash problem and FF3 has yet to work!

---

