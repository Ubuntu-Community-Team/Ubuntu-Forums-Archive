---
title: "Fastest installing OS w/ A GUI"
date: 2007-05-09
forum: Other OS Talk
---

### Post by goumples on 2007-05-09
Hey folks.  I have an exam tomorrow in hardware/software support.  The exam is essentially take a box of parts, build a computer, slap an OS on it, boot it up to show that it works, and go home.. So I figure for the exam I'll carry a small Linux distro (but that still has a gui) that installs very quickly, thus taking less time, and go the hell out of there as fast as possible. 

Any suggestions?

---

### Post by RAV TUX on 2007-05-09
> **goumples said:**
> Hey folks.  I have an exam tomorrow in hardware/software support.  The exam is essentially take a box of parts, build a computer, slap an OS on it, boot it up to show that it works, and go home.. So I figure for the exam I'll carry a small Linux distro (but that still has a gui) that installs very quickly, thus taking less time, and go the hell out of there as fast as possible. 

Any suggestions?

**[[B][B]Wolvix**[/B]]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwolvix.org%2F&ei=Nn1CRs7CDaX-gQLfyo2WAg&usg=AFrqEzc3DXdN63-gNuf_i1vmZPNEcjRCAQ&sig2=SZ8J6zRgpZpTsapaODC2Dw")[/B]

---

### Post by Nikron on 2007-05-09
Does it realllly need a GUI?

---

### Post by goumples on 2007-05-09
> **Nikron said:**
> Does it realllly need a GUI?

Unfortunately yes... Or otherwise everyone would install DOS on it and be out of there in 5 minutes.

---

### Post by Pobega on 2007-05-10
If you have internet go for Debian Etch; It downloads everything right off of the internet so you should have up-to-date packages (At least in Etch terms) and you don't have to worry much about stability.

Or you could always give FreeBSD a shot, and install the binaries for X and a window manager. Or if you're daring use ports to install.

---

### Post by hermitguy on 2007-05-10
Puppy Linux.  I use it as my main operating system day to day.  Boot from live cd, run installer, and install GRUB.  Usually for me worth spending couple minutes more going over GRUB menu file before rebooting.  So if you are familiar with Puppy, definitely under 10 minutes. You can also just copy the three files off Puppy cd manually and either install GRUB or use a boot floppy/cd/usbkey.  There are different varieties of Puppy.  For absolutely smallest, look for Bare Bones Puppy or Simple Puppy.  They are like 20 to 30mb.  There is OneBone Puppy down close to 12mb, but it is commandline only.  If pretty counts , then 2.15CE though its over 100mb. 

Been a while since I've used it, but DamnSmall Linux also was a pretty fast install.  Not as flexible as Puppy, but its small and fast.

BeOS fairly fast to install if it supports your hardware.  win3.1 requires you install msdos and then 3.1 is fairly fast install.  Sure very fast if you prepare your own cd version.  Its the floppys that slow it down. Again it may not support modern hardware.  Hmm, think there was a 3.1 group that made a version that would boot directly from cd.  Unofficially since it still has M$ copyright.

Oh yea, there is BlueFlops.  2 floppy linux with a gui.  Think it can be installed to hardrive, but dont hold me to that for sure.

Hmm, I was assuming you had to install to hardrive, if not then the QNX demo floppy is by far fastest booting operating system with gui.  QNX no longer offers it, you have to go hunting for it.  Like any boot floppy it can be put on cdr and booted that way also.  Vaguely remember one of those "free bunch of dos tools on a cd" iso's includes copy of the old QNX demo on it.

---

### Post by -Rick- on 2007-05-10
Maybe [Syllable]("http://www.syllable.org")? Not really sure about installation, but atleast booting goes very fast.

---

### Post by Neobuntu on 2007-05-10
It depends on the hardware.

Assuming live CD's are allowed (otherwise you just hard drive install the live CD but it will take longer) use a Puppy Linux 2.15CE live CD. 

Really old CDROM drives may give you trouble.

128MB RAM will (automatically) run super fast in that RAM. 64MB RAM recommended minimum and it should work in less.

Watch out for weird Video card and monitor as you will have to spend time trying other xvesa settings or even the bigger xorg video. Most things should work with xorg set to vesa, as a fall back.

What are the "rules"?

Will you get points for a better experience or just a gui?

A really (bad) minimalist gui (with extream RAM limits) would be Basic Linux. I still mean to test it's remote X as a client  (XDMCP) type usage on otherwise worthless boxes (from a more powerful server).

My guess is, the parts you will be working with are pitiful.

---

### Post by JoxBG on 2007-05-12
Bring menuetOS (also known as MeOS), installs from a single floppy, complete with GUI. Very fast and coded in assembler. :) That thing kicks-***.

---

### Post by RAV TUX on 2007-05-12
**[[B][B]elive**[/B]]("http://www.elivecd.org/")[/B]


Has the fastest install with a gui that I have ever seen.

---

### Post by john_spiral on 2007-05-13
elive or [DSL]("http://www.damnsmalllinux.org/") would have my vote.

---

### Post by ep2011 on 2007-05-13
I would say to install Damn Small Linux or Puppy Linux. They both are very small and fast loading, with a gui.

---

### Post by yatt on 2007-05-14
I'd have to say Elive is the fastest in my experience.

---

### Post by anaconda on 2007-05-16
Does it have to be linux? If not
Windows 3.0
The install just copies the 10MB to the HD and its installed!!

but it wil need DOS under it..

---

### Post by librano on 2007-05-18
the fastest distro i ever installed was a while back... and on a modest computer... wait for it.... it was Lindows! honestly it took just 10-12 minutes... it was one of the distros i tried when i was switching to Linux... but I never did stick to it. 

10-12 mins is quite a feat though... i remember telling my friends that Linux installs faster than application do on Windows. :) oh and it did come with a full compliment of applications... it wasnt barebones or anything.

---

### Post by ThinkBuntu on 2007-05-18
Arch will install in 5-10 minutes if you use the Base install. That leaves you with a text-only system and vi, nano, internet, package management, and more. If you have internet, then "pacman -Syu; pacman -S xorg xfce; /etc/rc.d/xdm start". Or, use the normal disc and install Fluxbox or Xfce off of it. Hope that helps!

---

### Post by 3006828 on 2007-06-03
so what did you end up doing?

---

