---
title: "Removing Ubuntu and going back to Windows Vista?"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by JK700 on 2013-07-16
Hi. I recently was given an old used laptop from my cousin. It works fairly well and is a **HP Pavilion dv3-2050ea**

According to a quick internet search and the sticker that is on the laptop, it should have Windows Vista as it's operating system. However, it is Ubunutu 13.04 that is installed and there is no option to boot up Vista, despite everything I have tried. I even attempted to restore the laptop to it's factory settings by tapping F11 when it boots but this does nothing and just gives me options about Ubuntu only.

I don't have the original CD to reformat it either.

I have been searching the net for a few days though trying to uninstall Ubuntu and have Vista instea but everything seems to complex for my limited ability. 

Is there an easy fool-proof way to uninstall Ubuntu and go back to Vista? I tried something called Easy BCD with a programme called "WINE" but it installed and then wouldn't load/open so that didn't work either.

Thanks :)

---

### Post by mastablasta on 2013-07-16
there is no easy option. previous user removed the restore partition it seems. which is why restore doesn't work. so the only option is buying Vista DVD, formatting the disk and installing it. but why would you want to run the horrible Vista? better to go with win7 or win8 than vista if you want windows. 

or better yet just use Ubuntu ;-)

If you don't like the interface try to install for example Kubuntu desktop instead.

---

### Post by coffeecat on 2013-07-16
> **JK700 said:**
> However, it is Ubunutu 13.04 that is installed and there is no option to boot up Vista, despite everything I have tried. I even attempted to restore the laptop to it's factory settings by tapping F11 when it boots but this does nothing and just gives me options about Ubuntu only.

There will have been a recovery partition once, from which you could reinstall Vista and set the laptop back to its factory condition, but as mastablasta said, it sounds as though the previous owner removed the recovery partition along with Vista when they installed Ubuntu. But let's be absolutely sure before you go to the expense of getting hold of a Windows install DVD. Can you boot into Ubuntu OK? Do you know the login password? If so, boot into Ubuntu and open a terminal with the keyboard shortcut ctrl-alt-T. Sorry about asking you to use the terminal, but it's the quickest and easiest way to get the information we need. Once the terminal is open, run these two commands and post the output:

```
sudo fdisk -lu
sudo blkid
```

You will be prompted for your password with the first command. It won't be echoed to the screen when you type it in, but be assured if you type it in, it will work. In order to copy and paste the terminal output into your post, highlight the output with the mouse, right-click -> copy.

---

### Post by Impavidus on 2013-07-16
I don't know whether it's true, but I read a few times that it's possible to get a legal Windows installation disk without buying a new license, provided you have a valid product key or what is it called. It should be printed on a sticker somewhere on the laptop, usually in the battery bay.

---

### Post by Mark Phelps on 2013-07-16
> I tried something called Easy BCD with a programme called "WINE" but it installed and then wouldn't load/open so that didn't work either.


EasyBCD is a Windows app that provides a GUI for editing the Windows boot loader -- the BCD.  It has nothing to do with installing or reinstalling Windows.

Wine is used in Linux to install Windows apps; it can not be used to install Windows.

You're probably NOT going to be able to find a Vista DVD anywhere -- as folks stopped selling those years ago.

You would better to get Win7 -- and avoid Win8.

---

### Post by Bucky Ball on 2013-07-16
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by kurt18947 on 2013-07-16
You *can* get a Windows Vista DVD.  I just found some on Ebay but you'd have to be careful, many (most) are upgrades, not full.  You machine does have a Vista license so I don't know if the reinstall DVDs would work or not.  I'm not really familiar with how MS upgrades work.  Having said that, as Marks says why bother?  Windows 7 makes a lot more sense to me.  For one thing, Windows 7 is supported longer.  You can download Windows 7 ISOs and just buy a key.  I don't know if that makes $ense or not.

---

### Post by mastablasta on 2013-07-16
windows 8 has strange interface but the system is more/better optimised than windows 7 and is generaly considered faster. but then again there is that strange interface. there are 3rd party tools that will get you arround that issue. windows 7 is not so young anymore (from 2009) but it is supported until 2020 (with security patches) i believe. why buy an almost 4 year old OS? but then again it does it's job and is stable, so might not be a bad idea afterall. 
i have the Win7 Starter on one mashcine and i hate the interface.

Again Ubuntu is preety good OS as well. it is much more secure than windows.

---

### Post by JK700 on 2013-07-16
First and foremost thanks for all of the replies.

They are extremely appreciated!

> **coffeecat said:**
> Sorry about  asking you to use the terminal, but it's the quickest and easiest way to  get the information we need. Once the terminal is open, run these two  commands and post the output:

You will be prompted for your password with the first command. It won't  be echoed to the screen when you type it in, but be assured if you type  it in, it will work. In order to copy and paste the terminal output into  your post, highlight the output with the mouse, right-click ->  copy.

Here is what I got...

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2344

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   616820735   308409344   83  Linux
/dev/sda2   *   616822782   625141759     4159489   ef  EFI (FAT-12/16/32)
```

```
/dev/sda1: UUID="eacb195a-5c2a-410a-889e-9f6a55b31d5f" TYPE="ext4" 
```

It's not that I actively dislike Ubuntu, it's just that I'm not familiar with it and have been used to Windows Vista.

---

### Post by su:bhatta on 2013-07-16
I used to dual boot Windows7 & Ubuntu, now i Dual boot Win8 & Ubuntu... Though i hardly use Win8...
First week after installatio, i really liked Win8 actually... Itz weird, true, but somehow i liked it, better than Win7 actually, which BTW is super stable (used it at home and office)...

But Vista? really?
Please dont do that ! If you have seen the Win8 Metro Interface & have no problems with it, please use Win8... I just loved IE10 that came with Win8, also Bing, with its lovely pictures....

But, if you try out Ubuntu, give it a fair chance, I am sure, you will never go back to Win anything ever again......

---

### Post by coffeecat on 2013-07-16
> **JK700 said:**
> 
Here is what I got...

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2344

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   616820735   308409344   83  Linux
/dev/sda2   *   616822782   625141759     4159489   ef  EFI (FAT-12/16/32)
```

```
/dev/sda1: UUID="eacb195a-5c2a-410a-889e-9f6a55b31d5f" TYPE="ext4" 
```

The bad news is that you have neither the original Vista partition, nor the recovery partition. 

> **JK700 said:**
> It's not that I actively dislike Ubuntu, it's just that I'm not familiar with it and have been used to Windows Vista.

Without a recovery partition, you will need some sort of Windows installation medium, whether you choose Vista, 7 or 8. One disadvantage of using a Microsoft Windows installation disc is that you will get a vanilla Windows installation without any of the special drivers that you might need for that laptop. Check with your cousin to see whether they created a set of recovery DVDs before they wiped the HD to install Ubuntu. With them you can restore the laptop to factory condition, complete with the special drivers. An alternative would be to contact HP. They will probably be prepared to sell you a set of recovery DVDs for that model - i.e. you would end up with a version of Vista tweaked ready for the laptop - but they would likely not be cheap.

And the final (and best! :)) alternative would be to stick with Ubuntu. You have a large number of helpful people on this forum who can help you with the learning curve. What exactly do you want to do with that laptop? You might find that Ubuntu will suit you well and would most likely run better than Vista.

---

### Post by Jerry N on 2013-07-16
> **coffeecat said:**
> ...... An alternative would be to contact HP. They will probably be prepared to sell you a set of recovery DVDs for that model - i.e. you would end up with a version of Vista tweaked ready for the laptop - but they would likely not be cheap.....

I have ordered recovery disk sets from HP for people.  I think the cost was about $16 the last time.  

Jerry

---

### Post by JK700 on 2013-07-16
> **coffeecat said:**
> And the final (and best! :)) alternative would be to stick with Ubuntu. You have a large number of helpful people on this forum who can help you with the learning curve. What exactly do you want to do with that laptop? You might find that Ubuntu will suit you well and would most likely run better than Vista.

Thanks.

I don't intend to do anything out of the ordinary or special with this laptop, just fairly standard stuff. Surf the web, watch tv/film, downloads, social media, etc.

It's just for example, this is a small thing but a program I used to use on Windows was **CCleaner**. There doesn't seem to be a Linux version of it available although a quick Google search tells me there is something called BLEACHBIT which is the best alternative.

And I've always used AVG for anti-virus, I'm not even sure what I have at the moment, will have to check.

I barely know what programs/software I have on this, as I'm so used to Windows and going in Control Panel -- Add/Remove Programs it's just going to take some getting used to. I also don't like the fact that the launcher (I think it's called that?) is on the left hand side of my screen, would be better at the bottom. 

I think I'm going to stick with Ubuntu as like you say it will probably be easier and I may grow to like it and could never turn back to Windows again. I guess I'll just have to try and have a play with settings and tweak the desktop to something I like.

Is Ubuntu 13.04 the most recent version available?

---

### Post by jdwaugh on 2013-07-16
I think you will like it once you get used to it.  I switched to Ubuntu from using Windows back in Dec. and once you get used to it it is much easier to do things than Windows, imo.

KDE may give you a more familiar presentation, it defaults to a menu system that is similar.  A guick goodle search will find you directions on how to install, and best part is it is easy to switch back if you want to.

As for software, open up the Software Center, and just search for what you want to do, generally there are multiple options to try to find one that works for you.  As for anti-virus, you don't really need one, few malicious programs exist for Linix/Unix systems.

Have fun, ask questions, and learn something new.  It is what keeps you young.

---

### Post by mörgæs on 2013-07-16
Yes, 13.04 is the most recent one. The number refers to 2013, 4th month.

Agree with the posters above. Now you have tried Windows for a number of years, why not give Ubuntu a chance for a few weeks? We are here when a question appears.

---

### Post by monkeybrain2012 on 2013-07-16
> **JK700 said:**
> Thanks.

It's just for example, this is a small thing but a program I used to use on Windows was **CCleaner**. There doesn't seem to be a Linux version of it available although a quick Google search tells me there is something called BLEACHBIT which is the best alternative.

And I've always used AVG for anti-virus, I'm not even sure what I have at the moment, will have to check.



Yes, bleachbit would be like CCleaner. But unlike CCleaner, it doesn't come with crapware like Ask toolbar. :)
You don't need anti-virus for Ubuntu.

---

### Post by craig10x on 2013-07-16
Yes 13.04 is the latest version and it's really great!  If you don't mind using a dock, then you may get to like unity which actually is a dock which you can auto-hide when not using, and even make it smaller (setting available in the system settings under appearance and behavior...What most of us do is put their favorites and frequently used apps on it for quick 1 click access and for the less used apps, just bring them up in the "dash" (search button on top of the dock) to bring them up quickly...it's pretty neat once you get use to it...

Kubuntu would look more like windows to you but why not try something different as long as your trying ubuntu? :D

---

### Post by JK700 on 2013-07-16
> **monkeybrain2012 said:**
> You don't need anti-virus for Ubuntu.

Really? I'm sure you're right but having no anti-virus on a PC/Laptop is an alien concept to me. 

How? Why?

So it's safe to use online banking on Ubuntu right? I'm having to use my old Desktop PC to do that at the moment as even though it's extremely slow I feel confident as it has all the programs and software that I've placed my confidence in over the years.

---

### Post by coffeecat on 2013-07-16
> **JK700 said:**
> Really? I'm sure you're right but having no anti-virus on a PC/Laptop is an alien concept to me. 

How? Why?

A couple of wiki pages that you might find useful:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

I'd really recommend reading through the second. People coming from the Windows world tend to over-emphasise the importance of AV software when considering security. There are bigger threats than viruses when using a Linux system. And since it is extremely unlikely that there are any Linux viruses in the wild at the moment, the best that you are likely to achieve by running AV software in Ubuntu is to ensure that your Ubuntu system doesn't harbour any Windows viruses! :)

---

### Post by craig10x on 2013-07-16
Yep it is true...i know, hard to believe coming from windows but i can tell you i have been running linux (mostly ubuntu but other "distros" as we call them too) and have not gotten one single virus, malware, trojan, you name it...and yep...no virus scanners...Linux is very secure by default...and even it's firewall that is built in has all ports closed...the only thing i do is download gufw from the software center which is a gui to access the firewall, and just turn it on...makes you even more "stealth" (invisible)...

Windows viruses cannot affect linux by the way...

---

### Post by monkeybrain2012 on 2013-07-16
One reason (not the only one of course, see the WIki) that makes Linux a lot safer is that it discourages certain user habits, such as downloading random freeware on the web. It is interesting that in Windows people do that almost without thinking and even legit software can be compromised if you download it from some secondary websites. For example, some spyware company has put out a hacked version of Firefox on some download site (other than mozilla's ) and have compromised some Windows Installations. And it seems that Windows freeware always comes bundled with some kind of crapware/otherwise dubious stuffs, and that is even true with antivirus software. For example, Avast! apparently installs Chrome behind your back. Now Chrome is not strictly a crapware, but the way that it gets stealthy installed when one tries to install an AV is disturbing (I tried to set in up on someone's Windows box recently. I did it twice to found out what happened and I couldn't find an option to not install Chrome, in fact I couldn't even find Chrome mentioned in the installation process) If they can install Chrome what else can they install? It is such a common thing in Windows that it indicates a very insecure and permissive culture for installing things.

---

### Post by Jerry N on 2013-07-16
> **monkeybrain2012 said:**
> ....
You don't need anti-virus for Ubuntu.
A whole bunch of Macintosh users thought that too.  Oops!
Don't bet the farm that there will never be a concerted malware attack on Linux.  
In case you are wondering, I don't use an AV program with Linux either but after 6 years of testing and experimentation Linux still isn't my primary operating system.

Jerry

---

### Post by monkeybrain2012 on 2013-07-16
> **Jerry N said:**
> A whole bunch of Macintosh users thought that too.  Oops!
Don't bet the farm that there will never be a concerted malware attack on Linux.  
In case you are wondering, I don't use an AV program with Linux either but after 6 years of testing and experimentation Linux still isn't my primary operating system.

Jerry



Mac's security model is not the same as Linux. For one thing, it is not open sourced so there is no constant monitoring and fixing of weaknesses,Just because you are too timid to switch to Linux doesn't mean there is anything wrong with Linux, or that AV is a better way to protect you (which is but a band-aid for an insecure system), it just shows that you have some strange ideas of how things work. :)

---

### Post by Smallwheels on 2013-07-16
The version of Vista I had didn't work well. Maybe HP just didn't put enough work into making everything function properly. If you have't used Vista on that machine you really don't know how much trouble you would have. Maybe it would work perfectly (as perfectly as Vista can work, joke)  Ubuntu is free and runs faster once you get everything functioning. That is the big thing though. It takes tweaking. I'm in that situation now. Maybe your installation already has everything working. If so then just get familiar with everything and you'll find it more intuitive than any Windows or Mac system.

---

### Post by craig10x on 2013-07-16
By the way, Google Chrome IS safe to download properly from Google's actual website...if you download it from some other site, you may encounter something you don't want (security wise) depending on the site...so for that i would only use their site to get it...Chrome is an excellent browser for linux....in fact, it is my favorite and primary browser...

---

### Post by arranskye on 2013-07-16
I have bought and used windows xp, vista, and win 7 restore disks from ebay and all have worked perfectly. They cost little more than pennies.  £5.00  tops. I_**ts absolutely essential that you have the correct COA product licence, **_a lable usually stuck to the bottom of the laptop.
I had recovery partitions and recovery disks but choose this method to get "bare bones" disks devoid of all the MS/HP bloat & rubbish.  In fact the win 7 on this PC now was installed from an ebay reinstallation disk.

However try Ubuntu for 10 days and you will never want to use Windows anything again.

---

### Post by waynefoutz on 2013-07-16
I might be of some help here. I've refurbished a few laptops in my day, and have found the most inexpensive place to get the original restore disks is from the manufacturer, if they don't have it, restoredisks.com has disks for virtually every model of computer ever made, fairly inexpensive. I've purchased their restore disks a few times, never a problem. This way you get not only the original OS, but all the right Windows drivers installed as well. [http://www.restoredisks.com/]("http://www.restoredisks.com/")

---

### Post by Bucky Ball on 2013-07-17
? If CCleaner is your only worry, don't worry. You don't need it. Install and start learning. If the things you outlined are all you want to do you don't need Windows, and you also don't need CCleaner on Ubuntu. I have personally never used Bleachbit either (it can kill things if you don't know what you're doing).

I would personally recommend the long-term support release for new-comers, 12.04 LTS. Five years support and a good place to start. Try from disk first.

---

### Post by mastablasta on 2013-07-17
> **JK700 said:**
> Thanks.

I don't intend to do anything out of the ordinary or special with this laptop, just fairly standard stuff. Surf the web, watch tv/film, downloads, social media, etc.

Which is exactly why we went with linux opn new HP laptop. spending 100EUR+ just to do those things in windows seemed like overkill (i mean since they can be done in linux just as well...).

> 
It's just for example, this is a small thing but a program I used to use on Windows was **CCleaner**. There doesn't seem to be a Linux version of it available although a quick Google search tells me there is something called BLEACHBIT which is the best alternative.


Linux is not windows and these programmes are not necessary. have you ever heard of Google or Facebook running bleachbit on their servers (both use linux for them)? POint is linux works in a completely different way than windows. the OS was designed primarily for servers (i mean the OS that linux kernel is based on) but then moved sort of to desktop.
Yeah bleachbit is alternative. also computer janitor. but they can do more harm than good if you don't know how to use them. and they are not necessary.

> 
And I've always used AVG for anti-virus, I'm not even sure what I have at the moment, will have to check.


It is not needed as they mostly scan for windows viruses. however if you want some free ones i think Avast and Avira are descent. ClamTk also works.

> 
I barely know what programs/software I have on this, as I'm so used to Windows and going in Control Panel -- Add/Remove Programs it's just going to take some getting used to. I also don't like the fact that the launcher (I think it's called that?) is on the left hand side of my screen, would be better at the bottom. 

You can find them in software center (package manager)

have a look at this interface:
[http://www.kubuntu.org/feature-tour](http://www.kubuntu.org/feature-tour)

That is Kubuntu and that one realyl does work like windows or not. it is fully customizable. you can give it a windows 7 theme if you would like to.

There is also a distribution based on Ubutnu called Zorin OS that has same interface as widnows 7.

> 
Is Ubuntu 13.04 the most recent version available?

yes most recent stable version. there is also testing alpha of 13.10 which comes out in October. in April next year a new LTS (long term support) comes out with 5 years of support.

read Ubutnu manual (link in my siganture). it is a really a good community made manual oriented towards those that first enocunter the OS.

> **waynefoutz said:**
> I might be of some help here. I've refurbished a few laptops in my day, and have found the most inexpensive place to get the original restore disks is from the manufacturer, if they don't have it, restoredisks.com has disks for virtually every model of computer ever made, fairly inexpensive. I've purchased their restore disks a few times, never a problem. This way you get not only the original OS, but all the right Windows drivers installed as well. [http://www.restoredisks.com/](http://www.restoredisks.com/)

that's a really good option. unfortunatelly a disk for my laptop is not there. maybe because it is still new. but still it is good to know this exists. bookmarked i gues....

---

### Post by MirrorUniverse on 2013-07-17
> I barely know what programs/software I have on this, as I'm so used to  Windows and going in Control Panel -- Add/Remove Programs it's just  going to take some getting used to. I also don't like the fact that the  launcher (I think it's called that?) is on the left hand side of my  screen, would be better at the bottom. 			 		
Like mastablasta said you could go to Ubuntu Software Center and click on "Installed" near the top of the screen to see lists of installed programs grouped by category.  Alternatively, you could use Synaptic Package Manager and click on the "Status" button near the lower left, then select "Installed" from the resulting menu on the left side of the screen.
As far as the launcher, you might be able to right click on it, go to Panel -> Panel Preferences and change settings that way.  I use Xubuntu, so my interface is different and that may not be an option for you.

---

### Post by mastablasta on 2013-07-17
XUBUNTU! another awesome highly cusotmizable desktop:
[http://xubuntu.org/tour/](http://xubuntu.org/tour/)
[http://xubuntu.org/screenshots/](http://xubuntu.org/screenshots/)

it is so easy to move the launcher arround in Xubuntu (uses XFCE) and also it is really easy to add and change things in various panels/windows. it has an additional bonus of using a lot less memorry than default Ubuntu.

to install it you can do it from software center - just find and install Xubuntu-desktop, then logout, change desktop and login. same goes for other desktops. Lubuntu is even lighter but it is not so easy for newcommer to configure it i believe.

one thing i need to mention here is that when you add a deskotp environment like that, you might get some duplicated indicators (e.g. two battery monitors, two network monitors...). but if you like the different newly installed  desktop we can help you remove them easilly.

---

### Post by kurt18947 on 2013-07-17
Another option would be to install XFCE, not XFCE-desktop.  I like the default apps in Ubuntu so didn't want the clutter of Xubuntu-default apps.  Installing XFCE seems to work well.  The only malfunction I've found compared to Ubuntu 13.10 w/ gnome-shell is in Thunderbird's compose.  With gnome-shell I can drag graphics files to the compose screen and they're added inline.  XFCE requires adding them as attachments, they can't just be dragged to the compose screen.  Other than that XFCE on 13.10 seems to function as advertised.

---

### Post by JK700 on 2013-07-17
Even though I can't reply directly to every post I just want to extend my thanks for all your replies and help in this topic!

I am in the process of installing XUBUNTU right now.

In terms of browsers I've always used Firefox but I can't seem to get the font quite right. I don't know what it is but it just doesn't look or feel "right". Is there an optimal font and size I should be using?

---

### Post by coffeecat on 2013-07-17
> **JK700 said:**
> 
In terms of browsers I've always used Firefox but I can't seem to get the font quite right. I don't know what it is but it just doesn't look or feel "right". Is there an optimal font and size I should be using?

What might help is to install the package ttf-mscorefonts-installer which gives you the Microsoft corefonts. A lot of websites use something like Verdana, which is one of the corefonts, and without this Firefox defaults to an open source alternative which, to my eyes, is not as good design-wise. You can install just the ttf-mscorefonts-installer package, but a better option might be to install the package ubuntu-restricted-extras (or xubuntu-restricted-extras if using xubuntu) which will also give you a number of restricted multimedia codecs, flash and so on, none of which come in the box in a default install. You need to agree to a EULA when installing the mscorefonts, so it's a good idea not to leave the package manager unattended when installing this package.

What you are seeing might be because of not having the correct fonts installed, or might be because of differences in font rendering between the Ubuntu family and Windows. I find Ubuntu font-rendering very good and Windows somewhat unpleasant, but that is just my opinion/taste. Others have the opposite opinion and prefer Windows type font rendering. If you find that the fonts in Firefox are still not right after installing the core fonts, then I suggest you start a new thread specifically about fonts, and someone might be able to help you.

---

### Post by oldrocker99 on 2013-07-17
I know it can be a bit scary to abandom Windows for GNU/Linux, but it's ultimately something you'll be glad you did. Open source software is PEER-REVIEWED (you know, like science), which is why it is so much more secure than any closed source OS.

As a Windows user, **you are** the administrator, which means any malware on your system can install itself (if your antivirus software doesn't detect it, and, believe me, that can happen) and hose your system. GNU/Linux systems' users, even if they have administrator access, MUST type in their passwords before altering the system in any way, and they get **temporary** root access. Compare this to Windows, which puts up "Do you want to do this?" dialogs, in which many Windows users just click "Yes" at. If they didn't read which program is trying to alter the system, they could be attacked.

Remember that (virtually) all the software you install is from approved repositories, and is 99+% safe to install. Contrast that with popular Windows programs which install toolbars, etc. And those are the UNharmful ones.

---

### Post by Bucky Ball on 2013-07-17
Xubuntu. Nice choice, use it myself, and great place to start. Minimal bells and whistles (unless you add them later) and will definitely do what you're after.

Install ttf-mscorefonts-installer as suggested by coffeecat to help with fonts. You should be able to find them in Synaptic Package Manager (in Xubuntu), which will be in the drop down apps menu at the far left under the 'System' heading. ;)

---

### Post by craig10x on 2013-07-17
After you install the microsoft fonts you may want to try Google Chrome... once the microsoft fonts are installed, you will be very pleased with the font rendering in the Chrome browser...
You can download the deb file from the Google Chrome website and once you have it...right click and select "open with ubuntu software center" and let it install it for you...

I find it is much easier to make font settings in Chrome then Firefox...actually, once the ms core fonts are installed it defaults to them automatically!  The only change i make is change the font sizes up by 2 (from the default 16 to 18) for my personal preference...otherwise, i leave the settings as they are...

If you decide to try it...suggest you use Chrome not Chromium from the software center....Chrome is more complete with up to date flash, built in pdf reader and they will send you updated versions through the software center automatically!...

---

### Post by monkeybrain2012 on 2013-07-17
> **craig10x said:**
> After you install the microsoft fonts you may want to try Google Chrome... once the microsoft fonts are installed, you will be very pleased with the font rendering in the Chrome browser...
.


I am very pleased without MS fonts. I wouldn't give the impression that it is something that one is expected to do after installing Ubuntu (like some blogs on "10 things to do after installing Ubuntu XX.XX") because somehow MS fonts are better, I think the default fonts are just fine. 
 
For new users who are puzzled that the MS EULA comes up when installing restricted-extras, If one doesn't want MS fonts just don't agree to EULA and press enter then package manager will continue installing the rest without MS fonts.

---

### Post by craig10x on 2013-07-18
True but the microsoft fonts installation doesn't change the ubuntu fonts that are used in the interface and all the windows, it only adds them to your web browser's font selection...without mscore fonts installed, Google Chrome is defaulted to a different font but changes to the ms fonts as the default when they are installed...but the original default fonts and other styles are still available to select if one prefers of course...;)

---

