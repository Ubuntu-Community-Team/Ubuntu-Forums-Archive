---
title: "Pure Ubuntu Gnome and Purge all of Unity?"
date: 2014-12-27
forum: New to Ubuntu
---

### Post by newbietwo on 2014-12-27
Can this be safely done?

If so, can someone please layout the steps.

Thanks.

---

### Post by 3246251196 on 2014-12-27
Try installing an ubuntu server distro which comes with minimal packages and then install gnome-desktop-environment?

---

### Post by vasa1 on 2014-12-27
Removing Unity may not be as simple as starting afresh with the distro you actually want: [http://ubuntugnome.org/](http://ubuntugnome.org/)

---

### Post by jimmy-frydkaer on 2014-12-28
Easiest way to serenity is a clean install of Ubuntu GNOME :KS

---

### Post by Bucky Ball on 2014-12-28
> **jimmy-frydkaer said:**
> Easiest way to serenity is a clean install of Ubuntu GNOME :KS

+1. Otherwise you're looking for needles in a haystack. Pretty hard to get rid of every skerrick of Unity, and 'sudo apt-get remove/purge unity' won't cut it.

---

### Post by buzzingrobot on 2014-12-28
> **Bucky Ball said:**
> +1. Otherwise you're looking for needles in a haystack. Pretty hard to get rid of every skerrick of Unity...

Just for jollies, I went through a "purge Unity" exercise after a Mate install several months ago. It was a deliberately pointless exercise on a machine that was gong to get a fresh install anyway.

My first attempt -- go through Synaptic's listing and check everything related to Unity for deletion -- generated a cascade of unwanted deletions.

Second attempt: Methodically deleting a few packages at a time, and then re-installing the unrelated packages that had also been removed. This was time consuming, but I was able to remove almost all Unity-related packages without breaking the system.

A very few Unity-related libraries remained because a number of packages are compiled against them so they can play happy with Unity. E.g., Thunderbird. 


There's no benefit from it, though, and I don't recommend it.

---

