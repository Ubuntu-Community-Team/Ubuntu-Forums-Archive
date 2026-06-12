---
title: "E:Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.l"
date: 2015-09-25
forum: New to Ubuntu
---

### Post by wintry on 2015-09-25
What have I done!  New to Ubuntu.  I tried to install Spotify with the code they presented on their website for Linux users. Not only does  Spotify NOT work.... but I just tried to run software updater and got this message :

"Failed to load the package list
This is a serious problem. Try again later. If this problem appears again, please report an error to the developers."

Then under details it says:

"E:Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened."

Anybody have any idea what I did wrong/how to fix this?  Thanks for your help!

Wintry


ps I'm TOTALLY new to everything so speak slowly and use hand gestures :-)

---

### Post by ian-weisser on 2015-09-25
1) Please show us the entire contents of the file /etc/apt/sources.list.d/spotify.list
Copy the contents and paste into your reply. Please [use [code] tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").

2) Please link to those instructions so we can read them. 'the code they presented' could mean a lot of things.

---

### Post by wintry on 2015-09-25
Thank you for your swift reply.... I will use code tags.  How to I find  the contents of ```
/etc/apt/sources.list.d/spotify.list
``` ?

---

### Post by yancek on 2015-09-25
Open it in a text editor, gedit /etc/apt/sources.list.d/spotify.list

---

### Post by wintry on 2015-09-25
I feel really slow.... what's a text editor?  I entered it into cmd line and got this. ```
/etc/apt/sources.list.d/spotify.list
bash: /etc/apt/sources.list.d/spotify.list: Permission denied
```

---

### Post by ian-weisser on 2015-09-25
A text editor is like Notepad in Windows. No formatting, just text. Gedit is a common text editor in Ubuntu. There are others.
Try it again:
```
gedit /etc/apt/sources.list.d/spotify.list
```

You're not slow...you're moving from a Toyota to a Lamborghini. There's a lot of new stuff under the hood, and it's a lot more fun.

---

### Post by wintry on 2015-09-26
Aha!  Ok.  Thanks for that clarification.  And thank you SO much for being patient with me.  It really means a lot.

So, on my Lubuntu I have Leafpad.  So Instead of typing ```
gedit /etc/apt/sources.list.d/spotify.list
```  I typed in ```
leafpad /etc/apt/sources.list.d/spotify.list
```
and a leafpad window sprung up with the following information in the txt editor (i'm not putting this in code tags cause it wasn't code?)... 
sudo apt-get update
sudo apt-get install spotify-client

in the terminal it said this ```
 leafpad /etc/apt/sources.list.d/spotify.list
/usr/share/themes/Lubuntu-default/gtk-2.0/apps/thunar.rc:55: error: invalid string constant "thunar-statusbar", expected valid string constant
```
And 
re: 'the code they presented'  here's a link to it.
[https://www.spotify.com/ca-en/download/linux/](https://www.spotify.com/ca-en/download/linux/)

I guess I should also mention that I'm running Ubuntu 15.04... on an old Dell Inspiron 2200...  

Does any of this help?   Thanks again!

---

### Post by yancek on 2015-09-26
I'm not sure if I'm understanding your last post.  You seem to be saying that you see the lines in code below in that file.  If they are, they don't belong there so delete them.  Use sudo to prefix the command to open it with leafpad as you most likely need root privileges.  The error you posted in the initial post indicates "'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list ".  You should not need sudo in that file so if it is delete it.

> sudo apt-get update
sudo apt-get install spotify-client

The two commands above are to be run in a terminal to update your sources list and install spotify-client.

---

### Post by ian-weisser on 2015-09-26
> **wintry said:**
> (i'm not putting this in code tags cause it wasn't code?)... 
Code tags simply keep the formatting of the text file*.* Web browsers reformat text (you knew that), which is a hindrance when we want to see the original formatting of a text file. 
We know it's not code.
You shouldn't trust any *real* code you find on the internet anyway.
So Yes, please continue to use code tags for terminal output and error messages. It makes them easier to read.

> **wintry said:**
> /usr/share/themes/Lubuntu-default/gtk-2.0/apps/thunar.rc:55: error: invalid string constant "thunar-statusbar", expected valid string constant
That's not the content of the file we need to see.
That is an error message, Thunar is explaining to you why it can't open the file. Since I don't have the Thunar source code in front of me, I don't find it helpful.
Seemingly irrelevant to the Spotify problem.

Basically, it looks you have a Syntax Error in your Spotify source. You perhaps made a typo when you created it.
Based on your description, I have an idea what the typo is.
But you can't fix that typo until you can read (and edit) the file in a simple text editor. NOT in a Word Processor - the invisible characters added by a Word Processor will horribly mangle the file.
Open a terminal and try the 'nano' text editor instead of the 'leafpad' text editor. Nano is an even simpler.
```
nano /etc/apt/sources.list.d/spotify.list
```
Again, just copy-and-paste the entire contents of the file here, contained within code tags.


> **wintry said:**
>  re: 'the code they presented'  here's a link to it.
[https://www.spotify.com/ca-en/download/linux/](https://www.spotify.com/ca-en/download/linux/)
I guess I should also mention that I'm running Ubuntu 15.04... on an old Dell Inspiron 2200...  

Excellent information. That helps.

Ugh. Spotify asking you --a new, unskilled user-- to manually add repositories and keys using cryptic terminal voodoo is awful, just awful. For a paid product, it would be unprofessional and laughably unacceptable. Debian and Ubuntu have a dozen *free* ways to make software trivially easy to install for users like you (that's Ubuntu's *greatest strength*)...and Spotify didn't use them. Shame on them.

Nevertheless, it will probably work once you figure out how to open that file in a text editor so we can take a look at it.

---

### Post by wintry on 2015-09-26
Ok.  Thanks for the clarification re: code tags, and also validating my concerns about the Spotify install process.  to be honest, I don't really even care that much about it.  If I could just delete all things re spotify and fix this that would work for me!  Up up up the learning curve I go!  

so I typed in ```

nano /etc/apt/sources.list.d/spotify.list
```

and this is what my terminal turned into...and I'm guessing this is STILL not the code you need to see...: ```



 GNU nano 2.2.6     File: /etc/apt/sources.list.d/spotify.list                 

sudo apt-get update
sudo apt-get install spotify-client

















               [ line 1/6 (16%), col 1/20 (5%), char 0/59 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell 
```

now what?

---

### Post by ian-weisser on 2015-09-26
> **wintry said:**
> ```

sudo apt-get update
sudo apt-get install spotify-client
```

That's the contents of the file! Congratulations.

If you have nano open, close it.
Reopen the file using sudo (you must use sudo because root, not you, owns that file)
```
sudo nano /etc/apt/sources.list.d/spotify.list
```

Line 1 is currently:
```
sudo apt-get update
```
Replace line 1 with
```
deb http://repository.spotify.com stable non-free
```

Line 2 is currently:
```
sudo apt-get install spotify-client
```
Delete all text on line 2.

Save your changes with ^O (CTRL+ lowercase-letter-o). It will prompt you to change the filename. Don't change the filename. Simply hit <ENTER>
After saving, exit with ^X (CTRL + lowercase-x)

Now that your source is fixed, and nano is closed, you can do
```
sudo apt-get update
sudo apt-get install spotify-client
```
The first command updates your package database from all sources, including your newly-fixed source. You use sudo because root (not you) owns the package database.
The second command installs the Spotify client, now that it's in the package database. You use sudo because only admins are allowed to install software.

If that works, then you have successfully installed Spotify!

---

### Post by wintry on 2015-09-26
Terrific!  I got further than ever before!  Here's what happened ```
sudo apt-get update
Ign http://archive.ubuntu.com vivid InRelease                                  
Get:1 http://repository.spotify.com stable InRelease [3,300 B]
Ign http://repository.spotify.com stable InRelease       
Get:2 http://archive.ubuntu.com vivid Release.gpg [933 B]
Get:3 http://archive.ubuntu.com vivid Release [217 kB]
Get:4 http://archive.ubuntu.com vivid/universe i386 Packages [6,486 kB]        
Get:5 http://repository.spotify.com stable/non-free i386 Packages [1,204 B]    
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:6 http://archive.ubuntu.com vivid/main i386 Packages [1,361 kB]            
Get:7 http://archive.ubuntu.com vivid/main Translation-en [793 kB]             
Get:8 http://archive.ubuntu.com vivid/universe Translation-en [4,456 kB]       
Fetched 13.3 MB in 1min 16s (174 kB/s)                                         
Reading package lists... Done
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13B00F1FD2C19886
```

then I said what the hey and continued with the 
```
sudo apt-get install spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 spotify-client : Depends: libqt4-dbus (>= 4.5.0) but it is not going to be installed
                  Recommends: libavcodec53 but it is not installable or
                              libavcodec52 but it is not installable or
                              libavcodec-extra-53 but it is not installable or
                              libavcodec-extra-52 but it is not installable
                  Recommends: libavformat53 but it is not installable or
                              libavformat52 but it is not installable or
                              libavformat-extra-53 but it is not installable or
                              libavformat-extra-52 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

So at this point, do I just give up on Spotify?  I don't like holding broken packages... it's just depressing :-)  OH I would also like to mention that my software updater is working beautifully now.  Thanks!

---

### Post by mc4man on 2015-09-26
It seems their stable packages are quite out of date as far as the Recommends:, 14.04 uses libavcodec54, 15.04 has libavcodec56. So whether spotify can work ok either without Libav(FFmpeg) or with newer libs support no clue.
However those are just Recommends:, not totally needed for install.

First try to install libqt4-dbus itself 
```
sudo apt-get install libqt4-dbus
```

(- there is at least one newer spotify .deb, seems suited to 14.04, not so much for 15.04 - (can be manually downloaded & installed
[http://repository-origin.spotify.com/pool/non-free/s/spotify-client/](http://repository-origin.spotify.com/pool/non-free/s/spotify-client/)

---

### Post by wintry on 2015-09-26
So I just tried ```

sudo apt-get install libqt4-dbus 
```

and this is what came up: ```
sudo apt-get install libqt4-dbus
[sudo] password for wintry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-dbus : Depends: libqtdbus4 (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 is to be installed
               Depends: qdbus (= 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

It seems to me that they just haven't caught up to 15.04?  IS this true and should I just abandon this whole epic battle?

---

### Post by mc4man on 2015-09-26
I don't know Lubuntu but you need to open Software Sources & enable under Updates tab   both 'Security' & 'Updates'
Screen shows here in Ubuntu
Try in a terminal - 
```
software-properties-gtk
```
Then check that both are enabled as in screenshot, reload your sources & try to install spotify again

---

### Post by wintry on 2015-09-26
> **mc4man said:**
> I don't know Lubuntu but you need to open Software Sources & enable under Updates tab   both 'Security' & 'Updates'
Screen shows here in Ubuntu
Try in a terminal - 
```
software-properties-gtk
```
Then check that both are enabled as in screenshot, reload your sources & try to install spotify again

Yes I did this.  Now am getting same message as before. ```
E:Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.
```

so I followed the steps listed before (see earlier posts) by Ian Weisser, changed the text of ```

sudo nano /etc/apt/sources.list.d/spotify.list
``` then tried ```
sudo apt-get update
sudo apt-get install spotify-client
```
and this is what I came up with. ```
sudo apt-get update
Get:1 http://repository.spotify.com stable InRelease [3,300 B]                 
Ign http://repository.spotify.com stable InRelease                             
Ign http://archive.ubuntu.com vivid InRelease                                  
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex      
Ign http://archive.ubuntu.com vivid-updates InRelease                          
Hit http://archive.ubuntu.com vivid Release.gpg                                
Get:2 http://archive.ubuntu.com vivid-updates Release.gpg [933 B]              
Ign http://security.ubuntu.com vivid-security InRelease                        
Hit http://archive.ubuntu.com vivid Release                                    
Get:3 http://security.ubuntu.com vivid-security Release.gpg [933 B]            
Get:4 http://archive.ubuntu.com vivid-updates Release [63.5 kB]                
Get:5 http://security.ubuntu.com vivid-security Release [63.5 kB]        
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:6 http://security.ubuntu.com vivid-security/universe i386 Packages [56.8 kB]
Hit http://archive.ubuntu.com vivid/universe i386 Packages                     
Hit http://archive.ubuntu.com vivid/main i386 Packages                         
Hit http://archive.ubuntu.com vivid/main Translation-en                        
Get:7 http://security.ubuntu.com vivid-security/main i386 Packages [115 kB]    
Hit http://archive.ubuntu.com vivid/universe Translation-en                    
Get:8 http://archive.ubuntu.com vivid-updates/universe i386 Packages [109 kB]  
Get:9 http://security.ubuntu.com vivid-security/main Translation-en [61.3 kB]  
Get:10 http://security.ubuntu.com vivid-security/universe Translation-en [35.1 kB]
Get:11 http://archive.ubuntu.com vivid-updates/main i386 Packages [196 kB]     
Get:12 http://archive.ubuntu.com vivid-updates/main Translation-en [97.8 kB]   
Get:13 http://archive.ubuntu.com vivid-updates/universe Translation-en [64.1 kB]
Fetched 867 kB in 43s (19.8 kB/s)                                              
Reading package lists... Done
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13B00F1FD2C19886
 
sudo apt-get install spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools account-plugin-ubuntuone accountsservice-ubuntu-schemas
  accountsservice-ubuntu-touch-schemas address-book-service apg
  apparmor-easyprof-ubuntu cheese-common click click-apparmor cups-pk-helper
  dbus-property-service folks-common geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-gnomebluetooth-1.0 gir1.2-json-1.0
  gir1.2-signon-1.0 gkbd-capplet gnome-control-center-shared-data gnome-menus
  gnome-session-bin gnome-settings-daemon-schemas gnustep-back-common
  gnustep-back0.24 gnustep-back0.24-cairo gnustep-base-common
  gnustep-base-runtime gnustep-common gnustep-gui-common gnustep-gui-runtime
  gsettings-ubuntu-schemas gstreamer1.0-clutter history-service hud
  imagemagick-common indicator-bluetooth indicator-datetime indicator-keyboard
  indicator-network indicator-power indicator-sound libaccounts-qt5-1
  libandroid-properties1 libao-common libao4 libboost-iostreams1.55.0
  libboost-locale1.55.0 libboost-log1.55.0 libboost-program-options1.55.0
  libboost-regex1.55.0 libboost-serialization1.55.0 libboost-thread1.55.0
  libcapnp-0.4.0 libcheese-gtk23 libcheese7 libclick-0.4-0
  libclutter-gst-2.0-0 libcolumbus1 libcolumbus1-common libconnectivity-qt1
  libcontent-hub0 libdbus-cpp4 libdbusmenu-qt5 libdouble-conversion1
  libfcitx-config4 libfcitx-gclient0 libfcitx-utils0 libfftw3-double3
  libflite1 libfolks-eds25 libfolks25 libgee-0.8-2 libgee2 libgflags2
  libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgnustep-base1.24
  libgnustep-gui0.24 libgoogle-glog0 libgsettings-qt1 libhardware2
  libhistoryservice0 libhud2 libhybris libhybris-common1 libhybris-utils
  libjsoncpp0 liblqr-1-0 liblttng-ust-ctl2 liblttng-ust0 libmagickcore-6.q16-2
  libmedia1 libmediascanner-2.0-3 libmirplatform6 libmirserver30
  libmission-control-plugins0 libnet-cpp1 libobjc4 libofono-qt1
  libonline-accounts-client1 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libpay2 libpgm-5.1-0 libphonenumber6 libpocketsphinx1
  libpoppler-qt5-1 libprocess-cpp2 libqdjango-db0 libqgsttools-p1
  libqmenumodel0 libqofono-qt5-0 libqt5concurrent5 libqt5contacts5
  libqt5feedback5 libqt5keychain0 libqt5location5 libqt5location5-plugins
  libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediaquick-p5
  libqt5multimediawidgets5 libqt5network5 libqt5opengl5 libqt5organizer5
  libqt5positioning5 libqt5positioning5-plugins libqt5printsupport5 libqt5qml5
  libqt5quick5 libqt5quickparticles5 libqt5script5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5svg5 libqt5systeminfo5 libqt5test5 libqt5versit5
  libqt5versitorganizer5 libqt5webkit5 libqt5websockets5 libqt5widgets5
  libqt5xml5 libqt5xmlpatterns5 libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libsodium13 libsphinxbase1 libsystemsettings1
  libtelepathy-qt5-0 libthumbnailer0 libtrust-store1 libu1db-qt5-3
  libubuntu-app-launch2 libubuntu-application-api2
  libubuntu-download-manager-client0 libubuntu-download-manager-common0
  libubuntu-location-service2 libubuntu-platform-hardware-api2
  libubuntuoneauth-2.0-0 libudm-common0 libudm-priv-common0
  libunity-action-qt1 libunity-api0 libunity-control-center1 libunity-scopes3
  libunity-settings-daemon1 libunityvoice1 libunwind8 liburcu2
  liburl-dispatcher1 libusermetricsinput1 libusermetricsoutput1 libwacom-bin
  libwacom-common libwacom2 libwhoopsie-preferences0 libzeitgeist-2.0-0
  libzmq3 libzmqpp3 linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic
  linux-image-3.19.0-15-generic linux-image-extra-3.19.0-15-generic
  mediascanner2.0 mir-platform-graphics-mesa1 mknfonts.tool mousetweaks
  obexd-client ofono oxideqt-codecs packagekit-tools pay-service powerd
  python-zeitgeist python3-apparmor-click python3-click python3-gnupg
  python3-xdg qmenumodel-qml qml-module-qt-labs-folderlistmodel
  qml-module-qt-labs-settings qml-module-qt-websockets qml-module-qtfeedback
  qml-module-qtgraphicaleffects qml-module-qtlocation qml-module-qtmultimedia
  qml-module-qtorganizer qml-module-qtpositioning qml-module-qtquick-layouts
  qml-module-qtquick-localstorage qml-module-qtquick-particles2
  qml-module-qtquick-window2 qml-module-qtquick-xmllistmodel
  qml-module-qtquick2 qml-module-qtsensors qml-module-qtsysteminfo
  qml-module-ubuntu-connectivity qml-module-ubuntu-onlineaccounts
  qml-module-ubuntu-onlineaccounts-client qmlscene qtcontact5-galera
  qtdeclarative5-accounts-plugin qtdeclarative5-folderlistmodel-plugin
  qtdeclarative5-gsettings1.0 qtdeclarative5-localstorage-plugin
  qtdeclarative5-ofono0.2 qtdeclarative5-online-accounts-client0.1
  qtdeclarative5-particles-plugin qtdeclarative5-poppler1.0
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtmir-plugin
  qtdeclarative5-qtorganizer-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-systeminfo-plugin qtdeclarative5-u1db1.0
  qtdeclarative5-ubuntu-content1 qtdeclarative5-ubuntu-download-manager0.1
  qtdeclarative5-ubuntu-mediascanner0.1 qtdeclarative5-ubuntu-push-plugin
  qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-syncmonitor0.1
  qtdeclarative5-ubuntu-telephony-phonenumber0.1
  qtdeclarative5-ubuntu-telephony0.1 qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-ubuntu-web-plugin
  qtdeclarative5-ubuntu-web-plugin-assets qtdeclarative5-ubuntuone1.0
  qtdeclarative5-unity-action-plugin qtdeclarative5-unity-notifications-plugin
  qtdeclarative5-usermetrics0.1 qtdeclarative5-window-plugin
  qtdeclarative5-xmllistmodel-plugin qtmir-desktop session-migration
  signon-plugin-oauth2 signon-plugin-password signon-ui signon-ui-service
  signon-ui-x11 signond sphinx-voxforge-hmm-en sphinx-voxforge-lm-en sqlite3
  suru-icon-theme system-image-common system-image-dbus
  telepathy-mission-control-5 telepathy-ofono telephony-service
  thumbnailer-common thumbnailer-service tone-generator ubuntu-app-launch
  ubuntu-app-launch-tools ubuntu-application-api2-test ubuntu-download-manager
  ubuntu-html5-container ubuntu-html5-ui-toolkit ubuntu-keyboard-data
  ubuntu-mobile-icons ubuntu-sdk-libs ubuntu-sounds ubuntu-system-service
  ubuntu-system-settings ubuntu-system-settings-online-accounts
  ubuntu-touch-sounds ubuntu-ui-toolkit-theme ubuntuone-client-data
  ubuntuone-credentials-common unity-asset-pool unity-control-center
  unity-plugin-scopes unity-schemas unity-scope-click
  unity-scope-click-departmentsdb unity-scope-mediascanner2 unity-scope-scopes
  unity-settings-daemon unity-voice-service unity-webapps-qml unity8
  unity8-common unity8-private urfkill usermetricsservice whoopsie-preferences
  zeitgeist zeitgeist-core zeitgeist-datahub
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgconf2-4 libnspr4-0d libqt4-dbus libssl0.9.8 qdbus
Recommended packages:
  libavcodec53 libavcodec52 libavcodec-extra-53 libavcodec-extra-52
  libavformat53 libavformat52 libavformat-extra-53 libavformat-extra-52
The following NEW packages will be installed:
  libgconf2-4 libnspr4-0d libqt4-dbus libssl0.9.8 qdbus spotify-client
0 upgraded, 6 newly installed, 0 to remove and 19 not upgraded.
Need to get 42.5 MB of archives.
After this operation, 103 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  spotify-client
Install these packages without verification? [y/N] y
Get:1 http://archive.ubuntu.com/ubuntu/ vivid/universe libssl0.9.8 i386 0.9.8o-7ubuntu4 [688 kB]
Get:2 http://security.ubuntu.com/ubuntu/ vivid-security/main qdbus i386 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 [29.6 kB]
Get:3 http://repository.spotify.com/ stable/non-free spotify-client i386 1:0.9.4.183.g644e24e.428-1 [41.7 MB]
Get:4 http://security.ubuntu.com/ubuntu/ vivid-security/main libqt4-dbus i386 4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1 [6,516 B]
Get:5 http://archive.ubuntu.com/ubuntu/ vivid/main libgconf2-4 i386 3.2.6-3ubuntu1 [2,108 B]
Get:6 http://archive.ubuntu.com/ubuntu/ vivid/universe libnspr4-0d i386 2:4.10.7-1ubuntu1 [6,630 B]
Fetched 42.5 MB in 2min 58s (238 kB/s)                                         
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list
debconf: apt-extracttemplates failed: No such file or directory
Selecting previously unselected package libssl0.9.8:i386.
(Reading database ... 411177 files and directories currently installed.)
Preparing to unpack .../libssl0.9.8_0.9.8o-7ubuntu4_i386.deb ...
Unpacking libssl0.9.8:i386 (0.9.8o-7ubuntu4) ...
Selecting previously unselected package libgconf2-4:i386.
Preparing to unpack .../libgconf2-4_3.2.6-3ubuntu1_i386.deb ...
Unpacking libgconf2-4:i386 (3.2.6-3ubuntu1) ...
Selecting previously unselected package libnspr4-0d:i386.
Preparing to unpack .../libnspr4-0d_2%3a4.10.7-1ubuntu1_i386.deb ...
Unpacking libnspr4-0d:i386 (2:4.10.7-1ubuntu1) ...
Selecting previously unselected package qdbus.
Preparing to unpack .../qdbus_4%3a4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1_i386.deb ...
Unpacking qdbus (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1) ...
Selecting previously unselected package libqt4-dbus:i386.
Preparing to unpack .../libqt4-dbus_4%3a4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1_i386.deb ...
Unpacking libqt4-dbus:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1) ...
Selecting previously unselected package spotify-client.
Preparing to unpack .../spotify-client_1%3a0.9.4.183.g644e24e.428-1_i386.deb ...
Unpacking spotify-client (1:0.9.4.183.g644e24e.428-1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up libssl0.9.8:i386 (0.9.8o-7ubuntu4) ...
Setting up libgconf2-4:i386 (3.2.6-3ubuntu1) ...
Setting up libnspr4-0d:i386 (2:4.10.7-1ubuntu1) ...
Setting up qdbus (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1) ...
Setting up libqt4-dbus:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6.1) ...
Setting up spotify-client (1:0.9.4.183.g644e24e.428-1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...


``` Now I have the spotify icon under my sound/video area but spotify won't open by clicking on it...
Y'all have been SO helpful.  I've learned so much here!  just a little further perhaps?  Thanks a bazillion times over for the patience and great answers given here!  WOOT.

---

