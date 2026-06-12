---
title: "Installing Fedora 7 as 3rd O/S, need infos"
date: 2008-05-19
forum: Other OS Talk
---

### Post by Browser_ice on 2008-05-19
I currently have as dual boot Windows XP Pro + Ubuntu 8.04.

I want to install Fedora 7 so I will have 3 O/S.

I have read the "How to Multi-boot (Maintain more then 2 OS)" thread but after this I am still unsure. 

Can I simply install Fedora 7 and hoping it will detect my 2 O/S, install itself as a 3rd one and not mess up my Grub ?

Do I have anything special to do prior to doing this ?

---

### Post by LaRoza on 2008-05-19
> **Browser_ice said:**
> 
Can I simply install Fedora 7 and hoping it will detect my 2 O/S, install itself as a 3rd one and not mess up my Grub ?

Do I have anything special to do prior to doing this ?

I am triple booting. It is easy. As for "simply installing", no. The Fedora disk isn't psychic as of Fedora 9 so I doubt 7 is.

I don't know what your scheme is, and how you have your disks. The simplist (but not best) way to do it is to have four partitions (one is swap)

What is the size of this disk and what is on it? 

I don't know about Fedora 7. Any reason for not using 9?

You can use the Fedora disk to do the partitioning, but I would use the latest GParted. Give your disk information for more precise details.

---

### Post by Browser_ice on 2008-05-19
I have 2 HD : 80Gb + 250Gb

HD1
-Windows XP : 40Gb
-Ubuntu 8.04 : 40Gb

HD2
- Projects (XP) : 20Gb
- Games (XP) : 20Gb
- Music+other games (XP) : 50Gb 
- Temp folders (XP) : 10Gb  -> internet, windows, users
- Install files (XP): 25Gb
- backups+movies (XP) : 100Gb
- Ubunutu Swap : 5Gb
- unmounted : 5Gb -> swap for Fedora

Humm, missing unused 15Gb on my HD2 and can't find it. 


I already split my swap partition so Fedora could use the other half.

I want to resize my Ubuntu from 40gb to 20gb, leaving an unmounted free 20Gb but the Gnome Partition editor doesn't want to do it.

SO bottom line, I want on HD1 : XP + Ubuntu + Fedora and on my HD2 : XP + Ubuntu Swap + Fedora Swap

I don't have Fedora 9 nor 8 because I only have 7 burned on a DVD. Office is using Fedora 7 so want to go with it.

---

### Post by LaRoza on 2008-05-19
> **Browser_ice said:**
> 

I already split my swap partition so Fedora could use the other half.

I want to resize my Ubuntu from 40gb to 20gb, leaving an unmounted free 20Gb but the Gnome Partition editor doesn't want to do it.

SO bottom line, I want on HD1 : XP + Ubuntu + Fedora and on my HD2 : XP + Ubuntu Swap + Fedora Swap

I don't have Fedora 9 nor 8 because I only have 7 burned on a DVD. Office is using Fedora 7 so want to go with it.

You can use the same swap partition for both. Use a live cd to resize it. Fedora should be able to do this. Remember to take the usual precautions when resizing.

If Fedora installs and doesn't find the other OS's, you can easily add them.

---

### Post by Browser_ice on 2008-05-19
I finally managed to install Fedora 7. I had to retry 4 times. First 3 times were because when it was time to actually do the installation, it said the swap partition wasn't initialized (tried in GUI and text format and had to boot into Ubuntu and format it myself). The 4th time was the one it finally managed to install it.

But, when I re-booted, I noticed it replaced the Grub menu with its own and it left me something like 5 second to make a choice. The choices were not visible. It was either hit a key to go into the menu or boot to the default O/S (windows XP). I restarted it and went into the grub menu. To my surprise it is now a graphic menu. I have found no way to edit the whole thing directly from there. Choosing Ubuntu to boot fails as there are no parms/options given and when it tries to boot it, it doesn't recognize it (don't recall exact message). So I had to boot back into Fedora (using it now to write this thread) and hoping to edit the Grub to fix this.

Before doing the 4th trial of installing, I had taken a copy of my Grub menu.lst and sent it to my hotmail for references. I had a feeling it would be messed up as during the install you have no choice of editing each O/S you add to it (didn't automatically recognized my Ubuntu and therefore I had to manualy add it to the list).

I will look and try but can I change this new GUI Grub to add the right infos to boot my Ubuntu and also to change the timer for the choice ?

I edited my menu.lst in Fedora and added the lines for Ubuntu (lines taken from my old menu.lst). I also put in comment the hiddenmenu so I could see the choices. Its currently downloading updates but as soon as it reboots, my changes should be ok (I hope).

---

### Post by LaRoza on 2008-05-19
> **Browser_ice said:**
> 
I edited my menu.lst in Fedora and added the lines for Ubuntu (lines taken from my old menu.lst). I also put in comment the hiddenmenu so I could see the choices. Its currently downloading updates but as soon as it reboots, my changes should be ok (I hope).

That may work out. If it doesn't, you can just reinstall Grub using the Ubuntu CD.

---

