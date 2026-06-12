---
title: "Server 13.04 x64 GUI"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by andrewgerm on 2013-05-31
Good afternoon all
I am currently downloading the ISO for Ubuntu Server 13.04 x64, to be installed on a new machine.
This replaces an old P4 that ran Desktop x32.

The purpose of the system is an office server that will run as a development platform for websites (Apache, MySQL, PHP).
It will also act as a file server, and synchronise to a DropBox account. This will also connect to a shared printer and scanner.

I know the whole debate over a server GUI, and have done a lot of searching and reading on this matter.
As all of this is maintained by me alone, a GUI is a lot simpler. I do the usual house-keeping via a remote terminal, but for soem tasks, a I find a GUI easier and quicker (and probably the only way the scanner will work).

Everyone suggest installing a desktop system once everything is up and running, but I have also read in a few places that doing so will change the kernel from the server version to the desktop version?

Is this correct? What is the best desktop to use with Server, that will not change any of the server components?

It would be nice to have an option to select a GUI designed for Server when installing. Just my thoughts for us SOHO admins.

Any help / tips / suggestions apprectiated.
Thank you in advance :)

---

### Post by 3rdalbum on 2013-05-31
Server Ubuntu + GUI = Desktop Ubuntu
Desktop Ubuntu - GUI = Server Ubuntu.

XFCE and LXDE are lightweight GUIs and it doesn't matter if you install them on top of Ubuntu Server or install Xubuntu or Lubuntu.

Don't worry about server kernel versus desktop kernel. Both will work fine for a basic server system. The server kernel is better for big rack-mounted or enterprise servers.

You could run any GUI you like, BTW.

---

### Post by andrewgerm on 2013-05-31
@**[COLOR=#000000]3rdalbum[/COLOR]**

Thank you for the reply. If there isn't going to be any big difference between the two kernels, then perhaps what I'll do is install Server, and then add a lightweight desktop to it. There's no need for the limited number of people accessing the server at any one time, so have another machine set up for print and scan sharing.

Just waiting on the ISO (a bit slow via torrent right now). But I'm sure, having used Desktop on other desktop systems, and my laptop, for many, many years, that it'll be a breeze.

Thank you for the clarification!!

---

### Post by Cheesemill on 2013-05-31
Ever since 12.04 both the Server and Desktop versions use an identical kernel so there is no difference at all between a Ubuntu Desktop installation and a Ubuntu Server installation with the ubuntu-desktop package installed.

Do you have a good reason for using 13.04?

Support for 13.04 runs out in January next year so you will only have 6 months before you need to upgrade your OS to the next version. 12.04 is the current LTS (Long Term Support) release and is supported until April 2017.

For servers it is highly recommended to only use LTS releases unless there are new features which you ***have*** to have that are only available in later versions.

As for DE's if I was going to install one on a server I would go for either Openbox, LXDE or XFCE as these are the most lightweight. If you are going to install any of the DE metapackages (xubuntu-desktop, lubuntu-desktop, etc) then make sure that you use the --no-install-recommends option with apt-get otherwise you will end up with a lot of applications installed that you will never use (office applications, social media apps etc).

I would also set the system up so that it always boots into CLI mode, only launching the DE with the startx command if I needed it.

---

### Post by andrewgerm on 2013-05-31
@cheesemill

No. No real reason to install 13.04, so I will use 12.04 instead.
The versions of MySQL, PHP, etc. that come with 12.04 are just fine for the development work being done.

I run LXDE on my Lubuntu laptop. It's really fast (this is a 1.6Ghz Celeron, with 512MB RAM).

Thank you too, for the input.

Been doing a lot of reading up and planning before the whole installation, so I have everything set out prior to install, and don't add anything I don't want / need. Would be nice to keep things as clean as possible.

:)

---

### Post by Cheesemill on 2013-05-31
> **andrewgerm said:**
> Been doing a lot of reading up and planning before the whole  installation, so I have everything set out prior to install, and don't  add anything I don't want / need. Would be nice to keep things as clean  as possible.

[IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
A good way to test out your setup before installing it on the actual hardware is to run through your installation on a VM keeping notes along the way.

This way you get the benefit of being able to take snapshots and rolling back if you make a mistake. For example create a snapshot before you install and test a DE, if you decide you don't like it or have installed to much extra software then just roll back to the previous snapshot and try again instead of having to start the installation from scratch.

---

### Post by andrewgerm on 2013-05-31
Great. Will try the VM :)
That'd actually be great to let me play with all the other distro's out there too. I see so many on cover discs, dedicated to media centres, video editing, or other.

Thanks again, all, for the advice and answers!!

---

### Post by sandyd on 2013-05-31
If you want to do easy setups, you can also use webmin for configuration ;)

I used to find it handy though I write my own config files now.

---

