---
title: "[SOLVED] How do I compile the source for this?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-20
[http://www.cyberlink.com/english/products/powercinema/pcm-linux/pcmlinuxgpl.jsp](http://www.cyberlink.com/english/products/powercinema/pcm-linux/pcmlinuxgpl.jsp)

The download link is at the bottom.

Thanks in advanced!

---

### Post by iaculallad on 2008-06-20
Instead of downloading the entire 143.9MB file, could you post the folder contents of that sources_zip file instead.

---

### Post by diablo75 on 2008-06-20
Here's a sample:

```
zeke@ubuntu:~/Desktop/PCMLinux_GPL_sources$ ls
alsa-driver-1.0.4.tgz  PCMLinux_GPL_sources
zeke@ubuntu:~/Desktop/PCMLinux_GPL_sources$ cd PCMLinux_GPL_sources/
zeke@ubuntu:~/Desktop/PCMLinux_GPL_sources/PCMLinux_GPL_sources$ ls
acpid     busybox  freetype  gtk          libc             ncurses  syslinux
alsa_lib  dialog   glib      ion_install  lilo             PCM      util-linux
autofs    ffmpeg   grub      kernel       MPlayer-1.0pre7  SDL      zlib
zeke@ubuntu:~/Desktop/PCMLinux_GPL_sources/PCMLinux_GPL_sources$ 

```

---

### Post by iaculallad on 2008-06-20
WoW.. Bunch of directories??? Must be a huge app. Try to wait for other member's reply if they did have experience on compiling this CyberLink's PowerCinema. I just thought it would simply be a make/configure/install procedure.

---

### Post by N.N. on 2008-06-20
From what I understand that .zip file simply contains the source codes of some of the software components that are included in the product. It doesn't contain the source code of the full product.
> This product includes certain copyrighted third-party software components [...] For the list of components of such nature, and to acquire the full source code of **these** licensed components, including any scripts to control compilation and installation of the object code, please see the page below.

If you're actually interested in installing the software components, I'm sure you can achieve that by using the package management software available in Ubuntu.

---

### Post by sdennie on 2008-06-20
That ls output looks like an complete media distro.  How do you plan on using it?  Can you not just install the relevant packages under Ubuntu or install Mythbuntu?

---

### Post by diablo75 on 2008-06-20
Well... I just checked Synaptic, and did a search for "cyberlink", but it didn't give any results.  Same goes for the Applications>Add/Remove applet....

My assumption from the replies I've gotten so far is that I should use the libdvdcss2 in Mediabuntu, am I right?  That's what I would do.  I'm actually looking into this Cyberlink software source compiling for someone else, but I will pass along the suggestion for them to install libdvdcss2 instead (since it is much easier).

---

### Post by N.N. on 2008-06-20
> **diablo75 said:**
> Well... I just checked Synaptic, and did a search for "cyberlink", but it didn't give any results.  Same goes for the Applications>Add/Remove applet....

My assumption from the replies I've gotten so far is that I should use the libdvdcss2 in Mediabuntu, am I right?  That's what I would do.  I'm actually looking into this Cyberlink software source compiling for someone else, but I will pass along the suggestion for them to install libdvdcss2 instead (since it is much easier).

What I was trying to say is that I don't think CyberLink is available for free, hence the "Trial Version" and "Buy Now" links on the CyberLink website.

My understanding is that CyberLink is proprietary software, but that it includes certain third-party components that are licensed under terms that bind the developers of the CyberLink applications to provide the source code of those components on their website. That means that only the source code of the open source components are provided on that page, not the source code of any of the CyberLink applications. It follows from this that you won't find any CyberLink software in the Ubuntu repositories, nor in the software repositories of any other Linux distribution. The only way to obtain it is to buy it from the website.

Unless you're interested in paying for the software, I'd suggest you look into an open source alternative (of which there are plenty).

---

