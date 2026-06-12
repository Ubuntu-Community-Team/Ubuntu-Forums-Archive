---
title: "Red Hat v Ubuntu"
date: 2009-09-25
forum: Recurring Discussions
---

### Post by goofynewf on 2009-09-25
I am currently using Ubuntu 8.04 on my Dell mini.  I like Ubuntu and I am going to install it on one of my desktops at home.  My husband wants to install Red Hat.   From what I have read, Ubuntu is more user friendly than other Linux programs.   

Can someone tell me their thoughts on the two, pros and cons.
 
 
Thanks!

---

### Post by Liolikas on 2009-09-25
Main difference that you will have to pay some money for Red Hat I think Red hat is not free. Fedora is base/experimental distro for RH. It will not hurt to download Fedora and try it out on liveCD mode if you have fast net. Really there is no big difference between them. Just package management is not same at all. Red hat/Fedora use rpm not deb packages and not synaptic/apt-get too but other similar tools.

---

### Post by Commander_Keen on 2009-09-25
There really is not any difference between the two.
They both uses Gnome and KDE
They both uses ( for the most part) the same command line commands
I believe they use the same kernel.
Redhat, will give you one on one support but that will cost $$$

---

### Post by karlson on 2009-09-25
> **goofynewf said:**
> I am currently using Ubuntu 8.04 on my Dell mini.  I like Ubuntu and I am going to install it on one of my desktops at home.  My husband wants to install Red Hat.   From what I have read, Ubuntu is more user friendly than other Linux programs.   

Can someone tell me their thoughts on the two, pros and cons.
 
 
Thanks!

You have to look at the following:

1.  Do you need commercial software?
2.  Are you going to use 3rd party drivers that on your system that are only available from the manufacturer?

if the answer to either one is yes your choice is pretty much set.

In my personal experience I would take Ubunutu/Debian over RedHat because RedHat has a tendency of putting customized fixes and features that are useless and in a lot of cases buggy.  The Fedora Core has reduced the buggy part somewhat, but not the feature part.

Also, In RedHat distribution you may not be able to find some of the restricted drives that are packaged with Ubuntu, such as NVIDIA drivers for the Quadro FX cards.

So for me Ubuntu is a preferred choice.

---

### Post by XCan on 2009-09-25
You could also try out CentOS that is supposed to reflect the Red Hat enterprise distro, however as it's not built by RH it's free.

---

### Post by Simian Man on 2009-09-25
> **karlson said:**
> 
In my personal experience I would take Ubunutu/Debian over RedHat because RedHat has a tendency of putting customized fixes and features that are useless and in a lot of cases buggy.  The Fedora Core has reduced the buggy part somewhat, but not the feature part.
That is actually completely backwards.  Red Hat/Fedora always tries to use upstream packages with little to no modification.  Debian and, by extension, Ubuntu are the opposite: they modify the applications in huge ways and often times not for the better.  That's how Iceweasel came about, they ****** up Firefox so badly that Mozilla wouldn't even let them call it "Firefox".  That OpenSSL fiasco also comes to mind here.

> **karlson said:**
> Also, In RedHat distribution you may not be able to find some of the restricted drives that are packaged with Ubuntu, such as NVIDIA drivers for the Quadro FX cards.
Drivers are in the RPM Fusion directory.  This has to be [setup]("http://rpmfusion.org/Configuration"), but it is still not hard to install.


BTW to clarify:
Red Hat Linux = An old distribution put out by Red Hat (ended in 2003 iirc)
Fedora Linux = The continuation of Red Hat Linux by Red Hat + the community, can be bleeding edge.
Red Hat Enterprise Linux = The supported distro that costs money but is very stable and has great vendor supprt.
CentOS = a free community version of RHEL which has no support, but is otherwise completely the same.

If you want to pay for support, choose RHEL.  If you want free and cutting edge, choose Fedora.  If you want free and stable choose CentOS.

---

### Post by Liolikas on 2009-09-25
ya

---

### Post by karlson on 2009-09-25
> **Simian Man said:**
> That is actually completely backwards.  Red Hat/Fedora always tries to use upstream packages with little to no modification.  Debian and, by extension, Ubuntu are the opposite: they modify the applications in huge ways and often times not for the better.  That's how Iceweasel came about, they ****** up Firefox so badly that Mozilla wouldn't even let them call it "Firefox".  That OpenSSL fiasco also comes to mind here.

With Fedora that may be the case as I haven't looked at RedHat Distros for close to a year now (and happier for it), but RedHat Linux and RedHat Enterprise Linux it wasn't, up to RHEL 5.


> Drivers are in the RPM Fusion directory.  This has to be [setup]("http://rpmfusion.org/Configuration"), but it is still not hard to install.

Easier if it's already on the CD or within a standard package distribution, would you not agree?

---

### Post by TrakerJon on 2009-09-25
> **goofynewf said:**
> I am currently using Ubuntu 8.04 on my Dell mini.  I like Ubuntu and I am going to install it on one of my desktops at home.  My husband wants to install Red Hat.   From what I have read, Ubuntu is more user friendly than other Linux programs.   

Can someone tell me their thoughts on the two, pros and cons.
 
 
Thanks!

Fedora Core (Red Hat) is rpm based much like SuSe and Mandriva. I've run into many an issue with having to find file dependancies on Fedora that are often hard to resolve. Ubuntu is much more user friendly when it comes to installing additional programs and applications. My post called "Ubuntu Desktop Computing Made Easy" should help you a great deal to win your argument [http://ubuntuforums.org/showthread.php?t=1181327]("http://ubuntuforums.org/showthread.php?t=1181327") Enjoy!

---

### Post by credobyte on 2009-09-25
There's only 1 thing you should remember - while Ubuntu offers some kind of 'click one, get ten' style of packaging, Fedora will require a little bit more knowledge ( finding appropriate packages, troubleshooting problems, etc. ).

---

### Post by Liolikas on 2009-09-25
Not true Fedora also have kpackagekit yum etc. nice tools.

---

### Post by credobyte on 2009-09-25
> **Liolikas said:**
> Not true Fedora also have kpackagekit yum etc. nice tools.

Did I said it comes with no package manager ? :neutral:

---

### Post by Liolikas on 2009-09-25
No but still Fedora package install is as simple as in Ubuntu. Find thing mark arrow and aply.

---

### Post by Simian Man on 2009-09-25
> **TrakerJon said:**
> Fedora Core (Red Hat) is rpm based much like SuSe and Mandriva. I've run into many an issue with having to find file dependancies on Fedora that are often hard to resolve. Ubuntu is much more user friendly when it comes to installing additional programs and applications.

This is quite a common misconception on this forum, and it isn't at all true.  It just comes from the fact that you know how Debian works but not how rpm does.  Yum and Packagekit are just as easy to use as apt and synaptic - actually I'd argue they are easier.

When I first used Ubuntu, I was looking for the package manager and saw "Add/Remove" in the menu and thought that was it.  That program had nothing that I was looking for and frustrated me a lot.  It's not really obvious to a beginner that I should have launched Synaptic which isn't even close by in the menus.  I was also frustrated by the fact that there was "apt-get", "apt-cache" and aptitude all with different insufficiencies.

Things that you know are *always* easier than things that you don't.

---

### Post by Simian Man on 2009-09-25
> **karlson said:**
> With Fedora that may be the case as I haven't looked at RedHat Distros for close to a year now (and happier for it), but RedHat Linux and RedHat Enterprise Linux it wasn't, up to RHEL 5.
Well back when I used the original Red Hat, I wasn't such a power user, so I didn't know that.  But nowadays Red Hat and Fedora *are* upstream for major parts of the Linux ecosystem so if you want "official" packages, Fedora is about as close as you'll get w/o building the software yourself.

At any rate Debian and Ubuntu change things around way more than any other distro.  Why do you think it took them 3 months to package Firefox 3.5??

> **karlson said:**
> Easier if it's already on the CD or within a standard package distribution, would you not agree?

Yep definitley.  Are restricted drivers on the Ubuntu CD or do you have to download them?

Unfortunately Fedora, as a US business, has to be much more careful not to break any US laws.  RPM Fusion makes it quite easy to get around this though.  And most Ubuntu users have no trouble adding Medibuntu repos right?

---

### Post by lykwydchykyn on 2009-09-25
What's your husband's reasoning on wanting to install red hat?  And does he mean red hat or fedora?

---

### Post by Liolikas on 2009-09-25
I think it is time to start distrowarz now. 
[IMG]http://www.lorenzgames.com/gamesdb/k/kill-smile.gif[/IMG]

---

### Post by snowpine on 2009-09-25
Install both. As long as your hard drive is big enough (20gb or larger), you can set up a dual boot. You can use Ubuntu, and your husband can use Red Hat.

:)

---

### Post by goofynewf on 2009-09-25
> **lykwydchykyn said:**
> What's your husband's reasoning on wanting to install red hat? And does he mean red hat or fedora?
 
He works at a university and gets it free.   He uses it on the servers so he has some familiarity with it.   I like Ubuntu and will probably just stick with it.   We have a few desktops so he can install Red Hat on another one.

---

### Post by ddrichardson on 2009-09-25
I wrote a blog post describing Fedora 11 from the point of view of someone using Ubuntu - [http://blog.lynxworks.eu/20090901/fedora-from-an-ubuntu-point-of-view](http://blog.lynxworks.eu/20090901/fedora-from-an-ubuntu-point-of-view)

It drew a lot of flack from someone in the Fedora community but most Ubuntu users told me they appreciated it.

---

### Post by lykwydchykyn on 2009-09-25
> **goofynewf said:**
> He works at a university and gets it free.   He uses it on the servers so he has some familiarity with it.   I like Ubuntu and will probably just stick with it.   We have a few desktops so he can install Red Hat on another one.

I take that to mean it's the commercial RHEL version, not Fedora.  In which case, it's probably worth a spin just out of sheer curiosity, but you'll probably find the applications are quite a bit older than Ubuntu's.  

A quick look at this page: [http://distrowatch.com/table.php?distribution=redhat](http://distrowatch.com/table.php?distribution=redhat)  will show you the versions of common applications to compare.

---

### Post by t0p on 2009-09-25
> **goofynewf said:**
> He works at a university and gets it free.   He uses it on the servers so he has some familiarity with it.   I like Ubuntu and will probably just stick with it.   We have a few desktops so he can install Red Hat on another one.

Probably the best solution.  Your hubby uses Red Hat, therefore he'll think Red Hat's best.  You use Ubuntu, therefore you'll think Ubuntu's best.  Folk seem to always prefer what they know over what they don't.

But I would suggest that you try out each other's choice - you have a play on his computer and let him go on yours.  Linux distros aren't all the same; each has its own feel and philosophy.  So check out your man's Red Hat machine, maybe you'll get to like it.  And vice-versa.

---

### Post by FunkyRes on 2009-09-28
I prefer CentOS / RHEL for anything server related.
I prefer RPM to .deb's.

But I think for a desktop, Ubuntu is better than CentOS / RHEL.
I haven't tried a recent enough Fedora, but Fedora seems to EOL way too quickly (why I left it and went to CentOS)

---

### Post by FunkyRes on 2009-09-28
With respect to red hat modifying stuff - I do a lot of package building on CentOS. Some of this includes patching RPM's.

While it is true that most RHEL RPM's have a lot of patches, those patches are almost always bug fixes, and the ChangeLog usually specifies exactly which bug an RHEL customer experienced that the patch fixes.

Many of the patches are backport bug fixes. With a few exceptions, RHEL freezes version and thus backports upstream fixes to issues.

This actually makes for a very stable system, you don't end up needing to recompile your own builds because a shared library changed, for example.

---

### Post by slakkie on 2009-09-28
I've tried Fedora for a real short while. I did not have any particular issue except for the fact the installer has problems with extended partitions. Which was really annoying since my homedir is located within that extended partition... 

Besides that, the Fedora experience was great, the only minor issue was the upgrading of packages, which took a bit longer then on Debian/Ubuntu. But other then that.. Nice. Upgrading to the latest development release also went smooth.

---

### Post by W2IBC on 2009-09-28
> **goofynewf said:**
> He works at a university and gets it free.   He uses it on the servers so he has some familiarity with it.   I like Ubuntu and will probably just stick with it.   We have a few desktops so he can install Red Hat on another one.

people like to keep to what they know.

i tried fedora, it was ok i thought i just prefer debian/ubuntu we get used to something and thats just what we prefer to use.

like I prefer KDE3 dont care much for KDE4 so i install KDE3

---

### Post by tjwoosta on 2009-09-28
Fedora/Redhat in my opinion are better suited for an enterprise environment. 

* Strict default firewall setup and GUI tools to manage firewall.
* SElinux management tools.
* Palimpsest disk utility  (warns you when drives are starting to fail long before they actually fail.) 
* Network login and authentication tools such as nis, ldpa, hesiod, winbind, and kerberos.
* Smartcard and fingerprint reader support.

They basically come by default with just about everything you would need in an Enterprise environment. Many Professional System Administrators would prefer redhat or fedora.

Ubuntu is more geared towards average users desktop environment.

---

