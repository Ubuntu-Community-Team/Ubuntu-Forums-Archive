---
title: "HOWTO: Sound Fixes"
date: 2010-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by lkjoel on 2010-07-18
[SIZE=5]Requirements[/SIZE]
[LIST=1]
[*]Check on soundcards.txt to make sure your soundcard is supported
[*]Make sure your sound card is working
[*]Your Ubuntu version must be 9.10 or greater
[*]You must have good knowledge of the Terminal
[/LIST]
[SIZE=5]Pre-Installation Instructions[/SIZE]
[SIZE=4]Removing ALSA and PulseAudio[/SIZE]
Open up a Terminal (Applications->Accessories->Terminal) window.
Type inside it:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo /etc/init.d/alsa-utils stop
sudo apt-get remove alsa-base alsa-utils
```Be sure that it does not want to remove gdm, but don't worry if it wants to remove ubuntu-desktop.
[SIZE=3][SIZE=4]Making sure ALSA is not being depended on[/SIZE]
[/SIZE]```
sudo dpkg-reconfigure linux-sound-base
```A message will pop up, just press <ENTER>.
Then it will ask you what is the default sound output.
Use the Up/Down arrow keys to navigate.
Select OSS, then press <TAB> to select OK, then press <ENTER>.
[SIZE=4]Making ALSA applications work with OSS (Optional)
[/SIZE]```
sudo apt-get install libasound2-plugins
echo "
 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }" > ~/.asoundrc
```[SIZE=4]Installing Necessary Packages
[/SIZE]```
sudo apt-get install -y binutils libgtk2.0-0 sed gcc libc6
sudo apt-get install -y build-essential linux-headers-`uname -r` gawk libtool libgtk2.0-dev
sudo apt-get install -y libesd0 libsdl1.2debian-oss
sudo apt-get install -y esound esound-clients esound-common libesd0
sudo apt-get install -y arts
sudo add-apt-repository ppa:dtl131/ppa
sudo apt-get install -y gnome-applets gnome-media gnome-settings-daemon libcanberra
```[SIZE=5]Installing OSS
**[SIZE=3]Restart your computer[/SIZE]**[SIZE=3]
[/SIZE][/SIZE]```
sudo apt-get install -y mercurial
cd /opt
sudo hg clone http://opensound.hg.sourceforge.net:8000/hgroot/opensound/opensound oss-devel
cd ~/
sudo rm -rf oss42build
mkdir oss42build
cd oss42build/
NO_WARNING_CHECKS=yes /opt/oss-devel/configure --enable-libsalsa=NO
make
sudo make install
```[SIZE=5]Updating OSS
[/SIZE]```
cd /opt/oss-devel
sudo hg pull
sudo hg update
cd ~/
sudo rm -rf oss42build
mkdir oss42build
NO_WARNING_CHECKS=yes /opt/oss-devel/configure --enable-libsalsa=NO
make
sudo make install
```[SIZE=5]Configuring Applications to use OSS[/SIZE]
A complete guide is located on: [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4)
[SIZE=5]What's Next?[/SIZE]
Reboot, then type:
```
osstest
```If you hear some music, your sound has been fixed!
[SIZE=5]Troubleshooting[/SIZE]
If you do have any problems, and/or "osstest" does not work, please reply and add the output of these commands:
```
ossmix
ossinfo -v3
```I would be glad to help you!

---

