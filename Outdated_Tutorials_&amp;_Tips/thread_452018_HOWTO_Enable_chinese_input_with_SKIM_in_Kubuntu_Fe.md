---
title: "HOWTO: Enable chinese input with SKIM in Kubuntu Feisty"
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by LordOfThePigs on 2007-05-22
Hello,

after hours of frustration I finally found a way to get SKIM to work properly in Kubuntu 7.04 Feisty (32 bits) in a non-chinese session (that is your session is in your native non-CJK language, but you still want to be able to input chinese). Although this guide has only been tested for chinese, it probably works just as well for Japanese or Korean or any other CJK language.

There are already several guides on how to setup CJK input under ubuntu or Kubuntu but none of them satisfied all my requirements:

Kubuntu/KDE
SKIM
Non-CJK session
Input also works in OpenOffice.org

if your requirements are the same, this guide should work for you.

[list=1]
[*]**Install chinese language support from the system settings**
   [list=a]
    [*] go to K->System settings->Regional & Language
    [*] Press "Install new Language", choose chinese and press install
    [*] let the installation take place. This will take a long time since because of weird package dependencies, firefox, thunderbird and Openoffice.org will all be installed too. You can remove them later anyway
    [*] The install is finishes, go again to K->System settings->Regional & Language
    [*] click "add language" and pick your variation of chinese
    [*] reorder the languages to put english (or you favorite language) on top of the list
    [*] click apply and exit the application
    [/list]

[*]** Setup scim to support your session's locale**
    [list=a]
    [*] open Konsole (K->System->Konsole)
    [*] type the following command to find you session's locale
```
locale | grep LANG=
```
this command should print something like
```
LANG=en_US.UTF-8
```
your locale is the part on the right side of the = symbol
    [*] open ~/.scim/global
```
kate ~/.scim/global
```
    [*] Add the following line at the end of the file
```
/SupportedUnicodeLocales = en_US.UTF-8
```
replace en_US.UTF-8 by the locale you found out in step b
    [*] save the file and close kate
    [/list]

[*]**Setup scim to use skim**
    [list=a]
    [*]type the following command to tell scim to use skim
```
scim-panel-kde -d -f
```
    [*] Open skim's configuration dialog (right-click the skim icon in the system tray and select "configure")
    [*] Go to Global Settings->General SCIM, change these settings as follows:
```
Panel Program: scim-panel-kde
Config Module: kconfig
```
    [/list]

[*] Configure scim to startup with your sesion
    [list=a]
    [*] type the following commands
```
kdesu kate /etc/X11/Xsession.d/74custom-scim_startup
```
to start kate as root.
    [*] paste the following lines in kate
```

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

```
    [*] Save the document and quit kate
    [*] Log out and log in again. (Or even reboot if you feel like it).
    [/list]
[/list]
 
SCIM should now work properly for your locale.

**References**

[SCIM/Kubuntu - Community Documentation](https://help.ubuntu.com/community/SCIM/Kubuntu?action=show)
[Kubuntu 7.04 - Japanese Input via Skim](http://ubuntuforums.org/showthread.php?t=428431)
[HOWTO: Japanese Input and Fonts in Ubuntu 7.04](http://ubuntuforums.org/showthread.php?t=396135)

---

### Post by Régis B. on 2007-06-05
Thanks, I've already used this Howto to install skim with simplified Chinese on two different computers.
However I have the same (admittedly small) problem on both computers: after the system has booted the default input method is set to Chinese; of course I just have to click and select English/European but it's quite annoying since I have to do this after each reboot. 

I haven't found a way to set the default language of skim, would you know how to do that?

Thanks
Régis

---

### Post by Cris987 on 2007-07-27
Great post! I spent the last hour trying to figure out why skim didn't just "work" as some wiki says. Perhaps you can change the scim community wiki with this.

---

### Post by zoobave on 2007-08-14
Hi,
     Is it possible to switch/choose the languages using shell commands dynamically?

regards,
Zoobave
[http://zoobave.blogspot.com](http://zoobave.blogspot.com)

---

### Post by mikerduffy on 2007-09-02
Thank you!

---

### Post by Metallion on 2007-11-18
Thank you very much for this guide. It worked perfectly for me... Until I broke it again :(


EDIT: Never mind... I noticed that everything still worked in gtk based programs. I just forgot to reinstall the scim-qtimm package. Thank you very much again for this solution!


The problem is that I wanted to make a shortcut to switch directly to Anthy. (I used Japanese input instead of Chinese) Afterwards I wanted to remove this hotkey again but it just didn't happen. I removed it in the options screen but nothing happened and it was right back there next time I checked.

Getting a bit desperate, I decided to purge all the scim and skim packages, reinstall them and retrace the steps in this guide. This time it didn't work... Skim isn't listening to my ctrl+space hits any more.

"im-switch -l" has given me this output

```

Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/***/.xinput.d/en_US" is defined as a link pointing to
scim
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - status is manual.
 link currently points to scim
default - priority 10
none - priority 0
scim - priority 0
scim-immodule - priority 0
uim - priority 0
uim-toolbar - priority 0
uim-systray - priority 0
uim-toolbar-qt - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default none scim scim-hangul scim-hangul_xim scim-immodule scim-pinyin th-xim uim uim-systray uim-toolbar uim-toolbar-qt
=======================================================

```

It looks like it's pointing to scim but somehow skim still won't listen. Any thoughts on this?

---

### Post by areskz on 2008-10-26
Great guide, thank you.
Guys, please help me choosing right input method &#8212; I just can't figure out what is the appropriate one (between all those Ziranma, Wubi and so on). I need to write simplified chinese.

---

### Post by margazhang on 2009-12-27
Hi, I am using the newest version of Kubuntu - 9.10. Do all the above instructions still apply?

I see Kubuntu (and all other variations Ubuntu, Edubuntu, etc.) use the iBus input method framework. I am running the iBus Preferences program and have successfully added Simplified Chinese PinYin to it. I guess I need to reboot to be able to input Chinese.

---

### Post by Janay on 2010-04-04
I can no but thank the author of this post.  I just did a fresh install of Karmic on a new computer, and after re-and un-installing scim, skim, editing files, erasing files, and everything for a day and a half, I found this guide and followed it. ** It worked!**  Thank you.  Just in case someone else is fighting despair just as I did, I copy below some possible googlings in order to try and make this easier to find.  In case they should not go here, I humbly pose a petition for a moderator to erase it and leave just

**[...]**  and any necessary comment.  There they go:

[COLOR=White]install scim on kubuntu karmic, chinese input kubuntu karmic, make scim work on karmic, scim configuration kubuntu karmic, easy scim configuration kubuntu, scim config solved, scim configuration solved, configure scim, scim skim not working on karmic, scim skim not working on kubuntu...[/COLOR]

  Again, my most sincere, thankful and honest greetings to LordOfThePigs for this post.

---

