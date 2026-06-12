---
title: "Installing GENTOO 2008.0 on a QEMU DISK IMAGE (and KDE4)."
date: 2008-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by JBSanchez on 2008-08-21
[color=blue][size=5]Installing GENTOO 2008.0 on a QEMU 
DISK IMAGE (and KDE4).[/size][/color]

A couple of years ago, I wrote a script to automatically install Gentoo 2006.0 from the Gentoo LiveCD. Recently, I trimmed the script to install Gentoo 2008.0 on a Qemu (virtual) hard-disk. I used the KVM version of Qemu, but everything should be the same for non-KVM Qemu. This guide was written for those using an AMD64 system, but other systems should be similar. Most of the necessary changes are obvious.

Download the following:

[[color=red]qemu-gentoo-2008.sh.bz2[/color]](http://linuxhelp.150m.com)
[[color=red]livecd-amd64-installer-2008.0-r1.iso[/color]](http://distfiles.gentoo.org/releases/amd64/2008.0/livecd/livecd-amd64-installer-2008.0-r1.iso) (696M)
[[color=red]portage-20080721.tar.bz2[/color]](http://distfiles.gentoo.org/snapshots/portage-20080721.tar.bz2)  from [distfiles.gentoo.org](http://distfiles.gentoo.org/snapshots/) (31M)

Although, I recommend the 2008-07-21 version of portage, because it has been checked and is known to compile KDE 4.0.5, you may wish to use the latest portage version which can be found here:

[[color=red]portage-latest.tar.bz2[/color]](http://distfiles.gentoo.org/snapshots/portage-latest.tar.bz2)  from [distfiles.gentoo.org](http://distfiles.gentoo.org/snapshots/) (31M)

```
mkdir /b 
```

The directory /b will be seen by Qemu/KVM as the hard-disk /dev/hdb.

```
mv qemu-gentoo-2008.sh.bz2 portage-20080721.tar.bz2 /b 
bunzip2 qemu-gentoo-2008.sh.bz2 
chmod +x qemu-gentoo-2008.sh 
/sbin/modprobe kvm-amd 
qemu-img create -f raw gentoo.img 10G 
qemu-system-x86_64 -boot d -m 256 -soundhw es1370 -usbdevice tablet \ 
      gentoo.img -cdrom livecd-amd64-installer-2008.0-r1.iso -hdb fat:/b & 
```

Although the Gentoo LiveCD recognizes the Qemu Cirrus Logic video card and sets the correct driver in the xorg.conf file, the X-server is unable to start the graphics environment (it turns out that the cirrus drivers have not been compiled). The screen flashes a few times and a window appears asking if you wish to see the X log. Say no, then OK and hit return a couple of times to get to the console. Once at the console, enter the command:

```
vi /etc/X11/xorg.conf 
```

Search for the string [color=red]cirrus[/color] and replace it with [color=red]vesa[/color]. 

Alternatively, you can also use the following commands to edit the xorg.conf file:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf-old 
awk '{print gensub(/cirrus/,"vesa","g")}' /etc/X11/xorg.conf-old > /etc/X11/xorg.conf 
```

After editing xorg.conf, start the window manager Xfce4 with:

```
startxfce4 
```

Open a terminal window in Xfce4. Then mount the first (and only) partition of /dev/hdb and run the script:

```
mkdir /b 
mount /dev/hdb1 /b 
``` (the script assumes /dev/hdb1 is mounted on /b)
```
/b/qemu-gentoo-2008.sh 
``` (run the script)

The script will partition the virtual hard-disk /dev/hda and set up Gentoo 2008.0 on /dev/hda3. Of course, these days you no longer need a swap partition and you never needed a boot partition. However, to keep in step with Gentoo we will have both. 

I would have usually formated /dev/hdb3 with the Reiser3 filesystem, however, this usually extremely reliable filesystem, has been deliberately sabotaged. This sabotage causes massive corruption of files after a short time. By comparison, I have used the Reiser3 filesystem for nearly ten years now and have never had any corruption, at all, on any of my many Reiser3 boxes.

When the script finishes, you should:

```
Shutdown the LiveCD. 
```

Then boot up Gentoo 2008.0 from the hard-disk, with:

```
qemu-system-x86_64 -m 256 -soundhw es1370 -usb -usbdevice tablet gentoo.img & 
```

[color=red]At this point you have a functional Gentoo system which uses the Xfce4 desktop.[/color]

The sound does not work because (since at least 2005) Gentoo has refused to compile the LiveCD kernel with the ALSA OSS emulation option. This means that the sound does not work for a few (very popular) older cards. The symptom of this problem is that the device /dev/dsp does not get created. This old, well-known problem, is easily fixed by recompiling your kernel with the following options:

```
Device Drivers  --->
    Sound  --->
        Advanced Linux Sound Architecture  --->
            <M> Sequencer support
            <M> Sequencer dummy client
            <M> OSS Mixer API
            <M> OSS PCM (digital audio) API
                [ * ] OSS PCM (digital audio) API - Include plugin system
           [ * ] OSS Sequencer API
           [ * ] Support old ALSA API
```

A new kernel will also stop the system loading every pata and sata module it can find.

The script adds 8139too and snd_ens1370 to /etc/modules.autoload.d/kernel-2.6 which causes the correct ethernet and sound kernel modules to be loaded at boot. To connect to the internet using Qemu's default networking, you need to connect to Qemu's DHCP server, which you do with the command:

```
dhcpcd eth0 
```

[color=red]Adding the KDE desktop to your Gentoo system.[/color]

First, you must uninstall the QT 4 libraries on the LiveCD with (you may ask why they are there):

```
emerge -C qt:4 
```

If you used the script, then this has been done for you.

If you want KDE4 (version 4.0.5), then hide the package.mask file [color=red](only for KDE4)[/color] with:

```
mv /usr/portage/profiles/{package.mask,hide-package.mask} 
```

If you want KDE3 (version 3.5.9), then do not hide the package.mask file.

Now you should check what happens in a dry run:

```
emerge -pv mesa 
emerge -pv kde-meta 
```

KDE 3.5.9 is chosen automatically if you did not hide the package.mask file and KDE 4.0.5 is chosen if you did.

Then you should download all the source files with:

```
emerge -f mesa
emerge -f kde-meta 
```

Now you should compile everything. This took somewhere between 12 & 16 hours on my box. I think that is good, considering that the compilation is being done in a virtual system. For KDE3 the following commands were necessary:

```
emerge mesa 
emerge flex 
emerge kde-meta 
```

For whatever reason, kdepim-meta-3.5.9 and related packages did not compile. Everything else did. If you need kdepim 3.5.9, you should use a version of portage different from portage-20080721.tar.bz2.

For KDE4 these commands were necessary:

```
emerge mesa 
USE="mdnsresponder-compat" emerge avahi 
USE="-doc" emerge glib 
emerge kde-meta 
```

Without the proper USE-variable KDE4's compositing is disabled at compile time. The stated reason is that the X-org development headers are missing. However, this is not true. You need USE="xcomposite" and even with this, compositing is not possible for older graphics cards, like the Cirrus Logic. The script qemu-gentoo-2008.sh now sets some USE-variables, like xcomposite, for you. You should check /etc/make.conf and see if you approve of the choices. Remember that the default USE-variables are listed in:

/usr/portage/profiles/targets/desktop/make.defaults

and your current configuration can be seen by typing:

```
emerge --info 
```

Now you need to configure KDE.

This is done by changing a line in your /home/gentoo/.dmrc file. 

For KDE4, change the line [color=red]Session=xfce[/color] to [color=red]Session=kde-4[/color].

You should save the downloaded files so that you can trash your virtual Gentoo system without losing them.

First, [color=red]shutdown Gentoo.[/color] Then mount the image gentoo.img with:

```
mount -o loop,offset=$((1124550*512)) gentoo.img /1 
```

[color=red]1124550[/color] is the number of sectors to the start of the 3rd partition. It comes from:

```
fdisk -lu
Disk /dev/hda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x934947c5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63      128519       64228+  83  Linux
/dev/hda2          128520     1124549      498015   82  Linux swap / Solaris
/dev/hda3         1124550    20964824     9920137+  83  Linux
```

Now you can copy files to and from the image. To save the downloaded files:

```
mkdir /gentoo 
cp -r /1/usr/portage/distfiles /gentoo 
```

Don't forget to [color=red]unmount your Gentoo disk image[/color] before booting Gentoo 2008.0.

```
umount /1 
```

So, what did I think of KDE4. Well, the main selling feature of KDE4, compositing, is turned off for older graphics cards like the Cirrus Logic. The system complains that: Required X extensions (XComposite and XDamage) are not available. KDE4 has more polished graphics, but it is missing some of the little features that made KDE3 so useable. The start "menu" is awful and it would be hard to use KDE4, if one was forced to use this grotesque feature. Thankfully, SuSE 11.0 has the old menu as an option. Things like the taskbar icons cannot be moved and some configuration options are poorer. Hopefully, KDE4 will catch up with KDE3 soon. However, at this point, KDE4 is definitely a regression.

If I get time I will write an article on how to transfer your virtual Gentoo 2008 system to a system using your real hardware.

For further information I recommend the [Gentoo installation manual.](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?full=1)

---

