---
title: "When will Openoffice 2.4 be updated to the new 3.0 in the repos?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by espressobeanies on 2008-10-15
Anyone know? The reason I ask is that the new version can open the .xlsx and .docx files from Microsoft Office 2007.

---

### Post by sillyxone on 2008-10-15
I have 2.41 on my Hardy and it can open docx, xlsx, and pptx files.

You can also install version 3.0 manually (see link below), or search for a few posts here about installing it within the last few days.

[http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

I have no problem running 2.41 and 3.0 side by side, except 3.0 couldn't load Scim.

---

### Post by louistan3 on 2008-10-15
i found these somewhere, i think theyre developer or test repositories..

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

but they work though.. im not sure if its the best solution.. but i think its easier than installing it manually. :)

---

### Post by Sef on 2008-10-15
> i found these somewhere, i think theyre developer or test repositories..

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

but they work though.. im not sure if its the best solution.. but i think its easier than installing it manuallyRun them only if you are running Intrepid Ibex.  Otherwise, you could have a problem.

Moved to Absolute Beginners.

---

### Post by stmiller on 2008-10-15
The openoffice.org download site has .debs for the new version. You can just install the 3.0 debs from their site. 

It installs in /opt/ and does not interfere with the current 2.4 install.

Check it out!

---

### Post by snowpine on 2008-10-15
There is a very slight chance the release version of Intrepid will include OO 3.0. Otherwise, it will be in 9.04 Jaunty J. They would never switch OO from 2.4 to 3.0 in the repositories of an existing release. Though it might be available through backports, and of course you can install it easily using the methods mentioned by other posters.

---

### Post by SunnyRabbiera on 2008-10-15
The easiest method I have tried to install open office 3 is:
Step 1: Download open office 3 for debian
2: Extract the zip file
3: In the debs folder move everything you have into the desktop integration folder by selecting as many of the debian insallers you can at a time but there are a whole crap load of them so this might take a while.
4: For normal Ubuntu users install the package nautilus-open-terminal, for Kubuntu and xubuntu users skip this
5: For normal Ubuntu users, restart your computer, for Kubuntu and xubuntu users skip this.
6: Remove as much of open office 2 as you can
7: go into that desktop integration directory and open up a terminal, now how to open your terminal in Ubuntu is by right clicking in the folder and selecting Open terminal.
Kubuntu and xubuntu users should have the open terminal command in the main menu of both Thunar and Dolphin/Konqueror
8: put in the command: sudo dpkg -i *.deb
9: after dpkg is done you may wish to try to install the package openoffice.org3.0-debian-menus_3.0-9354_all located in your desktop integration folder.
10: done

---

### Post by leandromartinez98 on 2008-10-15
[QUOTE=snowpine;5969878 They would never switch OO from 2.4 to 3.0 in the repositories of an existing release. [/QUOTE]

Why not? (This is not a critic, just a question). Other software is normally updated when new versions become available, why shouldn't be that way with the OOffice?

---

### Post by jocko on 2008-10-15
> **leandromartinez98 said:**
> Other software is normally updated when new versions become available, why shouldn't be that way with the OOffice?

That's not true. New versions of programs are usually never added to an already released version of ubuntu. There has only been a few exceptions to this (such as updating a beta version of firefox to the final version, which happened in Dapper if I remember correctly).

---

### Post by snowpine on 2008-10-15
> **leandromartinez98 said:**
> Why not? (This is not a critic, just a question). Other software is normally updated when new versions become available, why shouldn't be that way with the OOffice?

Because each release of Ubuntu (Gutsy, Hardy, Interepid, etc) has its packages "frozen." Ubuntu is not a "rolling release" distro like, say, Arch. Rather, it's based on a 6-month development cycle that obviously has its pros and cons but works for many people.

There is a "backports" system in place for those who want newer versions: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

If you want a list of which packages are in which version of Ubuntu: [http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

---

### Post by tgyorgyi on 2008-10-18
I managed to install OOo3 from the .deb files, only the desktop integration fails.
Prior to install I removed OOo 2.4 with Add/Remove in the Applications menu as well as the hidden .openoffice.org2 directory from my /home directory.

I'm getting the following error message in dpkg:

 > openoffice.org-core conflicts with openoffice.org-unbundled

Have I missed removing a component? I checked Synaptic as well, but there are only language files for open office there, I presume they could not cause the conflict?

---

### Post by leandromartinez98 on 2008-10-30
> **jocko said:**
> That's not true. New versions of programs are usually never added to an already released version of ubuntu. There has only been a few exceptions to this (such as updating a beta version of firefox to the final version, which happened in Dapper if I remember correctly).

We must admit that this is a bit frustrating from the point of view of software installation facility. In this case, we will only have a supported apt-get for OOffice 3.0 in Ubuntu in 9.04 and, then, we will have to fully update de operating system (what, by the way, is not required, since I did manage to install it now, but following the old-times linux style of installing things). This kind of puts back the installation/updating advantage that Ubuntu has over windows, don't you think?

---

### Post by NewJack on 2008-10-30
I followed the instructions posted on Tombuntu and had no problems at all.  Everything works great.

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

