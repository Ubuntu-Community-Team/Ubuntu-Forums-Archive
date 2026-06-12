---
title: "I hate Plymouth..."
date: 2010-07-25
forum: Recurring Discussions
---

### Post by Legendary_Bibo on 2010-07-25
Well I've had a low resolution Plymouth screen ever since I've had Ubuntu, I didn't dare mess with it when I first started Linux because it scared me, so now that I've had a lot of experience I figured I would finally try fixing it. I followed two guides, and I found out what resolutions I could set Plymouth to, so when I was following another guide I forgot to set it to a resolution that was supported. Well I thought what the hey, just because the boot screen doesn't work should mean that the whole OS won't. Turns out because I put the wrong resolution in one of the files, Plymouth wouldn't work, so all of Ubuntu wouldn't. So I had to boot into a Live CD to copy the files which at first sucked because I could only find my Kubuntu disc which I thought would've been fine except for the fact that it wouldn't let me copy the freaking files! The Ubuntu disc worked which I didn't get why one worked and the other didn't, and yes I used sudo dolphin for Kubuntu. Well now I've got everything back except programs, and libs. Why couldn't they have it where it skips it if Plymouth isn't working?!?!?!?!?! I'm never messing with Plymouth again...

---

### Post by Lucradia on 2010-07-25
Switch to Debian?

ubuntu REQUIRES Plymouth to even boot, but debian, ubuntu's base, has not, and never will. Give it a spin.

---

### Post by CJ Master on 2010-07-26
On a side note, it's generally good practice to use "gksu" instead of "sudo" when launching graphical applications.

---

### Post by Lucradia on 2010-07-26
> **CJ Master said:**
> On a side note, it's generally good practice to use "gksu" instead of "sudo" when launching graphical applications.

as a side-side note:

Unless you tell Debian (in expert install I believe?) to use sudo, sudo will not be installed.

---

### Post by cascade9 on 2010-07-26
> **Lucradia said:**
> as a side-side note:

Unless you tell Debian (in expert install I believe?) to use sudo, sudo will not be installed.

Its installed on debain, just has no rights- 

> Strictly speaking, sudo is installed and enabled (if you installed the Desktop task during the installation). However no rights are granted by default in Debian (as opposed to some others distributions).

[http://wiki.debian.org/sudo](http://wiki.debian.org/sudo)

---

### Post by Lucradia on 2010-07-26
> **cascade9 said:**
> Its installed on debain, just has no rights

Last time I did debian netboot, it said sudo was not a valid command.

Obviously I didnt install a DE, seeing as I didn't need one, which means I don't need "desktop"

---

### Post by JustinR on 2010-07-26
Again, whats your graphics card? And what guides have you tried?

What about this guide? [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Khakilang on 2010-07-26
I hate to ask this. What is Plymouth anyway?

---

### Post by JustinR on 2010-07-26
> **Khakilang said:**
> I hate to ask this. What is Plymouth anyway?

Its the splash screen that says 'Ubuntu' with the 5 white/orange loading dots below it.

---

### Post by Khakilang on 2010-07-26
Oh! That is Plymouth! I didn't bother it much since it only take a few second. Thanks.

---

### Post by Mr. Picklesworth on 2010-07-26
> **Legendary_Bibo said:**
> Well I've had a low resolution Plymouth screen ever since I've had Ubuntu

This is just the reality of having a proprietary graphics driver. Plymouth or not, your system will [SIZE="3"]_*always*_[/SIZE] have the wrong resolution until X loads, unless your current graphics driver supports KMS.

(If you have an Intel card, it should out of the box. If it's Nvidia, you need to use the Nouveau driver).

If you want a proprietary graphics driver, you'll need to put up with not having kernel mode setting. This has always been the case. Heck, until about a year ago, we didn't have kernel mode setting. Plymouth may exacerbate the problem you experience by encouraging fancy boot splashes that are designed for KMS, but I hardly think that's grounds for hating it. It has a reasonable fallback mechanism where the boot splash still functions just fine, only looking as ugly as boot splashes have always been before. (How about that nicely integrated disk checking?)
Plymouth itself has nothing to do with setting your screen resolution.


As for Ubuntu not booting without Plymouth, that wouldn't be Plymouth itself, but some other component of Ubuntu's boot process. There's probably a bug to be reported here, but it's somewhere else. (And to find that somewhere else, we would have needed more information. Was it crashing and dropping you to a root shell, or what?)
The mountall package does have a hard dependency on Plymouth, although it isn't technically a "requirement" so much as "removing this will sometimes break things." At least, that's my understanding. It's all part of the shiny, new, ridiculously fast boot process, so I'm assuming it's a good idea because Scott J Remnant did it :P


If you really don't like how the default boot splash looks, you can change your Plymouth theme to something else, too. There's a (strangely complicated) command to change the default, but the easiest way is to install a package like plymouth-theme-ubuntu-text and remove plymouth-theme-ubuntu-logo. Next time you boot you'll have a text-based boot splash, which won't look like it's trying too hard.


I have an nvidia card (with proprietary nvidia driver) on my bigger computer, and the way I put up with the rather ugly splash is to remember that when it starts up I will be able to run all kinds of fancy 3D stuff that the other drivers can only dream of ;)

---

### Post by Dustin2128 on 2010-07-26
all this about a boot splash? I prefer the text based boot thing like you get on the more traditional distros.
[IMG]http://server.ericsbinaryworld.com/blog/wp-content/uploads/2009/02/slackware122-8.png[/IMG]

Also, I would highly recommend debian. It's still fairly easy to use (if you know what you want) but ***much*** more stable than the average distro.

---

### Post by gnomeuser on 2010-07-26
I love Plymouth, it is a thing of beauty and personally I have never seen a problem with it. On earlier versions of the proprietary driver there was a slight offset but they seem to have solved that and Nouveau always worked beautifully for me with Plymouth (though the power saving features being unimplemented currently causes increased risk of overheating and thus locking up on anything > kernel 2.6.32, a bug I have yet to track properly).

the only issue I have is pretty much with the progress dots being redundant movement on a screen that is seen at the most 10 seconds or so. They also aren't timed with actual progress so they repeat the same animation over and then ends ungracefully in the middle of one repetition. I say they go entirely, just display and elegant Ubuntu logo perhaps with an effect ala the Windows 7 boot.

Plymouth is likely one of the additions in Lucid I was the most excited to see as it also represents the replacement of a poor custom Ubuntu solution with a proper upstream project. I think Ubuntu benefited then and continues to do so in the future. 

Any issue with proprietary software is unfortunate but there is really little we can do to solve them. However to improve the general experience I believe in Maverick the aim is to have Grub2 hand off a framebuffer to Plymouth, this should if it can be made to work and the code proves robust (I believe this will be the first time the code paths for this were actually used, so it sounds like a bumpy ride could be expected). This should also help with such things as flickering.

---

### Post by Legendary_Bibo on 2010-07-26
> **Dustin2128 said:**
> all this about a boot splash? I prefer the text based boot thing like you get on the more traditional distros.
[IMG]http://server.ericsbinaryworld.com/blog/wp-content/uploads/2009/02/slackware122-8.png[/IMG]

Also, I would highly recommend debian. It's still fairly easy to use (if you know what you want) but ***much*** more stable than the average distro.

Do I have to compile anything? I've kind of grown accustomed to Synaptic and Ubuntu software center and sudo apt-get install.

I'll probably just stick with Ubuntu though, Plymouth is the only thing I've had issues with, and as long as I don't mess with it, everything works.

Well luckily I keep a log of everything I do so that I can easily set everything back up how I had it. There's just a few things I have left to do and then I should be back into full production! :D

The good thing about this ordeal was I was able to reduce the amount of programs and whatnot that I installed just to try them out, and only kept essential programs. I didn't uninstall any programs already on there as I might use them whenever. I have a lot more free space on my hard drive as well (about 60gbs). I treat everything as a learning experience no matter how frustrating they are.

---

### Post by Perfect Storm on 2010-07-26
For proprietary Nvidia driver I fixed it with this: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by NightwishFan on 2010-07-26
I am glad to see Ubuntu using Plymouth. Usplash was more limited than most people think, especially with KMS.

---

### Post by realzippy on 2010-07-26
> **Artificial Intelligence said:**
> For proprietary Nvidia driver I fixed it with this: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Thanks.I never cared about that ugly boot screen,but now I changed it.
Solution works :D

---

### Post by RiceMonster on 2010-07-26
> **Legendary_Bibo said:**
> Do I have to compile anything? ]

No. You can just use apt like you do on Ubuntu.

---

### Post by JohnnyC35 on 2010-07-26
I found going into Synaptic and removing everything plymouth related but 'plymouth' seems to fix any issues with the program itself. no more logo and I can see the lines firing off before boot.

---

### Post by BigSilly on 2010-07-26
> **JohnnyC35 said:**
> I found going into Synaptic and removing everything plymouth related but 'plymouth' seems to fix any issues with the program itself. no more logo and I can see the lines firing off before boot.

Actually that's not a bad idea, since the workarounds available aren't that great and still show a poor resolution. Even our Dell laptop with integrated Intel graphics wouldn't show Plymouth, so I had to use the Softpedia method, which I was very unhappy about.

I can't get that excited about Plymouth, since I do believe it's one of the things that will leave a negative impression on the end user at the moment as it stands. A great many people will be using these graphics cards, they will be offered the proprietary driver by Ubuntu, only to watch it nuke the boot screen with a pixellated mess on their next boot. Since the answer is not to *not *offer to driver (that would be silly), the only other solution is a Google search for these users, which adds negatively to the Ubuntu impression imho. It's not a popular train of thought here I admit.

It's OK to say 'well it's only a boot screen', but when the end result is that such a simple thing that works without fuss on Windows needs user intervention here on Ubuntu. I do sincerely hope it gets fixed for the next release. I understand the politics of it (non-free vs proprietary), and also the eventual functionality too, but at the moment I'm a little fearful that this can colour a users opinion of the OS at an early stage.

---

### Post by nerdy_kid on 2010-07-26
> **Mr. Picklesworth said:**
> This is just the reality of having a proprietary graphics driver. Plymouth or not, your system will [SIZE="3"]_*always*_[/SIZE] have the wrong resolution until X loads, unless your current graphics driver supports KMS.

(If you have an Intel card, it should out of the box. If it's Nvidia, you need to use the Nouveau driver).

If you want a proprietary graphics driver, you'll need to put up with not having kernel mode setting. This has always been the case. Heck, until about a year ago, we didn't have kernel mode setting. Plymouth may exacerbate the problem you experience by encouraging fancy boot splashes that are designed for KMS, but I hardly think that's grounds for hating it. It has a reasonable fallback mechanism where the boot splash still functions just fine, only looking as ugly as boot splashes have always been before. (How about that nicely integrated disk checking?)
Plymouth itself has nothing to do with setting your screen resolution.


As for Ubuntu not booting without Plymouth, that wouldn't be Plymouth itself, but some other component of Ubuntu's boot process. There's probably a bug to be reported here, but it's somewhere else. (And to find that somewhere else, we would have needed more information. Was it crashing and dropping you to a root shell, or what?)
The mountall package does have a hard dependency on Plymouth, although it isn't technically a "requirement" so much as "removing this will sometimes break things." At least, that's my understanding. It's all part of the shiny, new, ridiculously fast boot process, so I'm assuming it's a good idea because Scott J Remnant did it :P


If you really don't like how the default boot splash looks, you can change your Plymouth theme to something else, too. There's a (strangely complicated) command to change the default, but the easiest way is to install a package like plymouth-theme-ubuntu-text and remove plymouth-theme-ubuntu-logo. Next time you boot you'll have a text-based boot splash, which won't look like it's trying too hard.


I have an nvidia card (with proprietary nvidia driver) on my bigger computer, and the way I put up with the rather ugly splash is to remember that when it starts up I will be able to run all kinds of fancy 3D stuff that the other drivers can only dream of ;)

sorry but thats wrong....i use nvidia drivers and have plymouth at 1280x800 -- my native res.  all i had to do was add the lines 
GRUB_GFXMODE=1280x800
GRUB_GFXPAYLOAD_LINUX=1280x800
to my grub.cfg.  It is very possible and easy to have full res boot and non free drivers.

---

### Post by philinux on 2010-07-26
See the General Help forum sticky re plymouth.

---

### Post by Grenage on 2010-07-26
When it comes to jading a new user's experience, I can think of a hell of a lot of things that will affect them more than a low boot res, that they'll see for about 5 seconds.

---

### Post by BigSilly on 2010-07-26
> **Grenage said:**
> When it comes to jading a new user's experience, I can think of a hell of a lot of things that will affect them more than a low boot res, that they'll see for about 5 seconds.

Well of course. I know that and I said that. But they all add up don't they?

---

### Post by Frogs Hair on 2010-07-26
Some times I see the splash screen and others not . It goes by so fast I don't consider it a major issue . The splash screen always appears without the nvidia driver installed. Until we get a 3D open source driver I can live with that. The Nouveau driver is only 2D and experimental at the moment according to the description given in the software center.

---

### Post by Yes on 2010-07-26
> **Mr. Picklesworth said:**
> *snip*

I don't think that's always the case.  I'm using the ATI proprietary drivers on my laptop and have a beautiful 1920x1080 bootsplash and virtual terminals.  Using fbsplash though instead of Plymouth.  And on my other computer yeah, I'm using proprietary nVidia drivers and have a tiny bootup resolution.

---

### Post by Grenage on 2010-07-26
> **BigSilly said:**
> Well of course. I know that and I said that. But they all add up don't they?

I guess that's true!

---

### Post by limestone on 2010-07-26
plymouth sucks i know, it sucks that it's build in so much in Ubuntu and you can't remove it. Ubuntu starts to get more of a non customizable system. :(

---

### Post by Lucradia on 2010-07-26
> **pont.andersson said:**
> plymouth sucks i know, it sucks that it's build in so much in Ubuntu and you can't remove it. Ubuntu starts to get more of a non customizable system. :(

Just wait until GNOME Shell!

They're STILL trying to add an addons system to that. (Like Gnome Panel applets)

---

### Post by Mr. Picklesworth on 2010-07-26
> **Yes said:**
> I don't think that's always the case.  I'm using the ATI proprietary drivers on my laptop and have a beautiful 1920x1080 bootsplash and virtual terminals.  Using fbsplash though instead of Plymouth.  And on my other computer yeah, I'm using proprietary nVidia drivers and have a tiny bootup resolution.

Indeed, I shouldn't have said always. Out of the box, it probably never will.
With two monitors it's less likely ;)

I definitely did needlessly exaggerate, though.

Having never played with fbsplash, I'm curious: is there still a pause and a blank screen from switching modes? (When you use chvt or Ctrl Alt F2 and then go back to the one with X running).

---

### Post by Legendary_Bibo on 2010-07-26
> **Mr. Picklesworth said:**
> Indeed, I shouldn't have said always. Out of the box, it probably never will.
With two monitors it's less likely ;)

I definitely did needlessly exaggerate, though.

I'm curious: is there still a pause and a blank screen from switching modes? (When you use chvt or Ctrl Alt F2 and then go back to the one with X running).

with the Ctrl+Alt+F2 terminal thing when booted into X with the proprietary ATI drivers is in low res, but everything is big so at least I can read the text on the screen. Sorry if my grammar is off, lack of sleep currently.

---

