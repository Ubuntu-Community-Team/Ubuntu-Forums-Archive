---
title: "HOW TO: online poker with Ladbrokes (Microgaming: 32RedPoker and others)"
date: 2007-02-27
forum: Outdated Tutorials &amp; Tips
---

### Post by wxnker on 2007-02-27
I have been trying to make Ladbrokes Poker and 32RedPoker (both Microgaming) work on Linux for some time and for a while they have been running with only a few bugs. Those bugs where mainly in the lobby.

I'm using **Kubuntu Feisty herd 4.**

_**Ladbrokes:**_
When using this setup method Ladbrokes works perfect for me with no graphics errors at all. As far as I can see it's running like in Windows.

_**32RedPoker and other Microgaming sites:**_
32Red (which should include other Microgaming sites) works but has a few bugs. Game play works fine though.
The lobby is quite slow. To work around the slow lobby issue, move the mouse cursor to the top of the screen to refresh the client. 
As soon as you're at the tables everything speeds up to normal. So there are no real game play issues, just the slow lobby.

I have found guides that told me to install Firefox for Windows, active x for firefox etc. to make these poker clients work and the guides worked. The graphics in Ladbrokes was not perfect when using that method though and W32 also runs better on my system if I use the steps below.

**_How I do it:_**
**1.** Install Wine. I use the newest version 0.9.31. Run "winecfg" at the terminal and Wine configures. I chose "**Win XP**" as default in Wine.
**2.** Install IE6 (IE4Linux) from this thread/link. it's a deb package that will work out of the box. [http://www.ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer](http://www.ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer)
**3.** make sure you set IE6's security settings to allow activeX. I also clicked that IE6 should ask if it's not the default browser. You can du this in "tools/internet options"
**4.** open IE6 and go to: [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp) and click "Download now" to get java for windows.
**5.** open IE6 and go to: [http://www.tatanka.com.br/ies4linux/page/Plugins](http://www.tatanka.com.br/ies4linux/page/Plugins) and install "Shockwave" and "Authorware" from the links on that site. Do not install other versions.

If you just want to use the "**Instant play**" clients then this is it. They work perfectly for me at this stage. If you would like to use the "**Download Client**s" then do the next few steps.

_**To make the "download clients" work:**_
I used to have a few graphics problems with Ladbrokes but following the next steps changed that. So I suggest you follow the next steps carefully. :D

**6.** open IE6 and download the poker installer to your /home/username folder.
Make sure that "close this dialog box when download completes" is not checked.
When the download completes pres "Open" to start installing WITH IE6.

**7.** Let the install finish. You will have an desktop shortcut and everything should be fine. The Poker folders will not be installed in the ".wine/drive_c" folder. They will be installed in the "ie4linux/drive_c" folder.

_**If you need fonts**:_
Install fonts if needed. Ladbrokes does not seem to need it but other 32RedPoker and other clients from the "Microgaming Poker network" may need it. 
I play both with no extra fonts in Wine or ie4linux/IE6 though.

[COLOR="DimGray"]sudo aptitude install msttcorefonts
In Wine add ttf fonts to the windows fonts directory (for other applications).
In ie4linux/IE6 add ttf fonts to the windows fonts directory (for the installed poker clients).[/COLOR]

If I do not do it this way and just download the software and then install with the usual: "wine fileinstallername.exe" it seems the software will use the systems default browser (firefox). When loading the poker software graphics I then get a "gecko" error and I will then have to install Firefox 1.07 for Windows, activeX plugin for Firefox 1.07 and some runtime 6.0 DLL's to make it work. (this is the way I used to do it). 

**_Link to guide if you do not want to use IE6 (ie4linux):_**
[http://mormanski.net/](http://mormanski.net/)
Beware that the "Instant play" versions do not work with this guide as they need IE.
Like mentioned, I had a few graphical issues with that guide too.

I hope this will help some gambling loving Linux users out there.

Regards wxnker

---

