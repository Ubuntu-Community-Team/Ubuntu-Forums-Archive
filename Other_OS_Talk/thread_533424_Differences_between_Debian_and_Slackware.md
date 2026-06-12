---
title: "Differences between Debian and Slackware?"
date: 2007-08-23
forum: Other OS Talk
---

### Post by tico on 2007-08-23
What are the main differences between Debian and Slackware. What's the package system that Slackware uses?

Thanks.

---

### Post by Bachstelze on 2007-08-23
Slackware is almost entirely the work of one man, so there is not nearly as much packages for it as for Debian. If you want to go ith Slack, be ready to do *a lot* of manual compilation, and to manage dependencies yourself. The package management system will *not* do that for you.

That's the main dfference, Slackware will do *nothing* more than what you tell it to do. So you'll basically have to take care of everything.

---

### Post by heimo on 2007-08-23
I'll just add that Debian's architecture support is wider.

---

### Post by tommcd on 2007-08-24
Slackware is "plain vanilla" linux. Unpatched kernel, KDE and XFCE and all apps straight from the developers as they intended. Slackware is also closer to Unix in that it uses simple rc.init scripts for configuration (which are well commented and not too hard to understand). Slackware package management does not install dependencies, but this makes Slackware more reliable and harder to break (as per Pat V). Check out this podcast on slackware installation. It is on Slackware 11, but it is very good:
[http://www.linuxreality.com/podcast/special-episode-1-slackware/](http://www.linuxreality.com/podcast/special-episode-1-slackware/)

I've been using Slack12 on my laptop and I'm starting to like it a lot. You have to configure a lot of things yourself, but it is a good learning experience. Read the book also:
[http://slackbook.org/](http://slackbook.org/)
Also, the 'Changes and Hints.txt'
[http://slackware.mirrors.tds.net/pub/slackware/slackware-12.0/CHANGES_AND_HINTS.TXT](http://slackware.mirrors.tds.net/pub/slackware/slackware-12.0/CHANGES_AND_HINTS.TXT)

---

### Post by fistfullofroses on 2007-08-24
There are programs that will manage Slackware dependencies... but you would have to install that yourself. Slapt-get, netpkg, etc...

---

### Post by RageOfOrder on 2007-08-24
Swaret handles package depencies for slackware. 
I generally just 
$ ./configure && make && su -c "make install"
for most of my packages, but occasionally I'll use pkgtool2 to convert a .deb binary to a .tgz slackware binary and install it that way.

Slackware is overly easy to install, but takes a lot of manual effort to configure the way you like it. Pays off in the end though. Very stable distro, but unique in the way it does things, so it's a great learning experience.

---

### Post by tommcd on 2007-08-24
> **fistfullofroses said:**
> There are programs that will manage Slackware dependencies... but you would have to install that yourself. Slapt-get, netpkg, etc...

Is there a netpkg available for Slackware, or do you use the one from Zenwalk? And how well does it work in slackware?

---

### Post by angryfirelord on 2007-08-25
When I was using Slackware, I used slapt-get/GSlapt and it worked like a charm, well almost, sometimes slapt-get doesn't resolve all dependencies, but it saved me from a lot of compiling.

---

### Post by Steve1961 on 2007-08-25
Slackware is a great distro but it doesn't hold your hand at all.  Installation is easy but you will need to manually edit config files to get the system working as you want.  That said, when combined with slapt-get and Dropline Gnome I was very happy with it, and I learned a lot.  I eventually replaced it with debian though, because the package management is difficult to beat.

---

### Post by jrusso2 on 2007-08-25
I recommend everyone to try slackware at least once to show how linux used to be in the 90's and how far its come to the present.

---

### Post by Rupertronco on 2007-08-25
Slackware is the most stable Linux distro I've come across and it's taught me an incredible amount about Linux in general. However, it can be extremely irritating and isn't for a person who lacks a great deal of patience. As some of the above posts have mentioned, it doesn't walk you through, or help you with anything. It does exactly what you tell it to and that's it, making it my favorite version  of linux, but sometimes I find it harder to do simple tasks and maintanence on slack vs deb based distros. 

The great thing about linux in general is, you find what's best for you.

---

### Post by angryfirelord on 2007-08-25
> **Rupertronco said:**
> isn't for a person who lacks a great deal of patience.
hehe, that's probably why I stopped using it. :)

---

### Post by fistfullofroses on 2007-08-26
Zenwalk was based off of Slackware, and is mostly still the same system. You can use the netpkg tool from Zenwalk, but you can also download the program for the particular Slackware distro you are using from linuxpackages.net

---

### Post by WishingWell on 2007-08-27
> **HymnToLife said:**
> Slackware is almost entirely the work of one man, so there is not nearly as much packages for it as for Debian. If you want to go ith Slack, be ready to do *a lot* of manual compilation, and to manage dependencies yourself. The package management system will *not* do that for you.

That's the main dfference, Slackware will do *nothing* more than what you tell it to do. So you'll basically have to take care of everything.

Actually, just like Ubuntu Slackware has a lot of unofficial packages, all you have to do is to ad linuxpackages.org as a source and you have almost the same amount of packages that Ubuntu has,

Debian has a lot more official packages than either Ubuntu or Slackware though.

My point is that you rarely have to compile anything.

slapt-get or SMART handles package dependencies just fine, i rarely use anything but SMART regardless of if i'm running SuSE, Ubuntu or Slackware (if you're a bit careful you can actually use debs on SuSE or RPM's on Slackware using SMART.

However, Slackware uses the BSD init and also gives you full control, just because you install a server doesn't mean that it will be started, you'll have to configure it via it's /etc/*.conf files to even make it viable to add to the init.

You'll learn a lot on Slackware but don't be certain that it's applicable to any other distro.

---

### Post by Majorix on 2007-08-27
Slackware was the first distro I used. Then I hated Linux and didn't use it for a whole 3 years. They don't have any community support like Ubuntu. You have to be a Linux Genius to just even use it.

On the other hand, Debian isn't comfortable with wireless. Other than that, its pretty stable and is updated often.

---

### Post by fistfullofroses on 2007-08-28
I do not think that Slackware is really far behind any other "Modern" distribution. I think that the Linux community has honestly strayed from their better beginnings.

---

### Post by Sutur on 2008-02-23
> **jrusso2 said:**
> I recommend everyone to try slackware at least once to show how linux used to be in the 90's and how far its come to the present.

+1,000,000.

---

### Post by jrusso2 on 2008-02-23
> **fistfullofroses said:**
> There are programs that will manage Slackware dependencies... but you would have to install that yourself. Slapt-get, netpkg, etc...
 
Doesn't that defeat the purpose.  Are you not supposed to use it as god and Patrick intended?

---

