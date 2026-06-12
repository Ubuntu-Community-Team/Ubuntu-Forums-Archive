---
title: "Xubuntu too slow in Toshiba Libretto L2"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by redification on 2008-08-04
Dear experts,

I know my Libretto L2 may be too outdated but I really want it revive under the god of Linux.

I have limited knowledge of Linux but I luckily encountered some guy from the web that taught me to boot the Libretto via PXE and I can install Hardy through network installation into the Libretto L2, some spec of it are:

Crusoe 600MHz CPU
128MB ram

I choose xubuntu, having been told that xfce is lightweight.

And I stumbled into two problems:
1) It is just too slow to start up or to load any application in xfce, is it because I have 128MB ram only? (I've tried to find the MicroDIMM PC100 SDRAM in computer store but they are too old to be found, or as expensive as a new notebook)
The same notebook can run winME with acceptable speed, and I wish for ubuntu there are ways to further trim down the OS/windows manager to make things run faster?

2) I cannot reconfigure the video setting for X environment, it is defaulted to 640x480 but my Libretto L2 has 1280x600 resolution. I googled for solution and found a command like:
dpkg-reconfigure xserver-xorg
I tried but it asked for my keyboard configuration only, never got the chance to touch the video setting.

Best regards,
Red

---

### Post by Paqman on 2008-08-04
> **redification said:**
> is it because I have 128MB ram only? 

Most likely, yes.

You can see if the system is chewing up your RAM by using the System Monitor. It'll show how much RAM and swap is being used at any one time. The system uses swap when it's running low on RAM.

---

### Post by snowpine on 2008-08-04
Hi Redification, your experience is not unique to the Libretto; many users with older hardware are experimenting with alternatives to 'vanilla' Xubuntu. I think you'll find this thread instructive: [http://ubuntuforums.org/showthread.php?t=873112](http://ubuntuforums.org/showthread.php?t=873112)

---

### Post by redification on 2008-08-05
> **snowpine said:**
> Hi Redification, your experience is not unique to the Libretto; many users with older hardware are experimenting with alternatives to 'vanilla' Xubuntu. I think you'll find this thread instructive: [http://ubuntuforums.org/showthread.php?t=873112](http://ubuntuforums.org/showthread.php?t=873112)

Thx for the info. I am planning to remove xubuntu Desktop and install fluxbox instead, are the following 2 command sufficient?

sudo apt-get remove xubuntu-desktop
sudo apt-get install fluxbox

I followed the link to
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

It mentioned that xubuntu run well at 64MB ram, is it accurate?

Best regards,
Red

---

### Post by mikjp on 2008-08-05
> **redification said:**
> 
The same notebook can run winME with acceptable speed, and I wish for ubuntu there are ways to further trim down the OS/windows manager to make things run faster?

You have to trim down the services running in the background, not only the user interface. You probably dont need things like bluetooth, CUPS, seven virtual terminals etc...

Remember also that you should run only lightweight software: Abiword instead of OpenOffice.Org etc.

You might also try some lighter distro, like Zenwalk.

Greetings,

mikko

---

### Post by kerry_s on 2008-08-05
> **redification said:**
> Dear experts,

I know my Libretto L2 may be too outdated but I really want it revive under the god of Linux.

I have limited knowledge of Linux but I luckily encountered some guy from the web that taught me to boot the Libretto via PXE and I can install Hardy through network installation into the Libretto L2, some spec of it are:

Crusoe 600MHz CPU
128MB ram

I choose xubuntu, having been told that xfce is lightweight.

And I stumbled into two problems:
1) It is just too slow to start up or to load any application in xfce, is it because I have 128MB ram only? (I've tried to find the MicroDIMM PC100 SDRAM in computer store but they are too old to be found, or as expensive as a new notebook)
The same notebook can run winME with acceptable speed, and I wish for ubuntu there are ways to further trim down the OS/windows manager to make things run faster?

2) I cannot reconfigure the video setting for X environment, it is defaulted to 640x480 but my Libretto L2 has 1280x600 resolution. I googled for solution and found a command like:
dpkg-reconfigure xserver-xorg
I tried but it asked for my keyboard configuration only, never got the chance to touch the video setting.

Best regards,
Red

try debian xfce4, also that "dpkg-reconfigure xserver-xorg" will still work in debian etch, so it should be easy to set your screen.
[http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-xfce-CD-1.iso)

---

### Post by meborc on 2008-08-05
> **redification said:**
> Thx for the info. I am planning to remove xubuntu Desktop and install fluxbox instead, are the following 2 command sufficient?

sudo apt-get remove xubuntu-desktop
sudo apt-get install fluxbox

I followed the link to
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

It mentioned that xubuntu run well at 64MB ram, is it accurate?

Best regards,
Red

xubuntu-desktop is just a metapackage, removing it will change nothing... but you can install fluxbox in parallel, and choose from the login interface which desktop environment you want to use

BUT it will still boot slow... i would go for reinstall of nubuntu or fluxbuntu

---

### Post by hyper_ch on 2008-08-05
with 128 mb ram you might want to try a different distro that is lighter. Debian with Xfce could be an option and it's also very much like Ubuntu (ubuntu is based on debian).

Maybe Arch would also be an option or then a real lightweight sytem like DamnSmallLinux or PuppyLinux or FeatherLinux.

OR if you can add a bit more ram. Another 128 MB or even 256 MB will make a huge difference.

---

### Post by Hallvor on 2008-08-05
> **redification said:**
> Dear experts,

I know my Libretto L2 may be too outdated but I really want it revive under the god of Linux.

I have limited knowledge of Linux but I luckily encountered some guy from the web that taught me to boot the Libretto via PXE and I can install Hardy through network installation into the Libretto L2, some spec of it are:

Crusoe 600MHz CPU
128MB ram

I choose xubuntu, having been told that xfce is lightweight.

And I stumbled into two problems:
1) It is just too slow to start up or to load any application in xfce, is it because I have 128MB ram only? (I've tried to find the MicroDIMM PC100 SDRAM in computer store but they are too old to be found, or as expensive as a new notebook)
The same notebook can run winME with acceptable speed, and I wish for ubuntu there are ways to further trim down the OS/windows manager to make things run faster?

2) I cannot reconfigure the video setting for X environment, it is defaulted to 640x480 but my Libretto L2 has 1280x600 resolution. I googled for solution and found a command like:
dpkg-reconfigure xserver-xorg
I tried but it asked for my keyboard configuration only, never got the chance to touch the video setting.

Best regards,
Red

Try adding more RAM and try a different distro. (Xubuntu isn`t that light.) TinyMe, Feather Linux, Puppy Linux and such should run - not fast, but they will run.

---

### Post by snowpine on 2008-08-05
> **redification said:**
> Thx for the info. I am planning to remove xubuntu Desktop and install fluxbox instead, are the following 2 command sufficient?

sudo apt-get remove xubuntu-desktop
sudo apt-get install fluxbox

Best to add fluxbox first, then remove xubuntu later once you're sure everything works (unless you are desperately low on hard disk space). You can choose between them at login by choosing sessions. I am not 100% sure, but I think that using Synaptic to mark xubuntu-desktop for complete removal is what you want to do (keeping in mind it will remove most of your applications as well). You could also use 'sudo aptitiude remove xubuntu-desktop' but I think that only works if you installed it using aptitude?

> **redification said:**
> I followed the link to
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

It mentioned that xubuntu run well at 64MB ram, is it accurate?


No, Xubuntu 8.04 definitely does not run well with 64mb--see the link in my previous post. :)

---

### Post by halitech on 2008-08-05
I've got a similiar laptop setup, Compaq Armada M700 (P3 750, 192meg of Ram) and Xubuntu isn't too bad after trimming the services you don't need but with the slightly slower machine and only 128meg of ram, don't think even trimming services will help much. If you want to stick with something similiar to Ubuntu, go with the base install of debian and then add XFCE (I'd do it on mine but cd rom is toast and I don't want to go through the netinstall again for a slight increase) or try one of the lighter distros like puppy, arch or dsl.

---

### Post by redification on 2008-08-05
Thx again for the suggestions

I am now trying using awesome windows manager, and it's quite awesome.

Also firefox takes quite long to launch but the experience is still acceptable.

Now I still have the problem of "dpkg-reconfigure xserver-xorg" didn't prompt me to reconfigure the video setting (default to 800x600 now).

A little browse through the web reveal that this is intentionally disabled in Hardy distribution, nor did the displayconfig-gtk work now, so.. how may I configure the libretto 1280x600 screen?

---

### Post by snowpine on 2008-08-05
Two of my favorite browsers that are faster than Firefox are Epiphany (very similar) and Kazehakase (quite unique).

---

### Post by sleepingdragon on 2008-08-05
You might want to have a look at Dream Linux, i had it running on a 633Mhz, 128Mb RAM machine. OK, it didn't break any speed records, but the performance was acceptable - and it has a beautiful desktop. 

You can find Dream by clicking [here]("http://www.dreamlinux.com.br/index.html")

Don't forget to pick the XFCE version!

---

### Post by redification on 2008-08-06
Thx for the information, I didn't realise there are su many lightweight linux distribution out there. I would try them after I have enough time and experiences with Linux platform.

I would stick with ubuntu for a while first, because it is the only system that I found easy PXE installation support, and also the apt-get type package installation tools (please correct me if this is common features to other distribution too)

I finally get the libretto 1280x600 video setting working. The problem with the default setting is that it query the BIOS for video setting support and override any user configuration in xorg.conf. So the modification I made are:

1. use gtf 1280 600 60 to generate a Modeline compatible with the libretto and add it in Monitor section of xorg.conf
2. add a line Option "UseBIOS" "false" to the Device section

whola! wide screen is up now, next quest is to set the audio. ~_~

---

### Post by mikjp on 2008-08-06
> **redification said:**
> I would stick with ubuntu for a while first, because it is the only system that I found easy PXE installation support, and also the apt-get type package installation tools (please correct me if this is common features to other distribution too)

Also Debian uses apt-get as package installer, but openSUSE's zypper and Fedora's yum are equally useful tools that take care of dependencies.

Greetings,

mikko

---

### Post by dmiller40 on 2008-08-07
I also have a laptop w/ similar specs, 600mhz w/ 128mb of ram. And I also have to install via PXE boot. The problem is Ubuntu is the only distro i can find to netboot.

Any suggestions on how to move to a lighter distro from ubuntu or how to PXE netboot a lighter distro?

thanks
dm

---

### Post by mikjp on 2008-08-08
* Debian: [http://wiki.debian.org/DebianInstaller/NetbootPXE](http://wiki.debian.org/DebianInstaller/NetbootPXE)
* Gentoo: [http://www.gentoo.org/doc/en/altinstall.xml](http://www.gentoo.org/doc/en/altinstall.xml)

But you can also install another distro to another partition from an an existing installation. 

* [http://www.gentoo.org/doc/en/altinstall.xml](http://www.gentoo.org/doc/en/altinstall.xml)
* [http://www.debian.org/releases/stable/i386/apds03.html.en](http://www.debian.org/releases/stable/i386/apds03.html.en)


mikko

---

### Post by meborc on 2008-08-08
> **snowpine said:**
> Best to add fluxbox first, then remove xubuntu later once you're sure everything works (unless you are desperately low on hard disk space). You can choose between them at login by choosing sessions. I am not 100% sure, but I think that using Synaptic to mark xubuntu-desktop for complete removal is what you want to do (keeping in mind it will remove most of your applications as well). You could also use 'sudo aptitiude remove xubuntu-desktop' but I think that only works if you installed it using aptitude?

ok, just to make this really clear, metapackages are packages that are needed to install a lot of programs that all together make up something like xubuntu (or any other) desktop... so they depend on a lot of packages... if you install the metapackage, all those packages get installed too... BUT no program depends on the metapackage itself... if you remove it, nothing gets removed except the metapackage... there is an exception and that is when installing metapackages through aptitude... this does not apply here as xubuntu was installed from a cd image / net image

more info [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by dmiller40 on 2008-08-08
mikjp thanks for the info!!!!

My question is will debian + xfce be any better than xubuntu? Also I've really only used ubuntu, so dont know much about gentoo. Which do you think would run better?

thanks again
dm

---

### Post by mikjp on 2008-08-08
AFAIK Debian does not run as many services by default as Ubuntu does. At least it used to be lighter than Ubuntu, nowadays things have slightly changed, as even Debian automounts USB drives :shocked: 

greetings,

mikko

---

### Post by redification on 2008-08-16
Dear friends,

After some struggle I finally got video (1280x600) and sound working in Libretto L2 with ubuntu.

I also tried using wine and play fallout 2 with it, it requires 640x480 fullscreen mode.

Then I have problem here, the machine cannot switch to 640x480 full screen correctly, half of the screen move outside the bottom monitor border, and the aspect ratio is incorrect (vertically too long)
 
However, the 1280x600, 800x600 mode are fine. I am still struggling with this issue. 

Cheers!

---

