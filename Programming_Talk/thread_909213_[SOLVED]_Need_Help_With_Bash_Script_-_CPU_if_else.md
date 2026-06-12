---
title: "[SOLVED] Need Help With Bash Script - CPU if else"
date: 2008-09-03
forum: Programming Talk
---

### Post by OffHand on 2008-09-03
Hi Guys,

I wondered if someone could help me with my nearly completed bas script. The problem is that if/else does not work properly. Basically it should detect which cpu is used (intel or ppc) and with that info do the if/else.
The command uname -p, if used on a Mac, will either output i386 for Intel and powerpc for PPC macs. The if part of the script is for the Intel (i386) and the else part is for PPC (powerpc).

Right now the script does not work. Help is greatly appreciated!


#!/bin/sh

uname -p
a=$?

if test "$a" = "0"; 
then
pushd ~/Desktop; curl -C - -O [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx_ub.dmg.zip;](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx_ub.dmg.zip;) popd
pushd ~/Desktop; unzip install_flash_player_osx_ub.dmg.zip -d ~/Desktop/ && rm -r __MACOSX; popd
pushd ~/Desktop; open /Users/180it/Desktop/Install\ Flash\ Player\ 9\ UB.dmg; popd
rm ~/Desktop/install_flash_player_osx_ub.dmg.zip
else
pushd ~/Desktop; curl -O [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx.dmg;](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx.dmg;) popd
pushd ~/Desktop; open install_flash_player_osx.dmg; popd
fi

---

### Post by ilrudie on 2008-09-03
you probably want something like:

> **OffHand said:**
> 
#!/bin/bash

UNAME_P=`uname -p`

if [ "i386" = "$UNAME_P" ]; then
#this is what happens if uname -p return i386
pushd ~/Desktop; curl -C - -O [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx_ub.dmg.zip;](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx_ub.dmg.zip;) popd
pushd ~/Desktop; unzip install_flash_player_osx_ub.dmg.zip -d ~/Desktop/ && rm -r __MACOSX; popd
pushd ~/Desktop; open /Users/180it/Desktop/Install\ Flash\ Player\ 9\ UB.dmg; popd
rm ~/Desktop/install_flash_player_osx_ub.dmg.zip
else
#this is what happens if uname -p does not return i386
pushd ~/Desktop; curl -O [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx.dmg;](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx.dmg;) popd
pushd ~/Desktop; open install_flash_player_osx.dmg; popd
fi

---

### Post by OffHand on 2008-09-03
Thanks ilrudie but I had already found a working solution:

#!/bin/sh

if [[ `uname -p` == 'i386' ]]; then
cd ~/Desktop; curl -C - -O [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx_ub.dmg.zip](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx_ub.dmg.zip)
unzip install_flash_player_osx_ub.dmg.zip -d ~/Desktop/ && rm -r __MACOSX
open /Users/180it/Desktop/Install\ Flash\ Player\ 9\ UB.dmg
rm install_flash_player_osx_ub.dmg.zip
else
cd ~/Desktop; curl -O [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx.dmg](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_osx.dmg)
open install_flash_player_osx.dmg
exit
fi

---

