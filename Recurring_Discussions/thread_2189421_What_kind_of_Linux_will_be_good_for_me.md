---
title: "What kind of Linux will be good for me?"
date: 2013-11-22
forum: Recurring Discussions
---

### Post by wsc1028 on 2013-11-22
Need advice: what Linux distro will be best fit for my requirements, if it exists at all? 
I'm looking for OS ready to use, with minimum fighting with it, for desktop use.

- Distro that comes with minimum preinstalled programs, I remove most of them, that will not uninstall desktop core files. But with possible installation of Firefox and GIMP. I'm not using office, multimedia, sounds, sharing. 

- No multiple workplaces, Recent and Bookmarks in File Manager.

- Preferably one that remembers in what directory you were when you save as or export file from programs. Or this functionality is gone forever, in both Linux and Windows?

- Desktop without buttons in the middle, on the left, or in the center of the bottom (not Unity, Gnome or Elementary OS). More like Windows 7 or Mint 15 64-bit: with panel at the bottom, with launch pad to drag frequently used programs' shortcuts there, and Menu/Start button. Or only Mint 15 64-bit has it?

- It has to be configurable from Settings and such, not dependent of use of Terminal.
- Be secure, so no Linux from Scratch, not my level.
- Not neccessarily lightweight, hardware is 64-bit capable, not old.

I spent a lot of time downloading and trying Linux distros. Mint 64-bit was closest, but the quirks that are being constantly added (hiding the open applications I was working with and file manager "advanced" behaviour) interfere heavily with productivity, so I'm asking for an expert advice. Thank you.

---

### Post by wtheron on 2013-11-22
Debian Wheezy with XFCE comes to mind.  You can pick this setting when you install wheezy, under advanced -- alternative desktops.  It is super lightweight and you have a lot of control of your desktop layout.  This is my default installation but I now use a tiled window manager, i3, which is simpy amazing.  The nice thing about debian is that, IF you run into problems, you can use the solutions posted under ubuntu to help troubleshoot.

---

### Post by lykwydchykyn on 2013-11-22
> **wsc1028 said:**
> Need advice: what Linux distro will be best fit for my requirements, if it exists at all? 
I'm looking for OS ready to use, with minimum fighting with it, for desktop use.

Ok, let's try
> 
- Distro that comes with minimum preinstalled programs, I remove most of them, that will not uninstall desktop core files. But with possible installation of Firefox and GIMP. I'm not using office, multimedia, sounds, sharing. 

Installing and removing software is trivial in most distributions.  It'd be a waste of time and effort trying to find one that had just the right packages installed by default.
I suggest not worrying about this.
> 
- No multiple workplaces, Recent and Bookmarks in File Manager.

Probably every linux desktop environment ever has some concept like multiple workspaces.  Fortunately, you can also turn off this feature in most environments.  
> 
- Preferably one that remembers in what directory you were when you save as or export file from programs. Or this functionality is gone forever, in both Linux and Windows?

This is probably a program-by-program issue, so distro will make no difference here.  Either the program is written to store your last save location or not.
> 
- Desktop without buttons in the middle, on the left, or in the center of the bottom (not Unity, Gnome or Elementary OS). More like Windows 7 or Mint 15 64-bit: with panel at the bottom, with launch pad to drag frequently used programs' shortcuts there, and Menu/Start button. Or only Mint 15 64-bit has it?

Why don't you check out something using KDE?  It can be configured to just about any layout you want, but the default is often compared to Windows 7.
> 
- It has to be configurable from Settings and such, not dependent of use of Terminal.
- Be secure, so no Linux from Scratch, not my level.
- Not neccessarily lightweight, hardware is 64-bit capable, not old.

This also sounds like a KDE-focused distro would be in order.  Maybe openSuse, which is known for it's YaST configuration GUI and its really polished KDE desktop.

Otherwise, maybe try Kubuntu, Mepis, or SolydXK.

---

### Post by wsc1028 on 2013-11-23
Thank you! I'll try Debian Wheesy XFCE.

        lykwydchykyn:
Mint 64-bit is closer to Windows than KDE, I started with KDE.
Removing programs is not that easy as it seems, if you uninstall most multimedia (and a lot of other programs) all you will see is a black screen. One has to watch closely for a list of files that will be removed during uninstall.
You see, the multiple workspaces were turnable off, but no more, and when your work disappears and you have to go to the Window Switcher to make visible applications you work for with copy-paste, it's not good.
File manager (or programs) not remembering where the last file was saved, may be or may be not program specific, they all display the same behavior, likely they relay on the same built-in mechanism.
But thank you for the providing help, negative result is still a result. t's generally good to know that what I'm looking for doesn't exist, so I will no longer waste my time trying to find it. 
I'll take a closer look at distros you suggested too.

---

### Post by vasa1 on 2013-11-23
> **wsc1028 said:**
> ....
You see, the multiple workspaces were turnable off, but no more ....
If workspaces and desktops are the same thing, can't you just have one desktop? It's possible with the Openbox window manager and I suspect with others as well.

---

### Post by lykwydchykyn on 2013-11-23
> **wsc1028 said:**
> Thank you! I'll try Debian Wheesy XFCE.

        lykwydchykyn:
Mint 64-bit is closer to Windows than KDE, I started with KDE.

I guess, I don't know.  KDE can be made to look like what you described, and you hadn't mentioned trying it.  But apart from Unity, or maybe some of these new desktop environments like pantheon,  most desktop environments allow you to rearrange the desktop.
> 
Removing programs is not that easy as it seems, if you uninstall most multimedia (and a lot of other programs) all you will see is a black screen. One has to watch closely for a list of files that will be removed during uninstall.

Yes, you can run into dependency issues if you're not careful.  But do you really think there's a distro out there that's going to have just the right set of applications that you want pre-installed?  Seems like a better strategy is to come to terms with package management.  Probably helps if you stick with a mainstream distro and don't add a bunch of third-party repositories. 
> 
You see, the multiple workspaces were turnable off, but no more, and when your work disappears and you have to go to the Window Switcher to make visible applications you work for with copy-paste, it's not good.

On which distro and desktop environment can you not turn off multiple workspaces?
> 
File manager (or programs) not remembering where the last file was saved, may be or may be not program specific, they all display the same behavior, likely they relay on the same built-in mechanism.

If you find that the same program behaves differently in this regard on different distros or desktops, let me know.  You may be right, but I've never seen this behavior in programs I've written unless I've added it specifically.  
> 
But thank you for the providing help, negative result is still a result. t's generally good to know that what I'm looking for doesn't exist, so I will no longer waste my time trying to find it. 
I'll take a closer look at distros you suggested too.

After ten years of using Linux, I've found that endless distro-hopping is a waste of time.  You pick a mainstream distro that is close to what you want, and learn how to make it into the thing you want.  The learning curve is a little steeper, but in the end you aren't beholden to some stranger for the experience you want.  Good luck!

---

### Post by Bucky Ball on 2013-11-23
*Thread moved to **Recurring Discussions**.*

I would advise doing a LOT of research by downloading ISOs, making CDs and trying the different flavours and distros from the CD. Find the bits that suit you; file managers, desktop environments, default apps, but ...

You provided the answers for what kind of Linux would be good for you in the first post. For what you're looking for I would suggest you design your own, that's why you should try out everything. Install a minimal install, which is just the Ubuntu kernel, nothing else, and then you add what you want. No bloat from the desktop environment (if you want one) up.   

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

To know what you want you're going to need to research. There is no doubt you can realise something close to what you mention. Customisation is a personal thing.

There are other distros apart from Ubuntu that have a more 'ground up' approach. Arch is one of them.

---

### Post by Lars Noodén on 2013-11-23
> **wsc1028 said:**
> 
- Desktop without buttons in the middle, on the left, or in the center of the bottom (not Unity, Gnome or Elementary OS). More like Windows 7 or Mint 15 64-bit: with panel at the bottom, with launch pad to drag frequently used programs' shortcuts there, and Menu/Start button. Or only Mint 15 64-bit has it?


That is  a function of the window manager and how it is configured.  Pick a distro that is close to what you want and then experiment with configuring the window manager.  Then try others: xfwm4, compiz, openbox, metacity, and so on.

---

### Post by wsc1028 on 2013-11-26
Thank you all.
I tried offered suggestions, different desktops and distros listed in DistroWatch as Independent, at my level, without using Terminal. 
Result: the kind of Linux I was looking for doesn't exist.

While number of workspaces is possible to reduce to one in many distros (except Mint 15 64-bit, at least in Cinnamon desktop), Recent and Bookmarks options for Open/Save as/Export appear in most of the applications I use (gedit, TreePad, GIMP, Gnumeric, GnuCash, pdf document viewer) and in most usual Libre Office, plume, squeeze, leaf. No matter what kind of Linux was used.

Windows manages instead of desktop environments are beyond my level now, as well as Minimal CD. If linux is fully customizable, maybe for people who are able to compile it from scratch and modify everything from command line, I honestly stated my level in my original post.

But I appreciate yout help.

---

### Post by lykwydchykyn on 2013-11-26
> **wsc1028 said:**
> Thank you all.
 Recent and Bookmarks options for Open/Save as/Export appear in most of the applications I use (gedit, TreePad, GIMP, Gnumeric, GnuCash, pdf document viewer) and in most usual Libre Office, plume, squeeze, leaf. No matter what kind of Linux was used.


Pretty sure this is just implemented at the program level.  If it's *that* big of a deal for you, you might want to look for some different programs, though considering it's kind of considered a usability standard/convention, you might have trouble doing that.

---

### Post by wsc1028 on 2014-01-19
Found a minimalist, user choice oriented Linix version for me: WattOS (long-term support Ubuntu-based, LXDE desktop). 

- Minimum preinstalled programs, 
- everything else can be installed form Software centre, 
- has Start Menu button and bottom panel,
- 2 desktop workspaces at the bottom panel can be easily reduced to 1,
- when saving files (from programs) it doesn't remember where the last file was saved, I was told the this depends on some library that these programs use. Work around: use Recent place when saving
- instead if Control Panel (Settings) it uses one step less: each part of Control Panel can be opened directly from Menu > Preferences.

Unexpected bonus features:
- installing manufacturer's driver for Brother printer went flawless, fine nuances of printing are now possible (same driver was not accepted by Mint 16 Cinnamon, 64 bit).
- Looks much better than Lubuntu.

Drawbacks, LXDE specific:
- More hand-work from terminal, described on the web ([http://linuxforcynics.com/tag/ubuntu-12-04](http://linuxforcynics.com/tag/ubuntu-12-04) and on main Ubuntu website), few lines actually, to install Oracle Java (not Open Java, if you need it for cross-platform software). 
- Making Desktop links for files or folders has to be done in text editor (take copy of existing file and change name and path), how-to described here: [https://lkubaski.wordpress.com/2012/06/29/adding-lxde-start-menu-and-desktop-shortcuts/](https://lkubaski.wordpress.com/2012/06/29/adding-lxde-start-menu-and-desktop-shortcuts/) 
- Disks utility has to be installed separately, or get used to mount/unmount media in File Manager (orange arrow near mounted volume name in Places view).
- Moving files and folders in File Manager is easier to cut-paste, drag-and-drop sometimes copies files instead of moving them. If File Manager opens as not 2 separate instances, but as tabbed interface, cut-paste works.
- Emptying trash is done also from File manager, Places view.
- Desktop icons has no options to be dragged anywhere you want them to be grouped in clusters of choice, but you can move them within area where they are.
- Applications icons from start menu can't be added to Quick launch bar, only limited scope of widgets (on right click).

Things to know before install: read top of home page of their website, do not upgrade to Ubuntu 13.10.
I did not, it works anyway, even propietary driver for a printer installs, only shutdown was disabled. Each time one has to go to Terminal and enter: sudo poweroff.  The unexpected bonus was that you can add application icons to Quick launch bar now.

I understand now what windows managers like Fluxbox are, AntiX Linux has variety of the to try, in different combinations with 3 built-in file managers. AntiX was expected to be minimalist, user choice version of Linux too, but in my experience there are too much preinstalled not needed programs and user choice to manage OS easily was more reduced than in LXDE. If not references from other users to WattOS and AntiX, I wouldn't even think to try them, there are too many versions of Linux.

As all you you said, try until you find what you want.
By the way, in process of finding better Linux for me, bought tablet with Windows 8.1. it appears that WattOS or Mint are much easier to learn and work with from scratch (for Windows 7 user) than re-learn how to use Windows 8.

Thanks again!

---

