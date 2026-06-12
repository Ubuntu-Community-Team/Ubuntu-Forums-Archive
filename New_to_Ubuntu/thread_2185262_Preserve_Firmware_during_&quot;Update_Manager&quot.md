---
title: "Preserve Firmware during &quot;Update Manager&quot;"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by shabuboy on 2013-11-01
I am new to Ubuntu and need some help. On my OLD OLD Dell Inspiron 8600 have a Broadcom BCM43xx wireless card. After so much trial and error was able to get it running just fine. This was my installation due to a non-PAE processor and wanting LTS, hence the reason to go to Ubuntu 12.04.
- Lubuntu 12.04. Got the wireless to work following offline option at [https://help.ubuntu.com/community/BroadcomSTA(Wireless)](https://help.ubuntu.com/community/BroadcomSTA(Wireless))
- Installed Ubuntu 12.04
- Updated all available options using "Update Manager". This is where I ran into issues, as the update died around 80%. Nevertheless, got pass it and installed all. However, at the end of all this, had to reinstalled the wireless driver, following the link again.

So my question is this: How can I prevent future updates from overwriting/deleting the firmware/driver again?

---

### Post by DuckHook on 2013-11-01
Hi shabuboy,

This is odd. I have a half-dozen old Dell laptops all running Linux and all requiring the Broadcom fixes on a pristine install. However, after the initial monkey business, kernel updates don't break my modules and they all work fine with each kernel update.

Since this is a relatively new install, back up any critical data and then do:```
sudo apt-get update
``````
sudo apt-get autoremove
``````
sudo apt-get clean
```The above is designed to clear out any cruft remaining from your previous install attempts.

Then do:```
sudo apt-get install fakeroot dkms
```...which should pull down the Dynamic Kernel Module Support system. DKMS allows the system to autobuild driver modules every time the kernel changes in the course of a regular update. However, if you re-install the system from scratch, you bypass DKMS altogether and it cannot intervene.

If DKMS is not already installed, then your problem may be as simple as the fact that DKMS is absent. If it is already installed, then your problem is more complicated and will need more detective work.

DKMS is not smart enough to look back in history and recognize your previous Broadcom travails. Therefore, your next kernel update may require you to go through the whole Broadcom nonsense again. However, DKMS should thereafter automatically compile the proper module of any future kernel updates.

Let us know how it goes.

---

### Post by shabuboy on 2013-11-04
ok, thanks, let me see what I find out.

---

### Post by mörgæs on 2013-11-04
It seems like you have had a lot of work just getting some operative system to run. If you want something stable for a non-PAE computer you could try Bodhi Linux.

When that works (using wired internet access) most of the Broadcoms should be easy to install.

---

### Post by DuckHook on 2013-11-04
> **mörgæs said:**
> If you want something stable for a non-PAE computer you could try Bodhi Linux.+1

@shabuboy

Bodhi is one of my favourite distros. Just be aware that it is not your average distro.

1. First of all, it is an independent distro based on the Ubuntu repositories. So while you can install into Bodhi almost anything that would work in any of the official flavours, Bodhi is not actually supported by Ubuntu. You would have to go to the Bodhi site and forums, which are quite active.

2. The philosophy behind Bodhi is the opposite of Ubuntu's. Whereas Ubuntu strives for as complete an experience as is reasonable in its typical install, Bodhi strives for minimalism. It comes with almost no preloaded apps and a pleasingly minimal set of drivers and services. For paranoids like some of us, this is the next best things to a minimal install. Sort of like the mini.iso but with an X environment. We can pick and choose only the apps we want and avoid the bloat and cruft that characterizes so many mainline distros. If you like to customize your computing experience down to the nth degree, Bodhi is the way to go.

3. Bodhi uses the Enlightenment environment which is like a cross between a full Desktop Environment and a plain Window Manager. It takes some getting used to, but once you get the hang of it, you'll be wondering why everyone isn't doing things this way.

4. Bodhi brings back incredible zip and responsiveness to some awfully old HW. It gives some of my oldest stuff a second life. However, this is only true of its default install in a pristine state. If you choose to then bloat it up with compiz, a large DE, inflated apps, and modules/services out the yin-yang, it will slow your old HW down just as if you had installed the bloated flavour to start with. There's an art to choosing only the most minimal apps for Bodhi--those with tiny footprints and few to no dependencies--and it is both challenging and rewarding to customize an installation that does everything you want it to do, but not a smidgen more. This obsession with absolutely optimal computing efficiency has long been lost in the mainstream distros.

I would suggest burning a DVD and going for a test drive. In your case, make sure you use their non-PAE version. Whatever you use, I'm afraid you're stuck with the extra work needed to install Broadcom drivers.

---

### Post by mörgæs on 2013-11-05
Agree on everything above, would just like to add that a DVD is not necessary. Bodhi fits to a CD.

---

