---
title: "Super light, fast booting OS with VERY lightweight wm?"
date: 2008-11-14
forum: Other OS Talk
---

### Post by blazemore on 2008-11-14
I use XP for heavy stuff like image editing and gaming.
I tend to live most of my life in Firefox however, as most of my apps are online.
At the moment I'm using Xubuntu, which is very lightweight. But I want to know:
is there a reeeeally lightweight *box distro which will run basic networking and Firefox, and maybe IM and a music player? I don't need Compiz or anything like that.
And I'd like Deb based if possible.

Can anyone reccomend anything?

---

### Post by Liviu-Theodor on 2008-11-14
I don't know for all what they are based on, neither their exact capabilities, but lightweight distros I know of are: Damn Small Linux, Feather Linux, Puppy Linux, Fluxbuntu.

---

### Post by blazemore on 2008-11-14
Fluxbuntu!? Is this officially supported?

---

### Post by markg48 on 2008-11-14
try some of the ubuntu flavours theres distro for most hardware

---

### Post by kerry_s on 2008-11-14
fast booting is tricky, i would look at the distro's that have the -toram option, they will be the fastest you can get once loaded.
size matters when it comes to speed, start from the smallest and work your way up.

by size?
slittaz
dsl
puppy
crunchbang
etc...

---

### Post by alwayshere on 2008-11-14
damm small linux is about 50mb in size

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by chucky chuckaluck on 2008-11-14
arch is fast and can be fast booting (mine boots in 18sec.). you only install what you need.

---

### Post by mips on 2008-11-14
> **blazemore said:**
> But I want to know:
is there a reeeeally lightweight *box distro which will run basic networking and Firefox, and maybe IM and a music player? I don't need Compiz or anything like that.
And I'd like Deb based if possible.

Can anyone reccomend anything?

Install Arch + X11 + ALSA + Openbox + Firefox + IM + player and you will have a very lightweight system. It will only have the apps you installed and not all the extra crap you don't need.

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

It's actually easy and most people are pleasantly suprised how easy it was in retrospect. The above document might seem long but if you only look at the parts you need there are not that many commands or editing.

Arch really is a beautifull and addictive distro.

---

### Post by Grant A. on 2008-11-14
> **mips said:**
> Install Arch + X11 + ALSA + Openbox + Firefox + IM + player and you will have a very lightweight system. It will only have the apps you installed and not all the extra crap you don't need.

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

It's actually easy and most people are pleasantly suprised how easy it was in retrospect. The above document might seem long but if you only look at the parts you need there are not that many commands or editing.

Arch really is a beautifull and addictive distro.

Actually, it may be a good idea to install fluxbox if you want a super light wm, it is only 966kb. Or, you could install xmonad/wmii, both are very light wms.

---

### Post by mips on 2008-11-14
> **Grant A. said:**
> Actually, it may be a good idea to install fluxbox if you want a super light wm, it is only 966kb. Or, you could install xmonad/wmii, both are very light wms.

Correct but it depends on the OP. Only reason I suggested Openbox was the config utilities it has.

---

### Post by K.Mandla on 2008-11-14
[Machboot]("http://www.machboot.com").

---

### Post by kelvin spratt on 2008-11-14
I'd also go for Arch as it supports all hardware + you get to learn Linux along the way also the file system makes more sense than Debian.

---

### Post by mips on 2008-11-14
> **K.Mandla said:**
> [Machboot]("http://www.machboot.com").

K.Mandla,

Have you tried this yet?

Will it work for a normal HD install as well?

IS there a howto on doing this for other distros?

Thx

---

### Post by basenvironment on 2008-11-14
debian

---

### Post by chucky chuckaluck on 2008-11-14
> **Grant A. said:**
> Actually, it may be a good idea to install fluxbox if you want a super light wm, it is only 966kb. Or, you could install xmonad/wmii, both are very light wms.

because of the haskell dependencies, xmonad is a giant blob of an installation. dwm is about a fifth the size of wmii and, imltho, the fastest of all wm's.

---

### Post by snowpine on 2008-11-14
> **blazemore said:**
> I use XP for heavy stuff like image editing and gaming.
I tend to live most of my life in Firefox however, as most of my apps are online.
At the moment I'm using Xubuntu, which is very lightweight. But I want to know:
is there a reeeeally lightweight *box distro which will run basic networking and Firefox, and maybe IM and a music player? I don't need Compiz or anything like that.
And I'd like Deb based if possible.

Can anyone reccomend anything?

Hi there Blazemore, here are my suggestions: 

1) Speed up your existing Xubuntu install with a faster windows manager (I like Openbox personally).
2) SliTaz. The entire distro is under 30mb and it includes a recent version of Firefox.
3) Minimal install of Debian Lenny, then install LXDE. 

Those are the options I can vouch for personally. I think Arch is a good suggestion too, but I haven't got around to trying it yet.

---

### Post by snowpine on 2008-11-14
> **blazemore said:**
> Fluxbuntu!? Is this officially supported?

The Fluxbuntu project has been dormant for over a year; it's a pre-release candidate based on 7.10 Gutsy Gibbon. Fluxbuntu was cool for its time, but IMO it has since been surpassed by other lightweight Debian-based distros (CrunchBang is an awesome 8.04+Openbox distro; Debian Lenny minimal install+LXDE is super-light; Sidux Lite is a new favorite of mine and it has LXDE and Fluxbox options). 

None of the Debian distros are as lightweight as Puppy, DSL, SliTaz, etc.

---

### Post by simtaalo on 2008-11-14
checkout this article
[http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

---

### Post by mikjp on 2008-11-14
> **blazemore said:**
> And I'd like Deb based if possible.

Can anyone reccomend anything?

Yes. Debian + Openbox.

Mikko

---

### Post by K.Mandla on 2008-11-14
> **mips said:**
> Have you tried this yet?
Yes, and the speed is unbelievable. :shock:
> **mips said:**
> Will it work for a normal HD install as well?
It should; I messed with it for a little while but it's hard-wired to work off the CD (or at least it was, about a year ago when I first tried it). You might be able to get it to boot off an ISO file via Grub, if you play with it.
> **mips said:**
> IS there a howto on doing this for other distros?
Not that I'm aware of. If you find one, let me know.

I'm still looking around for a howto or some details on that five-second boot on an eeePC.

---

### Post by cardinals_fan on 2008-11-14
It has LXDE or JWM, but SliTaz is a fabulous light distro.  Otherwise, install a more minimal distro (Arch, Ubuntu minimal, etc.) and install your own WM.

---

### Post by nitehawk777 on 2008-11-14
I also have been thinking along that same line,....
I got Xfce downloaded and working in Linux Mint,...(as nice as Xubuntu,...but with the multimedia codecs already added in the install).

I have been using Puppy Linux 4.1 mostly.  It comes with the  JWM ("Joe's Window Manager"),...and is still somewhat based on Slackware (but has it's own "pet" packages).  It's very fast,..and pretty complete in the way of installed applications (suits me).  It's very lightweight,..quick,...and IMO easy to configure. (But that is just me,...someone else may think different).
You can download the latest Firefox,...music players etc. etc.  

I've also been wanting to try Zenwalk Linux,...which is also based on Slackware,...but has a package manaqer a little like Deb and Ubuntu's Synaptic (good,..but not quite as advanced yet).  Zenwalk uses the Xfce WM like Xubuntu does,.....but they say it's more "integrated" with the distro itself.

Vector Linux also uses the Xfce desktop,...but I had trouble with it the time I tried it.  And there really wasn't a package manager at all (used Slackware's "get-slapt"...which means it took FOREVER for my older computer to try and download and compile software!!!!)

So I'd probably suggest what you have (Xubuntu)(change the WM)
Puppy Linux
Zenwalk
Elive.... (haven't tried it,...but it's based on Debian,..and has the Enlightenment WM).  Sounds nice.

---

### Post by cardinals_fan on 2008-11-14
> **nitehawk777 said:**
> 
Vector Linux also uses the Xfce desktop,...but I had trouble with it the time I tried it.  And there really wasn't a package manager at all (used Slackware's "get-slapt"...which means it took FOREVER for my older computer to try and download and compile software!!!!)

Eh?  Vector uses slapt-get, and there is no compiling required.  If it was slow, either the mirrors were slow or something was wrong with your connection.

---

### Post by chris4585 on 2008-11-14
[plusone base]("http://boxbuntu.com/") with firefox and menu installed?

:-\"

---

### Post by Sorivenul on 2008-11-15
Have to echo the SliTaz sentiment here.  If that's not enough, Debian netinstall +WM of your choice (I suggest Openbox or Ion2).

---

### Post by gjoellee on 2008-11-15
If you want many features I would recommend:
-TinyME
-Fluxbuntu
-Linux Mint XFCE
-Linux Mint Fluxbox
-wattOS

---

### Post by walkerk on 2008-11-15
Minimal install with the Intrepid mini.iso. Install the basics + whatever you want. 

My setup
```
sudo apt-get install xorg pekwm menu xterm gdm gksu synaptic firefox thunderbird gedit
```

---

### Post by chris4585 on 2008-11-15
> **walkerk said:**
> Minimal install with the Intrepid mini.iso. Install the basics + whatever you want. 

My setup
```
sudo apt-get install xorg pekwm menu xterm gdm gksu synaptic firefox thunderbird gedit
```

Plusone Base makes getting what you suggested a little easier, because it is a LiveCD.

Plusone Base very minimal, with xorg and openbox, from there just install whatever

---

