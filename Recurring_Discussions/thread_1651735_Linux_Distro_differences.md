---
title: "Linux Distro differences?"
date: 2010-12-23
forum: Recurring Discussions
---

### Post by CP2 on 2010-12-23
Hey all. I will soon enough begin my journey into the Linux world at home. A question came to mind though. I initially thought about using ubuntu on my project computer, but then I thought that if Linux in general was so Open then what are the differences in the different distros of Linux? Ubuntu is probably the most popular, but I've been hear about all these other distros (Yellow Dog, Mint, etc.)  Do all these different distros have specific functionality tailor made for certain types of people?  and then you can trim or buff the distro as you see fit?

---

### Post by oarion7 on 2010-12-23
You're probably going to get a spectrum of different answers to this question from different people. I would say there are a number of different reasons why to pick one distribution over another, but when you are new to Linux the only difference that is relevant is ease of use. You don't want to start out using a distribution that is tailored towards advanced, long-term Linux users, although you may be perfectly happy and comfortable using such an OS after several months of transitioning via Ubuntu or Mint.

I think for now, the question you want to be asking, other than the very important question as to hardware compatibility, is which distribution makes the easiest transition to Linux from, I'm assuming, Windows. Of course, ease of transition and ease of hardware compatibility, ideally, should come hand-in-hand, and this will general lead you towards starting with Ubuntu. Or Mint, or even something else. I think Ubuntu is a great start. 

And as I've stressed before, just because Ubuntu is easy to get used to doesn't make it inferior to other distributions in really any way. Unless you're trying to run Linux on old hardware or really need to conserve energy or something. The more used to it you get, the more you can make it your own.

EDIT: Don't forget to take the size of the online community available for support into consideration as well!

My two cents, feel free to disagree.:p

---

### Post by WorMzy on 2010-12-23
The main differences between distros are: 1) the package manager they use, and 2) the desktop environment they come with.

For package managers: Ubuntu, Mint, and other Debian-based distros use dpkg, with apt as a front-end. Gentoo uses portage, with emerge as a front-end. Arch uses pacman. Fedora uses rpm, with yum as a front-end. Suse uses rpm with yast as front-end. Etc.

For desktop environments: Ubuntu, Mint and Debian all use GNOME by default, as does Fedora. Gentoo and Suse use KDE. Arch doesn't come with one. LXDE and XFCE are two other popular desktop environments.

Ubuntu is very new-user-friendly, but it's not as popular with established Linux users as it takes a lot of flexibility away (presumably) in order to be more stable and harder to bork; it also has a really strong community of users (e.g. this forum) to help people who experience problems. Arch gives you a lot more freedom, but gives you little to nothing out-of-the-box -- just the bare basics -- it's up to you to install what you want, and indeed, what you need. Debian, like Ubuntu, is user-friendly; it also gives you more freedom than Ubuntu, but at the cost of less frequent updates. I can't really comment on the other distros, as I haven't used them enough to garner an opinion.

TLDR: Ubuntu is a good first step into the world of Linux; but you may find it's restrictions tiresome after a while and switch to a different distro.

---

### Post by CP2 on 2010-12-23
Thanks for the responses mates. I'll say this to set the environment for you:

1. This will be a project/gaming computer. Dual booted Linux/windows(game part) I want to test/expand my linux skills on this computer. For career progression and freedom to do what I want with an OS.

2. I am building a computer from scratch. Not the best parts, but the more bang for your buck parts.

3. I want flexibility and compatibility. Can I get both with a not so popular version of Linux? I could do the research through this and other forums and see what hardware parts jive well with Linux

Comments?

EDIT: Partitioning hard drive where there is a DATA partition would be no problem when it comes to different linux distros accessing and running the DATA correct?

---

### Post by WorMzy on 2010-12-23
For compatibility, in my experience one linux distro is as good as another. Ubuntu certainly tries to make this easier for you by alerting you to available drivers (e.g. nvidia drivers if you have an nvidia graphics card, printer drivers if you connect a printer to your PC, etc), but these drivers are available on most (if not all) Linux distros.

For flexibility: Ubuntu will suit most of your needs as a newbie; it's only when you try to change "core" programs, or when you try to trim down your install size by removing unwanted applications, that Ubuntu starts to show it's weaknesses. If you want complete control over what applications you have installed, Ubuntu isn't the distro for you, and you should consider something like Arch or Gentoo instead; but if you don't care about unwanted applications taking up hard-disk space, then Ubuntu will be fine.

Regarding the DATA partition: You can store user data on a shared partition, but not installed applications. An NTFS partition is generally recommend for sharing data between Linux and Windows, instead of accessing the Windows installation partition from Linux, or the Linux partition from Windows.

---

### Post by CP2 on 2010-12-23
> **WorMzy said:**
> For compatibility, in my experience one linux distro is as good as another. Ubuntu certainly tries to make this easier for you by alerting you to available drivers (e.g. nvidia drivers if you have an nvidia graphics card, printer drivers if you connect a printer to your PC, etc), but these drivers are available on most (if not all) Linux distros.

For flexibility: Ubuntu will suit most of your needs as a newbie; it's only when you try to change "core" programs, or when you try to trim down your install size by removing unwanted applications, that Ubuntu starts to show it's weaknesses. If you want complete control over what applications you have installed, Ubuntu isn't the distro for you, and you should consider something like Arch or Gentoo instead; but if you don't care about unwanted applications taking up hard-disk space, then Ubuntu will be fine.

Regarding the DATA partition: You can store user data on a shared partition, but not installed applications. An NTFS partition is generally recommend for sharing data between Linux and Windows, instead of accessing the Windows installation partition from Linux, or the Linux partition from Windows.

Interesting. I stumble upon [www.distrowatch.com](www.distrowatch.com) and was overwhelmed by the amount of linux distros available. I don't know why i was so surprised though. In the cyber age there are bound to be thousands of linux aficionados out there lol. 

Looking at that web site made my decision a bit harder. But I shouldn't make a pure decision. I should just download a group of them and then just run them from an external drive. Or I can run different ones from different USB flash drives.

---

### Post by bodhi.zazen on 2010-12-23
*Thread moved to **Recurring Discussions**.*

About 80-85% or so is the same across distros.

The major differences are, IMOH, package management (apt vs rpm vs pcman vs emerge vs slaptget vs well the list goes on vs none).

Other then that there are (minor) differences in the config files (names, locations, syntax). 

Nothing the man pages can not fix :twisted:

---

### Post by CP2 on 2010-12-23
> **bodhi.zazen said:**
> *Thread moved to **Recurring Discussions**.*

About 80-85% or so is the same across distros.

The major differences are, IMOH, package management (apt vs rpm vs pcman vs emerge vs slaptget vs well the list goes on vs none).

Other then that there are (minor) differences in the config files (names, locations, syntax). 

Nothing the man pages can not fix :twisted:


Ah ok, when I get more into the uses of Linux then the package management might make more sense. As of now, I don't currently have a distro so I can't speak on it. I think another poster also said he same thing as you did. 

Alright, I'll get stop asking all the dumbness until I get my hands on a distro.

---

### Post by WorMzy on 2010-12-23
Yeah, I think that hands-on experience is the best way to decide which distro is best suited to you. LiveCD/USBs are great for trying out a distro before "taking the plunge" as it were.

---

### Post by johntaylor1887 on 2010-12-23
> **CP2 said:**
> I could do the research through this and other forums and see what hardware parts jive well with Linux

Comments?


Check out [www.phoronix.com](www.phoronix.com) They review hardware with the linux user in mind.

---

### Post by oldfred on 2010-12-24
If you have a good sized USB flash drive you can run many different Linux as live installs from the one flash drive. It will not run as fast a a full install to a hard drive but will let you test drive.

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

If you have room on your hard drive, you can create many root partitions of 10-20GB. If you have the separate /Data partition then you can have the same data linked into each install. As suggested above if dual booting with windows you will also want a NTFS shared partition. You can share swap, just do not try hibernating, but should not share /home as each distribution may have different settings. (Ok you can share the a /home partition but then have to have different users for each install, which to me defeats the purpose). If you move all data out of /home, it does not get very large as it just has the hidden user settings and folders. I even move some hidden (data) folders to my Data and /home is less than 1GB, so it is easy to backup.

---

