---
title: "Switching From Ubuntu To Lubuntu &amp; Others"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by Shadius on 2012-06-23
Hey everybody! :)

I'm thinking of switching from my current Ubuntu 12.04 LTS to Lubuntu 12.04 LTS. However, being that I'm fairly new to Linux and such, I don't know how to proceed. I came across a thread here that stated that I can use Synaptic Package Manager to install *Lubuntu-core* or *Lubuntu-desktop*, something like that. I checked in Synaptic Package Manager for all things Lubuntu, and received a bunch of results. I don't really know what's needed. I'd like some guidance in transitioning. Note that I'd still want the option to use Ubuntu 12.04 LTS as well as Lubuntu 12.04 LTS. Is this just a matter of installing LXDE? If so, please explain. Another thing I was thinking of was to run Lubuntu in Virtualbox to see if I like it and decide whether I want to switch to it or not. I'm also thinking of trying out other operating systems like Kubuntu, Xubuntu and Linux Mint. That's why I'm thinking of using Virtualbox. 

I've said a lot so to sum up, first, how does one transition to using Lubuntu from Ubuntu and, second, how do I set up Virtualbox? Thank you kindly.

---

### Post by Bucky Ball on 2012-06-23
Install 'lxde' from Synaptics and see if you like it. That will give you the desktop environment at least. Install, log out, choose 'Lxde' from the Sessions popup, log in. 

You could install the Lubuntu components ... but, you would be missing one of the major benefits of installing such an OS in the first place; lack of bloat, speed and ease of use. You will have a regular Ubuntu install, plus the extra stuff you need for Lubuntu making things possibly slower than they are now (all Ubuntu apps will appear in the menus when you are booted into Lxde).

But having said all this, yes, you basically only need lubuntu-desktop and that's it. Everything else will be dragged in. ;)

My preference would be to clear some space on a hard drive and install it fresh there. You'll certainly notice the difference then. (Or you could try as a virtual machine inside your current install.) Running it from its own partition will give you access to the /home folder and others on your current install. 

If you already have a /home partition then you can use that one for the Lubuntu install also (as well as the existing /swap).


PS: Easiest? Try it from the LiveCD. Install if you like it.

---

### Post by Shadius on 2012-06-23
> **Bucky Ball said:**
> Install lxde and see if you like it. That will give you the desktop environment at least. Install, log out, choose 'Lxde' from the Sessions popup, log in. 

You could install the Lubuntu components ... but, you would be missing one of the major benefits of installing such an OS in the first place; lack of bloat, speed and ease of use. You will have a regular Ubuntu install, plus the extra stuff you need for Lubuntu making things possibly slower than they are now (all Ubuntu apps will appear in the menus when you are booted into Lxde).

But having said all this, yes, you basically only need lubuntu-desktop and that should be it. Everything else will be dragged in. ;)

My preference would be to clear some space on a hard drive and install it fresh there. You'll certainly notice the difference then.

Thanks for the reply Bucky Ball. So all I need to do is
```
sudo apt-get install lubuntu-desktop
``` 
and that'll install LXDE, log out and select Lubuntu from the Login Screen?

---

### Post by Bucky Ball on 2012-06-23
> **Shadius said:**
> Thanks for the reply Bucky Ball. So all I need to do is
```
sudo apt-get install lubuntu-desktop
```and that'll install LXDE, log out and select Lubuntu from the Login Screen?

NO. That will install Lubuntu complete. Installing 'lxde' will install only the desktop environment.

Please re-read my last post as I have changed it a bit. ;)

(PS: Yes, ```
sudo apt-get install lubuntu-desktop
``` is the correct command to install Lubuntu and all its packages and dependencies.)

---

### Post by Shadius on 2012-06-23
> **Bucky Ball said:**
> NO. That will install Lubuntu complete. Installing 'lxde' will install only the desktop environment.

Please re-read my last post as I have changed it a bit. ;)

(PS: Yes, ```
sudo apt-get install lubuntu-desktop
``` is the correct command to install Lubuntu and all its packages and dependencies.)

Oh okay. I will install just LXDE for now to test out the interface and see if I prefer it over my current Ubuntu setup.

---

### Post by vasa1 on 2012-06-23
> **Shadius said:**
> ..
I'm thinking of switching ... other operating systems like Kubuntu, Xubuntu and Linux Mint. That's why I'm thinking of using Virtualbox. 
...
You've not given the reasons for "thinking of switching" ... . I'm making that point because if you want to go for something **lighter**, I'm not sure that Kubuntu would be a candidate.

---

### Post by Shadius on 2012-06-23
> **vasa1 said:**
> You've not given the reasons for "thinking of switching" ... . I'm making that point because if you want to go for something **lighter**, I'm not sure that Kubuntu would be a candidate.

You're right vasa1, my reason for switching to Lubuntu is to have a lighter system, and also just to experience the other operating systems.

---

### Post by seppalta on 2012-06-23
LXDE is a simple desktop to add to another distribution because in total it consists of only about 10 or 11 components.  The main component is lxde-core.  That will get you the file browser, lxpanel (taskbar),  session manager, windows manager and screensaver, which is a working desktop.  To see what you might add from there, see [http://douwil7.100webspace.net/linux/Debian.htm](http://douwil7.100webspace.net/linux/Debian.htm), which is a complete recipe for making LXDE the only desktop on a Debian system.    If you do not want to lose the Ubuntu desktop, then just skip the "remove" part of the recipe.  

To use and set-up an LXDE desktop, see [URL="http://douwil7.100webspace.net/linux/Tuning.html"]http://douwil7.100webspace.net/linux/Tuning.html .
[/URL]

---

### Post by MG&amp;TL on 2012-06-23
> **Shadius said:**
> Oh okay. I will install just LXDE for now to test out the interface and see if I prefer it over my current Ubuntu setup.

Bear in mind that Lubuntu sets up themes, tweaks and settings when you install it fully.
Raw LXDE looks like a developer had a bad day. :(

Basically, it'll look better when you install fully.

---

### Post by vasa1 on 2012-06-23
> **MG&TL said:**
> Bear in mind that Lubuntu sets up themes, tweaks and settings when you install it fully.
Raw LXDE looks like a developer had a bad day. :(

Basically, it'll look better when you install fully.
I don't know about Lubuntu but when I installed Xfce 4.10 (launchpad.net/~xubuntu-dev/+archive/*xfce-4.10) on top of Ubuntu 12.04, there wasn't much of a problem.

---

### Post by MG&amp;TL on 2012-06-23
> **vasa1 said:**
> I don't know about Lubuntu but when I installed Xfce 4.10 (launchpad.net/~xubuntu-dev/+archive/*xfce-4.10) on top of Ubuntu 12.04, there wasn't much of a problem.

[Lubuntu]("http://www.google.com/imgres?um=1&hl=en&client=ubuntu&sa=N&channel=fs&gl=uk&biw=1301&bih=647&tbm=isch&tbnid=kbxhB9lGrUyFsM:&imgrefurl=http://en.wikipedia.org/wiki/Lubuntu&docid=3wNavuO2gSnmIM&imgurl=http://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Lubuntu_12_04.png/300px-Lubuntu_12_04.png&w=300&h=176&ei=gPzlT6SaCo_w8QPAn5jWCg&zoom=1&iact=rc&dur=301&sig=102260030224065349129&page=1&tbnh=90&tbnw=154&start=0&ndsp=18&ved=1t:429,r:0,s:0,i:77&tx=33&ty=17")
[LXDE]("http://www.google.com/imgres?um=1&hl=en&client=ubuntu&sa=N&channel=fs&gl=uk&biw=1301&bih=647&tbm=isch&tbnid=ZYqTJzLgMSr0ZM:&imgrefurl=http://linux.softpedia.com/progScreenshots/Lubuntu-Screenshot-50492.html&docid=vauPryjcUdNKCM&imgurl=http://i1-linux.softpedia-static.com/screenshots/Lubuntu_1.jpg&w=800&h=600&ei=gPzlT6SaCo_w8QPAn5jWCg&zoom=1&iact=hc&vpx=533&vpy=196&dur=330&hovh=171&hovw=228&tx=91&ty=67&sig=102260030224065349129&page=1&tbnh=128&tbnw=171&start=0&ndsp=18&ved=1t:429,r:2,s:0,i:83")

Maybe Xfce is different, but LXDE really does look bad.

---

### Post by Shadius on 2012-06-23
So I installed LXDE from Ubuntu Software Center, logged into it, and my first impression of it was yuck!! :lolflag: It reminds me so much of Windows, which is what I don't want! However, I noticed a major difference in speed. Everything is faster when compared to when I was using GNOME Classic (No effects). I also noticed that there's no Global Menu in the LXPanel. :( Is it possible to get it? I really miss it. Also, I began to customize the panels and I accidentally removed the "Shut Down" icon, or "Power" icon, whatever it is called, anyone know how to get it back or even restore the default LXPanel and start from fresh again?

So far, I'm liking LXDE with Ubuntu. Maybe with a little tweaking, I can make it look how I want to.

---

### Post by Bucky Ball on 2012-06-24
You can try xfce also by installing xfce4. That has plenty of flexibility and is also fast. ;)

---

### Post by kansasnoob on 2012-06-24
IMHO installing DE's such as 'lxde', 'xfce4', 'gnome', etc is NOT a good idea. These are generally the versions of those DE's available in either Debian stable or testing, although it can vary - particularly due to gtk3 compatibility issues. Remember we are based on Debian and many of the devs work both for Ubuntu and Debian, etc ;)

I think it would be much wiser to follow the paths in the Playing Around section here:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Not sure how exactly you'd clean up after installing 'lxde' as you did, I'd need to see the applicable apt log to figure that out.

You should also know that Lubuntu 12.04 is not LTS, it's only supported for 18 months. Xubuntu 12.04 is a 3 year LTS, but Ubuntu 12.04 itself is a 5 year LTS.

---

### Post by Shadius on 2012-06-24
> **Bucky Ball said:**
> You can try xfce also by installing xfce4. That has plenty of flexibility and is also fast. ;)

Might get rid of LXDE and try XFCE. LXDE is weird :lolflag: I liked that I was able to make the panels transparent in LXDE, but I couldn't do that in GNOME Classic (No effects). :confused: Also, it really sucks that there's no "Return To Default" option for going back to the default panel settings in case you messed up the panel, in my case, removed the "Power" icon. It does feel like the developers just dropped LXDE and did something else. That "Other" menu was huge!!

---

### Post by Shadius on 2012-06-24
> **kansasnoob said:**
> 
Not sure how exactly you'd clean up after installing 'lxde' as you did, I'd need to see the applicable apt log to figure that out.

So cleaning up this LXDE would take some effort now? ](*,) Oh gosh, I wish I knew that before I installed it.

---

### Post by Bucky Ball on 2012-06-24
Transparent panes in xfce. ;)

---

### Post by Shadius on 2012-06-24
> **Bucky Ball said:**
> Transparent panes in xfce. ;)

What about Global Menu? I noticed LXDE didn't have that.

---

### Post by afixane on 2012-06-24
You can add wrapper for global menu in XFCE, but in Precise, you'll need edit some of it source code (from libindicator6 to libindicator7) and compile it yourself.

---

### Post by Shadius on 2012-06-24
> **afixane said:**
> You can add wrapper for global menu in XFCE, but in Precise, you'll need edit some of it source code (from libindicator6 to libindicator7) and compile it yourself.

Hmm....compiling is a whole new thing to me.

---

### Post by vasa1 on 2012-06-24
> **Shadius said:**
> Might get rid of LXDE and try XFCE. ...
If you do, then [http://forum.xfce.org/](http://forum.xfce.org/) is your friend. At the top right are other useful links.
As I've said elsewhere, the documentation is quite decent. Plus, we have **Toz** :)

---

### Post by Shadius on 2012-06-24
> **vasa1 said:**
> If you do, then [http://forum.xfce.org/](http://forum.xfce.org/) is your friend. At the top right are other useful links.
As I've said elsewhere, the documentation is quite decent. Plus, we have **Toz** :)

Toz?

---

### Post by vasa1 on 2012-06-24
> **Shadius said:**
> Toz?

Ubuntu member, active here, very helpful on matters Xfce (and other things).

---

### Post by Shadius on 2012-06-24
> **vasa1 said:**
> Ubuntu member, active here, very helpful on matters Xfce (and other things).

Oh okay.  Also, does Conky work well in XFCE? I had to change something in my Conky script in order to get it to work in LXDE.

---

### Post by vasa1 on 2012-06-24
> **Shadius said:**
> Oh okay.  Also, does Conky work well in XFCE? I had to change something in my Conky script in order to get it to work in LXDE.
I don't know. Never used Conky because I don't know why I should need it though a lot of people simply love it!

---

### Post by Shadius on 2012-06-24
> **vasa1 said:**
> I don't know. Never used Conky because I don't know why I should need it though a lot of people simply love it!

:lolflag: Yeah, I've recently started using it and like it so far. Since I'll probably uninstall LXDE, how would I install XFCE? Should I go to Ubuntu Software Center, search for XFCE and install it that way?

---

### Post by vasa1 on 2012-06-24
> **Shadius said:**
> :lolflag: Yeah, I've recently started using it and like it so far. Since I'll probably uninstall LXDE, how would I install XFCE? Should I go to Ubuntu Software Center, search for XFCE and install it that way?
I installed it from here: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

The USC still has 4.8.

---

### Post by Shadius on 2012-06-24
> **vasa1 said:**
> I installed it from here: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

The USC still has 4.8.

Thanks.

---

### Post by MG&amp;TL on 2012-06-24
Could I just reiterate that LXDE looks UGLY. BUt Lubuntu looks fairly nice. So you could at least try Lubuntu from a USB or whatever, that way you might get a fair representation of what LXDE can do. Also bear in mind that Xfce isn't as light as LXDE.

Global menu is unfortunately an Ubuntu-only thing, with some hacks for Xfce.

Choose whatever works for you, just giving an opinion.

---

### Post by Shadius on 2012-06-24
> **MG&TL said:**
> Could I just reiterate that LXDE looks UGLY. BUt Lubuntu looks fairly nice. So you could at least try Lubuntu from a USB or whatever, that way you might get a fair representation of what LXDE can do. Also bear in mind that Xfce isn't as light as LXDE.

Global menu is unfortunately an Ubuntu-only thing, with some hacks for Xfce.

Choose whatever works for you, just giving an opinion.

I agree! LXDE was ugly!! Really ugly. But I thought Lubuntu uses LXDE, no? Is it not the same thing? :confused:

---

### Post by sudodus on 2012-06-24
> **Shadius said:**
> I agree! LXDE was ugly!! Really ugly. But I thought Lubuntu uses LXDE, no? Is it not the same thing? :confused:
No, basic LXDE is not the same as the tweaked version of the complete Ubuntu flavour Lubuntu.

I repeat what was written before: Try Lubuntu live from a CD or USB drive. Then nothing will happen to your hard disk drive.

But it is also possible to install the desktop
```
sudo apt-get install lubuntu-desktop
```
It is described by *psychocats* how to remove it.
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/pureubuntu_[/COLOR]]("http://www.psychocats.net/ubuntu/pureubuntu")

---

### Post by Shadius on 2012-06-24
> **sudodus said:**
> No, basic LXDE is not the same as the tweaked version of the complete Ubuntu flavour Lubuntu.

I repeat what was written before: Try Lubuntu live from a CD or USB drive. Then nothing will happen to your hard disk drive.

But it is also possible to install the desktop
```
sudo apt-get install lubuntu-desktop
```
It is described by *psychocats* how to remove it.
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/pureubuntu_[/COLOR]]("http://www.psychocats.net/ubuntu/pureubuntu")

Ohhhh. Well, here's the thing, I ran out of CDs/DVDs and don't have any spare USB Flash drives to make a LiveUSB, that's why I also mentioned setting up Virtualbox. I thought maybe Virtualbox would be good for these types of things, like playing around with other operating systems. Could I use the Virtualbox method?

---

### Post by sudodus on 2012-06-24
> **Shadius said:**
> Ohhhh. Well, here's the thing, I ran out of CDs/DVDs and don't have any spare USB Flash drives to make a LiveUSB, that's why I also mentioned setting up Virtualbox. I thought maybe Virtualbox would be good for these types of things, like playing around with other operating systems. Could I use the Virtualbox method?
Yes, provided that your installed system is powerful enough to host a reasonable virtual machine as guest. Many of us use VirtualBox for a first test of new distros. It is straight-forward to boot in VirtualBox from an iso file.

But it is also possible to boot directly from some iso files, for example [KLX]Ubuntu 11.10 and newer with the following method:
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

---

### Post by Bucky Ball on 2012-06-24
Yes, but each virtual machine needs RAM. i.e. if you have 4Gb of RAM and intend running a virtual machine then each OS would have 2Gb of RAM (if you split it that way).

If you intend running a host and three virtual machines they end up with 1Gb RAM each.

---

### Post by MG&amp;TL on 2012-06-24
> **Shadius said:**
> Ohhhh. Well, here's the thing, I ran out of CDs/DVDs and don't have any spare USB Flash drives to make a LiveUSB, that's why I also mentioned setting up Virtualbox. I thought maybe Virtualbox would be good for these types of things, like playing around with other operating systems. Could I use the Virtualbox method?

You could, or you could just install the desktop, then remove it if you don't like it.

To prove it's not ugly, here's a screenshot of Lubuntu 12.04: [http://distrowatch.com/images/cgfjoewdlbc/lubuntu.png](http://distrowatch.com/images/cgfjoewdlbc/lubuntu.png)

All the Lubuntu team basically does is provide a set of lightweight programs, and make LXDE prettier.

---

### Post by Shadius on 2012-06-24
> **MG&TL said:**
> You could, or you could just install the desktop, then remove it if you don't like it.

To prove it's not ugly, here's a screenshot of Lubuntu 12.04: [http://distrowatch.com/images/cgfjoewdlbc/lubuntu.png](http://distrowatch.com/images/cgfjoewdlbc/lubuntu.png)

All the Lubuntu team basically does is provide a set of lightweight programs, and make LXDE prettier.

Couldn't view that image. Got a "Forbidden" page.

---

### Post by Shadius on 2012-06-24
> **sudodus said:**
> Yes, provided that your installed system is powerful enough to host a reasonable virtual machine as guest. Many of us use VirtualBox for a first test of new distros. It is straight-forward to boot in VirtualBox from an iso file.

But it is also possible to boot directly from some iso files, for example [KLX]Ubuntu 11.10 and newer with the following method:
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

> **Bucky Ball said:**
> Yes, but each virtual machine needs RAM. i.e. if you have 4Gb of RAM and intend running a virtual machine then each OS would have 2Gb of RAM (if you split it that way).

If you intend running a host and three virtual machines they end up with 1Gb RAM each.

Since my computer only has 512 MB of RAM I'm thinking it's not powerful enough to host virtual machines...?

---

### Post by mlentink on 2012-06-24
> **Shadius said:**
> Since my computer only has 512 MB of RAM I'm thinking it's not powerful enough to host virtual machines...?
Don't even try with less than 2GB.

---

### Post by sudodus on 2012-06-24
> **Shadius said:**
> Since my computer only has 512 MB of RAM I'm thinking it's not powerful enough to host virtual machines...?
No, try the other method I described with Lubuntu 12.04, 32-bit

[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

---

### Post by Shadius on 2012-06-24
Okay, thanks everybody! :) Really appreciate all the help. I'm going to remove the ugly LXDE that I have now and install *lubuntu-desktop*. I'm leaning more towards Lubuntu because it's the lightest of the rest of the variants. I'll report back if I run into any problems. Thanks again everyone!

---

### Post by MG&amp;TL on 2012-06-24
> **Shadius said:**
> Okay, thanks everybody! :) Really appreciate all the help. I'm going to remove the ugly LXDE that I have now and install *lubuntu-desktop*. I'm leaning more towards Lubuntu because it's the lightest of the rest of the variants. I'll report back if I run into any problems. Thanks again everyone!

Awesome, let us know how it goes. Weird that you couldn't view that image, it just works for me.

---

### Post by Shadius on 2012-06-26
I uninstalled LXDE via Ubuntu Software Center, but the entries of: **LXDE**, **GNOME/Openbox**, and **Openbox** remain in the login screen, LightDM. I thought to look in Synaptic Package Manager and here's what I found: see screenshot. I've marked the LXDE related packages for complete removal. Also, I've included a screenshot of Ubuntu Software Center confirming that LXDE has been uninstalled. I also looked at what LXDE installs and according to the description given in Ubuntu Software Center they are, *lxde-core, lxappearance, lxinput, lxsession-edit, lxshortcut, gpicview, lxterminal, lxmusic, leafpad*, and *xarchiver*. I've marked these packages for complete removal in Synaptic Package Manager as well. Hope this fixes the problem of having those three entries in LightDM!

---

### Post by Shadius on 2012-06-26
Okay,l so doing that removed the **LXDE** entry from LightDM and leaves me with just **GNOME/Openbox** and **Openbox**. I suspect there's some package that I have to remove to get rid of the other two entries. I have no idea what those packages might be so I think I'll search for any related GNOME/Openbox and Openbox packages in Synaptic Package Manager.

---

### Post by MG&amp;TL on 2012-06-26
> **Shadius said:**
> Okay,l so doing that removed the **LXDE** entry from LightDM and leaves me with just **GNOME/Openbox** and **Openbox**. I suspect there's some package that I have to remove to get rid of the other two entries. I have no idea what those packages might be so I think I'll search for any related GNOME/Openbox and Openbox packages in Synaptic Package Manager.

Have you installed Lubuntu-desktop yet? That'll have dependencies on openbox, as it uses it for the WM.

---

### Post by Shadius on 2012-06-26
> **MG&TL said:**
> Have you installed Lubuntu-desktop yet? That'll have dependencies on openbox, as it uses it for the WM.

No, I haven't done that yet. Right now, I'm just trying to get rid of the LXDE I had previously installed. I have a question, when I had both Synaptic Package Manager and Ubuntu Software Center open, and I was uninstalling something in Ubuntu Software Center, the progress bar would get stuck unless I closed Synaptic Package Manager. Why's this happen? Is this normal? Both applications can't be open at the same time when one is performing a task, or better, Ubuntu Software Center can't perform the task when Synaptic Package Manager is open? Weird...

---

### Post by MG&amp;TL on 2012-06-26
> **Shadius said:**
> No, I haven't done that yet. Right now, I'm just trying to get rid of the LXDE I had previously installed. I have a question, when I had both Synaptic Package Manager and Ubuntu Software Center open, and I was uninstalling something in Ubuntu Software Center, the progress bar would get stuck unless I closed Synaptic Package Manager. Why's this happen? Is this normal? Both applications can't be open at the same time when one is performing a task, or better, Ubuntu Software Center can't perform the task when Synaptic Package Manager is open? Weird...

Well, I wouldn't bother getting rid of LXDE as Lubuntu is based upon it...you'll just be reinstalling with a theme package added.

Yup, when an application accesses APT, it locks it so that you can't do stuff like removing a dependency of package X while you install package X in another program. Having two APT processes running at the same time without locking would not be good.

---

### Post by Shadius on 2012-06-26
> **MG&TL said:**
> Well, I wouldn't bother getting rid of LXDE as Lubuntu is based upon it...you'll just be reinstalling with a theme package added.

Yup, when an application accesses APT, it locks it so that you can't do stuff like removing a dependency of package X while you install package X in another program. Having two APT processes running at the same time without locking would not be good.

Ohhh, okay, but see the panel of LXDE was messed up because I accidentally removed the "Shutdown" icon. So maybe when I install *lubuntu-desktop* it'll be fixed? Plus, I'm learning a bunch about what packages LXDE uses along with Openbox. I do appreciate your tips & suggestions! Keep 'em coming! I actually feel like I know what I'm doing from all this. :D :lolflag:

---

### Post by MG&amp;TL on 2012-06-26
> **Shadius said:**
> Ohhh, okay, but see the panel of LXDE was messed up because I accidentally removed the "Shutdown" icon. So maybe when I install *lubuntu-desktop* it'll be fixed? Plus, I'm learning a bunch about what packages LXDE uses along with Openbox. I do appreciate your tips & suggestions! Keep 'em coming! I actually feel like I know what I'm doing from all this. :D :lolflag:

It should be fixed anyway, but FWIW you can edit the panel applets by right-clicking on the panel->Panel Preferences...

```
apt-cache depends lubuntu-desktop
```

;)

---

### Post by Shadius on 2012-06-26
> **MG&TL said:**
> It should be fixed anyway, but FWIW you can edit the panel applets by right-clicking on the panel->Panel Preferences...

```
apt-cache depends lubuntu-desktop
```

;)

What's FWIW? Yeah, I figured out that I could edit the applets on the panel with right-clicking on it, but my problem was that there was no "Shutdown" applet to add back to the panel. I even made a thread specifically for that issue, but nothing worked. Even restarting the panel didn't work. So here I am, learning the hard way. :D

---

### Post by MG&amp;TL on 2012-06-26
> **Shadius said:**
> What's FWIW? Yeah, I figured out that I could edit the applets on the panel with right-clicking on it, but my problem was that there was no "Shutdown" applet to add back to the panel. I even made a thread specifically for that issue, but nothing worked. Even restarting the panel didn't work. So here I am, learning the hard way. :D

"For What It's Worth". ;)

Hmm...well, install lubuntu-desktop, see if you like it, then we can deal with the applet problem if you give me a link to  your thread. I have a feeling it's called something stupid like 'logout-panel'.

---

### Post by Shadius on 2012-06-26
> **MG&TL said:**
> "For What It's Worth". ;)

Hmm...well, install lubuntu-desktop, see if you like it, then we can deal with the applet problem if you give me a link to  your thread. I have a feeling it's called something stupid like 'logout-panel'.

Here's the link for you to look at: [LXPanel Settings - Get Back "Power Icon]("http://ubuntuforums.org/showthread.php?t=2009061"). Thank you in advance. I tried looking for "Power", "Shutdown", "Logout", "Session", but couldn't find anything. One member, VinDSL, was kind enough to do a screencast to show me how to add it, but I just didn't have that applet, "Shutdown", to add back to the panel. I hope this doesn't happen again when I try the full Lubuntu.

---

### Post by Shadius on 2012-06-26
Success! I have succeeded in removing the **LXDE**, **GNOME/Openbox**, and **Openbox** entries from LightDM. Very happy right now!! :D I used Synaptic Package Manager to search for any packages related to Openbox and marked them for complete removal.

---

### Post by MG&amp;TL on 2012-06-26
> **Shadius said:**
> Success! I have succeeded in removing the **LXDE**, **GNOME/Openbox**, and **Openbox** entries from LightDM. Very happy right now!! :D I used Synaptic Package Manager to search for any packages related to Openbox and marked them for complete removal.

:D

Awesome. Okay, the panel applet thing is weird, as I have that applet too. Maybe the package didn't install quite right or something.

Oh well, keep us posted on your progress.

---

### Post by Shadius on 2012-06-26
> **MG&TL said:**
> :D

Awesome. Okay, the panel applet thing is weird, as I have that applet too. Maybe the package didn't install quite right or something.

Oh well, keep us posted on your progress.

Yeah, I'm thinking something went wrong during installation of LXDE as well. With all the removing of packages that I just did, should I run any maintenance commands? 

Like say:
```
sudo apt-get update
```

or: 
```
sudo apt-get autoremove
```

Anything at all? I want to make sure all my packages are in check and updated.

---

### Post by MG&amp;TL on 2012-06-26
> **Shadius said:**
> Yeah, I'm thinking something went wrong during installation of LXDE as well. With all the removing of packages that I just did, should I run any maintenance commands? 

Like say:
```
sudo apt-get update
```or: 
```
sudo apt-get autoremove
```Anything at all? I want to make sure all my packages are in check and updated.

Updating, upgrading, and autoremoving might help, but aren't compulsory. 
Also bear in mind you're just going to be reinstalling LXDE as soon as you install lubuntu-desktop, so don't worry too much about the administration stuff.

---

### Post by Shadius on 2012-06-26
> **MG&TL said:**
> Updating, upgrading, and autoremoving might help, but aren't compulsory. 
Also bear in mind you're just going to be reinstalling LXDE as soon as you install lubuntu-desktop, so don't worry too much about the administration stuff.

Okay, cool. Just out of curiosity I ran those commands to see if anything would happen and *autoremove* did remove two packages and *upgrade* upgraded one package. 

Here's the output:
```
shadius@shadius-5410US:~$ sudo apt-get autoremove
[sudo] password for shadius: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libfm-data libmenu-cache1
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 1,293 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 294691 files and directories currently installed.)
Removing libfm-data ...
Removing libmenu-cache1 ...
Processing triggers for shared-mime-info ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
shadius@shadius-5410US:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  unity-lens-video
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,094 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unity-lens-video all 0.3.5-0ubuntu1.1 [8,094 B]
Fetched 8,094 B in 0s (43.8 kB/s)     
(Reading database ... 294616 files and directories currently installed.)
Preparing to replace unity-lens-video 0.3.5-0ubuntu1 (using .../unity-lens-video_0.3.5-0ubuntu1.1_all.deb) ...
Unpacking replacement unity-lens-video ...
Setting up unity-lens-video (0.3.5-0ubuntu1.1) ...
shadius@shadius-5410US:~$ 

```

The two packages that were removed were *libfm-data* and *libmenu-cache1*. I don't know what these packages are for exactly, but I can guess that *libfm-data* has to do something with the file manager of LXDE. I also have no idea what *unity-lens-video* is. Maybe you can shed some light on that. :)

---

### Post by MG&amp;TL on 2012-06-26
> **Shadius said:**
> Okay, cool. Just out of curiosity I ran those commands to see if anything would happen and *autoremove* did remove two packages and *upgrade* upgraded one package. 

Here's the output:
```
shadius@shadius-5410US:~$ sudo apt-get autoremove
[sudo] password for shadius: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libfm-data libmenu-cache1
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 1,293 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 294691 files and directories currently installed.)
Removing libfm-data ...
Removing libmenu-cache1 ...
Processing triggers for shared-mime-info ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
shadius@shadius-5410US:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  unity-lens-video
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,094 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unity-lens-video all 0.3.5-0ubuntu1.1 [8,094 B]
Fetched 8,094 B in 0s (43.8 kB/s)     
(Reading database ... 294616 files and directories currently installed.)
Preparing to replace unity-lens-video 0.3.5-0ubuntu1 (using .../unity-lens-video_0.3.5-0ubuntu1.1_all.deb) ...
Unpacking replacement unity-lens-video ...
Setting up unity-lens-video (0.3.5-0ubuntu1.1) ...
shadius@shadius-5410US:~$ 

```The two packages that were removed were *libfm-data* and *libmenu-cache1*. I don't know what these packages are for exactly, but I can guess that *libfm-data* has to do something with the file manager of LXDE. I also have no idea what *unity-lens-video* is. Maybe you can shed some light on that. :)

Indeed I can.

*libfm-data *is part of the backend for PCManFM, LXDE's file manager. It was no longer required for anything when you autoremoved, so it was put up for deletion.

*libmenu-cache *I believe has something to do with the menu applet in lxpanel. I could be wrong, but I think it provides the menu entries. (Applications, terminal, etc.) Again, no longer required without LXDE.

*unity-lens-video* is the Video Lens in Unity (far right by default). Presumably it had an update from upstream for some reason. :)

---

### Post by Shadius on 2012-06-26
> **MG&TL said:**
> Indeed I can.

*libfm-data *is part of the backend for PCManFM, LXDE's file manager. It was no longer required for anything when you autoremoved, so it was put up for deletion.

*libmenu-cache *I believe has something to do with the menu applet in lxpanel. I could be wrong, but I think it provides the menu entries. (Applications, terminal, etc.) Again, no longer required without LXDE.

*unity-lens-video* is the Video Lens in Unity (far right by default). Presumably it had an update from upstream for some reason. :)

Gotcha. Thank you kindly my friend. I dislike PCManFM, or maybe I'm just used to Nautilus. ;) I'm going to take a break for now. Sleep is calling my name. I'll be sure to post back with my progress of installing *lubuntu-desktop*. Thanks for all your help! Greatly appreciated! :)

---

### Post by Bucky Ball on 2012-06-26
Can't have two package managers running at the same time.

Sounds like you are starting to chase your tail a bit. Once lxde is installed (among the other tweaks) you are going to spend a lot of time trying to get rid of everything again; needle in a haystack. 

If you are intending to install lubuntu-desktop, you are removing what it is going to install again anyway (as it will install lxde).

Leave as is and install lubuntu-desktop, if that is what you're intending.

---

### Post by cmcanulty on 2012-06-26
ubuntu classic has transparent panels. alt+rt cl panel-select background and drag slider to get transparent

---

### Post by Shadius on 2012-06-26
> **cmcanulty said:**
> ubuntu classic has transparent panels. alt+rt cl panel-select background and drag slider to get transparent

But the entire panel isn't transparent.

---

### Post by Shadius on 2012-07-01
Here's an update on my progress:

I've successfully installed *lubuntu-desktop*! It's looks very nice compared to LXDE, or even GNOME Classic. 

I was wondering if there's a way to use Nautilus as my file manager instead of Lubuntu's file manager, PCManFM. 

Also, do you only have to use LXTerminal in Lubuntu? I did the  Terminal keyboard shortcut, *Ctrl+Alt+T*, and the Terminal came up, but when I tried to enter a code nothing showed up. Nothing was being written. 

Does it matter if I use Ubuntu Software Center or Lubuntu Software Center?

---

### Post by vasa1 on 2012-07-01
> **Shadius said:**
> ...
I was wondering if there's a way to use Nautilus as my file manager instead of Lubuntu's file manager, PCManFM. 
...
I hope you don't misunderstand or get offended but I've been lurking and can't help thinking that somethings are contradictory. You want a "lighter" experience but then start making things heavier. Nautilus instead of PCManFM is an example.

I'm not sure, but some of the effects you want seem also along those lines of making things heavier.

---

### Post by Shadius on 2012-07-01
> **vasa1 said:**
> I hope you don't misunderstand or get offended but I've been lurking and can't help thinking that somethings are contradictory. You want a "lighter" experience but then start making things heavier. Nautilus instead of PCManFM is an example.

I'm not sure, but some of the effects you want seem also along those lines of making things heavier.

Oh, I didn't realize Nautilus was "heavier" than PCManFM. Yes, that would definitely be contradictory on my part.

---

### Post by vasa1 on 2012-07-01
> **Shadius said:**
> Oh, I didn't realize Nautilus was "heavier" than PCManFM. Yes, that would definitely be contradictory on my part.
I don't have proof or numbers but from what I read I *think* it is.

---

### Post by Shadius on 2012-07-01
> **vasa1 said:**
> I don't have proof or numbers but from what I read I *think* it is.

I'll take your word for it. I thought that file managers didn't matter. I'll just have to get use to PCManFM for now. Thank you for helping me avoid making my desktop a potential hog again. :)

---

### Post by MG&amp;TL on 2012-07-01
> **Shadius said:**
> Here's an update on my progress:

I've successfully installed *lubuntu-desktop*! It's looks very nice compared to LXDE, or even GNOME Classic. 

I was wondering if there's a way to use Nautilus as my file manager instead of Lubuntu's file manager, PCManFM. 

Also, do you only have to use LXTerminal in Lubuntu? I did the  Terminal keyboard shortcut, *Ctrl+Alt+T*, and the Terminal came up, but when I tried to enter a code nothing showed up. Nothing was being written. 

Does it matter if I use Ubuntu Software Center or Lubuntu Software Center?

Awesome, hope you enjoy it. :)

Of course. Just use nautilus as you ordinarily would. There's not *much* difference, but obviously PCManFM is designed to be lighter. Lightness is always a compromise.

No, you can use any terminal you choose. Although it is odd that LXTerminal is misbehaving, I've never had a problem with it. Two things to check:

-Has it got keyboard focus? You may have to click on it.
-Check the preferences (Edit->Preferences) and check the background is not the same colour as the text.

No, of course not. But obviously LSC is lighter than USC.

> **Shadius said:**
> Oh, I didn't realize Nautilus was "heavier" than PCManFM. Yes, that would definitely be contradictory on my part.

Not...that much, but use whatever you're comfortable with.

---

### Post by Shadius on 2012-07-01
> **MG&TL said:**
> Awesome, hope you enjoy it. :)

Of course. Just use nautilus as you ordinarily would. There's not *much* difference, but obviously PCManFM is designed to be lighter. Lightness is always a compromise.

No, you can use any terminal you choose. Although it is odd that LXTerminal is misbehaving, I've never had a problem with it. Two things to check:

-Has it got keyboard focus? You may have to click on it.
-Check the preferences (Edit->Preferences) and check the background is not the same colour as the text.

No, of course not. But obviously LSC is lighter than USC.



Not...that much, but use whatever you're comfortable with.
Okay, if I can use Nautilus without turning my computer into a hog, I'll do that. How do I begin to use it? Do I have to install it? 

LXTerminal isn't the problem. The Terminal that comes up when I use the keyboard shortcuts is the problem. It looks like the same Terminal I used in GNOME Classic. I don't know if there's a specific name for it, like GNOME Terminal, or whatever, but it's the default Terminal in GNOME Classic. 

I'm enjoying it so far. I just have to get acquainted with my new Lubuntu friend. :)

---

### Post by Shadius on 2012-07-01
I fixed the Terminal issue! It was my dark theme messing with it. The font was black on a transparent background. I fixed it within the preferences settings. Thank you MG&TL.

---

### Post by MG&amp;TL on 2012-07-01
> **Shadius said:**
> Okay, if I can use Nautilus without turning my computer into a hog, I'll do that. How do I begin to use it? Do I have to install it? 

LXTerminal isn't the problem. The Terminal that comes up when I use the keyboard shortcuts is the problem. It looks like the same Terminal I used in GNOME Classic. I don't know if there's a specific name for it, like GNOME Terminal, or whatever, but it's the default Terminal in GNOME Classic. 

I'm enjoying it so far. I just have to get acquainted with my new Lubuntu friend. :)

Well, if you installed lubuntu-desktop on top of Ubuntu, there should be nautilus still installed. I suspect it's probably in Applications.

Have fun. :)

---

### Post by Bucky Ball on 2012-07-01
From a terminal if not in menu:

```
nautilus
```

---

### Post by Shadius on 2012-07-05
Thank you Bucky Ball. 

Since I installed Lubuntu on top of Ubuntu, it replaced my Ubuntu loading screen (the screen with the dots before you get to the login screen) and I'd like to get it back. How do I do that? I don't know what that screen is called so I'd appreciate it if someone could tell me the official name. :)

---

### Post by MG&amp;TL on 2012-07-05
> **Shadius said:**
> Thank you Bucky Ball. 

Since I installed Lubuntu on top of Ubuntu, it replaced my Ubuntu loading screen (the screen with the dots before you get to the login screen) and I'd like to get it back. How do I do that? I don't know what that screen is called so I'd appreciate it if someone could tell me the official name. :)

When you say 'replaced' - do you mean the dots are now a different colour, or that they no longer exist?

The boot animation backend is called *plymouth* - the Ubuntu theme is *plymouth-theme-ubuntu-logo* I believe. I believe the command to choose the default theme would be:

```
sudo update-alternatives --config default.plymouth
```

---

### Post by Shadius on 2012-07-06
> **MG&TL said:**
> When you say 'replaced' - do you mean the dots are now a different colour, or that they no longer exist?

The boot animation backend is called *plymouth* - the Ubuntu theme is *plymouth-theme-ubuntu-logo* I believe. I believe the command to choose the default theme would be:

```
sudo update-alternatives --config default.plymouth
```

Right, MG&TL. The Lubuntu loading screen (blue) shows up now instead of my original Ubuntu loading screen (purple). The loading screen itself says "Lubuntu" instead of "Ubuntu" and the dots are still shown but the colors are changed also.

---

### Post by MG&amp;TL on 2012-07-06
> **Shadius said:**
> Right, MG&TL. The Lubuntu loading screen (blue) shows up now instead of my original Ubuntu loading screen (purple). The loading screen itself says "Lubuntu" instead of "Ubuntu" and the dots are still shown but the colors are changed also.

In which case you want to run the command I gave above. :)

---

### Post by Shadius on 2012-07-06
> **MG&TL said:**
> In which case you want to run the command I gave above. :)

Okay, thanks again MG&TL! :)

---

