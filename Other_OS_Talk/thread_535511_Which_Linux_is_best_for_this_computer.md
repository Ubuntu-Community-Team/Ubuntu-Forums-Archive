---
title: "Which Linux is best for this computer"
date: 2007-08-26
forum: Other OS Talk
---

### Post by monsieurdozier on 2007-08-26
I have a Pentium III 733MHz 256 RAM machine and Ubuntu Feisty Fawn is a little slow for me.  

What is a good distro I can put on it to run quickly?  I mainly want to use if for the internet and just all around playing with Linux.

Monsieur Dozier

---

### Post by Super TWiT on 2007-08-26
Have you tried installing Xubuntu?```
sudo apt-get install xubuntu-desktop
```  Otherwise, you could try Puppy LInux, DSL, or DSL-N

---

### Post by boopyg on 2007-08-26
You could use Puppy Linux, it is meant for slow computers so give it a try

[http://linuxondesktop.blogspot.com/2007/04/puppy-linux-linux-distribution-that.html](http://linuxondesktop.blogspot.com/2007/04/puppy-linux-linux-distribution-that.html)

---

### Post by SNYP40A1 on 2007-08-26
About two years ago, there was a distribution called Damn Small Linux that took up around 40 MB.  I played around with it on older systems and the speed was fine.  However, in your case, I do not think that the issue is the CPU speed, you need more ram.  Throw in another 256 MB or preferably 512 MB and your speed will be fine.

---

### Post by Super TWiT on 2007-08-26
Right now, I am only using 230 MB of my ram.  No swap space is being used either.   Usually, I don't use more than this.  However, it of course depends on what you use the system for and how many programs you have open at a time.  SNYP40A 1 is right though your CPU is probably fast enough.  I just noticed that I don't use that much ram.

---

### Post by monsieurdozier on 2007-08-26
I run the system check while I'm using Feisty Fawn and the memory doesn't top out on me with what I do, it's the processor that spikes.

I'm downloading xubuntu now and give Puppy Linux and Damn Small Linux a try.

Thanks much everyone.

Monsieur Dozier

---

### Post by Warren Watts on 2007-08-26
> **SNYP40A1 said:**
> However, in your case, I do not think that the issue is the CPU speed, you need more ram.  Throw in another 256 MB or preferably 512 MB and your speed will be fine.

I am running Ubuntu on a 450 MHz P-III with 384MB, and I agree.  When I boosted the RAM from 256MB to 384MB, it made a huge difference in performance.

If you are still looking for a smaller, faster alternative, you might try Wolvix Cub.  Like Xubuntu, it utilizes the XFCE desktop which is a lot less resource hungry than Gnome.

Wolvix Cub is intended as a Live Distribution (meaning it is set up to be booted and used from CD/USB Flash Drives), but the option to install it to the hard drive is included.  I installed it on a 4.3GB secondary drive in my 256MB 700MHz system, and it works like a charm. The entire OS only occupies 1GB, and I still have 2.4GB of the 4.3GB still free, and that includes the 512MB swap partition!
> warren@wolvix ~ $ df
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             3.5G  964M  2.4G  29% /

Multimedia works right out of the box, including Adobe Flash 9.  In my opinion, Wolvix Cub is a much slicker and easier to use distro than Xubuntu.

---

### Post by Lord Illidan on 2007-08-26
Zenwalk is also nice.

---

### Post by kellemes on 2007-08-26
> **Lord Illidan said:**
> Zenwalk is also nice.

It is indeed..
There are a bunch of smaller distro's out there offering a lot more possibilities as the bigger boys, like *buntu. With all respect.
I'm on Arch and loving it.

---

### Post by darksong on 2007-08-26
256mb of ram should be more than enough to run ubuntu. I recomend either puppy - is a good distro but your pc specs are not that bad for email, internet, music ect - and you will probably want something that looks abit more flash than puppy. I would try debian (people say its hard to install but if you have a bit of tech experience its not to hard. Debian is like ubuntu but i find it faster and more streamline) zenwalk - a very good distro (again i find the installer harder than ubuntu to use), wolvix and slax also works well on older systems (i belive all are based around slackware) or try xubuntu and see if that works for you. 

Your PC would run XP fine, so most linux distros - maybe except suse and fedora should work fine on your PC. More ram will speed up  your system, bumping it up to 512 should let you run any linux distro with ease.

A reason why ubuntu may be running slow is that it has (so called) alot of background processes running which require more ram and work on behaf of processor.

---

### Post by flatwombat on 2007-08-26
I'd try SAM linux, an Xfce version of PCLinuxOS.  It's surprisingly fast and full-featured and I've had it run on as little as 96meg/ram and a 600mhz. Pentium 3.

---

### Post by jrusso2 on 2007-08-26
I have tried most of these, I have a lot of old computers and I find Sam Linux to be very good.

Puppy Linux and Damn Small are nice for really old hardware but they are not really complete distros and you get frustrated if you try to add things not in the repository.

---

### Post by monsieurdozier on 2007-08-26
Believe it or not I'm downloading all the suggestions given and giving them all a test drive.

As of now,

Damn Small Linux or Puppy Linux are at the top.

Xubuntu is up there just because of my familiarity with Ubuntu.

I'm downloading Debian 4 and SAM Linux to give them a test drive.

Zenwalk didn't like my video card.  (Forgot to mention I have a Nvidia.)

I'm trying them all, so thanks for all the suggestions.

Monsieur Dozier

---

### Post by ArtF10 on 2007-08-26
Did you try the Zenwalk Live-Cd first?

I found that it gave me some problems with my video card drivers as well,,,, it too was NViDia.  But since I do not plan on doing any fancy stuff with the Zenwalk install, I just removed and reinstalled it and didn't install the Nvidia drivers....runs fine and I didn;t notice any difference in anything.  It's the only OS on the hard drive...has all I need.

BTW, the error message was about me having selected a WRONG MODE...whatever, I selected no such thing.

The distro is flying on my old machine.

---

### Post by Epilonsama on 2007-08-27
You should also try Dreamlinux, it comes  with a customize xfce and it come multimedia ready and is compatible with debian repos:)

---

### Post by Midwest-Linux on 2007-08-27
> **monsieurdozier said:**
> I have a Pentium III 733MHz 256 RAM machine and Ubuntu Feisty Fawn is a little slow for me.  

What is a good distro I can put on it to run quickly?  I mainly want to use if for the internet and just all around playing with Linux.

Monsieur Dozier

 Chances are you have PC 100 SDRAM 168 pin DIMM RAM. The good news is that memory is cheap for those  RAM chips. 99 cents to $5.00 for 64 MB, and $5.00 to $10.00 for 128 MB RAM on E-Bay.

 I personally found Ubuntu 7.04 will choke on 192 MB Ram, run OK on 256 MB but occasionally "hang" and do better with 384 MB and up. I am running Freespire 2.0 which is based on Ubuntu 7.04 on two separate machines, one a 256 MB and another with 384 MB. Of course the 384 MB runs better, and since you have a 733 Mhz Pentium...may I suggest Freespire 2.0 if you do decide to add some extra ram.

 Besides DSL, there is also Vector linux which I heard will run fine on 128 MB. 

Windows 2000 will run fine on 256 MB also......just kidding...lol

---

### Post by dptxp on 2007-08-27
> **Midwest-Linux said:**
> Chances are you have PC 100 SDRAM 168 pin DIMM RAM. The good news is that memory is cheap for those  RAM chips. 99 cents to $5.00 for 64 MB, and $5.00 to $10.00 for 128 MB RAM on E-Bay.

 I personally found Ubuntu 7.04 will choke on 192 MB Ram, run just OK on 256 MB and do better with 384 MB and up. I am running Freespire 2.0 which is based on Ubuntu 7.04 on two separate machines, one a 256 MB and another with 384 MB. Of course the 384 MB runs better, and since you have a 733 Mhz Pentium...may I suggest Freespire 2.0 if you do decide to extra ram.

Ubuntu runs fine on my desktop with 192 MB RAM (256-64 for video).
My CPU is Sempron 2500+ 64 bit.

---

### Post by Midwest-Linux on 2007-08-27
> **dptxp said:**
> Ubuntu runs fine on my desktop with 192 MB RAM (256-64 for video).
My CPU is Sempron 2500+ 64 bit.

 
I have a Gateway E-1400 running 600 Mhz 256 MB Ram running Freespire 2.0, and a HP 6640 running 500 MHz and 384 MB Ram also running Freespire 2.0. So I have low end equipment and I belive too that the faster the machine will improve performance also.

---

### Post by init1 on 2007-08-27
Try Vector linux. It's very complete, and very fast. 
[http://www.vectorlinux.com/](http://www.vectorlinux.com/)

---

### Post by WishingWell on 2007-08-27
> **Lord Illidan said:**
> Zenwalk is also nice.

I'll second that.

---

### Post by monsieurdozier on 2007-08-27
I've tried almost all of the titles suggested so far.

Zenwalk - Once I actually got the live CD running, I enjoyed the interface of it, and it worked well off the Live CD.

SAM Linux - Didn't like my video card in both the normal boot and the safe graphics mode.

Damn Small Linux - I really liked the interface but the earlier comment about it and Puppy Linux kind of worries me.  Would be great as a live CD, but for a full install, I'm doubtful.

Puppy Linux - Same as Damn Small Linux

Xubuntu - I like Ubuntu, but I'm in the mood to try something new.

Dream Linux - Okay, didn't really leave a lasting impression on me.  =\

Wolvix Cub - I looked at their website and it posted the requirements as more than I have, so I didn't try it.

Debian 4 - I think I downloaded the install version and not the Live CD version, so I installed it and gave up.  I just don't want to go through that hassle not now.

I'm downloading Vector Linux now to give it a try.



About upgrading my machine, I'm not interested in making it any better than what it is.  I built this thing from junk parts so it really doesn't hold that special of a place in my heart.

I appreciate all these suggestions and I'm giving every one a try.

Monsieur Dozier

---

### Post by jrusso2 on 2007-08-27
I got one more suggestion elive.  I tried it once and it was pretty nice.

---

### Post by mindtrick on 2007-08-28
Wolvix is an awesome lightweight distro.

---

### Post by walktod on 2007-08-28
I second that. P500 with 192MB of Ram. I couldn't even get the liveCD's of Ubuntu/Xubuntu to boot.

DSL & Puppy were a bit too unfamiliar for a complete winedoz newbie (gf).

So I hooked her up with Wolvix. Fast and has that Ubuntu ease of use.

---

### Post by fistfullofroses on 2007-08-28
Slackware is great. Especially for hardware of that era. 
Arch is an extremely fast system, as is GoboLinux.
You may want to look into Fluxbuntu or March as well.
Damn Small and Puppy will not give a general Linux feel,
and if you are looking to learn a little, they hide the undercarriage a bit.

---

### Post by bake7221 on 2007-08-28
I've got an AMD 4400+ X2 running at 2.1 ghz ... 2 gigs of PC3200 ram ... and a Nvidia 6600GT ... Kubuntu with Beryl runs amazing on my machine. (Obviously I would hope so ... ) ... for speed, and a small distro that doesn't use much resource. I was suggested arch-linux. It is a little difficult to install, you'll need some tech expertise, I had to have help, but I'm not the greatest with linux ... yet.

---

### Post by finferflu on 2007-08-28
I second Arch. You'll love it. It's fast, stable (even though it's very up to date) and simple, even though you'll have to read the Beginner's Guide to get started. I assure you you'll never leave it :)

---

### Post by j.miller565 on 2007-08-28
What about SLAX?

---

### Post by Bart_D on 2007-08-29
If you want speed, Fluxbuntu might be worth a look.

---

### Post by init1 on 2007-08-29
> **j.miller565 said:**
> What about SLAX?
Slax does have it's limitations, but it does run well on old computers, as long as you don't try to run KDE. TWM should run fine.

---

### Post by eeried on 2007-08-29
hello Monsieurdozier,

You say you like DSL: well, then you'll love Debian 4 (Etch) running Flubox as the window manager (DSL window manager). Debian takes some learning after the install which is very simple. I'd recommend the Debian.net forums which holds a very good Fluxbox howto.

Your computer is very powerful compared to mine:
I've got a PII 400MHZ, 256Mo: this ran Ubuntu dapper fine, and Xubuntu Feisty and now I've switched to Debian Etch for a change. Flubox is the window manager I used a few years ago after using IceWM, and I really like Fluxbox. It's rather minimalist but you can customize it by editing a couple of files and by using Rox filer (file manager used by Puppy).

In fact your computer should run Xubuntu Feisty quite satisfactorily. Don't open 100 tabs in firefox, that's all. But you can have several apps opened providing they aren't working all at the same time. For instance when I run apt-get (am on dial-up) I don't burn a CD but I don't quit k3b before running apt-get.

Rather use the command line for things like upgrading (apt-get rather than synaptic), copying large files or dirs.

Add a USB 2.1 PCI card if you're using an external HDD, and copy using the command line.

I have been given a PIII 400MHZ Compaq with 320 MB RAM, and I run Xubuntu-Feisty packed with software: k3b, k9copy, grip, the whole openoffice.org suite, F-Spot, Apache (local server only), mysql, php5...

I'v bought a recent DVD burner. I can watch DVDs too.

The HDD is 20GB but I use only part of the 4Gs set for the /. /home is on the rest -- I'm on the PII so I can check rght now.

As soon as I can, I'll install fluxbuntu on an antique PII 230MHZ, 320 MB RAM.

As has been said Xubuntu requires some easy tweaking: disabling useless services so that they don't start at boot  time (you can starrt them later if need be), deleting unnecessary locales, "deleting" some ttys.

I've also installed Xubuntu-Feisty on a PII 350MHZ with 256Mo and on an AMDk6-400MHZ 256MB RAM. they both run fine.

As far as I konw the quality of the processor is important. i felle my PII 400MZh (Deschuttes) is better thatn the PIII 400MHZ (Kalmai or someting like that). Amd-k6 is good too but the motherboard is lousy (no AGP port), and the ISA video card is quite bad: S3 -- still it's okay and you can watch a VCD.

@others: reading through the thread makes me feel like trying Sam Linux -- PCLinuxOS is great. And Arch too sounds good. :guitar:

cheers,

---

### Post by monsieurdozier on 2007-08-29
I'm in the process of downloading ArchLinux, and I'm going to give it a try.

I've installed Xubuntu on my machine and giving it a go, to see how smoothly it runs, and right now it's doing fine.  But I am still nervously looking for something new.

I found I really like the XFCE interface better than the GNOME and KDE.

I'm going to give Arch Linux a try and look over the posts another time to see if there are any others I missed.

Monsieur Dozier

---

### Post by fwojciec on 2007-08-29
Make sure to use the install guide ([link]("http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide"))  and the Arch wiki in general - you'll find it indispensable in your first weeks of using Arch.  Good luck with the installation and have fun!

---

### Post by monsieurdozier on 2007-08-29
To the guys who use Arch Linux, maybe you can help me out.

I've installed it according to the guide here: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

But I've his a road block.

In the video drivers section I've followed the instructions for installing my Nvidia GeForce 2 MX/MX 400.  I installed the nvidia-96xx driver, ran the program, downloaded Xterm and tried it.

My screen goes blank for a bit then makes grey boxes with flashing white lines in them.  I Ctrl+Alt+BackSpace, and I get a Fatal Server Error.  Caught Signal 11.

I actually created a xorg.config file and ran the driver again.  Same problem.  

Any help, or should I post this somewhere else?  If so, where?

Monsieur Dozier

---

### Post by fwojciec on 2007-08-29
Try posting it on the Arch linux forums, you'll likely get better answers there.  My only suggestion would be to try different nvidia drivers, or even just download the driver from Nvidia website and install it (this is what I usually do anyways), you can also try and use the xorg.conf from your ubuntu install if you still have it around (it should work, but you might have to adjust font paths and minor stuff like that later).  But yeah, it's something that should be fixable.

---

### Post by fistfullofroses on 2007-08-31
Slax has quite a few limitations actually, but seeing as it has its basis in Slackware, it should run well on older hardware. KDE will require quite a bit of RAM, and as such you might want to look into alternative Slax Live CDs.

---

### Post by jacob01 on 2007-09-01
dsl *(damn small linux)

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

feather linux 

[http://featherlinux.berlios.de/](http://featherlinux.berlios.de/)

but both of those may be a bit extreme they are able to be run on a comp with 128 meg of ram or less

---

### Post by LinuxGuy1234 on 2007-09-02
> **monsieurdozier said:**
> I have a Pentium III 733MHz 256 RAM machine and Ubuntu Feisty Fawn is a little slow for me.  

What is a good distro I can put on it to run quickly?  I mainly want to use if for the internet and just all around playing with Linux.

Monsieur Dozier
You should try Puppy Dog Linux.:)

---

### Post by monsieurdozier on 2007-09-02
Well, after trying countless versions of Linux, I've settled with Arch Linux.

Why?

I actually build it from the kernel up, and I have learned so much from just installing it.  It's extremely customizable, (Don't get me wrong, so are most of the others).  And it's running like a dream on my machine.

I appreciate everyone's suggestions and I'm keeping all the Live CD's to play with for when I get my next computer.

Monsieur Dozier

---

### Post by mips on 2007-09-03
> **monsieurdozier said:**
> Well, after trying countless versions of Linux, I've settled with Arch Linux.


What Desktop Manager did you settle on ?

---

### Post by monsieurdozier on 2007-09-03
> **mips said:**
> What Desktop Manager did you settle on ?

XFCE

---

### Post by oiler920 on 2007-09-03
Yeah, I think if you want speed, your best option is to use Xubuntu and Openbox together. :)

---

