---
title: "Totally new, and not sure where to begin."
date: 2008-10-11
forum: New to Ubuntu
---

### Post by jfinner1 on 2008-10-11
Hello! My name is Jessyca, and I'm brand new to the whole Linux scene. I downloaded and installed Ubuntu yesterday, and I've spent all day today reading tutorials and fiddling, but I'm still quite lost. I'm not sure what version of Ubuntu I'm running, and I don't know how to find out. I figured out how to change my desktop background, and part of a theme, but I can't figure out how to change my login screen, or the initial load screen, though I've seen others do it. And some of the desktop effects that I've seen look awesome, but I've no clue how to get them. I want to put my music back on my computer (it's all on USB right now) but I'm not sure what music play to use, or how to install/use one. I would also like to get the widgets (Screenlets?) that I see a lot of people using, but I've got no clue on that either. 
So far I've installed Wine, and I think I at least got that to work right, but it's only for the one program I'm still running that's windows based. Luckily I'm a Firefox fanatic, so the browser isn't new to me. Same thing with Pidgin. Gimp I've tried to use in the past and it confused me, but I guess I'll have to get used to it. 

I'm sorry this is so long, but I really don't even know where to begin, what I need to do first, or how to do any of it. If you could point me in the right direction, or give me a few tips, I tend to be a fast learner. Thanks in advance.

---

### Post by Louis de Broglie on 2008-10-11
[Multimedia]("http://ubuntuforums.org/showthread.php?t=766683")
[Desktop Effects]("http://ubuntuforums.org/showthread.php?t=809695")

You will need to become familiar with the command line to enjoy the full power of linux but gui will do for now. 

[Terminal Guide]("http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+aliases")

Just keep learning and let us know if you have any problem.

---

### Post by jerome1232 on 2008-10-11
Allright.

To find out what release of ubuntu you are using you can goto:

System->About Ubuntu

To change you login screen (aka gdm theme)

System->Administration->Login Window

By default Ubuntu uses Rhythmbox as it's default media player, It's one of my favorite.

Applications->Sound & Video->Rhythmbox

you can also install Amarak, banshee, or vlc from the repos all great players. (Applications->Add/Remove...)

As far as widg-a-whos-it's go I hate them; but Screenlets and gdesklets are both programs you can use, I think you'll have to use the more advanced program installer synaptic.

System->Administration->Synaptic; search for screenlets and/or gdesklets and you should find it.

hope this helps

---

### Post by eternalnewbee on 2008-10-11
Let's start with your system information.
Go to Main Menu > SystemTools > Sysinfo.
If you don't have it, go to Main menu >ADD/Remove...
and in the search bar type: sysinfo, tick the program and apply

---

### Post by eternalnewbee on 2008-10-11
Let's start with your system information.
Go to Main Menu > SystemTools > Sysinfo.
If you don't have it, go to Main menu >ADD/Remove...
and in the search bar type: sysinfo, tick the program and apply

---

### Post by Louis de Broglie on 2008-10-11
If you are totally new in linux,  then I will recommend not to tinker with compiz for now. You might screw up things :lolflag:

---

### Post by aeiah on 2008-10-11
for the desktop effects, im assuming you're referring to compiz. you'll need graphics card drivers. if you have intel onboard graphics there's no need to worry, they'll all be there ready. if you have an nvidia or ati graphics card, you'll have to install them. its mostly painless. just go to system > administration > restricted drivers manager. you'll figure out the rest.

if you have a graphics card thats very very new i suggest you look into whether it'll work or not. linux can have a few problems if your card is only a few months old.

once thats sorted you should be able to enable desktop effects through system > preferences > desktop effects (or whatever its called)


what windows program are you trying to get working through wine, and what does it do? there will probably be something that'll do the job that's native to linux

---

### Post by soho2014 on 2008-10-11
]If you check: System > Administration > System Monitor  it will tell you what version of Ubuntu that you are using, amoung other things.:guitar:

---

### Post by Jackelope on 2008-10-11
Hi Jessyca, welcome to the Ubuntu community! I'm sure if you've gotten this far, you'll have no trouble getting things set up and running smoothly. Generally you'll get a better response to questions if there's only one per post, but I'll try to answer some of the basics for you. 

You can find the version of Ubuntu you're running by typing "gnome-system-monitor" (without quotes) into a terminal. A window will pop up, and the tab on the far left will have your edition number, such as 'Release 8.04,' which is the current one. The terminal is under "Accessories" on your menu if you can't find it. Most questions in the forums will be solved by terminal commands, not because you cant use a graphical interface, but because its faster and less error prone to just copy and paste commands. 

Changing the login screen can be done by going to your menu, then system > adminsitration > login window. The tab called 'local' will let you change the login theme. You can get more login themes on websites like gnome-look.org. Try looking for GDM themes. GDM stands for gnome display manager, and you'll find plenty of them. Just drag and drop one you've downloaded into the local window and you'll see it in the list. 

The fancy effects you see are from a program called compiz. You can enable it by going to your menu, then system > preferences > appearance. There should be a tab on the far right called 'visual effects.' click on it, and there should be several options for graphics effects. If these don't work, just look for help with compiz on the forums and you can trouble shoot any problems. Also, you'll need some kind of minimal graphics card to run compiz well.

Rhythmbox is the default music player in Ubuntu, and its a lot like itunes. Just try playing an mp3 and it should come up, asking about downloading the right codecs. Once the codecs are downloaded, mp3's should play fine. there are lots of other players if you don't like Rhythmbox. And lots of comparison threads can be found on the forums pointing out the best ones.

Screenlets can be downloaded from synaptic package manager, which is where you can download all the other softwarea as well. Just search for 'screenlets' and you should find a package to install. Right click on it and select mark for installation, then click apply.  

I hope that helps some. I tried to keep things simple but if you have any questions there are much more detailed posts all over the forums. Best of luck with it. :)

---

### Post by fidamehran on 2008-10-12
This is a very good place to for some elementary information:
["http://www.psychocats.net/ubuntu/index"]("http://www.psychocats.net/ubuntu/index")

---

### Post by hyper_ch on 2008-10-12
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by jfinner1 on 2008-10-12
Wow, I wasn't expecting so many responses so soon. Thanks everyone! I've been making slow progress, and your comments have helped a lot! I've got a lot more reading and fiddling to do, and I'm sure I'll be back with a few more questions. Thanks again for all your help so far!

---

### Post by bodhi.zazen on 2008-10-12
This is also a good place to start :

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by m_ad on 2008-10-12
In terms of customizing your desktop/etc.. I just found this in the Tutorials/tips section which is very good.

[HOWTO: Customize Ubuntu A-Z]("http://ubuntuforums.org/showthread.php?t=856190")

---

### Post by sayems on 2008-10-12
Some of the things you can do after installing ubuntu on your machine .

1.Putting your repositories in order
***************************************
$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

1.Installing Multimedia codecs for GStreamer
*********************************************
sudo apt-get install faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install w32codecs

sudo apt-get install build-essential

3.Avant Window Navigator
**************************
echo "deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list

echo "deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk

4.Installing MPlayer with all codecs and dvd playing support
*************************************************************
sudo apt-get install mplayer

sudo apt-get install w32codecs

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot

sudo /usr/share/doc/libdvdread3/install-css.sh

5.RealPlayer
************
[http://www.real.com/linux/](http://www.real.com/linux/)

chmod +x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin

6.Flash and Java Support
************************
sudo apt-get install flashplugin-nonfree libflashsupport

sudo apt-get install mozilla-plugin-gnash

sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin

7.Installing Microsoft fonts package
*************************************
sudo apt-get install msttcorefonts

sudo fc-cache

8.Adobe Reader
**************
sudo apt-get install acroread

9.Installing VLC Player
***********************
sudo apt-get install vlc

10.Ubuntu Tweak
***************
[http://www.getdeb.net/app/Ubuntu+Tweak](http://www.getdeb.net/app/Ubuntu+Tweak)

11.Strata Human 1.0
*******************
[https://addons.mozilla.org/en-US/firefox/addon/8105](https://addons.mozilla.org/en-US/firefox/addon/8105)

12.Midnight Commander
*********************
sudo apt-get install mc

13.Figlet
*********
$ sudo apt-get install figlet

14.Startup Manager
******************
sudo apt-get install startupmanager

15.GParted
**********
sudo apt-get install gparted

16.NumlockX
***********
sudo apt-get install gparted


17.Hamster
**********
sudo apt-get install hamster-applet


18.Free Disk Space from APT’s Cache
***********************************
sudo apt-get autoclean

19.StackSwitch and Wallpaper Plugins with Compiz 0.7.6
******************************************************
sudo apt-get install stackswitch

20.How to Install Cursor Themes
*******************************
[http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/](http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/)

21.p7zip Adds Built-In 7-Zip Tools to Ubuntu
********************************************
sudo apt-get install p7zip

22.Convert Red Hat/Fedora Packages for Ubuntu/Debian Installation
*****************************************************************
$sudo alien -k name-of-rpm-file.rpm

23.Global Menu
**************
[http://www.downloadsquad.com/2008/02/21/get-mac-style-menus-on-ubuntu-with-global-menu/](http://www.downloadsquad.com/2008/02/21/get-mac-style-menus-on-ubuntu-with-global-menu/)

24.Enable DVD Playback in Ubuntu in Two Commands
*************************************************
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

25.Howto install gnome-do in Ubuntu Hardy
*****************************************
[http://www.ubuntugeek.com/howto-install-gnome-do-in-ubuntu-hardy-and-gutsy.html](http://www.ubuntugeek.com/howto-install-gnome-do-in-ubuntu-hardy-and-gutsy.html)

29.Turn Your Ubuntu Hardy to Mac OSX Leopard
*******************************************************
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

30.Install Google Gadgets for Linux on Ubuntu
*********************************************
[http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/](http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/)

31.(Optional) btnx Customizes a Multi-Button Mouse for Linux
************************************************************
[http://lifehacker.com/384698/btnx-customizes-a-multi+button-mouse-for-linux](http://lifehacker.com/384698/btnx-customizes-a-multi+button-mouse-for-linux)

32.Watch YouTube Clips Inside GNOME's Built-In Movie Player
*****************************************************
[http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/](http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/)

33.Custom Compiz Effects in Ubuntu 8.04
*****************************************
[http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/)

34.(Optional) Use an OS X-Style Global Menu in Ubuntu
***************************************************
[http://lifehacker.com/359571/use-an-os-x+style-global-menu-in-ubuntu](http://lifehacker.com/359571/use-an-os-x+style-global-menu-in-ubuntu)

35.Toggle Desktop Effects with Compiz-Switch
*********************************************
[http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/](http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/)

36.Rip DVDs in Linux the (Semi-)Easy Way
**************************************
[http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php](http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php)

37.Hide Partition Icons on GNOME Desktops
**************************************
[http://lifehacker.com/software/linux-tip/hide-partition-icons-on-gnome-desktops-316179.php](http://lifehacker.com/software/linux-tip/hide-partition-icons-on-gnome-desktops-316179.php)

38.Share a Firefox Profile Between Ubuntu and Windows
********************************************
[http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/](http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/)

39.Banshee Media Player
***************************
[http://banshee-project.org/download/](http://banshee-project.org/download/)

40.Gnome-Do
*************
[http://do.davebsd.com/](http://do.davebsd.com/)

41.Ubuntu System Panel
*********************
[http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)

1.Slab (Start Menu)
*******************
[https://wiki.ubuntu.com/Slab](https://wiki.ubuntu.com/Slab)

42.Getdeb.net


43.Playdeb - The Gaming Repository for Ubuntu
*******************************************
[http://tombuntu.com/index.php/2007/10/22/the-apturl-protocol-handler-in-ubuntu-710/](http://tombuntu.com/index.php/2007/10/22/the-apturl-protocol-handler-in-ubuntu-710/)

44.Hamster Time Tracking for GNOME
*******************************
[http://tombuntu.com/index.php/2008/08/08/hamster-time-tracking-for-gnome/](http://tombuntu.com/index.php/2008/08/08/hamster-time-tracking-for-gnome/)

45.Replace the System Beep with a Compiz Effect
**********************************************
[http://tombuntu.com/index.php/2008/08/04/replace-the-system-beep-with-a-compiz-effect/](http://tombuntu.com/index.php/2008/08/04/replace-the-system-beep-with-a-compiz-effect/)

46.Free Disk Space from APT’s Cache
**********************************
[http://tombuntu.com/index.php/2008/08/01/free-disk-space-from-apts-cache/](http://tombuntu.com/index.php/2008/08/01/free-disk-space-from-apts-cache/)

47.Install Three Experimental Compiz Plugins
******************************************
[http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/](http://tombuntu.com/index.php/2008/07/31/install-three-experimental-compiz-plugins/)

48.Launchy Application Launcher Released for Linux
*********************************************
[http://tombuntu.com/index.php/2008/07/29/launchy-application-launcher-released-for-linux/](http://tombuntu.com/index.php/2008/07/29/launchy-application-launcher-released-for-linux/)

49.Upgrade to the Latest Compiz Fusion Release
********************************************
[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/)

50.StackSwitch and Wallpaper Plugins with Compiz 0.7.6
******************************************************
[http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/](http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/)

51.Guake Drop-Down Terminal for GNOME
**************************************
[http://tombuntu.com/index.php/2008/07/24/guake-drop-down-terminal-for-gnome/](http://tombuntu.com/index.php/2008/07/24/guake-drop-down-terminal-for-gnome/)

52.Install Google Gadgets for Linux on Ubuntu
*********************************************
[http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/](http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/)

53.How to Install Cursor Themes
***********************************
[http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/](http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/)

54.Enable Commercial DVD Playback in Ubuntu
*********************************************
[http://tombuntu.com/index.php/2008/05/13/enable-commercial-dvd-playback-in-ubuntu/](http://tombuntu.com/index.php/2008/05/13/enable-commercial-dvd-playback-in-ubuntu/)

55.Install Extra GNOME Themes
*************************************
[http://tombuntu.com/index.php/2008/04/29/install-extra-gnome-themes/](http://tombuntu.com/index.php/2008/04/29/install-extra-gnome-themes/)

56.Workaround for Pink Shadows with Compiz
**********************************************
sudo ln -sf /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so

57.Vista Basic By drvdw (Desktop Themes)
*******************************************
[http://art.gnome.org/themes/metacity/1337](http://art.gnome.org/themes/metacity/1337)

58.Aurora by memo_mapc (Backgrounds/Wallpaper)
************************************************
[http://art.gnome.org/backgrounds/abstract/2519](http://art.gnome.org/backgrounds/abstract/2519)

59.OSX (GNOME Icon)
*******************
[http://www.gnome-look.org/content/show.php/OSX?content=31618](http://www.gnome-look.org/content/show.php/OSX?content=31618)

60.GNOME-colors (GNOME Icon Theme)
**********************************
[http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562](http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562)

1.Show the Computer, Home, and Trash desktop icons in GNOME
***********************************************************
Alt+F2: gconf-editor
Choose apps->nautilus->desktop.
Tick the box beside computer_icon_visible, home_icon_visible, and trash_icon_visible. The changes take effect immediately.

1.KDE4 Oxygenstyle update
****************************
[http://kims-area.com/?q=node/63](http://kims-area.com/?q=node/63)
Download KDE4 Oxygen GTK theme .DEB

1.KDE Oxygenstyle Wallpaper
**************************
[http://pinheiro-kde.blogspot.com/](http://pinheiro-kde.blogspot.com/)

1.Change Gnome Panel Text Color
*******************************
$ gedit ~/.gtkrc-2.0
style "panel"
{
fg[NORMAL] = "#c6d8e1" #<--edit for panel font color
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"

# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#2ef60c" #yellow "#ffffff"
# base[PRELIGHT] = "#f60c22" #dark red "#EFEFEF"
# base[ACTIVE] = "#3c06ff" #blue "#D0D0D0"
base[SELECTED] = "#000000" #"#DAB566"
# base[INSENSITIVE] = "#d8d0b2" #biege "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Applet*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

1.Tweak Firefox 3 full screen mode
**********************************
[http://mozillalinks.org/wp/2008/06/tweak-firefox-3-full-screen-mode/](http://mozillalinks.org/wp/2008/06/tweak-firefox-3-full-screen-mode/)

1.Ubuntu Cheat Sheet
*********************
[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

1.A Day Without X
*****************
[http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)

1.More terminal programs you should be using … like a pro
*********************************************************
[http://kmandla.wordpress.com/2007/05/17/more-terminal-programs-you-should-be-using-like-a-pro/](http://kmandla.wordpress.com/2007/05/17/more-terminal-programs-you-should-be-using-like-a-pro/)

1.Paytube: YouTube video converter for Ubuntu Linux
*************************************************
[http://www.getdeb.net/release/3057](http://www.getdeb.net/release/3057)

1.Ultamatix: Install 101 Applications in One click including Games,codecs,applications
***********************************************************************************
[http://www.ubuntugeek.com/ultamatix-install-101-applications-in-one-click-including-gamescodecsapplications.html](http://www.ubuntugeek.com/ultamatix-install-101-applications-in-one-click-including-gamescodecsapplications.html)
Use the Synaptic Package Manager

1.Youtube-dl - Download videos from youtube in Ubuntu
*******************************************************
[http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html#more-556](http://www.ubuntugeek.com/howto-download-videos-from-youtube-in-ubuntu.html#more-556)


1.Ubuntu System Panel Setting
******************************

USP Bottom Text [Start]

Application Width - 230
Application Height - 500

Shortcut Height - 352
Shortcut Width - 180

System Height - 130
System Width - 200

1.Use a Screensaver as Desktop Wallpaper
*****************************************
[http://lifehacker.com/software/linux-tip/use-a-screensaver-as-desktop-wallpaper-299410.php](http://lifehacker.com/software/linux-tip/use-a-screensaver-as-desktop-wallpaper-299410.php)

1.Animated Wallpaper with Compiz Fusion on Ubuntu
[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

1.Fix for firefox crashes on flash contents when using libflashsupport in hardy
**********************************************
[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

1.The other Firefox 3 themes
******************************
[http://mozillalinks.org/wp/2008/07/the-other-firefox-3-themes/](http://mozillalinks.org/wp/2008/07/the-other-firefox-3-themes/)

Install VLC media player 0.9.2 in Ubuntu
******************************************
[http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

Customize Ubuntu A-Z
*********************
[http://ubuntuforums.org/showthread.php?t=856190&highlight=panel+background](http://ubuntuforums.org/showthread.php?t=856190&highlight=panel+background)

8 Ways to Maintain a Clean, Lean Ubuntu Machine
************************************************
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/)

---

