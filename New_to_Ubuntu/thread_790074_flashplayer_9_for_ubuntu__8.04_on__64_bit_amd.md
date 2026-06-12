---
title: "flashplayer 9 for ubuntu  8.04 on  64 bit amd ?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by infoanalysis on 2008-05-11
8.04/ 64 amd/  

I finally got my hd boot up on a 64 amd. But earlier when I cd booted while I was running 32 bit  XP, I was able to load flashplayer, but now the terminal says that I can't run 64 bit after I formated the entire hard drive off of XP

ERROR your archtecture ,\'x86 64\ is not supported by the adobe flash player installer.

I have not been able to find step by step instructions on how to get flash 9 running on 64 bit

help is appreciated, I only got a garbled screen when I tried to run the 32 bit version of ubuntu 8.04 on the 64 bit amd

---

### Post by halln on 2008-05-11
Try this link: [http://ubuntuforums.org/showthread.php?t=476924&highlight=flashplayer+nonfree](http://ubuntuforums.org/showthread.php?t=476924&highlight=flashplayer+nonfree)
Hope it helps.

---

### Post by infoanalysis on 2008-05-11
I did the install of nspluginwrapper, it looked like it took , selected 4 for hardy heron and also entered password then before the reboot my username- but nothing came up for the flashplayer when I opened you tube.

Any thoughts or suggestions?

---

### Post by SunnyRabbiera on 2008-05-11
well I think youtube also needs the java plug in too, good luck as 64bit systems can be a pain to get media on.

---

### Post by Hutto on 2009-06-24
echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

---

### Post by presence1960 on 2009-06-24
here is the simplest of simple fixes to install 64 bit Flash taken from our Ubuntu x86-64 users section of the forum : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Has worked flawlessly for me on hardy, Intrepid & Jaunty.

I would remove all other instances of flash prior to installing.

for the 64 bit Java see here: [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)  this is really crisp & snappy. Thanks to zika for the how to.

---

### Post by durand on 2009-06-27
Why not use flash 10 instead? It has a native 64bit plugin.

---

### Post by MasterProg on 2009-06-27
I have used 64 bit version of flash player 10 when it came out and it worked fine. Try it.

---

