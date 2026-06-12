---
title: "Booting ISO w/ iPXE:initramfs Unable to find a medium containing a live file system"
date: 2016-07-29
forum: New to Ubuntu
---

### Post by fitzzz on 2016-07-29
Hello, this is my first post on this forum, so if I omit anything please let me know.

[COLOR=#333333][FONT=Roboto]I’ve been tasked with setting up a bootable Linux ISO over iPXE so the company I work for may use it to access guest machines (we do this to pull drivers from our network to apply to freshly imaged PCs) that are usually themselves running Win7.[/FONT][/COLOR]
Right now I'm trying to boot an ISO over iPXE using FOG, the ISOs I have tried are Ubuntu 16.04, Mint 17.3, and Hiren's Boot CD. As of this moment, Hiren's works.

[COLOR=#333333][FONT=Roboto]**The system running fog is Linux Mint, and is a VM I access through vSphere. The guest machine in my scenario is another (basic, no drive/OS etc) VM. **From what I’ve seen, some solutions involve physical problems such as USB3.0 vs USB2 sockets, etc., so I don't think that comes into play at all using a VM.[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]Ubuntu and Mint both go into their respective ISOs, I can select Try Without Installing and all that good stuff, and then it eventually stops, leaving me with: 
[B]BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

[/B]I've looked it up and have yet to find a solution that applies to what I'm working with. 
I also have tried going to the FOG forums, which helped another problem I had, but I have a feeling this is a problem inherent to using VMs, or configuration of my server... any leads would be awesome.

Thank you for your time, I'll try to respond as soon as possible to any replies.
I will try to check periodically on the long weekend, but I can't work on it at all from home.[/FONT][/COLOR]

---

### Post by kyrithis on 2016-07-29
About the only thing I can find that can be applied to a network boot would be an corrupted image. Try running a md5 check on the image when you can and make sure it matches up. I will update my post should I find any more relevant information.

---

