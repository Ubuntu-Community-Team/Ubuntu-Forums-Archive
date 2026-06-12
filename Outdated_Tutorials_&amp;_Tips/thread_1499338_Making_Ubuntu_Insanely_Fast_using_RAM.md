---
title: "Making Ubuntu Insanely Fast using RAM"
date: 2010-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by terminator14 on 2010-06-01
[B][COLOR="Red"][SIZE="4"]Although this howto still works for the main part, an updated version of it in the form of a script (greatly simplified) can be found here: 
[http://ubuntuforums.org/showthread.php?t=1594694]("http://ubuntuforums.org/showthread.php?t=1594694")[/SIZE][/COLOR][/B]

**[SIZE="4"]What this guide will try to accomplish[/SIZE]**

I will try to update and expand upon the guide written by capink [here]("http://ubuntuforums.org/showthread.php?t=707230") back in 2008. The guide basically explains how to create a squashfs image out of your existing Ubuntu installation and copy the entire image to RAM upon boot to speed up your OS. I will also go into some detail of how to make your /home mount from a regular hard drive thereby making sure the important information one would wish to save on their machine would remain untouched between boots.

**[SIZE="4"]A little history[/SIZE]**

I have always been fascinated with the idea of speeding up an OS by the non-conventional way of providing a faster medium from which it runs. I call this non-conventional because I use to think (and I believe many people still do) that just by buying faster and faster processors that my computer would keep speeding up more and more. Although this is the case to some degree, after purchasing my QX9650 a few years back and not seeing as much of a difference as I would have hoped, I realized there had to be something else that was slowing my computer down.

That's when I found out about SSDs. I've read much about them, and finally a few months ago got my first SSD - an X25-M 160GB Intel SSD. Installing my Windows 7 on it, I realized how insanely fast this made it run. Everything just seemed to open instantly. All my games loaded instantly. This was what I had been looking for to speed up my OS.

Unfortunately the downside of this was that the speed of my Windows 7 now made my Ubuntu 10.04 feel slow. The first thought that came to mind was of course to create another partition on the large, 160GB SSD and move my Ubuntu there. In order to maintain the SSD's fast speeds however, TRIM was required. TRIM is something that keeps an SSD running at its top speed. Without it, an SSD will slowly slow down while being used. TRIM is built into Windows 7, so I had no problems with my SSD in Windows, but, from what I've read, TRIM did not make it into the kernel Lucid uses by 1 day. 

I had a choice here. I could either find the patched kernel that included TRIM support, and replace my existing kernel with it (messing with the kernel is something I've never done as I've never had the need to), or I could take the opportunity to make my Ubuntu work even faster than the SSD could allow.

One of the first Linux distributions I tried was knoppix. Knoppix had (and probably still does) an amazing feature called "toram". The way you would use this is simply add the string "toram" to the boot line when knoppix was starting from the cd and the entire knoppix CD would be copied into your RAM before being run. Now even though this took a while (about a minute in most cases), the advantage to this was that this made knoppix run insanely fast. Which brings me to the reason why you would want to do this:

[SIZE="4"]**Why do this?**[/SIZE]

Looking at the DDR2 page of wiki, it is clear the advantage RAM has over regular hard drives. Something as cheap as DDR2-533, something you could easily obtain an extra 1 GB of for about $30, has roughly a speed of 4266 MB/s. Compared to a regular 100MB/s hard drive, that's 42 times faster. If you have a slightly more expensive system that supports faster RAM (I have 6GB of DDR2-1066 RAM), the speed of the RAM can be up to 8533 MB/s. Imagine every file your operating system requests to read or write being served up at that speed!

[SIZE="4"]**Who should do this?**[/SIZE]

What this will do is basically remove (or at least significantly decrease) the conventional hard drive as a bottleneck for computing. That means your processor will likely be the next in line to be the bottleneck. If you have a slow processor (anything below dual core I would imagine) than this will likely not help you as your processor won't be fast enough to take advantage of the speed increase and the trouble of setting this up and maintaining it would not be worth the slight (if any) increase in performance.

You also need enough RAM to pull this off. I would guess that you would need at least [S]2GB[/S] 3.5GB to fit the entire Ubuntu Lucid 10.04 OS into your RAM and have RAM left over to work with. As RAM is cheap these days, this should not be too much of a problem for most people. I have 6GB so I've had no problems running out so far and do not plan to have any in the future. You could of course use less RAM (eg 2GB), but that would require you to keep a close eye on your free space, or remove packages from Ubuntu that you do not use to decrease its size (like Open Office). If you are curious why the sudden change from my initial estimates, this is mainly due to the recently discovered inaccuracy of System Monitor in telling the used/free RAM. See the "Possible Reason for Slowdown" section of this howto at the bottom for more info.

You will also need at least an intermediate knowledge of linux. A beginner might be able to do this with a little reading into the concepts being used here but will more than likely get lost.

[SIZE="4"]**Lets Begin**[/SIZE]

The following is an almost word for word copy and paste of capink's original post (link above). This is because many of the steps he wrote about in 2008 are still relevant today. To keep this from being half quotes and half not quotes, effectively destroying formatting, I will not put the sections that came from him in quotes. I will however make them red, while my additions will be black.

[COLOR="Red"]The main idea and the general principles are similar to the original [wiki on how to boot Ubuntu to RAM]("https://wiki.ubuntu.com/BootToRAM"). But this guide has some differences to the original wiki:

   1. Rather than using a live CD, we will use the system installed on your harddisk as the basis of the image we will create.
   2. This guide uses live-initramfs instead of casper. This is because live-initramfs is present in both Ubuntu and Debian so that guide can serve wider audience. For those who want to use casper instead it should work the same but I have not tested it, you will just need to replace live-initramfs with casper and /live with /casper.
   3. No editing of the boot scripts as live-initramfs introduced an option to boot from ram automatically.
   4. Unlike the method of the original wiki, using this method all your partitions are going to be mounted automatically exactly as they are mounted when you boot your normal system, with the exception of the root partition.

Note: Since the system is going to be copied to RAM, the boot process takes slightly longer time.[/COLOR] For those of you with an SSD, I will explain how to copy the image to a partition on the SSD to speed this up a bit.

[COLOR="Red"]N.B This guide works only for Ubuntu gutsy and Debian lenny or later.[/COLOR] I have tested this only with Ubuntu Lucid 10.04. You may need to modify a few things to get it to work with other versions of Ubuntu.

NOTE: Although I will cover a way to make the data on your desktop and in your home folder (the entire /home) remain after a reboot, anything you install or configure (with a few exceptions) will be lost after a reboot! This guide also deals with partitioning your disks and formatting them. This can also destroy data if not done carefully. Proceed with caution.

[COLOR="Red"][SIZE="4"]**Requirements**[/SIZE]

Enough RAM. How much depends on the size of the squashfs image we are going to create from the installed system. A system that is 1.5 G in size will create roughly a 500 M squashfs. Since this 500 M is going to be copied to RAM, your RAM must be larger than 500 M, at least by an additional 256 M of RAM (Amount of RAM required = squashfs size + at least 256 M). But to work comfortably in the previous scenario it is recommended to have 1 G or more of RAM.

If you have a swap partition (which you should since you already have a copy of Ubuntu installed), The system will fall back to it when the RAM gets full. But this will severely limit the speed of the system which defeats the purpose of this guide.


You also need enough harddisk space. At least double the amount taken up by your system.

Note: A command to know how much space is taken up by your system:[/COLOR]

```
sudo du -hcs --one-file-system / --exclude=/dev/* --exclude=/tmp/* --exclude=/sys/* --exclude=/proc/* --exclude=/home/*
```

[COLOR="Red"]The process:


1. Install some essential packages:

live-initramfs is present in the universe section of the repository. You must first enable universe repository before attempting to install the package. Here is guides to enable universe ([Ubuntu GUI]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096"), [Kubuntu GUI]("http://linux.about.com/od/kubuntu_doc/a/kubudg22t04.htm"), [CLI]("https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0")).

```
sudo apt-get update
```

```
sudo apt-get install live-initramfs squashfs-tools
```
[/COLOR]

Note: the 'linux-ubuntu-modules-$(uname -r)' from capink's guide can no longer be found in the Lucid repos and is not necessary, so it has been removed.
Also, if you have casper installed, you may have to remove it for live-initramfs to install properly (thanks to CarloMagno for the tip).

If you run into problems (especially in Jaunty) where apt exits with a message similar to:

```
update-initramfs: Generating /boot/initrd.img-2.6.28-19-generic
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-19-generic
dpkg: subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

run:
```
gksudo gedit /usr/share/initramfs-tools/hooks/live
```

and change the line that reads:

> copy_exec /usr/bin/udevinfo /bin

to

> copy_exec /sbin/udevadm /bin

also add the line:

> copy_exec /usr/bin/du /bin

to the file. Save and exit gedit.

then run:

```
sudo dpkg --configure -a
```

Thanks to happyhamster for the tip.

[COLOR="Red"]2. Update the kernel modules dependencies:

```
sudo depmod -a
```

3. Update the initramfs

```
sudo update-initramfs -u
```

4. Copy your filesystem to temporary directory [/COLOR](go get yourself a cup of coffee once you do this since this could take a few minutes)

[COLOR="Red"]```
DEST=/var/squashfs
```

```
sudo mkdir -p ${DEST}
```

```
sudo rsync -av --delete / ${DEST} --one-file-system \
--exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* \
--exclude=/sys/* --exclude=/boot/* \
--exclude=/home/* --exclude=/etc/mtab \
--exclude=/live --exclude=${DEST}
```

Note: You can replace /var/squashfs with any path you wish. Just make sure that it have enough space.[/COLOR]

5. The home directory

The home directory is the location where your Desktop, Music, Pictures, and user specific settings are kept. The main idea behind this guide is that in linux, the home directory is modified frequently, such as when you save files to your desktop, add mp3s to your collection or even modify programs like firefox, evolution, pidgin, or the like which creates files to store those settings in your home directory. The rest of the system however is rarely modified where the modifications are vital. This is why keeping the /home directory on a non-volatile storage medium will in most cases keep your files and settings between reboots, while the speed of the RAM which the rest of the system will reside upon will give you a much needed boost. Of course this means that things like system updates, log files, and settings stored in /etc will not survive a reboot, but I will show you how to deal with this below.

To move the home directory, you must first create a new partition where it will reside:

```
sudo apt-get install gparted
gksudo gparted
```

Note: Be careful with this tool as you can seriously damage your system by wiping out Linux or Windows completely if you start formatting things you shouldn't be.

Using gparted, create a new partition using some free space somewhere on your hard drives. In most cases, you will not have any unallocated space to create such a partition. In this case, you will first have to find your linux partition, and resize it by taking some space from the end of it. Because you are working from within the linux located on this partition, you may first have to boot into a live cd and launch gparted from there in order to resize your linux partition. You can also use a usb drive to store your /home partition but you would need to remember to always have it pluged in when booting into your Ubuntu.

You will need this partition to be as big as you expect to use up with the files that will be on your desktop, your music folder, pictures, and anything else in your home directory. I recommend at least 5GB.

You will also be asked which file system to use for this partition. I recommend ext4 as it is the latest and greatest, or ext3 if you would rather have stability and peace of mind (ext4 originally had some issues that kept people from adopting it - I think they have been worked out since then though).

Take note of the device this partition is using (eg. /dev/sda3). You will need this later.

Once you have created the new partition, mount the device:

```
sudo mkdir -p /mnt/home
sudo mount [COLOR="DarkOrange"]/dev/sda3[/COLOR] /mnt/home
```

Change [COLOR="DarkOrange"]/dev/sda3[/COLOR] to the one in your case. Then run:

```
sudo cp -a /home/* /mnt/home/
```

to copy everything you have in your /home to the new partition that will contain your /home. The -a will preserve the file permissions and ownership.

[COLOR="Red"]6. Modify fstab of the copied filesystem
```
gksudo gedit ${DEST}/etc/fstab
```

delete the entry of the root directory. It should look like this:

```
UUID=.....      /         ext3    defaults,.... 0       1
```
[/COLOR]

To use the partition that we created in step 5 as our /home, add a line similar to the following:

```
[COLOR="DarkOrange"]/dev/sda3[/COLOR]	/home	[COLOR="Olive"]ext4[/COLOR]	auto	0 0
```

Change [COLOR="DarkOrange"]/dev/sda3[/COLOR] to the device you took note of in step 5, and [COLOR="Olive"]ext4[/COLOR] to the type of filesystem you created in step 5 (likely either ext4 as above, or ext3).

After finishing with that, save the file and close gedit.

[COLOR="Red"]7. Clean some unnecessary files

Delete some files under ${DEST}/var

```
[ -n "$DEST" ] && sudo find ${DEST}/var/run ${DEST}/var/mail ${DEST}/var/spool ${DEST}/var/lock ${DEST}/var/backups ${DEST}/var/tmp -type f -exec rm {} \;
```

Delete only OLD log files:

```
[ -n "$DEST" ] && sudo find ${DEST}/var/log -type f -iregex '.*\.[0-9].*' -exec rm -v {} \;
```

```
[ -n "$DEST" ] && sudo find ${DEST}/var/log -type f -iname '*.gz' -exec rm -v {} \;
```

Clean current log files:

```
[ -n "$DEST" ] && sudo find ${DEST}/var/log -type f | while read file; do echo -n '' | sudo tee $file; done
```[/COLOR]

Note the small difference from the original command by capink which prevents the extra newline created in log files.

[COLOR="Red"]Clean Pakcage cache:[/COLOR]

```
[ -n "$DEST" ] && sudo rm -v ${DEST}/var/cache/apt/archives/*.deb
```

[COLOR="Red"]8. Create the squashfs image

The squashfs image must reside in /live[/COLOR]

```
sudo mksquashfs ${DEST} /live/filesystem.squashfs -noappend -always-use-fragments
```

[COLOR="Red"]Examine the size of the image and make sure it is less than the size of your RAM.[/COLOR]

```
sudo du -h /live/filesystem.squashfs
```

9. Add a new entry to Grub

If you are using regular grub (the old grub), than capink's instructions will probably work for you. If however you are using Grub2, which comes default in Lucid, skip to the grub2 section.

[SIZE="3"]**Grub:**[/SIZE]

[COLOR="Red"]Add a new entry to /boot/grub/menu.lst of your main system
```
gksudo gedit /boot/grub/menu.lst
```

Copy the entry of your main system and modify it to look exactly like this:[/COLOR]

```
title		RAM Session
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		[COLOR="Blue"]/boot/vmlinuz-$(uname -r)[/COLOR] [COLOR="Red"]BOOT=LIVE boot=live toram username=[COLOR="DarkOrchid"]user[/COLOR] nosudo noxautoconfig noautologin quickreboot[/COLOR] ro quiet splash
initrd		[COLOR="Blue"]/boot/initrd.img-$(uname -r)[/COLOR]
```


[COLOR="Red"]The text highlighted in [COLOR="Blue"]blue[/COLOR] should match the corresponding parts of your main system entry.
Replace [COLOR="DarkOrchid"]user[/COLOR] with your account username.
The parts highlighted in Red are essential.
[/COLOR]

[SIZE="3"]**Grub2:**[/SIZE]

This is probably the biggest change since capink's guide. Since 2008, Grub2 has become Ubuntu's default, and it works a little differently from Grub. To create the menu entry for your RAM session using grub2 do the following:

Create a file called 50_RAMSESS in your /etc/grub.d/ folder.

```
gksudo gedit /etc/grub.d/50_RAMSESS
```

The file should read something very similar to:

```
#!/bin/sh -e

cat << EOF

menuentry "Ubuntu, Linux $(uname -r) to RAM" {
set root='[COLOR="DarkOrange"](hd0,1)[/COLOR]'
linux /boot/vmlinuz-$(uname -r) boot=live toram=filesystem.squashfs apparmor=0 security=""
initrd /boot/initrd.img-$(uname -r)
}
EOF
```

Where [COLOR="DarkOrange"](hd0,1)[/COLOR] is the location of your Ubuntu installation.

Save the file and exit gedit. Run:

```
sudo chmod a+x /etc/grub.d/50_RAMSESS
```

to make the script executable and:

```
sudo update-grub2
```

to update the grub menu.

[COLOR="Red"]10. Reboot and choose the RAM Session from your boot menu.[/COLOR]

It will take a few seconds or minutes to copy the squashfs image into your RAM, after which, the system will boot and you will be able to use it at incredible speeds.

**[SIZE="4"]Speeding up boot using an SSD[/SIZE]**

If you are fortunate enough to have an SSD (for your Windows 7 for example because this obviously can't be done in Windows), you can speed up the boot process by copying the squashfs image onto a partition on the SSD. Since the SSD is faster than a regular hard drive, your system will copy the image into RAM during boot at far greater speeds (with an X25-M, I can copy the ~1.5GB image in about 10 seconds at 160MB/s, about 3 times faster than from my regular 7200RPM WD hard drive at about 50MB/s).

To do this, resize whatever partition is currently on your SSD. If it's Windows, you may want to do the resize with Windows tools such as those provided by Paragon or Acronis as they will properly inform Windows of the change, something I don't think gparted does - though I could be wrong. All you need is a partition big enough to fit your squashfs image. If you have plenty of space on your SSD, a 5GB partition should do. If not, try 3GB. 

I formated my partition as ext4 but you could probably get away with ext3 if you like. 

Make a folder on the newly created partition on your SSD in the root of the drive (don't make it in any subfolders) and call the folder "live". 

Copy your /live/filesystem.squashfs to this folder. You will need to repeat this whenever you update /live/filesystem.squashfs.

Modify your /etc/grub.d/50_RAMSESS on your Lucid (NOT ON THE RAM IMAGE OR /var/squashfs) to read:

```
#!/bin/sh -e

cat << EOF

menuentry "Ubuntu, Linux $(uname -r) to RAM" {
	set root='[COLOR="Sienna"](hd0,2)[/COLOR]'
	linux [COLOR="DarkOrange"](hd0,1)[/COLOR]/boot/vmlinuz-$(uname -r) boot=live toram=filesystem.squashfs apparmor=0 security=""
	initrd [COLOR="DarkOrange"](hd0,1)[/COLOR]/boot/initrd.img-$(uname -r)
}
EOF
```

Where [COLOR="Sienna"](hd0,2)[/COLOR] should now point to your newly created 5GB partition on your SSD, while [COLOR="DarkOrange"](hd0,1)[/COLOR] should point to your regular Ubuntu Lucid partition.

Once this is done, run:

```
sudo update-grub2
```

and your image should now be copied from your SSD during boot.

**[SIZE="4"]Issues once you boot from RAM[/SIZE]**

The first time I did this, as soon as I booted from RAM I noticed that my Internet was not working. It turns out as stated [here]("https://bugs.launchpad.net/ubuntu/+source/fsprotect/+bug/477012") by jesbecker:

> apparmor does not work well with stacked and read only files systems. A work around for this bug is to either disable for remove apparmor.

Disable:
You can disable by adding apparmor=0 and security="" as kernel options in your grub boot configuration.

Remove:
You can also choose to remove apparmor by executing: sudo apt-get remove apparmor

This issue seems to affect any program that is protected/enforced by apparmor. 

As you may have noticed, this is the reason I added apparmor=0 and security="" to the end of the 50_RAMSESS. This fixes the internet. I also tried "sudo apt-get remove apparmor" as suggested by jesbecker before I made those additions to my 50_RAMSESS and that works too.

**[SIZE="4"]Broken time[/SIZE]**

If your time is wrong every time you boot into your RAM session, run:

```
gksudo gedit /var/squashfs/etc/rc.local
```

from your regular Lucid and add the line:

```
dpkg-reconfigure --frontend noninteractive tzdata
```

just before the "exit 0" line that is already there. Save and exit. You will have to recreate your filesystem.squashfs image with:

```
sudo mksquashfs /var/squashfs /live/filesystem.squashfs -noappend -always-use-fragments
```

and move it to your SSD if necessary.

**[SIZE="4"]Broken applets[/SIZE]**

You may also find that some of your items from the Panel (top right) have disappeared, or moved around. I'm not sure why this happens [S]but once you restore them once, and arrange them the way you want, they should be fine.[/S] The way these items are arranged is saved within the /home folder as settings so in theory they should remain the way you set them up despite reboots. They do get jumbled around sometimes after a reboot for some reason.

For those adventurous enough to test something that has yet to be properly tested, try this to fix the panel:

Organize the panel the way you want it to be. Then run:

```
mkdir -p ~/.settings/
gconftool-2 --dump /apps/panel > ~/.settings/saved_panel_settings.entries
```

[S]Boot into or mount and chroot into your regular lucid, and open your /var/squashfs/etc/rc.local with a text editor as root:[/S]

```
[S]gksudo gedit /etc/rc.local[/S]
```

[S]and above the "exit 0" line, add:[/S]

```
[S]gconftool-2 --dump /apps/panel > /tmp/saved_panel_settings.entries
if [[ `md5sum /tmp/saved_panel_settings.entries | cut -d ' ' -f 1` != `md5sum ~/.settings/saved_panel_settings.entries | cut -d ' ' -f 1` ]]
then
	rm /tmp/saved_panel_settings.entries
	gconftool-2 --load ~/.settings/saved_panel_settings.entries
	killall gnome-panel
fi[/S]
```

The code above works better as a script for some reason. Try saving it to your ~/Documents/ folder, making it executable with:

```
sudo chmod a+x panelfix.sh
```

and in the RAM session, go to System --> Preferences --> Startup Applications. Create a new startup program, call it anything, and for command, browse to or type the entire path including the file name of panelfix.sh.

Because fixing the panel involves reloading gnome-panel, which for a second makes the panel disappear and may be annoying every time you boot, this will check if the panel layout has changes since you saved it. If there has been a change, it will reload the panel to restore the save file. If not, it will not bug you.

[S]After you have edited /var/squashfs/etc/rc.local, recreate your squashfs image with:[/S]

```
[S]sudo mksquashfs /var/squashfs /live/filesystem.squashfs -noappend -always-use-fragments[/S]
```

[S]Move it to the SSD if you need to.[/S]

If after a while you decide to change the panel again and want to save it again, just rerun:

```
gconftool-2 --dump /apps/panel > ~/.settings/saved_panel_settings.entries
```

This method of saving/loading the panel seems to work manually, but above is my attempt to make the process automated. I'm not sure if it will work. Let me know if there's a problem with it.

**[SIZE="4"]Performing System Updates/Changes[/SIZE]**

Although you may not need to modify your system other than your /home folder for quite a while, eventually you will need to perform updates or will want to install packages that will modify the system. This will be overwritten on next reboot unless you do the following (from within the RAM Session):

```

sudo mkdir -p /mnt/lucid
sudo mount [COLOR="DarkOrange"]/dev/sdc1[/COLOR] /mnt/lucid/
sudo mount -o bind /proc /mnt/lucid/var/squashfs/proc
sudo mount -o bind /dev /mnt/lucid/var/squashfs/dev
sudo mount -o bind /dev/pts /mnt/lucid/var/squashfs/dev/pts
sudo mount -o bind /sys /mnt/lucid/var/squashfs/sys
sudo cp /etc/resolv.conf /mnt/lucid/var/squashfs/etc/resolve.conf
sudo chroot /mnt/lucid/var/squashfs /bin/bash

```

change [COLOR="DarkOrange"]/dev/sdc1[/COLOR] to the device of your partition where Lucid was installed. You are now modifying the image you boot from (not directly - you will need to recreate it). To do updates run:

```
sudo apt-get update
sudo apt-get upgrade
```

and to install packages run

```
sudo apt-get install vlc
```

change vlc for the package you wish to install. Once you are done this, you will need to unmount the RAM disk and mount the regular lucid install to recreate the image. Type:

```
exit
```

and 

```
sudo umount /mnt/lucid/var/squashfs/proc
sudo umount /mnt/lucid/var/squashfs/dev/pts
sudo umount /mnt/lucid/var/squashfs/dev
sudo umount /mnt/lucid/var/squashfs/sys
```

to unmount the previously mounted partitions. Then run:

```
sudo mount -o bind /proc /mnt/lucid/proc
sudo mount -o bind /dev /mnt/lucid/dev
sudo mount -o bind /dev/pts /mnt/lucid/dev/pts
sudo mount -o bind /sys /mnt/lucid/sys
sudo cp /etc/resolv.conf /mnt/lucid/etc/resolve.conf
sudo chroot /mnt/lucid /bin/bash
```

rerun:

```
sudo mksquashfs /var/squashfs /live/filesystem.squashfs -noappend -always-use-fragments
```

to recreate the image. This will create a new /live/filesystem.squashfs with the changes you made. If you moved your filesystem.squashfs to an SSD as mentioned earlier, copy the new filesystem.squashfs from /live to the SSD. 

Now Reboot.

To simplify the steps above, I have created a script to mount either the lucid installation or the RAMDISK. I keep this script in my /home/Documents folder and launch it from within the RAM session when I need to do updates or want to install a new program. It seems to work ok. See the file attached for the script.

Edit: Sorry, I forgot to mention that the script has the device hardcoded as /dev/sdc1, which for me it is. I made it easier to change by only making it necessary to modify a single variable at the top, but you will still have to open the file with a text editor such as gedit and change the $DEVICE at the top to the proper device for your setup.

**[SIZE="4"]Possible Reason for Slowdown[/SIZE]**

As I keep using my RAM session and notice things about it, I update this article as much as I can. The thing I recently noticed was that when you use a program (VMware in my case) that takes up your entire RAM, your swap begins to fill up. Now that's not unusual, but it does mean that your system may become ridiculously slow if this happens (in my case so much so that even the music I had playing started to lag a lot). This is why you should keep an eye on your RAM and swap space if you know you are going to be using programs that eat up RAM.

In order to see how much RAM is used up by your system, DO NOT use the System Monitor. The System Monitor seems to show how much RAM your OS (Ubuntu) is using, but does not tell you how much RAM is actually in use. As RAM is normally only used by your OS, this works fine most of the time, but since in our case we initially copied an image into RAM that the OS does not account for, the System Monitor ends up showing that you have much more free RAM than you actually have. To display a proper reading of how much RAM and SWAP space you are using (in MB), use:

```
free -m
```

One other problem that I noticed was that if you already started using a program that eats RAM and your swap fills up, simply turning off that program frees up RAM but your OS still continues to use that SWAP space, keeping it slow when it doesn't have to be. To solve this, you can either reboot, or run:

```
sudo swapoff -a && sudo swapon -a
```

to dump your swap and make the system use RAM again.

**[SIZE="4"]Conclusion[/SIZE]**

I'm no Linux expert, and this is pretty much my first howto but if anyone has any questions I'll try to help you out with them. Also if those more wise than myself see any problems or corrections with what I wrote, let me know so I can fix them.

---

### Post by happyhamster on 2010-06-01
Very interesting. I'm definitely going to try this this weekend. I have a setup with 8GB of ram, with /tmp and firefox's cache in ram. / is on an ssd, /home on a regular drive. I'm really curious how big a difference it will make.

> **terminator14 said:**
> Unfortunately the downside of this was that the speed of my Windows 7 now made my Ubuntu 10.04 feel slow.
But now it's the other way around again, I assume? :)

One thing though: when running graphical applications as root, it's best practise to use gksudo instead of sudo. ([http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo))

Thanks for the guide!

---

### Post by Espionage724 on 2010-06-01
Hmm, well I would like to try this, I have exactly 2GB though. I want to be able to play games in Wine like WoW and War3 though. So If I were to put the OS to RAM, would I have enough to be able to play those games? And does Ubuntu have a pagefile similar to window (maybe I'm thinking of Swap)? And would parts of the game go to that if my ram is too full?

---

### Post by sdennie on 2010-06-01
This is well written and interesting.  I'll be moving it to Tips & Tutorials after I reply.

I've always run my machines with a lot of RAM because I understand the benefits of letting linux grow the page cache to gigantic proportions.  If you have enough RAM, over time, your machine will do some of what you've described automatically.  You can also be a bit more forceful about it by using something like the preload daemon.

But, as RAM sizes grow but squashfs'd distro sizes stay about the same, this kind of solution starts to make more sense.  If you store a squash'd OS in memory, you can completely write that memory off.  It's gone.  But, unfortunately, a lot of it is going to also be duplicated (in expanded form) in the page cache as you use your system.  Upon boot, if you have enough memory, you will literally have a squashed and unsquashed version of every file needed to boot living in memory.  As time goes on, you will have more and more files living twice in memory.  Once in the squashfs and once in the page cache.

Depending on how you use your machine, having files stored twice in memory is a potential performance problem because you've lost whatever the squashfs is using but are still putting pressure on the page cache as you access the squashfs.  But, as the percentage of memory used by a squashfs partition continues to drop because you have more memory, you are less likely to notice that performance hit and more likely to notice the crazy speedup of *always* having things in memory.

With 8GB of RAM on my machine, I think this might be pretty awesome.

---

### Post by terminator14 on 2010-06-01
> **happyhamster said:**
> 
But now it's the other way around again, I assume? :)

Definitely! :)

> **happyhamster said:**
> One thing though: when running graphical applications as root, it's best practise to use gksudo instead of sudo.

Just read the article you linked to. I didn't know that, but now that I read it, it makes sense. Thanks!

> **Espionage724 said:**
> Hmm, well I would like to try this, I have exactly 2GB though. I want to be able to play games in Wine like WoW and War3 though. So If I were to put the OS to RAM, would I have enough to be able to play those games? And does Ubuntu have a pagefile similar to window (maybe I'm thinking of Swap)? And would parts of the game go to that if my ram is too full?

When you install stuff in wine, it goes into the /home/username/.wine directory. This means if you mount your /home onto another drive (other than RAM I mean) like in the guide, the game files will not be in RAM.
My Ubuntu image is about 1.6GB. Assuming yours is pretty close to that, you will have roughly 400MB left over. I'm not sure what the WoW and War3 minimum RAM requirements are, but it may be more than 400MB. If it is, and your games run out of RAM, they will definitely start using swap. Since swap is located on the hard drive, it will slow down the game, likely to the point it won't be playable anymore. In that case you may have to buy more RAM, or play around with the Ubuntu image and remove some packages you don't use to have RAM left over for the games.

---

### Post by terminator14 on 2010-06-01
> **sdennie said:**
> This is well written and interesting.  I'll be moving it to Tips & Tutorials after I reply.

Thanks

> **sdennie said:**
> You can also be a bit more forceful about it by using something like the preload daemon.

I've tried preload before but it didn't seem to speed up my system all that much. Maybe I should have configured it to be more aggressive - I used the default settings, hoping it would spot that I had tons of RAM and use aggressive settings on its own.


> **sdennie said:**
> If you store a squash'd OS in memory, you can completely write that memory off.  It's gone.  But, unfortunately, a lot of it is going to also be duplicated (in expanded form) in the page cache as you use your system.  Upon boot, if you have enough memory, you will literally have a squashed and unsquashed version of every file needed to boot living in memory.  As time goes on, you will have more and more files living twice in memory.  Once in the squashfs and once in the page cache.

Depending on how you use your machine, having files stored twice in memory is a potential performance problem because you've lost whatever the squashfs is using but are still putting pressure on the page cache as you access the squashfs.

That does sounds like a problem. Is there any way to, instead of just copy the squashfs image to RAM during boot, simply having the squashfs image uncompress into RAM so the compressed version is no longer taking up space? It would probably be larger than the 1.6GB my squashfs image takes up now, but if it will prevent duplicate files, it might be worth it.

---

### Post by sdennie on 2010-06-01
> **terminator14 said:**
> I've tried preload before but it didn't seem to speed up my system all that much. Maybe I should have configured it to be more aggressive - I used the default settings, hoping it would spot that I had tons of RAM and use aggressive settings on its own.


Preload helps but, it's difficult to figure out how to turn the knobs right to make it more aggressive.

> 
That does sounds like a problem. Is there any way to, instead of just copy the squashfs image to RAM during boot, simply having the squashfs image uncompress into RAM so the compressed version is no longer taking up space? It would probably be larger than the 1.6GB my squashfs image takes up now, but if it will prevent duplicate files, it might be worth it.

You might be able to create squashfs/unionfs/tmpfs monstrosity that leaves everything on disk in squashfs until it's brought into RAM and then it's kept in RAM once (tmpfs lives in the page cache) and synced via unionfs.  I've grown fuzzy on my knowledge of unionfs so, I can't remember if it can actually provide that level of "glue" but, if it could and were fast enough, a simple tutorial on how to set it up would be the grandaddy of all, "Use your RAM to make stuff fast" tutorials.

---

### Post by terminator14 on 2010-06-01
> **sdennie said:**
> You might be able to create squashfs/unionfs/tmpfs monstrosity that leaves everything on disk in squashfs until it's brought into RAM and then it's kept in RAM once (tmpfs lives in the page cache) and synced via unionfs.  I've grown fuzzy on my knowledge of unionfs so, I can't remember if it can actually provide that level of "glue" but, if it could and were fast enough, a simple tutorial on how to set it up would be the grandaddy of all, "Use your RAM to make stuff fast" tutorials.

That sounds pretty interesting, but I'm afraid my skills aren't quite enough to make something like that happen quite yet. Maybe someday. Or maybe someone reading this who knows more about this can take a look at making this happen.

---

### Post by sdennie on 2010-06-01
> **terminator14 said:**
> That sounds pretty interesting, but I'm afraid my skills aren't quite enough to make something like that happen quite yet. Maybe someday. Or maybe someone reading this who knows more about this can take a look at making this happen.

When I described that possible solution as a monstrosity, I was being polite.  The forum rules prevent me from describing it with language that will do it justice.

Your tutorial looks great and I hope people find it useful.

---

### Post by terminator14 on 2010-06-02
> **sdennie said:**
> When I described that possible solution as a monstrosity, I was being polite.  The forum rules prevent me from describing it with language that will do it justice.

Your tutorial looks great and I hope people find it useful.

Perhaps someone eventually will find a more elegant way to accomplish this (hopefully soon), but until then, this will have to do. :)

---

### Post by Ozitraveller on 2010-06-02
Doesn't PuppyLinux also run from ram and it's Ubuntu based?
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by terminator14 on 2010-06-02
> **Ozitraveller said:**
> Doesn't PuppyLinux also run from ram and it's Ubuntu based?
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

Puppy might be the way to go for people who don't have the RAM to run Ubuntu this way, but who still want to experience the speed of running a distribution directly from RAM. This howto however allows all the functionality of Ubuntu with the advantage of the speed of running it in RAM. I haven't tried puppy for a while so I can't really compare it with Ubuntu but from taking a quick look, it's .iso is 128mb, far smaller than that of Ubuntu, so I'm assuming a lot of the packages had to be removed from Ubuntu to make Puppy as small as it is. Some of these packages may not be absolutely necessary, but are convenient to have. Therefore I would personally prefer getting Ubuntu, the distribution that I am used to and have been using for years, to work at such speeds, than to switch to a different distribution to accomplish this.

---

### Post by Tech2077 on 2010-06-02
Great tutorial, if only i had a 64 bit desktop with 8gb ram to try this on. I just looked it up though, and doesn't the updated Linux kernel(Linux 2.6.32) have SSD trim fully implemented?

---

### Post by terminator14 on 2010-06-02
> **Tech2077 said:**
> Great tutorial, if only i had a 64 bit desktop with 8gb ram to try this on. I just looked it up though, and doesn't the updated Linux kernel(Linux 2.6.32) have SSD trim fully implemented?

From what I'm getting from places like [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476") and [here]("http://ohioloco.ubuntuforums.org/showthread.php?p=9182548") (
> First, to newcomers, make sure you have 2.6.33.x Kernel, otherwise forget about TRIM.

  ), it sounds like 2.6.33 has trim but 2.6.32 does not. Or has 2.6.32 got some patch for trim that I missed?

---

### Post by Tech2077 on 2010-06-02
Hmmmm, I must have miss-read, I'm just going get a SSD then instead of trying this, I can skimp on write speeds with read speeds like that :)

---

### Post by farbird on 2010-06-02
any bootchart images to show off the boot speed?

---

### Post by terminator14 on 2010-06-02
> **farbird said:**
> any bootchart images to show off the boot speed?

I don't know if this is impressive or not - I'm afraid I can't interpret these charts all that well. All I know is boot takes about 10 seconds to copy the squashfs image to RAM from my SSD, 4 or 5 seconds of what looks like the initrd doing stuff to load the OS (my /boot is not on the SSD so this could probably be speed up further if I moved it there) until I see the login screen, and another 2 seconds to get from the login screen to the Desktop that's ready to go. I realize that only adds up to about 17 seconds whereas the chart says 26 - I'm not sure where it starts and stops counting so I can't say where the discrepancy is coming from - maybe the values of 10, 4-5, and 2 that I came up with are way off and it actually is closer to 26 seconds. I'm not sure.

All this is probably reflected in the image however so see for yourself.

[The chart seems to be too large of an image for ubuntuforums, which makes the system resize it, so here's an external link to it.]("http://dxgameunit.webs.com/boot.png")

---

### Post by happyhamster on 2010-06-03
Wow, finally got it to work :D. Had quite a lot of trouble too, but that's very likely because I'm using Jaunty with a self-compiled kernel (2.6.34). Things I ran into:
```

sudo apt-get install live-initramfs squashfs-tools

```
This broke apt for me (at least I think that's what started it). Running "sudo dpkg --configure -a", resulted in:
> 
update-initramfs: Generating /boot/initrd.img-2.6.34-core2
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.34-core2
Failed to create initrd image.

The fix, after some Googling, appeared to be to edit the file
"/usr/share/initramfs-tools/hooks/live", and change the line "copy_exec /usr/bin/udevinfo" into "copy_exec /sbin/udevadm".

When trying to boot into RAM, I was dropped into busybox, with:

> 
can not mount /dev/loop0 (/live/image/filesystem.squashfs) on //filesystem.squashfs

Regular Jaunty creates Squashfs filesystem version 3.1. I tried installing the squashfs-tools from Karmic instead and recreated the squashfs image (version 4). That took care of it, but now a new error appeared:
> 
mount aufs on /root failed with option noatime,dirs=/cow=rw://filesystem.squashfs=rr

When looking in the live.log, there was a complaint about a missing "wc" command (for busybox). This was fixed by adding a line "copy_exec /usr/bin/wc /bin" to the "/usr/share/initramfs-tools/hooks/live" file. After rebooting, the aufs error still appeared, so I tried installing squashfs-tools from Lucid and going through the process again, but still no luck.

So, back to Google, and it became clear that aufs-support isn't part of the mainline kernel; you'll need to patch it first (standard ubuntu kernels are already patched). So, compiled a kernel with aufs patches applied (it took several times because of kernel version conflicts), compiled the module, added module to /etc/modules (did forget to do that initially), and after going through the howto again, everything actually booted! Yay! :D 

I must say, the speed difference is very noticable. I'm talking about application startup-time, something as simple as scrolling in firefox, etc. Very impressive. Boot time increased though (as expected).

I have a few more things to write (some recommendations as well), but I *really* should go to sleep now. Anyway, thanks again for the howto, I learned a lot.

---

### Post by benmandude on 2010-06-04
I'm having issues with my home directory. I created a new partition and added it to the fstab. However whenever I boot into ram it gives me errors saying that I need to create a home directory. I tried to copying my home directory to the new partition to no avail. Am I missing something?

---

### Post by sgosnell on 2010-06-04
You don't need a patched kernel.  Just download the .34 kernel from [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and install it with gdebi.  Quick and painless.

---

### Post by terminator14 on 2010-06-04
> **happyhamster said:**
> Wow, finally got it to work :D. Had quite a lot of trouble too, but that's very likely because I'm using Jaunty with a self-compiled kernel (2.6.34). Things I ran into:
```

sudo apt-get install live-initramfs squashfs-tools

```
This broke apt for me (at least I think that's what started it). Running "sudo dpkg --configure -a", resulted in:

The fix, after some Googling, appeared to be to edit the file
"/usr/share/initramfs-tools/hooks/live", and change the line "copy_exec /usr/bin/udevinfo" into "copy_exec /sbin/udevadm".

When trying to boot into RAM, I was dropped into busybox, with:


Regular Jaunty creates Squashfs filesystem version 3.1. I tried installing the squashfs-tools from Karmic instead and recreated the squashfs image (version 4). That took care of it, but now a new error appeared:

When looking in the live.log, there was a complaint about a missing "wc" command (for busybox). This was fixed by adding a line "copy_exec /usr/bin/wc /bin" to the "/usr/share/initramfs-tools/hooks/live" file. After rebooting, the aufs error still appeared, so I tried installing squashfs-tools from Lucid and going through the process again, but still no luck.

So, back to Google, and it became clear that aufs-support isn't part of the mainline kernel; you'll need to patch it first (standard ubuntu kernels are already patched). So, compiled a kernel with aufs patches applied (it took several times because of kernel version conflicts), compiled the module, added module to /etc/modules (did forget to do that initially), and after going through the howto again, everything actually booted! Yay! :D 

I must say, the speed difference is very noticable. I'm talking about application startup-time, something as simple as scrolling in firefox, etc. Very impressive. Boot time increased though (as expected).

I have a few more things to write (some recommendations as well), but I *really* should go to sleep now. Anyway, thanks again for the howto, I learned a lot.

Ya, playing around with such things can be a bit frustrating at times. Glad to hear it finally worked out for you. Thanks for sharing your experience so people know if they run into the same problems what they can try to fix them.

> **benmandude said:**
> I'm having issues with my home directory. I created a new partition and added it to the fstab. However whenever I boot into ram it gives me errors saying that I need to create a home directory. I tried to copying my home directory to the new partition to no avail. Am I missing something?

What's your new partition formatted as? ext4/3? What device is it using (like /dev/?). And what does the line look like that you added to /etc/fstab for /home? Also, make sure your RAM session's /etc/fstab is the one that has been modified - if you simply modify your main OS's /etc/fstab and don't update the squashfs image, the RAM session's /etc/fstab won't change. To do this, you can't modify the RAM session's /etc/fstab directly either since it won't save after a reboot - you need to modify /var/squashfs/etc/fstab of your main OS and then rerun the command that creates the squashfs image.

Oh yeah and I forgot to mention in the howto (I will modify it now) that when you are in your main OS, run:

```
sudo cp -a /home/* /mnt/home/
```

to copy all your content of /home to the new partition you created. That is assuming you mounted the new partition on /mnt/home - change that to where you mount it.

---

### Post by happyhamster on 2010-06-04
I tested it on a fresh (unmodified) Jaunty installation (only 1.5GB of RAM), and it was much easier this time.

- Installing the necessary tools broke apt as before:
```

user@test:~$ sudo apt-get install live-initramfs squashfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  busybox user-setup
Suggested packages:
  loop-aes-utils curlftpfs genext2fs httpfs2 mtd-tools squashfs-source
  lzma-source
The following NEW packages will be installed:
  busybox live-initramfs squashfs-tools user-setup
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 651kB of archives.
After this operation, 1683kB of additional disk space will be used.
Do you want to continue [Y/n]? 

Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe busybox 1:1.10.2-2ubuntu7 [304kB]
Get:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main user-setup 1.23ubuntu20 [144kB]
Get:3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe live-initramfs 1.154.8-1 [86.8kB]
Get:4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main squashfs-tools 1:3.3-7ubuntu2 [117kB]
Fetched 651kB in 0s (1025kB/s)   
Preconfiguring packages ...
Selecting previously deselected package busybox.
(Reading database ... 95750 files and directories currently installed.)
Unpacking busybox (from .../busybox_1%3a1.10.2-2ubuntu7_i386.deb) ...
Selecting previously deselected package user-setup.
Unpacking user-setup (from .../user-setup_1.23ubuntu20_all.deb) ...
Selecting previously deselected package live-initramfs.
Unpacking live-initramfs (from .../live-initramfs_1.154.8-1_all.deb) ...
Selecting previously deselected package squashfs-tools.
Unpacking squashfs-tools (from .../squashfs-tools_1%3a3.3-7ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-19-generic
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-19-generic
dpkg: subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
- And as before: changing the line "copy_exec /usr/bin/udevinfo /bin" into "copy_exec /sbin/udevadm /bin" (in the file "/usr/share/initramfs-tools/hooks/live") and then running "sudo dpkg --configure -a" fixed it. I'll see if there's a bugreport on this***.

- When trying to boot into RAM, there was a new error though: the command "du" was missing, which soon caused a zillion other errors. Adding "copy_exec /usr/bin/du /bin" to the file "/usr/share/initramfs-tools/hooks/live" fixed that.
- Same thing for the "wc" command. Rebuild the image again, booted, and it worked. So using a stock kernel does indeed make things easier on Jaunty. :guitar:

- There were a few things I did not do: /home was already on a separate partition, so I just kept it as it was. And instead of using a device name, I used UUID's in menu.lst, but that's it I guess.

One suggestion:
```
4. copy your filesystem to temporary directory
```
Would be nice to add a little warning:
```
4. Copy your filesystem to temporary directory (this could take a few minutes)
```
Don't keep staring at the terminal output (especially if using a slow harddrive)! Go get yourself a cup of coffee or such :P

*** edit: found it: [https://bugs.launchpad.net/ubuntu/+source/live-initramfs/+bug/343735](https://bugs.launchpad.net/ubuntu/+source/live-initramfs/+bug/343735)
So, this appears fixed for Karmic and onwards.

---

### Post by terminator14 on 2010-06-04
> **happyhamster said:**
> Installing the necessary tools broke apt as before

I wonder why it does that in Jaunty. It seemed to go ok in Lucid when I did that. I added a note about it to the howto in case anyone else runs into this problem.

> **happyhamster said:**
> One suggestion:
```
4. copy your filesystem to temporary directory
```
Would be nice to add a little warning:
```
4. Copy your filesystem to temporary directory (this could take a few minutes)
```
Don't keep staring at the terminal output (especially if using a slow harddrive)! Go get yourself a cup of coffee or such :P

Noted! haha ;)

---

### Post by CarloMagno on 2010-06-09
Terminator14 thanks for this useful guide. I am writing now from my Ram Session in my htpc. I had planned to install a new SSD Drive but with your suggestion it seems I could live without it :-)

I haven't set up a separate /home partition for Ram session (everything is in RAM as it was in the original post) and I will try to check what works and what doesn't (up the moment it seems mythtv frontend refuses to connect to the backend ... could be something to do with the home partition.. I will look for a solution)

Just in case anybody has the same problem I had, it seems that casper and live-initramfs cannot be installed simultaneously (at least from the repos) so you have to uninstall casper if you have it installed in your system to be able to follow Terminator14 instructions, I had it installed because I use Remastersys to backup my system).

Thanks again for the work,

---

### Post by terminator14 on 2010-06-09
> **CarloMagno said:**
> Terminator14 thanks for this useful guide. I am writing now from my Ram Session in my htpc. I had planned to install a new SSD Drive but with your suggestion it seems I could live without it :-)

Awesome!

> **CarloMagno said:**
> I haven't set up a separate /home partition for Ram session (everything is in RAM as it was in the original post)

That works great for a while but if you use your Ubuntu a lot, eventually you're going to want to save files to your desktop and to your home folder and be able to reboot the system without thinking twice about what you will lose. When you do, post back if you run into problems.

> **CarloMagno said:**
> Just in case anybody has the same problem I had, it seems that casper and live-initramfs cannot be installed simultaneously (at least from the repos) so you have to uninstall casper if you have it installed in your system to be able to follow Terminator14 instructions, I had it installed because I use Remastersys to backup my system).

Thanks for the tip.

> **CarloMagno said:**
> Thanks again for the work

Glad to help. :)

---

### Post by mbsullivan on 2010-06-14
Nice tutorial and good idea! Make sure to try and keep it as simple as possible!

Now let's get some benchmarks in here! How about running some of the [Phoronix Test Suite]("http://www.phoronix-test-suite.com/") on both the (1) RAM drive system, as well as the (2) harddrive system, if possible.

To do so:

(1) Install the test suite

```
sudo aptitude install phoronix-test-suite
```

(2) Choose the applicable benchmark suites. To see a list, you can run "phoronix-test-suite list-suites". For your purposes, the most important is definitely:

> disk - "real-world disk and file-system tests"

However, to get a more well-rounded feel for Ubuntu desktop users, it might be nice to see results from a couple more suites, like:

> gaming-free - "all game tests that are open-source"
workstation - "designed to test a system's workstation / server capabilities"


(3) Run all chosen benchmark suites (will also install them). For each chosen suite, run the following command:

```
phoronix-test-suite benchmark [suite name]
```

The benchmarking process takes a while, but should give a wealth of valuable info about when this makes a difference.

Mike

PS: Because of caching and the nature of demand paging under Linux, you should reboot right before running the test suite.

---

### Post by sdennie on 2010-06-14
@mbsullivan:

I'm not sure if this is the kind of change you can meaningfully benchmark without some sort of "desktop interactivity" benchmark.  In which case, yes, having a fully populated cache is cheating.  However, the purpose of this guide is to forcefully create a fully populated "cache" of the filesystem.  So, it's not like comparing a fully cached benchmark with an uncached benchmark.  You wouldn't be benchmarking apples and oranges.  You'd be benchmarking apples that happen to be oranges and oranges.

---

### Post by mbsullivan on 2010-06-15
> 
I'm not sure if this is the kind of change you can meaningfully benchmark without some sort of "desktop interactivity" benchmark. In which case, yes, having a fully populated cache is cheating. However, the purpose of this guide is to forcefully create a fully populated "cache" of the filesystem. So, it's not like comparing a fully cached benchmark with an uncached benchmark. You wouldn't be benchmarking apples and oranges. You'd be benchmarking apples that happen to be oranges and oranges.

That's true. I'd argue, though, that it'd be interesting to see all three: (1) Un-warmed up harddrive, (2) Nicely warmed up harddrive (perhaps through repeated runs of the benchmark), (3) RAM drive. 

That'd give a good indication of how much the virtual page cache can approximate the gains bought through the full RAM drive approach.

Mike

---

### Post by terminator14 on 2010-06-15
> **mbsullivan said:**
> Now let's get some benchmarks in here! How about running some of the [Phoronix Test Suite]("http://www.phoronix-test-suite.com/") on both the (1) RAM drive system, as well as the (2) harddrive system, if possible.

Despite the apparent questionable usefulness of these tests in this case, I wanted to try them out as I have read a bit about this benchmark suite and was curious about it months ago but never got around to trying it out. I tried to run it on my RAM session with:

```
$ phoronix-test-suite benchmark disk
```

and after it downloaded the disk test, all it showed is:

> SQLite:
      sqlite
      Test Run 1 of 21
      Expected Trial Run Count: 3
            Started Run 1 @ 21:16:51

It sat like that for hours, until I restarted it. Now it's back to the same screen. Is it supposed to take forever or is it stuck? I can't imaging a test involving SQL taking this long.

---

### Post by sdennie on 2010-06-15
> **mbsullivan said:**
> That's true. I'd argue, though, that it'd be interesting to see all three: (1) Un-warmed up harddrive, (2) Nicely warmed up harddrive (perhaps through repeated runs of the benchmark), (3) RAM drive. 

That'd give a good indication of how much the virtual page cache can approximate the gains bought through the full RAM drive approach.

Mike

*That* would be an excellent test actually.

---

### Post by terminator14 on 2010-06-15
After a few hours left unattended, the test finally finished on the RAM disk. I'll post the results as soon as I figure out how - they opened up as a web page with plenty of graphs.

---

### Post by terminator14 on 2010-06-15
Oh, well that's simple enough... It looks like the tool automatically uploads the results. [Here's the link.]("http://global.phoronix-test-suite.com/index.php?k=profile&u=hellspawn-24935-9863-12209") This was done in the RAM session. I should probably run it again with swap disabled as I'm not entirely sure if it was used. I'm also not sure if /home was used at any point during the tests, which would slow down as this is not in my RAM. Should I run the next test as root since root's home folder (/root) is in RAM whereas my user's home folder is not? Or does it not use the home folder? Does it just use /tmp?

Edit: Haha I just realized why it uploaded the results to Phoronix Global without warning me - during the test I was trying to get a response from it (some indication that it was still doing something) so I hit enter a few times. When the tests finished it asked a bunch of questions like "Would you like to upload these results to Phoronix Global (Y/n)?" and the enter I hit several times hours earlier made it accept the defaults. Overall it looks like an awesome benchmarking tool - it would be nice if I could understand half the results it shows though :)

---

### Post by terminator14 on 2010-06-16
Clearly the test uses the hard drive to transfer large files during its tests:

As soon as I launched the tool as root (after I disabled all swap with "sudo swapoff -a"), it was clear the tests were running much faster than before as the first few tests had already finished within the first few seconds. Unfortunately at about the fourth test, the system started to freeze. Before it completely froze, I managed to open a terminal and type "free -m" which showed my RAM totally full. I'm afraid I won't be able to even finish these tests properly as they need far more drive space for copying files around than my RAM can provide (unless there's a way to skip those particular tests?).

---

### Post by terminator14 on 2010-06-16
A few minutes of digging turned up this:

> - pts-core: Add support for stopping/skipping the current test by touching ~/.phoronix-test-suite/skip-test during the process

found [here]("http://www.phoronix-test-suite.com/?k=changes_22").

I wonder if this would skip the entire disk benchmark, or if it would just skip the particular test it was running (which is what it sounds like it does). If this does skip individual tests, I could probably whip up a script that checks free RAM constantly about every half a second or second or so, and if it notices it below a certain point, it will touch that file. I'll see if that works... Any other ideas?

---

### Post by Stason on 2010-06-16
> **sdennie said:**
>  You can also be a bit more forceful about it by using something like the preload daemon.

Preload is broken, doesn't work and is on nobody's fixit list. ](*,)

And to make your system extra-insanely fast also do this: 

write vm.swappiness=1 and vm.vfs_cache_pressure=50 on your /etc/sysctl.conf  file

this would drastically reduce swap activity keeping more stuff in Ram. ;)

---

### Post by terminator14 on 2010-06-16
Tested the theory with a simple script - didn't skip the test... Looking for other solutions.

> **Stason said:**
> Preload is broken, doesn't work and is on nobody's fixit list. ](*,)

Well that sucks...

> **Stason said:**
> And to make your system extra-insanely fast also do this: 

write vm.swappiness=1 and vm.vfs_cache_pressure=50 on your /etc/sysctl.conf  file

this would drastically reduce swap activity keeping more stuff in Ram. ;)

Awesome, thanks!

---

### Post by mbsullivan on 2010-06-16
In general, the results are what I guess I might expect until we get the swapping issues ironed out... Compared to my workstation, some tests are crazy great, some are sameish, and some are awful. :) I assume that this is related to those that have hangups and those that don't. As expected, random reads and writes absolutely destroy my performance, which is nice to see. It's important to figure out some way to all of the real-world benchmarks at least fare decently, so that we can declare success at becoming "insanely fast".

> I wonder if this would skip the entire disk benchmark, or if it would just skip the particular test it was running (which is what it sounds like it does). If this does skip individual tests, I could probably whip up a script that checks free RAM constantly about every half a second or second or so, and if it notices it below a certain point, it will touch that file. I'll see if that works... Any other ideas?

How much RAM do you have? 6GB?

I might be inclined to let them swap... after all, we're trying to get a real world indication of performance, no?

If you run it again with vm.swappiness=0, does it ONLY swap when you run out of RAM? You can get regular updates on your virtual memory usage with vmstat:

```
vmstat 5
```

Mike

---

### Post by terminator14 on 2010-06-16
I have 6GB of RAM. I edited /usr/share/phoronix-test-suite/pts/test-suites/disk.xml to exclude tests that required too much space. [This is what I ended up with.]("http://global.phoronix-test-suite.com/index.php?k=profile&u=root-13572-29660-27239")

I ran the test as root (which means all tests presumably used /root/.phoronix... as temp storage, which is on the RAM drive) and removed all SWAP beforehand with:

```
sudo swapoff -a
```

I kept a close eye on my free RAM (I had a script tell me if I even had below 100mb or RAM) and removed tests that froze my system because of lack of free RAM.

---

### Post by pratzy on 2010-06-17
This sounds good..will try it soon.

---

### Post by terminator14 on 2010-06-17
Running the benchmark again in the RAM session, this time with 6.8GB of SWAP resulted in the completion of about 3 tests until the compilebench test ate up all the RAM and started using SWAP. The test ran for a while but eventually failed as the RAM ate up any room on the fs to save the test results to. All subsequent tests failed within a few seconds of starting as they had no room on the fs (/root/.phoronix...) to write temp data and results to. 

I'm probably going to try the benchmark on the slower Ubuntu that has its filesystem on the HDD soon.

---

### Post by mbsullivan on 2010-06-17
> I have 6GB of RAM. I edited /usr/share/phoronix-test-suite/pts/test-suites/disk.xml to exclude tests that required too much space. This is what I ended up with.

You definitely get blazingly fast numbers on those benchmarks, especially the synthetic ones. Congrats!

> Running the benchmark again in the RAM session, this time with 6.8GB of SWAP resulted in the completion of about 3 tests until the compilebench test ate up all the RAM and started using SWAP. The test ran for a while but eventually failed as the RAM ate up any room on the fs to save the test results to. All subsequent tests failed within a few seconds of starting as they had no room on the fs (/root/.phoronix...) to write temp data and results to. 

Hmm... That's odd. Isn't the point of the swap space be to prevent the process from freezing when you run out of RAM? Pages should be pushed out to the disk, such that you can run programs as though you have a seemingly infinite memory space.

I'd think it'd be painfully slow when you have to swap, but not freeze.

Mike

---

### Post by terminator14 on 2010-06-17
In our case, the filesystem (/) is located in RAM. When the space for the filesystem (saving files) starts to run low (RAM runs out), SWAP does not add to that space (AFAIK). It only replaces RAM when running applications need RAM.

---

### Post by sdennie on 2010-06-17
> **Stason said:**
> Preload is broken, doesn't work and is on nobody's fixit list. ](*,)

And to make your system extra-insanely fast also do this: 

write vm.swappiness=1 and vm.vfs_cache_pressure=50 on your /etc/sysctl.conf  file

this would drastically reduce swap activity keeping more stuff in Ram. ;)

Sort of.  It depends on how you use your machine.  Setting swappiness to a very low value can have some initial "feel good" results but, it may not be doing you as many favors as you think.  A low swappiness value means that you are preferring basically abandoned RAM to disk cache.  Even if you have a fast SSD, your hard drive by far the slowest part of your computer and the page cache does a nice job of hiding that fact.  Setting a low swappiness value reduces the kernels ability to hide the fact that your disk is crazy slow.

Yes, setting swappiness to 0 is a known way to increase performance. But, it's not a benchmarked way to increase performance across the board.  And at least 1 kernel developer runs with swappiness=100 because he understands what turning that knob means.

I think my signature is very relevant here.  Don't try to make something "fast" until you are able to quantify "slow".

---

### Post by terminator14 on 2010-06-18
Performing the exact same tests on my regular Ubuntu and comparing them to the previous results, it is clear the advantage running an OS in RAM has. Here are the results:

[Regular OS running from HDD]("http://global.phoronix-test-suite.com/index.php?k=profile&u=root-2024-22036-15391") 
[RAM Session]("http://global.phoronix-test-suite.com/index.php?k=profile&u=root-13572-29660-27239")

The SQLite test appears in the regular OS benchmark but not in the RAM session presumably because it errored out in the RAM session for some reason (I must have missed the error) and was not included in the results by phoronix-test-suite.

> **sdennie said:**
> I think my signature is very relevant here.  Don't try to make something "fast" until you are able to quantify "slow".

I noticed your signature a while ago and thought it was very insightful and relevant to our topic. I guess I went about it the wrong way in first getting my system to work fast and only now benchmarking the speed of my old system (the regular HDD OS) and the new OS (RAM Session). I should have tested the system thoroughly with similar benchmarks first and focused on improving areas that I was not satisfied with, but I guess it was just easier to say "slow" is what I have now, "fast" is what I want it to be.

---

### Post by mbsullivan on 2010-06-18
> 
In our case, the filesystem (/) is located in RAM. When the space for the filesystem (saving files) starts to run low (RAM runs out), SWAP does not add to that space (AFAIK). It only replaces RAM when running applications need RAM.

Is is possible to make the filesystem be larger than the available amount of RAM? If so, this (combined with playing with vm.swappiness) might make it possible to run the enterprise-level programs in this setup. 

> Performing the exact same tests on my regular Ubuntu and comparing them to the previous results, it is clear the advantage running an OS in RAM has. Here are the results:


I wonder why unpacking the linux kernel (the only non synthetic benchmark on there) actually got slightly worse on the RAM drive. The difference could be in the noise margin, indicating that the process is simply not disk bound. However, otherwise it makes no sense to me!

Mike

---

### Post by terminator14 on 2010-06-18
> **mbsullivan said:**
> Is is possible to make the filesystem be larger than the available amount of RAM? If so, this (combined with playing with vm.swappiness) might make it possible to run the enterprise-level programs in this setup.

The only way I know to make that happen is:

1. To extend RAM that applications have to use, add SWAP space
2. To extend fs in our case, figure out the biggest user of space in the fs (like /home) and edit /etc/fstab to mount that part somewhere on a disk. This would slow down operations considerably if you do it to a highly used portion of the fs (like /etc or /usr or something), but it would allow more space if you are running short on RAM.
3. Some sort of lvm setup that combines the storage or RAM and an HDD (I haven't played with lvm much). The problem with this is, even if it is possible, it would cause Linux to have no preference of where to write to and read from (AFAIK). This would mean, in the worst case, you could have totally empty RAM while your disk contained the OS, which would be no better in performance than having a simple OS install to the HDD.

> **mbsullivan said:**
> I wonder why unpacking the linux kernel (the only non synthetic benchmark on there) actually got slightly worse on the RAM drive. The difference could be in the noise margin, indicating that the process is simply not disk bound. However, otherwise it makes no sense to me!

That is a weird one. I guess some things are already optimized to use RAM as efficiently as possible in Linux, so much so that putting them completely in RAM doesn't help. Not sure why it would hurt though.

---

### Post by mbsullivan on 2010-06-18
> 
Quote:
Originally Posted by mbsullivan View Post
Is is possible to make the filesystem be larger than the available amount of RAM? If so, this (combined with playing with vm.swappiness) might make it possible to run the enterprise-level programs in this setup.
The only way I know to make that happen is:

1. To extend RAM that applications have to use, add SWAP space
2. To extend fs in our case, figure out the biggest user of space in the fs (like /home) and edit /etc/fstab to mount that part somewhere on a disk. This would slow down operations considerably if you do it to a highly used portion of the fs (like /etc or /usr or something), but it would allow more space if you are running short on RAM.
3. Some sort of lvm setup that combines the storage or RAM and an HDD (I haven't played with lvm much). The problem with this is, even if it is possible, it would cause Linux to have no preference of where to write to and read from (AFAIK). This would mean, in the worst case, you could have totally empty RAM while your disk contained the OS, which would be no better in performance than having a simple OS install to the HDD.

Hmmm... [tmpfs]("http://www.funtoo.org/en/articles/linux/ffg/3/") can do this, albeit with a performance penalty. As a proof of concept, I created a 5G file in my workstation with 4G of RAM, 50% of which was already full. Note that tmpfs is a dynamically resizing ramdisk, such that the 8G is just a precaution given my situation:

```
sudo mkdir /media/tmpfstst/
sudo mount tmpfs /media/tmpfstst/ -t tmpfs -o size=8G
dd if=/dev/zero of=bigfile bs=1G count=5
```

By monitoring vmstat, I could see that it wrote to the swap when it ran out of memory. Unfortunately, it was also obvious that it was doing it in a very inefficient manner (copying only a small amount at a time). All in all, the performance was quite horrendous:

> 5368709120 bytes (5.4 GB) copied, 1084.94 s, 4.9 MB/s


Normally, I keep my vm.swappiness at 0, since I don't do much with my memory. Increasing it to 90 improved the performance considerably, though it is still a far cry from even a normal harddrive:

> 5368709120 bytes (5.4 GB) copied, 398.006 s, 13.5 MB/s


I think that the performance could be improved further with more tuning, but it's still likely to be as slow or slower than just a harddrive. My normal harddrive gets about 40MB/s. Also, I'm using a swap file instead of a swap drive, which might adversely impact performance a bit.

The test was meant to be a somewhat extreme case -- as you get closer to the size of the (free) RAM, performance increases considerably. Also, obviously, if the files fit in RAM, then performance is very good (though not as good as with a fixed size ramdisk).

I'd find it interesting if you could create a resizable ramdisk for the directories that might have large files in them (i.e. /home/). This should, I would think, allow the benchmarks to run to completion. It's clear that this makes memory system tuning (vm.swappiness and the like) much more important for the performance, though.

Mike

---

### Post by terminator14 on 2010-06-18
> **mbsullivan said:**
> I'd find it interesting if you could create a resizable ramdisk for the directories that might have large files in them (i.e. /home/). This should, I would think, allow the benchmarks to run to completion. It's clear that this makes memory system tuning (vm.swappiness and the like) much more important for the performance, though.

For the test to complete, this would need to be done to /root if running the benchmark as root like I am. I think I could use fstab to mount /root as a tmpfs filesystem allowing any overflow to use SWAP. That's a great idea.

Actually, now that I think about it, I don't need to do it at boot so I don't need fstab. Lets see if that works...

---

### Post by gameguy on 2010-06-19
I created a RAM boot thing and it said:
"could not update /home/matthew/.ICEauthority"
"There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"
"Nautilus could not create the following the required folders:
/home/matthew/Desktop, /home/matthew/.nautilus.
Before running nautilus, please create these folders, or set permissions such that nautilus can create them"
and it won't display panels (probably because nautilus won't load)

I then copied /home to the filesystem, and updated it. I already have a seperate data partition, which loads to /data (works fine on RAM and HD).
Now the last error message isn't displayed.
I can press alt-F2 and run something (only using terminal) or load terminal, and can run nautilus as sudo.
Also, every time I boot, it does the first time boot process (like creating users) because RAM doesn't save it.
And a lot of the config won't load, but I'm pretty sure that all this is to do with nautilus.

---

### Post by terminator14 on 2010-06-20
> **gameguy said:**
> I created a RAM boot thing and it said:
"could not update /home/matthew/.ICEauthority"
"There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"
"Nautilus could not create the following the required folders:
/home/matthew/Desktop, /home/matthew/.nautilus.
Before running nautilus, please create these folders, or set permissions such that nautilus can create them"
and it won't display panels (probably because nautilus won't load)

I then copied /home to the filesystem, and updated it. I already have a seperate data partition, which loads to /data (works fine on RAM and HD).
Now the last error message isn't displayed.
I can press alt-F2 and run something (only using terminal) or load terminal, and can run nautilus as sudo.
Also, every time I boot, it does the first time boot process (like creating users) because RAM doesn't save it.
And a lot of the config won't load, but I'm pretty sure that all this is to do with nautilus.

Hmm... It sounds like the first time around you didn't have a /home so nautilus had issues storing or retrieving config files. Once you copied your /home over, that was fixed as it now finds the config files it originally created. Even if you have a /data where you store all your data, you still need the /home because many GUI programs like firefox, panel settings, settings of any program you install are all stored in /home/.* which are hidden folders in /home that start with a "." (dot).

So what are the errors you are getting now that you copied /home over? Are you still getting the gconf-sanity-check-2 error?

> **True said:**
> it appears that this resolves it:

sudo chmod 755 /etc/gconf/gconf.xml.system

> **Vadi said:**
> Also try:

```
mkdir -p /etc/gconf/gconf.xml.system; chmod 755 /etc/gconf/gconf.xml.system 
```

---

### Post by gameguy on 2010-06-20
Got it working by not having the home directory taken out. Because my data partition is NTFS I keep /home in the normal spot and write to /data.
However, my internet connection dies after about a minute of being booted from it. Is there any way to upgrade certain packages (permanently, not just from that session), because there are some packages, which, when upgraded, get it working (preferably without having to use the mksquashfs command again).
Also, uncompressed (compressed is 1.1 GB), how much would squashfs be (or the equivalent uncompressed)?

---

### Post by JohnnyC35 on 2010-06-21
maybe it would help, rather than move everything to RAM, move certain directories to RAM as long as their resetting doesn't kill anything.

I had started a thread with that in mind. I'll see if I can find it ...

here it is:
[http://ubuntuforums.org/showthread.php?t=1413653](http://ubuntuforums.org/showthread.php?t=1413653)

---

### Post by terminator14 on 2010-06-21
Making /root a tmpfs filesystem was a great idea to finish the benchmarks. It seems to have worked. Unfortunately, because it is using SWAP a lot more now, the speed of individual tests is closer to 5MB/s, far slower than even a regular hard drive. This means it takes so long to finish all the benchmarks, that even leaving it overnight doesn't complete them all. While it is running the benchmark, its use of SWAP makes the system lag (even the mouse) to the point that it becomes virtually unusable for anything (like watching movies). This means I need to wait for hours and hours until my computer finishes without being able to touch it at all. I've been trying to find the time to do that but when I'm tired and want to relax by watching some show/movie on my computer and a benchmark is still running I always end up canceling it. Either way, the results are going to be terrible. The point here is that, if you want to do this, make sure you have enough RAM not to need to use SWAP. Otherwise you may end up with a system far slower than even a regularly installed one.

> **gameguy said:**
> However, my internet connection dies after about a minute of being booted from it. Is there any way to upgrade certain packages (permanently, not just from that session), because there are some packages, which, when upgraded, get it working (preferably without having to use the mksquashfs command again).

Because any packages you install are normally installed into places like /sbin, /bin. and /usr and such, with their settings stored in /etc (all of which are in RAM), and because the squashfs image cannot be directly edited (AFAIK), you will have to modify the folder you created (/var/squashfs in my howto) by either installing the packages you want on your main system and recopying everything to /var/squashfs, and recreating the squashfs, or better yet, use chroot on /var/squashfs and run "apt-get install [package_name]". Then you will have to recreate the squashfs image. Either way, you will need to run mksquashfs any time you want to modify something. The command usage is pretty straight forward, it simply takes a while to run - even on my quad core. For a more detailed, step by step guide on how to add packages to a RAM session permanently, see the "Performing System Updates/Changes" section of the howto. It's actually pretty easy if you use the script I uploaded.

> **gameguy said:**
> Also, uncompressed (compressed is 1.1 GB), how much would squashfs be (or the equivalent uncompressed)?

This should give you a clue:

```
sudo du -hcs --one-file-system / --exclude=/dev/* --exclude=/tmp/* --exclude=/sys/* --exclude=/proc/* --exclude=/home/*
```

Or if you've already done it, you can check the size of your /var/squashfs.

> **JohnnyC35 said:**
> maybe it would help, rather than move everything to RAM, move certain directories to RAM as long as their resetting doesn't kill anything.

I had started a thread with that in mind. I'll see if I can find it ...

here it is:
[http://ubuntuforums.org/showthread.php?t=1413653](http://ubuntuforums.org/showthread.php?t=1413653)

Cool idea.

---

### Post by mbsullivan on 2010-06-22
> Making /root a tmpfs filesystem was a great idea to finish the benchmarks. It seems to have worked. Unfortunately, because it is using SWAP a lot more now, the speed of individual tests is closer to 5MB/s, far slower than even a regular hard drive.


That's too bad, but not unexpected. Is your vm.swappiness set to 100? These benchmarks must just use a ton of temporary diskspace.

If all of the files reside in one directory, you could just symlink it to a directory on the harddrive. This might be an effective (though hackish) way to simulate storing only the "folders you want to" in RAM.

Mike

---

### Post by terminator14 on 2010-06-22
> **mbsullivan said:**
> That's too bad, but not unexpected. Is your vm.swappiness set to 100? These benchmarks must just use a ton of temporary diskspace.

My swappiness is 60, the default of Ubuntu. My SWAP only gets used if I run out of RAM completely. 

All the tests in the phoronix benchmark for disk have completed now on my RAM session (other than the ones that failed to complete). I will post the results when I run them again on my regular Ubuntu in such a way as to have the results side by side on the same page.

---

### Post by gameguy on 2010-06-23
> **terminator14 said:**
> 
Because any packages you install are normally installed into places like /sbin, /bin. and /usr and such, with their settings stored in /etc (all of which are in RAM), and because the squashfs image cannot be directly edited (AFAIK), you will have to modify the folder you created (/var/squashfs in my howto) by either installing the packages you want on your main system and recopying everything to /var/squashfs, and recreating the squashfs, or better yet, use chroot on /var/squashfs and run "apt-get install [package_name]". Then you will have to recreate the squashfs image. Either way, you will need to run mksquashfs any time you want to modify something. The command usage is pretty straight forward, it simply takes a while to run - even on my quad core. For a more detailed, step by step guide on how to add packages to a RAM session permanently, see the "Performing System Updates/Changes" section of the howto. It's actually pretty easy if you use the script I uploaded.


I would use your script but since I need access to the internet on the RAM system, and the reason I want to update the system is .so synaptic can update certain packages which will let me access the internet, it doesn't work (the mounting and copying works, but I can't connect to the internet.

Actually, turns out I was trying to fix wireless, because it turned out that internet still works on the laptop when running through ethernet.

---

### Post by gameguy on 2010-06-23
It seems to be working for ethernet and wireless now that I tried the idea.
However, it comes up with an an error (see attachment) every time I boot (around 1-2 minutes after login). I am assuming that this means that something happened that wasn't supposed to which will stop me from doing something.
Does anyone know if there is a way to keep things like settings stored on hard drive while the actual programs are stored in RAM (because I was pretty sure that the settings were stored in /home/user)?
And can't you put your mounting and bonding stuff in /etc/fstab so /home/user/ would be writing these settings to disk as well as RAM?

---

### Post by gameguy on 2010-06-23
other error in this attachment.

---

### Post by terminator14 on 2010-06-23
I ran all disk tests from phoronix suite on both again. Some failed to complete, but here are the majority of those tests side by side.

[http://global.phoronix-test-suite.com/index.php?k=profile&u=root-13449-9640-26627]("http://global.phoronix-test-suite.com/index.php?k=profile&u=root-13449-9640-26627")

Again, the results are a mix because some tests have to use SWAP instead of just RAM, slowing them down considerably. This demonstrates that if you are to follow the guide, you should have enough RAM for your OS not to need to use SWAP or you may end up with a slower system than you started off with. This of course doesn't mean you should disable your SWAP altogether, since it gives you a safety net - if you run out of RAM, your system may slow down using SWAP but it won't crash like it would with completely no SWAP.

> **gameguy said:**
> It seems to be working for ethernet and wireless now that I tried the idea.
However, it comes up with an an error (see attachment) every time I boot (around 1-2 minutes after login). I am assuming that this means that something happened that wasn't supposed to which will stop me from doing something.

First thing I'd try there is to chroot /var/squashfs (you say the internet works now right?) and do a "apt-get update" and an "apt-get upgrade" to see if any of your packages need updating. Then you will need to rerun mksquashfs to recreate the squashfs image and then boot from it. Other than that, I'm not quite sure what could be the problem - especially since normally having outdated packages doesn't make any such popups appear.

> **gameguy said:**
> Does anyone know if there is a way to keep things like settings stored on hard drive while the actual programs are stored in RAM (because I was pretty sure that the settings were stored in /home/user)?

Most user specific settings are stored in /home/user in invisible folders. That is why the guide goes through modifying /etc/fstab to mount /home on startup to a hard drive. This will ensure anything on your desktop, in your music/pictures/documents folders, and user specific applications settings (your entire /home) will be stored on a hard drive, keeping the data alive past a reboot.

> **gameguy said:**
> And can't you put your mounting and bonding stuff in /etc/fstab so /home/user/ would be writing these settings to disk as well as RAM?

I think creating a way for the system to simultaneously write to RAM and disk would require something complex (am I wrong?) and if you simply want to store your /home on the hard drive, it is unnecessary. This is because your hard drive is fast enough to open an mp3 for reading (playing) or a text file for editing without the user noticing too much of a lag, while at the same time giving the user the ability to save it directly to the hard drive. Other than the user specific settings mentioned above, there's not really much in your /home that the OS needs to access on a regular basis that would slow it down.

> **gameguy said:**
> other error in this attachment.

npviewer.bin always crashes for me too. It is related to flash somehow, but flash seems to function fine even immediately after the crash. I tried to look up any relation of the error to a squashfs filesystem but found nothing so I kind of just ignore it for now.

---

### Post by mbsullivan on 2010-06-23
> 
Again, the results are a mix because some tests have to use SWAP instead of just RAM, slowing them down considerably. This demonstrates that if you are to follow the guide, you should have enough RAM for your OS not to need to use SWAP or you may end up with a slower system than you started off with. This of course doesn't mean you should disable your SWAP altogether, since it gives you a safety net - if you run out of RAM, your system may slow down using SWAP but it won't crash like it would with completely no SWAP.

That's definitely true. Not crashing is always a plus, though... I think that setting to a swappiness of 100 is probably a good idea in practice.

Think about it... You'll maybe take a 5-10% penalty off of CRAZY FAST, but you'll extend the effective use of your available RAM by 20-30% perhaps. Therefore, you'll hopefully never go down the dark and scary road to CRAZY AWFUL.

Is it me, or did the Kernel Compilation unexplainably get 2s better? It now beats out the normal HD. That didn't used to be true.

Mike

PS: I'm completely making these numbers up, but they seem reasonable to me this morning. :) Linux memory management seems very much like black magic!

---

### Post by JohnnyC35 on 2010-06-23
Going to try the great tmpfs experiment. Put as many directories in  tmpfs and still be able to do my day to day stuff without running swap  or rebooting. Should be doing this after the weekend after I get my SSD :p  and my new RAM (4Gb) :KS
Here's the list I have of directories I have that I think are safe (not  worried if I lose any info in /home atm) and if you know of other safe  ones let me know :)

For any new exciting developments and benchmarks I will continue on                                             "Looking to add more tmpfs" -> [http://ubuntuforums.org/showthread.php?p=9502298#post9502298](http://ubuntuforums.org/showthread.php?p=9502298#post9502298)
> 
/home/   
/media
/tmp
/usr/src/
/var/cache  
/var/cache/apt
/var/cache/apt/archives/  
/var/cache/apt/archives/partial
/var/crash
/var/lib/dhcp3
/var/lock
/var/log  
/var/log/apt  
/var/run
/var/spool/cups
/var/tmp  
Thanks ):P

---

### Post by terminator14 on 2010-06-25
> **mbsullivan said:**
> I think that setting to a swappiness of 100 is probably a good idea in practice.

Think about it... You'll maybe take a 5-10% penalty off of CRAZY FAST, but you'll extend the effective use of your available RAM by 20-30% perhaps. Therefore, you'll hopefully never go down the dark and scary road to CRAZY AWFUL.

I guess that would be an effective way to handle things if you are short on RAM. If your RAM spills over into SWAP, everything could get slow (and probably will), but if swappiness is set high, it is likely to only move things to SWAP that get rarely used (as I understand it) so it might be a good idea.

> **mbsullivan said:**
> Is it me, or did the Kernel Compilation unexplainably get 2s better? It now beats out the normal HD. That didn't used to be true.

Ya the results differ a bit everytime. I guess it depends on what else the CPU is working on at the time. I pretty much left my machine alone for the duration of the benchmarks (mostly because I ran them overnight) and tried not to run any software in the background at the time, but who knows when Ubuntu is scheduled to check for an update or perform some other action that takes CPU cycles away from compiling for the benchmark.

---

### Post by Jonny87 on 2010-06-27
First of all if this has been brought up please point me to as I've already had a breif look through the pages but didn't find it.

Sorry if this is a stupid question but does the Trial Desktop on a CD boot into RAM? I ask this not knowing alot bout this sort of thing because I noticed it has a "filesystem.squashfs" file on it but have never noticed fast speeds like I get when booting from a Puppy Linux CD. And if not is there a way to modify the CD files/image so that it does boot to RAM?

---

### Post by terminator14 on 2010-06-28
> **Jonny87 said:**
> First of all if this has been brought up please point me to as I've already had a breif look through the pages but didn't find it.

Sorry if this is a stupid question but does the Trial Desktop on a CD boot into RAM? I ask this not knowing alot bout this sort of thing because I noticed it has a "filesystem.squashfs" file on it but have never noticed fast speeds like I get when booting from a Puppy Linux CD. And if not is there a way to modify the CD files/image so that it does boot to RAM?

No, the CD does not copy itself to RAM. What it does is boot into a filesystem that is a merge between your RAM and your CD. What that means is that when you run an application from the live environment, it will run it from the CD. When you save a file to the Desktop (actually anywhere in /) it saves this into your RAM (because CDs are generally readonly). This gives you the ability to temporarily modify your filesystem in a live environment even though you are running it from a readonly CD. Because most of your applications are still being run directly from the CD (which is relatively slow even compared to a hard drive), the speed of a live CD environment is normally considered slower than a regular install to the hard drive.

Getting a live CD to copy into RAM was actually something I looked into a while back, and was able to do it successfully using this guide:

[https://wiki.ubuntu.com/BootToRAM]("https://wiki.ubuntu.com/BootToRAM")

---

### Post by Jonny87 on 2010-06-28
> **terminator14 said:**
> No, the CD does not copy itself to RAM. What it does is boot into a filesystem that is a merge between your RAM and your CD. What that means is that when you run an application from the live environment, it will run it from the CD. When you save a file to the Desktop (actually anywhere in /) it saves this into your RAM (because CDs are generally readonly). This gives you the ability to temporarily modify your filesystem in a live environment even though you are running it from a readonly CD. Because most of your applications are still being run directly from the CD (which is relatively slow even compared to a hard drive), the speed of a live CD environment is normally considered slower than a regular install to the hard drive.

Getting a live CD to copy into RAM was actually something I looked into a while back, and was able to do it successfully using this guide:

[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

Thanks for that. Have checked it out and saved the pages. Will spend some time this week perhaps seeing if I can get it to work.

---

### Post by ytaews on 2010-06-29
This is a brilliant idea. I'll be purchasing some RAM on Friday and giving it a go over the weekend.

---

### Post by doixanh on 2010-07-02
I followed the thread and it's working on my laptop system. Since I has only 2GB RAM I installed a CLI Ubuntu and installed only the packages I need. The squashfs image file is only 480MB. However since it's a laptop the HDD is slow (5400rpm) and it reads at 22MB/s only :D Anyway after loading the squashfs into tmpfs it's fast, really :D

Thank you Terminator14.

---

### Post by ytaews on 2010-07-02
My mistake - my problems are with my regular lucid installation.

---

### Post by terminator14 on 2010-07-02
> **doixanh said:**
> I followed the thread and it's working on my laptop system. Since I has only 2GB RAM I installed a CLI Ubuntu and installed only the packages I need. The squashfs image file is only 480MB. However since it's a laptop the HDD is slow (5400rpm) and it reads at 22MB/s only :D Anyway after loading the squashfs into tmpfs it's fast, really :D

Thank you Terminator14.

Glad it worked for you. :p

---

### Post by terminator14 on 2010-07-25
After using the RAM session for a while longer, I noticed that whenever I run "apt-get update" in the chroot environment, and recreate the squashfs session, if there was an update to the kernel (a new version was released), my grub menu during boot would still show the old version. After a bit of digging to find where this was coming from, it turns out that since I use the /boot of the original Ubuntu, which I do not keep up to data (which does not have the new kernel), the kernel never updates. There are 2 ways to fix this: a hack job and a proper way.

[SIZE="4"]**Hack Job**[/SIZE]

This involves updating the original OS (Non RAM-session) so that it downloads the new kernel to its /boot folder. This can be done either directly by booting into it, or from the chroot environment by running ./lucidchroot.sh -L, and running "apt-get update && apt-get dist-upgrade". After this, you will need to boot into the new kernel, open a terminal, and run "sudo update-grub". This is because /etc/grub.d/50_RAMSESS uses $(uname -r) (the currently running kernel) to create the RAM session grub entry.

If you don't feel like booting into the old, slow OS just to run update-grub, you can also edit the /etc/grub.d/50_RAMSESS file in the chroot environment (where your grub gets its /boot files) and replace the $(uname -r) instances with the new kernel version. Check /usr/src for the latest linux-headers-* file. DO NOT use the "linux-headers-" part of the file name, just replaced $(uname -r) with the number (and "-generic" if necessary) so that it looks like the same form as the "uname -r" command would give you. Once you are done messing with this file, save it and run update-grub. Reboot to see if the grub menu changed.

To avoid changing the /etc/grub.d/50_RAMSESS file manually to the kernel version each time the kernel updates, try using the following 50_RAMSESS file:

```
#!/bin/sh -e

KER_NAME=$(ls /usr/src/ | sort -n | grep linux-headers | grep generic | tail -1 | sed 's/linux-headers-//')

if [ -z "$KER_NAME" ]
then
        KER_NAME=$(uname -r)
fi

cat << EOF

menuentry "Ubuntu, Linux $KER_NAME to RAM" {
        set root='(hd0,2)'
        linux (hd0,1)/boot/vmlinuz-$KER_NAME boot=live toram=filesystem.squashfs apparmor=0 security=""
        initrd (hd0,1)/boot/initrd.img-$KER_NAME
}
EOF
```

The major disadvantage to this method is that you unnecessarily have to update the old OS, even if you rarely boot into it just to keep the kernel up to date. This means you either need to know the names of the kernel packages that need to be updated so that you only update them and no other packages, or if you are lazy, you will need to update a large number of packages just to get a small kernel update.

[SIZE="4"]**Proper Way**[/SIZE]

The best way to do this is to move your /boot to a separate partition and mount it at startup in /etc/fstab. Point grub to that instead of the original OS. This is very similar (almost exactly the same) as the steps taken in the howto for moving the /home folder to a different partition. You may also have to modify the lucidchroot.sh script to mount /boot so that any updates effect the right /boot folder.

For myself, I did the hackjob because it was faster and simpler. The proper way however is more complicated at first, but once you do it you never have to worry about kernel updates not making it to your grub again.

---

### Post by terminator14 on 2010-07-25
When I was writing the howto, I tried to keep it more or less organized so that it was easy enough to follow. Since then however, there have been many things I discovered which I have added to the howto, and in the comments section. Unfortunately, the more I add, the less organized the howto seems to get. Hopefully when Ubuntu 10.10 comes out, I'll run though this howto again to do the same on it, and rewrite the howto to make it more organized (if I have the time). For now, sorry if anyone is confused about some parts of it - if you have questions I'd be glad to try to answer them.

---

### Post by sikander3786 on 2010-09-17
Definitely worth a try. I'll try and see how much a difference does it make. Will my install be super fast...?

---

### Post by herryyan on 2010-09-17
okay... nice tips dude... 
i'll try it soon..

---

### Post by terminator14 on 2010-09-18
> **sikander3786 said:**
> Definitely worth a try. I'll try and see how much a difference does it make. Will my install be super fast...?

Depends what you mean by install. The process takes a while, but once you get the hang of it, it's not that long. Any application you install in your ram session after that, assuming it's not installed in your /home (which most aren't) will be installed very fast. If you are using apt-get or a similar package manager to download the app from a repository however, the download does not depend on your computer's speed so it will take as long as it always has (until it gets to installing).

---

### Post by dcstar on 2010-09-18
> **terminator14 said:**
> 
.........
Unfortunately the downside of this was that the speed of my Windows 7 now made my Ubuntu 10.04 feel slow. The first thought that came to mind was of course to create another partition on the large, 160GB SSD and move my Ubuntu there. **In order to maintain the SSD's fast speeds however, TRIM was required.** TRIM is something that keeps an SSD running at its top speed. Without it, an SSD will slowly slow down while being used. TRIM is built into Windows 7, so I had no problems with my SSD in Windows, but, from what I've read, TRIM did not make it into the kernel Lucid uses by 1 day. 

I had a choice here. I could either find the patched kernel that included TRIM support, and replace my existing kernel with it (messing with the kernel is something I've never done as I've never had the need to), or I could take the opportunity to make my Ubuntu work even faster than the SSD could allow.
...........
I'm no Linux expert


TRIM is only of real benefit if the SSD is constantly pushed towards 100% usage as the internal reallocation algorithm that spreads the use of writes requires vacant blocks (that it knows about) to use.

There is no short-term problem whatsoever in using a SSD for Linux without a TRIM supported kernel, all it means that there **might** be some issues with **write speed** after a significant amount of usage, and if that is an issue for a particular user then installing a TRIM kernel is not that difficult.

If people want to make their Ubuntu "Insanely fast" then simply do two hardware things (there is little need to do anything else):
[LIST=1]
[*]Install as much RAM as you can afford
[*]Use a SSD and leave ~30% of it unused
[/LIST]
My 10.04 system boots from my SSD in just a few seconds, my system automatically uses the 4GB RAM I have effectively and efficiently without any mucking around of system configuration.

---

### Post by terminator14 on 2010-09-18
> **dcstar said:**
> TRIM is only of real benefit if the SSD is constantly pushed towards 100% usage as the internal reallocation algorithm that spreads the use of writes requires vacant blocks (that it knows about) to use.

There is no short-term problem whatsoever in using a SSD for Linux without a TRIM supported kernel, all it means that there **might** be some issues with **write speed** after a significant amount of usage, and if that is an issue for a particular user then installing a TRIM kernel is not that difficult.

If people want to make their Ubuntu "Insanely fast" then simply do two hardware things (there is little need to do anything else):
[LIST=1]
[*]Install as much RAM as you can afford
[*]Use a SSD and leave ~30% of it unused
[/LIST]
My 10.04 system boots from my SSD in just a few seconds, my system automatically uses the 4GB RAM I have effectively and efficiently without any mucking around of system configuration.

This is true. And having an SSD to install Linux on is definitely much easier, not to mention keeping it up to date is hassle free. For me however, the idea of being able to do this awesome setup - something Windows couldn't do in a million years, is worth the trouble. This also allows me to install all the packages I want without wondering if I'm ever going to need them later, since they will disappear later anyways as soon as I reboot. This does mean however that if I want to keep a package, I have to install it again and recreate the filesystem image, but with my scripts it's pretty quick and painless and it turns out I install more useless packages (to see if they do what I think they do - only to realize they're not what I'm looking for) than actual packages I would use on a regular basis.

I am also a bit paranoid. To the point where if I have a laptop, it has to be plugged in all the time or the fact that it's going to run out of battery is always in the back of my mind eating at me. Same with SSDs - if there's a chance that my machine will start to run slow if I fill up the SSD (I might not notice right away that I filled it up) and TRIM is the fix for my paranoia, then TRIM is what I need. If I can't get that - I will find another way to run my OS that will give the benefits of an SSD, but not the downside of always having to worry of it becoming more and more slow. If I was unable to do this with RAM, recompiling the kernel with TRIM support to use on my SSD would be next on my list to get a fast OS.

---

### Post by Andy06 on 2010-10-14
Excellent idea (the original post). I always wondered if OSes could be made to run from RAM.

I have a hypothetical question, is it possible to have a "normal" install run from RAM? What I mean is, if anything is then changed/installed in the RAM, it gets write cached and then written in the background seamlessly to the HDD so that changes are persistent?

Also, most importantly, does a similar "Run from RAM" guide exist for Firefox (just the app, so that Firefox is superfast at loading) and for LiveUSBs? (Already saw [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM) but it is old and sort of complicated).

Why doesn't the Live system auto detect and load itself into RAM anyway? It is tiny enough to do it. At the very least, it should copy itself into Swap space entirely (it detects and uses swap partitions on your HDD anyway)

---

### Post by NightwishFan on 2010-10-14
You can put any file that fits into /dev/shm which is virtual memory. Please note anything placed in there will be deleted on reboot!

Placing an application that is not standalone I do not recommend. Just do not do it. (I use it when I have to do work on something that is small, but really io bound like a small game that runs in it's own folder)

---

### Post by Andy06 on 2010-10-14
What about LiveUSB from RAM? Possible?

---

### Post by Sylslay on 2010-10-14
exelent post!!!! THX

Would be interesting to do

install ubuntu on usb steak (sorry Andy06),

and than load that to ram.

Will be the faster OS booted on old machine (with usb 2.0 interface) ever!!!!, 

just by use fast 4/8GB pendrive and all this IDEAS! and old pc with 2GB DDR or DDR2 ram.

If some one can make image of that kind of system *img
and "end user" use only tool like universal-usb-creator, that will be AWSOME !!!

But, how update that kind of OS?

---

### Post by Andy06 on 2010-10-14
> **Sylslay said:**
> exelent post!!!! THX

Would be interesting to do

install ubuntu on usb steak (sorry Andy06),

and than load that to ram.

Will be the faster OS booted on old machine (with usb 2.0 interface) ever!!!!, 

just by use fast 4/8GB pendrive and all this IDEAS! and old pc with 2GB DDR or DDR2 ram.

If some one can make image of that kind of system *img
and "end user" use only tool like universal-usb-creator, that will be AWSOME !!!

But, how update that kind of OS?

I din't understand. Why sorry? :)

Live USBs cannot be updated even when they're not running from RAM. It is a read only "live" system. You might be able to update stuff if you use persistance squashfs files but even then it may not be ideal. Live USBs aren't really meant to be updated since they're not a primary use system. Their only purpose is demonstration, testing and portable/travel use

The guide I linked to above shows how to do this but is a bit complex (terminal commands) and is also a bit old. I'm pretty sure there has got to be a much easier way. The whole Live system is a tiny 700MB, with flash drives and even unobtrusive SD cards (that you can stick into a laptop and forget about) coming in 32GB for quite cheap, you will literally lose nothing by having a Live Ubuntu on there permanently :D

---

### Post by terminator14 on 2010-10-14
> **Andy06 said:**
> Excellent idea (the original post). I always wondered if OSes could be made to run from RAM.

I have a hypothetical question, is it possible to have a "normal" install run from RAM? What I mean is, if anything is then changed/installed in the RAM, it gets write cached and then written in the background seamlessly to the HDD so that changes are persistent?

Perhaps there is a low level, efficient way to do this but I'm not sure what that could be. The best thing I can come up with is a hack that uses a slightly modified version of my process. If you were to have an rsync job run once every few seconds, or once a minute to sync your RAM Session with /var/squashfs, it may accomplish what you are talking about. The alternative to running every few seconds is to have it somehow be event driven and run rsync whenever a part of the filesystem is modified. This can cause too many rsync jobs to run at once though if the filesystem is being heavily modified.

The downside of the above process is that:

1. Modifying /var/squashfs has no effect until you actually recreate the squashfs image, so whenever you reboot, you would have to take the time to recreate the image. This can be written to be done automatically (on reboot, a script would run to recreate the image) but that would still mean your reboot would take 5 minutes or more while it recreates the image. Of course you could bypass the process in such a case and quickly reboot, but you would then need to still recreate the image when you boot up and restart once more.

2. If the rsync was interrupted by an unexpected power loss, the system could become in an inconsistent state. By that I mean that some files got update and some didn't. You couldn't continue the update, since the RAM Session would be gone at that point. This could cause some problems. The good news however is that Linux's stability makes sure that unexpected power failures due to the OS freezing and such are not very common. I guess a case could also be made that the exact same thing happens to just a regular OS during a power failure, so this problem may not be unique to our situation.

> **Andy06 said:**
> 

Also, most importantly, does a similar "Run from RAM" guide exist for Firefox (just the app, so that Firefox is superfast at loading) and for LiveUSBs? (Already saw [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM) but it is old and sort of complicated).

I think for single applications, the best solution is to use preload ([http://sourceforge.net/projects/preload/]("http://sourceforge.net/projects/preload/")). I've hear of preload before, and even tried to use it once, but I didn't stick with it long enough to see any results so I don't really have any first hand experience using it.

For Live USBs or CDs, ([https://wiki.ubuntu.com/BootToRAM]("https://wiki.ubuntu.com/BootToRAM")) is basically the only article I'm aware of to do that. I followed it once (I think it was on an Ubuntu 9.04) and have a disk somewhere that can copy itself into RAM when it boots, but you are right it was pretty complicated. And back then, it used to get updated with every new version of Ubuntu that came out, but now it looks like it has fallen behind a bit. If I have time I'll see if I can do something about that. I think I started a script to speed up the process outlined on that page back then and if I'm far enough along on it (and I can find it), maybe I'll update it and throw it up online.

> **Andy06 said:**
> Why doesn't the Live system auto detect and load itself into RAM anyway? It is tiny enough to do it. At the very least, it should copy itself into Swap space entirely (it detects and uses swap partitions on your HDD anyway)

I have always wondered why they don't make this as one of the options they offer for their Live CDs, but I think the reason they don't do it by default is that Ubuntu still tries to be something that can run on any machine (even older ones) and older machines don't have the RAM to accomplish this (the CD is what, like 700MB?). Ubuntu also tries to be simple, simple enough for "regular people" to use. I guess the development team thinks that most people would have no idea what a ToRAM feature would mean if they spent the time to develop it, and cluttering up the Live CD boot menu with another option may confuse those people.

If they were to make this automatic however, then some people (anyone with enough SWAP or enough RAM) would see a large chunk of their SWAP or RAM being used while others (that don't have enough SWAP or RAM) would see a relatively little part of their SWAP or RAM being used. This may cause people to complain about how much RAM or SWAP Ubuntu uses, so Canonical would have to somehow get the message across to everyone that uses the live CD that it does this to speed up their live CD. It just sounds like a complicated thing for them to accomplish politically, rather then technically.

> **Sylslay said:**
> exelent post!!!! THX

Would be interesting to do

install ubuntu on usb steak (sorry Andy06),

and than load that to ram.

Will be the faster OS booted on old machine (with usb 2.0 interface) ever!!!!, 

just by use fast 4/8GB pendrive and all this IDEAS! and old pc with 2GB DDR or DDR2 ram.

If some one can make image of that kind of system *img
and "end user" use only tool like universal-usb-creator, that will be AWSOME !!!

But, how update that kind of OS?

Installing Ubuntu to a USB and making itself copy to RAM upon boot does sound interesting, but it may take some time messing with grub to get this working right in order for this to be portable to other computers as well.

As for updating such a solution: about 2 days ago, I opened another thread on the topic of speeding up Ubuntu using RAM that basically updates and simplifies the process. It includes ways to update, modify, and do whatever else you may want with or to the RAM Session, and it is very easy to use (at least I think so). Since it was posted in the Tips and Tricks section however, it needs to be examined by a moderator before it can be made public. As soon as it's online, I'll update my HOWTO to say it's a bit outdated (it still works but there's a better way to do it - the main process hasn't changed however) and post a link to the new thread. That may answer your question.

---

### Post by Sylslay on 2010-10-14
Presistant Ubuntu works until get "flat out" ,
mean that after fiew updated is broken anyway.

So, Would be nice to heave at list opiton on liveusb  "toram"  just for compare it speed.

Today I will finly try install ubuntu on USB key, thx forum for that msg:

[http://ubuntuforums.org/showthread.php?t=1596497](http://ubuntuforums.org/showthread.php?t=1596497)

Tomorrow I will try understood what is wirten above and try copy 
usb installtion toram, :guitar:

---

### Post by terminator14 on 2010-10-17
> **Andy06 said:**
> Also, most importantly, does a similar "Run from RAM" guide exist... for LiveUSBs?

Using a combination of the newly updated [https://help.ubuntu.com/community/LiveCDCustomizationMaverick]("https://help.ubuntu.com/community/LiveCDCustomizationMaverick") and the old [https://wiki.ubuntu.com/BootToRAM]("https://wiki.ubuntu.com/BootToRAM") articles, I was able to put together a script to take an ubuntu iso and give it a toram option. I tested it using the amd64 iso, and ran the script from the same (amd64) Ubuntu. It should work for 32 bit Ubuntu iso too, but keep in mind:

[QUOTE=https://help.ubuntu.com/community/LiveCDCustomizationMaverick]The architecture (Amd64 or i386) to be stored on the LiveCD should be the same as the architecture used to perform the customization, or the LiveCD may not run. It is not trivial to customize an AMD64 LiveCD using an i386 operating system, for example.[/QUOTE]

The final result is an .iso file. Once it is created, you can either burn it to a CD (obviously), or use whatever method you normally use to create a live USB from an .iso.

Although the script was written using an article that explains how to Customize the LiveCD, it doesn't actually let you customize anything. It simply does what it needs to do to make the .iso have a toram option.

I'll probably start a new thread to post this script just so people can find it more easily if they want it.

PS. There's nothing more fun than dealing with linux bootloaders. For this script, I was trying to figure out how to add a menu entry to the live CD bootloader. Sounds simple enough: read what the menu actually says during boot and grep for those words on the CD. That'll give you where the boot menu items are set. Add another entry and you're done. Accomplishing this however is a different story. When looking on the CD, there's a /boot folder and it only makes sense that anything related to booting the CD is there. If you grep all the files in it for one of the menu entries, you'll come across 2 files that have the menu layout (boot/grub/loopback.cfg, and /boot/grub/grub.cfg). Turns out NEITHER of them are right - the actual bootloader is in the /isolinux folder on the CD, not the /boot folder. Once you find the right file and add the menu entry, you gotta deal with the fact that the menu on Maverick doesn't show up during boot on the live CD unless you click a button. ALL documentation online says to make it show up, change "PROMPT 0" to "PROMPT 1" in /isolinux/isolinux.cfg. Turns out this does nothing, and the way to do this (which seems to be completely undocumented) is to change the hidden-timeout value in /isolinux/gfxboot.cfg from 2 to 0. Who designed this? It would probably make sense to me if I knew the reasoning behind this (along with how these bootloaders work and interact with each other since it seems there are several of them on the CD), but reverse engineering it, even with the help of the internet, is... fun. Hours and hours of fun.

Oh and word of warning: I try to build safeguards into any script I upload to the internet, including this one but a single slip up on my part can make the script kill a system. An example of this that I actually ran into while working on this script (it didn't kill anything but I noticed its potential to do so) is a line that read something like "rm -rf $TEMP_FOLDER_NAME/". If the $TEMP_FOLDER_NAME variable ended up being empty, the code that got executed would simply read "rm -rf /". I avoided the above problem by excluding the final /, but this shows how a simple command could inadvertently destroy a system. I've tested this script tons of times but be careful with it nonetheless. If you can, run it in a VM where it's safe. You could also run it from a live CD where, if it goes rouge for some reason, it won't kill anything.

---

### Post by terminator14 on 2010-10-22
Ok, as promised, the new updated page is finally online and I put a link to it at the top of the HOWTO. You can also see it by clicking here:

[http://ubuntuforums.org/showthread.php?t=1594694]("http://ubuntuforums.org/showthread.php?t=1594694")

---

### Post by TheeMahn2003 on 2011-01-03
terminator14, you are the bomb.  How about a little benchmark.  Solid State, eat your heart out ;)  Both benchmarks are from the same PC.

[Adata 32 GB SSD](http://img706.imageshack.us/i/adatassd.png/)
[[img]http://img706.imageshack.us/img706/9580/adatassd.th.png[/img]](http://img706.imageshack.us/i/adatassd.png/)

Thanks again,

TheeMahn

---

### Post by terminator14 on 2011-01-03
> **TheeMahn2003 said:**
> terminator14, you are the bomb.  How about a little benchmark.  Solid State, eat your heart out ;)  Both benchmarks are from the same PC.

[Adata 32 GB SSD](http://img706.imageshack.us/i/adatassd.png/)
[[img]http://img706.imageshack.us/img706/9580/adatassd.th.png[/img]](http://img706.imageshack.us/i/adatassd.png/)

Thanks again,

TheeMahn

HAHAHA. Nice stats! 1.7 GB/s - 16.0 GB/s is crazy!

I can't believe I never noticed how useful Ubuntu's default Disk Utility tool is - I didn't even know it could do benchmarking like that. Cool.

Ran a quick benchmark on my Intel x25-M 160GB drive - got some nice stats too. No where near as good as RAM will give of course, but still not bad.

---

