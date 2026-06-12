---
title: "Server distro, min requirements"
date: 2009-02-11
forum: Other OS Talk
---

### Post by L815 on 2009-02-11
I need a linux distro to use as a server inside a virtual machine (virtualbox). 

It needs to be a "server edition" without x or a wm/de installed. I need one that requires very low ram; running in VM and all. And, I wish for it to be up to date (not many outdated packages).

I know ubuntu server is an option, but I want to explore other options first.

---

### Post by cardinals_fan on 2009-02-11
SliTaz can make quite a good server with lighttpd.  With that said, I have to give my overall server blessings to Slackware, NetBSD, and FreeBSD.  BSD systems make excellent and minimal servers.

---

### Post by mohitchawla on 2009-02-11
CentOS, OpenSUSE and Ubuntu are your safest and easy choices. But as you are looking for rather lightweight alternatives, Slackware should do just fine except that keeping your system up-to-date won't be as easy in Ubuntu etc. 

As far as BSDs are concerned, I read somewhere VirtualBox support for BSDs is not good...so maybe you could try alternative virtualization softwares and run BSD on them.

---

### Post by L815 on 2009-02-11
I thought of CentOS, but it seems to install a gui & X by default.

I haven't ever dealt with *BSD or Slackware. Looks like something to learn!


Hmm.. the choices lol

---

### Post by KaiHeimann on 2009-02-11
If you are looking for a server distro without a gui to run in your vm by default at a small footprint then you can't go past Ubuntu JeOS. It is a variant of Ubuntu Server that has been optimised for running inside vm's.

You can get a copy [here]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos")

Hope that helps and if you have any questions don't hesitate to contact me.

---

### Post by SkonesMickLoud on 2009-02-11
Arch Linux.  A default install gives you a command line, and not much else.  Full system upgrade is as simple as running *pacman -Syu* once or so a week.

---

### Post by notwen on 2009-02-11
[Debian Sid]("http://www.debian.org/releases/unstable/") perhaps?  Debian is a rock solid distro, and using sid would be the best bet for newer packages, considering Debian's time-frame for adding/removing/changing packages in it's stable branch.  =]

---

### Post by SkonesMickLoud on 2009-02-11
> **notwen said:**
> [Debian Sid]("http://www.debian.org/releases/unstable/") perhaps?  Debian is a rock solid distro, and using sid would be the best bet for newer packages, considering Debian's time-frame for adding/removing/changing packages in it's stable branch.  =]

Sid's not a great idea for a production server.

---

### Post by SuperSonic4 on 2009-02-11
> **SkonesMickLoud said:**
> Arch Linux.  A default install gives you a command line, and not much else.  Full system upgrade is as simple as running *pacman -Syu* once or so a week.

Seconded for Arch

Pacman is an awesome package manager.

---

### Post by snowpine on 2009-02-11
> **notwen said:**
> [Debian Sid]("http://www.debian.org/releases/unstable/") perhaps?  Debian is a rock solid distro, and using sid would be the best bet for newer packages, considering Debian's time-frame for adding/removing/changing packages in it's stable branch.  =]

For a server, I would recommend Debian stable first, then testing, with unstable (sid) a distant third...

---

### Post by Sorivenul on 2009-02-11
If you're setting up a server in a virtual environment, I would go with Slackware or Debian (Lenny). Both are quite stable and aren't "resource hogs". I *would* suggest one of the BSDs, but they are notoriously painful to set up in a VM.

---

### Post by SunSpyda on 2009-02-11
*BSD or Debian GNU/Linux would be great for a server. I use OpenBSD on mine and it works great. I used Debian before that, and that worked really well too.

Virtualbox doesn't play nice with BSDs, so VMware might be in order for BSD ditros. I managed to get OpenBSD to work in Virtualbox, but there were loads of problems.

I know there are many other Linuxes for servers, but I have only used Debian for a long period of time. I hear nothing but positive feedback about Slackware, so you might want to try that.

---

### Post by kk0sse54 on 2009-02-11
I definitely check out one of the *BSDs. I've got FreeBSD working currently through Virtualbox with a few slight glitches but for testing *BSD in a vm I'd definitely recommend Vmware Server or you can try out KVM (there's also Qemu but I've read mixed reports about it)


btw nice avatar Sorivenul :)

---

### Post by notwen on 2009-02-11
> **L815 said:**
> I need a linux distro to use as a server inside a virtual machine (virtualbox). 

It needs to be a "server edition" without x or a wm/de installed. I need one that requires very low ram; running in VM and all. **And, I wish for it to be up to date (not many outdated packages).**

I know ubuntu server is an option, but I want to explore other options first.

> **SkonesMickLoud said:**
> Sid's not a great idea for a production server.

> **snowpine said:**
> For a server, I would recommend Debian stable first, then testing, with unstable (sid) a distant third...

Only recommended sid to avoid any packages the user may want from becoming 'outdated'.  =]

---

### Post by SkonesMickLoud on 2009-02-11
> **notwen said:**
> Only recommended sid to avoid any packages the user may want from becoming 'outdated'.  =]

Better to be a tad outdated than have your server crash because foo.package isn't stable.

Most apps that are used for a server have been around for a while, and are already quite stable.

---

### Post by Sorivenul on 2009-02-11
> **C!oud said:**
> I've got FreeBSD working currently through Virtualbox with a few slight glitches but for testing *BSD in a vm I'd definitely recommend Vmware Server or you can try out KVM (there's also Qemu but I've read mixed reports about it)
I second this, if you were to use a BSD. FreeBSD has given me the best results in a virtual environment.

> **C!oud said:**
> btw nice avatar Sorivenul :)
Thanks... ;)

---

### Post by L815 on 2009-02-11
I have limited my choices based on the suggestions to Ubuntu JeOS, Arch, Slackware (BSD I will leave for the future). 

Arch I like because of packman and it's fast, Slackware for an adventure, and Ubuntu JeOS because I like Ubuntu :]


I will end up just trying these 3 out and choosing one based on experience.

I'd like to thank all for the suggestions :popcorn:

---

### Post by Sorivenul on 2009-02-11
> **L815 said:**
> I have limited my choices based on the suggestions to Ubuntu JeOS, Arch, Slackware (BSD I will leave for the future).
Any of those choices will do just fine. Let us know what you end up with...

---

### Post by handy on 2009-02-11
I don't think I would use Arch as a server.  I tend to think that cutting edge is not a good reliable place for a server to be.

If you can afford downtime with your server, & you're happy to spend the extra time that may be required to maintain Arch then go for it.  It will be fast & light.

---

### Post by L815 on 2009-02-11
I forgot to ask, what is the lowest amount of ram that any of the 3 choices above would run on? 


I can manage with a few problems here and there if it runs at the lowest amount of ram. If there are others which would run at less than Arch, please say so :]


EDIT: Having issues getting Arch to install in virtualbox. When it comes time to install packages, it just doesn't do it (can't see the error messages).

---

### Post by Sorivenul on 2009-02-11
> **L815 said:**
> I forgot to ask, what is the lowest amount of ram that any of the 3 choices above would run on? 


I can manage with a few problems here and there if it runs at the lowest amount of ram. If there are others which would run at less than Arch, please say so :]
Last I knew, Arch needed about 192Mb of RAM; Slackware can run on 64Mb.

---

### Post by L815 on 2009-02-12
> **Sorivenul said:**
> Last I knew, Arch needed about 192Mb of RAM; Slackware can run on 64Mb.


Ooooo, will have to play with Slackware this weekend. I'm currently installing the VM version of Ubuntu 8.10 with 120mb ram with no issues so far.

---

### Post by handy on 2009-02-13
> **Sorivenul said:**
> Last I knew, Arch needed about 192Mb of RAM; Slackware can run on 64Mb.

The following is from the Arch Wiki:

[I]Memory requirements:

    * CORE : 160 MB RAM x86_64/i686 (all packages selected, with swap partition)
    * FTP : 160 MB RAM x86_64/i686 (all packages selected, with swap partition) [/I]

---

### Post by Sorivenul on 2009-02-13
> **handy said:**
> The following is from the Arch Wiki:
I stand corrected. Still, 160 vs 64 is a fairly large difference, especially on lower end machines. 

Arch, while a great system, would make an fine server, IMO, but the rolling release system and possibilities of difficulties after updates keep me from suggesting it as a server. While it is a very solid system, it is still relatively too unstable to practically use as a server, especially with highly sensitive data or high amounts of traffic.

Just my two cents.

---

### Post by doorknob60 on 2009-02-13
Debian or Arch for sure. I got Debian running (with FLuxbox too I should add) on 64 MB of RAM and 400 Mhz K6 CPU. NO problems with it. I don't have any doubts that Arch courd run on it too, since I just set up an Arch box on a computer with 128 MB of RAM and a 667 mhz P3. It rivals the speed of a computer with 256 MB RAM and a 1.3 Ghz Celeron (P3 era) (also running Arch with similar software setup). Yeah they're both great distros for old computers. The trick to install Arch on limited RAM systems is tell pacman to keep packages in pacman cache instead of /tmp (I'm talking about during installation, it asks you, just the default is no say yes instead), which resides in the Ramdisk, which is too small to hold the packages. When it stores in pacman cache (which goes into the partition you chose to install it on) then it installs just fine.

---

### Post by handy on 2009-02-13
> **Sorivenul said:**
> 
I stand corrected. Still, 160 vs 64 is a fairly large difference, especially on lower end machines. 

I agree, or especially in a VM, on a machine running more than one VM.

{I only checked on the required RAM as I had never seen it written anywhere (or don't remember at least ;-))}

> **Sorivenul said:**
> 
Arch, while a great system, would make an fine server, IMO, but the rolling release system and possibilities of difficulties after updates keep me from suggesting it as a server. While it is a very solid system, it is still relatively too unstable to practically use as a server, especially with highly sensitive data or high amounts of traffic.

Just my two cents.

I agree completely.  

I don't want to do anything to a server except use it, & much as I love my Arch on desktop, I wouldn't ever use it as a server. I think BSD wins hands down (from my limited experience & knowledge). :-)

---

### Post by L815 on 2009-02-13
Arch I can't get to install packages during base install. 
Ubuntu Server (JeOS) won't boot because of "pae"
Gonna try Slackware next.

---

### Post by Sorivenul on 2009-02-13
> **handy said:**
> I think BSD wins hands down (from my limited experience & knowledge). :-)
On real hardware, you know this gets my vote. ;)

---

### Post by handy on 2009-02-14
> **Sorivenul said:**
> On real hardware, you know this gets my vote. ;)

In my office, Arch suits my needs/desires best for a workstation; though OSX suits my wife's needs perfectly on identical hardware, in her office. 

Riders for horses for courses... :-)

These days we are so fortunate to have so many high quality choices  available to us.

---

