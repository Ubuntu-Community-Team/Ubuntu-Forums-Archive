---
title: "Power Outage while updating"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by Schwenkdawg on 2011-10-18
Hey ya'll

First off, this is the first time I've posted anything here, even though I've had Ubuntu for about 1.5 years now. So, Hi!

Now the issue:
While I was downloading the most recent update, a power outage happened at my apartment and my comp shut down in the middle of updating. Now, when I try to boot into Ubuntu, it just shows a black screen with the time at the top, and a large picture of a desktop computer that says (my name) desktop. I can't even move my mouse or anything. What can I do to fix this, and if at all possible, keep the directions simple to follow, because I'm still very new at all this. Thanks a million!

---

### Post by hansdown on 2011-10-18
Hi, Schwenkdawg.

Do you still have your original install disk?

I know this is pretty high on the "suck-o-meter", but your best bet, is to do a fresh install.

Please tell me it was an "update", and not an "upgrade"?

---

### Post by dFlyer on 2011-10-18
First are you dual booting? If so can you access windows or what every os you were using beside ubuntu?

Second was this and update to an install or an distro upgrade from and older version?

---

### Post by Schwenkdawg on 2011-10-18
> **hansdown said:**
> Hi, Schwenkdawg.

Do you still have your original install disk?

I know this is pretty high on the "suck-o-meter", but your best bet, is to do a fresh install.

Please tell me it was an "update", and not an "upgrade"?

I don't have my original install disk (one of my computer engineering friends installed it for me), but luckily I'm dual-booting Windows (which is how I'm managing to type this right now), so I could make one once I go out and get a disc. Sadly, I'm pretty sure it was an upgrade. Started it, left the house to go get dinner, got back and noticed that alarm was reset, computer is angry. :(

---

### Post by wildmanne39 on 2011-10-18
Hi, reboot your computer and as soon as it comes on start tapping the shift key if the grub menu comes up choose recovery then on the next screen if you see the option to fix broken packages take it if is says root with networking or shell prompt choose that instead.
and do this.
```
sudo apt-get update && sudo apt-get upgrade
```
Thank you

---

### Post by Schwenkdawg on 2011-10-18
> **wildmanne39 said:**
> Hi, reboot your computer and as soon as it comes on start tapping the shift key if the grub menu comes up choose recovery then on the next screen if you see the option to fix broken packages take it if is says root with networking or shell prompt choose that instead.
and do this.
```
sudo apt-get update && sudo apt-get upgrade
```
Thank you

Tried this. terminal in recovery mode won't let me type. simplest way to do this now is probably just re-installing isn't it. Will that lose me all my saved stuff?

---

### Post by hansdown on 2011-10-18
> **Schwenkdawg said:**
> Tried this. terminal in recovery mode won't let me type. simplest way to do this now is probably just re-installing isn't it. Will that lose me all my saved stuff?

Sorry to say, it will,Schwenkdawg.

Many times, I've reinstalled, to fix things, that went bad, because I like to learn new things.

Now, I do fresh installs, to keep in practice.I hope all goes well, Schwenkdawg.

---

### Post by wildmanne39 on 2011-10-18
Hi, when you get booted to the screen that if stops on hit ctrl+alt+f1-f6 and see if any of those let´s you type in your user name and password then run that command in my last post, and it will be a blank screen.

ctrl+alt+f7 after the upgrade.
Thank you

---

### Post by Schwenkdawg on 2011-10-18
> **hansdown said:**
> Sorry to say, it will,Schwenkdawg.

Many times, I've reinstalled, to fix things, that went bad, because I like to learn new things.

Now, I do fresh installs, to keep in practice.I hope all goes well, Schwenkdawg.

So, it will delete all my saved stuff? Well, crap, there goes 250ish gigs of anime down the drain, as well as my resume, cover letters, etc. Ah well, lesson learned I guess

Yea, it's not even showing that frozen image anymore, just a wall of text with no opportunity to type in commands. tomorrow, i get a live disc and fix this...hopefully

---

### Post by hansdown on 2011-10-18
> **Schwenkdawg said:**
> So, it will delete all my saved stuff? Well, crap, there goes 250ish gigs of anime down the drain, as well as my resume, cover letters, etc. Ah well, lesson learned I guess

Yea, it's not even showing that frozen image anymore, just a wall of text with no opportunity to type in commands. tomorrow, i get a live disc and fix this...hopefully

If you can burn a "live" disk, try running it, and choose, "try ubuntu".

Open a terminal, and enter

```
gksudo nautilus
```

You may get your info back.

^crosses fingers, and eyes*, for good luck.

---

### Post by mikechant on 2011-10-18
Yes, just to emphasize, there is no good reason you should lose your data, as long as you have some device such as an external hard drive to copy it to, you should be able to copy all your data off the unbootable install while running from a Live CD or USB.

However, it's probably a good idea to do a file system check on the partition containing your data before you try to copy it or update it in any way.
Ask if you don't know how (e.g. gparted can do it if you're familiar with that).

Unless you're very unlucky, only files which were open for update at the time of the crash should be lost or damaged - hopefully none of your personal data.

---

