---
title: "How does program installation work on Ubuntu?"
date: 2019-02-04
forum: New to Ubuntu
---

### Post by ocelot79 on 2019-02-04
I may switch from Windows to (K)ubuntu 18.10 in the near future. I haven't used a Linux distro extensively before and I'm not sure what is different regarding program installation. I know about Ubuntu's built-in software tool, that some programs designed for Windows require WINE to work and that downloading programs can be done from the terminal and the respective repositories. I still don't know 

* What happens with older versions? Example: [https://www.videolan.org/vlc/download-ubuntu.html](https://www.videolan.org/vlc/download-ubuntu.html) . If I use Kubuntu 18.10, what happens when I install VLC released for Ubuntu 18.04? Will it definitely work/not work? Does it depend on the program? If so, should I use an older version of Ubuntu instead?

* What is the equivalent of .exe in Ubuntu? If so, should I use that instead of terminal commands?

* What happens if I install a program designed for Debian/Mint? Will it work because Ubuntu is based on Debian? Are all programs designed for e.g: Arch incompatible with Ubuntu? Is there any compatibility between Linux distros?

* Sometimes uninstalling programs on Windows leaves some stuff behind, such as folders and registry entries. Does the same thing happen on Linux? If so, how do I remove a program in it's entirety?

* How well do Windows programs work with WINE in general? Will I have to tinker with WINE a lot to make such programs work properly or is it something I can install and forget? Should I use WINE to open .exe files?

* Does most software lag behind in terms of updates?. For example, VLC is version 3.0.6 on Windows, should I expect it to be 3.0.6 and updates as regularly on Ubuntu as well?

* Is there anything else I should know beforehand?

Thank you in advance.

---

### Post by Impavidus on 2019-02-04
That's a long list of questions and you can expect a long list of answers.

* If you use Kubuntu 18.10 and install vlc from the Ubuntu repositories (all flavours use the same repositories), you'll get a version of vlc compiled for Kubuntu 18.10. If you use Kubuntu 18.04 and install vlc the same way, you'll get a version compiled for 18.04. It will be a slightly older version, but it will work. Using a PPA (an alternative repository) you can get the latest version of some software, compiled for older, still supported releases of Ubuntu, and if the PPA is properly maintained, it works. If not properly maintained, it may not work.

* Filename extensions are optional in Linux. Some applications use them, many humans use them, but to the OS they're just part of the filename. Most executables have no filename extension.

* If you're installing a pre-compiled binary, it will only work if it was linked to compatible versions of libraries or was statically linked (meaning more portability, but also more disk space and reinstalling the entire program to install a patch in a library). You can have multiple versions of the same library installed at the same time, but that's not so easy to manage. More closely related Linux systems are more likely to be compatible, as long as you use a version released around the same time. If you're installing from source code and compile yourself, it tends to work, but you have to manage everything manually, which is something I wouldn't recommend to most users. The easy way is to install everything from the official Ubuntu repositories.

There are also snap packages, which is a new way to package software for Ubuntu. The packages are self-contained, so more portable and they have some security advantages. They also have some disadvantages.

* If you installed software using the package manager, you can remove it using the package manager. When you use the option to purge, no trace of the program should be left, except user config files in the user's home directory. Those have to be removed manually. Of course, there are bugs, so it may not always work.

* Sometimes it works in wine, sometimes it doesn't. If you can, try a native Linux alternative. I've never used wine in 12 years of using Ubuntu. See the appDB at [https://www.winehq.org/](https://www.winehq.org/) for other user's experiences with your favourite Windows software. If you need a lot of Windows software, use Windows.

* Whenever a version of Ubuntu is released, the versions of most applications in de repositories are frozen. If Ubuntu 18.04 comes with foo 4.3, then Ubuntu 18.04 will still provide you with foo 4.3 in three years time, when Ubuntu 21.04 will provide you with foo 4.9. There are some exceptions, like Firefox, which is regularly updated to the latest official version, usually just a few days after release. Most packages will get important bug fixes though, which are backported into the versions in the repositories. If you want the latest version of some software, either use the interim releases of Ubuntu or install them from a PPA. Note that latest also means less stable.

If you have more questions, consider making a separate thread for each question.

---

### Post by CatKiller on 2019-02-04
I'd also add that the OP shouldn't dive in with 18.10. 18.04 would be a much more sensible choice, because of its Long Term Support.

---

### Post by oldrocker99 on 2019-02-04
> **CatKiller said:**
> I'd also add that the OP shouldn't dive in with 18.10. 18.04 would be a much more sensible choice, because of its Long Term Support.

+1 on that. The equivalent to Windows .exe installation files in Ubuntu are .deb files. Different distros differ mostly in how they install software.

To install from the terminal, first try this:```
sudo apt update
sudo apt upgrade
```

That will show you the way that Ubuntu installs software. Being able to install software, which is SAFE, unlike some Windows .exe files, from the terminal is one of the joys of using Linux. Of course, you do need to know the name of the program. The program which has the entire, huge collection of software for Ubuntu, much bigger the the Software app, is Synaptic, the program which was preinstalled on 8.04, when I started. And, to install it:```
sudo apt install synaptic
```

Synaptic categorizes the repositories in types of software, making it easy to find what you're looking for.

Good luck!

KDE is somewhat resource-intensive. Ubuntu MATE (MAH-tay) has an introductory Software Boutique, making a selected collection of some of the best programs. It is lightweight, and can look like Windows (or KDE, for that matter) Mac, and even Unity. I consider Ubuntu MATE to be the best distro I have ever used, and I've done some distro-hopping over the years.

The "sudo" command gives you temporary Super User abilities, which are required to install or remove software, edit system text files, etc.

And it's pronounced "Sudoo,"for Super User do."

---

### Post by ocelot79 on 2019-02-04
Thanks for the help.

> **oldrocker99 said:**
> 
KDE is somewhat resource-intensive. Ubuntu MATE (MAH-tay) has an introductory Software Boutique, making a selected collection of some of the best programs. It is lightweight, and can look like Windows (or KDE, for that matter) Mac, and even Unity. I consider Ubuntu MATE to be the best distro I have ever used, and I've done some distro-hopping over the years.

I'm going with Kubuntu because I dislike how GNOME looks like, at least initially. I like how KDE and XFCE look like a lot. My system can already handle everything I throw it in Win10 so I expect it to run KDE just fine. I may try MATE in the future, thanks for pointing that out.

---

### Post by CatKiller on 2019-02-04
> **oldrocker99 said:**
> KDE is somewhat resource-intensive.

It's actually much lighter than you'd think. At the transition to KDE 4 and Gnome 3 they were both quite clunky, and the difference between those and the "light" desktop environments of Xfce, LXDE or Mate were quite stark. KDE has got much leaner with its resource usage as it gets more performant. Gnome's other decisions have stopped me bothering to see if they've got similarly efficient.

To the OP, Muon is the KDE equivalent of Synaptic, and is installed by default in Kubuntu unlike Synaptic in Ubuntu these days. Seeing package management in action is a very good way to understand it.

---

