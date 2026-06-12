---
title: "Possible to watch youtube, netflix with ubuntu?"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by yonster on 2014-03-13
I am extremely new to Ubuntu, and am actually not much of a "geek" whatsoever.  I use my dinky dell latitude laptop mostly to go on youtube or Netflix.  A friend gave me a 12.10 live disk, so I gave it a try, and found that it wouldn't let me download adobe flash player to watch youtube or to access Netflix.  I noticed that Ubuntu was not even listed as an OS option on the adobe  download site.   Does this mean that it is not possible to access youtube/Netflix via Ubuntu, or is there a way around this problem?

Thank you so much for any help in this  matter :D !

---

### Post by monkeybrain20122 on 2014-03-13
Yes and yes.
A few points
1) Don't install 12.10 as it will reach end of life in April. Get 13.10 which will be supported til July (14.04 is coming out April and will be supported for 5 years but it is now in alpha so I would not recommend it)
2) Install flash through the Software Centre (or better synaptic if you install it) by installing the package ubuntu-restricted-extras. This will install flash along with other multimedia codecs.
3) flash installed this way is not up to date as Adobe has stopped developing flash for Linux except for security updates til 2017. flash 11.2 is definitely good for Youtube and most streaming sites but in the odd events that you need up to date flash, install Chrome as google has some deal with Adobe to package its own flash in chrome which is up to date and works in Linux.
4) For netflix use pipelight on Firefox.
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)
Pipelight also allows you to install Windows' flash on Linux browsers (basically Firefox), it will be useful if you need to watch some drm protected contents (Linux flash doesn't support drm, whether it is system flash from restricted extras or Chrome)
5) Never download flash from Adobe, it will not work (at least not without some work and you have to locate the correct version)

Edited: you don't really need flash to watch Youtube, there are many alternative options
[https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/](https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/)
[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) (note: need to install the greasemonkey addon)
[https://apps.ubuntu.com/cat/applications/minitube-ubuntu/](https://apps.ubuntu.com/cat/applications/minitube-ubuntu/)  (note: there are two versions of minitube in the Software Centre, make sure to get 2.1.5 which is maintained by the developer, the other one is maintained by Ubuntu community or whatever, it is outdated and wouldn't work)

---

### Post by yonster on 2014-03-13
THANX MB!!  I had already planned to download lubuntu 13.10, but wanted to make sure it was poss to watch youtube/Netflix via Ubuntu first.  Of course, most of what you've said has gone over my head, but I'll certainly attempt your suggestions, for which I am most grateful :) !

---

### Post by monkeybrain20122 on 2014-03-13
Just post back if you have any problem once you are set up.
lubuntu comes with the synaptic package manager so for point 2) change "ubuntu software centre" to synaptic and "ubuntu-restricted-extras" to "lubuntu-restricted-extras"

---

### Post by yonster on 2014-03-13
So if I understand you correctly, 13.10 will no longer be usable after July 2014?

---

### Post by Iowan on 2014-03-13
> **yonster said:**
> So if I understand you correctly, 13.10 will no longer be usable after July 2014?
It'll still be usable, "it receives no further maintenance updates, including critical security upgrades". 
I still have a server running 8.04... not online, of course.

---

### Post by yonster on 2014-03-13
Thanx lowan!  Forgive me for being so ignorant, but when you say "not online, of course," is that because of security threats such as lack of virus updates, or will it actually no longer work online, (or other reason)?  And since we're on the subject, what is the best (free) virus protection software for Ubuntu?

---

### Post by newb85 on 2014-03-13
Unsupported versions still work, but they no longer receive support.  Most importantly, that means you will no longer receive system updates.  If your system isn't up-to-date, that means you aren't protected from exploitation of newly discovered security vulnerabilities.

Bottom line, if you're not operating your system in a vacuum, you're best off using a supported release and keeping it up-to-date.

This is made easier by the availability of lighter variants of Ubuntu, since supported releases of Ubuntu are much more resource hungry than, say 8.04.  The release of Lubuntu's first LTS (14.04) will make keeping up-to-date on older, weaker machines much more effortless.

---

### Post by Iowan on 2014-03-13
Actually, the box sits under my desk at work. It'd be considered a "rogue" machine if I connected it to the corporate network. It hasn't had security updates for... (ever?)...
So, I suppose it operates in a vacuum. :)

---

### Post by newb85 on 2014-03-13
> **yonster said:**
> And since we're on the subject, what is the best (free) virus protection software for Ubuntu?

There's plenty out there on the subject if you do a little searching.  If you're looking for software to protect your Linux system from viruses, that's analogous to preparing to defend yourself from water buffalo if you live in London.  There is a possibility of passing along viruses that affect Windows, and if that is your concern, then it's a different story.

---

### Post by newb85 on 2014-03-13
> **Iowan said:**
> Actually, the box sits under my desk at work. It'd be considered a "rogue" machine if I connected it to the corporate network. It hasn't had security updates for... (ever?)...
So, I suppose it operates in a vacuum. :)
:)

---

### Post by monkeybrain20122 on 2014-03-13
If you want to make updating your OS as easy as possible, when you install lubuntu, choose 'something else' in the installer to manually partition the drive into a root (boot flag /) partition and a separate /home partition (and a swap) That way when you need to install a new version, use the same root partition (/) and home partition but do not format /home, so all your settings and data will be saved.

I don't recommend "upgrade" through the update-manager as it takes a very long time and it tends to break and creates more problems than it is worth. A little work in reinstalling saves a lot of work fixing a broken system later.

---

### Post by thenh813 on 2014-03-13
I couldnt agree more, I have a few partitions, /tmp, /home, / and /boot. Easy reinstalls. :)

@[**[COLOR=#000000]yonster[/COLOR]**]("http://ubuntuforums.org/member.php?u=1910654")
On the antivirus side, you really dont need anything, if you must, install ClamAV from the software center and use it to scan files that worry you. As long as you do not run random shell scripts and Linux binaries you download as root you will have no problem. Also never enter commands (or let anyone enter commands) into a terminal unless you can trust the person telling you to, and search the internet for what it does first (or ask someone like on here). For example if someone tells you to "rm -rf ~/" it would delete all of your documents, music, pictures, videos and settings and anything else. You do not want someone to destroy your data or compromise your system. Look at the post dangerous commands at the top of the absolute beginners fourm or click this link for dangerous commands that you should never let anyone tell you to do unless you know what you are doing. [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326) I reccommend you read the announcement for future reference. Dont make any account you add an Administrator account unless you can trust them with complete controll of the computer. Never install software from "strange" or untrustable sources. Those are the only ways someone else can harm your system. Follow these simple rules and you are safe. Same goes for Windows, dont execute random downloads,dont install random "FREE DOWNLOAD" programs, dont give others Admin accounts unless you trust them and dont execute random commands in Run or CMD.

REMINDER: Please mark the thread as solved from the Forum Tools menu when your question is answered, just letting you know. :)

---

### Post by yonster on 2014-03-14
I'd like to thank all of you who have tried to help me!  Unfortuneately I'm not able to understand most of what you're saying, :( .  For instance, I'm only able to guess what you're referring to when you say "enter into the terminal (such and such)", as the horizontal blinking cursor that appears briefly when booting up the system...  THAT'S how much of a true absolute beginner I am!!  Perhaps I should change my user name to "completelylostcause," because that's what I'm feeling like right now.  At the moment I'm baffled why when I downloaded Lubuntu 13.10 on a completely brand new memory stick, it booted as Xubuntu and looks exactly the same as the Xubuntu 12.10 version I first tried.  

I guess the bottomline to what I'm saying is that if you're going to be kind enough to try to continue to help me, you should probably consider yourself talking to a toddler.  To those of you capable of such saintly patience, THANK YOU SO MUCH!!  To those who are not, that's ok, I understand.

---

### Post by deadflowr on 2014-03-14
> At the moment I'm baffled why when I downloaded Lubuntu 13.10 on a  completely brand new memory stick, it booted as Xubuntu and looks  exactly the same as the Xubuntu 12.10 version I first tried.  

Did you happen to download the lubuntu 13.10 to the same stick as xubuntu 12.10 was on?

Anyway, if you could gives us point to point run downs of what you know, and what you have tried so far then we can try to help you in the most simplest of ways.

For the record, hopefully when you get Lubuntu up and running, you can utilize the Lubuntu Software Center to try to install the various tools you would need to watch stuffs.
We can guide on that if need be.

---

### Post by thenh813 on 2014-03-14
> 
"I'd like to thank all of you who have tried to help me!"


No problem, as I say, these are no stupid questions, not asking one is.

Deleting the other version of ubuntu off the USB before putting the new bersion on. Otherwise it might now work correctly or will start the wrong version, like you experienced. If you wish to have multiple versions of Ubuntu on the same flash drive, use YUMI or similar. [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

Also a terminal is a window like what you see when you start up, so you are right. It is usually found in applications>accessories>terminal. You usually dont need to use it unless you are customizing things, installing things manually or compiling code. Its more of a moderately knowledged or advanced user item. Its similar to the Command Prompt on Windows where you can enter commands. Before Linux/Unix had GUIs, the computer would boot up to a full sscreen text terminal where you would type in commands to use it.

Unix (which is what Linux is based off of) has actually existed since 1969, and ever since then it has been continually built upon and improved. Many other operating systems have been made using its standards. Ubuntu, Debian, Gentoo, Linux Mint, Arch Linux, Crunchbang, Puppy Linux, all are based on the core standards and framework of Unix, and share something in common. There are countless (hundreds of thousands) Linux distros (Like Ubuntu) and there is something for everyone.

To the Live USB drive have Lubuntu, first delete the previous version. This means removing the following files/folders from the usb if they exist: casper; isolinux; syslinux (if existant); boot; [BOOT]; live; .disk

Delete any syslinux.cfg, idlinux.sys or islinux.cfg files off the drive, you have to remove any files that are not yours off the flash drive.

Next download UNetbootin (Linux, MAC and Windows) [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) or YUMI (Windows only) [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/). Take the ISO of Lubuntu you downloaded and put it somewhere like on your desktop, and open Unetbootin/YUMI.

[[img]http://s9.postimg.org/9fwqtb36z/UNetbootin.jpg[/img]](http://postimg.org/image/9fwqtb36z/)
Assuming you are using Unetbootin, click the isoimage button then ... and browse to your ISO. Select the flash drive you are going to be using from the Drive dropdown list (Make sure the type to the left is set to Flash Drive) and click OK. Wait for it to finish and all is done. Simply reboot and start Lubuntu off the flash drive and test/use it or install.

If you are using YUMI it walks you through the process so I dont really have to explain.

Hope these instructions are good enough, if not just tell me and I will make a very detailed screen recording that you can download and watch. Also, Lubuntu is very light and runs decently on older hardware. It uses the LXDE interface (thus the L in from of the Ubuntu in its name). Nice choice, im sure you will be able to use it with confidence prety quickly. I am using a LXDE based Ubuntu also, it is called wattOS and is designed for older computers like the 2001/2003 mixed hardware I am using, Lubuntu works too as I have tried it.

---

### Post by yonster on 2014-03-20
Thanks MB, and to all you other kind souls who responded!  What I ended up doing was following one of MB's suggestions of installing Greasemonkey then Viewtube.  I was a little concerned when on the Youtube sign-in page a high-lighted message said I would be required to update to the latest Adobe flash, but I just ignored it, and it WORKED (WOO-HELL YA-HOO)!!

Oh, and I was obviously successful in finally getting my wack-**** computer to properly dowload and access lubuntu, the details of which I'll post in that thread. 

Now I just have to figute out how to mark this thread as "Solved"...

---

### Post by QIII on 2014-03-20
Hi!

Under "Thread Tools", choose "Mark this thread as solved."

;)

---

### Post by yonster on 2014-03-20
Thanx Qlll, but for the life of me I don't see "thread Tools" *_anywhere_* :( !!

---

### Post by Nick_Germaine on 2014-03-20
I've been using 14.04 for about a week and everything seems fine.  Netflix was a bit harder to setup when I tried a year or two ago.  But I'll try the method above as well.

---

### Post by rewyllys on 2014-03-20
> **yonster said:**
> Thanx Qlll, but for the life of me I don't see "thread Tools" *_anywhere_* :( !!
Scroll up to the top of the page.  Then cast your eye down to the first box with a gray fill-in.  Toward the right side of that box is the option of "Thread Tools".  Click on it, and you'll see a drop-down menu with further options, one of which is "Solved".

---

