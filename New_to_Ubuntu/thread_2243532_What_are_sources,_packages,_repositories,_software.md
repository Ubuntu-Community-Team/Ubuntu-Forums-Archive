---
title: "What are sources, packages, repositories, software centers? Uninstall completely?"
date: 2014-09-09
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-09
I just recently decided to install Kubuntu on an old laptop to try out Linux for the first time. As a Windows user, can someone explain in elementary terms what sources, packages, repositories, and software centers are? I have a very vague idea of the different ways to install/uninstall a program--*some ways are better than others.* I really appreciate Linux's lack of registries (in Windows, the process of uninstall/installing applications leave behind orphan/redundant registries which accumulate and slow down the system). I realize that at worst, uninstalling an application improperly (meaning any files associated with application is somehow not removed from the system) means files such as config files are left behind and take up trivial amounts of space. However, I really want to learn the command lines (or if there is an application that performs the same task) that allow me to completely remove a program. I'm guessing this would mean its depencies and repositories as well? I'm don't think I fully understand these terms.[[IMG]http://ubuntuforums.org/clear.gif[/IMG] Edit Post]("http://ubuntuforums.org/editpost.php?p=13118505&do=editpost")

Doing a google search, I haven't found a complete guide on this and it is frustrating. I see that some people use "sudo purge" while others use "sudo apt-get clean," "sudo apt-get autoclean," and "sudo apt-get autoremove."

Let's say I want to install Firefox and then completely uninstall it. What are the ways I can accomplish this and how can I uninstall it completely? For example, I know that you have to manually delete hidden folders like .mozilla and .firefox in your home directory. Do I google to find out what kinds are files are left behind and where to track them down and delete them after doing an "improper uninstall"? Or is there something I can type in the terminal that can do all this for me?

Thanks.

P.S. I can't find Google Chrome for Kubuntu on the Muon Software Center, so I went to Chrome's installer page. Is the ideal installer the one that says "Debian/Ubuntu only" or is there one specifically for Kubuntu? If I see an application that I want that is for Ubuntu, can I use it for Kubuntu with as much success?

---

### Post by whitesmith on 2014-09-09
That's some post, kemosabe! I'll help with as much as possible before I get dragged out for lunch. Packages in Linux correspond to a .msi in Windows. Repositories have no direct equivalent in the Windows world. They are essentially collections of (usually related) code. For the command line, check out the second reference in my signature line. For the "sudo apt-get ..." stuff, check out this (sort of official) Apt-Get Howto: [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto).

Time to grab some chow. Others, no doubt, will fill in more details. Best wishes as you pursue the Beast!

{edit] As arguments persist about where to go, let me answer one more for you. The Ubuntu Software Cednter is kind of like Apple's iStore or Android's Play Store. You'll find apps there that have passed a certain level of peer review. You can be pretty sure that anything you get there won't, shall we say, give you anything. Even if you download a .deb file, just by double clicking oin it you'll be taken to the Software Center for installation. Hope this does for a start!

---

### Post by uRock on 2014-09-09
For Chrome, you  want the Debian/Ubuntu only package, which once installed will and the source repository, so you will get updates when Google releases newer versions or the package.

---

### Post by ibjsb4 on 2014-09-09
Two things to help you out in the quest for answers.

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

And in my sig below

---

### Post by Rob Sayer on 2014-09-09
I've never seen one all in one guide that's comprehensive and readable by inexperienced users.  The web (and linux distros) is fragmentary.  But this is the best guide to removing software I've seen:

[http://askubuntu.com/questions/187888/what-is-the-correct-way-to-completely-remove-an-application](http://askubuntu.com/questions/187888/what-is-the-correct-way-to-completely-remove-an-application)

Though I don't necessarily 100% remove applications and rarely use autoremove because it can cause problems.

You can definitely install ubuntu packages like chrome in kubuntu.  This ain't windows.  Thank frak.  The KDE desktop you're using in kubuntu is, as far as the operating system is concerned, *just another application program*.

I use kubuntu on the laptop I mostly use at home, xubuntu on this netbook.  I haven't used muon software center in ages.  And I don't think I've ever used whatever equivalent program came with xubuntu.  I use the terminal or synaptic package manager.  Synaptic is great.  If you don't have it, get it and learn how to use it.

---

### Post by garycheng12 on 2014-09-09
Thanks for the quick and informative answers, guys. I'm always surprised at the quality of responses in such a short period of time in ubuntuforums. Can't wait to read on the bus =D

---

### Post by grahammechanical on 2014-09-09
In Linux software, the libraries, the applications and programs and their component parts all come in packages because they are packaged to run on that distribution of Linux.

Ubuntu is built on top of Debian. So, packages in Ubuntu are in the Debian package (deb) format. Another distribution might be built on Fedora, which is closely related to Red Hat and is packaged in the Red Hat package management system (rpm). The two systems are incompatible.

All the packages that go to make up Ubuntu and the default applications that come with Ubuntu and any application that is in the Software Centre (think - app store) are stored on Ubuntu servers. These servers are called repositories because they are just that. They are the sources of all the packages in Ubuntu and available through the Ubuntu Software Centre. Sources lists are files that contain the URLs to the servers. Each release of Ubuntu has its own set of repositories which are closed and moved elsewhere when the release reaches End of Life. Which is after 5 years for a Long Term Support (LTS) release and 9 months for the other releases of Ubuntu.

The Software Centre will also remove software for us. Most of us get through life with out needing to use the Command line to install and remove software. Chrome is proprietary software and it is not available through the software centre. Downloading and installing software off of web sites carries the risk of installing code that has not been code audited to see if the code is malicious in any way. Whereas, the applications in the software Centre are code audited.

Ubuntu can be as easy and as confusing as we wish to make it. In Linux we have the freedom to run before we can walk.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Regards.

---

