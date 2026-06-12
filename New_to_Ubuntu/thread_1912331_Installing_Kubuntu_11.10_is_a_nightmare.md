---
title: "Installing Kubuntu 11.10 is a nightmare"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by jermza on 2012-01-20
I've decided to try KDE and thus, Kubuntu.

Ubuntu 11.10 installed like a dream. It gave me options to install my Nvidia driver and whatnot.

Kubuntu has done nothing like that. I've received nothing but error messages. I can't open the Software Centre because it keeps crashing. I have to use the Package Manager instead. I've tried doing updates and when it reaches "committing changes", it's hung twice somewhere in the middle. I can't reboot because the hung installation keeps overriding, so I have to press the button on my casing. I don't get prompted to install the Nvidia driver and, in the packagae manager, there's a whole bunch of Nvidia options; which do I choose?

It didn't even bother remembering my desktop wallpaper.

I really want to stick with an Ubuntu derivitive, but this is unbelievably frustrating. 

Surely this isn't normal?

I'm considering installing Kubuntu all over again.

---

### Post by snowpine on 2012-01-20
Personally what I would do in your situation is:

1. Install Ubuntu and get it set up just the way I like it

2. Install the package **kubuntu-desktop**

3. Switch back and forth between Unity and KDE depending on my mood that day

4. (personal preference) Use reliable apt-get terminal commands instead of the buggy software center

```
sudo apt-get install whatever
```


Kubuntu is simply Ubuntu with the KDE desktop environment; it is not a separate operating system and does not require a reinstall. :)

And if you decide that KDE is a buggy bloated mess like a lot of people seem to think ;) then you can get rid of it with: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

ps As an aside, here are two great ways to try new distros/desktop environments without actually installing them: 1) create a Live CD or Live USB; 2) use a virtualization tool such as Virtualbox (see the stickies in the virtualization subforum if this sounds appealing to you).

---

### Post by SeijiSensei on 2012-01-20
> **jermza said:**
> Surely this isn't normal?

Having installed Kubuntu at least a dozen times now, I'd say it's not normal.

I'll suggest you start by trying to install [10.10]("http://cdimage.ubuntu.com/kubuntu/releases/10.10/release/"), which is the most stable and least problematic version of Kubuntu I've used.  The 11.x versions haven't fared so well in my experience.  The next long-term release, 12.04, will be out in a few months; I'm waiting on that before upgrading.

As for NVIDIA, once you've got a working installation, open the main menu and pick Applications > System > Additional Drivers.  The application will scan your hardware then recommend and install the appropriate NVIDIA driver.

---

### Post by jermza on 2012-01-21
Thanks for the help. I really do like Kubuntu, so I'm going to try get my installation to work.

Next question.

Once I've installed it, the first thing I did was install the Nvidia drivers. In Ubuntu, it prompts me to do updates. Kubuntu hasn't done that, but I'm assuming there are a bunch of updates I need to do.

Where / how do I do the updates?

---

### Post by SeijiSensei on 2012-01-21
Usually you'll get prompted.  If you see an icon that looks like a gear in the system tray, it means there are pending updates.  Click on it to show the list.

Another approach is to use KPackageKit.  In the menu, choose Applicatons > System > Software Management and click the gear icon in the left-hand column.

Alternatively, you can run "sudo apt-get upgrade" from a Konsole.

---

### Post by jermza on 2012-01-21
> **SeijiSensei said:**
> Usually you'll get prompted.  If you see an icon that looks like a gear in the system tray, it means there are pending updates.  Click on it to show the list.

Another approach is to use KPackageKit.  In the menu, choose Applicatons > System > Software Management and click the gear icon in the left-hand column.

Alternatively, you can run "sudo apt-get upgrade" from a Konsole.

Thanks.

When the package manager does the updates, it freezes at 45% when committing changes. Any idea why?

---

### Post by jermza on 2012-01-21
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
This is the error I get when doing updates. It did this on my last installation of Kubuntu AND this installation of Kubuntu.

Any advice?

---

### Post by mastablasta on 2012-01-21
> **jermza said:**
> This is the error I get when doing updates. It did this on my last installation of Kubuntu AND this installation of Kubuntu.

Any advice?


i would say: manually run 'sudo dpkg --configure -a'

:-)

I hope you checked the downloaded image. Also Kubuntu uses Muon not software center as package manager or Kpackagekit (if you are suign 10.10 you will only have Kpackage kit). Muon is still very new. It is supposed to be faster than kpackagekit and offer more features.

i have no idea why it freezes. you could 
1. check the logs
2. run sudo apt-get upgrade to see any possible errors. there could be an error on repository mirror you are using.

---

### Post by jermza on 2012-01-21
This is awful. Kubuntu is semi-working. Even Xubuntu installed more seamlessly than this.

Ive installed the MSFonts and it's made no difference. I even accepted the user agreement and can access the fonts, but the systemwide fonts haven't changed even though I've changed them.

I get far too many errors for this to be a daily OS.

If Kubuntu is based on Ubuntu, then why does UBuntu 11.10 install without a single error and Kubuntu has erros piled up (including messing up my sound).

I'm going to remove Kubuntu and try it again in a few months.

Very disappointing.

---

### Post by PaulW2U on 2012-01-21
> **jermza said:**
> 
I'm going to remove Kubuntu and try it again in a few months.

Very disappointing.

jermza, glad to see that you haven't totally given up on Kubuntu. :)

From my signature, you can see that I'm running three version of Kubuntu at present. Two of them started out as alpha or beta versions and even in at that stage of development I never saw any serious problems that prevented me from updating or using Kubuntu. For me 11.04 was the turning point in Kubuntu where everything suddenly got better although SeijiSensei has found the opposite. Different hardware can mean a very different Kubuntu experience.

The only real issue I have is that of screen fonts. In the alpha version of 12.04 I'm seeing some very poor fonts displayed in LibreOffice at a point where I hoped that they would improve. Screen fonts have always been an issue on this PC and you may well see the same problem. There are currently one or two issues with 11.10 relating to crashes and unwanted task-bar images that are being worked on. Hopefully will be fixed by the time 12.04 is released.

Please do try 12.04 in April. I'm sure it's going to be the best Kubuntu release so far. :P

---

### Post by mastablasta on 2012-01-21
i think something is wrong with your install or image itself.

KDE is only another way to display desktop and has nothing to do with your issues.

---

### Post by SeijiSensei on 2012-01-21
> **jermza said:**
> This is awful. Kubuntu is semi-working. Even Xubuntu installed more seamlessly than this.

Ive installed the MSFonts and it's made no difference. I even accepted the user agreement and can access the fonts, but the systemwide fonts haven't changed even though I've changed them.

Did you trying install 10.10 or 11.04 instead of 11.10?

My default system font is Verdana.  I set it via System Settings > Application Appearance > Fonts.  Is that what you did?

> **PaulW2U said:**
> For me 11.04 was the turning point in Kubuntu where everything suddenly got better although SeijiSensei has found the opposite. Different hardware can mean a very different Kubuntu experience.

Some of my problems with 11.04 were hardware-related, wifi in particular.  The rt2500 driver seems to work in some releases then break in later ones. :mad:

---

### Post by jermza on 2012-01-21
> **SeijiSensei said:**
> Did you trying install 10.10 or 11.04 instead of 11.10?

My default system font is Verdana.  I set it via System Settings > Application Appearance > Fonts.  Is that what you did?



Some of my problems with 11.04 were hardware-related, wifi in particular.  The rt2500 driver seems to work in some releases then break in later ones. :mad:

I set my system fonts like you did, yes. But they didn't change. 

I'm running two Nvidia GTX460 cards. I installed Kubuntu 11.10, and am now installing Ubuntu 11.10 and my Ubuntu installation has given not a single error.

At this stage of all three Kubuntu installations (two separate downloads), I had aready seen numerous errors.

However, I do prefer the KDE environment and don't want to give up. Perhaps, before I go any further with my UBuntu installation, I should install the KDE environment on top of my Ubuntu. What do you think?

---

### Post by jermza on 2012-02-01
I've now installed Kubuntu for the 3rd time and, again, the software centre crashes every time I open it.

Yet, when running off the live CD, it opened and I was even able to download stuff.

I'm now sitting in a bare bones Kubuntu 11.10 installation and nothing has popped up to tell me to install graphics drivers (like Ubuntu does) and nothing has popped up to tell me to install Kubuntu updates (like Ubuntu does).

I'm about to give up completely on Kubuntu and attempt a different KDE distro.

---

### Post by drmrgd on 2012-02-01
Although I'm not sure I have explanations for your issues, this definitely is not normal.  I've been running Kubuntu (both in a VM on my Windows 7 box at work and a full version on my home computer), and have not seen any of the problems that you describe.  It's really too bad that you're having such a bad experience!  On my computers, Kubuntu runs a million times more smoothly and efficiently than Unity.

---

### Post by jermza on 2012-02-01
Is Kubuntu supposed to prompt me to update my software?

And why does the software centre crash every time I open it?

With these in mind, I am worried that other parts of my installation are faulty.

---

### Post by jermza on 2012-02-01
If this helps...

[IMG]http://i.imgur.com/L5sBp.png[/IMG]

---

### Post by drmrgd on 2012-02-01
For me, I was getting software updates and notifications.  However, I usually turn them off since I do it manually on a semi-regular schedule and don't really need the notifications.  Also, I don't use Muon all that often.  When I do, it does seem to work OK, though.  Just Googling around, though, I seen a couple cases of people seeing Muon crash on them, but overall it seems to work OK for most.  I wish I could come up with a solution to why your system is not stable.

---

### Post by oldos2er on 2012-02-01
If you enter *muon segmentation fault site:launchpad.net* into a google search, you'll see muon has several outstanding bugs. I use Synaptic instead.

---

### Post by uRock on 2012-02-01
> **oldos2er said:**
> I use Synaptic instead.

+1 The few times I've installed kubuntu, I also installed Synaptic right away.

When you installed, did you tick the box to install updates during the install? When you open a terminal and run **sudo apt-get update && sudo apt-get dist-upgrade** does it show any updates being ready to install?

---

### Post by QIII on 2012-02-01
+1 more.  Muon has been problematic for me (that doesn't mean it doesn't work perfectly fine for others) so I use synaptic.

---

### Post by drmrgd on 2012-02-02
Does anyone else find it funny that a muon, according to Wikipedia, is:

> The muon is an unstable subatomic particle with a mean lifetime of 2.2 µs.

Seems to accurately describe a lot of users' experience :D

---

### Post by mastablasta on 2012-02-02
now that made me laugh....
 
but i also find it strange it performs badly. i was follwing a blog for a while and the developer said it is quite stable. i guess they didn't really test it in new Kubuntu before release.

---

### Post by lykwydchykyn on 2012-02-02
Muon is pretty new, it's only been written in the last year or so.  It's the *third* attempt at a native package manager for Kubuntu, and FWIW it shows more promise than either of the others ever did, so don't be too rough on it.

I mostly use aptitude or synaptic; you can install ubuntu software center too if you like.

The things to remember about Kubuntu:

 - It's a community-run, community-driven project
 - It ships with all KDE software, but that doesn't mean you have to limit yourself to all KDE software.  Package manager and web browser are probably the two biggest weak points of native KDE apps.
 - KDE's window manager has historically been more finicky about the graphics card/driver than other environments.

---

