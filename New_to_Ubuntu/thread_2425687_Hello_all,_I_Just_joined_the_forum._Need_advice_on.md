---
title: "Hello all, I Just joined the forum. Need advice on Linux O/Ss"
date: 2019-08-28
forum: New to Ubuntu
---

### Post by dagmann on 2019-08-28
I would like to install 'ubuntu' along side Windows 7 Prof 64 bit.
I would like to be able to play Battlefield 4.
Ah, you ask why, well I am bored, retired and would like to mess around.

So which 'O/S' should I use for gaming and are there some installation instructions to follow?

Current computer specs:  i7-4790k, 32 GB G.Skill Sniper 1866 memory, GTX 1080ti SC, Sabertooth Z97 Mark 2 motherboard.
Also I might build a new rig which means I will most likely have to use Windows 10.

---

### Post by Autodave on 2019-08-28
Well, I always like new rigs, but your specs are quite good and you really shouldn't have much problem with gaming.  And, you certainly will not have problems with Ubuntu.

You will almost certainly use Windows for gaming since most of the major games are Windows or Mac.  You may be able to run Steam and then run Battlefield 4 in that, but I have no idea how well it would work.

I have one game that I play and I have Win10 for that.  That is the ONLY thing that I use Windows for.  It is the ONLY program installed in Win10.  I use Ubuntu (Xubuntu) for everything else.

Oldfred will probably wander in this thread soon and give you all sorts of info on how to install Ubuntu alongside Windows.

---

### Post by Autodave on 2019-08-28
I did a quick search for running BF4 on Steam and it doesn't look real promising.  It does seem possible, but there are a lot of things that must be done in order to get it to work.  Hopefully, I am wrong about that and someone else with knowledge about the game will jump in, but if it were me, I would just use Windows for that and use Ubuntu for everything else.

BTW: welcome to the forums!

---

### Post by dagmann on 2019-08-28
Thanks for the replies Autodave.
I purchased BF4 through Origin. 
So I guess running BF4 on Ubuntu is not looking good.

I do have some games from Steam such as Insurgency and Squad.
I would have to download them from Steam and install them.

I thought that it would be fun experiencing another O/S.

---

### Post by CatKiller on 2019-08-28
> **Autodave said:**
> I did a quick search for running BF4 on Steam and it doesn't look real promising.

EA don't sell their games through Steam. They have their own client: Origin. You can run it through Wine, as well as using Lutris to help out, but that's not as straightforward as simply firing up Steam and hitting play.

---

### Post by CatKiller on 2019-08-28
> **dagmann said:**
> I thought that it would be fun experiencing another O/S.

I've been gaming every day for the past thirty-something years, and I haven't used Windows for the last 14. Games that run through Steam are generally pretty straightforward; the problem areas are generally DRM, anti-cheat, and games that are flaky on Windows too.

Wine is the software that allows Windows software to run on Linux. Setting it up can be a hassle, which is why front-ends like Lutris and Steam's Proton exist.

Since you've got a Windows licence too, you can use Linux for the games that you're interested in making work on Linux and switch to Windows for the others. At least until Windows 7 hits its final End of Life at the beginning of next year.

---

### Post by Frogs Hair on 2019-08-28
Win 7 is EOL January 13, 2020 and If you aren't upgrading to Win 10 you have some time to experiment with games and Linux in general. I dual boot with Win 10 for reasons  that include gaming.There is some software I can't run in wine or crossover. My computers were upgraded to Win 10 during the free upgrade  period and then I reinstalled windows 7 until this summer. I then installed a much better version of Win 10 free of charge due to my device data being stored on the MS servers.

---

### Post by oldfred on 2019-08-28
That is an UEFI system, but most Windows 7 installs were/are BIOS with MBR partitioning.
You can only have Windows in BIOS mode on MBR(msdos) or UEFI with gpt partitioning. And then if on same drive Ubuntu must be installed in same boot mode and should be in same boot mode even if on another drive.
But since UEFI system, you may want to upgrade to Windows 10 and install in UEFI boot mode. 
For both Windows & Ubuntu how you boot install media UEFI or BIOS is then how it installs.
Post this from Ubuntu live installer in live mode & its terminal:
sudo parted -l

If interested in UEFI, many links in the link in my signature.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by dagmann on 2019-08-29
As of right now, to simplify this experience, I plan to use a formatted Samsung 500GB SSD drive for the Ubuntu installation, and no other drives except of course an HP DVD.
I would like to install and use the Firefox browser.

I downloaded the following software files. I hope that they are correct.
PowerISO7-x64,  NVIDIA-Linux-x86_64-430.40,  ubuntu-18.04.3-desktop-amd64

I found on Youtube some videos on how to install Ubuntu from a USB drive. I'll give that a try.

I appreciate everyones input. I'll be back!

---

### Post by Autodave on 2019-08-29
Do not do it that way.  Burn the ubuntu.iso file to a USB stick or DVD and install on the 500G SSD drive.  Once installed, go to Settings -> Additional Drivers and make sure that the most current Nvidia driver is installed.

You want to install 99.9% of your software through the repositories: not downloaded from some site.  Please remember: Linux is NOT Windows!  It is very different from what you are used to.

---

### Post by CatKiller on 2019-08-29
> **dagmann said:**
> As of right now, to simplify this experience, I plan to use a formatted Samsung 500GB SSD drive for the Ubuntu installation, and no other drives except of course an HP DVD.
I would like to install and use the Firefox browser.

I downloaded the following software files. I hope that they are correct.
PowerISO7-x64,  NVIDIA-Linux-x86_64-430.40,  ubuntu-18.04.3-desktop-amd64

I found on Youtube some videos on how to install Ubuntu from a USB drive. I'll give that a try.

I appreciate everyones input. I'll be back!

Firefox is already installed by default.

Don't use the file that you downloaded from Nvidia's site. In fact, don't download any software from websites for use in Ubuntu. Ubuntu uses software packages, which you install using a package manager, and they're automatically configured and updated. The Software Centre is the user-friendly way of installing software, or you can install Synaptic if you want more insight and control over what's actually happening. The drivers for most things are already part of the kernel and proprietary software - like the Nvidia driver - can be installed using normal package management.

---

### Post by Autodave on 2019-08-29
The driver installation disks that you get with Windows programs and hardware are called cup holders here. Put your coffee mug or cold drink on it.

---

### Post by dagmann on 2019-08-29
Many thanks to all. Yup, I am learning a little about Ubuntu. I have a bootable/installation USB ready to go. Just gotta get the nerve to use it, lol.

---

### Post by CatKiller on 2019-08-29
> **dagmann said:**
> I have a bootable/installation USB ready to go. Just gotta get the nerve to use it, lol.

You don't have to install it on the first go. The install disk is fully-functional without installing anything at all. You can just play around with it without affecting anything else on your computer till you're comfortable. Any changes to the Ubuntu part won't be saved, either: the install image is read-only.

Since you're using Nvidia graphics, there's a reasonable chance that you'll boot into a black screen - perhaps with a flashing cursor. If that happens, at the screen where it says "Try Ubuntu" press E to edit the startup options, find where it says "quiet splash" and change that to "quiet splash nomodeset". It's an Nvidia-specific problem, but it doesn't affect everyone. If you make that change you may find that the resolution is lower than you'd want, but it's fine for just playing around and fine for doing the install. When you've done the install and installed the proprietary driver you won't need it any more. The Nvidia driver has some special sauce for setting the resolution, and they won't share it.

---

### Post by dagmann on 2019-08-29
I just tried Ubuntu's 'try' to see how it runs. It was very fast. Firefox works very well. I was quite surprised.

I do have a question about the installation.
I have a Samsung 500 GB SSD that is empty and formatted. Can I install on that drive?
Can I assume that I could boot into Ubuntu by using the USB and go to that drive?

I could remove the USB and reset the bios to boot up in Windows if needed.

BUT when in Windows would that O/S damage the SSD that contains Ubuntu?

---

### Post by CatKiller on 2019-08-29
It depends.

After you've done the install you won't need to keep the install image inserted, and having it inserted won't help you.

If you're using BIOS then a different bootloader can go in the Master Boot Record of each drive and your drives can be completely independent of each other, and you can select which drive you boot from using just the BIOS. That's not the default, but you can do it. Otherwise, Grub would be the bootloader, and would chainload the Windows bootloader, so you'd pick which OS you wanted to boot from using Grub's menu.

I'm hazy on what happens if you're using UEFI, since I stopped using Windows long before I started using UEFI. But *I think* that all the bootloader stuff has to go in one EFI System Partition, so you can't have independent discs in the same way.

Whether you use BIOS or UEFI depends on how your Windows install is set up. If it's already BIOS you'll want to stay with BIOS, and if it's UEFI you'll want to stay with UEFI. You can't mix-and-match easily. You'll also want to pay attention to how you're booting your install image: if you boot it in BIOS mode it will install in BIOS mode; if you boot it in UEFI mode it will install in UEFI mode.

For the most part I think Windows will simply ignore your Ubuntu partitions. Obviously if it says, "I've found some non-NTFS partitions, would you like me to nuke them?" don't say yes.

---

### Post by dagmann on 2019-08-30
Is there a recommended VPN and Antivirus to use with Ubuntu?

I found this VPN list. Is anyone using any of these? If so how is it speed wise?

[https://www.pcmag.com/roundup/361826/the-best-vpn-apps-for-linux](https://www.pcmag.com/roundup/361826/the-best-vpn-apps-for-linux)

---

### Post by him610 on 2019-09-01
You probably have no worry about antivirus programs; as for VPN, there is at least one in the repositories.
```

 apt show openvpn
Package: openvpn
Version: 2.4.7-1ubuntu1
Priority: optional
Section: net
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bernhard Schmidt <berni@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,171 kB
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.15), liblz4-1 (>= 0.0~r130), liblzo2-2, libpam0g (>= 0.99.7.1), libpkcs11-helper1 (>= 1.11), libssl1.1 (>= 1.1.1), libsystemd0, iproute2, lsb-base (>= 3.0-6)
Suggests: openssl, resolvconf, openvpn-systemd-resolved, easy-rsa
Homepage: https://openvpn.net/
Task: ubuntu-desktop-minimal, ubuntu-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Supported: 9m
Download-Size: 477 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu eoan/main amd64 Packages
Description: virtual private network daemon
 OpenVPN is an application to securely tunnel IP networks over a
 single UDP or TCP port. It can be used to access remote sites, make
 secure point-to-point connections, enhance wireless security, etc.
 .
 OpenVPN uses all of the encryption, authentication, and certification
 features provided by the OpenSSL library (any cipher, key size, or
 HMAC digest).
 .
 OpenVPN may use static, pre-shared keys or TLS-based dynamic key exchange. It
 also supports VPNs with dynamic endpoints (DHCP or dial-up clients), tunnels
 over NAT or connection-oriented stateful firewalls (such as Linux's iptables).

```

TheFu is absent tonight, but he will probably have some good advice to share about VPN.

---

### Post by oldos2er on 2019-09-02
Regarding antivirus, see [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

### Post by dagmann on 2019-09-09
Well Ubuntu is install along with some other software.
Just to let ya'll know, the SSD I used for Ubuntu does not show up in Windows 7.
However the revers is true.
I am not using a dual-boot scenario, I use Grub2Win. Tacky but it works.

I have not been able to install Wine, I keep getting some kind of package error.
I follow instructions from two website, still no joy.

Isn't there a simple way to install Wine from the repository?

---

### Post by Autodave on 2019-09-09
Yes....and that is the preferred way!  Go to the Software center and search for "wine".  When you find it, click to install.

---

### Post by SeijiSensei on 2019-09-09
Some programs like Lutris prefer that you use [wine-staging]("https://wiki.winehq.org/Wine-Staging").

---

