---
title: "Trouble installng ubuntu on chromebook"
date: 2016-08-30
forum: New to Ubuntu
---

### Post by rs-design on 2016-08-30
Hi new here and new to linux/ubuntu. I have attempted to install ubuntu on my Acer CB3-111 by following the procedures on this link:
[https://gist.github.com/timrs2998/c802c6f4a631d248d70f](https://gist.github.com/timrs2998/c802c6f4a631d248d70f)

The installation failed mid way through with the following error:

```
After this operation, 9180 kB of additional disk space will be used.
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libroken18-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1
Temporary failure resolving 'archive.ubuntu.com'
```

There was a long list of these failures followed by another long list of the following failures:

```
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libasn1-8-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libasn1-8-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb)Temporary failure resolving 'archive.ubuntu.com'
And then:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Failed to complete chroot setup.
Unmounting /mnt/stateful_partition/crouton/chroots/trusty...
```

So I tried the follwoing without success:

```
chronos@localhost ~/Downloads $ sudo apt-get update
sudo: apt-get: command not found
chronos@localhost ~/Downloads $ sudo apt-get update --fix-missing
sudo: apt-get: command not found
chronos@localhost ~/Downloads $ sudo apt-get upgrade --fix-missing
sudo: apt-get: command not found
```

Any help would be appreciated.

---

### Post by rs-design on 2016-08-31
For other who experience the same problem, I downloaded crouton direct from github and installed the kde desktop, that did the trick.

---

### Post by robertusa on 2016-12-06
[COLOR=#000000]Dual boot is the way to go to get a clean and full Linux install, and maintain the ChromeOS distro properly. "Sideloading" makes for easy Ubuntu-like installs, but doesn't really provide the best of each native environment from a long-term use and flexibility perspective. Decoupling OS variants is often the best approach to achieving the value from each distro.[/COLOR]

[COLOR=#000000]However, there are some installation glitches with the current model Acer and Samsung Chromebooks.[/COLOR]

[COLOR=#000000][COLOR=#000000]I found in necessary to use [/COLOR][/COLOR][https://etcher.io/](https://etcher.io/)[COLOR=#000000][COLOR=#000000] to burn the ISO image to USB, as the standard Ubuntu tools would not work reliably, seemingly building an incompabible boot stack configuration.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Having accomplished this, the next hurdle is that the native hardware USB keyboard-mouse is completely non-functional. I imagine a USB keyboard-mouse might work, but I do not have them available to test.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]These are very popular devices in education and business. These devices could be useful for R&D and software development with 4G RAM and dual core. Not the fastest, but certainly something usable while lowering the cost of entry for software development to $100 to $200. The Samsung xe500c13-K02 would be much more useful with Ubuntu, Mint, or GalliumOS installed.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Can someone take the lead in updating-fixing the boot-config-stack to support the Samsung xe500c13-K02us?[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]I'm happy to participate in testing of the Samsung xe500c13-K02 or Acer [/COLOR][/COLOR][COLOR=#417394]CB3-111[/COLOR][COLOR=#000000][COLOR=#000000]. I also have access to many other models of Chromebook, Dell, and other machines to test. [/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]What is needed is someone to coordinate the release of "debug mode" Ubuntu OS so we can get these popular machines up and running Ubuntu vs. ChromeOS.[/COLOR][/COLOR]

---

