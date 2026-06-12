---
title: "install kernel 2.6.25, hardy"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Arand on 2008-04-27
How do I upgrade to the 2.6.25-kernel in Hardy.

Is this doable without too much effort?

Will this kernel de the default in 8.04.1

- Arand

---

### Post by SOULRiDER on 2008-04-27
The kernel just came out and isnt i the repos. If you want ti youre going to have to compile it yourself or find a deb for Ubuntu. IMHO, unless you really need the improvements, just wait until its officially released.

---

### Post by Arand on 2008-04-27
alright, is this going to be in proposed-updates, or backports?

So I won't have to wait 'til 8.04.1 to try it?

- Arand

---

### Post by FredB on 2008-04-27
> **Arand said:**
> How do I upgrade to the 2.6.25-kernel in Hardy.

Is this doable without too much effort?

Will this kernel de the default in 8.04.1

- Arand

Simple question : does your hardware need it ? I don't think it will be provided in 8.04.1

---

### Post by Arand on 2008-04-27
What it will fix, according to the NTFS-3G Lead Developer, is permissions for ntfs mounts, which as of now gives write permissions to everyone, regardless of settings.

See [Bug #190329]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/190329")

It's not a complete crisis on my part since I'm kinda okay with mounting it read-only.

So there will probably be a whole lot of hassle, and possible instability in installing this then?

- Arand

---

### Post by sdennie on 2008-04-27
2.6.25 should be stable but, unless you are familiar with installing a custom kernel, it will indeed be a hassle to install.  The stock Ubuntu kernel often includes upstream bug fixes so, it may be worth waiting to see if the specific fix you want from 2.6.25 ends up in the default kernel.

---

### Post by Arand on 2008-04-27
Alright, should I suggest this to somebody, or is it just waiting from here?

- Arand

---

### Post by SOULRiDER on 2008-04-27
Theres a thread on the Tutorials and Tips forums called "Master Kernel Thread" explaining how to compile kernels and configure them. Those who want 2.6.25 should check it out.

---

