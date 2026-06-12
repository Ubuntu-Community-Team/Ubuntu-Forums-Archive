---
title: "Gettings Updates for Software That Are Not Installed"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by toady2 on 2013-09-02
I keep getting updates for firefox even though I don't have it installed. One of the recent updates I received was a language pack. I received more in the past, but I don't remember what they were sorry. Can someone explain why I get updates for a software that is not installed? Thank :)

*EDIT*
Sorry I forgot to mention that i'm using Lubuntu.

---

### Post by novice_penguin on 2013-09-02
It sounds like the program files were not "purged" correctly.

---

### Post by UltimateCat on 2013-09-02
Hi! ;)

By default Ubuntu comes with the Firefox browser.

Also, your sources.list is where all of the updates operate from so that's why those updates are showing up-
On my system the sources list is in this path /etc/apt/sources list
If you want to view your sources list to see all the repositories you can use the terminal and run:
```
cat /etc/apt/sources.list

```
The http:// address's that are in your sources list is where the updates come from.
You can either remove that line in your sources list (the one with the Mozilla address) or you can just comment out that entire argument with the (#) in
front of the exact line it's self.

But to edit your sources list you will have to use Nano, Gedit or whatever your favorite text editor is.
[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

[https://projects.gnome.org/gedit/](https://projects.gnome.org/gedit/)
[http://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/](http://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/)

HTH
Ultimatecat

---

### Post by Impavidus on 2013-09-03
Maybe you uninstalled firefox, but kept its dependendies. Running```
sudo apt-get --purge autoremove
```may work.

---

### Post by ian-weisser on 2013-09-03
> **toady2 said:**
> I keep getting updates for firefox even though I don't have it installed.

You probably do have some element of Firefox installed.
Uninstalled packages do not receive updates.

How, exactly, did you remove Firefox?

Please open a terminal, try the following command, and post the complete output (including error messages) here:
```
sudo apt-get autoremove firefox
```

---

### Post by sandyd on 2013-09-03
> **toady2 said:**
> I keep getting updates for firefox even though I don't have it installed. One of the recent updates I received was a language pack. I received more in the past, but I don't remember what they were sorry. Can someone explain why I get updates for a software that is not installed? Thank :)
If you are talking about language-pack-en/base pulling in the firefox-locale-en dependency, it is not the full firefox - just the firefox english locales

---

### Post by vasa1 on 2013-09-03
Run [FONT=Courier New]sudo apt-get purge firefox-locale-en[/FONT]

---

### Post by toady2 on 2013-09-03
I actually never installed firefox. I never installed any browser. I am using Lubuntu so I'm just using chromium, as that came already installed.

---

### Post by ian-weisser on 2013-09-03
The firefox-locale-en package is Recommended by language-pack-en-base, which is included in Lubuntu.
You can safely remove it if you wish. Be aware that the package manager may (helpfully) reinstall it for you in the future.

```
$ apt-cache rdepends firefox-locale-en
firefox-locale-en
Reverse Depends:
  firefox-testsuite
  language-pack-en-base


$ apt-cache show language-pack-en-base
[...]
Recommends: firefox-locale-en
[...]
Description-en: translations for language English
 Translation data for all supported packages for:
 English
 .
 This package provides the bulk of translation data and is updated
 only seldom. language-pack-en provides frequent
 translation updates, so you should install this as well.
[...]
Task: ubuntu-live, ubuntu-usb-live, kubuntu-live, kubuntu-active-live, kubuntu-active-live, edubuntu-live, edubuntu-dvd-live, edubuntu-usb-live, xubuntu-live, lubuntu-live, ubuntustudio-dvd-live

```

---

### Post by vasa1 on 2013-09-03
> **toady2 said:**
> I actually never installed firefox. I never installed any browser. I am using Lubuntu so I'm just using chromium, as that came already installed.
Same here. IMO, it's just a hangover from most other Ubuntu Flavors having Firefox as the default. The Lubuntu devs perhaps forgot to address this issue which otherwise is normally taken care of during installation and cleanup.
No big deal. Just delete it.

If you want more, assuming you've done a clean install of Lubuntu 13.04  ... I don't know what happens with an "upgrade".

Go to [FONT=Courier New]/var/log/apt[/FONT]. Copy the oldest [FONT=Courier New]history.log.n.gz[/FONT] you see (where n is an integer) to your desktop, uncompress it, open the log with Leafpad and search for "firefox-locale-en". You'll see that the installation process installs it but doesn't purge it later on when several other things, including other locales for Firefox are purged.

---

### Post by vasa1 on 2013-09-21
Just to add something to this "unsolved" thread: [https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000386.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000386.html) and follow-ups including [Should not recommend firefox-locale]("https://bugs.launchpad.net/ubuntu/+source/language-pack-fr-base/+bug/820056")

---

