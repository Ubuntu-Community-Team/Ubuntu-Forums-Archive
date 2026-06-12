---
title: "Sound broke after update"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by flamingsole on 2008-07-19
Hello,

After a recent update, my sound stopped working. It's been a few weeks or so, and I've let it go as I haven't been able to work on this system as much as normal, lately. Anyway, I seem to remember running into this issue on Gutsy, at some point, but I can't find the solution.

My motherboard does have two sound cards, if that is relevant to the solution. The one that is active is a NVIDIA.

Thanks for any ideas,
Jon

---

### Post by crmccreary on 2008-07-20
I bought an inexpensive emachines recently and installed a fresh copy of hardy. The boot sounds and such were playing but there was no sound from any media player. I went to system->preferences->sound and changed Music and Movies from autodetect to something that worked. In this case, ALSA worked.

Of course your problem may be much deeper than mine, but it's an easy thing to try.

---

### Post by t0p on 2008-07-20
> **flamingsole said:**
> Hello,

After a recent update, my sound stopped working. It's been a few weeks or so, and I've let it go as I haven't been able to work on this system as much as normal, lately. Anyway, I seem to remember running into this issue on Gutsy, at some point, but I can't find the solution.

My motherboard does have two sound cards, if that is relevant to the solution. The one that is active is a NVIDIA.

Thanks for any ideas,
Jon

It happened to me too!! And I was gutted... until I found this fix: [http://ubuntuforums.org/showthread.php?p=4928900]("http://ubuntuforums.org/showthread.php?p=4928900")

This worked for me... hope it's good for you too!!

---

### Post by iaculallad on 2008-07-20
Install the linux-generic header to get back your Audio:

```
sudo aptitude install linux-generic
```

---

### Post by flamingsole on 2008-07-22
> **iaculallad said:**
> Install the linux-generic header to get back your Audio:

```
sudo aptitude install linux-generic
```

I got an error message during this, which I'm assuming might be related to my sound not working.

I am apparently unable to stop, uninstall, or upgrade my mysql installation. I've been seeing this error for a while, maybe exactly as long as my sound hasn't been working. A number of searches have failed to get a good fix for this, as well.

Do you think these are connected?

Thanks for your help,
Jon

---

### Post by iaculallad on 2008-07-22
> **flamingsole said:**
> I got an error message during this, which I'm assuming might be related to my sound not working.

I am apparently unable to stop, uninstall, or upgrade my mysql installation. I've been seeing this error for a while, maybe exactly as long as my sound hasn't been working. A number of searches have failed to get a good fix for this, as well.

Do you think these are connected?

Thanks for your help,
Jon

I don't think so. The sound problem limiting you to your mysql. Had your tried the command below to remove your mysql:

```
sudo aptitude --purge remove mysql-server-x.x mysql-server
```

x.x = version number

---

### Post by flamingsole on 2008-07-22
Interestingly, after I finally got MySQL settled and ran the aforementioned update, I logged off and when I came back the sound worked, but then the next time I logged on it didn't work.

There are two sound cards in this machine. I seem to remember a fix that would allow me to specify which one was loaded on startup, but I can't remember where that is.

Thanks for your willingness to help.
Jon

---

### Post by iaculallad on 2008-07-23
> **flamingsole said:**
> Interestingly, after I finally got MySQL settled and ran the aforementioned update, I logged off and when I came back the sound worked, but then the next time I logged on it didn't work.

There are two sound cards in this machine. I seem to remember a fix that would allow me to specify which one was loaded on startup, but I can't remember where that is.

Thanks for your willingness to help.
Jon

To list all the soundcard present in your PC:

```
asoundconf list
```

To set your sound card priority:

```
asoundconf set-default-card sound_card_from_asoundconf_list
```

---

### Post by kansasnoob on 2008-07-23
> My motherboard does have two sound cards, if that is relevant to the solution. The one that is active is a NVIDIA.

I think that's at least part of it. I'm seeing way too many sound related issues here on the forum.

This is not a fix, but I'd try installing > startupmanager from synaptic and then try booting different kernels to see if the problem goes away with previous kernels. (That way your changes can all be reverted in gui - no breakage!)

Other than that the first thing I do after installing Hardy is install > gnome-alsamixer from synaptic. It then shows up under Applications > Sound & Video. Pay particular attention to the first three toggles and the last four toggles.

Also look at this:

[http://ubuntuforums.org/showthread.php?t=855544](http://ubuntuforums.org/showthread.php?t=855544)

That is in a nutshell pretty much everything I know about sound.

---

