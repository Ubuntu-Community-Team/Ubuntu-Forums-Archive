---
title: "How To: Ubuntu 8.04 i386 on Compaq F750US"
date: 2008-05-08
forum: Outdated Tutorials &amp; Tips
---

### Post by AlanB66 on 2008-05-08
This is a how-to with regards to the long-threaded post "[_[COLOR="Blue"]So has anybody successfully installed Ubuntu or Kubuntu on a Compaq F700 #f750us ?[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=687833")"

**_What you'll need:_**
* Compaq F750US
* Ubuntu 8.04 i386 ISO burned to CD (do NOT use AMD64 unless you have patience to iron other things out)

**_What versions are covered:_**
* Ubuntu 8.04  Kernel 2.6.24-16-generic
* NDisWrapper 1.52

**_What you'll have:_**
At the end of these steps, you will have a Ubuntu installation that:
[LIST]
[*]Has wired and wireless LAN access
[*]Has the Wireless LAN supporting non-broadcasting SSID's
[*]Has the i386 OS to support Canon MP520 (for MX700) drivers
[*]Has the capability for other i386 apps that are otherwise hard to come by in AMD64-bit mode
[/LIST]

**_Steps:_**
[LIST=1]
[*]Download and Burn CD for i386 Ubuntu 8.04


[*]Install from CD


[*]Reboot


[*]Open Hardware Manger
   [LIST=a]
   [*]Enable Nvidia Display adapter
   [*]DISABLE HAL & Atheros Wireless
   [/LIST]


[*]Open linux-restricted-modules-common:
     [LIST=a]
     [*]sudo gedit /etc/default/linux-restricted-modules-common )
     [*]Disable both ath_hal and ath_pci            ( DISABLE_MODULES="ath_hal ath_pci" )
     [/LIST]


[*]Reboot


[*]Run Update Manager and update EVERYTHING
    [LIST=a]
    [*]Run "Software Sources" Manager and uncheck/re-check "Universe". During "close" allow "Reload" of sources.
    [*]Run Update Manager, kick of a "Check", and now all updates are now available to download/install.
    [/LIST]


[*]Using Firefox, download to /tmp:
   [LIST=a]
   [*]xp32-5.3.0.56-whql.zip (available here: [[COLOR="Blue"]_http://www.atheros.cz/download.php?atheros=AR5007EG&system=1_[/COLOR]]("http://www.atheros.cz/download.php?atheros=AR5007EG&system=1"))
   [*]ndiswrapper-1.52.tar.gz (available here: [[COLOR="blue"]_http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=573476_[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=573476"))
   [/LIST]


[*]Unravel packages
   [LIST=a]
   [*]cd /tmp
   [*]unzip xp32-5.3.0.56-whql.zip
   [*]tar xvfz ndiswrapper-1.52.tar.gz
   [/LIST]


[*]Get "Make" capabilities updated:
   [LIST=a]
   [*]sudo apt-get update && sudo aptitude install build-essential
   [*]sudo apt-get install subversion
   [/LIST]



**(Picking up from Step #4 on [http://ubuntuforums.org/showpost.php?p=2801168&postcount=86](http://ubuntuforums.org/showpost.php?p=2801168&postcount=86) ...)**


[*]Make and Install ndiswrapper
     [LIST=a]
     [*]cd /tmp/ndiswrapper-1.52
     [*]sudo make all
     [*]sudo make install
     [/LIST]


[*]Do **[COLOR="Red"]_NOT_[/COLOR]** Update /etc/network/interfaces with these lines:
[I][INDENT]     auto eth0
     iface eth0 inet dhcp

     auto wlan0
     iface wlan0 inet dhcp[/INDENT][/I]

[*]Install xp32-5.3.0.56-whql drivers
     [LIST=a]
     [*]cd /tmp
     [*]sudo ndiswrapper -i net5211.inf
     [*]sudo ndiswrapper -l (see item was installed)
     [/LIST]


[*]Load ndiswrapper and check if it worked.
    [LIST=a]
    [*]sudo modprobe ndiswrapper 
    [*]sudo dmesg (shows that the card is installed (hopefully)) 
    [/LIST]


[*] Do [COLOR="Red"]**NOT **[/COLOR]run "ndiswrapper -m"



**At this point, you should be able to use the Network Manager to configure your connection.** :guitar:


[*]Enable ndiswrapper at startup:
    [LIST=a]
    [*]sudo gedit /etc/init.d/ndiswrapper
    [*]add these lines:
[INDENT][I]#!/bin/sh
PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

case "$1" in
start)
        modprobe ndiswrapper
        ;;

*)
        echo "Usage: /etc/init.d/ndiswrapper {start}"
        exit 1
        ;;
esac

exit 0[/I][/INDENT]
    [*]sudo chmod 755 /etc/init.d/ndiswrapper
    [*][COLOR="Gray"]Create link in /etc/rc2.d/S41ndiswrapper --> /etc/init.d/ndiswrapper:[/COLOR]   sudo  ln -s  /etc/init.d/ndiswrapper  /etc/rc2.d/S41ndiswrapper
    [*]Reboot and see if you get on wireless automatically
    [/LIST]
[/LIST]

(Resubmitted from archived post [http://ubuntuforums.org/showthread.php?t=749481](http://ubuntuforums.org/showthread.php?t=749481))

---

### Post by OmniDistortion on 2008-05-16
It works, but does not load automatically at start-up. That doesn't seem to work.

Edit:
> start)

And this was just now fixed by simply putting an open parenthesis where there is a closed. Here it should be "start(" instead.

---

### Post by AlanB66 on 2008-05-16
Not sure why it's working for you now, but that is _**not**_ correct syntax.

What is not auto-loading?

Are you unplugging your wired LAN connection before reboot? For some reason, the system cannot handle both and having the wired LAN plugged in will block the Wireless from working.

Let me know.

---

### Post by OmniDistortion on 2008-05-17
> **AlanB66 said:**
> Not sure why it's working for you now, but that is _**not**_ correct syntax.

What is not auto-loading?

Are you unplugging your wired LAN connection before reboot? For some reason, the system cannot handle both and having the wired LAN plugged in will block the Wireless from working.

Let me know.

That's all I changed to get it to work, honest! I'm clueless beyond that if it's not proper.

---

### Post by AlanB66 on 2008-05-17
> **OmniDistortion said:**
> That's all I changed to get it to work, honest! I'm clueless beyond that if it's not proper.

Well, I can tell you for absolute 100% certainty, that syntax is incorrect.

"Case" is a simplified "IF" statement in Unix scripting. Rather than righting a comparison IF-THEN-ELSE-ELSE-ELSE-ELSE-ENDIF, Case gives a list of options of which to compare and then runs the lines associated with the comparison that matches. 

So, in this situation, "Case" is comparing the first argument to "start". If the first argument is not "start", then the fallback is anything else (thus, *, the wildcard). And, all it does if it's anything else is merely exit.

Please do the following and submit the results:
1. ls -l /etc/init.d/ndiswrapper
2. ls -l /etc/rc2.d/ndiswrapper

Thanks.

---

### Post by smokiemac on 2008-05-25
Thanks for this, saved me a lot of headaches!!! You rock!  also the auto-start listed here didnt work for me either but all i did was:

gedit /etc/modules 
and added ndiswrapper 

after that all was perfect, that maybe a little easier for more noobish people like myself too.

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

