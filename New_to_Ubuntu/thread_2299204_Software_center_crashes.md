---
title: "Software center crashes"
date: 2015-10-16
forum: New to Ubuntu
---

### Post by igorteuri on 2015-10-16
Hi guys! I'm a beginner using Ubuntu, then sorry if my question is too silly.

Everytime I try to open the software center, the window appear, but crashes and close. I tried to open by terminal, but the same error. Then I tried to reinstall it, but the error persists.

I don't know what to do. I've searched all over internet, and even in foruns in portuguese (I'm brazillian), but nothing. I was almost giving up in using ubuntu, but this will be my last try haha. I'll paste the log error bellow.

Thanks for reading! 

```
ryuke@uRyuke:~$ software-center
2015-09-19 14:46:49,130 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-09-19 14:46:50,135 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-09-19 14:46:50,141 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-09-19 14:46:50,238 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-09-19 14:46:51,107 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Argumento inv\xc3\xa1lido -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-09-19 14:46:51,109 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Argumento inv\xc3\xa1lido -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 68 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Falha de segmentação
ryuke@uRyuke:~$ /usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 20 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
```

---

### Post by Bucky Ball on 2015-10-16
Welcome and thanks for using code tags. :)

Which release are you using? What happens when you:

```
sudo apt-get update
```

... in a terminal? Post the output, please.

* Waaaaay too early to give up! Just a glitch. ;)

---

### Post by igorteuri on 2015-10-16
Thanks for the answer Bucky Ball !

Im using, Ubuntu 14.04 version.

Well, when I tried the code 'sudo apt-get update', it got this
> Lendo listas de pacotes... Pronto

Translating:
"Reading packages lists... Done

It seems that it updated as usual
Should I 'sudo apt-get upgrade' ?

---

### Post by v3.xx on 2015-10-16
Yes go ahead and upgrade.

Maybe try a different package manager

```
sudo apt-get install synaptic
```

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by igorteuri on 2015-10-16
Well, updated and upgraded. But the error continues. I can install apps only by terminal. That's not a huge problem, but it turns in to a honor issue to fix the software-center. 
I'll install synaptic anyway. 

After upgrading, heres what I got trying to run software-center

> ryuke@uRyuke:~$ software-center2015-10-16 15:46:54,186 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-10-16 15:46:57,528 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-10-16 15:46:57,549 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-10-16 15:46:57,747 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-10-16 15:46:59,848 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Argumento inv\xc3\xa1lido -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-10-16 15:46:59,849 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Argumento inv\xc3\xa1lido -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 74 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
2015-10-16 15:47:06,076 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'leadwerks\r\nleadwerks-indie'' not available
Falha de segmentação /*translating: segmentation fault*/
ryuke@uRyuke:~$ /usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 20 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)

---

### Post by v3.xx on 2015-10-16
> That's not a huge problem, but it turns in to a honor issue to fix the software-center. 

I think others have given up.

[http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html](http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html)

---

### Post by Geoffrey_Arndt on 2015-10-16
What happens if you use a live version of ubuntu - - can you do a session only install without errors?  (using Ubuntu Software Center of course).

---

### Post by blm-ubunet on 2015-10-16
apt-get autoremove
apt-get autoclean
apt-get update
apt-get dist-upgrade


Note: the "dist-upgrade" **does not** upgrade your ubuntu release from 14.04 to 15.xx. It upgrades you to the latest point release in the 14.04 LTS series.

Un-installing (or non-functional) software centre package is bonus IMO.

---

### Post by sandyd on 2015-10-16
The issues with software center are sometimes caused by issues with sources.

Can you post the output of
```

cat /etc/apt/sources.list
grep "" /etc/apt/sources.list.d/*

```

---

### Post by shadytv on 2015-10-18
software center has nothing on a package manager. It's nice to have a gui every once and awhile but a better way to install applications in Ubuntu is:

sudo apt-get install <Program Name>

after doing a little searching I found this thread that might help:
[https://askubuntu.com/questions/481597/software-center-doesnt-work](https://askubuntu.com/questions/481597/software-center-doesnt-work)

The answer is to reinstall software center which can be done with the following command:

sudo apt-get --purge autoremove software-center && sudo apt-get install software-center 

Please let us know if this works for you.

---

### Post by igorteuri on 2015-10-18
Thank you guys for the answers !! *--* It's amazing to have as interested comunity to count on! 

**@blm-ubunet**
Unfurtunatelly, it didn't work

**@sandyd**
Of course I can ^^
[SIZE=1]```
ryuke@uRyuke:~$ **sudo cat /etc/apt/sources.list**# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) stable non-free



```

```
ryuke@uRyuke:~$** grep "" /etc/apt/sources.list.d/***/etc/apt/sources.list.d/getdeb.list:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb apps
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/indicator-brightness-ppa-trusty.list:deb [http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu](http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/indicator-brightness-ppa-trusty.list:# deb-src [http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu](http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/indicator-brightness-ppa-trusty.list.save:deb [http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu](http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/indicator-brightness-ppa-trusty.list.save:# deb-src [http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu](http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu) trusty main
/etc/apt/sources.list.d/jd-team-jdownloader-trusty.list:deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) trusty main
/etc/apt/sources.list.d/jd-team-jdownloader-trusty.list:# deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) trusty main
/etc/apt/sources.list.d/paolorotolo-droidcam-trusty.list:deb [http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu](http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu) trusty main
/etc/apt/sources.list.d/paolorotolo-droidcam-trusty.list:# deb-src [http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu](http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu) trusty main
/etc/apt/sources.list.d/paolorotolo-droidcam-trusty.list.save:deb [http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu](http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu) trusty main
/etc/apt/sources.list.d/paolorotolo-droidcam-trusty.list.save:# deb-src [http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu](http://ppa.launchpad.net/paolorotolo/droidcam/ubuntu) trusty main
/etc/apt/sources.list.d/steam.list:deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
/etc/apt/sources.list.d/steam.list:deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
/etc/apt/sources.list.d/steam.list.save:deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
/etc/apt/sources.list.d/steam.list.save:deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
/etc/apt/sources.list.d/webupd8team-java-trusty.list:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
/etc/apt/sources.list.d/webupd8team-java-trusty.list:# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
/etc/apt/sources.list.d/webupd8team-java-trusty.list.save:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
/etc/apt/sources.list.d/webupd8team-java-trusty.list.save:# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
ryuke@uRyuke:~$ 



```[/SIZE]

**@shadytv**

It didn't work too T_T

---

### Post by sandyd on 2015-10-18
Looks clean

There are no errors when running 
```

sudo apt-get update
```
right?

---

### Post by igorteuri on 2015-10-18
No, not even one error... :X 
apt-get updating is doing fine

---

### Post by sandyd on 2015-10-18
Huh, seems to be a software center bug then.

Judging from the amount of bugs in [https://bugs.launchpad.net/ubuntu/+source/software-center/](https://bugs.launchpad.net/ubuntu/+source/software-center/), your probably better off using synaptic.
I've personally found muon (KDE/Kubuntu) quite reliable myself though I mainly use the command line to manage packages.

---

### Post by Bucky Ball on 2015-10-18
Perhaps try installing Synaptic? 

```
sudo apt-get install synaptic
```

... and use that? Not a fix, but noticing a few Software Centre issues from people at the moment. :-k

---

### Post by igorteuri on 2015-10-18
I've already installed Synaptic  ^^
Now I have to learn how to use it. I'll search a few tutorials on internet.
In a certain way, this crash helped me, because I had to learn how use terminal haha (at least the basics)
Thanks for the reading! :D

---

