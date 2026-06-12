---
title: "Video Problem HP 820 G1 Distro Debian"
date: 2019-04-11
forum: New to Ubuntu
---

### Post by halj82 on 2019-04-11
Hi everyone,


I am writing to help me solve a problem with my HP820 G1 laptop.


After a few hours of using my laptop, the artifact images are displayed. This happens only with Debian-derived Linux distro, while with Windows or Opensuse the laptop works.


I tried searching the system logs but couldn't find anything.


On the internet I found a post from a guy who has the same problem as me but no one answers him (I try to write to HP without being answered)
[https://h30434.www3.hp.com/t5/Notebook-Video-Display-and-Touch/820-g1-Ubuntu-Screen-artifacts/td-p/7029819](https://h30434.www3.hp.com/t5/Notebook-Video-Display-and-Touch/820-g1-Ubuntu-Screen-artifacts/td-p/7029819)

Thanks for the reply.

---

### Post by deadflowr on 2019-04-11
What Debian derived distribution, specifically?

---

### Post by halj82 on 2019-04-11
Thanks for reply deadflowr,

I had the problem using Linux Mint, Ubuntu 18.10, Kali linux and Parrot Os.

I am currently using opensuse without problems but I would like to install and use a debian based distro.

---

### Post by halj82 on 2019-04-12
Help me please

---

### Post by oldrocker99 on 2019-04-12
Here's something directly from debian.org:
[https://wiki.debian.org/InstallingDebianOn/HP/EliteBook%20820%20G1](https://wiki.debian.org/InstallingDebianOn/HP/EliteBook%20820%20G1).

I hope it helps.

---

### Post by halj82 on 2019-04-15
Hello oldrocker99,

I had already read this guide, but I could not understand what it says about the "screen mode" item (I inserted in brackets what I didn't understand):
~ / bin / watcher_acpi.sh (Do I need to create the script whatchare_acpi.sh script on this path?)

socket = / var / run / acpid.socket

nc -U "$ {socket}" | while read event
do
     case "$ {event}" in
         Video / switchmode *)
             ~ / bin / monitor_switch.sh (This script does not exist ... should I create it? What should I put in it?)
             ;;
     esac
done

---

### Post by NM5TF on 2019-04-15
> **halj82 said:**
> Thanks for reply deadflowr,

I had the problem using Linux Mint, Ubuntu 18.10, Kali linux and Parrot Os.

I am currently using opensuse without problems but [COLOR="#FF0000"]I would like to install and use a debian based distro.[/COLOR]

you might take a look at MX 18.2 Continuum Linux....based on Debian9 stable....

go here  [https://mxlinux.org/](https://mxlinux.org/)

tommy

---

### Post by halj82 on 2019-04-16
yes, I installed this distribution but the problem reappears. Perhaps the best solution is to install Red Hat based distro as open suse or fedora.:cry:

---

### Post by NM5TF on 2019-04-16
I have used both of those distros....Fedora is the development distro for RH....very similar to a Debian system....

openSUSE is geared more towards computer nerds that like to tinker..

whatever distro works for you

is this your 1st foray into the *NIX world ???

tommy

---

### Post by oldrocker99 on 2019-04-17
The biggest difference between different distros is the way that software is installed; Debian-based systems use apt, Fedora-based systems use yum, Arch-based systems use pacman. Aside from that, there are little differences between distro types.

---

### Post by mastablasta on 2019-04-18
Some HPs are SUSE EL certified and even came SUSE EL preloaded, so i am not surprised that OpenSUSE would work well on it. OpenSUSE is not based on redhat. They are using [FONT=arial]ZYpp package manager (via YaST).[/FONT]

However many HPs (at least used to be) certified for Ubuntu as well. So it is a bit strange things are not working for you. hard to say what is wrong from the data posted. perhaps you need to dig through logs.

in any case i woul duse what works best on the hardware. OpenSUSE is a good solid distro, especially for desktops.

---

### Post by halj82 on 2019-04-30
Nobody has a solution for my problem?

---

