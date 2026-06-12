---
title: "Opera Browser on Ubuntu?"
date: 2017-02-11
forum: New to Ubuntu
---

### Post by Daveski17 on 2017-02-11
Has anyone ran Opera (Blink) on Ubuntu? If so have you encountered any problems? Thanks.

---

### Post by oldrocker99 on 2017-02-11
You'll have to install Opera this way:[https://www.ubuntuupdates.org/ppa/opera](https://www.ubuntuupdates.org/ppa/opera).

I have had no problems running Opera, personally.

---

### Post by Frogs Hair on 2017-02-11
Currently running beta to test built in adblocking and vpn/proxy. No problems running video so far.

---

### Post by oldrocker99 on 2017-02-11
You'll have to install Opera this way:[https://www.ubuntuupdates.org/ppa/opera](https://www.ubuntuupdates.org/ppa/opera).

I have had no problems running Opera, personally.

---

### Post by leunam12 on 2017-02-11
Alternatively you can go to their website, download the installer and double-click it. You will be asked if you want to update Opera when you update your system.

---

### Post by Daveski17 on 2017-02-11
> **oldrocker99 said:**
> You'll have to install Opera this way:[https://www.ubuntuupdates.org/ppa/opera](https://www.ubuntuupdates.org/ppa/opera).

I have had no problems running Opera, personally.
OK thanks. What's the Terminal command for its uninstallation should I choose to uninstall it?

> **leunam12 said:**
> Alternatively you can go to their website, download the installer and double-click it. You will be asked if you want to update Opera when you update your system.

Thanks, that's probably the way I'll do it.

> **Frogs Hair said:**
> Currently running beta to test built in adblocking and vpn/proxy. No problems running video so far.

OK, thanks.

---

### Post by Daveski17 on 2017-02-12
Would <sudo apt purge opera> uninstall the Debian package downloaded from the Opera site?

Thanks

---

### Post by howefield on 2017-02-12
> **Daveski17 said:**
> Would <sudo apt purge opera> uninstall the Debian package downloaded from the Opera site?

Thanks

Yes it would, install it with apt and apt will be able to remove it.

---

### Post by Daveski17 on 2017-02-12
> **howefield said:**
> Yes it would, install it with apt and apt will be able to remove it.

OK thanks. So, if I install it from here:

[IMG]http://i386.photobucket.com/albums/oo307/Davebucket17/opera_zps04t6axrt.jpg[/IMG]

I should be able to uninstall it with <sudo apt purge opera>.



I installed Chrome again recently. I uninstalled it a while back with the Terminal after running it for some time. Although it appears to be here in the repo now. Can I uninstall Chrome from the Software Centre if I wished to uninstall it again? And, will Opera be able to be uninstalled directly from the Software Centre?

Thanks

---

### Post by howefield on 2017-02-13
The software Centre is a front end for apt.. so again, yes. Just use the remove button that you can see on the screenshot to remove the application. Chrome will still be in the repository as it put the repository information there when you installed it, as Opera will.

Just as a fyi, if you are on 16.04 or later you can use the command line to install Opera..

```
wget ftp://ftp.opera.com/pub/opera/desktop/43.0.2442.806/linux/opera-stable_43.0.2442.806_amd64.deb -P ~/Downloads
```
to download the .deb package to your downloads folder and.
```
sudo apt install ~/Downloads/43.0.2442.806/linux/opera-stable_43.0.2442.806_amd64.deb
```
to install it.

It will offer to add the repository to your sources in order that it can update itself along with the rest of your system. 

PS. Please use the paperclip icon to attach your images or downsize them to about 800x600 as a courtesy to those using lower bandwidth connections to browse the forum.

---

### Post by Daveski17 on 2017-02-13
Thanks for the reply. Sorry about the jpeg size.

---

### Post by bm0127 on 2017-02-16
Have any of you all succeeded in installing Flash on Opera?  It's working on Firefox for me, but not Opera.  I'm running Lubuntu 16.04.2.  Thanks in advance!

---

### Post by #&amp;thj^% on 2017-02-16
> **bm0127 said:**
> Have any of you all succeeded in installing Flash on Opera?  It's working on Firefox for me, but not Opera.  I'm running Lubuntu 16.04.2.  Thanks in advance!

If I'm not mistaken for Opera you will need pepperflashplugin-nonfree package
See post #3 by mc4man here:[https://ubuntuforums.org/showthread.php?t=2280567](https://ubuntuforums.org/showthread.php?t=2280567)

Ubuntu Wiki:[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by ubunticus on 2017-02-16
> **bm0127 said:**
> Have any of you all succeeded in installing Flash on Opera?

I believe running Flash is disabled in Opera by default. If you haven't enabled it go to settings>websites, scroll down to Flash and enable it.

---

### Post by bm0127 on 2017-02-16
> **1fallen said:**
> If I'm not mistaken for Opera you will need pepperflashplugin-nonfree package
See post #3 by mc4man here:[https://ubuntuforums.org/showthread.php?t=2280567](https://ubuntuforums.org/showthread.php?t=2280567)

Ubuntu Wiki:[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

I tried this, no luck.  I think that Ubuntu Wiki page might be outdated.  This is what Opera suggested: [http://www.opera.com/docs/linux/plugins/install/](http://www.opera.com/docs/linux/plugins/install/)  But this also looks outdated, as it says at the top of the page it's meant for version 11.

> **ubunticus said:**
> I believe running Flash is disabled in Opera by default. If you haven't enabled it go to settings>websites, scroll down to Flash and enable it.

I tried this and had no luck.  To test, I've been going to this page: [https://www.whatismybrowser.com/detect/is-flash-installed](https://www.whatismybrowser.com/detect/is-flash-installed)  Does this work for you?

---

### Post by ubunticus on 2017-02-16
Did you install flash running this in the terminal:
sudo apt-get install adobe-flashplugin ?

---

### Post by deadflowr on 2017-02-16
To install flash for opera.
Open the program Software and Updates 
go to Other Software and enable Canonical Partners
then reload and exit (reload should be the option on exiting anyway...)
then install the package adobe-flashplugin, not flash-plugin-installer, or peperflashplugin-non-free.

The adobe-flashplugin package contains both the npapi-plugin for firefox and the ppapi plugin for chrome and chrome-based browsers.
(Of which Opera is a chrome-based browser)

Unfortunately, if on 16.04 or newer(16.10, really) you need to install it through either the command line or using a secondary package manager such as synaptic.
(Since the Ubuntu Software program does not list non-gui applications like flash.)

So in a terminal run
```
sudo apt install adobe-flashplugin
```
and flash should install and become available on Opera.

Hope it helps

---

### Post by bm0127 on 2017-02-16
> **deadflowr said:**
> To install flash for opera.
Open the program Software and Updates 
go to Other Software and enable Canonical Partners
then reload and exit (reload should be the option on exiting anyway...)
then install the package adobe-flashplugin, not flash-plugin-installer, or peperflashplugin-non-free.

The adobe-flashplugin package contains both the npapi-plugin for firefox and the ppapi plugin for chrome and chrome-based browsers.
(Of which Opera is a chrome-based browser)

Unfortunately, if on 16.04 or newer(16.10, really) you need to install it through either the command line or using a secondary package manager such as synaptic.
(Since the Ubuntu Software program does not list non-gui applications like flash.)

So in a terminal run
```
sudo apt install adobe-flashplugin
```
and flash should install and become available on Opera.

Hope it helps

I uninstalled my flash installation and then installed via command line like you suggested, and everything seems to be working perfectly now.  I believe I originally installed flash via lubuntu-restricted-extras, so perhaps something went wrong there.

Thanks for the help!

---

