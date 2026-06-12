---
title: "apt-get install and remove method - make file?"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by starstreams on 2013-01-06
Hi. I've been reading all kinds of documents and web sites on apt-get, but there's something I'm not getting. With regard to how an *install manager* such as apt-get handles it's download packages and removing programs. Let me please explain what led me up to one of the questions: 

While reading a tutorial on compiling the lesson mentioned that if you want to run *make clean* it's impotent to keep your *Make file* so you could later run a *make uninstall* command to remove the program if needed. This brought me to the question about how apt-get deals with uninstalling. 

1. When you run *apt-get install* ..ect, does it keep the package source/ or binaries somewhere? I'm assuming the *Make file* or what ever apt-get uses to remove a program is kept somewhere and later accessed for the uninstall paths? Or does apt-get delete the source files it obtains from the repository after it installs your program? I mean how does it know where all the files are from when it installed the application?

2. If you run something like *apt get autoremove*, would that remove the *make file* that apt-get possibly needs to uninstall software? As mentioned *make clean* will remove it.  

Thank you

---

### Post by coldcritter64 on 2013-01-06
With installing from source code, you configure and make the source into a binary installable package [s]or a debian installer (.deb package)[/s]. This is then used to install your program. **EDIT**: I mixed up the 2 methods here. .deb not used in source installs, UNLESS checkinstall command is used.

apt-get downloads premade .deb packages from the repositories to /var/cache/apt/archives, installs the package to the system and maintains a database of installed packages to manage the system.

If you build and install from source your installed package is not registered with apt-get's database, you will then need the make files to uninstall as you mentioned. 

If you use checkinstall instead of the install command with source installs, (sudo apt-get install checkinstall), your source built package will be correctly registered with apt-get for easy installation/maintainence/removal with apt-get or Synaptic, or any tool using apt-get as a backend.

---

### Post by starstreams on 2013-01-06
Hello coldcritter64, Thank you, the good explanation. 
I didn't know apt-get downloaded premade .deb packages. When I hear people use the world packages rather then executables as I'm use to in windows, I always thought the packages were filled with source that apt-get compiles and installs during it's run. I do realize anything can come in a package, tar..ect. But I was always confused by how the term package was used in the Linux world.

> **coldcritter64 said:**
> 
If you use checkinstall instead of the install command with source  installs, (sudo apt-get install checkinstall), your source built package  will be correctly registered with apt-get for easy  installation/maintainence/removal with apt-get or Synaptic, or any tool  using apt-get as a backend.

Your post brings up one more question.  I was refering to the Make compiler as an exmaple to compare how manual removal works compaird to apt-get. (or how it was explained to me).
However, after reading your post, I didn't realize you could use apt-get to run source installs. So if I have a program that comes as source code,  can run an apt-get checkinstall on the source files and it will configure the binary files for my kernel version and install the application?

---

### Post by coldcritter64 on 2013-01-07
When you compile code to install, generally the steps go,

```
cd /to/source/folder
``````
./configure --some-option-if-needed
``````
make
``````
make install # (or can be **replaced** with checkinstall)
```Those commands can be varied with options etc. very basic steps. This will install a program fully, but NOT registered. If install is REPLACED with checkinstall the program/package installation is registered correctly.

Hope that makes it a bit clearer :)

Edit: I need to add apt-get doesn't "run the source install", checkinstall does that, but correctly adds the package and its necessary details to apt-gets database so apt-get or other tools like Synaptic can then handle it. Also compiling against a specific kernel or other dependency etc specific header file packages may be needed to be installed for successfull builds.

A link worth checking : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
A more advanced link : [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by starstreams on 2013-01-07
Hello coldcritter64.

  Those are all great points I will keep in mind, Thank you.
I think I might have gotten mixed up, because I was trying to follow this lesson.
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

In that lesson they specifically talk about *Make*. For clerity, is Make a command, or an actual utility? Does *checkinstall* evoke the Make utility ..then the details are added to apt-gets/ Synaptic's database?

note:  I installed System essentials onto  my Lubuntu OS, using apt-get so I could get Make as that lesson mentioned it.

---

### Post by oldos2er on 2013-01-07
The info in [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) is old, but most of it is still relevant (keep in mind Ubuntu didn't exist in 2002). Usually it's best to stick to a distro's own documentation:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by coldcritter64 on 2013-01-07
"make" is a command that is run in the process, make could also be said to be a utility.

The user invokes make as a step in the process of building, as they also do with checkinstall. 

A part of the job checkinstall does is to correctly register the installation with apt-get as well as replacing the old install/make install (whichever is used) command.

Note the last modified date at the top of your link, 2005. Old info, It looks valid still but is an older way of doing it. Seems I got the last command a bit wrong, that "make install" looks correct. I'll alter my previously posted steps with it. 

"make install" is replaced there with "checkinstall" if used. If you use checkinstall, the uninstallation section is moot, uninstallation can be done with apt-get/Synaptic etc.

Edit: I missed the checkinstall link last post, thanks oldos2er :).

---

### Post by starstreams on 2013-01-07
Thanks for the update coldcritter64, and for the info on how checkinstal registers the installs. You explained that well, Much appreciated!
If I my please push this question a bit more. I guess what I'm trying to understand at this point is, what is the actual program that's doing the work when you run commands like checkinstall, or Make Install? is it GCC that's actually carrying out the commands above? In other words these are commands associated with GCC, or a different utility such as Make?

EDIT, I'll check these three links below that oldos2er posted, my answer might be in there. Not sure yet.

Thanks for them direct links oldos2er, those look good. 
I've been saving/archiving all the good lessons I find to folders on my drives. 
I didn't realize tuxfiles.org was so old. But I have to say, who ever is teaching the lessons does a darn good job. The author is so thorough and detailed. Learned a lot from it.
I think I might light a cigar up while I read though these three links you posted :p
I need to get out of panic mode and just take things one day at a time. 


Thank you again!

---

### Post by coldcritter64 on 2013-01-07
> **starstreams said:**
> ....If I my please push this question a bit more. I guess what I'm trying to understand at this point is, what is the actual program that's doing the work when you run commands like checkinstall, or Make Install? is it GCC that's actually carrying out the commands above? In other words these are commands associated with GCC, or a different utility such as Make?

..

I need to get out of panic mode and just take things one day at a time. 


Relax/Read the links and try and absorb some more of what is going on 1st. :) 

As I understand it, "make"  and "make install" are separate commands run to build the source code into a binary program and install it as required by the system. When configuring the code for building, the configure script does ususally check the environment for such as GCC, yasm and other system settings /variables/tools available, before "make" is used to build the package. Those tools like GCC and yasm etc,are like "back end" tools required in the code compiling/application building process and are only called as and if needed (note: my explanation may be a bit simplified, my experience here is limitted_ best to refer to the links :)). Cheers.

---

### Post by Zill on 2013-01-08
> **starstreams said:**
> ...I need to get out of panic mode and just take things one day at a time...
In the "old days" most Linux software *was* generally installed by compiling from source.

However, the introduction of package management systems (such as apt-get), made this largely unnecessary for most users.

Personally, I have not installed anything from source for many years now!  Everything I need can simply be installed either from a GUI application such as Synaptic, or from a terminal command:
```
sudo apt-get install mynewpackage
```

Just in case you are new to Ubuntu and don't fully understand how software is normally installed you may find it helpful to read the following link:
[LIST]
[*][Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")
[/LIST]

---

### Post by Zill on 2013-01-08
> **starstreams said:**
> ...So if I have a program that comes as source code...?
I do recommend that you don't try to install *anything* from source until you have considerably more experience.

To requote myself from our posts of four weeks ago:
> [If you obtain packages from any other source, or try to compile and install software from source, then you are quite likely to end up in "dependency hell" and break your system!]("http://ubuntuforums.org/showpost.php?p=12390500&postcount=22")

---

### Post by starstreams on 2013-01-08
**@coldcritter64,** thanks for that last post, that makes sense. At first it was a lot to take in, but I'm retaining it now.  
 

 **@oldos2er**, thanks again for them three links, I was reading them last night, they are golden. So much info there. Those are definitely being archived on my drive..lol ( I save everything, even these forum answers) so watch what you say... and check your spelling..haha. J/K :p

 

 **@Zill**, Thank you also
 Although I have read that link not too long ago, I ran tough it again. Great info.
 The part about converting rpm files to deb's was interesting.  
 

 On a side note: I think the managers, software center is pretty straight forward. However, I have to mention. One of the security programs I always recommend to friends or anyone I'm helping with their system is Truecrypt. The issue with that software is that the developers of Truecrypt choose to be unknown and as a result they can not obtain a GNU license. (I can only speculate that they choose to be anonymous to avoid being forced  to implement back doors into the software) For what ever the reason, they have not been allowed to add their program to any Linux repository&#8217;s despite the fact that it's totally open source software. I suppose there might be privet repository's hosting it, but being that you're dealing with passwords, I don't know if it's wise to start downloading modified versions of the package as apposed to getting it from the main site. They do have an executable that you can download direct from the main site to install onto linux but the issue I've had with Lubuntu is that it needs Nautilus FM to mount drives. I have installed it before and it works _as long as you install Nautilus FM_, but I'm not sure if Nautilus breaks things in the default File manager. ...Which happens to be Pcman for Lunubu. Some people have written scripts that do what Nautilus FM does, but can  someone trust those scripts to not key-log your password if you don't know scripting to verify it yourself.
 

 One last note:
 One of the things I think most people (including myself) finds confusing about Linux (when coming from windows), is that people in the Linux world tend to refer to programs as packages. In windows, you download either an **[COLOR=DarkGreen]exe[/COLOR]**, **[COLOR=DarkGreen]msi[/COLOR]**, or a **[COLOR=Blue]zip[/COLOR]**, **[COLOR=Blue]rar, tar[/COLOR]**..ect file. In the last **[COLOR=Blue]three[/COLOR]** examples, would be what windows users refer to as a package. Once the program is installed, it's called an application or program. I've recently discovered that Linux users call these zip, rar, tar files packages, but then use the "same terminology" to reference something that has "already" been installed. So a program in Linux is also called a package. That really through me off for the longest time. But I think I've got the hang it

---

### Post by oldos2er on 2013-01-08
A *package* is a package, it may or may not contain a program (that is, an executable file). For example, there are many packages that are only library files, they usually begin with lib-. Library files on Linux are similar in function to DLL files in Windows.

A *.deb file is a package that can be installed on Debian and Debian-based distros, such as Ubuntu.

An *.rpm file is a package that can be installed on Red Hat and Red Hat-based distros, such as Fedora.

---

### Post by coldcritter64 on 2013-01-08
I agree with Zill, it is best for a novice in Ubuntu to stick to the offficial repositories. This especially comes into play when assistance from here is required by a novice. The more standard your install the higher the likelyhood of a successful repair.

Even (less preferably) PPAs or personal package archives hosted on launchpad could be used for software.

Truecrypt I have no exposure to. I personally wouldn't like the fact the devs are anonymous (though your suggestion for "why" seems feasible), and would look for an alternative myself. 

**If you trust truecypt,** I would consider either installing Nautilus on lxde (it will haul in a "ton" of gnome related dependencies) and using the main site installer **OR** if you build from code, before doing so, ask about the scripts that worry you here (the lxde nautilus replacement scripts ). I am sure someone will happily "talk you through" what the script is doing. I have seen a similar script used to "trick" dropbox on xfce to think Nautilus was in use, but I'd already installed Nautilus :).

---

### Post by starstreams on 2013-01-09
*@oldos2er*: 
True. I was just saying when a program is installed, people still tend to call it a package in the linux world, or will often refer to removing a program as removing a package which sort of through me off at first.   I could be wrong about that assumption, it just seems like that was the case.

*@coldcritter*: 
I've never seen an alternitive to truecrypt. The things you can do with it is amazing.  Check out the intro documentation to see what I'm talking about. I don't use all it's features, but I think it's a master piece of software.  But what you said about installing Nautilus and having it pull in gnome related dependencies was probably why I was getting strange behavior with PCman. Truth is, I have plenty of power to run Ubunut so I probably don't need to be running this Lubuntu.. lite ver of Ubuntu. I just can't stand Unity. If I could figure out how to put the older style Gnome back on so I can put things on the desktop and remove that bar I would switch back to Ubuntu. At least it comes with Nautilus as it's defult FM. Something to look into I guess.

---

### Post by Zill on 2013-01-09
> **starstreams said:**
> ...The part about converting rpm files to deb's was interesting...
...but generally unnecessary!

Red Hat Package Management (rpm) is a *different* packaging system to the Debian (deb) packaging system used by Ubuntu.  Forcing rpms into deb systems by using "alien" *may* work, but is more likely to cause problems, if not breakage, with your system.

There is negligible useful software that is not packaged as a deb but is only packaged as a rpm!

From the [RPM/AlienHowto]("https://help.ubuntu.com/community/RPM/AlienHowto")
> Alien converts an RPM package file into a Debian package file or Alien can install an RPM file directly. This is not the recommended way to install software packages in Ubuntu. If at all possible, install packages from Ubuntu's repositories using Add/Remove, apt-get, or the Synaptic Package Manager. **Package dependency conflicts may occur when attempting to install RPM packages.**

---

### Post by starstreams on 2013-01-12
I probably wouldn't have to do that anyway Zill.
Just seemed like an interesting read. Thanks for the warning. Being that the kernal of Linux is pretty common, it seems like most of these compatibility issues with dependencies seems to be predicated on what ever desktop environment you run. For example, if I uninstall LXDE for Lubuntu and put Gnome on, Then I'm assuming I could probably install Genome dependencies at that point. I guess what I'm saying is, (and this is just an observation) The desk environment is what seems to be the determining factor as to what you can and can not install with regard to dependencys. Is that true?

> **coldcritter64 said:**
> I
**If you trust truecypt,** I would consider either installing Nautilus on lxde (it will haul in a "ton" of gnome related dependencies).

I wanted to command more on this. 
Gnome3 is the default desk environment for the current Ubuntu. What would happen if I uninstalled LXDE, and installed say Gnome2 to get the older Ubuntu look, .. with the luxury of starting off with with Lubunu's striped down OS. Lubuntu doesn't come with much installed which is nice. But I don't know if LXDE is as important to me as having a Gnome desktop that comes packaged with Nautilus by default. I liked the environment of Gnome2 actually, Just can't stand Unity that comes with Gnome3.

---

### Post by Zill on 2013-01-12
> **starstreams said:**
> ...Being that the kernal of Linux is pretty common, it seems like most of these compatibility issues with dependencies seems to be predicated on what ever desktop environment you run. For example, if I uninstall LXDE for Lubuntu and put Gnome on, Then I'm assuming I could probably install Genome dependencies at that point. I guess what I'm saying is, (and this is just an observation) The desk environment is what seems to be the determining factor as to what you can and can not install with regard to dependencys. Is that true?...
While a "Linux kernel" is fundamental to all Linux distributions, *different* versions of the kernel are used in different releases of each distribution.  The package maintainers ensure that all the packages in the repos *for your particular release* will work with the specific kernel version for that release.  Therefore you *cannot* mix'n'match different kernel versions with your installed release without risking problems.

Dependencies are all the other installed packages, such as libraries, that are required to run a particular application.  The *versions* of such dependencies therefore have to be matched to the specific release to ensure functionality.  This is why it is very important to only install packages intended for your release.

Regarding Desktop Environments (DEs) the best advice is to stick to just one DE as installing multiple DEs will install very many new packages for each DE as dependencies, leading to bloat and confusion with the menu systems.

Gnome2 is dead.  If you really want a DE that looks similar to Gnome2 then I suggest you install [Mate]("http://mate-desktop.org/"), which is actually built on Gnome3.

---

