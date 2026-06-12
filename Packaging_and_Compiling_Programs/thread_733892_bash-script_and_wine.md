---
title: "bash-script and wine"
date: 2008-03-24
forum: Packaging and Compiling Programs
---

### Post by Sandsound on 2008-03-24
On my website ( [http://www.sandgreen.dk/index.php?side=linux_wineasio](http://www.sandgreen.dk/index.php?side=linux_wineasio) ) I have made a simplyfied guide on how to install wineasio, mostly for my own amusement.
I'd like to make it even more simple, so I'm trying to make a script that does this :

$ sudo apt-get -y install wine wine-dev libjack0.100.0-dev qjackctl build-essential

winecfg : click the audio-tab, make shure that only the "alsa" is checked

Download a precompiled wineasio.dll.so (version 0.7.3) and copy the file to the /usr/lib/wine/ folder

$ regsvr32 wineasio.dll

$ sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0

This is my script so far (by the way... my first script ever :-) ) :

> #!/bin/bash
# by Sandy Sandgreen
# Install wineasio 0.7.3 on Ubuntu 8.04
echo "This script will download and install wineasio ... this might take awhile, please be patient" ;
echo "First it will install the latest wine, jack and some other usefull stuff" ;
sudo apt-get -y install wine wine-dev libjack0.100.0-dev qjackctl build-essential
echo "Then it will download the wineasio driver and place it in your wine-folder" ;
mkdir -p ~/wineasio_tmp
cd ~/wineasio_tmp
wget [http://www.sandgreen.dk/xt2/files/wineasio_0.7.3/wineasio.dll.so](http://www.sandgreen.dk/xt2/files/wineasio_0.7.3/wineasio.dll.so)
chmod u+rwx wineasio.dll.so
sudo mv wineasio.dll.so /usr/lib/wine/
rm -Rf ~/wineasio_tmp
regsvr32 wineasio.dll
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
echo "All done :-) ... Now you can use the win-version of EnergyXT2 (or Reaper) with wineasio" ;
exit

My problem is that I don't know how to check if wine is set to alsa in the audio-tab, and how to corect this if it isnt ?

---

### Post by Sandsound on 2008-03-25
Almost there, had some help in the wine-forum :-)

> #!/bin/bash
# by Sandy Sandgreen
# Install wineasio 0.7.3 on Ubuntu 8.04
#
# Thanks to Jacklab for the wineasio source
# but also to David Hayes and AlanPoPo who both made a great howto
#
echo "This script will download and install wineasio" ;
echo "This might take awhile, please be patient" ;
echo "First it will install the latest wine, jack and some other usefull stuff" ;
sudo apt-get -y install wine wine-dev libjack0.100.0-dev qjackctl build-essential
echo "Configuring wine" ;
wineprefixcreate -w
mkdir -p ~/wineasio_tmp
cd ~/wineasio_tmp
echo "REGEDIT4" >> alsa.reg
echo "[HKEY_CURRENT_USER\Software\Wine\Drivers]" >> alsa.reg
echo '"Audio"="alsa"' >> alsa.reg
wine regedit alsa.reg
echo "Then it will download the wineasio driver and place it in your wine-folder" ;
wget [http://www.sandgreen.dk/xt2/files/wineasio_0.7.3/wineasio.dll.so](http://www.sandgreen.dk/xt2/files/wineasio_0.7.3/wineasio.dll.so)
chmod u+rwx wineasio.dll.so
sudo mv wineasio.dll.so /usr/lib/wine/
rm -Rf ~/wineasio_tmp
regsvr32 wineasio.dll
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
echo "All done :-) ... Now you can use the win-version of EnergyXT2 (or Reaper) with wineasio" ;
echo "Press [ENTER] to close the shell"
read

If anyone have ideas, suggestions or other input, you are more than welcome.

---

### Post by musicfanlinux on 2008-10-14
Dear Sandsound!

I used your excellent script before successfully. 

But in september (2008) I reinstalled my Ubuntu (with Wubi), and after that it's not working perfectly...

I tried to edit your script, because the wine folder is now in usr/lib32/wine folder.

It can be installed with error messages, but after that it's not working. 

Wineasio is working in Wine, I can test it's sound in Wine (in the configuration settings). 

I can also choose WINEASIO in Reaper.

But there is no input/output device in Reaper below the wineasio driver box. It is completely blank (all four little boxes or windows)!

There is no sound of course...

I tried with Jack running, and it got even worse, Reaper is crashing instantly...

I suspect, that maybe the new Wine version can be the problem, but in Wine 0.9x the problem remains.

Maybe libjack is the problem?

Can you help me?

It worked before on the same configuration without any problems!

---

