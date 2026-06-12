---
title: "HOW TO: Customize the LiveCD"
date: 2007-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by phenest on 2007-08-02
I have seen the question raised quite a lot on this forum, so I have decided to do a comprehensive tutorial on how to customize the LiveCD.

This will work for Feisty, and for Gutsy too.

This tutorial is actually based on a bash script. I figured typing commands line by line is far to slow, and mistakes can be made. A script simplifies the operation, and can be modified to taste.

I will first provide a basic script that everyone should find useful. The script can be further modified by simply adding lines of code where necessary.

Here's how you do it:

1 - What you need:
Create a new folder called: live
Download the 7.04 (Feisty) desktop iso and place in the live folder.
Download the Flash browser plugin from Adobe: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")
Extract the flashplayer.xpt and the libflashplayer.so files and place in the live folder.
You will also need to install a couple of tools onto your computer to make this whole thing possible:
```
sudo apt-get install squashfs-tools mkisofs
```
These only need to be installed the once, and so don't need to be part of the script.

2 - The basic script:

```
#!/bin/bash

ubuntuiso=ubuntu-7.04-desktop-i386.iso
customiso=ubuntu-7.04-H12Y-v1.iso
kernel=2.6.20-15-generic

clear
echo Customize Ubuntu LiveCD
echo
echo Script by: Stephen Clark
echo Based on documentation found at:
echo https://help.ubuntu.com/community/LiveCDCustomization
echo
echo "For customizing Ubuntu 7.04 (Feisty Fawn)"
echo
echo Press Ctrl C at any time to quit
echo

echo -n "Loading squashfs module... "
modprobe squashfs
echo Done
echo

echo -n "Extract iso contents? y/[n] "
read ua
if [ "$ua" = "y" ]; then
	if [ -e "edit" ]; then
		echo -n "Removing existing Desktop System... "
		rm -r edit
		echo Done
	fi
	mkdir edit
	if [ -e "extract-cd" ]; then
		echo -n "Removing existing CD contents... "
		rm -r extract-cd
		echo Done
	fi
	mkdir extract-cd
	if ! [ -e "mnt" ]; then
		mkdir mnt
	fi
	if ! [ -e "squashfs" ]; then
		mkdir squashfs
	fi
	echo -n "Extracting CD contents... "
	mount -o loop $ubuntuiso mnt
	rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
	echo Done
	echo -n "Extracting Desktop System... "
	mount -t squashfs -o loop mnt/casper/filesystem.squashfs squashfs
	cp -a squashfs/* edit/
	umount squashfs
	umount mnt
	echo Done
fi
echo

# Place custom scripting here

# Initialize networking and sources

cp /etc/resolv.conf edit/etc
cp /etc/hosts edit/etc
cp /etc/apt/sources.list edit/etc/apt

echo -n "Start package removal? y/[n] "
read ua
if [ "$ua" = "y" ]; then
	echo
	# Not all apps can be purged without dependency problems
	# Accept whatever solution aptitude offers
	chroot edit apt-get remove --purge ekiga evolution tomboy serpentine f-spot gnome-games bittorrent onboard gnome-pilot gnome-pilot-conduits libpisock9 libpisync0
fi
echo

echo -n "Start package installation? y/[n] "
read ua
if [ "$ua" = "y" ]; then
	echo
	# -q supresses the output to a minimum
	chroot edit apt-get update -qq
	# sox, vorbis-tools, & mpg123-alsa are for previewing sound files in nautilus
	# The gstreamer packages are for codec support
	chroot edit apt-get install mozilla-thunderbird sox vorbis-tools mpg123-alsa vlc comixcursors gnome-themes-extras gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
	chroot edit apt-get clean
fi
echo

echo -n "Installing Flash plugin for Firefox... "
# Install flash plugins
cp flashplayer.xpt edit/usr/lib/firefox/plugins
cp libflashplayer.so edit/usr/lib/firefox/plugins
echo Done
echo

# Clean up

rm edit/etc/resolv.conf
rm edit/etc/hosts
rm edit/etc/apt/sources.list

if [ -e "extract-cd/programs" ]; then
	echo -n "Remove unwanted Windows applications from LiveCD? [y]/n "
	read ua
	if ! [ "$ua" = "n" ]; then
		echo -n "Removing Windows applications... "
		rm -r extract-cd/programs
		echo Done
	fi
	echo
fi

echo -n "Copying wallpaper... "
if [ -f "edit/usr/share/backgrounds/*.*" ]; then
	rm edit/usr/share/backgrounds/*.*
fi
cp wallpaper/* edit/usr/share/backgrounds/
cp ubuntu-wallpapers.xml edit/usr/share/gnome-background-properties/
echo Done
echo

echo Setting gconf defaults for wallpaper, mouse, theme, nautilus and panel
# Wallpaper
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/01.jpg"
# Mouse
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /desktop/gnome/peripherals/mouse/cursor_theme "ComixCursors-Orange-Large-Slim"
# Theme
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /desktop/gnome/interface/gtk_theme "Nuvola"
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /desktop/gnome/interface/icon_theme "Nuvola"
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /apps/metacity/general/theme "Nuvola"
# Nautilus
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /apps/nautilus/preferences/click_policy "single"
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /apps/nautilus/preferences/desktop_font "Sans Bold 10"
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/nautilus/preferences/start_with_sidebar "false"
chroot edit gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/nautilus/icon_view/default_use_tighter_layout "true"
echo

# End of custom scripting

# Putting the CD together

echo -n "Recompile iso? [y]/n "
read ua
if [ "$ua" = "n" ]; then
	echo
	echo The End
	echo
	exit
fi

echo Compressing filesystem
if [ -e "extract-cd/casper/filesystem.squashfs" ]; then
	rm extract-cd/casper/filesystem.squashfs
fi
mksquashfs edit extract-cd/casper/filesystem.squashfs
echo

echo -n "Removing old md5sum.txt and calculating new md5 sums... "
rm extract-cd/md5sum.txt
(cd extract-cd && find . -type f -print0 | xargs -0 md5sum > md5sum.txt)
echo Done
echo

echo Creating iso
if [ -f "$customiso" ]; then
	echo -n "Removing old custom iso... "
	rm $customiso
	echo Done
	echo
fi
cd extract-cd
mkisofs -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../$customiso .
echo

echo The End
echo
```

Open Gedit and paste this code in. Save file as: customize-livecd.sh and place in your live folder.
To run the script, open a terminal and type:
```
sudo sh ./customize-livecd.sh
```
The first time round, you will answer yes to all questions. After that, you can respond with no to save time extracting the iso again (unless you want to clean things up).

3 - A brief explanation:

The first thing the script does is to load the squashfs module. This is necessary for the extraction/compression process to work.
Then it asks whether to extract the iso contents. If you want to start a fresh customization, answer yes. Answering no will save time having to extract everything from the iso again.
There are 3 lines that copy your network settings and the sources.list to enable downloading of packages to the extracted iso.
Then follows package removal and installation. Again, you can answer no to save time if you have already done it. Adjust the packages to be removed or installed to taste.
Then your Flash plugin for Firefox will be copied over.
There are some Windows application on the LiveCD which don't serve much purpose, so they can be removed too making a bit of room.
The next section is for copying any wallpaper over. If you don't want this, delete these 7 lines. If you do, create a folder in the live folder called wallpaper. Copy any wallpaper you want into this folder. If you wish to have these show up in the Desktop Background applet, you can customize the ubuntu-wallpapers.xml and add them. You can find this file in /usr/share/gnome-background-properties/. Make a copy of the ubuntu-wallpapers.xml file into the live folder and alter this copy instead. This will have to be modified by hand using Gedit before running the script. It's quite obvious how to alter the xml file once you've opened it.
The next few lines are for modifying some settings that you can find using the Configuration Editor. It gives you an idea of how to create your own default settings. This can be extended to just about everything you find in the Configuration Editor including setting up a complete customized desktop and panel(s).
Now we come to the part where the whole thing will be put back together and create a new iso.
At the very beginning of the script, you will notice 3 variables. ubuntuiso is the name of the Ubuntu iso you downloaded. customiso is the name of the new iso you will create from this script. kernel is the kernel used in the iso you downloaded. If you're customizing Gutsy, it will be 2.6.22-7-generic.

4 - There are some laptop owners having problems booting the LiveCD due to driver problems. I personally own a Philips X56 which has this exact problem. So, for anyone with a Philips freevents X56, Twinhead H12Y, Avaretec 2460, or Everex Stepnote SA2050, this is the fix:
EDIT: Ubuntu 7.04 ships with the 2.6.20-15-generic kernel. Arne.F informs me you need the correct module version available here:
[http://www.fitzenreiter.de/averatec/8139too.ko]("http://www.fitzenreiter.de/averatec/8139too.ko")
Copy this to the live folder. Add these few lines to the script:
```
# Patch for Twinhead H12Y notebooks
echo -n "Install patch for $kernel kernel? y/[n] "
read ua
if [ "$ua" = "y" ]; then
	echo 8139too PIO from: http://www.fitzenreiter.de/averatec/index-e.htm
	echo -n "Removing SDHCI and replacing 8139too MIMO to PIO... "
	sdhci=edit/lib/modules/$kernel/kernel/drivers/mmc/host/sdhci.ko
	too=edit/lib/modules/$kernel/kernel/drivers/net/8139too.ko
	if [ -f "$sdhci" ]; then
		rm $sdhci
	fi
	if [ -f "$too" ]; then
		rm $too
	fi
	cp 8139too.ko $too
	echo Done
	echo
	echo -n "Rebuilding initrd... "
	chroot edit mkinitramfs -o /initrd.gz $kernel
	mv edit/initrd.gz extract-cd/casper/
	echo Done
fi
echo
```
... just before the line that reads: # End of custom scripting. Bear in mind that any updates to the kernel will also have to be patched. After installation, any new kernels can be patched using the patch you just download and extracted. Follow the instructions within.

That's about it.

Please post any comments/question here for all to read, and I will keep this updated as questions arise.

---

### Post by frodon on 2007-08-02
How is this different from what reconstructor do ?
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

---

### Post by phenest on 2007-08-02
Reconstructor doesn't appear to be open source. Some would like to know how it works. Scripts offer much greater flexibility.

---

### Post by frodon on 2007-08-03
> Reconstructor is written in python and is licensed under the GNU General Public License (GPL). I think it is is open source but yeah getting knowledge to do the things with a custom script is always better or offers way more flexibility, advanced users will surely prefer the way described in your post :)
However i think some beginners will prefer reconstructor for understandable reasons (it is a GUI).

---

### Post by phenest on 2007-08-03
I couldn't find the source to download, so it's a bit of an assumption that it's not open source.

I totally agree that the script method is for advanced users or for those wishing to learn. I did try Reconstructor myself but, being a programmer, I had to find my own way of doing it.

I would like to advance the script to a menu system to advance its features further and make it more user friendly, so maybe even a novice could use it. That will still leave it open source so others can learn from it.

---

### Post by golem3 on 2007-08-03
> **frodon said:**
> How is this different from what reconstructor do ?
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

Thanks for the tip. I will see if this works on the newest oversized Gutsy build.

---

### Post by Arne.F on 2007-08-14
Hi phenest, nice script. I had used UCK to do this job.

Please change your description. The 8139too.ko file from [http://www.fitzenreiter.de/averatec/h12y-patch-2.6.20-16-generic.tgz](http://www.fitzenreiter.de/averatec/h12y-patch-2.6.20-16-generic.tgz)
is not the correct one for Kernel 2.6.20-15 that was used on the 7.04 cd.

[http://www.fitzenreiter.de/averatec/8139too.ko](http://www.fitzenreiter.de/averatec/8139too.ko) is the korrekt one for 2.6.20-15-generic.

This modul is different for every kernel version.

---

### Post by phenest on 2007-08-14
> **Arne.F said:**
> Please change your description. The 8139too.ko file from [http://www.fitzenreiter.de/averatec/h12y-patch-2.6.20-16-generic.tgz](http://www.fitzenreiter.de/averatec/h12y-patch-2.6.20-16-generic.tgz)
is not the correct one for Kernel 2.6.20-15 that was used on the 7.04 cd.

Er, that may be true, but that module worked for me in both the 2.6.20-15 and 2.6.20-16 kernels.

---

### Post by az on 2007-08-14
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
and my personal favorite:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

The former is a well-maintained howto that starts from an Ubuntu live cd.  The latter starts from nothing - you build it from scratch.

---

### Post by phenest on 2007-08-14
> **az said:**
> [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
and my personal favorite:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

The former is a well-maintained howto that starts from an Ubuntu live cd.  The latter starts from nothing - you build it from scratch.

No dis-respect to anyone, but my script method is quite possibly far easier to modify and/or understand for both newbie and power user.

Also, my script is based on the 1st link (as mentioned). I wasn't aware of the 2nd.

---

### Post by az990tony on 2007-09-03
Phenest,
Thanks for the script.  I have customized it for myself and posted my version here:

[http://www.990tony.com/ubuntu/download.html](http://www.990tony.com/ubuntu/download.html)

I don't understand why you "rm edit/etc/sources.list"?  The original ISO has one, and probably should exist on the new CD as well.  I comment those lines out.

My modified version is to address the fact that my co-workers are afraid to run LiveCD in that they might accidently install over their Windows system.  I updated the isolinux.cfg and removed the ubiquity apps to eliminate that fear.

For those looking for a no-install LiveCD.  Here you go.

---

### Post by phenest on 2007-09-03
I never thought of a "no install" LiveCD. Nice idea.

Also, thanks for the mention on your website. I must get a site of my own sorted out.

---

### Post by darkmaster on 2007-10-13
Anyone, I've got a problem in the Live cd customization. I'd like to be able to change username and password of the Live CD but I can't understand how to make it. Reconstructor can't do it with Gytsy Gibbon, dunno why. Any idea of how can I do it?

---

### Post by phenest on 2007-10-14
The only thing I can point you to at the moment is: [LiveCD customization]("https://help.ubuntu.com/community/LiveCDCustomization")

It's not something I've tried to do.

---

### Post by darkmaster on 2007-10-14
> **phenest said:**
> The only thing I can point you to at the moment is: [LiveCD customization]("https://help.ubuntu.com/community/LiveCDCustomization")

It's not something I've tried to do.

I know this, I read it all. There's no mention about my problem :(

---

### Post by theyain on 2007-11-03
> **az990tony said:**
> Phenest,
Thanks for the script.  I have customized it for myself and posted my version here:

[http://www.990tony.com/ubuntu/download.html](http://www.990tony.com/ubuntu/download.html)

I don't understand why you "rm edit/etc/sources.list"?  The original ISO has one, and probably should exist on the new CD as well.  I comment those lines out.

My modified version is to address the fact that my co-workers are afraid to run LiveCD in that they might accidently install over their Windows system.  I updated the isolinux.cfg and removed the ubiquity apps to eliminate that fear.

For those looking for a no-install LiveCD.  Here you go.


Actually what you did was pretty intelligent.  Next time SFD (Software Freedom Day) comes around I will have to have a bunch of those for people who just want to try it out.

---

### Post by phenest on 2008-03-26
I've been trying to set my default keyboard layout on the Live CD to Dvorak. Has anyone had success doing this?

I edited 2 files:
/etc/default/console-setup
/etc/X11/xorg.conf (changed in //usr/bin/dexconf)
... but X and the console continue with Qwerty.

Anyone have any ideas?

---

### Post by sh4d0w808 on 2008-04-05
phenest, I have downloaded tha flashplayer archive but there are only two files: the installer and the so-file, there is no xpt. How can I get that one?

---

### Post by phenest on 2008-04-05
> **sh4d0w808 said:**
> phenest, I have downloaded tha flashplayer archive but there are only two files: the installer and the so-file, there is no xpt. How can I get that one?

Have you tried it with just the .so file?

---

### Post by sh4d0w808 on 2008-04-07
Yes, after my post i made some search by Google and i saw that the other file belongs to flash version 7.

I had run your script (by the way: great work!), but during the boot-up of the new iso, there was a freeze.

---

### Post by strider5236 on 2009-04-06
How is it going guys. I want to first thank you for your script. I have modified it for my personal use and it has been a life saver. One problem I would like some help with is the changing of the default Ubuntu usplash. I want to incorporate my own. It works after I install the CD but not during the boot up of the Live Installer. Any help would be greatly appreciated.

This is what I added to change the usplash

echo -n "Change default usplash to Stoner_Edition_x32? y/[n] "
read ua
if [ "$ua" = "y" ]; then
	echo
	# -q supresses the output to a minimum
        chroot edit update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/Stoner_Edition_x32.so 10
        chroot edit update-alternatives --config usplash-artwork.so
        chroot edit update-initramfs -u
fi
echo

What I did is copy my usplash into the /home/stoner/test/edit/usr/lib/usplash/

The command works and changes usplash-artwork.so with my usplash and all but is not there when I boot up the Live disk. Very strange and I am not sure if fully understand what is needed to change this?

---

### Post by strider5236 on 2009-04-06
Scratch the above question as I have answered if for myself. The trick was I needed to edit the init.gz and replace the default.so file within it. The above code works for replacing the system usplash. I hope this helps some one else that may have had the same issue as I.:guitar:

---

### Post by phenest on 2009-06-27
I haven't played with this for a while and now I have a problem. I thought about customizing the Karmic Alpha 2 iso, but I can't even modprobe squashfs:
```
steve 17:44: ~/live $ sudo modprobe squashfs
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
steve 17:50: ~/live $ 

```
I'm doing this from Jaunty.

---

### Post by phenest on 2009-06-27
> **strider5236 said:**
> Scratch the above question as I have answered if for myself. The trick was I needed to edit the init.gz and replace the default.so file within it. The above code works for replacing the system usplash. I hope this helps some one else that may have had the same issue as I.:guitar:

I only copied a new splash.pcx (edited with GIMP) into the extract-cd/isolinux folder. That's good for the LiveCD, but I can't remember whether that's copied to an installation.

If anyone knows how you update the kernel on the LiveCD, please post it here. Thanks.

---

### Post by jhahoneyk on 2009-09-27
I tried to customize the CD to include more apps which are generally used. Now, if I use the LiveCD to install, all MP3s are started in Audacity by default. I want to change it back to Amarok. So, in  general I want to set default applications in the custom ISO.
Where are the config files for this? Most probably they'll be there in the home dir of the user after a install. But, how do I change those files while customizing ?
Thanks :)

---

### Post by senrabdet on 2010-11-17
I was wondering if Phenest was still involved in LiveCD customization.  I wanted to circle back on the question about adding users to the customized CD to avoid that part of the LiveCD install, as well as possibly importing some Gconf values for printers and networks.

---

### Post by zeigerpuppy on 2011-03-01
I have built a USB live Ubuntu 10.10 install which I can use on work computers.  I am now trying to secure it a bit more.
I disabled auto login, created a new user with encypted home, changed sudo settings to something more sane and changed the ubuntu and root passwords.

However, there is still one major insecurity which is that the ubuntu user 
is automatically logged in to virtual consoles (try ctrl-alt-F2).
How do I disable this behaviour???

I'll post/modify a howto once I get this customised, there's a few features steps not covered in the existing help docs.

---

