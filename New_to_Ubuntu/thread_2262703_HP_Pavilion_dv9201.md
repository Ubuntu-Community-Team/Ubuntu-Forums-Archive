---
title: "HP Pavilion dv9201"
date: 2015-01-26
forum: New to Ubuntu
---

### Post by Helo888 on 2015-01-26
Hi everyone,  

I'm hoping to get some general advice and help on some very basic topics.  I browsed the forum for a while and didn’t find answers to my questions, so I thought I would post a new thread.  (And the sheer volume of info on this forum is very intimidating.)
  
I just got an old laptop and wanted to try using Ubuntu.  It's got Windows Vista on it right now.  The previous user did a clean wipe of the entire unit and I’m reinstalling updates... 104 updates.  I may die before they're all done, it’s taking that long.

I tried loading Ubuntu from a USB using the Pen Drive installer, but it got to the initial screen and then froze up.  I managed to get it to check for errors- it found one, then rebooted itself, then froze again.

I thought maybe the machine itself needed to run all the updates.  Do i really need to install all these updates before I try a Linux based OS?  Is Ubuntu too heavy for this machine?
Do I still need an antivirus?  I’ve read that if I install a dual boot system then the Windows OS is still vulnerable to viruses.  Would I just log into it every once in a while to just run a virus scan? 

It’s an HP Pavilion dv9201ca.  ACPI x86 based PC.  The processor is an AMD Turion 64 x2 TL-150, 1.6GHz.  32 bit, 958MG of ram left.  86 GB storage, 49 GB free.

Thank you for any help you can give me!

---

### Post by Stefan_Vukanovic on 2015-01-26
Hello,
I started using linux 3 months ago so I might not be of big help. First of all, I installed Kubuntu Linux (its made from Ubuntu, and it works with older hardware) around 15 times (from that 10 times on my PC). I don't belive anyone ever installed nor linux nor windows from first trial (windows maybe), so everytime you install it you find solutions for different errors. Now, lets see.
If those are windows updates, you don't need to install them. If those are BIOS updates, again, you don't need to install them, but sometimes it helps if you do. Next, if you have working windows system, try using Wubi. If it won't work, I always use Unetbootin. Next, your PC can be harmed by windows viruses only if you boot to windows. I hope these are answers you are looking for. If not, ask more questions.

---

### Post by Helo888 on 2015-01-26
Hi, thanks Stefan.  I will check out Kubuntu.  Does anyone have any advice on a different distro to use?  I want to use this laptop for primarily writing and for email and social media.  I might get around to downloading movies or tv shows but not a gamer.

---

### Post by TheFu on 2015-01-26
When you run Windows, it is possible to get Windows viruses. If you never run Windows, then you won't get any Windows viruses .. well, unless you run Wine under Ubuntu and get a Windows virus that way.

A few important things to know: [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)

Oh - welcome to the forums.

---

### Post by Jonathan Precise on 2015-01-26
> if you have working windows system, try using Wubi.
Wubi, as of right now, is not supported nor given away for any version other than 12.04, which is quite outdated right now. Sorry.

> If it won't work, I always use Unetbootin.
Unetbootin has bought me probs in the past (especially with older hardware), so let me suggest Linux Live USB creator, which as long as you don't choose the virtualization option, might work better than the others.

> If those are windows updates, you don't need to install them.
+1. As for updates, don't waste your time with them, mostly they create more problems than they fix.

> your PC can be harmed by windows viruses only if you boot to windows
+1 this. Windows viruses only hurt Windows. They don't mess with Linux, as they're somewhat independent.

As for older hardware support, you might like Ubuntu MATE, with a lighter UI, a bit less "bloatware" than KDE, and more support for older hardware still. As long as your PC can run 11.04, it can run Ubuntu MATE 14.04 LTS.

Any questions that arise we will be happy to help with.

-Jonathan

---

### Post by Stefan_Vukanovic on 2015-01-26
Well, Kubuntu, like most distros, comes with LibreOffice. It also has Firefox. It has e-mail app, but you better install Thunderbird, I belive its the best. It uses KDE Desktop Enviroment, which is known to be easiest for windows users to get used to.

---

### Post by Jonathan Precise on 2015-01-26
> **TheFu said:**
> When you run Windows, it is possible to get Windows viruses. If you never run Windows, then you won't get any Windows viruses .. well, unless you run Wine under Ubuntu and get a Windows virus that way.

+1, forgot to mention that. I don't have WINE anyway, so I forgot about it.

---

### Post by Jonathan Precise on 2015-01-26
> **Stefan_Vukanovic said:**
> Well, Kubuntu, like most distros, comes with LibreOffice. It also has Firefox. It has e-mail app, but you better install Thunderbird, I belive its the best. It uses KDE Desktop Enviroment, which is known to be easiest for windows users to get used to.

+1. Well yes, Kubuntu gets a plus for easier switching from Windows.

---

### Post by kc1di on 2015-01-26
Hi Helo888 and welcome to Ubuntu Forums,

You don't have to do the windows updates, they have nothing to do with Linux/ Ubuntu.  if you trying to run Ubuntu with Unity desktop, your video card may not be new enough to run it.
Unity requires 3D acceleration.  Usually when there are freezes like you describe it's a video card issue. When I look up the specs on that laptop it list a NVIDIA GeForce Go 6150 video card - you will have to start that card with the nomodeset parameter in the boot line on the live usb/DVD.  you can findout how [here]("http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu").  once it's installed you will need to install the proprietary Nvidia for your card - I believe for the 6150 series of card it will be the Nvidia-304 driver you'll need.

---

### Post by Impavidus on 2015-01-26
That laptop is not exactly a powerhouse, so I suggest you try one of the lighter flavours. Xubuntu may just be satisfactory, there is also Lubuntu and the Mate desktop environment. KDE can be configured to be quite light. Right after installing you'll get a lot of updates. That are just all updates released since creation of the image file you put on the live disk.

---

### Post by Stefan_Vukanovic on 2015-01-26
You could also install Kubuntu and then install LXDE over it. That way you should be able to switch from KDE to LXDE. But I do not belive it is recommended, because it can cause some strange anomalies.

---

### Post by mikodo on 2015-01-26
Welcome, Helo888  :)

I am sure we are overwhelming with suggestions. I apologize, that I am going to give you some more ...

With your laptop, I would do as others have suggested and go with the "lighter" [Ubuntu flavors]("https://wiki.ubuntu.com/UbuntuFlavors"). You can see the full list of all flavors there. All these, except Ubuntu Mate, are officially supported, and I think Ubuntu Mate, is to have an official release, this spring. An "Ubuntu flavor", has all the "goodness of Ubuntu" underneath, (security, support, and user friendliness) with a different [Linux Desktop Environment]("http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/?PageSpeed=noscript"). Some use "lighter" desktops, that run better on devices that have lower resources. Here, is what I suggest you try, or at least read about, for your laptop:

**Xubuntu **I use it, and see lots of support here for it. It is very light.  Its "mature" desktop is [Xfce.]("http://www.xfce.org/") Used since 1996, and the favorite of Linux power users, that use Desktops.

**Lubuntu** I like it too. It is the lightest of all the official flavors. Its desktop is [L]("http://lxde.org/")[XDE.]("http://lxde.org/") Presently, [LXQT]("http://lxqt.org/") is being developed for its replacement. There are users here, that answer questions about it.

I would start with considering those two. If you do download them to try, try them in a ["live" environment]("https://help.ubuntu.com/community/LiveCD") first. That link says, "Ubuntu", but live environments work with the "official flavors", also. (I suggest you do this). They, run a little slower this way while the are in "live mode", but they give you somewhat of an idea, what they are like on your system. Ask away, if you have questions.

What versions of Xubuntu or Lubuntu? I would pick the 14.04.1 series, because they both have at least 2 years of support remaining with them. If you keep a Ubuntu variant installed, you can then update it to, or install newer versions, as they become available. They are more built for stability of the distro and apps, than the 14.10 series, which also has less length of support. 

You need to discern if you will use the 32 bit (Intel x86) versions, or the 64 bit (AMD64) versions. The Intel and AMD names, are just what are commonly used to refer to these kind of versions.  A safe thing is to choose the 32-bit, if you don't know for sure which to pick. If you know or find out (just ask how to do this), that your system is capable of running the 64-bit system, it may be faster for you but, likely not, given your lower RAM.

So, here are the links for the two distros I suggest:

[Xubuntu]("http://xubuntu.org/getxubuntu/") see the links on the right of the page for more information including, [Xubuntu (14.04) Documentation]("http://docs.xubuntu.org/1404/"). [Xfce Documentation]("http://docs.xfce.org/"). [Customization of the Xfce Desktop examples]("https://plus.google.com/communities/111754836499684090642/stream/99fb8df0-e9e5-41b4-ae8e-5ff796e3c0ae").

[Lubuntu ]("https://wiki.ubuntu.com/Lubuntu")see the links provided for more reading.[ Lubuntu Documentation]("https://help.ubuntu.com/community/Lubuntu/Setup"). [LXDE Documentation]("http://lxde.org/lxde"). [LXDE Screenshots]("http://lxde.org/image_galleries/screenshots").  

Enjoy!

---

### Post by oldrocker99 on 2015-01-26
I personally recmmend Ubuntu MATE (pronounced Mah-TAY, after the Argentinian caffeinated herb), which is close to as lightweight as Xubuntu or Lubuntu, and has a far better file manager. Ask people who used Ubuntu 2008-2009 about the interface, which takes all of ten minutes to learn how to use. Here's a link for the 14.04.1 version (supported until 2019):

[https://ubuntu-mate.org/trusty/](https://ubuntu-mate.org/trusty/)

---

### Post by JeQhdMD on 2015-01-26
About 4 months ago, a friend asked me to install Linux on an older HP laptop.   It has nearly identical specs to yours.   It took me several attempts and a few hours to successfully install Ubuntu with the standard Unity desktop.   Use of "nomodeset" was required in the startup boot parameters, and then installing the proprietary nvidia driver.   After all that . . . Unity still ran too slow for an acceptable and functional PC.

So, I installed Linux Mate v17 on it (17.1 is available now).   Anyway, it now runs like a dream - - fast, no need to install the proprietary nvidia drivers.   The whole install took about 45 minutes, and then another hour or so to do all the tweaking that I like to do (such as installing extra codecs for running DVD media, etc.).   All my Intel based or newer PC's run Ubuntu Unity great, but your machine is perfect for Linux Mint 17.1 . . . get it via "distrowatch.com".

---

### Post by hansmariush on 2015-01-27
I personally like LinuxMint a little better than Ubuntu (just because it looks better I think). I would recommend using Rufus to create a bootable usb stick: [https://rufus.akeo.ie/downloads/rufus-1.4.12.exe](https://rufus.akeo.ie/downloads/rufus-1.4.12.exe)

Unetbooting also works great, but I have noticed that Rufus is able to create bootable sticks of almost "everything". I used it for CentOS cause I didn't get anything else to work.

---

### Post by TheFu on 2015-01-27
> **Helo888 said:**
> Hi, thanks Stefan.  I will check out Kubuntu.  Does anyone have any advice on a different distro to use?  I want to use this laptop for primarily writing and for email and social media.  I might get around to downloading movies or tv shows but not a gamer.

I don't bother with different Ubuntu distros.  The GUI is **not** the OS.  You can put any GUI you like on any Linux variant to get the look and feel you prefer.  It is possible to install 20 different GUIs onto the same distro you install and try each out just by selecting them on the login screen (before logging in).  Sure, the different variants will pre-install different applications, but you can remove and add any application you like from any of the repositories.  You can run KDE applications under Unity and you can run Gnome applications under KDE and you can mix and match the best application under any of these different GUIs. 

Or, if you are like me and don't use any DE (desktop environment) like KDE, Gnome, Gnome3, Unity, LXDE, XFCE, Cinnamon, .....    I run in an old-school way with just a Window Manager, WM, and all the same programs work just fine without the bloat of any DE. Of course, I don't get an automatic generated menu either. 

So ... which distro should someone new to Linux use?  All of them. You need to see them for yourself to make a decision (or just watch some youtube videos of each).  How much "cheese" do you like?  Unity (the default desktop) is full of "cheese."  XFCE has less. LXDE has even less.  I've run both of these for a few years. Only ran Unity for about 3 weeks back in 2011 - hated it. If I want a Mac .... actually I had a Mac for 2 weeks and gave it back - OSX felt like "linux-lite" plus I couldn't control anything, CIFS was broken at the time, and all the keyboard bindings were "wrong."  Apple had renamed common things to be more friendly rather than using the names we've know for 30 yrs. 

Try them all. Oh ... just be certain you create a new userid for each or you can use the "guest login" - so settings don't get messed up between the different GUIs in the same account. Many of these GUIs are based on slightly different versions of the same libraries, so they put settings into the same files. Sometimes those settings aren't compatible. Anyway, it is best to use a different userid to test each one as you trying them out.

---

### Post by stalkingwolf on 2015-01-27
my preference is linux mint 13 mate.iput it on all my minis and many others. have had no problems with it.  might also try zorin.

---

### Post by Helo888 on 2015-01-27
Thanks everyone for the welcome and all the info!  :)  Will go through your recommendations and try a few options.  I'm hoping to find the best option that works with minimal tweaking, since I really don't know how to do any tweaking!  :confused:  I will post my results (and resulting questions!) as I go.

---

### Post by mikodo on 2015-01-27
> **Helo888 said:**
> Thanks everyone for the welcome and all the info!  :)  Will go through your recommendations and try a few options.  I'm hoping to find the best option that works with minimal tweaking, since I really don't know how to do any tweaking!  :confused:  I will post my results (and resulting questions!) as I go.

Hi again.

A couple more thoughts.

1) You do need to choose distro's with lighter desktops, to get the best performance of your hardware, that is a little compromised in abilities.

2) I would stay away from Kubuntu and distros that use the KDE desktop. It uses a lot of resources, and as you are newer, tweaking it to use less, would be harder for you.

3) Certainly try out the different suggestions, and see what you like, and what works well for your computer.

4) Start new threads, with subject headers, that describe what help you want. One long thread is not going get the same support as separate ones.

[Here]("http://ubuntuforums.org/showthread.php?t=1422475"), is the forums suggestions for starting threads, that can help you with getting the answers you need.

The best to you, and  again ...

Enjoy!

---

