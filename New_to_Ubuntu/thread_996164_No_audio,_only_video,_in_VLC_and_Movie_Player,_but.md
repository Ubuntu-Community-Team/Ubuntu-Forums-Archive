---
title: "No audio, only video, in VLC and Movie Player, but Amarok has"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by AlexOslo on 2008-11-28
I am running Ubuntu 8.04 and have no audio, only video, in VLC and Movie Player respectively. Audio works fine in Amarok, though!
In VLC, I've tried all the different settings under Audio -> Output options, and the plugins are all installed. The sound is not muted either.

For some reason, in the VLC player, on the Audio tab in the menu, by default it says "disabled". I set it to Track 1 instead, but then it switches back to disabled again when I restart VLC (but it makes no difference what I set it to anyway!).

Anyone got a clue on this?

Alex


(I tried posting this to the original thread here, without getting a response: [http://ubuntuforums.org/showthread.php?p=6258548#post6258548](http://ubuntuforums.org/showthread.php?p=6258548#post6258548) )

---

### Post by bangmalley on 2008-11-28
go to System->Preferences->Sound, switch to ALSA.

---

### Post by HittingSmoke on 2008-11-28
> **AlexOslo said:**
> I am running Ubuntu 8.04 and have no audio, only video, in VLC and Movie Player respectively. Audio works fine in Amarok, though!
In VLC, I've tried all the different settings under Audio -> Output options, and the plugins are all installed. The sound is not muted either.

For some reason, in the VLC player, on the Audio tab in the menu, by default it says "disabled". I set it to Track 1 instead, but then it switches back to disabled again when I restart VLC (but it makes no difference what I set it to anyway!).

Anyone got a clue on this?

Alex


(I tried posting this to the original thread here, without getting a response: [http://ubuntuforums.org/showthread.php?p=6258548#post6258548](http://ubuntuforums.org/showthread.php?p=6258548#post6258548) )

Also, with VLC I had to go into it's own sound preferences and switch that to ALSA as well to get it to play audio.

---

### Post by nynoah on 2008-11-28
any of you guys know how to get the sound effects in Kopet to work?

---

### Post by AlexOslo on 2008-11-29
> **bangmalley said:**
> go to System->Preferences->Sound, switch to ALSA.

Thank you for this!
I think I know what's happened: A dialogue box came up previously and alerted me of something about the sound not working in VLC because of another application running (Amarok, I think). I mistakenly hit "yes" to the disable sound option, so now I need to enable it again, somehow.

Alex

---

### Post by AlexOslo on 2008-12-17
> **AlexOslo said:**
> Thank you for this!
I think I know what's happened: A dialogue box came up previously and alerted me of something about the sound not working in VLC because of another application running (Amarok, I think). I mistakenly hit "yes" to the disable sound option, so now I need to enable it again, somehow.

Alex

I just rephrased and reposted this in a new thread, here:
[http://ubuntuforums.org/poll.php?t=1013732&polloptions=4](http://ubuntuforums.org/poll.php?t=1013732&polloptions=4)

---

### Post by Fidelaki on 2008-12-30
> **bangmalley said:**
> go to System->Preferences->Sound, switch to ALSA.

Thanx. That solved my problem.

---

