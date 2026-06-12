---
title: "Guidelines to package Ubuntu for software release"
date: 2021-08-26
forum: Packaging and Compiling Programs
---

### Post by tc2020 on 2021-08-26
Hi,

I have this application software developed for an embedded device that is based on Ubuntu Server 20.04 LTS on RPi4B. The software is in its final development stage and should be ready for pre-release soon. I am looking for general guidelines/help on what steps to take to pack this application software together with Ubuntu and installed packages required for development, and to make this whole system more robust for use in 24/7 environment. Are there such standard guidelines available for developers to use as checklist during/after application software development?. 

Thanks.

---

### Post by dragonfly41 on 2021-08-27
> [COLOR=#000000]pack this application software together with Ubuntu and installed packages required for development[/COLOR]

If you intend packaging a custom Ubuntu *.iso for installation, including developed apps, then try Cubic.

---

### Post by mikewhatever on 2021-08-27
There aren't any guidelines for "package Ubuntu for software release", because third party developers never do it. All they need to do is to package their own software, and make it available for installation. 
One way is to have a PPA on launchpad.net, another is to submit it to [https://snapcraft.io/](https://snapcraft.io/)

---

### Post by grahammechanical on 2021-08-27
Ubuntu is based on the Debian distribution of Linux. Software packaged by the Debian package format will run on Ubuntu. Such software has the deb file suffix.

I have heard that learning to package software in the Debian package format is not simple. But here you go

[https://www.debian.org/doc/manuals/debian-faq/pkg-basics.en.html](https://www.debian.org/doc/manuals/debian-faq/pkg-basics.en.html)

There are other Linux distributions based on the Redhat distribution. They run software that is packaged using the Redhat Package Management method. Those packages have the rpm suffix.

The two package formats and not compatible. There are attempts to produce package formats that can run on any and every distribution of Linux. You need to research AppImage and Flatpack and Snap. I assume they each have their benefits and drawbacks. Distribution developers are taking sides but some have recognised that they have to meet the wishes of their users and make it possible for packages in these alternative package formats to run in their distribution.

[https://appimage.org/](https://appimage.org/)

[https://flatpak.org/](https://flatpak.org/)

[https://snapcraft.io/](https://snapcraft.io/)

The Snap Package format is developed by Canonical the sponsor of Ubuntu. Who have also produced a very secure version of Ubuntu to go on Internet of Things devices. This version is called Ubuntu Core. It, itself, is a Snap based operating system and will only run Snap apps.

I have heard that the packaging of an application as a snap is not too difficult and that the process of getting the app accepted by Ubuntu is far quicker than if you were applying to have a deb packaged app accepted. Ubuntu developers will not allow a deb packaged application to be put in the Ubuntu app store/repository/archive  unless it has been code audited and that can take some time.

You can even have your own store/repository/archive for the snap apps you create.

Regards

---

### Post by slickymaster on 2021-08-27
Thread moved to **Packaging and Compiling Programs** for a better fit

---

### Post by TheFu on 2021-08-27
Raspberry Pi OS installs are really just copying an image file to a microSD storage device and booting.  Raspberry Pis don't have BIOS. That's due to the ARM CPU architecture.  After booting from the image, I've seen all sorts of setup programs - mainly they just configure the software.  The OS itself is just an image of a working system that knows to use DHCP for initial networking.

Canonical makes a number of different images and management methods available for embedded software devices.  Perhaps reading up on Ubuntu Core which is an IoT management system would be good?  This expects all packages to be snap-based and will do automatic updates when the snaps are released.  For a hands-off device, this could be better than the old Ubuntu Server/Desktop management method running apt-get/apt/aptitude.  The downside to Ubuntu Core is that to distribute packages, you HAVE to use snaps and Canonical is the only "store" distribution available.  I've never seen anyone else create a snapstore, though Canonical claims it is possible.

BTW, don't use raspberry pi hardware if you want 24/7/365 devices.  Splurge for industrial hardware.

---

### Post by tc2020 on 2021-08-27
Thanks for all inputs so far. 

I had a look at Snapcraft, Flatpak, AppImage and debian. The first two appear to be app stores (like Google Play) for developers to pack their apps in certain ways (per their store guidelines) for Linux variants. I do not really know how those would help me.

This application software is for our own custom hardware from which we plan to produce embedded devices. In the beginning, we built SD card for RPi4B with Ubuntu Server 20.04LTS image via Raspberry Imager software tool. Plug this SD card in RPi4B and it boots. We then added device tree overlays that adapt to our custom hardware board. Once working, we started developing various software modules to perform specific applications. Many of them run as services. During this development, we installed many Ubuntu/Linux packages (such as Apache2, Python, logrotate, syslog-ng, net-snmp, etc...) in addition to what already installed/available in the initial/fresh Ubuntu image. Also, during development, we edited many config files (e.g.. syslog-ng.conf, snmpd.conf, logrotate.conf, ssmtp.conf, etc...). At this point, we have files that spread across many places. On top of this, for every kernel update, the system breaks because the update installs files over our modified versions such as overlays *.dtbo files.

Our prototype software works and we are about to pack this software and turn it into a pre-release version for regression testing and so on. I plan to start with a fresh Ubuntu on SD card, install software package by package, copy file by file to the card and hope I would not miss anything. This is an error prone approach. I would like to know if there are guidelines/checklist established somehow somewhere for this process. Are there tools/techniques to handle this and also to handle install/remove/backtrack software upgrades (our software upgrades as well as kernel/packages updates/upgrades) once it's out there?.

On RPi4 hardware, I could not resist so I added a few hardware features to harden it for 24/7/365.

---

### Post by TheFu on 2021-08-27
Snaps automatically update and are self-contained for all the dependencies, so they can run on any Linux OS with a compatible architecture.  Snap packages were the outcome of the Ubuntu-Mobile project (I think), which makes them great for similar hardware needs, but when the underlying OS is just "linux", not exactly kernel 5.4.11-x.y.z.1  Pretty much and Linux running kernels from v4.15 - 6.x should work with those packages ... assuming CPU compatibility.  The real great thing is that updates for each package are auto-installed and the only way to disable that is by network blocking.  Snaps typically retain 3 versions of each package. 2 is the minimal under our control, but it is possible to come in after the fact and delete all but the latest snap package for each version.  Additionally, snaps run inside a little sandbox - almost a container, but not quite.  It is strong separation than the OS provides, but less than what a full Linux container provides.  Different software in different snaps has to be configured by the package creator to allow other programs/libraries/tools to have access.  For example, the VLC program snap package didn't initially allow some addons to work, until the snap package creation team setup permissions for the sandbox to allow it.

The great thing about snaps is that only the parts that have to be updated would be updated, not the entire image. If you only plan to have 500 installs, perhaps an image update where you ship out new microSD cards for every release is fine.  If you will have 10,000-20M installs, that just won't work.

This drives me crazy, but I appreciate when my roku auto-updates and I never need to worry (much) if I'm running the current version. That's all handled for me.  

You might want to use Linux containers, like Docker for each daemon. This will have minimal overhead, but keep the dependencies separate for each tool.  With docker, there are all sorts of build tools, plus becoming fluent in docker with aid your marketable skills and add to buzzword compliance on your resume.

If you want to do things consistently, script it.  This can be simple bash scripts, python/perl/ruby/golang scripts or you can use devops tools to accomplish it. Using a devops tool just means that other people will be able to more quickly understand what it being done without the "scary" script-written-by-someone-else.  I use both.  The key is being consistent and always improving the process. When issues arise in the image creation, fix it in the image build so it never happens again.

Most people start with a text file and commands to run. That becomes a bash script.  When it gets too complex, they will switch to some other language.  I wrote my first cross-platform installation Bourne Script in the early 1990s.  That was used to install software around the world for thousands of workstations used by many different govts.  Consistency is key.

I'd look into using SSDs rather than microSD storage if you don't want a dead SD storage device every year too.

---

