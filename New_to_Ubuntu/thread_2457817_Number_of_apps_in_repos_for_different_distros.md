---
title: "Number of apps in repos for different distros"
date: 2021-02-10
forum: New to Ubuntu
---

### Post by Advait on 2021-02-10
I've been away from Linux for a long time, but I'm thinking of adding Ubuntu to my next laptop. I know the Ubuntu Software Center offers access to download lots of apps. Do the 'Software Centers' in other popular distros like MXLinux, Elementary OS, or Zorian offer access to an equally large number of apps? Or is the Ubuntu Software Center unique in that it offers access to download more apps than in other distros?

I'm referring to distros that would be popular for Linux beginners.

(I'm not talking about the apps that come bundled with Ubuntu or other distros.)

I hope my question is clear. Thx.

PS: Can the Ubuntu Software Center be installed on other non-Ubuntu distros?

PPS: Also forgot to mention that I definitely won't be compiling any software myself. Have never done it and don't have the time to learn.
.
.

---

### Post by mastablasta on 2021-02-10
software center is basically GUI for apt (or apt-get). these pull down precompliled applications from servers
all opensource applications with linux version can be run on any distro, but you might need to compile them yourself. what you talk about is the precompiled applications. Ubuntu has a large collection of those available on their servers. another advantage is that a larger number of PPA which are precompiled libraries that people offered. then there are also debs and snaps available and also large number of binaries that will work out of the box on Ubuntu (and some other large distros). snaps and flatpack can work on any distro. debs can be translated to rpm using alien.

additionally if application is closed source it has a larger chance of working out of the box (being pre-compiled) on larger distro (like Ubuntu, Debian, RedHat/CentOS/AlmaLinux, SuseEL/OpenSUSE or similar).

so the real advantage is actually ease of use and install, not that you can't install those same applications elsewhere or that you are somehow limited by choosing certain distro.

If it's opensource - yes you can install it elsewhere. just make from source and dela with any bugs that might show up (or not).

to me and for now, Kubuntu offers everything i need. it really developed well in last 8 years. Wine and Valve's Proton work made me stick with Linux and finally i was able to replace windows for 95% of things. i think when i can get a new machine i will just stick windows to VM for some occasional use. Opensource stuff is many times far from commercial, but it has been a pleasure looking at how they are slowly (really slow) but steadily closing the gap. 

For beginners that move over from Windows i would say Mint or Kubuntu (Xubuntu on older machine). Or if they want to use a different desktop Ubuntu and Ubuntu/Mint Mate is where i would point them to.

---

### Post by linuxyogi on 2021-02-10
In my experience Debian & Debian based distros enjoy the largest repositories.
Mint is based on Ubuntu & Ubuntu is based on Debian so ultimately the amount of apps which each hold is almost the same.
Now, suppose you install Ubuntu or Mint & you want to install Spotify or Ksnip then you have to install them as snaps. These 2 apps are not in the repos.

On the other hand if you use Arch or an Arch based distro like [EndeavourOS]("https://endeavouros.com/") you get access to a community maintained source called AUR. Under Arch if something is not available in the main repos its almost certain that AUR will provide you that app. In short if you combine the main Arch repos & AUR its simply huge.

But one can argue that Arch is not for beginners.

---

### Post by cmcanulty on 2021-02-10
yes all ubuntu derivatives ie lubuntu xubuntu etc have available all the ubuntu apps

---

### Post by Advait on 2021-02-11
Thanks. This answers my question. The universe of precompiled ready-to-install-and-run Linux apps is available to most popular distros, but Ubuntu makes it easy to search, do discovery and find, download and install the apps I want. Also it helps me to know that the Software Center is a gui for apt-get. Thx.

---

### Post by Advait on 2021-02-11
Thanks for the info. More evidence for me (as a relative beginner) to go with Ubuntu. 

In regards to Arch, I'm pretty much a beginner, so I want to avoid getting a new hobby in addition to getting a distro.

---

### Post by Advait on 2021-02-11
Thx. I'm learning toward Xubuntu or Lubuntu.

---

### Post by cmcanulty on 2021-02-11
for the maximum number of included apps available enable universe AND multiverse repositories

---

### Post by Advait on 2021-02-11
> **cmcanulty said:**
> for the maximum number of included apps available enable universe AND multiverse repositories

Ahh... great tip for a newbie like me. Thx! Will do.

---

### Post by CatKiller on 2021-02-11
> **Advait said:**
> Ahh... great tip for a newbie like me. Thx! Will do.
Just so that you're aware of what that means, 

> The four main repositories are:
[list][*]Main - Canonical-supported free and open-source software.
[*]Universe - Community-maintained free and open-source software.
[*]Restricted - Proprietary drivers for devices.
[*]Multiverse - Software restricted by copyright or legal issues.[/list]
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Advait on 2021-02-11
> **CatKiller said:**
> Just so that you're aware of what that means, [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

:cool: Thx!

---

