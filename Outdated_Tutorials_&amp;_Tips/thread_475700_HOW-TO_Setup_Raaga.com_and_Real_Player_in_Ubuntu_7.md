---
title: "HOW-TO: Setup Raaga.com and Real Player in Ubuntu 7.04 Feisty Fawn"
date: 2007-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by vguhesan on 2007-06-16
Hello All:

I have seen a lot of posts in the past that have complained that after upgrade to Ubuntu 7.04 Feisty Fawn, some of the popular music sites for Indians such as Raaga.com are no longer working when it comes to using RealPlayer 10.

Here is a fix that worked for me...

My Specifications:
Ubuntu 7.04 Feisty Fawn
Fire Fox 2.0.0.4
Real Player 10 (what came with the regular Synaptic sources...)
Date: Saturday, June 16, 2007

Issue:
From my limited understanding and research, it seems that the current production release of RealPlayer has some incompatibility with some sites... and some solutions propose that you revert to an older release of Real Player 10.0.3-1... This solution is sound but I have found that instead of going backward, I tried using a build from the nightly release of Real Player and this also fixes the problem so I usually prefer using a newer release than a older release... So if you would like to use a newer release, then read on...

1. Go here: (Helix Community Nightly Stable Builds of RealPlayer NOT HelixPlayer)
[http://forms.helixcommunity.org/helix/builds/?category=realplay-current](http://forms.helixcommunity.org/helix/builds/?category=realplay-current)

2. Download: RealPlayer (package) - linux-2.2-libc6-gcc32-i586@rhel4
(The one I have is built on 06/15/07. And at this present time Helix Community DOES NOT distribute packages for Ubuntu/Debian releases. Hopefully that will change in the future. So what we'll need to do is install and run another program called 'alien' which re-packages the RPM file into a DEB install package.) 
Save the file to ~/Desktop because my directions below are assuming that you have it downloaded to your 'Desktop'. File name downloaded will be something like this: 

3. Open a terminal prompt and run the following commands: (need to have administrator password for this)
sudo apt-get update
sudo apt-get install alien

Now you have alien installed. If you have some problem go here and read about it:
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

4. Converting RPMs to DEB installer. Type the following in the terminal prompt
cd ~/Desktop
sudo alien -k name-of-rpm-file.rpm
[in my case the file name is RealPlayer-10.1.0.3239-20070615.i586.rpm]
After completeion you should now have a ".deb" file on your desktop.

5. Installing the debian package (DEB): Run the following in the terminal:
sudo dpkg -i name-of-deb-file.deb
[in my case it's RealPlayer-10.1.0.3239-20070615.i586.deb]
This brings up a dialog asking you to install the package... go ahead and install and when completed this copies the files and the executables under /opt/real/RealPlayer directory.

6. Now you need to add the realplay executabel to the System Path. Here's how:
sudo ln -s /opt/real/RealPlayer/realplay /usr/bin/realplay

7. Now you need to make sure you have copied the needed plugin's to FireFox profile under your user home directory:
- Open a Nautilus Explorer (equivalent to Windows Explorer) and choose under <View> in the top menu, <Show Hidden Files>
- Navigate to "/opt/real/RealPlayer/mozilla" directory. And here you should see a couple of files: nphelix.so nphelix.xpt. Copy those two files to this location: "~/.mozilla/plugins", here the tilde(~) represents your Home Directory. Once you copy the two files there and you restart FireFox (ff), ff will be able to find the plugins when it needs RealPlayer...

8. Now you can goto, Raaga.com - choose your favorite songs and listen to them... 

I hope you have found this link useful. If you have any questions or comments to share send them to Venkatt.Guhesan @ yahoo dot com

Enjoy!!!

---

