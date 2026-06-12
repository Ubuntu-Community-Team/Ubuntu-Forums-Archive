---
title: "How To: Install regular Ubuntu on the EeePC 2g Surf"
date: 2008-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by wolfen69 on 2008-12-22
OK, it's not the regular full blown gnome desktop, but I think it's alot better than the stock OS.

How To: Install regular Ubuntu onto a 2G Surf

I suggest printing this before beginning.

Like many people, i have tried to get a "real" install of Ubuntu on my 2G Surf, but found myself reinstalling the default Xandros OS because of limited space on the SSD. The following tutorial will enable you to have an honest to goodness Ubuntu install that will do all the basic tasks you need.

What you will need: 

1. Intrepid Ibex mini iso [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso)

2. A wired internet connection.

3. An external CD drive.

4. Some spare time and patience. (took me about 4 hours)
_______________________________________________________________________________________________________________________________________

Burn the mini iso to cd using your favorite burning app. There are other methods of installing this .iso, but i'll leave that up to you if you decide to go in another direction. (think google)

Make sure to have network cable connected before you begin the installation.

Connect external cd drive.

Immediately after turning on the eeepc, press Esc button a few times until a boot menu comes up. You should see a list with your cd drive listed. Select it and hit enter.

After cd boots up, select language then select command line install. The installation after this point will be pretty straight forward, asking you the usual questions and requiring you to add a user name and password.

When you get to the part about partitioning the drive, you basically have 2 choices: Guided-use entire disk and manual. If you choose entire disk, be aware it will use more swap space than doing manual partitioning and you will be left with about 300mb of free space after the install is completely finished. If you choose manual, i recommend using about 128mb of swap space. 

After install you will reboot and be left with a system without a desktop environment. That will be dealt with later in this tutorial.

Log in.

Do:  sudo nano /etc/apt/sources.list

The nano text editor will now open. With the arrow keys, navigate to the following line:
#deb [http://us.archive.ubuntu.com/ubuntu/intrepid-backports](http://us.archive.ubuntu.com/ubuntu/intrepid-backports) main restricted universe multiverse

Place the cursor over the # symbol and hit delete. Next, navigate to the following line:
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

Delete the # as before. If the following line has a # in front of it, remove # also:
#deb [http://us.archive.ubuntu.com/ubuntu/intrepid](http://us.archive.ubuntu.com/ubuntu/intrepid) main restricted 

Use arrow key to go to the bottom of the file to create a new line. Type in the following:
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

Do Ctrl-x, then y, then enter.

Do:  wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 
(keep in mind that -O- is the letter O, not a zero)


Then do:   sudo apt-get update

Then:   sudo apt-get install xorg

Then:   sudo apt-get install xfce4

I chose xfce as the desktop environment simply because it is the smallest lightweight desktop environment that has features similar to gnome. And xfce will fit on the drive, gnome won't. Of course you are free to choose openbox or fluxbox as a desktop environment, but you are on your own as how to configure those. I will provide help for xfce only.

Let's get our apps installed next.

Do:   sudo apt-get install xfce4-battery-plugin gnome-terminal xdm firefox synaptic leafpad wicd wpa-supplicant alsa alsamixer alsamixer-gui thunar

After these apps install, simply do:   startx   to get to your new desktop.

Of note: wicd will be the app to handle our wireless access, leafpad is a text editor, and thunar is the file manager. If at any point a window is too big for the screen, you can move it around by alt-left click-mousepad. Or if you are using a mouse, alt-left click-move mouse.

OK, the fun begins. Let's get our desktop straightened out before we worry about wireless or sound. Right click desktop and go to settings>settings manager>panel. Select the fixed position button. Just below the button you just clicked is a pull down menu. Select full width. Auto-hide is up to you. In the settings manager you will notice that there are many things you can tweak, but i will let you have fun discovering what can be changed and tweaked.

Close the settings manager window and get back to the desktop. Right click your new taskbar and select "add new item". Select xfce menu and task list. Feel free to add any others you see fit. (volume control is also handy) After you install them, you can move them around by right clicking and select "move".

Tired yet? That's too bad, we're almost done ;-)

If, when you go to play music or have sound and it doesn't work, check alsamixergui (in the xfce menu) first. If it still doesn't work, the following is how i set it up:
sudo apt-get install module-assistant

Then:   sudo m-a a-i alsa
This will recompile the latest alsa. (it may give an error at the end of compiling drivers, but disregard this and reboot) This may or may not be a problem for some people, but it worked for me. If you need more assistance, i'm sure the friendly people at eeeuser forums or ubuntuforums will be glad to help.

On to wi-fi.

Do:     sudo apt-get update

Then:   sudo apt-get install linux-backports-modules-intrepid-generic

Then:   sudo modprobe ath5k

Then:   sudo -s
        
Then:   echo blacklist ath_pci >> /etc/modprobe.d/blacklist

Open gnome-terminal and do:   sudo leafpad /etc/default/halt

Add a new line to this file with the following:   rmmod snd_hda_intel
(this fixes a shutdown issue where the eeepc appears to shutdown, but power light stays on)
Save file.

Reboot.

By simply going to Menu>Network>WICD, you should be able to see available wireless networks. The rest is easy.

For those that want a quick helper to install flash in firefox, go to  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)  and download the .deb file for ubuntu 8.04+

Put that file into your Home folder. Open terminal and type: sudo dpkg -i install_flash_player_10_linux.deb

Restart Firefox if open.

I am not going to get into installing multimedia codecs and such, because i will assume that most if not all of you are familiar with using synaptic. But for those that do need help with restricted formats, see this webpage:  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I hope this document is of some value to people out there who were looking for a "real" desktop on a 2G Surf. (and we all know our choices are very limited)

If anyone has any corrections or suggestions to what I wrote, please PM me and i will make the necessary adjustments, giving you credit. Thanks.

---

