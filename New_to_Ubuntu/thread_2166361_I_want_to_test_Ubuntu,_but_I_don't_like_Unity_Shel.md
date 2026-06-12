---
title: "I want to test Ubuntu, but I don't like Unity Shell"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by renato3 on 2013-08-08
Hi, I want to test Ubuntu, but I don't like Unity Shell. Can I remove it after installation and install another desktop environment like Gnome Shell or Mate without harming the system? If I do so, will these desktop environments have the default ubuntu theme already?

---

### Post by SweetAurora on 2013-08-08
Here:
[http://ubuntugnome.org/](http://ubuntugnome.org/)
The officially supported, Canonical Endorsed, Gnome Sell based Ubuntu. Is this what you are looking for? :)

---

### Post by ibjsb4 on 2013-08-08
Try Gnome-Classic

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:
```
sudo apt-get install gnome-session-fallback
```

---

### Post by renato3 on 2013-08-08
I have an EFI partition that does an EFI boot and I need to install Ubuntu in dual boot with Windows 8. Does Ubuntu Gnome support this?

---

### Post by carl4926 on 2013-08-08
> **renato3 said:**
> I have an EFI partition that does an EFI boot and I need to install Ubuntu in dual boot with Windows 8. Does Ubuntu Gnome support this?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-08-08
The desktop with Linux is separate from the underlying operating systems. So which desktop you choose does not change grub as the UEFI boot loader and the Linux kernel to support it. Since UEFI is changing a lot or has many fixes by grub, Linux & vendors on UEFI on system best to have updated UEFI and use newer version of Ubuntu.

I use fallback or gnome-panel with 12.04, but have an older system only with BIOS.

 Ubuntu 13.04 Desktop Comparison: 6 Desktops, 5 Driver/GPU Combinations
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)

Desktop includes the gui and basic functions like a file browser. The full environment with Ubuntu is all the applications for a full system. Each is different. The standard Ubuntu ISO is the base system and gnome with Unity.
      
 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)


 Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

---

### Post by prodigy_ on 2013-08-09
> **renato3 said:**
> Can I remove it after installation and install another desktop environment like Gnome Shell or Mate without harming the system?
Yes, you can. There HOWTOs for both Gnome and MATE. Examples:
Gnome 3: [http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/](http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/)
MATE: [http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-mate-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-mate-desktop)

---

### Post by renato3 on 2013-08-09
Thank you very much, guys! I'll do some readings. Thanks a lot!

---

### Post by monkeybrain20122 on 2013-08-09
Instead of removing an existing desktop why don't you just install a *buntu flavour you like (gnome-edition, Kubuntu, xubuntu lubuntu)? It would be a lot simplier and you don't risk inconsistencies.

---

### Post by Chris of Arabia on 2013-08-09
Whilst it may not apply in your case, there's no reason why you can't install a desktop over a server install either. I'm running the KDE on my 64-bit 13.04 install and that works just fine. Whilst I'm still doing a lot of things in a terminal, some things are just more comfortable to do using a GUI.

---

### Post by Netstatus on 2013-08-09
> **monkeybrain20122 said:**
> Instead of removing an existing desktop why don't you just install a *buntu flavour you like (gnome-edition, Kubuntu, xubuntu lubuntu)? It would be a lot simplier and you don't risk inconsistencies.

That's what I'd suggest, too.

---

### Post by Rob Sayer on 2013-08-09
I have had more than one desktop installed but I wouldn't recommend it.  There is definitely a possiibility for conflicts leading to hard to diagnose problems.  Like othere here I never had a problem with it but that's anecdotal and doesn't mean you wouldn't have one.
I definitely wouldn't recommend installing the linux mint mate desktop over ubuntu.  Mint mate is ubuntu based but they use a 6 month or so old kernel version.  Again, possible hard to diagnose problems.  Plus, linux mint support is *pitiful* compared to ubuntu's.  That's probably the #1 reason I use ubuntu (kubuntu actually).

If you install another desktop, I'd install the full kubuntu or whatever version (rather than just kde4 or whatever).  Then  if you settle on that you can remove unity entirely.

Actually, I think the best option is be to just download install iso's of the different desktops and just try them for yourself.  If possible I'd do it from usb stick.  It just runs a lot faster than cd/dvd.

---

