---
title: "Howto: Use Ubuntu Backports Repositories Correctly"
date: 2005-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Devi0s on 2005-06-28
**When to Use Ubuntu Backports**

According to the individuals in the #ubuntu IRC channel on the Freenode IRC network, one should only uncomment the backports repositories in the /etc/apt/sources.list file when they face one of the following scenarios:

1) looking for a package that isn't in the official/other repositories.

2) user absolutely MUST have the latest version of a particular package for some reason, and the latest version isn't available in the official repositories.

**About Ubuntu Backports**

"Ubuntu Linux is a great distribution, but falls short in the desktop realm to Gentoo and Fedora Core. Why? Once a stable version is released, no new software updates are accepted. I subscribe to the view that a distribution can be both stable and up-to-date, so I've taken it into my own hands to recompile newer packages from Hoary and Debian Sid for Warty."

**Example of How Ubuntu Backports can be Dangerous**

I left the Ubuntu Backports repositories uncommented in my /etc/apt/sources.list and tried to use synaptic to install gaim-encryption.  It was found in the backports repositories, but to install it, I would have to remove packages mozilla-firefox-gnome-support and ubuntu-desktop, both of which I want to keep.

I went into /etc/apt/sources.list and commented out the backports repositories, and reloaded synaptic package manager, and there was an official version of gaim-encryption that did NOT conflict with the mozilla-firefox-gnome support and ubuntu-desktop packages.

**More on Backports**

Here are the links you should read about backports:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)
[http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php)

To add the backports repositories, you'll need to read and understand how you add the backports repositories to /etc/apt/sources.list:
[https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

**Don't Ever Trust Me**

It is always possible that someone willing to lend a helping hand is wrong, so always double-check provided information using official sources. The following web pages allow you to search the official Ubuntu Wiki and Forum, respectively.

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)

---

### Post by bored2k on 2005-06-28
Backports dangerous ? When multiverse gets Java, universe gets azureus, main gets decent upgraded versions of Firefox and Gaim I'll think about it. To this day backports have done nothing wrong on my machina.

---

### Post by DarkT on 2005-06-28
I utterly agree with bored2k, I have not once had a problem with backports and it's the only reason I keep using k/ubuntu. 
If they didn't keep the packages at least on a par with breezy I would get frustrated with packages that are out of date. Despite the usual debian-esk speel about up to date packages being a bad thing (untested etc. ), if it's something you work with regularly you want the new features/bug-fixes... *shrug* trollish I know but never mind.

---

### Post by manicka on 2005-06-28
I'm pretty new to Ubuntu after being with SuSE for a number of years and backports is just fine. I haven't had a problem with a single package.

---

### Post by benplaut on 2005-06-28
no problems here...

and, BTW, ubuntu-desktop is just a meta-package... it's safe to remove it ;-)

---

### Post by epb613 on 2005-06-28
I never comment out the backport repos and I have never had a problem.

---

### Post by skoal on 2005-06-28
Hmmm...I never even paid attention to such warnings (or advice) like this before concerning backports.  I still have my BP servers uncommented.  No problems here either, but thanks for the 411.

\\//_

---

### Post by Devi0s on 2005-06-29
I also rely on a lot of the backports packages.  I agree that backports are necessary.

My intent was not to say that backports packages are dangerous in all, or even many cases.

However, I did have a problem with them, as documented in my post, and I only seek to encourage new ubuntu users to understand exactly what backports are and understand the potential consequences, particularly with less commonly used packages they might want to install.

Thanks for the comments.

---

### Post by frodon on 2005-06-29
[QUOTE=Devi0s]Example of How Ubuntu Backports can be Dangerous

I left the Ubuntu Backports repositories uncommented in my /etc/apt/sources.list and tried to use synaptic to install gaim-encryption. It was found in the backports repositories, but to install it, I would have to remove packages mozilla-firefox-gnome-support and ubuntu-desktop, both of which I want to keep.

I went into /etc/apt/sources.list and commented out the backports repositories, and reloaded synaptic package manager, and there was an official version of gaim-encryption that did NOT conflict with the mozilla-firefox-gnome support and ubuntu-desktop packages.[/QUOTE]

I can confirm, since I enable backports and updates softwares firefox doesn't work.

---

### Post by bored2k on 2005-06-29
[QUOTE=frodon]I can confirm, since I enable backports and updates softwares firefox doesn't work.[/QUOTE]
 It happens with the one in main too. YOu need to tweak your vendorSub to install firefox packages. That's old.

---

### Post by frodon on 2005-06-29
[QUOTE=bored2k]It happens with the one in main too. YOu need to tweak your vendorSub to install firefox packages. That's old.[/QUOTE]

Can you give me a way or ideas to reinstall correctly firefox ?  I disable backports and reinstall firefox but .... still not start. For the moment i use mozilla and like it but I want to understand why a synaptic reinstall doesn't solve the problem.

thanks for this really interesting thread.

---

### Post by poofyhairguy on 2005-06-29
Thanks for the into.

I will point greens in this direction.

---

