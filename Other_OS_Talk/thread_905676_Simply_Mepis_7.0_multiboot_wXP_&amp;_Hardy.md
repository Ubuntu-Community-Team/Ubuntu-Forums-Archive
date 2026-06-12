---
title: "Simply Mepis 7.0 multiboot w/XP &amp; Hardy"
date: 2008-08-30
forum: Other OS Talk
---

### Post by kansasnoob on 2008-08-30
OK, I'm a glutton for punishment! Fact is I've installed Ubuntu, Xubuntu, and Kubuntu for nearly 30 seniors that were still stuck in Win 98 or ME and I try very hard to keep them on actual Ubuntu as it's what I prefer, and since I use it myself it's simply easier for me to tweak to their needs!

Occasionally someones system specs are just reasonable enough I go for Xubuntu, but more often I upgrade them to a cheap "all-in-one" mobo and I normally have DDRII RAM pulls and PS pulls from paying customers upgrades so I can get them a good box for about $60.00.

But, enough for the backstory. Some really like the KDE desktop but Kubuntu, both 7.10 and 8.04, drive me nuts with problems, and I do this for free (sometimes I even go out of pocket), so I've been looking for other KDE alternatives. Here's where Simply Mepis 7 comes in.

I've been trying it as time allows and it seems to suit my needs quite well but I've not yet tried multi-booting it! So sooner or later you have to get your feet wet and I'm wondering if anyone else has tried multi-booting Mepis with Win and Hardy.

I'm not in a rush, I'd just like to know of any potential pit-falls before I try it the first time. I could try dual booting with Ubuntu first on my trial machine I guess, but I've found people here to be a true wealth of knowledge .............. so why not ask?

I just never want to fall into the hall of shame like I did with Open SUSE! I know .............. choices, choices! But SUSE sucked for me!

---

### Post by caljohnsmith on 2008-08-30
If you are going to give Mepis its own partition, which I think is obviously what you have in mind, then it really doesn't matter what other OSs you might have in the other partitions on that HDD as far as Mepis is concerned. So you could have Windows 95, Ubuntu, Kubuntu, Fedora, or anything else on your HDD, but as long as you give Mepis ample disk space for its partition, then Mepis couldn't care less what else is on your HDD. :)

The main thing to consider with a multi-boot system is which OS is going to control the boot loader in the MBR. Assuming you will use Grub, I would first pick which distro you want to control Grub in the MBR; then when you install any other distros, have them *install Grub/Lilo to the boot sector of the partition they are in, rather than the MBR*. So when it comes time to install Grub in the distro's installer, have it install Grub to (hd0,X), or the distro's partition, rather than (hd0) which is the MBR. Then in the menu.lst of the distro that controls the MBR, just put:
```
title  Mepis
root   (hd0,X)
chainloader +1
```
And that's all you would need to boot Mepis for example (no messing with kernel/initrd/option lines). 

P.S. Just as a quick side note, have you by chance given PCLinuxOS/Mandriva a try? They come with KDE and they work really well for me.

---

### Post by kansasnoob on 2008-08-30
Hmmm, thank you! I hadn't thought to check if Grub was the default Mepis bootloader. I'd think so.

---

### Post by kansasnoob on 2008-08-30
I'll actually be removing the OS that controls Grub right now (Linux Mint) and replacing it with Mepis. I think now I'll return Grub to Hardy before I start.

---

### Post by kansasnoob on 2008-08-30
> have you by chance given PCLinuxOS/Mandriva a try? 

I will now!

---

### Post by caljohnsmith on 2008-08-30
Did I perchance misunderstand your original question? 

By the way, PCLinuxOS is a Debian derivative while Mandriva is Red Hat based, so you will probably feel more at home with PCLinuxOS if you haven't yet used Red Hat's Yum program installer. I just thought I would mention that, because if you are more comfortable with Synaptic than Yum, I would give PCLinuxOS a shot first.

---

