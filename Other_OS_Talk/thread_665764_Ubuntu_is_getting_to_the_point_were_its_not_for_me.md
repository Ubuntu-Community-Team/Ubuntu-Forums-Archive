---
title: "Ubuntu is getting to the point were its not for me any more..."
date: 2008-01-12
forum: Other OS Talk
---

### Post by Drakx on 2008-01-12
Hello people

I need some advice, while I've always loved how ubuntu is in terms it sees and uses every piece of hardware my laptop has I feel its getting/gotten bloated some what! now I'm looking for a slim, fast distro that has support and I don't want to mess around with ipw3945. This is one of the main reasons ive stuck to ubuntu like glue because i just click the network-manger and connect to which ever network i want.

Reasons I dont like ubuntu are it seems really heavy like windows vista heavy it comes with open office which i dont want or use (if i remove that half of ubuntu is gone with it (well gnome) and some other apps that i never use)

Reasons I love ubuntu every thing works!

So I'm looking for suggestions of a distro that is fast dont come with oo.org and my wlan card works out of the box like it does with ubuntu!

btw please don't suggest xubuntu as i really don't like XFCE

Thanks.

---

### Post by CM Xtasy on 2008-01-12
Wait for Linux Mint E17?

---

### Post by Drakx on 2008-01-12
Hmm ive taken a look at Linux Mint and im not impressed at all plus i wanna stick with gnome I just don't want OO.org and some other things that come with ubuntu like ive already said try take it out of ubuntu and gnome is gone :(

---

### Post by ajgreeny on 2008-01-12
You can remove open office and although it will remove **ubuntu-desktop**, it doesn't remove gnome, in spite of how it seems.  **ubuntu-desktop** is just a meta-package that makes sure that if you install it overtop a server installation, for example, you end up with all the packages of ubuntu gnome desktop without having to specify all of them separately.  **Ubuntu-desktop** can be removed and you will still have the gnome desktop left.  The loss of **ubuntu-desktop** may make a difference if you try to do an online version upgrade to 8.04, for example, but otherwise it will make no real difference to your system.

---

### Post by mikewhatever on 2008-01-12
Why not install CLI from mini-iso? What you get is the bare bones of Ubuntu including drivers, but no programs at all. After that you can add whatever you want, and that baby should be rocket fast and very slim. Here is a good guide to follow [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal). The guide is a bit outdated, but it should not be too hard to figure things out. I had to substitute 'server' for 'cli'. Be aware, it you simply hit enter, the installer will download and install full ubuntu-desktop.

---

### Post by Antman on 2008-01-12
> **mikewhatever said:**
> Why not install CLI from mini-iso? What you get is the bare bones of Ubuntu including drivers, but no programs at all. After that you can add whatever you want, and that baby should be rocket fast and very slim. Here is a good guide to follow [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal). The guide is a bit outdated, but it should not be too hard to figure things out. I had to substitute 'server' for 'cli'. Be aware, it you simply hit enter, the installer will download and install full ubuntu-desktop.

+1 
If you like the hardware detection of Ubuntu, Just start minimal and build from there.

---

### Post by mips on 2008-01-12
Arch maybe?

---

### Post by Dark Hornet on 2008-01-12
I have been playing around with Fluxbox recently...and I have to say, its pretty nice.  I am pretty sure there is a much easier setup called "Fluxbuntu" that comes with a light office app, etc.

---

### Post by mthei on 2008-01-12
> **ajgreeny said:**
> You can remove open office and although it will remove **ubuntu-desktop**, it doesn't remove gnome, in spite of how it seems.  **ubuntu-desktop** is just a meta-package that makes sure that if you install it overtop a server installation, for example, you end up with all the packages of ubuntu gnome desktop without having to specify all of them separately.  **Ubuntu-desktop** can be removed and you will still have the gnome desktop left.  The loss of **ubuntu-desktop** may make a difference if you try to do an online version upgrade to 8.04, for example, but otherwise it will make no real difference to your system.

Removing OpenOffice.org no longer removes the ubuntu-desktop package, and has been that way since at least Feisty.

---

### Post by LinuxGuy1234 on 2008-01-12
> **Drakx said:**
> Hello people

I need some advice, while I've always loved how ubuntu is in terms it sees and uses every piece of hardware my laptop has I feel its getting/gotten bloated some what! now I'm looking for a slim, fast distro that has support and I don't want to mess around with ipw3945. This is one of the main reasons ive stuck to ubuntu like glue because i just click the network-manger and connect to which ever network i want.

Reasons I dont like ubuntu are it seems really heavy like windows vista heavy it comes with open office which i dont want or use (if i remove that half of ubuntu is gone with it (well gnome) and some other apps that i never use)

Reasons I love ubuntu every thing works!

So I'm looking for suggestions of a distro that is fast dont come with oo.org and my wlan card works out of the box like it does with ubuntu!

btw please don't suggest xubuntu as i really don't like XFCE

Thanks.

```
sudo apt-get --purge remove openoffice.org && sudo apt-get install abiword abiword-gtk
```
should:
* uninstall OpenOffice.org
* install AbiWord

---

### Post by jrusso2 on 2008-01-12
Get a distro where you can choose what to install like Fedora.

---

### Post by Drakx on 2008-01-12
Thanks for the suggestions, but I dont want any office tools at all when i need them ill install then :D, as for arch ive looked it's not really what im looking for! though funny enough I like gentoo but again its not as good for detecting making sure every thing works like ubuntu does!, as for Fedora... well what can i say... its about as much use as a chocolate fireguard for me! yes ive also used that too *my ideal distro would be gentoo's speed and ubuntus user friendlyness and hardware detection*

what about totuem and rythumbox etc etc i never use them this is what i meant about if i remove them it removes gnome! and KDE well.... IMO thats a joke 6 tools todo one thing? id rather use one tool todo the job (sorry KDE lovers), though the new KDE does look fine!.

---

### Post by Tenken on 2008-01-12
You could try the minimal install CD and install just the [gnome core]("http://packages.ubuntu.com/feisty/gnome/gnome-core") components.

```
sudo apt-get install gnome-core
```

---

### Post by mikewhatever on 2008-01-12
Other distros aside, I think Ubuntu is very customisable. You can try removing anything you want, and getting rid of ubuntu-desktop package is no always a problem. Use a terminal for uninstalling and watch out. If you see that a lot (hundred+) of packages are going to be uninstalled and several hundreds mega freed, don't do it.

---

### Post by mips on 2008-01-13
> **Drakx said:**
> 
what about totuem and rythumbox etc etc i never use them this is what i meant about if i remove them it removes gnome! and KDE well.... IMO thats a joke 6 tools todo one thing? id rather use one tool todo the job (sorry KDE lovers), though the new KDE does look fine!.

I know you said arch is not for you but maybe you should have a look at KDEmod, there is also a KDEmod4 out. kdemod is very modular, you only install what you need and this leaves you with a very lean & light install.

Btw. What are the issues with arch for you?

---

### Post by Drakx on 2008-01-13
Hi Mips

Thanks for the reply! not a lot really though I could never get the ipw3945 driver to work. I suppose if I give it another try it would not be so bad? it has been at least 24months since i last looked at arch.

---

### Post by K.Mandla on 2008-01-13
> **Drakx said:**
> I feel its getting/gotten bloated some what! now I'm looking for a slim, fast distro . ...
> **Drakx said:**
> i wanna stick with gnome. ...
Not to be nitpicky, but aren't you contradicting yourself? ;)

Seriously though, if you want Ubuntu's perks, but don't want the weight attached, start with a minimal installation, add the core Gnome structure and then the few software packages you want. Isn't that the best of both worlds?

But really, if you want to get away from the bloat, I would suggest getting away from Gnome. :???: I felt much better about life when I did.

---

### Post by mips on 2008-01-13
> **Drakx said:**
> Hi Mips

Thanks for the reply! not a lot really though I could never get the ipw3945 driver to work. I suppose if I give it another try it would not be so bad? it has been at least 24months since i last looked at arch.


I honestly can't comment on the ipw3945 as I don't have one. The installation instructions for the ipw3945 is on their wiki page though. 24months is a pretty long time in the linux world where things move at a hectic pace ;)

---

### Post by climatewarrior on 2008-01-13
What about elbuntu? [https://wiki.ubuntu.com/Ebuntu](https://wiki.ubuntu.com/Ebuntu) or what about installing an ubuntu commandline system and building your way up from there with what you need?

---

### Post by Antman on 2008-01-13
> **Drakx said:**
> Hi Mips

Thanks for the reply! not a lot really though I could never get the ipw3945 driver to work. I suppose if I give it another try it would not be so bad? it has been at least 24months since i last looked at arch.

Arch works fine with the ipw3945 now. When I tried Arch, I just followed the Wiki step-by-step and everything worked.

---

### Post by Drakx on 2008-01-13
Im not saying it don't but at the time of me using Arch i could not get it work, though i do intend of giving it ago again.

---

### Post by Drakx on 2008-01-13
edit deleted double post

---

### Post by wolfen69 on 2008-01-13
wow. ubuntu is heavy? do you have 256mb ram?i have ubuntu base install with fluxbox running on 64mb of ram. you must be doing something wrong or im good.

---

### Post by Drakx on 2008-01-13
neither ;) any way I've got arch installed and this is more like the kinda speed i was talking about

Thanks guys!

---

### Post by Antman on 2008-01-13
> **Drakx said:**
> neither ;) any way I've got arch installed and this is more like the kinda speed i was talking about

Thanks guys!

Yeah, Arch rocks...

---

### Post by Drakx on 2008-01-14
Well its intersting to say the least :) just a few tweaks and im done with customizing Arch, I learnt a few tricks too

---

### Post by eljoeb on 2008-01-15
> **wolfen69 said:**
> wow. ubuntu is heavy? do you have 256mb ram?i have ubuntu base install with fluxbox running on 64mb of ram. you must be doing something wrong or im good.

Ubuntu is heavy, at least compared with other distros.

---

