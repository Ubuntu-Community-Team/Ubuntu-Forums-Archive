---
title: "ubuntu minimal openbox install ended up with gnome 3"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by opfeld on 2014-05-26
So I followed the directions [here]("http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/"), to do an ubuntu minimal openbox install but ended up with gnome 3 as my default DE.  Openbox is still there if I select it in the login but I was hoping for this to be nothing but openbox.  The only thing I can think of is when I used the command _**sudo apt-get install gdm network-manager**_ it wanted to install 600 packages I believe, could this be what caused gnome 3 to be installed?  I wanted to use lightdm but the I found numerous issues through google about problems with lightdm and openbox.  So is there a way to remove gnome 3 from the system besides doing a clean install?  Also if gdm was the culprit, what other login manager could a i use if I want to auto boot into the desktop while seeing nothing but a black screen?

---

### Post by LastDino on 2014-05-26
That guide maker has mentioned that he is installing gnome3 DE quite specifically in a quite a few posts in comment section, did you not read it? 

To avoid installing gnome getting install just skip that step.

Which should be
```
sudo apt-get install gnome-core
```

Or for minimum version of gnome, it should be

```
sudo apt-get install gnome &#8211;no-install-recommends
```



BUT, more importantly; why are you not trying something like Bodhi (since Lubuntu doesn't seems to be option enough) instead of doing all this?

I forgot to reply to second part on removing gnome core, sorry.
Read this link
[http://askubuntu.com/questions/164941/why-removing-gnome-core-does-not-remove-all-of-its-dependencies](http://askubuntu.com/questions/164941/why-removing-gnome-core-does-not-remove-all-of-its-dependencies)

---

### Post by opfeld on 2014-05-26
When doing through the guide he did say it was optional to use those gnome core commands and so I skipped over them entirely and just install gdm network-manager and openbox.

Then upon first boot up I was placed into gnome 3.  I was able to log out and select openbox, but still seems strange...

---

### Post by opfeld on 2014-05-26
Also I noticed that I never got the Select Packages screen where the author selected Manual.  After partitioning my install jumped straight into installing the base system

---

### Post by buzzingrobot on 2014-05-26
> **opfeld said:**
> Also I noticed that I never got the Select Packages screen where the author selected Manual.  After partitioning my install jumped straight into installing the base system

I've installed with the mini.iso a number of times and that has never happened.  Perhaps there was an error in retrieving files from the server. Or, perhaps an inadvertent extra keystroke queued and skipped by the package selection screen. (You do not actually need to select anything there.  You can hit return and move on, adding what you want after the reboot.)

If GDM -- Gnome Display Manager --wanted to install 600 packages as dependencies, then that's how Gnome was installed. You do not need GDM for Openbox.  Several other DM's are available.

---

### Post by verymadpip on 2014-05-26
Hi there.
I run a mini-iso install with open box & lxpanel on some properly ancient hardware.
I just log in from the terminal when the machine has booted up.
No DM (gdm; lightdm etc) used at all - mainly because sorting out log out/shutdown options was far too much like hard work for me.

---

### Post by opfeld on 2014-05-26
> **verymadpip said:**
> Hi there.
I run a mini-iso install with open box & lxpanel on some properly ancient hardware.
I just log in from the terminal when the machine has booted up.
No DM (gdm; lightdm etc) used at all - mainly because sorting out log out/shutdown options was far too much like hard work for me.

I would do that but I really am looking for something that will auto login.  

I tried reinstalling the mini.iso again, and it again didn't show me the package selection screen, however when installing the DM I ran the install command on gdm, lightdm, and lxde while saying no to all of them just so I could see how many packages each wanted to install, I believe they ranged from 250-450 total packages GDM being the largest and lxdm being the smallest.  I finally did install lxdm, and in the boot up screen there was an option to run lxde so maybe the DM is installing the DE as well as some kind of dependency?

---

### Post by vasa1 on 2014-05-26
> **opfeld said:**
> ... so maybe the DM is installing the DE as well as some kind of dependency?
Would the output of *apt-cache show <package_name>* help you? In the case of *lxdm*, I see this:
```
[07:14 AM] ~ $ apt-cache show lxdm
Package: lxdm
Priority: optional
Section: universe/x11
Installed-Size: 785
Maintainer: Julien Lavergne <gilir@ubuntu.com>
Original-Maintainer: Debian LXDE Packaging Team <pkg-lxde-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 0.4.1-0ubuntu6
Provides: x-display-manager
Depends: libc6 (>= 2.14), libcairo2 (>= 1.2.4), libck-connector0 (>= 0.2.1), libdbus-1-3 (>= 1.0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.24.0), libgtk2.0-0 (>= 2.24.0), libpam0g (>= 0.99.7.1), libpango1.0-0 (>= 1.14.0), libx11-6, libxcb1, debconf (>= 1.2.9) | debconf-2.0, upstart-job, x11-utils | xbase-clients | xmessage, lsb-base (>= 3.0-6), gtk2-engines-pixbuf, librsvg2-common, libpam-runtime (>= 0.76-14), libpam-modules, iso-codes
Recommends: lxsession (>= 0.4.0), lxde-common, locales-all
Filename: pool/universe/l/lxdm/lxdm_0.4.1-0ubuntu6_amd64.deb
Size: 116840
MD5sum: 729265b179f4a6a5e1fe8c49ae95dc72
SHA1: a33fd686a07aafea87362864c676e20c3bd075f4
SHA256: 80052b6babee4f1dedffa83b3ba19fff10c2d74ea5fb9171bc1527bf5bc6bb89
Description-en: GUI login manager for LXDE
 lxdm is a lightweight GUI login manager which can
 be used as a dropped-in replacement for GDM or KDM.
 .
 Besides LXDE, lxdm can also work with KDE and others
Description-md5: b8e3da45a6f996b0d98b1dc577c5d8a1
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

---

### Post by verymadpip on 2014-05-27
Hi again.
Regarding your log in requirement;
I wonder if this is of any use to you?
[https://wiki.manjaro.org/index.php?title=Auto-Login_without_a_Graphical_Desktop_Manager_%26_with_Systemd](https://wiki.manjaro.org/index.php?title=Auto-Login_without_a_Graphical_Desktop_Manager_%26_with_Systemd)

---

### Post by Sufian_Ahmed on 2014-05-27
Thank for such a useful post.

---

