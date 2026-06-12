---
title: "Japanese language support broke something."
date: 2008-08-06
forum: New to Ubuntu
---

### Post by danmeetswood on 2008-08-06
So I go into System>Administration>Language_Support and enable Chinese and Japanese language support, click ok. Things start downloading and such and eventually come to a standstill; stopped while installing the Japanese pack. It's sitting there for who knows how long and I eventually restart the computer. Now I hear 
"Only one software management tool is allowed to run at the same time. Please close the other application e.g. 'Update Manager', 'aptitude' or 'synaptic' at first." 
When I try to open something like Synaptic Package Manager, it tells me 
"An error occurred. The following details are provided. 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'"
I run 'sudo dpkg --configure -a' like it tells me to, and I assume it resumes the incompleted download. But the problem is that the Japanese language support install still does nothing! Is there anywhere to go from here? Can I reset my language settings or something? 'Cause I tell ya, It's times like this when I really hate Ubuntu. It can really be like a house of cards built on a marble block.
Running Ubuntu 7.10 "The Gutsy Gibbon" on a Sony Vaio VGN-N365E laptop, and any help is appreciated.

---

### Post by Pro-reason on 2008-08-07
Did running "*sudo dpkg --configure -a*" fix your system so that you are able to install/remove packages normally?

What Japanese packages are you trying to install exactly?

---

### Post by danmeetswood on 2008-08-07
No, it just sits there in some sort of download loop, sucking up about 60% of my computers resources, and preventing me from opening Synaptic. And I've been running like that over 24 hours, so chances are pretty slim that it's working.
I was trying to add support through System>Administration>Language_Support. So nothing weird or foreign to the system. The terminal says 
"Setting up language-support-ja (1:6.06+20060529) ...
Generating locales...
  ja_JP.UTF-8... "
The Chinese works, Japanese just caught a snag it seems.

---

### Post by Pro-reason on 2008-08-09
Ah yes, that thingy in the GNOME menus.  I think I had trouble with that when I tried out GNOME.

I use KDE 4.  I just set up CJK input myself.  Get Synaptic working, and then use it to install *language-support-ja*.  Look on these forums for guides to setting up input methods perfectly.

---

### Post by danmeetswood on 2008-08-11
No such luck, I enter "sudo apt-get install language-support-ja" and Ubuntu tells me 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
But I know THAT'S not going to work.

---

### Post by danmeetswood on 2008-08-11
If anybody has any ideas don't be embarrassed to chime in. I sure would like to download things again!

---

### Post by Pro-reason on 2008-08-11
Perhaps you could try

```

sudo apt-get -f remove

```

---

### Post by danmeetswood on 2008-08-14
Nope, still get "dpkg was interrupted" error.

---

### Post by Pro-reason on 2008-08-15
Try these two commands, one after the other:

```

sudo dpkg --remove --force-all language-support-ja
sudo dpkg --configure -a

```

Copy the full output of these commands and paste it here.

---

### Post by danmeetswood on 2008-08-15
First line
```
dan@dennis:~$ sudo dpkg --remove --force-all language-support-ja
[sudo] password for dan:
(Reading database ... 130517 files and directories currently installed.)
Removing language-support-ja ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

```
Second line
```
dan@dennis:~$ sudo dpkg --configure -a
Setting up language-support-zh (1:7.10+20070626) ...
Generating locales...
  zh_CN.UTF-8... 


```
and then it gets stuck there, eating 60% of my resources again.

---

### Post by Pro-reason on 2008-08-16
> **danmeetswood said:**
> 
Second line
```
dan@dennis:~$ sudo dpkg --configure -a
Setting up language-support-zh (1:7.10+20070626) ...
Generating locales...
  zh_CN.UTF-8... 


```
and then it gets stuck there, eating 60% of my resources again.

Hmm, I don't know why it's having problems setting up the locale.

I can only suggest the following:
```

sudo dpkg --force-all --remove language-support-zh language-support-ja
sudo apt-get -f remove

```

There must be a way of getting a list of the packages that it considers to be broken, but I don't know.

---

### Post by danmeetswood on 2008-08-16
After entering the first line it told me to use --purge and I did. The second line gets me stuck again.```
dan@dennis:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjack0.100.0-0 libqt3-i18n caps libsdl-sound1.2 libmikmod2 libsamplerate0
  stk tcl8.4 tk8.4 libstk0c2a libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up language-pack-zh-base (1:7.10+20080205) ...
Generating locales...
  zh_CN.UTF-8... 

```

---

### Post by Pro-reason on 2008-08-16
> **danmeetswood said:**
> After entering the first line it told me to use --purge and I did. The second line gets me stuck again.```
dan@dennis:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjack0.100.0-0 libqt3-i18n caps libsdl-sound1.2 libmikmod2 libsamplerate0
  stk tcl8.4 tk8.4 libstk0c2a libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up** language-pack-zh-base** (1:7.10+20080205) ...
Generating locales...
  zh_CN.UTF-8... 

```
It seems that it gets stuck on each package that requires the locales to be generated.  You see that it's "language-pack-zh-base" this time?

Run the commands I gave you before again, and add that package to the list of ones to remove/purge.  If it chokes on another package, then add that to the list too.  Rinse and repeat.  Keep on doing it until no packages mess it up.  I don't know a more elegant way of doing it, although there surely is one.  Sorry.

---

### Post by danmeetswood on 2008-08-17
I think it worked with language-support-zh-base, but now It's stuck on language-support-ja-base. I enter ```
dan@dennis:~$ sudo dpkg --force-all --remove language-support-ja-base
dpkg - warning: ignoring request to remove language-support-ja-base which isn't installed.

```
or "purge" to fix it, but it ignores me. But when I go to run "sudo apt-get -f remove" it gets stuck here. ```
dan@dennis:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up language-pack-ja-base (1:7.10+20080205) ...
Generating locales...
  ja_JP.UTF-8... 

```
What's that about? I need to communicate to my computer that I don't want this thing.

---

### Post by Pro-reason on 2008-08-17
OK, looking in Synaptic, I can see that the dependants of *language-support-ja-base* are *language-pack-ja, language-pack-kde-ja, language-pack-gnome-ja, language-pack-kde-ja-base, *and* language-pack-gnome-ja-base*.

If you make sure that all of those are gone (with *sudo dpkg --purge*), I think (or hope) that the package will not try to install itself again.

---

### Post by danmeetswood on 2008-08-18
```
dan@dennis:~$ sudo dpkg --force-all --purge language-support-ja-base language-pack-ja language-pack-kde-ja language-pack-gnome-ja language-pack-kde-ja-base language-pack-gnome-ja-base
[sudo] password for dan:
dpkg - warning: ignoring request to remove language-support-ja-base which isn't installed.
(Reading database ... 129716 files and directories currently installed.)
Removing language-pack-ja ...
Removing language-pack-kde-ja-base ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
Purging configuration files for language-pack-kde-ja-base ...
Removing language-pack-gnome-ja-base ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
Purging configuration files for language-pack-gnome-ja-base ...
Removing language-pack-kde-ja ...
Removing language-pack-gnome-ja ...
dan@dennis:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  language-pack-ja
The following NEW packages will be installed:
  language-pack-ja
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/195kB of archives.
After unpacking 815kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```
Doesn't look like it, man.

---

### Post by Pro-reason on 2008-08-19
> **danmeetswood said:**
> 
Doesn't look like it, man.
Ah, but at least it's not trying to install *language-pack-ja-base* any more.  Looking at *language-pack-ja*, I can see some more dependants: *ubuntu-desktop-ja, kubuntu-desktop-ja* and *kubuntu-desktop-ja-base*.  Add those to the list of things to purge, and try again.

---

### Post by danmeetswood on 2008-08-19
I guess that's true. But it doesn't look like any of those things you said were installed anyway.
```
dan@dennis:~$ sudo dpkg --force-all --purge language-pack-ja ubuntu-desktop-ja kubuntu-desktop-ja kubuntu-desktop-ja-base
[sudo] password for dan:
dpkg - warning: ignoring request to remove language-pack-ja which isn't installed.
dpkg - warning: ignoring request to remove ubuntu-desktop-ja which isn't installed.
dpkg - warning: ignoring request to remove kubuntu-desktop-ja which isn't installed.
dpkg - warning: ignoring request to remove kubuntu-desktop-ja-base which isn't installed.
dan@dennis:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  language-pack-ja
The following NEW packages will be installed:
  language-pack-ja
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/195kB of archives.
After unpacking 815kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by Pro-reason on 2008-08-19
This is driving me crazy.

OK, new tactic: I've used the menu to install all Japanese support, and noted what packages got installed.

Add the following to the list of things to purge:

```
openoffice.org-I10n-ja *edit: sorry, that should be "openoffice.org-**l**10n-ja"*
openoffice.org-help-ja
scim-anthy
thunderbird-locale-ja
language-support-input-ja
language-support-fonts-ja
language-support-translations-ja
scim-tables-ja
```

---

### Post by danmeetswood on 2008-08-20
There's GOT to be a better way.
```
dan@dennis:~$ sudo dpkg --force-all --purge openoffice.org-I10n-ja openoffice.org-help-ja scim-anthy thunderbird-locale-ja language-support-input-ja language-support-fonts-ja language-support-translations-ja scim-tables-ja
[sudo] password for dan:
dpkg - warning: ignoring request to remove openoffice.org-i10n-ja which isn't installed.
(Reading database ... 128886 files and directories currently installed.)
Removing openoffice.org-help-ja ...
Removing scim-anthy ...
Removing thunderbird-locale-ja ...
dpkg - warning: ignoring request to remove language-support-input-ja which isn't installed.
dpkg - warning: ignoring request to remove language-support-fonts-ja which isn't installed.
dpkg - warning: ignoring request to remove language-support-translations-ja which isn't installed.
dpkg - warning: ignoring request to remove scim-tables-ja which isn't installed.
dan@dennis:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  language-pack-ja
The following NEW packages will be installed:
  language-pack-ja
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/195kB of archives.
After unpacking 815kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by Pro-reason on 2008-08-20
OK, let's put it together a little differently, with one command:

```
**sudo apt-get -f remove** openoffice.org-l10n-ja openoffice.org-help-ja scim-anthy thunderbird-locale-ja language-support-input-ja language-support-fonts-ja language-support-translations-ja scim-tables-ja language-pack-ja language-pack-ja-base ubuntu-desktop-ja kubuntu-desktop-ja kubuntu-desktop-ja-base language-support-ja language-support-zh

```

---

### Post by danmeetswood on 2008-08-23
Doesn't look like it did much more.. appreciate the interest, though.
```
dan@dennis:~$ sudo apt-get -f remove openoffice.org-l10n-ja openoffice.org-help-ja scim-anthy thunderbird-locale-ja language-support-input-ja language-support-fonts-ja language-support-translations-ja scim-tables-ja language-pack-ja language-pack-ja-base ubuntu-desktop-ja kubuntu-desktop-ja kubuntu-desktop-ja-base language-support-ja language-support-zh
[sudo] password for dan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-help-ja is not installed, so not removed
Package scim-anthy is not installed, so not removed
Package thunderbird-locale-ja is not installed, so not removed
E: Couldn't find package language-support-input-ja

```

---

### Post by Pro-reason on 2008-08-23
Hmm, it might have worked... it didn't finish the command, because there was a package it couldn't find.  I don't know why it couldn't find *language-support-input-ja* (I certainly have it installed), but just take it out of the list anyway, and try again.

If we can't fix this, it might be a good idea to go to [https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug) and report it as a bug.

---

### Post by danmeetswood on 2008-08-23
Wow. I can't believe my computer did it. Everything is cool now, opening up download managers and such. I'm going to stay far away from language support for the rest of my life, but I'm really grateful that you helped get my computer back to speed. And hey! It only took two weeks!
```
dan@dennis:~$ sudo apt-get -f remove openoffice.org-l10n-ja openoffice.org-help-ja scim-anthy thunderbird-locale-ja scim-tables-ja language-pack-ja language-pack-ja-base language-support-ja language-support-zhReading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-help-ja is not installed, so not removed
Package scim-anthy is not installed, so not removed
Package thunderbird-locale-ja is not installed, so not removed
Package scim-tables-ja is not installed, so not removed
Package language-pack-ja is not installed, so not removed
Package language-support-ja is not installed, so not removed
Package language-support-zh is not installed, so not removed
The following packages will be REMOVED:
  language-pack-ja-base openoffice.org-l10n-ja
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 13.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128702 files and directories currently installed.)
Removing language-pack-ja-base ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
Removing openoffice.org-l10n-ja ...

```

---

### Post by Pro-reason on 2008-08-23
Glad it got fixed!

Sorry it took me so long to work it out.  An unfortunate characteristic of these forums is that we tend to take the number of replies in a thread as a measure of whether it is being dealt with.  Since I replied several times, other people (who might have been able to lend their expertise) assumed that the thread didn't require them to step in. So, it ended up being my job alone to fix the problem.

This has taught me something about package-manager glitches, and I'll be able to help people better in the future.

Please don't be too scared of language support!  You had a rare glitch in the management of packages.  It is normally not such a big deal.  Now that all of those packages are cleared out, you should be able to install support quite easily.  And just run that final command again if anything messes up.

So, what were you trying to do?  Do you want the system language to be Japanese, or do you just want to be able to input the characters?  I have my machine set up to input Chinese, Japanese, and a host of other languages.  It's a matter of installing the right stuff in Synaptic.

---

### Post by danmeetswood on 2008-08-24
heh, don't worry about the time, man. I understand how things are and I just chilled out on the computer for a while.
As for what I was doing... just exploring really, feeling out some of the edges of Ubuntu. I hadn't really planned on inputting foreign characters, though that does sound interesting. Was it hard to do?

---

### Post by Pro-reason on 2008-08-25
> **danmeetswood said:**
>  I hadn't really planned on inputting foreign characters, though that does sound interesting. Was it hard to do?

No, it's quite easy.  You just go to Synaptic and install some packages like “SCIM”, which allow input of East Asian languages.  There's only a small amount of tweaking to make sure that the input will work in Gtk, Qt3 and Qt4 apps.

---

