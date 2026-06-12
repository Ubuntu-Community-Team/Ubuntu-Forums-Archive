---
title: "cannot do many a things"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by ashwinipn on 2008-08-05
Hi,
I am new to Ubuntu/Linux/Nonwindows OS and yearning to wean myself from Windows for obvious reasons. I have installed Ubuntu 8.04 64 bit onto my system. But I face many a problems when it comes to usability. I am not talking about usual office suit etc. These get done easily. But other useful and regular usages include, watching online streaming videos/TVs on Mozilla Firefox, using various softphones, hardware supports.... (specifically Realtek HD audio 889A and Creative webcam Live Ultra), Wine installation and compatibilities, etc. Wine has been installed but when I try installing other application of windows, despite of the apparent suggestion that the applications have been installed, they don't work. Even included applications such as Ekiga softphone can call a google talk user, but there is no sound from either side. I am not sure that with 32 bit OS also, this problem will be solved or not.
Initially Firefox 3 prompted to install flash players (multiple) when I tried watching online videos. After installing one of the plug-in flash player, never received another prompt for installing other missing plug-ins. But still videos won't work. Tried installing different applications like VLC media player etc. without success. Although the current version of Ubuntu has done a tremendous job of simplifying OS installation, it has to do a lot to make it work for common people. I am a person with the fairly OK knowledge of hardware and installations and troubleshooting (in Windows environment) and I find these things difficult.... Think of people who want a running a system out of the box. I mean the logical end of the system and application software development is its usability and user friendliness. I wish if these concerns can be taken care of and wish to participate if possible.

---

### Post by snowpine on 2008-08-05
Hi there, welcome to the forums, and your desire to get involved in the community is admirable! :)

Let's go one problem at a time. The Flash video fix is easy. Open a terminal and type: ```
sudo apt-get install flashplugin-nonfree
```

Hope that gets you started on the Ubuntu path!

---

### Post by snowpine on 2008-08-05
ps I agree it would be more "user friendly" to include Flash by default, however, the player is not included in Ubuntu because it is proprietary software. :)

---

### Post by cpetercarter on 2008-08-05
All of these problems are soluble, believe me. But you will need to pick them off a few at a time, and gain confidence in the way that things are done on Ubuntu/Linux.

Start by reading [this.]("http://ubuntutip.googlepages.com/home")

---

### Post by Bucky Ball on 2008-08-05
Hi Ashwinipn. All good advice, but one thing to remember is: Ubuntu is not Windoze. There is a slight brain shift involved so perhaps leave the Wine stuff for a little later until you get a feel for Ubuntu. As mentioned, one thing at a time and you can do pretty much what you would do with Windoze anyhow (if in a slightly more DIY manner!) :)

There was a good point raised about propriatory software earlier; something to keep in mind, but there are usually workarounds. Good luck ...

---

### Post by ashwinipn on 2008-08-05
Thanks for the encouraging words.... at a lightening fast speed... reminds me to keep positive outlook... will do the same as suggested... that one by one...
Thanks once again...

---

### Post by rokytnji on 2008-08-05
A good simple step and starting point is to go Online first and then open System>Andministration>Synaptic Package Manager and open it up. After entering your password and synaptic opens go to Settings and click on repositories. On third party software and Ubuntu software make sure all the boxes are checked.Then hit the reload button. You will get a popup window showing downloading package information. Wait for it to finish and your software repositories in synaptic will be up to date. Other members can probably address your specific problems like ekiga since I don't use it. I know skype works for webcams though and its in synaptic. Most everything you'll need is in synaptic.

---

### Post by suprfish on 2008-08-05
Go to Applications > Add/Remove, then: Show: **All available applications**, Search: **Ubuntu restricted extras**. (Install it). That's it!

---

### Post by Bucky Ball on 2008-08-05
> I wish if these concerns can be taken care of and wish to participate if possible.

Forgot to mention, you are now participating and welcome! Incidentally, it is hardly the fault of Linux developers if hardware and software creators *do not* participate make open source drivers and information available to the open source community. Makes it a little hard to cover every hardware situation 'out of the box' ... :)

---

### Post by ashwinipn on 2008-08-07
Hi,
Thanks very much for the links and suggestions. I, in fact, erased previous installation of ubuntu and reinstalled it again.... this time 32 bit... once become comfortable with it... then would look for 64 bit etc... I followed the instructions given  in the link provided "Tips for beginers with ubuntu 8.04" and found it quite useful... To start with... got the basic idea of folder/file structures, configurations, and organizations within unix/linux environment. I wish this kind of guide gets more and more disseminated among users.... As was suggeted, now with a clean installation, I can do pretty much many a things. However, as predicted, many a things remained to be solved. First, I had enabled Vista (other OS) to to able to boot up with AHCI enabled. After ubuntu installation, I get the error message
"GRUB Loading Stage1.5.
GRUB Loading, Please wait
Error 17
After this none of the OS will boot-up until I change AHCI to Native IDE in the BIOS setup. Please help me to solve this. Moreover, with every update of kernel image, two additional lines get added to the on boot menu, i.e., main updated kernel and recovery mode. Do I have to keep all this or there is any way to remove old kernel images. This will make it easy for boot options.
Apart from this, how to install applications that are not in repositories or can not be searched by add/remove program. As suggested in the "beginners manual" (link provided), avoid manual installations. For example, I want to have skype and the installable file is available on to its website... but synaptic manager or add/remove program is not able to search it... In such case, what to be done...?
DivX streaming does not work... the player (Totem Plugin Viewer 2.22.1) that is called to play this file does not play videos.
How to make Creative webcam Live! Ultra work in Ubuntu?
How my Creative Wireless Desktop 6000 series (USB) would respond while booting up... I can go inside BIOS by pressing "Del" key multiple times ... but after that it becomes unresponsive...
These are few problems among others... all the suggestions are valuable and helpfull...
Thanks in advance...

---

### Post by suprfish on 2008-08-07
quick bump/help

> **ashwinipn said:**
> Hi,
First, I had enabled Vista (other OS) to to able to boot up with AHCI enabled. After ubuntu installation, I get the error message

GRUB Loading Stage1.5.
GRUB Loading, Please wait
Error 17

After this none of the OS will boot-up until I change AHCI to Native IDE in the BIOS setup. Please help me to solve this. 


sorry

> **ashwinipn said:**
> 
Moreover, with every update of kernel image, two additional lines get added to the on boot menu, i.e., main updated kernel and recovery mode. Do I have to keep all this or there is any way to remove old kernel images. This will make it easy for boot options.


In a terminal, enter **cat /boot/grub/menu.lst**; copy and paste the output back here.

> **ashwinipn said:**
> 
Apart from this, how to install applications that are not in repositories or can not be searched by add/remove program. As suggested in the "beginners manual" (link provided), avoid manual installations. For example, I want to have skype and the installable file is available on to its website... but synaptic manager or add/remove program is not able to search it... In such case, what to be done...?


In situations such as this, typically you should find a trustworthy repository that hosts the packages, or you get the package some other way (download from [some website]("http://www.getdeb.net/") etc). For Skype, use [these instructions]("https://help.ubuntu.com/community/Skype").

> **ashwinipn said:**
> 
DivX streaming does not work... the player (Totem Plugin Viewer 2.22.1) that is called to play this file does not play videos.


Do you have gstreamer installed (**Add/Remove**)? Try another player, such as VLC (also in **Add/Remove**).

> **ashwinipn said:**
> 
How to make Creative Webcam Live! Ultra work in Ubuntu?


Those webcams don't work with [linux-uvc]("http://linux-uvc.berlios.de/#devices"), so you'll have a hard time :(.

[http://ubuntuforums.org/showthread.php?t=765638](http://ubuntuforums.org/showthread.php?t=765638)

> **ashwinipn said:**
> 
How my Creative Wireless Desktop 6000 series (USB) would respond while booting up... I can go inside BIOS by pressing "Del" key multiple times ... but after that it becomes unresponsive...


sorry

---

### Post by Bucky Ball on 2008-08-08
Suprfish, that Skype page you suggest is a little out of date. Go to the source:

[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

They now have an easily installable Linux version which works on my machine fine. In the past, getting Skype working was a headache (unless you got lucky!).

When you install a kernel, it installs a recovery kernel (same version) and also the previous kernel version - regular kernel and its recovery kernel. This is in case anything goes really wrong with the latest one - you have the version before it which is known to work (hopefully). Therefore, each new kernel will, as you have found, give you two, not one, new items in the grub.

As for repositories, you need to add them to your software sources. This is only possible if the repository is supported in someway by Ubuntu. If not, manual it is or some other workaround. There is a lot of information about on this but you could start here ...

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

and here:

[http://wiki.flexion.org/UbuntuHardyRepositoryConfiguration.html](http://wiki.flexion.org/UbuntuHardyRepositoryConfiguration.html)

... and this is a good one which will help you install ubuntu-restricted-extras, which may solve some problems regarding 3rd party software/hardware before they arise,...

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good luck and have fun! :)

---

### Post by eddVRS on 2008-08-08
> **snowpine said:**
> ps I agree it would be more "user friendly" to include Flash by default, however, the player is not included in Ubuntu because it is proprietary software. :)

Whilst these can't be included in the OS installation process I wonder if there could be drafted a check list of things to do after a new install. Things like flash, codecs for the media players... I'll look into drafting and posting this but might need some help... thoughts anyone?

---

### Post by sharma2008 on 2008-08-08
yes, he is right

---

### Post by ashwinipn on 2008-08-08
> **eddVRS said:**
> Whilst these can't be included in the OS installation process I wonder if there could be drafted a check list of things to do after a new install. Things like flash, codecs for the media players... I'll look into drafting and posting this but might need some help... thoughts anyone?
that is what I have mentioned earlier... and know what.... in fact there are drafts like this... one of which was given to me as a link by the member named cpetercarter...  you can find it here.... [http://ubuntutip.googlepages.com/home](http://ubuntutip.googlepages.com/home).... Or something like this can be done... we choose user who would compile the draft.... and others would send their inputs from time to time as we solve some puzzles the the designated person... the role of the compiler may be assumed on rotation basis for the sake of sharing responsibilities... And that draft be put on net with the periodic updates..... That link can be promoted as a Beginner's step by step guide or something.... any takers.....

---

### Post by eddVRS on 2008-08-08
ashwinipn- this looks brilliant, and assuming you're still working on it, I'd like to contribute to this if I may.

Something I could have done with knowing about late last year...

---

### Post by ubuntu-freak on 2008-08-08
If the OP, or anyone else browsing this thread is still having issues, take a look at my [how-to](ubuntuforums.org/showthread.php?t=766683). It's command line based, but it's easy and will remove any conflicting packages.

---

### Post by ashwinipn on 2008-08-08
> **ubuntu-freak said:**
> If the OP, or anyone else browsing this thread is still having issues, take a look at my [how-to](ubuntuforums.org/showthread.php?t=766683). It's command line based, but it's easy and will remove any conflicting packages.
Thanks a ton... As a new user, I face problem and any new information is useful to make me adaptive.... after all coming out of the system (dependence, in my case Windows) is never a smooth process...

---

### Post by Bucky Ball on 2008-08-08
Ashwinipn, sounds like you are making the transition and getting into the spirit and idea of the Linux and Ubuntu community just fine. Welcome! Some great ideas and keep 'em coming.  With what sounds like some solid experience in Windoze, that makes the transition easier when you begin to forget a few things embedded in the brain by MS (the corporation, that is!). In fact, most things start to get easier and those bad memories just start to fade away ... lol. Good luck with your explorations ... :)

---

### Post by suprfish on 2008-08-08
> **eddVRS said:**
> Whilst these can't be included in the OS installation process I wonder if there could be drafted a check list of things to do after a new install. Things like flash, codecs for the media players... I'll look into drafting and posting this but might need some help... thoughts anyone?

It is recommended that new users install the meta package '(k or x)ubuntu-restricted-extras'; from it's description:

> Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (gstreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

Another bump/help for OP's remaining problems...

> **ashwinipn said:**
> Hi,
First, I had enabled Vista (other OS) to to able to boot up with AHCI enabled. After ubuntu installation, I get the error message

GRUB Loading Stage1.5.
GRUB Loading, Please wait
Error 17

After this none of the OS will boot-up until I change AHCI to Native IDE in the BIOS setup. Please help me to solve this. 


Try restoring it (grub), if possible, [from a Live CD]("http://ubuntuforums.org/showthread.php?t=224351") after changing to AHCI.

> **ashwinipn said:**
> 
Moreover, with every update of kernel image, two additional lines get added to the on boot menu, i.e., main updated kernel and recovery mode. Do I have to keep all this or there is any way to remove old kernel images. This will make it easy for boot options.


In a terminal, enter **cat /boot/grub/menu.lst**; copy and paste the output back here.

> **ashwinipn said:**
> 
How my Creative Wireless Desktop 6000 series (USB) would respond while booting up... I can go inside BIOS by pressing "Del" key multiple times ... but after that it becomes unresponsive...


:confused:

---

### Post by ashwinipn on 2008-08-11
Quote:
"Try restoring it (grub), if possible, from a Live CD after changing to AHCI."

The problem was solved by the BIOS and other driver updates I applied. Now, it does not show the GRUB stage/s and directly goes to the second stage (i.e., the list of kernel images to boot from). Thanks for the suggestion though. I think relatively new motherboards and chip-sets may come across such issues and periodical updating would be helpful.

About Wireless desktop problem, I suppose it is the power issue and may be solved by the addition of an AC powered USB hub. I have ordered one and waiting to see the results. Although I checked my power supply and found it very good and stable, but for some unknown reason, I face this USB issue. Can anyone give me the idea that if the PSU is sound and healthy, will it still be possible for the system to be underpowered? The reason I am asking is, I have a PSU which claims to give 700 Watts of output. I am no gamer so my actual usages of power remains low (I got the PSU through a deal). When I checked AC power supplied to the PSU, it read 123V. Then I checked all DC powers supplied from it to the motherboard and components, the multimeter read +12.14V, +5.06V, and 3.328V for respective wires (Yellow, Red, and Orange) on the 20/24 pin connector. However, I did not check for the Amps, therefore, won't be able to calculate the wattage output and efficiency.

To be specific, suppose if I have a new and healthy 700 Watt SMPS and my need for the power remains low (integrated HD graphics and Audio, one HDD, one DVD writer, one 28" LCD Monitor, 3-4 wireless USB peripherals, and 5 fans including 2 120 mm, 2 70mm and one CPU fan), would I face power issues of the nature I described above or some other kind?

Quote:
"In a terminal, enter cat /boot/grub/menu.lst; copy and paste the output back here."
I am sorry... could not exactly understand this... Do you mean that I have to delete those older kernel images/lines I don't wish to use?
thanks in advance...

---

### Post by Bucky Ball on 2008-08-11
Try editing grub at boot up.

Where you get the list of kernels, select your ubuntu one and press 'e'. Add this to the end of the line that starts with 'kernel', 

irqpoll

hit return and reboot and let us know what happens.

---

