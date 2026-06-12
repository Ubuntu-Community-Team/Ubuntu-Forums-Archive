---
title: "Centrally Manage Updates? / Breathe life into old hardware"
date: 2014-08-17
forum: New to Ubuntu
---

### Post by ben5 on 2014-08-17
We are interested in putting Ubuntu on some old desktop hardware that used to run XP.

We are a call center and these PC's are used mostly to telnet/ssh into a server... to view text based surveys, or sometimes to go to web pages to view surveys there. 

Two main questions... 

1. I think ubuntu has different desktops.  I think unity is the more flashy but probably heavy one... Whats the most light weight no frills one?  

2. We have clients that require centralized patch management.  Is there a way to centrally manager and report on the update status of hundreds of ubuntu desktops?

---

### Post by JKyleOKC on 2014-08-17
I can only answer your first question: The two lightest desktops are Lubuntu and Xubuntu. I'm using Xubuntu and find it more than adequate for fully professional needs. Lubuntu, I'm told, is slightly lighter, but not quite as mature. I chose Xubuntu originally to replace a Mandrake system that ran with less than 100 MB of RAM and a 20-GB drive; it ran nicely for me on systems converted from Win98SE with 256 MB of RAM and 40-GB drives, so anything capable of running XP will fairly fly using Xubuntu. It has far less "eye candy" than does Unity or Kubuntu (KDE), but the interface doesn't resemble Windows at all if that's a problem...

I'm sure that a centralized patch management system is possible, but have no idea how you would implement it. I do know that this system is used in other call centers, so I'm confident you'll get responses telling you much more...

---

### Post by ubudog on 2014-08-17
+1 to Xubuntu, it runs great on all the computers I have installed it on, and is lightweight and fast.

To answer your second question, Canonical offers the [Landscape]("https://landscape.canonical.com/") management tool that may help you.

---

### Post by ben5 on 2014-08-17
Thanks!

So is there a downside to using Xubuntu.... I feel like I remember watching someones review of a lot of linux variants and some of the offshoots of main distros had more bugs, etc.   These PC's are all 1Ghz+ 512MB ram, etc... so I think they meet min spects for Ubuntu LTS 14.  But there are different desktops to use within ubuntu right?  Like unity?  Or gnome2 or gnome3.  I feel like I remember there were some more light weight desktop options that came with "Ubuntu" itself.    Will that work?  

If I go with something like Xubuntu is there the same level of support out there?  Does everything work the same (howto's for ubuntu... is there support for xunbuntu etc)

RE landscape... I am having a hard time figuring out pricing... on the main page I dont see pricing until you go over to "Ubuntu Advantage" which seems to be ubuntu support... which is $105 a year per desktop... **does this mean you have to pay for Ubuntu Advantage to use landscape?**  **Or can I get landscape without support? ** 

We have 300+ PC's... its not feasible to pay $30k just for patch management...

---

### Post by sotiris2 on 2014-08-17
I suppose that for identical PCs you could make them boot from a network and have a server to feed them an image of the updated os. [This](https://help.ubuntu.com/community/DisklessUbuntuHowto) seems to be a relevant guide, and there are probably more if you search for it.

---

### Post by JKyleOKC on 2014-08-17
> **ben5 said:**
> Thanks!

So is there a downside to using Xubuntu.... I feel like I remember watching someones review of a lot of linux variants and some of the offshoots of main distros had more bugs, etc.   These PC's are all 1Ghz+ 512MB ram, etc... so I think they meet min spects for Ubuntu LTS 14.  But there are different desktops to use within ubuntu right?  Like unity?  Or gnome2 or gnome3.  I feel like I remember there were some more light weight desktop options that came with "Ubuntu" itself.    Will that work?  They will work, but you will have a lot of bell-and-whistle files installed that you won't really need for your purposes.> 

If I go with something like Xubuntu is there the same level of support out there?  Does everything work the same (howto's for ubuntu... is there support for xunbuntu etc)It's exactly the same level of support from Canonical and there are enough of us Xubuntu users on the forums here to give you good support. You may get suggestions from users of other flavors that don't quite apply to Xubuntu, because its configuration files are rather different (and in general much simpler) but I've never felt unsupported, and I've been using it in a professional installation for seven years now even though my current hardware is quite adequate to run Unity or most anything else.> 

RE landscape... I am having a hard time figuring out pricing... on the main page I dont see pricing until you go over to "Ubuntu Advantage" which seems to be ubuntu support... which is $105 a year per desktop... **does this mean you have to pay for Ubuntu Advantage to use landscape?**  **Or can I get landscape without support? ** 
I'm not familiar with "landscape" so cannot comment with any confidence, but I would be amazed if it's limited to paying customers. The name "Ubuntu" itself implies free sharing between all people.

[COLOR="#FF0000"]EDIT: I clicked the highlighted "Landscape" in the post above, which took me to the sales page for the package, and apparently it IS limited to paying customers. However it might well be worth it to contact the sales folk and get definite cost information. Most support companies offer site licenses or something similar at rather steep discounts when you have so many users involved![/COLOR]
> 
We have 300+ PC's... its not feasible to pay $30k just for patch management...Agreed. The "update manager" that comes as part of each system package can be configured for silent behind-the-scenes upgrades, and you can limit those to just what's needed for security. This might be something you can live with. Best bet would be to download Xubuntu's live-CD/install package, put it on a single test system, and try everything out. That would cost you only a bit of time, and would almost certainly give you additional more detailed questions to ask here!

We're all volunteers, not part of Canonical's sales staff; the only reason it might sound otherwise is that all of us who post regularly are quite happy with the product and are paying forward by assisting others to get better results with it!

---

### Post by grahammechanical on 2014-08-17
Ubuntu and its official flavours are updated from the same archives/repositories. Here are the desktop user interfaces that come with Ubuntu and its flavours

Ubuntu = Unity

Xubuntu = Xfce

[http://xubuntu.org/](http://xubuntu.org/)

[http://www.xfce.org/](http://www.xfce.org/)

Kubuntu = KDE

[http://www.kubuntu.org/](http://www.kubuntu.org/)

[http://www.kde.org/](http://www.kde.org/)

Lubuntu = LXDE

[http://lubuntu.net/](http://lubuntu.net/)

[http://lxde.org/](http://lxde.org/)

Ubuntu Gnome = Gnome 3 shell

[http://ubuntugnome.org/](http://ubuntugnome.org/)

[http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

For the record, there are other Ubuntu flavours - Ubuntu Studio, Mythbuntu, Edubuntu.

Your choice comes down Xubuntu or Lubuntu.

> [COLOR=#000000]So is there a downside to using Xubuntu[/COLOR]

I would not agree with that. What are you thinking of? Xubuntu more buggy than some other operating system? I do not think so. Bug fixes in the many components that make up Ubuntu are also pushed into Xubuntu. The differences are in the User Interface, the system utilities and some default applications.

To put it factually. You have 300 PCs using an unsupported OS and that most probably are not powerful enough to run a graphic intensive UI. And you are doubting Xubuntu which comes free to download, copy, install and use on as many machines as you like?

Regards.

---

### Post by ian-weisser on 2014-08-17
They always ask such questions until they finally download a Live image onto a USB stick, boot from the USB stick, and try it 100% risk-free.

"Centralized patch management" depends upon the patches to be managed. *buntu is a package-manager environment, which might make things much easier...or much more complex. You won't know until you try.

---

### Post by ben5 on 2014-08-17
> **ian-weisser said:**
> They always ask such questions until they finally download a Live image onto a USB stick, boot from the USB stick, and try it 100% risk-free.

"Centralized patch management" depends upon the patches to be managed. *buntu is a package-manager environment, which might make things much easier...or much more complex. You won't know until you try.
Huh?  I am thoroughly confused by this comment.... 

I am looking for patch management software... i.e. software that ensures that workstations are fully up to date with all patches for all software on them... and that has a central console that reports on the status of this.  

GFI Languard would be an example of the type of thing I am looking for except for linux. 

It seems like a straight forward question.  What do you mean "depends upon the patches to be managed."?

---

### Post by ubudog on 2014-08-17
GFI Languard seems to claim to support Linux:
[http://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard/specifications](http://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard/specifications)

---

### Post by JKyleOKC on 2014-08-17
> **ben5 said:**
> Huh?  I am thoroughly confused by this comment.... 

I am looking for patch management software... i.e. **software that ensures that workstations are fully up to date with all patches for all software on them... and that has a central console that reports on the status of this**.  

GFI Languard would be an example of the type of thing I am looking for except for linux. 

It seems like a straight forward question.  What do you mean "depends upon the patches to be managed."?Based on the part of your reply that I highlighted, I believe that setting up the "update-manager" package to check for and automatically install security-related updates invisibly, every day, will handle the first requirement -- but to include "all software" you might want to also include other updates. As for reporting the status, there's a free application called "logwatch" that can be configured to report all updates by e-mailing to a central location on your network. I'm sure that other similar, free-as-in-beer, applications exist, but I've only used logwatch since discovering its existence. It can also keep track of resource usage and many other things if you so desire.

"Depends on patches" refers to the fact that *buntu repositories divide updates into a number of categories. Most critical is "security" but there's also "recommended," "main," "backports," "proposed," and "universe." Some are things you wouldn't usually want to put into a production machine; others are somewhat optional.

The "They always ask such questions" part of the comment wasn't intended to be derogatory, I'm sure, although it easily could be interpreted that way. Many system administrators in enterprise-wide environments like to (or must) wait until new updates have completed reliability tests, before propagating them to their entire network. I personally tend to do this even though only my own small business would be harmed by an update gone crazy. To deal with this would require a more sophisticated update management system than I outline above, allowing you to obtain any new updates, perform your tests, and only then release them to the production network.

Such a system would be very easy to implement in any of the *buntu flavors, but would require changing the repository list in each terminal to point only to your local repository rather than to the official mirror for your area. This would be a one-time change at each terminal; then your control would be maintained by your own decision about when to copy the new update packages into your local repository.

All of this will, of course, make more sense once you've done a test installation and begun to learn the jargon associated with Debian-based distributions -- it's similar to, but different from, the language used by folk maintaining Windows, just as theirs differs from that of mainframe technicians. Having been all three, with DEC minis tossed in for good measure, I can help translate while you get there!

---

