---
title: "UbuntuStudio Hardy 32-bit on the Acer Aspire 4520 in 10 easy steps"
date: 2008-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by calraith on 2008-03-25
You will need a wired Internet connection for this part.  Wireless will not be detected during the initial installation.  Grab the Intel x86 alternate install image from [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) and burn it to a DVD.  (DVD-RW will do just fine, and you won't have to throw away your DVD when you want to burn a fresher image.)

[SIZE=3]_**Installation**_[/SIZE]

1. Power on the laptop.  On the Acer logo splash screen, hit F12 to get to the boot device selection menu.  Insert the UbuntuStudio alternate install DVD, select the CD drive, and boot.

2. Choose your language, follow the prompts, and proceed with installation as normal until you reach the "Installation Complete" screen and the CD drive ejects.  [B]DO NOT HIT CONTINUE YET.

[/B] 3. Hit Alt+F2 to get to a console.  Hit Enter to activate the console.

4. Type the following commands:
```
mount -o loop /proc /target/proc
chroot /target /bin/bash
cd /usr/src
wget "http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz"
echo "blacklist pcspkr" | tee -a /etc/modprobe.d/blacklist
echo "deb http://apt.wicd.net hardy extras" | tee -a /etc/apt/sources.list
apt-get update
apt-get install -y --force-yes linux-generic nvidia-glx-new nvidia-settings wicd build-essential
apt-get remove -y linux-image-2.6.24-16-rt
sed -i -r -e '/^# defoptions/s/quiet/vga=791/' /boot/grub/menu.lst
update-grub
grub-install /dev/sda
```5. Hit Alt+F1 and hit enter to reboot.  If your system hangs, just hold Alt+SysRq with your right hand while you peck out the letters r-e-i-s-u-b with your left.

At this point, my system hung once more during the next boot, and again I had to Alt+SysRq and r-e-i-s-u-b.  That was the last time, though.  *shrug*  Could have had something to do with my messing with different combinations of splash and vga= boot settings.  For what it's worth, splash does not like vga=792.

6. Once you have completed booting into UbuntuStudio, click the Restricted Drivers applet icon when it appears in your notification area in the upper right.  If it doesn't appear, the Restricted Drivers manager can also be accessed via the Menu --> System --> Administration --> Hardware Drivers.  Check mark the box for the accelerated graphics driver.  You'll get a message that this will require a reboot.  Don't bother rebooting quite yet.

7. Go to the Menu --> Accessories --> Terminal.  Type the following commands:
```
sudo su
cd /usr/src
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz

##  note: You do know about tab completion, right?  Instead of typing the previous
##  command letter-for-letter, you can simply type "tar -xvzf mad" and hit Tab to auto-
##  complete the rest.  Same goes for the directory name in the next command as well.

cd madwifi-nr-r3366+ar5007
make clean
make install
```8. Before you reboot, go to the Menu --> System --> Preferences --> Sessions.  Add a new startup program as follows:
> Name: Wicd Tray Applet
Command: /opt/wicd/tray.py
Comment: networking applet9. OK, reboot.  When you get back into UbuntuStudio, you'll have a new tray applet for networking.  Single left-click it.  Go to the Preferences tab.  Change the WPA Supplicant Driver to "madwifi" and change the Wireless Interface to "ath0" (without the quotation marks).  Salt any other settings to taste and hit OK.  When you refresh, you should see wireless working.  w00p!

10. See [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) for information regarding tweaking your touchpad.

[SIZE=3]**_Personalizing your system_**[/SIZE]

Go nuts with your new system!  Install Compiz Fusion if you wish[SIZE=1](a)[/SIZE].  Install Conky if you wish[SIZE=1](b)[/SIZE].  Tell your system to quit asking you for a password every time you want to install or tweak something[SIZE=1](c)[/SIZE].  Auto-login without having to enter your password[SIZE=1](d)[/SIZE].  Find a spiffy wallpaper[SIZE=1](e)[/SIZE].  Install webcam software[SIZE=1](f)[/SIZE].

** a. Compiz Fusion (3D effects for your desktop)**

To install Compiz Fusion, install the following package, either via apt-get or Menu --> System --> Administration --> Synaptic Package Manager:
> compizconfig-settings-managerThat's all you need!  You don't need themes.  You don't need emerald.  That package will install everything you need.  Believe it or not, Compiz works fine without Emerald, you don't have the added overhead of having to replace your window decorators, and you can let your GTK themes shine through.  Just go to the Menu --> System --> Preferences --> Appearance.  Click the Visual Effects tab.  Change the setting to Extra, and you're done.  The change is persistent through reboots.  Salt to taste via Menu --> System --> Preferences --> Advanced Desktop Effects Settings.

**b. Conky (system information displayed on the desktop)**

Install Conky via Synaptic Package Manager or apt-get.  Use [my .conkyrc]("http://headcandy.org/rojo/conkyrc") if you wish (save it to your home directory, salt to taste, and rename it to .conkyrc).

** c. Admin rights via sudo without requiring a password**

In a terminal, type the following:
```
sudo nano -w /etc/sudoers
```Append the following to the bottom:
>  your_username ALL=NOPASSWD: ALLHit Ctrl-X then Y to exit and save your changes.

**d. Auto Login on boot**

Go to the Menu --> System --> Administration --> Login Window.  Click the Security tab.  Check mark the box regarding automatically logging in, and select your username in the dropdown list.

** e. Wallpapers**

Right-click on your desktop and choose "Change Desktop Background."  If you don't like any of those, fire up Firefox and visit [http://interfacelift.com](http://interfacelift.com).  Browse the 1280x800 wallpapers.  If you find one you like, click "download," then right-click the picture and choose "Set as desktop background."

** f.  Webcam**

The webcam just works.  All you need is software to use it.  (For instance, install "cheese" either via apt-get or Synaptics Package manager.)

[SIZE=3]_** Notes**_[/SIZE]
[LIST]
[*] The WiFi button between the keyboard and the display hinge will still toggle the wireless radio, even though the indicator showing the radio state does not illuminate in Linux.  If your wireless inexplicably doesn't work or stops working, even if ath0 appears as an interface when you type "iwconfig," try hitting that WiFi button once to turn the radio back on.
[*]Framebuffer is increased to 1024x768 with the VGA=791 line.  This is the best resolution which still supports the UbuntuStudio splash screen.  Removing the "quiet" option provides a tasty text status below the progress meter in the splash screen during takeoff and landing.
[*] I blacklisted the "pcspkr" module because, well, the PC speaker is loud, annoying, startling at times, and not terribly useful if you're not often in console mode.
[*] I prefer Wicd over Gnome's default nm-applet for a few reasons.  It's on the whole a little more intuitive to configure, it doesn't prompt you for a password to connect to an encrypted network (which is nice when a technophobic wife occasionally wants to use the laptop), and it seems to handle 802.1x / LEAP well.
[*] Whenever you install a new kernel and reboot, wireless will break again (at least until ath5k is not so experimental and Debian and Ubuntu bring it to the mainstream).  You'll need to pop open a terminal, cd /usr/src/madwifi-nr-r3366+ar5007, sudo make clean, sudo make install, and reboot again.
[*] By no means do I claim that this is the best way to set up Hardy on an Acer Aspire 4520.  But it's my way, and it makes me happy.
[*] Not tested: microphone, bluetooth
[/LIST]

---

### Post by caravena on 2008-03-30
@calraith:
* You test 64bits?
* MadWifi work with 64bits?

---

### Post by calraith on 2008-03-30
> **caravena said:**
> @calraith:
* You test 64bits?
* MadWifi work with 64bits?

I haven't tested with 64-bit, but I do believe I read on the madwifi website that that patched set of kernel modules is 32-bit only.

---

### Post by caravena on 2008-03-30
> **calraith said:**
> I haven't tested with 64-bit, but I do believe I read on the madwifi website that that patched set of kernel modules is 32-bit only.
Ok- > [http://madwifi.org/ticket/1679#comment:120]("http://madwifi.org/ticket/1679#comment:120")

Thanks for response. Other question:
* You video card detect automatic in Hardy Heron?, resolution default is 1280x800. Not problem with video card?

---

### Post by calraith on 2008-03-31
> **caravena said:**
> Other question:
* You video card detect automatic in Hardy Heron?, resolution default is 1280x800. Not problem with video card?

Steps 4 and 6 in the howto take care of the video driver.  Installing nvidia-glx-new and activating it through the Restricted Drivers Manager will enable 1280x800 resolution and glx acceleration without your having to edit xorg.conf manually.  Before activating nvidia-glx-new, the display only runs at 800x600 if I recall correctly.

---

### Post by vwest87 on 2008-04-20
I've got an Acer Aspire 5570 and it has the same basic hardware with the exception that the graphics card is the intel 945, and hardy recognizes it normally so what would I leave out of this guide to not install the nvidia specific things?

---

### Post by calraith on 2008-04-20
> **vwest87 said:**
> I've got an Acer Aspire 5570 and it has the same basic hardware with the exception that the graphics card is the intel 945, and hardy recognizes it normally so what would I leave out of this guide to not install the nvidia specific things?

I don't know whether you'll need step 6 or not.  In any case, I'd say just modify step 4 as follows:
```

mount -o loop /proc /target/proc
chroot /target /bin/bash
cd /usr/src
wget "http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz"
echo "blacklist pcspkr" | tee -a /etc/modprobe.d/blacklist
echo "deb http://apt.wicd.net feisty extras" | tee -a /etc/apt/sources.list
apt-get update
apt-get install -y linux-generic wicd build-essential
apt-get remove -y linux-image-2.6.24-16-rt
update-grub
grub-install /dev/sda
```I took out not only the nvidia driver installation, but also the VGA mode change in /boot/grub/menu.lst.  Since I can't test the mode change, it's probably safer to leave it out.  If you'd like to play around with changing the console mode, re-add the following steps:
```

sed -i -r -e '/^# defoptions/s/quiet/vga=791/' /boot/grub/menu.lst
update-grub
grub-install /dev/sda
```You might also need to use a utility such as [915resolution]("http://www.geocities.com/stomljen/") to get X to display correctly.  If you get it working, I'd be interested to know what you had to do.  Good luck!

---

### Post by pockie on 2008-07-31
I know this is an old thread, but I have been trying to install Ubuntu Studio Gutsy on my 4520 lately with many issues. I haven't tried your approach, but I see that it doesn't address sound. Does this mean that Studio 8.04 supports my sound card out of the box? If so, do you think this is true for 7.10? (Another) If 7.1 doesn't have it working, will an update make it start working?

---

### Post by calraith on 2008-07-31
> **pockie said:**
> I know this is an old thread, but I have been trying to install Ubuntu Studio Gutsy on my 4520 lately with many issues. I haven't tried your approach, but I see that it doesn't address sound. Does this mean that Studio 8.04 supports my sound card out of the box? If so, do you think this is true for 7.10? (Another) If 7.1 doesn't have it working, will an update make it start working?

Sound does indeed work out of the box on 8.04.  I think it works out of the box on 7.10 but I wouldn't swear by that.  I've slept and drunk beer since Gutsy.

Have a look at the page I've been maintaining on the [Ubuntu Wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire4520") for a list of hardware that does / does not work on the 4520.  Feel free to make changes to it if you get to test any of the components marked as "untested," or if your mileage otherwise varies.

---

### Post by pockie on 2008-08-01
I hate to be a bother, and it could be because I only have 7.10, but as you predicted, my system doesn't boot. No matter how many times I do a ALT+SysRq REISUB, I get a blinking cursor. 

Any ideas?

---

### Post by calraith on 2008-08-01
> **pockie said:**
> I hate to be a bother, and it could be because I only have 7.10, but as you predicted, my system doesn't boot. No matter how many times I do a ALT+SysRq REISUB, I get a blinking cursor. 

Any ideas?

The kernel version numbers are different from version 7.10 to 8.04.  Whatever kernel version is appropriate to 7.10, did you remove the -rt kernel and install -generic when you installed nvidia-glx-new?

Another idea, although not necessary for a completed install, it helps to troubleshoot if you take the "splash" and "quiet" parts out of the kernel options, so you can see any error messages / kernel panics during the boot process.  You can either do this by modifying /boot/grub/menu.lst (sudo nano -w /boot/grub/menu.lst) and reinstalling grub (sudo grub-install /dev/sda), or by hitting Esc as grub displays "hit esc for boot menu" or whatever and modifying the kernel parameters at boot time.  Getting rid of the Ubuntu splash screen is not a fix, but it could reveal what needs to be fixed.

---

