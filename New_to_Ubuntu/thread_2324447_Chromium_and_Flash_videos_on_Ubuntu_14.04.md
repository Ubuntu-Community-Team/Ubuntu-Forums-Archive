---
title: "Chromium and Flash videos on Ubuntu 14.04"
date: 2016-05-13
forum: New to Ubuntu
---

### Post by rdb3 on 2016-05-13
I installed Chromium today from Terminal..

sudo apt-get install chromium browser

It installed ok.  I can see videos on youtube fine.

However, when I click on a video from another source, like a newspaper, I get:

"Couldn't load plugin."

I've searched but have not been successful in resolving this.

Any thoughts on this one?

Thanks!

---

### Post by Dennis N on 2016-05-13
The sites that don't work probably use the adobe flashplugin. Chromium needs a different flash plugin than Firefox uses to view flash media. My guess is that you don't have it installed. So,

Run the "Software and Updates" package, and on the "other software" tab, check "Canonical Partners". See the attached screenshot. Close, and reload the software lists.

Then install the package **adobe-flashplugin**.

If you had installed "flashplugin-installer", it will be removed, but that is ok since adobe-flashplugin will also supply the flashplugin for firefox.

---

### Post by rdb3 on 2016-05-14
> **Dennis N said:**
> The sites that don't work probably use the adobe flashplugin. Chromium needs a different flash plugin than Firefox uses to view flash media. My guess is that you don't have it installed. So,

Run the "Software and Updates" package, and on the "other software" tab, check "Canonical Partners". See the attached screenshot. Close, and reload the software lists.

Then install the package **adobe-flashplugin**.

If you had installed "flashplugin-installer", it will be removed, but that is ok since adobe-flashplugin will also supply the flashplugin for firefox.

Thanks for your response.

I did what you suggested, but unfortunately it did not fix the situation.

On those videos, I still get the msg, "We're sorry    you need to update your Flash Player."

Youtube videos work fine, and Firefox does not have this problem, it's good too.  It's only affecting Chromium.

---

### Post by Dennis N on 2016-05-14
The message "We're sorry you need to update your Flash Player" implies the latest version is not being used.

I suggest you start Chromium and go to this test page:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

If flash is enabled, the bouncing cube animation will show, and in the box "version information" it will show the version number of flash player you currently have installed. I just visited (14 May 2016), and the current version is 21.0.0.242

---

### Post by rdb3 on 2016-05-14
No animation showing.  Instead I got "The plugin is not supported."

I have uninstalled and re-installed Chromium and get the same thing.

---

### Post by Dennis N on 2016-05-14
***"The plugin is not supported"...***

I haven't seen a response exactly like that - it's a genuine Adobe plugin. Apparently a plugin is detected, or you would get nothing if it is not.  (If you have no plugin, it gives no message in the version box. Just checked that).

You can check your installed version with dpkg-query and post the result. Here is the first part of my output when I run it:

```
dmn@Roxanne:~$ dpkg-query -s adobe-flashplugin
Package: adobe-flashplugin
Status: install ok installed
Priority: optional
Section: partner/web
Installed-Size: 37272
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Architecture: amd64
Version: 1:20160512.1-0ubuntu0.14.04.1


```Since you have 14.04, the version shown on the last line should be the same as shown. My updates are current.

---

### Post by kevdog on 2016-05-14
Do you install chromium-pepperflash?  


$ apt-cache search chromium
liboxideqt-qmlplugin - Web browser engine for Qt (QML plugin)
liboxideqtcore-dev - Web browser engine for Qt (development files for core library)
liboxideqtcore0 - Web browser engine for Qt (core library and components)
liboxideqtquick-dev - Web browser engine for Qt (development files for QtQuick library)
liboxideqtquick0 - Web browser engine for Qt (QtQuick library)
mozc-data - Mozc input method - data files
mozc-server - Server of the Mozc input method
mozc-utils-gui - GUI utilities of the Mozc input method
oxideqt-codecs - Web browser engine for Qt (codecs)
unity-scope-chromiumbookmarks - Chromium bookmarks scope for Unity
cgpt - GPT manipulation tool with support for Chromium OS extensions
chromium-browser - Chromium web browser, open-source version of Chrome
chromium-browser-dbg - chromium-browser debug symbols
chromium-browser-l10n - chromium-browser language packages
chromium-bsu - fast paced, arcade-style, scrolling space shooter
chromium-bsu-data - data pack for the Chromium B.S.U. game
chromium-chromedriver - WebDriver driver for the Chromium Browser
chromium-chromedriver-dbg - chromium-chromedriver debug symbols
chromium-codecs-ffmpeg - Free ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-dbg - chromium-codecs-ffmpeg debug symbols
chromium-codecs-ffmpeg-extra - Extra ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-extra-dbg - chromium-codecs-ffmpeg-extra debug symbols
chromium-lwn4chrome - Chromium extension for making LWN.net slightly easier to read
emacs-mozc - Mozc for Emacs
emacs-mozc-bin - Helper module for emacs-mozc
ibus-mozc - Mozc engine for IBus - Client of the Mozc input method
libv8-3.14-dbg - V8 JavaScript engine - debugging symbols
libv8-3.14-dev - V8 JavaScript engine - development files for 3.14 branch
libv8-3.14.5 - V8 JavaScript engine - runtime library
libv8-dev - V8 JavaScript engine - development files for latest branch
ninja-build - small build system closest in spirit to Make
ninja-build-doc - documentation for ninja-build
oxideqt-codecs-extra - Web browser engine for Qt (codecs)
python-pyftpdlib - Python FTP server library
python3-pyftpdlib - Python FTP server library
unity-chromium-extension - Unity WebApp extension for the chromium browser
browser-plugin-freshplayer-pepperflash - PPAPI-host NPAPI-plugin adapter for pepperflash
flashplugin-installer - Adobe Flash Player plugin installer
pepperflashplugin-nonfree - Pepper Flash Player - browser plugin

I believe it is the pepperflashplugin-non-free package.

---

### Post by rdb3 on 2016-05-14
> **Dennis N said:**
> ***"The plugin is not supported"...***

I haven't seen a response exactly like that - it's a genuine Adobe plugin. Apparently a plugin is detected, or you would get nothing if it is not.  (If you have no plugin, it gives no message in the version box. Just checked that).

You can check your installed version with dpkg-query and post the result. Here is the first part of my output when I run it:

```
dmn@Roxanne:~$ dpkg-query -s adobe-flashplugin
Package: adobe-flashplugin
Status: install ok installed
Priority: optional
Section: partner/web
Installed-Size: 37272
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Architecture: amd64
Version: 1:20160512.1-0ubuntu0.14.04.1


```Since you have 14.04, the version shown on the last line should be the same as shown. My updates are current.

```

max@max-GN571AA-ABA-SR5210NX:~$  dpkg-query -s adobe-flashplugin
dpkg-query: package 'adobe-flashplugin' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

I've tried several times to install it.  At least I thought I had.  ????

---

### Post by rdb3 on 2016-05-14
> **kevdog said:**
> Do you install chromium-pepperflash?  


$ apt-cache search chromium

browser-plugin-freshplayer-pepperflash - PPAPI-host NPAPI-plugin adapter for pepperflash
flashplugin-installer - Adobe Flash Player plugin installer
pepperflashplugin-nonfree - Pepper Flash Player - browser plugin

I believe it is the pepperflashplugin-non-free package.

```

max@max-GN571AA-ABA-SR5210NX:~$  apt-cache search chromium
unity-scope-chromiumbookmarks - Chromium bookmarks scope for Unity
webaccounts-extension-common - Ubuntu Online Accounts browser extension - common files
flashplugin-installer - Adobe Flash Player plugin installer
pepperflashplugin-nonfree - Pepper Flash Player - browser plugin
cgpt - GPT manipulation tool with support for Chromium OS extensions
chromium-browser-dbg - chromium-browser debug symbols
chromium-bsu - fast paced, arcade-style, scrolling space shooter
chromium-bsu-data - data pack for the Chromium B.S.U. game
chromium-chromedriver - WebDriver driver for the Chromium Browser
chromium-chromedriver-dbg - chromium-chromedriver debug symbols
chromium-codecs-ffmpeg-dbg - chromium-codecs-ffmpeg debug symbols
chromium-codecs-ffmpeg-extra-dbg - chromium-codecs-ffmpeg-extra debug symbols
cloudprint - Server for Google Cloud Print
emacs-mozc - Mozc for Emacs
emacs-mozc-bin - Helper module for emacs-mozc
gecko-mediaplayer - Multimedia plug-in for Gecko browsers
ibus-mozc - Mozc engine for IBus - Client of the Mozc input method
libv8-3.14-dbg - V8 JavaScript engine - debugging symbols
libv8-3.14-dev - V8 JavaScript engine - development files for 3.14 branch
libv8-3.14.5 - V8 JavaScript engine - runtime library
libv8-dev - V8 JavaScript engine - development files for latest branch
mozc-data - Mozc input method - data files
mozc-server - Server of the Mozc input method
mozc-utils-gui - GUI utilities of the Mozc input method
ninja-build - small build system closest in spirit to Make
ninja-build-doc - documentation for ninja-build
oxideqmlscene - Web browser engine library for Qt (QML application runner)
python-pyftpdlib - Python FTP server library
uim-mozc - Mozc engine for uim - Client of the Mozc input method
unity-chromium-extension - Unity WebApp extension for the chromium browser
webaccounts-chromium-extension - Ubuntu Online Accounts extension for chromium
liboxideqt-qmlplugin - Web browser engine for Qt (QML plugin)
liboxideqtcore-dev - Web browser engine for Qt (development files for core library)
liboxideqtcore0 - Web browser engine for Qt (core library and components)
liboxideqtquick-dev - Web browser engine for Qt (development files for QtQuick library)
liboxideqtquick0 - Web browser engine for Qt (QtQuick library)
oxideqt-chromedriver - Web browser engine for Qt (transitional package)
oxideqt-codecs - Web browser engine for Qt (codecs)
oxideqt-codecs-dbg - Web browser engine for Qt (Debug symbols)
oxideqt-codecs-extra - Web browser engine for Qt (codecs)
oxideqt-codecs-extra-dbg - Web browser engine for Qt (Debug symbols)
oxideqt-dbg - Web browser engine for Qt (Debug symbols)
chromium-browser - Chromium web browser, open-source version of Chrome
chromium-browser-l10n - chromium-browser language packages
chromium-codecs-ffmpeg - Free ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-extra - Extra ffmpeg codecs for the Chromium Browser
adobe-flashplugin - Adobe Flash Player plugin
slimjet - Fast, smart and powerful browser based on Blink
 
```

I'll try to install pepperflashplugin next.  Thanks.

---

### Post by rdb3 on 2016-05-14
When I tried to install pepperflash, I got this...

```

max@max-GN571AA-ABA-SR5210NX:~$ sudo apt-get install browser-plugin-freshplayer-pepperflash
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package browser-plugin-freshplayer-pepperflash
```

Doesn't work on my 32-bit.

---

### Post by rdb3 on 2016-05-14
Installed PepperFlashPlayer-browserplugin  from the Ubuntu Software Center but it's still not showing up.

---

### Post by Dennis N on 2016-05-14
> **rdb3 said:**
> ```

max@max-GN571AA-ABA-SR5210NX:~$  dpkg-query -s adobe-flashplugin
dpkg-query: package 'adobe-flashplugin' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

I've tried several times to install it.  At least I thought I had.  ????

Clearly, it's not installed. I suggest you reread the steps given in Post #2. Did you enable the "Canonical Partners" repository in "Software and Updates" by checking the box as shown in the image in post #2? After you check the box, when you close the window you get a popup message that says "Repositories Changed..." You need to click the "Reload" button on that message.

After the reload completes, as a check if you sources now include the new package, you can run

[FONT=Courier New]**apt-cache policy adobe-flashplugin**[/FONT]

NOT available:

```
dmn@Sydney:~$ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: (none)
  Candidate: (none)
  Version table:

```
IS available:

```
dmn@Sydney:~$ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: (none)
  Candidate: 1:20160512.1-0ubuntu0.14.04.1
  Version table:
     1:20160512.1-0ubuntu0.14.04.1 0
        500 http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages
```


If available, then you should be able to install.

Also, there is this about pepperflashplugin-nonfree:

> As of 2015-05, the old "pepperflashplugin-nonfree" is deprecated in favor of an official, maintained, one-step package called adobe-flashplugin, which works for Firefox and Chromium and derivatives...

source: [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)


---

### Post by Dennis N on 2016-05-14
> **rdb3 said:**
> Installed PepperFlashPlayer-browserplugin  from the Ubuntu Software Center but it's still not showing up.

If you have a 32-bit Chromium browser, then this package does not work anymore.

---

### Post by rdb3 on 2016-05-14
> **Dennis N said:**
> Clearly, it's not installed. I suggest you reread the steps given in Post #2. Did you enable the "Canonical Partners" repository in "Software and Updates" by checking the box as shown in the image in post #2? After you check the box, when you close the window you get a popup message that says "Repositories Changed..." You need to click the "Reload" button on that message.

After the reload completes, as a check if you sources now include the new package, you can run

apt-cache policy adobe-flashplugin
I did this again and here's what I got..

```

max@max-GN571AA-ABA-SR5210NX:~$ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: (none)
  Candidate: 1:20160512.1-0ubuntu0.14.04.1
  Version table:
     1:20160512.1-0ubuntu0.14.04.1 0
        500 http://archive.canonical.com/ubuntu/ trusty/partner i386 Packages
```

Then I went to the Software Center, did the install of AdobeFlashPlugin, but it still did not work.
That's after giving it some time after re-starting Chromium.
At least, Firefox works fine.  I'm thinking I will have to settle for that. 
Thanks very much for all your help on this.

---

### Post by Dennis N on 2016-05-14
> Then I went to the Software Center, did the install of AdobeFlashPlugin, but it still did not work.

If you install from the Ubuntu Software Center in Ubuntu 14.04, then the package you want to install is named "Adobe Flash Player Plugin". I think from the quote above that you may have installed the package named "Adobe Flash Plugin" - this installs **flashplugin-installer 11.202.621ubuntu0.14.04.1** which is now only for Firefox, not for Chromium - I learned what it is from reading information found using the "More" button, then looking under "Version". _You need to install the exact package shown in the attached screenshot to get the Chromium-compatable flash plugin from Ubuntu Software Center_. Notice what I searched for in the search box.

Attached is a screenshot of the correct package to choose.

---

### Post by carl4926 on 2016-05-14
I think there is a PPA for the fresh plugin, and this will enable FF to use the pepper flash, it may support 32 bit.
Obviously some folk still use 32 bit
**ppa:itachi-san/freshplayerplugin**

---

### Post by rdb3 on 2016-05-15
> **Dennis N said:**
> If you install from the Ubuntu Software Center in Ubuntu 14.04, then the package you want to install is named "Adobe Flash Player Plugin". I think from the quote above that you may have installed the package named "Adobe Flash Plugin" - this installs **flashplugin-installer 11.202.621ubuntu0.14.04.1** which is now only for Firefox, not for Chromium - I learned what it is from reading information found using the "More" button, then looking under "Version". _You need to install the exact package shown in the attached screenshot to get the Chromium-compatable flash plugin from Ubuntu Software Center_. Notice what I searched for in the search box.

Attached is a screenshot of the correct package to choose.

Dennis,

That did it!! Works on this 32-bit machine.

In the Ubuntu Software Center, installed  "Adobe Flash Player Plugin."  It will show as...  Adobe-flashplugin.

 I checked the videos on a couple of news sources, and they are working.

Thank you so much for staying with this and taking me through it.

I did a "chrome plugins" and Schockwave flash is now showing.  It was not before.

```

 Adobe Flash Player- Version: 11.2.999.999Shockwave Flash 11.2 r999

[TABLE]
[TR]
[TD="class: plugin-details-label"]Name:[/TD]
[TD]Shockwave Flash[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Description:[/TD]
[TD]Shockwave Flash 11.2 r999[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Version:[/TD]
[TD]11.2.999.999[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Location:[/TD]
[TD]/usr/lib/adobe-flashplugin/libpepflashplayer.so[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Type:[/TD]
[TD]PPAPI (out-of-process)[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"][/TD]
[TD][Disable]("chrome://plugins/#")[/TD]
[/TR]
[/TABLE]


```

---

### Post by Dennis N on 2016-05-15
> **rdb3 said:**
> Dennis,

That did it!! Works on this 32-bit machine.



Persistence pays off. The Ubuntu Software Center names for these flash plugins are confusing. You have to look at the details to be sure what you are getting.

Beware: the **chrome://plugins** in Chromium doesn't correctly display the version you actually have installed. Mine shows 11.2.999.999 also, which is wrong. The best way to check the flash version installed is to go to the Adobe test page given in post #4. I think it is 21.0.0.242 at this time.

Since yours is now working on your 32-bit machine, it has to be good.

---

### Post by rdb3 on 2016-05-15
> **Dennis N said:**
> Persistence pays off. The Ubuntu Software Center names for these flash plugins are confusing. You have to look at the details to be sure what you are getting.

Beware: the **chrome://plugins** in Chromium doesn't correctly display the version you actually have installed. Mine shows 11.2.999.999 also, which is wrong. The best way to check the flash version installed is to go to the Adobe test page given in post #4. I think it is 21.0.0.242 at this time.

Since yours is now working on your 32-bit machine, it has to be good.

Good to know that.  I went to the Adobe site and I also have 21.0.0. 242 installed.

Thanks again!!

---

### Post by Uwe_Riisenberg on 2016-05-15
Thank you!

As a user of 32-bit Estobuntu 14.04 I did not find Adobe Flash Player plug-in in Lubuntu Software Centre, but it was at Synaptic Package Manager and I installed Adobe Flash Player 21.0.0.242 successfully over there according to the test at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/), even though Chromium 49.0.2623.108 for Ubuntu 14.04 shows at chrome://plugins/ that Adobe Flash Player 11.2.999.999 is installed.

---

### Post by Daveski17 on 2016-05-15
I'm not able to get Pepperflash to work in Chromium either. I've heard Google are ending support for flash and changing completely to HTML5 this year.

---

### Post by rdb3 on 2016-05-16
> **Daveski17 said:**
> I'm not able to get Pepperflash to work in Chromium either. I've heard Google are ending support for flash and changing completely to HTML5 this year.

Are you 32 bits too?

Adobe is also heading towards HTML5.

[http://fortune.com/2015/12/01/adobe-animator-flash/](http://fortune.com/2015/12/01/adobe-animator-flash/)

---

### Post by Daveski17 on 2016-05-16
> **rdb3 said:**
> Are you 32 bits too?

Adobe is also heading towards HTML5.

[http://fortune.com/2015/12/01/adobe-animator-flash/](http://fortune.com/2015/12/01/adobe-animator-flash/)

No, x64. I've had the problem before but it usually seems to download Pepperflash eventually. I can always open Firefox I suppose. I use it more than Chromium anyway.

---

