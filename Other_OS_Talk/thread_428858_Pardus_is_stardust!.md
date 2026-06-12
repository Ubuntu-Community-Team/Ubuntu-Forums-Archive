---
title: "Pardus is stardust!"
date: 2007-04-30
forum: Other OS Talk
---

### Post by floke on 2007-04-30
Tonight I've installed Pardus alongside my Feisty partition; and its excellent!
Wireless works out of the box; installation was a breeze (you need the non-LiveCD though - and make sure you don't install grub to the mbr - install to root and then copy the grub.conf lines into your normal grub menu.lst before running a sudo grub-update) - although it took longer than ubuntu - around 30-40mins.
Just got beryl set up with no hitches.
Package installation is simplicity itself, and the whole thing is set up very nicely.
Super fast too. And boots in 40 secs from selecting in grub to having a usable desktop (including the time spent entering my password at login screen).

If anyone has a spare 10Gs or so knocking about in an unused partition I would heartily recommend giving this a bash. Its different enough to feel new (I don't use KDE normally so thats an extra newness too); but very easy to suss out and navigate around.

Enjoy Pardus :)

---

### Post by floke on 2007-04-30
Forgot to add the cliched screenshot....

---

### Post by Leeghoofd on 2007-05-03
I just gave the Pardus Live cd a spin, since i do not have any partition space left atm.

It shows some pretty good things:

* hardware support seems better than Ubuntu/debian ( in my case anyway, ubuntu and many other distro's did not support my wireless out of the box. same for my sounddrivers. Do keep in mind that this was on a machine hardly a few weeks old )

* Excellent UI. I liked the UI better than the userinterface in PClinux OS. Altho both distro's are strong in this department, Pardus appears to have a better organised, more finished look. Altho this might be something personal. PCLinuxOs borrowed alot from Mandriva, which has some shortcommings. Again this is just my personal opinion and other might disagree.
The UI in Pardus can be configured to look alot like the one in Sabayon, which is not bad at all.

* stability. For me PClinuxos has been the distro i worked with so far. Altho very impressive for a non final RC it did have some serious issues, most of those are being worked on. Anyway this was PClinux. Pardus seems to have less issues. One however has to keep in mind that this distribution is rather new and small so it will have its own share of problems.

There were some things that bugged me about pardus aswell:

* . Live cd seems to have no clear " installation " option. There is a seperate cd for installation available, however one should be able to install from a live cd without any hassle.

* Package manager. As a former ubuntu and pclinux user I am pretty much used to Synaptic, which was working perfectly. I haven't really given the Pardus package manager a spin yet, so I don't know if their choice is a bad one or not, but for now i'm still wondering why they haven't picked synaptic ;)

* Installed default programs. I really do not like kopete messenger and prefer VLC over kaffeine any day. THis however is personal taste. Install your own programs through the packetmanager.

* Forum support. There is a worldforum, but the number of users is fairly small. The most used pardus Forum is in the Turkish language. Since most of us don't speak turkish, getting free support is hard. This problem might fix itself if Pardus manages to become more popular.
I do however doubt pardus will even be able to compete with Ubuntu.. The forum is still the driving force of ubuntu.

* no default 3d support. Pardus has nog beryl manager installed by default, like sabayon has. 
For some this might be plus, but i'm going to write this down as a minus. It is said that beryl can be installed fairly easy.

So much for my view on Pardus. For all critics among us: I have not tested this distro in depth.

---

### Post by floke on 2007-05-03
Well I've been using Pardus solidly since installing a few days ago and am falling more in love with it. From my readings and experience I can answer some of your points:

Hardware support seems much better than Ubuntu ootb - the only distro I've ever tried that can run a broadcom 4311 and a Belkin card off the bat. The only issue I had was an oversensitive touchpad - easily cured my experimenting with the xorg.conf :)  DVD's play perfect straight off - Kaffiene is all over the place but VLC is in the repos and works like a dream with no configuring.

UI is also excellent - I feel completely comfortable with KDE - and this from a steadfast Gnomer who couldn't stand it! The whole thing is very polished and very impressive. In fact I would go so far as to say that the whole experience feels slicker than Ubuntu.

The community and forums are very small, though, which is, of course, a massive plus point for Ubuntu :) 

The LiveCD does not have an installer - so not a flaw there. To install you have to run a separate disk (I suppose they can get more on the LiveCD if they leave the installer off, and more on the installer disc if they leave the Live-ability to one side). The installation is ridiculously easy (easier, I would say, for a new user, than installing ubuntu) - although as I mentioned earlier be sure to install grub to the root partition rather than the mbr and then copy over the stanza to the ubuntu menu.lst (if installing alongside ubuntu).

Installed default programs - no biggy to install others from the repos. OOo writer didn;t have the dictionary installed by default though - which meant I couldn't use spellcheck until I worked out why (!).

Beryl is also easy to get up-and-running - although the version I have is an old one and doesn't work to well with OOo (word count is displayed as full screen and other oddities) - I suppose I could get a newer version but to be honest I haven't been using Beryl in any case so am not bothered.

The package manager is also excellent - PiSi (Packages Install Successfully as Intended) - it only dowloads the altere/updated code, rather than the entire package for an update; and configures all dependencies etc. - like synaptic but better polished. Of course, it doesn't use deb or rpm packages - uses pisi instead - so the repos are a bit limited ('only' 5000 or so programs!); though is will increase rapidly I'm sure as the user base grows. 

In short, Pardus is great. I still consider Ubuntu to be my 'home' distro, but Pardus is certainly up there alongside it ATM. On Distrowatch it's rated as 44, but will definitely be a top 20 sooner rather than later. Since its only been around for a couple of years - and only in its 'modern' form since March - this is not surprising.

Give it a go; this one's gonna be big, and for good reason :)

---

### Post by fastguy on 2007-05-27
Hi,

I've read your posts about Pardus. I'm an active user of both Ubuntu and Pardus. In my current setup:
- XEN Dom0: Ubuntu Gutsy base install
- Xen DomU: My daily OS, Pardus 2007.1

Some more info about Pardus:

- Website: [http://www.pardus.org.tr/eng/index.html](http://www.pardus.org.tr/eng/index.html)

- Nice article using Pardus as an example. "Rethinking the Linux Distribution"
[http://www.onlamp.com/pub/a/onlamp/2007/05/10/rethinking-the-linux-distribution.html?page=1](http://www.onlamp.com/pub/a/onlamp/2007/05/10/rethinking-the-linux-distribution.html?page=1)

- You can send mail to pardus-users or pardus-devel mailing list in English and sure you'll get an answer pretty quickly in English (at least I will answer you) :)

- Usually, I report a bug on Sunday morning at 01h00 and the developers respond at 01h30 :) we have some geeks there :)

- Installing Grub to MBR won't do any hard (at least in my setup)

- I didn't check dictionary support, but Pardus is famous in Turkey for its "out of the box" Turkish spell checking functionality. I'm sure it also exists for other languages. Just neess a big digging, and if any problem, an email to pardus-devel list.

- Foreign users' problems are especially taken care on priority due to the hospitality of Turkish people :)

- According to the HOWTO document, Beryl is installed from svn, so shall always be the latest version.

- For package manager pisi (which means little cat in Turkish), the delta update function (for only downloading changed portions) is still being tested. We hope to have it this summer with Pardus 2007.2

- PISI has both goodies of apt-get of Debian and emerge of Gentoo. It's an advanced package management system. You're welcome to read the paper about it:

- Security is especially given importance:
[http://www.pardus.org.tr/eng/documents/developer/security-in-pardus.pdf](http://www.pardus.org.tr/eng/documents/developer/security-in-pardus.pdf)

- Pardus is developed by the Scientific and Technologic Research Counsil of Turkey, so has government support behind it. The operating system is targeted to be used in the Government and Military Desktops. Nevertheless, it's GPL, so if you like, you can fork your own distro from it.

Some yet-negative points from my point of view:
- Server setups, lvm and raid is not in the distro as it's mainly targeted for desktop users. Nevertheless, I've checked their "internship" programs for this summer, it seems that all LVM/RAID and Installation with LVM/RAID will come this summer. Currently, Ubuntu can be setup with LVM/RAID when doing the installation with alternate setup.

- Some exotic packages don't exist yet. But can be compiled as usual. May also be possible to locate such packages with "pisibul" , an applicaiton which checks all test/beta/playground package databases (use at your own risk).

- Needs a bit time to adapt for advanced users. No /etc/init.d no /etc/rcx.d but instead a new service start/stop mechanism based on "Mudur" (manager in Turkish) and "Comar" (a common name given to a dog in Turkish). Pretty effective. There are laso two files (/etc/conf.d/local.start and /etc/conf.d/local.stop) for people who don't want to develop a service script written in python.

It's sure that Ubuntu is a very powerful distro and it will for-sure be in the coming years, just to mention that Pardus is working as good as it is and I think some marketing would do it much better.

Best regards,

Fastguy

---

