---
title: "Checklist: How I've set my (almost) perfect Ubuntu desktop!"
date: 2006-09-26
forum: Outdated Tutorials &amp; Tips
---

### Post by wladston on 2006-09-26
I'm a recently switched from windows to ubuntu person ... These was the steps I had to do in order to get my (amost) perfect desktop enviroment:

This is a work in progress - as I find out more things that will leave my desktop better, I'll try to add here.

1. Thought about how would the two disks I had be partitioned. Turned out that I've used about 25% for a windows partition, 25% for the linux partition, 25% for the home directory partition, 25% for a media(musics, clips, etc.) partition, and some for swap. The second disk would include more swap and a miscelaneous partition.


2. Put the Ubuntu CD in, and clicked install. :) Windows partition is ntfs, linux and home are ext3, misc and media are vfat, for easy sharing with windows. Install time is the perfect time to set your home partition to be mounted in /home!! Mounting a special /home partition will allow you to change/reinstall your operating system without touthing your personal files/settings.


3. Configure gedit to use 10pt fonts, not 12pt ( on GEdit: Edit->Preferences, Font). Take your time to change other things you like there. Gedit is MUCH more than window's notepad.


4. Enable NTP time adjusting (adjust time and date-> mark the checkbox). I've suggested to let this on by default : [https://features.launchpad.net/distros/ubuntu/+spec/ntp-on-by-default](https://features.launchpad.net/distros/ubuntu/+spec/ntp-on-by-default)


5. Got to System->Preferences->About, and fill the forms. Anyways, looks like this REALLY does not matter for anything: [http://www.ubuntuforums.org/archive/index.php/t-84998.html](http://www.ubuntuforums.org/archive/index.php/t-84998.html)


6. Go to System-> Preferences->keyboard shortcuts. Seting special keys on the keyboard was never that easy! There was a little bug, wich I've reported here : [https://launchpad.net/distros/ubuntu/+bug/60336](https://launchpad.net/distros/ubuntu/+bug/60336) . Also, be aware of this bug : [https://launchpad.net/distros/ubuntu/+source/control-center/+bug/8146](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/8146)


7. Now, System->Preferences->Power Management. Put screen to sleep after 15 mins, and set sleep button action to hybernate. Hibernation works great, except when the system is on the hibernation process, no feedback is given to the user, and there are some strange screens on the process ([https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/41137](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/41137) and [https://features.launchpad.net/distros/ubuntu/+spec/usplash-hibernation](https://features.launchpad.net/distros/ubuntu/+spec/usplash-hibernation))


8. Go to gnome-look.org and get some prety backgournds and themes (I use a bliss/vista looking set). It's really great to have your system looking exactly the way you like more. I use this [http://www.gnome-look.org/content/show.php?content=35645](http://www.gnome-look.org/content/show.php?content=35645) and this [http://www.gnome-look.org/content/show.php?content=35643](http://www.gnome-look.org/content/show.php?content=35643) and some others as wallpaper. On the themes side, I use Human for controls, Vistabut([http://www.gnome-look.org/content/show.php?content=32227](http://www.gnome-look.org/content/show.php?content=32227)) for window border. I like Gion-blu ([http://www.gnome-look.org/content/show.php?content=37689)](http://www.gnome-look.org/content/show.php?content=37689)), but I'm using the default Human iconset, that is more complete. Later I'll maybe edit VistaBut ... i think it lacks a bit of contrast...
Don't forget to get GDM themes too - I'm using this one : [http://www.gnome-look.org/content/show.php?content=18178](http://www.gnome-look.org/content/show.php?content=18178) . To install a GDM theme, go to System->Administration->Login Window - and drop the tar theme there.


8. Install a gmail notifyer program. The best option seems to be "checkgmail" - but it's not addable via "Add/Remove..", nor Synaptic nor apt get. I  had to download a .deb package in order to install it ([https://launchpad.net/distros/ubuntu/+ticket/1810](https://launchpad.net/distros/ubuntu/+ticket/1810)) . Also suggesting to include this on the available list of ubuntu apps.


9. Configure Gaim and it's extensions. You'll need this to setup google talk/jabber : [http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073). And to tune up gaim (remove the buddy list from the taskbar) you'll need to get "Extended preferences" plugin (sudo apt-get install gaim-extendedprefs). To toast-like pop-up notifications, get the "Guifications" plugin (sudo apt-get install gaim-guifications). Go to Tools->Preferences and tune it up!


10. Get a pretty theme for gaim and guifications. For guifications, i use this one [http://www.gnome-look.org/content/show.php?content=40005](http://www.gnome-look.org/content/show.php?content=40005) . To install a guification theme, drag-drop them to the guification theme configurations (find it on gaim's preferences, guification plugin).
For the main gaim theme, I like this : [http://www.gnome-look.org/content/show.php?content=40047](http://www.gnome-look.org/content/show.php?content=40047) . Putting themes on gaim is a non-obvious operation - it involves having to "sudo nautilus" to copy files to /usr/share/pixmaps/gaim .
For the smileys, i use tango-gaim-emotes ([http://www.gnome-look.org/content/show.php?content=43901)](http://www.gnome-look.org/content/show.php?content=43901)). These ones you can install via the Gaim configuration.


11. Install/configure amule. Amule is not as good as clean as emule - but it's ok ...


12. Install/enable aditional languages, System->administration->language support (example: portuguese) (my request to support installing more than one language at instalation [https://features.launchpad.net/distros/ubuntu/+spec/multi-language-instalation](https://features.launchpad.net/distros/ubuntu/+spec/multi-language-instalation))

13. Install the printer. System->administration->printing (Spec to do this automatically : [https://features.launchpad.net/distros/ubuntu/+spec/automatic-printer-conf/](https://features.launchpad.net/distros/ubuntu/+spec/automatic-printer-conf/))


14. Install samba to share files with my brother's computer. Just left click a folder and choose to share. Had to diasble autentication ( [http://ubuntuforums.org/showthread.php?p=1489425#post1489425](http://ubuntuforums.org/showthread.php?p=1489425#post1489425) ). Also, enable printer sharing printer sharing [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) (had to edit config, files). Suggestion to make this on a easyer way : [https://features.launchpad.net/distros/ubuntu/+spec/printer-sharing](https://features.launchpad.net/distros/ubuntu/+spec/printer-sharing)


15. Install JRE. Had to hit the advanced tab(synaptic) to find JDK. (Anyone knows why ???)


16. Install gstreamer (mp3) plugins. I would stick with OGG, but my digital media player is limited to the mp3/wma format.


17. Set checkgmail, gaim and amule to start automaticaly (system, preferences, session)


18. Install flash player for firefox (did not work with me : [https://launchpad.net/distros/ubuntu/+ticket/1804](https://launchpad.net/distros/ubuntu/+ticket/1804)) and ([https://launchpad.net/distros/ubuntu/+bug/60895](https://launchpad.net/distros/ubuntu/+bug/60895))


19. Install firefox extentions : googletoolbar, stumbleupon, etc.


20. Had issues with nautilus and “executable text files” - nautilus was misdetecting my txts files as "executables text files". ( [https://launchpad.net/distros/ubuntu/+ticket/1888](https://launchpad.net/distros/ubuntu/+ticket/1888) )


21. Install gFTP - everyone needs an FTP client. Not as user-friendly as cristalFTP (for example, when you press a key is does not go to the folder starting with the key... it's not easy to reach your desktop... pressing f5 does not refresh your local dir...you can't drag and drop files to send ...)

22. Install p7zip - the best archiver system is not available by default - and I had to go on synaptic to get it!! ([https://features.launchpad.net/distros/ubuntu/+spec/dpkg-7zip/](https://features.launchpad.net/distros/ubuntu/+spec/dpkg-7zip/))

23. Finally take some time to read the complete user guide :)

---

### Post by Kapt nemo on 2006-10-02
ok just out of curiosity, how did you install stumble Upon?? I've been trying to install it for the last hour... please help..

---

### Post by wladston on 2006-10-02
to install stumbleupon, just go here :
[https://addons.mozilla.org/firefox/138/](https://addons.mozilla.org/firefox/138/)

and click the "Install now" link! Then you'll be asked by firefox to confirm the instalation.

---

### Post by Kapt nemo on 2006-10-02
weird... I tried for like 20 min... and kept getting errors....

---

### Post by quik77 on 2006-10-02
what was the error message? I know I'm on edgy atm and the default for it is fireFox bon echo 2.0, some of the firefox extenstions won't work in certain versions (had to get 1.5.07 again to get any web dev stuff done >.<)

---

### Post by kerry_s on 2006-10-02
#15. Should be sun-java5-jre and sun-java5-plugin

You've got to be specific, the reason is is because the regular jre has sound issues, specially on sites like runescape. The sun one is also more up to date.

For incompatiable firefox plugins you can use->
Nightly Tester Tools -> [http://users.blueprintit.co.uk/~dave/web/firefox/nightly/index.html](http://users.blueprintit.co.uk/~dave/web/firefox/nightly/index.html)

It can make most extensions compatiable in firefox you have to grab the one that matches your firefox though, the newst one(1.2) is for firefox2

---

### Post by Roman27 on 2006-10-02
As an alternative to item #4, you could simply add a command to:

```
ntpdate ntp_server
```

...somewhere.  I put my in the system crontab.  But I've heard of others placing it in rc.local to sync during the boot process.

I believe ntpdate is already installed by default.

**EDIT:** Actually, let me revise this.  Ubuntu is already programmed from the default install to automatically sync with ntp.ubuntu.com whenever a network interface is brought up.  That normally happens during the boot process.

You can see the script that does this at /etc/network/ifup.d/ntpdate.  You may adjust the timeserver to something other than ntp.ubuntu.com by editing /etc/default/ntpdate.

---

### Post by Frothy on 2006-10-03
I used gFTP for a couple weeks but found it too clunky & had issues with uploading large numbers of files. If you're already using FireFox, you may want to try [FireFTP]("https://addons.mozilla.org/firefox/684/") as an alternative.

---

### Post by Frothy on 2006-10-03
Dbl Post

---

### Post by Fire on 2006-10-03
Just so you know if you set up automatix this will help you download a lot of things your system needs to run.  Also Checkgmail is on there and it will install it for you.  Infact it will also correctly install flash and most if not all media codec.  It is a great software

[http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

---

### Post by Cynical on 2006-10-12
[quote=wladston]the best archiver system is not available by default[/quote]

You didnt have tar/bzip2 installed on your system?

---

### Post by BLTicklemonster on 2006-10-12
I have this sitting in my pm box where I have pmed these instructions so I will always be able to get to them:

[QUOTE=BLTicklemonster]Setting it all up

Formatting in XP: fat32 does not work on more than 32 gigs, so the windows partition will need to be less than 32 gigs.

First things first. 

Go to terminal and upgrade to kernel k7 and reboot to dapper kernel k7. It won’t want to boot to x server because it’s different now, but just log in and run envy again and ignore any errors.  Reboot.

Once you get to the desktop, chances are you will be prompted to do some upgrades. Ignore that, and immediately go and download Envy, the nvidia driver installer and install the nvidia card. [http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Now you are set up and ready to screw up your newest installation of Ubuntu. Proceed with random abandon.

Logitech mouse: [http://www.ubuntuforums.org/showthread.php?t=219894](http://www.ubuntuforums.org/showthread.php?t=219894)

Dapper Repos: [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

Automatix: [http://www.getautomatix.com/](http://www.getautomatix.com/)

Broadband tweak: [http://www.ubuntuforums.org/showthread.php?p=1470154#post1470154](http://www.ubuntuforums.org/showthread.php?p=1470154#post1470154)

UT: [http://ubuntuforums.org/showthread.php?t=74623](http://ubuntuforums.org/showthread.php?t=74623)

VMWare (use iso): [http://www.ubuntuforums.org/showthread.php?p=490521#post490521](http://www.ubuntuforums.org/showthread.php?p=490521#post490521)

Hotmail using Evo: [http://www.ubuntuforums.org/showthread.php?t=200408](http://www.ubuntuforums.org/showthread.php?t=200408)

Backup and restore: [http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

K9Copy for ripping dvds: [http://www.ubuntuforums.org/showthread.php?p=1471941#post1471941](http://www.ubuntuforums.org/showthread.php?p=1471941#post1471941)[/QUOTE]

---

### Post by wladston on 2006-10-14
> **Cynical said:**
> You didnt have tar/bzip2 installed on your system?
Well, on the 7zip site, they state that they have the greatest compression algorithm. Someone can google a page with reviews of tar/bzip2 and 7zip ?

---

### Post by drr422 on 2006-12-03
Wine is getting really good, it can run emule 0.47c, which is the latest, without a problem.  You should give it a try, i feel its better than amule.

---

