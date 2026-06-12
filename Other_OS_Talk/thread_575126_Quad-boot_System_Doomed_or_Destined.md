---
title: "Quad-boot System: Doomed or Destined?"
date: 2007-10-13
forum: Other OS Talk
---

### Post by Xanderfoxx on 2007-10-13
I am seriously considering installing four GNU/Linux distros, while completely ditching Winblows (at least for my laptop).

I will probably install as many as six on my desktop.

But I'll save that for later.

**HERE'S THE DEAL:**

I have a Toshiba Satellite laptop, that more or less works completely under Ubuntu Dapper. I was quite pleased with my experience with Dapper, even though I had plenty of problems getting it to work, and it eventually became too unstable (freezing up every now and then, where I have to force the power off) to use. I intend to install these Linux OSes:

Ubuntu 7.04 (Feisty)
OpenSUSE 10.3
Slackware 12.0
Fedora 7 (Moonshine)

If I had more space I would also install:

PCLinuxOS 2007
Gentoo Linux 2007.0
Zenwalk 4.6.1

This is going to be fun!! :lolflag:  :lolflag:  :lolflag:

*ahem* Anyway, I want to know:

[LIST=1]
[*]What are possible problems with this quad install?
[*]What are some recommendations for a fifth distro?
[*]What are any tips, comments, or help you would like to offer?
[*]How am I going to overcome all of the GRUB problems?
[*]Are there any distros that will overwrite GRUB and place LILO in it's stead?
[/LIST]

I would love to know if there are any possible problems with this **BEFORE** I start.

I have already started erasing my disk (after backing up the more important data), but I was going to do that anyway.

Any pointers, guys?

---

### Post by FurryNemesis on 2007-10-13
AFAIK there's not technical barrier to having 4 OSs on there at once. Just RTM before you install to see what the install will do to GRUB.

---

### Post by ArtF10 on 2007-10-13
Zenwalk would cause LILO to overwrite GRUB.  However, this is my recommendation for a 5th distro.  I would wait for version 4.8 though...it's right around the corner.

There's a way to use GRUB by restoring it, that works for all distros.  There;'s a link in my thread, with the appropriate warning in **[COLOR="Red"]BOLD[/COLOR]**.  Note:  I just use my Ubuntu or Xubuntu CD to restore GRUB but that's just me.

GRUB **_WILLL_** be your main concern.

PS:  I tried triple booting and it did not work although I used Ubuntu, Xubuntu and Zenwalk....the Zenwalk install butchered up some stuff.  I have no clue about how Slackware, Fedora or SUSE are going to react.

PS # 2:  It maybe too late, but I would wait for Gutsy.

---

### Post by wolfen69 on 2007-10-13
my experience with multi-booting told me that installing ubuntu last is the best way. it handles grub flawlessly everytime. a couple of other distros would not see one of the drives, and then have to fix grub. feisty does grub well.

---

### Post by wolfen69 on 2007-10-13
i "only" triple boot now. ubuntu studio/gutsy/xp(not touched in 7 months) im thinking of getting another drive for a distro "flavor of the day" drive. i like to run 2 flavors of ubuntu at the same time, yet still experiment with others.

---

### Post by mindtrick on 2007-10-14
> Zenwalk would cause LILO to overwrite GRUB. However, this is my recommendation for a 5th distro. I would wait for version 4.8 though...it's right around the corner.

It's released.
[http://www.zenwalk.org/modules/news/article.php?storyid=62](http://www.zenwalk.org/modules/news/article.php?storyid=62)

OP, if you're in adventure mood, you might wanna try Fedora 8 Test 3

---

### Post by Shazaam on 2007-10-14
Size of your hard drive? Windows partition size?
What I did when I only had one drive (80gig) was to have XP (resized to 30gigs) as a Primary partition, added a 1gig /swap primary partition, then I made an Extended partition in the remaining space. Added DSL, PuppyLinux, Mepis, Mandriva and Ubuntu to the Extended partition (sharing the /swap partition). They all worked fine till XP crashed requiring a reinstall. Decided to isolate XP from linux so I added another drive.
Now I have XP on one drive and Linux on the other.

---

### Post by ArtF10 on 2007-10-14
> **wolfen69 said:**
> my experience with multi-booting told me that installing ubuntu last is the best way. it handles grub flawlessly everytime. a couple of other distros would not see one of the drives, and then have to fix grub. feisty does grub well.

I installed Xubuntu and THEN Ubuntu.  I could not get Xubuntu to boot correctly and had to change something through fdisk? (something that sounds like fdisk, but not fdisk<---disk check utility).  Needless to say, it was very much not install and let *buntu worry about it.  GRUB worked fine but another change had to be made.....I got help from user "rsambuca" for this.

PS:  If you're planning on going with Zenwalk, they I would agree with the Quote above...install Zenwalk and then Ubuntu.

---

### Post by DinCahill on 2007-10-16
I quad-boot XP, Vista, Feisty and OSX86. High five.

---

### Post by Xanderfoxx on 2007-10-16
I'm afraid I don't follow: "RTM" What do you mean?

I like your sig, BTW.

---

### Post by Xanderfoxx on 2007-10-16
Slackware uses LILO, and would not cooperate.

Fedora uses GRUB, and should work.

Ubuntu uses GRUB, obviously, and is known to work with Debian (it auto detects Debian install).

I don't know about OpenSUSE.

Again Zenwalk is based on Slackware, so it would follow that is also uses LILO, and could care less about GRUB data.

---

### Post by Xanderfoxx on 2007-10-16
I'm ditching Windows on this laptop.

I'll have XP on my new school laptop.

---

### Post by Xanderfoxx on 2007-10-16
If Zenwalk uses LILO, how would GRUB detect it? Is GRUB superior?

(Not trying to start a LILO vrs. GRUB war, but just curious as to what the two parties believe.)

I personally believe that if something encompasses, integrates, and expands the horizons of, another thing, it is usually superior.

Gotta go. Bye.

---

### Post by eelel_kielat on 2007-10-18
my only question is why would u want to put 4 os on one computer

---

### Post by LaRoza on 2007-10-18
On a single 160 GB hard disk, on a single computer, I managed to get 14 OS's installed and all in Grub and bootable, one was Windows XP, the rest were Linux's. So four should be easy.

The easiest way to do it, is to configure your partitions with GParted live CD, remember to make a swap partitions.

Install each OS with Ubuntu last, and everything will work.

---

### Post by Xanderfoxx on 2007-12-01
> **LaRoza said:**
> On a single 160 GB hard disk, on a single computer, I managed to get 14 OS's installed and all in Grub and bootable, one was Windows XP, the rest were Linux's. So four should be easy.

The easiest way to do it, is to configure your partitions with GParted live CD, remember to make a swap partitions.

Install each OS with Ubuntu last, and everything will work.

What all OS's did you install? Do any of them use LILO by default?

How did you get those to work?:confused:

---

### Post by maybeway36 on 2007-12-01
I can verify that Ubuntu detects other Ubuntu, Windows, Debian, PCLinuxOS, FreeDOS, and Linux Mint installations. I'm pretty sure it will work with almost every Linux distro out of the box. If not, you can always change menu.lst :)

---

### Post by Cursim on 2007-12-02
If you want to experiment with new OSes, why not just install VMware server? It's free, works well, and won't nuke your MBR :)

-cursim

---

### Post by sandysandy on 2007-12-02
i have quad boot - XP, Open SUSE 10.3, Edubuntu7.10 and Mandriva - all installed in that order.
edubuntu does detect previous installations and in my case Mandriva did not. so i copied relevant entries of Mandriva menu.lst into edubuntu&#347; menu.lst  after reloading Edubuntu&#347; GRUB using SGD.

quad boot is working fine in my case.

regards

---

### Post by CouchMaster on 2007-12-03
I'm booting 9 distros following this install thread [http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959) with no problems.  Put grub on it's own partition and it will boot just about anything, including LILO.  BSD and Solaris are problems though.
You might have to edit fstab in the Buntu family (comment out) some of the uuid lines to get them to boot to the desk top instead of a command line also...
But it's really cool.

---

### Post by LaRoza on 2007-12-03
> **maurin.alex@gmail.com said:**
> What all OS's did you install? Do any of them use LILO by default?

How did you get those to work?:confused:

Many, I don't remember all of them, as I often replaced them.

Some of them did use LILO, but the easiest thing to do is just install Ubuntu last, and it detected all of them.

If it didn't, I just added the entry usually using the menu.lst from the other distro.

---

### Post by Xanderfoxx on 2007-12-03
> **Cursim said:**
> If you want to experiment with new OSes, why not just install VMware server? It's free, works well, and won't nuke your MBR :)

-cursim

I didn't know it was free! I should have checked.

I've heard of it so many times, I thought it was a really cool system that you paid for. If it's free, then I'm going to have to go that direction! YES!

[singsong] I'm going to virtualize my PC! [x2 /] [/singsong]

BTW, what do mean, "MBR"?

Thanks a bunch, I just might do that!

I just need to learn everything I can about VMWare.

Thank you. :lolflag:

---

### Post by maybeway36 on 2007-12-03
VirtualBox is great at Linux guest systems.

---

### Post by b9anders on 2007-12-03
From the annals of the web acronyms:

> **maurin.alex@gmail.com said:**
> BTW, what do mean, "MBR"?


MBR: Master Boot Record - where the bootloader is often stored.

> **maurin.alex@gmail.com said:**
> I'm afraid I don't follow: "RTM" What do you mean?

A polite adaptation of RTFM which means: Read The F****** Manual

Sometimes expressed in politer form as 'Read The Fine/frigging/fragging/friendly/fantastic Manual' or simply, as here, RTM (Read the Manual). 

Related to terms like GIYF (Google is your Friend/Google It You F***wit), FGI (F****** Google It), STFW (Search The F****** Web) from before google's all-dominance, STFNG (Search the F****** Newsgroup) from when internet discussion was done properly, RTFS (Read the F****** Source) and UTSL (Use the Source, Luke) for hardcore unix users and WTFM (Write The F****** Manual) for those going where no man has gone before.

It is generally considered bad netiquette to put out as advice, particularly here (although I think the advice is sound enough in context) although there are fora like Gentoo and Arch (where 'RTFW - Read the F****** Wiki' is probably more prevalent) where you are expected to do a bit of homework before getting your feet wet, and it is thus considered par for the course if someone asks a question they could have answered themselves if they had read them manual.

---

### Post by LaRoza on 2007-12-03
> **b9anders said:**
> 
MBR: Master Boot Record - where the bootloader is often stored.


It isn't actually stored there, but it is the first 512 bytes of the hard disk and is checked by the BIOS for a bootloader. The bootloader is usually stored elsewhere, because it is too big, although the MBR's contents point to it.

---

### Post by new2*buntu on 2007-12-03
I have installed 4 OS's before (during my very short 2 month  linux experience). They were (in this order): Zenwalk, OpenSUSE, Mepis, then Linux Mint. After using them for several days, I decided to re-install Linux Mint and overwrite the others.

---

