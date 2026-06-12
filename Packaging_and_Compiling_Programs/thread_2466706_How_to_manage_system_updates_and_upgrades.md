---
title: "How to manage system updates and upgrades"
date: 2021-09-03
forum: Packaging and Compiling Programs
---

### Post by tc2020 on 2021-09-03
Hi,

My application runs Ubuntu Server 20.04 LTS 64-bit server OS. It is an embedded device to be used in an internal and controlled environment with no internet access in most cases. Updates/upgrades of application software as well as kernel/OS are also user controlled, not automatic. What is the best way to manage updates/upgrades in such environment?. 

The following are what I need to work with:

1). My development device is configured with auto daily update/upgrades (in [FONT=&amp]/etc/apt/apt.conf.d/20auto-upgrades)[/FONT], as:  
APT:: Periodic::Update-Package-Lists &#8220;1&#8221;;
APT:: Periodic::Unattended-Upgrade &#8220;1&#8221;;

  The issue I face is that for every kernel update, I need to manually copy all my device tree overlays *.dtbo file to /boot/firmware/overlays because update overwrites my .dtbo files with system default ones. If not, application software would not work because it relies on proper hardware setup. Two scenarios below:

a). If I keep auto unattended upgrade enabled, I assume I can write some script to check kernel version. If newer then copy .dtbo files over.
b). If no auto unattended upgrade, how would you handle such upgrade without internet access?.

2). Following on 1).b. above, how would you upgrade application software?. Right now, I am thinking of a .gz file to send to end users. They can then upload it to the device. Run a command and it will self unzip files to their specific paths.

3). For embedded application like mine, which way is better/more suitable: 
- Use pre-built Ubuntu server 20.04 LTS?
- Build your own OS from the same source files. In this case, how would you upkeep it with updates and upgrades?.

4). Where can I find source files for kernel for Ubuntu?.

Thanks.

---

### Post by TheFu on 2021-09-04
About once a year, an automate patch/update will fail, so I stopped doing that. Beware.

You can reduce the risks, by only doing security patches. I know it is possible, not the exact way, since I run a script manually every weekend to patch all my systems and it logs that.

If I were setting up an IoT device, I'd have commands pulled from my infrastructure by each device.  Each client would have a different ssh-key and we'd have a copy of their public key.  Then they could ssh into our infra on whatever port we decide for specific commands. to be used and any other settings we want to have about the devices. That way, I could test the patches before my devices get any.  Let the clients decide which day of the week they patch - I'd want Saturday, but I could see lots of people NOT wanting to be hassled over a system failure all weekend long. They might choose Thurday or Monday instead.

For automatic kernel module rebuilds, search on dkms.

You can get the source for nearly all the software on your Ubuntu system through APT. Google easily finds that answer.  I think there are source packages, but don't recall the exact naming convention. It is based on the normal package name.

If there isn't any internet connectivity, then you'll need a per-update or subscription solution, since you'll be shipping microSD/storage devices out that will need scripting.  You'll probably want to do the updates like off-line Ubuntu systems have done since the beginning with CDROMs.

---

### Post by tc2020 on 2021-09-04
In my case, I would like to implement a solution to upgrade the devices remotely, so no physical swapping of uSD card. These devices are not connected to the Internet but are on internal network. To upgrade, I would electronically send an upgrade zip file to the users. They then upload it (via network) to the devices for self-installed upgrade on user command, via shell or Web page. In the device, I would have a utility that would unzip the uploaded upgrade file and copy files according to their paths. This part can be easily done. 

My challenge is where to get all those security patches, how to bundle them into an upgrade package (what format are they in?), how to install them?. 

I will look into dkms to see what it is. 

For Linux packages, I am thinking of using apt download-only and collect all those packages that I use. Bundle them together and install them in remote devices in /var/cache/apt/archives/ [FONT=arial]then apt install.

For kernel build, if I get it from kernel.org, can I use it with Ubuntu OS since its kernel may not be the same (or is it the same?)?. It says Linux 5.4.0-1042.


[/FONT]

---

### Post by TheFu on 2021-09-04
I'd use tgz, a Unix-native format that can deal with all sorts of things ZIP cannot. It is probably best for self-packaged stuff. 

If you need for APT to know about the updates, then use apt techniques.  Setup a local repo, probably outside /var/lib/apt/ ... I'd lean towards /opt/, but that's my preference for commercial support stuff.  Look at how optical storage is used to upgrade an OS in Ubuntu - just point to that repo in /opt/somewhere/ like they do for /cdrom/ based repos. You could have the customer expand the tgz there as part of your install script.  Then it would end up in /var/lib/apt ..... though approved methods.

Google "ubuntu kernel source" - lots of *.ubuntu.com information.

Almost all Ubuntu packages are .deb format.  That's a standard, documented on the debian.org site.  

If you use Ubuntu Core, then there will be challenges since those use snap packaging and I have no idea how or if it is possible to patch those without an internet connection.  Snap packages have infiltrated Ubuntu 20.04 and later.  Most packages are available as .debs still (without all the dependencies that APT handles), but a few are not and Canonical's repos only provide snap packages.  For example, LXD and Chromium.  Chromium has other people creating PPAs with .deb packages, so that isn't hard to avoid, but LXD does not - last time I checked.  

If you have multiple, self-contained, daemons, consider using some sort of Linux container like LXD to reduce the dependencies from the hostOS.  For example, if your setup begins with a single version of a DBMS and 1 version of a scripting language for the webapp, over time those will diverge just because that's what happens.  I have a VM that started out with 3 related, but disconnected webapps. They all used the same php and dbms, but 3 yrs later and now I have 3 php versions and 2 dbms versions because the different project teams don't care which OS I'm running and the normal versions of those tools provided on that release.  Now I'm going to migrate the webapps to separate containers for the php dependencies and setup different DBMS servers to provide the specific, latest, version supported by each webapp.  Live and learn.  

At least I'm running them in a separate VM now and not on a single OS. That would never have worked. Learned that lesson back around 2006-ish.  I always VM stuff. It has worked well, but linux containers are 10-100x lighter than a full VM.  Just need to be careful about picking a container management system that doesn't prevent some OS services that are needed.  For example, I don't think docker can support ipset firewall rules.  That's a trade off with that container type.  Lxd can.  A full VM can too.  LXD probably isn't as light as docker, but it is about 90% there. Much faster/lighter than a full VM.  I can feel the performance difference, both in service speed and at a shell, if that makes sense. I suppose docker has a lighter storage requirement than lxd, but lxd is still very light compared to a small VM.  Both my lxd containers are under 1G in size.  I think the smallest Ubuntu Server would be about 4G.

Two email gateways here.
[LIST]
[*]lxd container is 650MB
[*]KVM VM is 4.5G
[/LIST]
I'll be powering down the KVM gateway within a month or so.  Need to ensure there's a fall-back until I get the redundant gateway inside a containers on a different box with a different IP.

---

