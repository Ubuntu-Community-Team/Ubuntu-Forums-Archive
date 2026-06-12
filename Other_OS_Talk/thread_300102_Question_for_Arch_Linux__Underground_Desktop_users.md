---
title: "Question for Arch Linux / Underground Desktop users."
date: 2006-11-15
forum: Other OS Talk
---

### Post by manmower on 2006-11-15
Hi all,

I'm a happy Kubuntu user but looking to delve a little deeper into Linux. Arch Linux has caught my attention at the moment, however one problem is the only box I have available to try it on connects to the internet via wireless only (Atheros chipset + WPA protected network). This was a breeze to set up in the latest Kubuntu release but I'm not entirely confident that I'll pull it off on CLI in a fresh install of Arch with no internet connection. I have a feeling I will have better luck with Underground Desktop, and there are various other reasons for considering it (being a KDE user for example, or the fact it just recently had a new release), but I read that it installs LILO to the MBR automatically with no questions asked. This is the second problem: I need this machine to dual boot with Windows XP Pro. The third problem is my bandwidth is limited so I'd rather choose one than download both, at least for now. :) 

So I'm looking for advice from actual users of these distributions:

- Since Arch is what I want to learn: is Underground Desktop essentially just Arch with some bells and whistles or are there any important differences, incompatibilities?

- Will the installer detect my NTFS partition and add an option in the bootloader for Windows XP, or alternatively: can it be easily adjusted afterward (I'm new to LILO)?

- Also if there are any arguments/reasons for choosing one of these distros over the other (considering my situation as explained above of course) I'd be glad to hear your input.

Thanks in advance!

---

### Post by manmower on 2006-11-16
Alright, I guess I answered my own question. Let's just say I ran into some extra bandwidth and downloaded both anyway. It seems that Underground Desktop is not very popular around here, perhaps because it is so young. But I have to tell you it was hands down the best and most polished LiveCD I've ever tried (and I've been trying a lot of them lately)! Being based on Arch it is quite fast yet offers a complete and smooth-looking KDE (although quite reminiscent of Windows and its Royale theme). It allegedly uses the Reiser4 file system and a kernel with Con Kolivas' patches by default when installed. I never did install it though, because although it comes with Kwlan which supports WPA, unfortunately the madwifi modules were not present.

I decided if I was going to have to install them myself I might as well do it the "hard" way. So I went with Arch Linux to make the whole experience more educational. Did a base install and after an evening of command line editing of config files and dragging the pc up the stairs and back down to get some necessary packages via wired network my wireless now works perfectly. Had zero problems configuring it although the Arch Wiki guide is a bit outdated, it was quite straightforward to figure out. I'm loving Arch so far so I guess I'll be seeing some of you in the Arch Talk thread soon.

Conclusion: 

[Underground Desktop](http://underground.geekcode.info/portal/posts/): amazing LiveCD for KDE users, complete and polished without being bloated.

[Arch Linux](http://www.archlinux.org/): Fast, lightweight, and looks like an excellent tool for those who are willing to learn.

---

