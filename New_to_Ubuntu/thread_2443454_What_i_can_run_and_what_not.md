---
title: "What i can run and what not"
date: 2020-05-15
forum: New to Ubuntu
---

### Post by dimitargeorgiev5 on 2020-05-15
Hi guys,

One thing lead to another and here i am in the Ubuntu forum, ready to pull the trigger and migrate from Windows 10. But i have a few questions and i would like to ask and eventually get answers. :)

1. Is the performance i get from the live preview the same if i actually install the distro?

2. I will post a list of everything i use on my computer, please tell me what can i run and i cant. I know that some apps have alternatives like Photoshop and GIMP, MS Office and Libre etc. I am fully ok with that. Here is the list:

- PDF Viewer - Acrobat
- Adobe Illustrator
- Adobe Photoshop
- Video Codecs - its kinda let down that these are not included out of the box!
- Audacity
- ACE Stream
- uTorrent
- Trello - I need a kanban app
- Skype
- Spotify
- Viber
- Whatsapp
- Telegram
- Team viewer
- Your Phone - I have an android and i really love to be able to access my messages and the actual screen of my phone on my PC

Thank you for the help.

---

### Post by fhesseti on 2020-05-15
Im no expert, and fresh off the windows boat myself looking to stay here, but i will go off of experience and what i deem to be common sense. If anyone reads this and sees something wrong please correct me

1.It should be better as your drive will most likely be way way way quicker than the usb stick you used (unless you did it another way).
2. Ill answer as many as i can for now and get back to you if i find out anymore. Currently looking into the your phone app as I am in the same boat as you with that one. by the way, try searching for apps in the ubuntu software app, search button is in the top left of that and its basically what the windows store should have been. If the app doesnt show up there, It may take some deeper browsing on the web but most of the time it will be there.
Team viewer YES
Telegram YES
Spotify YES
Whatsapp YES
Skype YES
Kanban apps YES
Audacity YES
Video Codecs YES
uTorrent YES, BUT MAY NOT WORK WELL. PLENTY OF ALTERNATIVES THAT ARE ACTUALLY BETTER IMO SUCH AS QBITTORRENT
Acorbat SORT OF. TECHNICALLY YES BUT OUTDATED SINCE 2013
Adobe Photoshop NO (alternative is GIMP)
Adobe Illustrator NO (alternatives can be found with a little research)

Found all these with a simple search in the Ubuntu Software app

---

### Post by Autodave on 2020-05-15
fhesseti did pretty good on his answer!  

First of all, Ubuntu, Xubuntu, whatever 'buntu will be quicker than you live preview and much faster than any Windows version you may have.  

The programs that he didn't know of, I unfortunately don't know either.  Viber does list a linux download on their website, so you should be good to go on that, too.  Further looking shows that VLC should be able to do what ACE Stream does.

I want you to keep this in mind: whenever possible insall the program(s) you want from the Software center before going after online programs.  'buntu is made to be very secure and the programs in the Software center will be secure.  Online progs? Maybe.

Also keep in mind that Linux is NOT Windows. Gone are the days of defragging HDDs, worrying about viruses (unless you do something really risky), updates that take minutes to hours to run, not being able to do anything while updates are being installed., etc.  No more CCleaner either.

---

### Post by grahammechanical on 2020-05-15
> - Video Codecs - its kinda let down that these are not included out of the box!

There is a reason that they are not included in the distribution. But if I remember correctly we can tick a box during installation to have them downloaded and installed at the same time as Ubuntu is installed.

Note the fourth tick box

[URL="https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#5-prepare-to-install-ubuntu"]https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#5-prepare-to-install-ubuntu

[/URL]Some Linux users don't want proprietary software for ethical reasons. So, it is not forced on them. In some countries it might be illegal to download these codecs. So, the user has to take responsibility.

I do not think it fair to describe this situation as a let down. Be prepared for further let downs as Linux developers never have had and never will have the intention of providing a cheap, very cheap copy of the Microsoft operating system. Linux developers have their own ideas about what a computer operating system should be like and are very independently minded.

Regards

---

### Post by Perfect Storm on 2020-05-15
If you're into games, there's Steam that works great on Linux. Just saying (the more the merrier) :KS

---

### Post by CatKiller on 2020-05-15
It's already been covered pretty well, but I'll highlight a couple of things.

> **dimitargeorgiev5 said:**
> 1. Is the performance i get from the live preview the same if i actually install the distro?

The performance of the installed version will be better than the live one: applications need to be loaded from the USB drive (or DVD) before they can be run in the live environment, so they're slower to start than they would be when installed to a hard drive; Intel and AMD graphics drivers are open source, meaning they can work in the live environment, but Nvidia drivers are proprietary, which means that they need to be installed before they work, so graphics performance on Nvidia hardware will be lower in a live environment. PopOS gets round that by having an Nvidia live image and an Everything Else live image; Ubuntu has just the one image that can install the Nvidia driver.

> - PDF Viewer - Acrobat
- uTorrent

Ubuntu flavours come with a PDF viewer and a torrent client out-of-the-box. Others are available through the software repositories; different desktop environments will use different applications, but the *function* is available in all of them.

> - Adobe Illustrator
- Adobe Photoshop

Adobe don't release software for Linux. There are alternatives that you may or may not get on with that will do the same sorts of things. Or you can run Windows in a VM just for those if you really need those specific applications; my understanding is that they don't work well under Wine.

All the rest are all available natively.
> - Your Phone - I have an android and i really love to be able to access my messages and the actual screen of my phone on my PC

[KDEConnect](https://community.kde.org/KDEConnect) is included with Kubuntu (which I would recommend to new users over the vanilla Ubuntu that comes with Gnome) or there is [an extension](https://extensions.gnome.org/extension/1319/gsconnect/) for Gnome that uses the same framework.

---

### Post by crip720 on 2020-05-15
You don't mention what hardware you are using, but imagine it is on the decent side.  You can probably use any desktop/distro, but some are lighter that others and can give better performance.  Comes down to what you think is best looking, unless the hardware is on the weak side and limits your choices some.

---

### Post by sisco311 on 2020-05-15
> **dimitargeorgiev5 said:**
> 
- Your Phone - I have an android and i really love to be able to access my messages and the actual screen of my phone on my PC


For messages/notifications and more you can use [gsconnect]("https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect") or KDE Connect.

To mirror and control your Android phone you can use [scrcpy]("https://www.omgubuntu.co.uk/2019/07/scrcpy-mirror-android-to-ubuntu-linux").

> **Autodave said:**
> 
I want you to keep this in mind: whenever possible insall the program(s) you want from the Software center before going after online programs.  'buntu is made to be very secure and the programs in the Software center will be secure.  Online progs? Maybe.


+1

---

### Post by TheFu on 2020-05-15
Linux isn&#8217;t Windows.  There's a completely different philosophy for the OS and for most applications. Learn those differences to become happier.  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

- PDF Viewer - Adobe controls the PDF file standards. They have an interest to keep changing it to sell "new" versions of PDF creation sorftware.  Basically, the non-commercial Linux versions are on v1.6 of the PDF standard. That's pretty old. There are $30 commercial PDF tools for Linux that have free trials if you need more. I think they implement the newer standards.
- forget about adobe stuff. They hate linux.
- Video Codecs - Linux has a different method.  Use **vlc** or **mpv** to playback any video file you should want to see on the planet.  All popular codecs are compiled into those tools. Different gui front-ends exist. The only stuff lots of us want are the DRM libraries to access commercial DVD videos. That's easily handled either at install time (install proprietary codecs) or after by installing a DVD DRM library. I don't know about Bluray, sorry.
- Audacity - there's a native version. I use it all the time. There are lots of batch processing tools as well, which I tend to use to make my audacity sessions shorter.
- Team viewer - there are so many better tools on any Unix that we don't need to trust some 3rd party. Learn **ssh** and x2go.
- Your Phone -  GSConnect, KDE Connect or just **scrcpy**. I&#8217;ve played games using scrcpy this week over a USB connection.  Depends what you need. I use typical Unix tools to sync files between the phone and PC - rsync, ssh, sftp, nextcloud. Usually, just USB connect, open a file manager and drag-n-drop any files either way as needed.

Don't go outside the package management system.  Definitely don't go looking for a setup.exe on any Linux.

System Maintenance for Ubuntu Desktops: [https://blog.jdpfu.com/linsysmaint](https://blog.jdpfu.com/linsysmaint) Lifehacker republished it, but I've updated it every few years as new releases change things, fix things, include better tools.

---

### Post by Autodave on 2020-05-16
Team Viewer works very well on Linux.  GIMP will replace your Photoshop.  I have used both of those and actually prefer Gimp over Photoshop.

---

### Post by dimitargeorgiev5 on 2020-05-16
> **fhesseti said:**
> Im no expert, and fresh off the windows boat myself looking to stay here, but i will go off of experience and what i deem to be common sense. If anyone reads this and sees something wrong please correct me

1.It should be better as your drive will most likely be way way way quicker than the usb stick you used (unless you did it another way).
2. Ill answer as many as i can for now and get back to you if i find out anymore. Currently looking into the your phone app as I am in the same boat as you with that one. by the way, try searching for apps in the ubuntu software app, search button is in the top left of that and its basically what the windows store should have been. If the app doesnt show up there, It may take some deeper browsing on the web but most of the time it will be there.
Team viewer YES
Telegram YES
Spotify YES
Whatsapp YES
Skype YES
Kanban apps YES
Audacity YES
Video Codecs YES
uTorrent YES, BUT MAY NOT WORK WELL. PLENTY OF ALTERNATIVES THAT ARE ACTUALLY BETTER IMO SUCH AS QBITTORRENT
Acorbat SORT OF. TECHNICALLY YES BUT OUTDATED SINCE 2013
Adobe Photoshop NO (alternative is GIMP)
Adobe Illustrator NO (alternatives can be found with a little research)

Found all these with a simple search in the Ubuntu Software app

Thanks for the detailed answer!

> **Autodave said:**
> fhesseti did pretty good on his answer!  

First of all, Ubuntu, Xubuntu, whatever 'buntu will be quicker than you live preview and much faster than any Windows version you may have.  

The programs that he didn't know of, I unfortunately don't know either.  Viber does list a linux download on their website, so you should be good to go on that, too.  Further looking shows that VLC should be able to do what ACE Stream does.

I want you to keep this in mind: whenever possible insall the program(s) you want from the Software center before going after online programs.  'buntu is made to be very secure and the programs in the Software center will be secure.  Online progs? Maybe.

Also keep in mind that Linux is NOT Windows. Gone are the days of defragging HDDs, worrying about viruses (unless you do something really risky), updates that take minutes to hours to run, not being able to do anything while updates are being installed., etc.  No more CCleaner either.

Does this mean that i dont need antivirus or firewall?

> **grahammechanical said:**
> There is a reason that they are not included in the distribution. But if I remember correctly we can tick a box during installation to have them downloaded and installed at the same time as Ubuntu is installed.

Note the fourth tick box

[URL="https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#5-prepare-to-install-ubuntu"]https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#5-prepare-to-install-ubuntu

[/URL]Some Linux users don't want proprietary software for ethical reasons. So, it is not forced on them. In some countries it might be illegal to download these codecs. So, the user has to take responsibility.

I do not think it fair to describe this situation as a let down. Be prepared for further let downs as Linux developers never have had and never will have the intention of providing a cheap, very cheap copy of the Microsoft operating system. Linux developers have their own ideas about what a computer operating system should be like and are very independently minded.

Regards

I respect the work and the knowledge of the developers!

> **Artificial Intelligence said:**
> If you're into games, there's Steam that works great on Linux. Just saying (the more the merrier) :KS

Thanks, but i dont game at all! :)

> **CatKiller said:**
> It's already been covered pretty well, but I'll highlight a couple of things.



The performance of the installed version will be better than the live one: applications need to be loaded from the USB drive (or DVD) before they can be run in the live environment, so they're slower to start than they would be when installed to a hard drive; Intel and AMD graphics drivers are open source, meaning they can work in the live environment, but Nvidia drivers are proprietary, which means that they need to be installed before they work, so graphics performance on Nvidia hardware will be lower in a live environment. PopOS gets round that by having an Nvidia live image and an Everything Else live image; Ubuntu has just the one image that can install the Nvidia driver.



Ubuntu flavours come with a PDF viewer and a torrent client out-of-the-box. Others are available through the software repositories; different desktop environments will use different applications, but the *function* is available in all of them.



Adobe don't release software for Linux. There are alternatives that you may or may not get on with that will do the same sorts of things. Or you can run Windows in a VM just for those if you really need those specific applications; my understanding is that they don't work well under Wine.

All the rest are all available natively.


[KDEConnect](https://community.kde.org/KDEConnect) is included with Kubuntu (which I would recommend to new users over the vanilla Ubuntu that comes with Gnome) or there is [an extension](https://extensions.gnome.org/extension/1319/gsconnect/) for Gnome that uses the same framework.

Thank you, i have Ryzen with Radeon, no problems at all!

> **crip720 said:**
> You don't mention what hardware you are using, but imagine it is on the decent side.  You can probably use any desktop/distro, but some are lighter that others and can give better performance.  Comes down to what you think is best looking, unless the hardware is on the weak side and limits your choices some.

Ryzen 7, 8gb ddr4, 256ssd, on an Asus Vivobook.


Thanks to the whole community, now i need to istall gnome extensions and gnome tweaks, and i guess that i can delete the windows drive and go full on Ubuntu!

---

### Post by Autodave on 2020-05-16
The antivirus and firewall question will get arguments both ways.....and many of them.  Unless you are visiting very shady sites and leave your PC open to anyone and everyone, my opinion is that you do not need either.  

Antivirus: basically there aren't any for Linux.  Windows viruses and Mac viruses will not affect you at all.

Firewall: again, I personally have never had the need for one.  You mileage may differ.  Right now, I have 13 computers operating at my home, friends' homes, and my church.  The one at church has many different users.  The ones at friends' homes have who knows how many users.  I have been using 'buntu for over 10 years now with no antivirus or firewall.  Total issues: 0.

---

### Post by dimitargeorgiev5 on 2020-05-16
You are a true hero, Sir!

---

### Post by TheFu on 2020-05-16
Linux security is as complex as any platform, but the really comes down to what you are doing, which services are being run, and other risk factors.

There **are** viruses for Linux, but they tend to be C[SUP]2[/SUP] type malware, not take-over-a-Windows-machine versions. There have been worms for Unix systems long before Windows had networking.  If you load up WINE (say to run TeamViewer), then there is a risk of getting certain Windows viruses.  Depending on the setup for WINE, those viruses might see outside the emulated environment and encrypt all the files permissions allow.   [https://askubuntu.com/questions/562388/do-wine-viruses-only-work-while-wine-is-running](https://askubuntu.com/questions/562388/do-wine-viruses-only-work-while-wine-is-running)

If you don't run any network services, always stay behind a patched hardware router/firewall, and don't do high risk activities, then the risks for a maintained Linux system getting a virus or being hacked is pretty tiny.  There are threads in these forums where people have been hacked, so it does happen.  The last 2 months, I've personally seen the phishing email attempts drastically increase from about 1 a month to 4 a day.  
There is a Security sub-forum here that has a number of sticky threads at the top.  Those are very worth reading.  
[LIST]
[*][https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)  Basic Ubuntu Security
[*][https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338) <---- Security forum
[/LIST]

With all that said, I don't run AV on my desktops (including Windows) unless required to do so by a business contract or my E&O Insurance policy. I do run AV on the email server.

When I'm doing riskier activities, I'll run those programs inside a sandbox, container or VM separate from the rest of the system.  By default, my email program and browser run constrained. When doing risky stuff, a new browser instance will be started with an overlay file system to prevent any writes by the browser from ever hitting storage.  Sadly, snap packages have broken this capability and I don't have an easy solution besides having a full container that gets created/destroyed with every run.

---

### Post by Autodave on 2020-05-16
Not arguing with TheFu: just saying that Teamviewer makes a Linux version so there is no need to run WINE for that program.

---

### Post by TheFu on 2020-05-16
> **Autodave said:**
> Not arguing with TheFu: just saying that Teamviewer makes a Linux version so there is no need to run WINE for that program.

No argument when there are facts.  I hadn't looked at teamviewer before for a number of reasons.
[https://community.teamviewer.com/t5/Community-Blog/The-Wait-is-Over-Presenting-TeamViewer-s-Native-Linux-Client/ba-p/36765](https://community.teamviewer.com/t5/Community-Blog/The-Wait-is-Over-Presenting-TeamViewer-s-Native-Linux-Client/ba-p/36765)  
[https://www.teamviewer.com/en-us/download/linux/](https://www.teamviewer.com/en-us/download/linux/)
Options are good, since we aren't all the same types of users with identical needs. ;)

---

### Post by ActionParsnip on 2020-05-17
Plenty of torrent clients for Ubuntu. WhatsApp runs in your Web browser. There are PDF viewers galore in Ubuntu (Chrome can do it too). Your Adobe products may run in WINE (See WINE AppDb for compatibility) or you can switch to open source solutions like GIMP.

---

### Post by ActionParsnip on 2020-05-17
[https://www.omgubuntu.co.uk/2019/07/scrcpy-mirror-android-to-ubuntu-linux](https://www.omgubuntu.co.uk/2019/07/scrcpy-mirror-android-to-ubuntu-linux)

---

