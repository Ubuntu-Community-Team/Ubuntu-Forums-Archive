---
title: "Installed 11.10 from USB but can't boot from Hard Drive"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by thailandtrev on 2012-03-17
I successfully installed Ubuntu on my kids computer a while ago and suggested it to a friend after failing to be able to install XP on his new machine HP Pavilion desktop. Apologies, I am an almost complete beginner to this and need a step by step 'idiots' guide. Some of this may or may not be relevant:
I have read this thread [http://ubuntuforums.org/showthread.php?t=1801336](http://ubuntuforums.org/showthread.php?t=1801336) but do not know how to gather the Boot Info Script to provide you with the similar information
Here's what I have managed to 'b*gger up' so far:confused:
His computer only had FreeDOS installed. When booting from the XP CD it loaded a load of files and then got the blue screen with a STOP: Ox000007B and a error message no fat32 installed. I followed the MS instructions to use fdisk to create a fat32 partition, this made no difference and then there appeared to be no way to get into DOS i.e. no DOS command line. It turns out the XP disk, although genuine, was an OEM version so not compatible with his new machine.
I downloaded 11.10 onto a USB stick, changed his BIOS settings and successfully installed it onto his empty hard drive, gave him a basic Ubuntu demonstration, launched Firefox, connected to the net etc, I then re-started the machine with the USB drive removed. When it re-booted, the screen turned 'Ubuntu' purple, but with no ubuntu logo/name or red dots, then multi coloured and then started 'pulsating' and nothing else happened.
I re-started again and checked the BIOS settings so it was booting from the Hard Drive - same again (a few times).
I re-inserted the USB stick, and moved this up in the boot order and ubuntu loaded fine again, but obviously running from the USB stick, any changes that we made earlier e.g. changing the 'home' page in Firefox were not retained.
I ran GPartition and it showed 2 partitions on the hard Drive and the USB stick. The main partition (I think sda) was not 'mounted' - so I mounted it. I then re-started the machine with the USB stick removed and ubuntu loaded (apparently from the hard drive_ - great I thought. This only happened once. A further re-start and ubuntu wouldn't boot. He is running off the USB for now. The other thread mentioned fdisk but if I have deleted DOS somehow, how can I get this again. I can open the  ubuntu terminal window run gpartition but that is about the extent of my skills. If you need the Boot Info Script/ other info, how do I get this?
Thank you in advance for your help!

---

### Post by thailandtrev on 2012-03-17
I'm in front of his computer now!
In GParted I have the following for the Hard Drive:
/dev/sda1  ext 4 927GB (17.6 used) Not Mounted Flags boot
/dev/sda2 extended 3.99GB Busy (at least 1 partition mounted) No Flags
  /dev/sda5 linux-swap 3.99GB Active No Flags

and for the USB stick
/dev/sdc1  fat32 Mount Point /cdrom Label PENDRIVE Flags boot, lba

I hope this helps!

---

### Post by thailandtrev on 2012-03-18
Bump - apologies if this is poor netiquette but I haven't received a reply and am already pushed down to page 5. Can anyone help?

---

### Post by HeroOfCanton on 2012-03-18
> **thailandtrev said:**
> Bump - apologies if this is poor netiquette but I haven't received a reply and am already pushed down to page 5. Can anyone help?

You can bump about once per 24 hours on these forums and be okay. Things do move fast.

Are you getting past the GRUB boot loader when you boot up from the hard drive? The problem you described sounds more like a video problem when Ubuntu tries to load than a bad MBR. Is it happening about the time you would expect the splash/login screens to be loading?

---

### Post by thailandtrev on 2012-03-18
When booting from the hard drive, I do not get GRUB bootloader, just straight to the purple, then multicoloured screen which then pulsates after about 10 seconds.
When booting from the USB, it boots (i.e. a load of white writing on a black background) then the purple screen with 'ubuntu' and the 5 white/ red dots as it loads.
How do I check the MBR from within Ubuntu or that I have GRUB bootloader? in the correct place on the hard drive?
Thanks

---

### Post by HeroOfCanton on 2012-03-18
Thinking about it, if you only have one OS you're not going to see the grub options anyways. You can check that grub has been installed by verifying the /boot/grub/grub.cfg file exists on the hard drive.

I'm assuming those exist, so let's take a look at your boot logs to what's happening when booting to the hard drive.

1) Boot to your live USB.
2) Mount the hard drive if it isn't already.
3) Browse to the /var/log directory *on the mounted drive*. (not your USB)
3a) Open a terminal in that directory (if you got there via the GUI)
4) Type this at your terminal prompt:
```
cat boot.log
```5) Paste the results here. Please place it within code tags (# button) for readability on the forums.

---

### Post by thailandtrev on 2012-03-18
Thanks Hero of Canton. I won't be in front of his machine until a few hours so I will do this later.

---

### Post by Harry.k on 2012-03-18
Hmm. . . . . Multicolour pulsating screen? Seems like a graphics problem. See if you can boot into verbose mode. When the loading screen comes, press ctrl-alt-f1.
The screen will show a verbose login screen in a minute. If it lets you login in verbose mode, it will be easier to pinpoint the problem.
Also, do paste the boot log.

---

### Post by oldfred on 2012-03-19
If you hold down shift key from BIOS until menu appears, you should get grub menu. Then you can edit it to add nomodeset which is the most common setting for video issues. If nVidia then it is definitely nomodeset, others may required some other setting.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

It you only have one large / (root) partition and you are booting ok then they must have solved a bug in grub that prevented it from booting from very large / (root) partitions. I normally suggest manual install with a / of 25GB and then the rest of the space for Ubuntu you want to use as /home.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by thailandtrev on 2012-03-22
Sorry, I haven't had time to get back to this! Please see the bootlog file below:
```
#Begin: Loading essential drivers ... done. 
Begin: Running /scripts/init-premount ... done. 
Begin: Mounting root file system ... Begin: Running /scripts/casper-premount ... done. 
done. 
stdin: error 0 
/init: line 7: can't open /dev/sr0: No medium found 
/init: line 7: can't open /dev/sr0: No medium found 
stdin: error 0 
/init: line 7: can't open /dev/sdb: No medium found 
/init: line 7: can't open /dev/sdb: No medium found 
stdin: error 0 
/init: line 7: can't open /dev/sdb: No medium found 
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Unable to find the persistent medium 
stdin: error 0 
/init: line 7: can't open /dev/sdb: No medium found 
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Unable to find the persistent home medium 
stdin: error 0 
/init: line 7: can't open /dev/sdb: No medium found 
/init: line 7: can't open /dev/sr0: No medium found 
stdin: error 0 
/init: line 7: can't open /dev/sdb: No medium found 
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Impossible to include the casper-sn Snapshot 
stdin: error 0 
/init: line 7: can't open /dev/sdb: No medium found 
/init: line 7: can't open /dev/sr0: No medium found 
stdin: error 0 
/init: line 7: can't open /dev/sdb: No medium found 
umount: can't umount /cdrom: Device or resource busy 
/init: line 7: can't open /dev/sr0: No medium found 
Warning: Impossible to include the home-sn Snapshot 
done. 
Begin: Creating debconf-communicate fifo mechanism ... done. 
Begin: Running /scripts/casper-bottom ... Begin: Moving mount points... ... done. 
Begin: Adding live session user... ... pwconv: failed to change the mode of /etc/passwd- to 0600 
done. 
Begin: Configuring fstab... ... done. 
Begin: Setting up swap... ... done. 
Begin: Setting up locales... ... Generating locales... 
  en_US.UTF-8... done 
Generation complete. 
done. 
Begin: Setting up automatic login... ... done. 
Begin: Setting hostname... ... done. 
Begin: Setting up console keyboard... ... done. 
Begin: Configuring gnome-panel-data... ... done. 
Begin: Configuring screensaver... ... done. 
Begin: Regenerating SSL certificate... ... done. 
Begin: Preconfiguring /etc/modules... ... done. 
Begin: Preconfiguring networking... ... done. 
Begin: Loading preseed file... ... done. 
Begin: Setting up init... ... done. 
Begin: Disabling user menu... ... done. 
Begin: Configuring accessibility options... ... done. 
Begin: Disabling update-notifier... ... done. 
Begin: Configuring power management... ... done. 
Begin: Enabling detection of crashes... ... done. 
Begin: Disabling unnecessary KDE services... ... done. 
Begin: Fixing language selector... ... Traceback (most recent call last): 
  File "/usr/bin/fontconfig-voodoo", line 102, in <module> 
    main() 
  File "/usr/bin/fontconfig-voodoo", line 88, in main 
    fc.setConfigBasedOnLocale() 
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/FontConfig.py", line 114, in setConfigBasedOnLocale 
    lang = self.li.getUserDefaultLanguage()[1] 
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py", line 244, in getUserDefaultLanguage 
    bus = dbus.SystemBus() 
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 202, in __new__ 
    private=private) 
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 108, in __new__ 
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop) 
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 125, in __new__ 
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop) 
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory 
Error in sys.excepthook: 
Traceback (most recent call last): 
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 88, in apport_excepthook 
    pr.add_proc_info() 
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 355, in add_proc_info 
    raise ValueError('invalid process') 
ValueError: invalid process 
 
Original exception was: 
Traceback (most recent call last): 
  File "/usr/bin/fontconfig-voodoo", line 102, in <module> 
    main() 
  File "/usr/bin/fontconfig-voodoo", line 88, in main 
    fc.setConfigBasedOnLocale() 
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/FontConfig.py", line 114, in setConfigBasedOnLocale 
    lang = self.li.getUserDefaultLanguage()[1] 
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py", line 244, in getUserDefaultLanguage 
    bus = dbus.SystemBus() 
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 202, in __new__ 
    private=private) 
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 108, in __new__ 
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop) 
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 125, in __new__ 
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop) 
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory 
done. 
Begin: Disabling trackerd... ... done. 
Using CD-ROM mount point /cdrom/ 
Identifying.. [1d17551b99903b3ca3cecdf0f924e6c9-2] 
Scanning disc for index files.. 
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures 
Found label 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)' 
This disc is called:  
'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)' 
Copying package lists...gpgv: Signature made Wed Oct 12 15:15:31 2011 UTC using DSA key ID FBB75451 
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" 
 Reading Package Indexes... 0%  Reading Package Indexes... 2%  Reading Package Indexes... Done  
Writing new source list 
Source list entries for this disc are: 
deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted 
Repeat this process for the rest of the CDs in your set. 
W: Skipping nonexistent file /cdrom/dists/oneiric/main/binary-i386/Packages 
W: Skipping nonexistent file /cdrom/dists/oneiric/restricted/binary-i386/Packages 
Begin: Possibly disabling update-initramfs (useless on a live CD)... ... chmod: /root/usr/sbin/update-initramfs: No such file or directory 
done. 
Begin: Grant administrative PolicyKit privileges to default user... ... done. 
done. 
done. 
Begin: Running /scripts/init-bottom ... done. 
 * Starting mDNS/DNS-SD daemon[194G[ OK ] 
 * Starting network connection manager[194G[ OK ] 
 * Starting configure network device security[194G[ OK ] 
 * Starting Mount network filesystems[194G[ OK ] 
 * Stopping Mount network filesystems[194G[ OK ] 
 * Starting Failsafe Boot Delay[194G[ OK ] 
 * Starting Bridge socket events into upstart[194G[ OK ] 
 * Starting configure network device[194G[ OK ] 
 * Starting System V initialisation compatibility[194G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
Checking for running unattended-upgrades:  
 * Stopping Failsafe Boot Delay[194G[ OK ] 
 * Stopping System V initialisation compatibility[194G[ OK ] 
 * Starting System V runlevel compatibility[194G[ OK ] 
 * Starting automatic crash report generation[194G[ OK ] 
 * Starting LightDM Display Manager[194G[ OK ] 
 * Starting ACPI daemon[194G[ OK ] 
 * Starting save kernel messages[194G[ OK ] 
 * Starting regular background program processing daemon[194G[ OK ] 
 * Starting deferred execution scheduler[194G[ OK ] 
 * Starting configure network device security[194G[ OK ] 
 * Starting configure network device[194G[ OK ] 
 * Starting CPU interrupts balancing daemon[194G[ OK ] 
 * Stopping save kernel messages[194G[ OK ]#
```

---

### Post by thailandtrev on 2012-03-22
The boot/grub/grub.cfg file does not appear in the file system.

Under boot/grub - I only have gfxblacklist.txt and grubenv.

---

### Post by oldfred on 2012-03-22
Added code tags, Please use code tags for any long dump of data or code. Paste, highlight and click on # in edit panel above your message.

That looks like a log from your USB boot. I thought you had it installed and had video issues. If you get video issues on the liveCD/USB you need to add nomodeset as part of the boot.

---

### Post by thailandtrev on 2012-03-22
Apologies, here is what I get when I type cat boot.log in the terminal
> cat: boot.log: No such file or directory
ubuntu@ubuntu:~$ 

---

### Post by oldfred on 2012-03-23
For whatever reason boot log is not where boot log is. See messages  and syslog for the info you see on the screen of the boot process when you delete quiet splash as kernel boot options.

Not sure what liveCD does as it only can write to memory, so I assume liveUSB does the same.

---

### Post by oldfred on 2012-03-23
Do you get two small symbols at the bottom of the screen for just a few seconds when booting from CD or USB key?

If booting from CD or USB press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option. Some times others options also required.

---

### Post by thailandtrev on 2012-03-23
oldfred
I am not sure where/ how to delete quiet splash as kernel boot option. I can only boot from the USB, I do not have grub as I only have ubuntu installed.
From the boot log posted earlier, the problem appears to be that it can't open /dev/sr0 or /dev/sdb, is /dev/sr0 where the MBR is supposed to be? When i boot from the USB the only bit that I can read is casper - premount,

---

### Post by oldfred on 2012-03-23
sr0 is the CD, so it is looking for a CD and fails which is normal. It then also looks for sdb and fails which may be normal or not as my system searches thru many drives and does not find them.

But if USB flash is promoted to sda as it is on some systems, not finding sdb (which then is hard drive) could be an issue. But if sda is hard drive then you should be ok.

The delete quiet splash is after you have installed to hard drive. It seems like you still are just booting or trying to boot from flash drive. What happens if you press any key as soon as it starts to load? Do you get a choice to press f6 and choose nomodeset?

You should get attached image at bottom of screen, as you start to boot from USB or CD. press any key as soon as you get this image.

---

### Post by thailandtrev on 2012-04-06
I have marked this thread as Solved to close it. Unfortunately I didn't manage to solve the problem. Whilst my mate was OK using the USB drive as a temporary solution, he decided (after all it's his computer) to buy a retail version of Windows 7 which is now installed and all working fine.

---

