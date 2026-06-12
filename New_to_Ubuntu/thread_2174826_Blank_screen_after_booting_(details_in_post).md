---
title: "Blank screen after booting (details in post)"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by linuxnovice on 2013-09-16
Hey,

Blank screen after booting is a very vague title, but please bear with me as I explain the details of my problem and the number of solutions I have tried. I built a new computer yesterday, the build details can be found [here]("http://pcpartpicker.com/user/shaun85/saved/2iyp"). The important parts relevant to this post are: Gigabyte GTX 770 2GB, Samsung 250 GB SSD, and WD 1TB 7200 HDD. I also have a Samsung Syncmaster 30" connected via HDMI and an Acer 24" connect via DVI. I have followed [lifehacker]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")'s instructions on dual booting Windows 7 and Ubuntu. This is how my hard drives are set up:

On SSD:
132 GB ntfs Windows 7
103 GB Ext 4 Ubuntu 12.04 LTS (Ext2FS)
2GB Swap

On HDD:
NTFS (for common data between Windows and Ubuntu)

I finished installing Windows 7 yesterday without too many problems. This morning I started to install Ubuntu 12.04 LTS. I was able to boot into the Live CD without any problems (it seems to have been using the nouveau driver) and complete installation. After I reboot, grub menu shows up with all the operating systems (btw I am able to boot into Windows 7 fine through grub). I select Ubuntu 12.04, but after that I just get a blank screen.

These are the things I've tried:
1) I booted into the live CD and install boot-repair and ran it. It said it's fixed something and gave me the [this]("http://paste.ubuntu.com/6114525/") URL. I rebooted and the problem remains.

2) Next, I tried to follow the instructions in [this]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it") post. However, after setting nomodeset, the screen dumps a bunch of stuff and then goes blank again. I do NOT get a login prompt. 

3) I downloaded the Nvidia GTX 770 driver for Linux 64bit onto a USB drive and booted into recovery mode thinking maybe I could install the driver and it would work. However, I am not able to mount the driver into flolder, because it says the filesystem is read-only, thus preventing me to create a folder for mounting. I does show the USB drive is present on sdc when I ran dmesg after inserting the drive.

I am doing all this while having both the monitors plugged in, however, all the boot menu stuff occurs only on the Acer monitor connected via DVI while the Samsung connected via HDMI becomes alive only after booting into Windows or Ubuntu live CD. So, basically I am stuck with a blank screen when I try to boot into Ubuntu, but I am able to boot into Windows fine. I can only get a login prompt when I boot into recovery mode (so if you guys need any info of the system I can get it from there, although I do not know how/where I would save it). The system is still new and I do not have a lot of stuff installed, so I am willing to try stuff that may end up with me having to reinstall everything including Windows (although I would prefer not to do it :) ). If any of you guys can help I appreciate it greatly.

Thanks and let me know if you need anymore information.

---

### Post by linuxnovice on 2013-09-16
Update:

Hey,

I have been working on this problem and just wanted to update my progress so that you guys had the latest information. I was able to boot into recovery mode and get root access. After enabling networking, I ran sudo apt-get update and sudo apt-get upgrade (after uncomming the partner links on sources.list). It upgraded/updated a bunch of stuff including stuff relavent to X. However, when I tried rebooting, it still went to a blank screen after selecting Ubuntu 12.04 on the grub menu. I will keep working and update this thread on my progress.

Thanks and any help is greatly appreciated.

---

### Post by linuxnovice on 2013-09-16
Update:

Hey,

I downloaded the nvidia linux x64 drivers for my graphics from [here]("http://www.nvidia.com/object/linux-display-amd64-319.49-driver.html") and put it on a flash drive. I booted into the Ubuntu 12.04 live cd and mounted the flash drive and the ssd (where Ubuntu is installed) and copied it over. Then I booted into the recovery mode again and installed the driver from there. The driver seemed to install properly. After installation, I rebooted and selected Ubuntu 12.04 from the grub menu, but still no sucesses. I still get a giant blank screen instead of the ubuntu logo followed by the login screen. I am not able to swtich to a text terminal too (ctrl+alt+f1). 

I am running out of ideas to try, hopefully someone can help me out.

Thanks.

---

### Post by CeejRab on 2013-09-16
Hello there LinuxNovice, 

You're doing good those are things we would've suggested anyway so keep plugging away. Someone will be along soon I'm sure, it doesn't usually take too long! 

I have some ideas but I'm really tight on time so I'll subscribe to this thread and get back to it a little later hopefully. Hang in there, you'll get help eventually! 

My best advice is since I believe you mentioned you don't mind re-installing, I would use gparted on the live cd to wipe your Linux partition and make it a fresh ext4 filesystem, and I would move the swap to a partition right next to it on the same drive, rather than jumping HD between the OS and the swap. 

Also I think I saw you have 32GB of swap? Dear me, the theory that the size of swap should be twice the amount of your ram has been out a while but the best Linux devs haven't been able to prove its value any more than lower swap sizes. I don't know if you're planning on running a server or virtual machines or what but I'm positive you'd do just fine with way way less swap area, I highly doubt you will even touch a fraction of your ram, so the swap wouldn't even be used ever. Just a side note! 

As for the black screen it could be a 64bit issue running on your custom PC, not sure, but I would use the 64 bit livecd and reinstall fresh and see how that goes. 

I'll get back later with more if I can, all the best to you!

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> Hello there LinuxNovice, 

You're doing good those are things we would've suggested anyway so keep plugging away. Someone will be along soon I'm sure, it doesn't usually take too long! 

I have some ideas but I'm really tight on time so I'll subscribe to this thread and get back to it a little later hopefully. Hang in there, you'll get help eventually! 

My best advice is since I believe you mentioned you don't mind re-installing, I would use gparted on the live cd to wipe your Linux partition and make it a fresh ext4 filesystem, and I would move the swap to a partition right next to it on the same drive, rather than jumping HD between the OS and the swap. 

Also I think I saw you have 32GB of swap? Dear me, the theory that the size of swap should be twice the amount of your ram has been out a while but the best Linux devs haven't been able to prove its value any more than lower swap sizes. I don't know if you're planning on running a server or virtual machines or what but I'm positive you'd do just fine with way way less swap area, I highly doubt you will even touch a fraction of your ram, so the swap wouldn't even be used ever. Just a side note! 

As for the black screen it could be a 64bit issue running on your custom PC, not sure, but I would use the 64 bit livecd and reinstall fresh and see how that goes. 

I'll get back later with more if I can, all the best to you!

Thanks a lot for your reply. The swap partition size is a suggestion by a friend. I will be using this computer for my P.hD computer science research and he suggested that there might be some programs that will automatically look for the swap partition. I agree it is overkill since I have 32GB of RAM! I might just erase it off the HDD. The problem with having swap on my SSD is this: my ssd size is 250 GB for which I've allocated 100GB for linux and rest for Windows. And, to my disgust, Windows is just eating storage space just for the OS! That is why I'm reluctant to put swap on my SSD. This begs the question, given that I have 32GB of RAM, perhaps I could just allocate maybe 1GB of swap on SSD and go with that?

Thanks.

---

### Post by CeejRab on 2013-09-16
Ok I see where you're coming from... I think!

With 32GB of ram I simply can't fathom any computing falling over that loft peak and into a swap area... Your friend may be right, some program may want to use swap and look for it on its own. In that case, you should have at least 2GB and I highly recommend it be on the same HD device as the OS partition. 

How much space is windows taking up? If you're not storing files, windows doesn't just "grow"... Lol

By the way... On a sidenote that you probably already know: If you're using Linux on a SSD drive, please please don't tell me you're using the EXT3 or EXT4 file system...... It's absolutely awful on SSD and can really damage the blocks because of the journaling methods the EXT3/4 systems use. It causes about 4-15% more writes to the HD on normal use and deleting files or high write requirement data can double the amount of writes. Basically it will wear your SSD out much faster than using a file system without journaling. EXT2 is safe because it doesn't have journaling, whereas EXT3 and EXT4 both include it. (End of humble opinion based on popular fact) lol

If you were going to consider reinstalling Ubuntu to try and fix the black screen, it might be good to consider switching and using ext2 (if you arent already, but the installer uses ext4 by default) at the same time when you install. 

In the install procedure it will offer to install alongside current Ubuntu or over it or you can choose the third option called "something else". This lets you manage partitions and choose file systems.

Here's my high and mighty arrogant opinion xD

1. Run the live CD installer
2. Choose "something else"
3. Delete swap partition
4. Delete Linux partition
5. Create new Linux partition using all but 3GB of free space, choose ext2 from the file system drop down menu, and choose the mount point "/"
6. Create a partition for the swap using the remaining free 3GB of space. Choose swap from the drop down menu. 
8. Click the Linux partition and then proceed through the install. 

Hope this is some trivia if or you if nothing else! Let me know what you think :) sorry if I come across as arrogant I'm trying to just throw some ideas out for you!

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> Ok I see where you're coming from... I think!

With 32GB of ram I simply can't fathom any computing falling over that loft peak and into a swap area... Your friend may be right, some program may want to use swap and look for it on its own. In that case, you should have at least 2GB and I highly recommend it be on the same HD device as the OS partition. 

How much space is windows taking up? If you're not storing files, windows doesn't just "grow"... Lol

By the way... On a sidenote that you probably already know: If you're using Linux on a SSD drive, please please don't tell me you're using the EXT3 or EXT4 file system...... It's absolutely awful on SSD and can really damage the blocks because of the journaling methods the EXT3/4 systems use. It causes about 4-15% more writes to the HD on normal use and deleting files or high write requirement data can double the amount of writes. Basically it will wear your SSD out much faster than using a file system without journaling. EXT2 is safe because it doesn't have journaling, whereas EXT3 and EXT4 both include it. (End of humble opinion based on popular fact) lol

If you were going to consider reinstalling Ubuntu to try and fix the black screen, it might be good to consider switching and using ext2 (if you arent already, but the installer uses ext4 by default) at the same time when you install. 

In the install procedure it will offer to install alongside current Ubuntu or over it or you can choose the third option called "something else". This lets you manage partitions and choose file systems.

Here's my high and mighty arrogant opinion xD

1. Run the live CD installer
2. Choose "something else"
3. Delete swap partition
4. Delete Linux partition
5. Create new Linux partition using all but 3GB of free space, choose ext2 from the file system drop down menu, and choose the mount point "/"
6. Create a partition for the swap using the remaining free 3GB of space. Choose swap from the drop down menu. 
8. Click the Linux partition and then proceed through the install. 

Hope this is some trivia if or you if nothing else! Let me know what you think :) sorry if I come across as arrogant I'm trying to just throw some ideas out for you!

I actually did not know that Ext4 on SSD is bad. I just reinstalled Ubuntu with 1G swap on my SSD but I used Ext4. In any case it still gives me a blank screen. Is it possible to just disable journalling on Ext4 on the SSD before or after installation? I am just curious that since Ext2 is sort of two "versions" behind Ext4 whether I will end up losing any performance after investing on a custom build.

Thanks.

---

### Post by linuxnovice on 2013-09-16
Update:

Ok here is where I am at how after taking into consideration CeejRab's advice. I reinstalled Ubuntu 12.04 (again!) on my SSD along side Windows 7 with a Swap of 2GB on the same drive. I have updated my current hard drive (SSD + HDD) configuration on my first post in this thread. I have installed using Ext2 file system as I tihnk I would like more performance than fault resiliance. After installation I have performed all the updates (boot-repair, apt-get update/upgrade, nvidia driver install) that are listed in this thread again. But to no avail. I am still getting a blank screen after selecting Ubuntu 12.04 from the grub menu. Windows 7 still works though. 

Is there anything else that I can try?

---

### Post by CeejRab on 2013-09-16
ok thats all looking good, im somewhat puzzled as to what i can suggest next but im working on it. "I'll BE BACK!!" lol

PS: It is possible to disable journaling is ext4 but its somewhat difficult and involved with commandlines. Also ext2 is faster for performance so thats a bonus in your situation to be using ext2. (ok here i go on the black screen issue...)

---

### Post by linuxnovice on 2013-09-16
Update:

I mentioned earlier that I installed the nvidia driver directly from the nvidia website for linux x86_64. However, it is still not working. So I installed the driver nvidia-319 which was present in the repositories. I am assuming that this driver will overwrite the original driver that I installed. But I am still getting a blank screen after I select Ubuntu 12.04 from the grub menu.

What is confusing me is the fact that the Live CD works perfectly when I boot from it. I am able to login live with both monitors working (mirroring each other) and I am able to browse the internet etc. How come after installation this goes away. What is different between the live cd session and the installation session? Perhaps I need to run the opensource driver nouveau ? How would I go about disabling the nvidia driver and installing this?

---

### Post by CeejRab on 2013-09-16
Ok have you checked to see if the drive is mounted? I know thats a big DUH but try booting from the live CD and open disk utility, (search for it in the dash, by pressing the windows key on the keyboard) and click the drive from the left hand side list. 

Down at the bottom it should say "unmount volume", this means it is mounted. If it says "mount volume" then you should do that. 

If possible, take a screenshot of that disk utility screen for me with the linux drive selected, that might help me see whats going on.

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> Ok have you checked to see if the drive is mounted? I know thats a big DUH but try booting from the live CD and open disk utility, (search for it in the dash, by pressing the windows key on the keyboard) and click the drive from the left hand side list. 

Down at the bottom it should say "unmount volume", this means it is mounted. If it says "mount volume" then you should do that. 

If possible, take a screenshot of that disk utility screen for me with the linux drive selected, that might help me see whats going on.

Hey,

Thanks a lot for your help. I did what you suggested, and when I ran disk utility, my SSD was not mounted. But I thought thats how it should be when running on live CD? I mounted and took a screenshot like you requested and have attached it to this post. I am posting this when booted into the LIve CD so something still works! 

One thing I noticed is that the all the Ubuntu partitions are under "Extended" section. I hope this is not in anyway interfering with the login/boot process.

Thanks.

---

### Post by CeejRab on 2013-09-16
It is pretty confusing, but yes perhaps trying the default driver would be good, i'll look into it and get back to you in a minute. In recovery mode can you access things normally? If so, try to go to system settings and click "Additional Drivers". See what the choices are there, maybe take a screenshot for me so i can see. If theres none listed, nevermind the screenshot.

---

### Post by linuxnovice on 2013-09-16
I dont have X in recovery just shell. As for accesing things normally, there is a shell and my home folder is there and I am able to apt-get update/upgrade and install stuff. But like I said no X and when I type startx, the screen just freezes. I will try it again and get back to you.

I have already installed two drivers for the graphics card: one from nvidia directly as shown in the link in the update and the second from the repositories nvidia-310 (and its dependencies). So, I am not sure what would be the "default" here now. Also, if I do install the default, would it just get "written" over these other drivers?

---

### Post by CeejRab on 2013-09-16
> **linuxnovice said:**
> Hey,

Thanks a lot for your help. I did what you suggested, and when I ran disk utility, my SSD was not mounted. But I thought thats how it should be when running on live CD? I mounted and took a screenshot like you requested and have attached it to this post. I am posting this when booted into the LIve CD so something still works! 

One thing I noticed is that the all the Ubuntu partitions are under "Extended" section. I hope this is not in anyway interfering with the login/boot process.

Thanks.


Ok thats great, it doesnt really matter if its mounted or not in the live CD but knowing that it wasnt helps the purpose here. Now if you can log into the full install on your HD (unplug (if USB) or remove (if CD) the liveCD device and boot the computer's ubuntu install in recovery mode). If it will let you log in and do things, check in there and see if the SSD is mounted. Dont do anything, just screenshot again. (dismiss all of this if you cant access the computer's ubuntu install at all and your only way of viewing it is from windows or the live CD)

Im looking in the driver aspect and also EUID info for your monitor... I'll keep you posted!

---

### Post by linuxnovice on 2013-09-16
When I run startx when on recovery mode I get this error:

X: user not authorized to run the X server, aborting.
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: unexpected signal 2

Please note that by this time I have already pressed Ctrl-C.

---

### Post by linuxnovice on 2013-09-16
How do I check is my disks are mounted?

---

### Post by CeejRab on 2013-09-16
> **linuxnovice said:**
> I dont have X in recovery just shell. As for accesing things normally, there is a shell and my home folder is there and I am able to apt-get update/upgrade and install stuff. But like I said no X and when I type startx, the screen just freezes. I will try it again and get back to you.

I have already installed two drivers for the graphics card: one from nvidia directly as shown in the link in the update and the second from the repositories nvidia-310 (and its dependencies). So, I am not sure what would be the "default" here now. Also, if I do install the default, would it just get "written" over these other drivers?


If you can open a terminal window, type "gnome-control-center". This should hopefully open your system settings. If so, you'll be able to see listed driver in the additional driver section.

Yes, installing the default would "overwrite" the others, but not completely it would just use that instead of the others you installed.

---

### Post by CeejRab on 2013-09-16
> **linuxnovice said:**
> When I run startx when on recovery mode I get this error:

X: user not authorized to run the X server, aborting.
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: unexpected signal 2

Please note that by this time I have already pressed Ctrl-C.

whoa, thats a problem! hmmm...

---

### Post by CeejRab on 2013-09-16
> **linuxnovice said:**
> How do I check is my disks are mounted?

well it sounds like you cant access disk utility from anything but a LiveCD and the live cd doesnt do any good in this instance because its acting as the host computer so mounting or unmounting there will only mount or unmount them to the liveCD not to the actual computer's ubuntu OS.

If you could access disk utility from the main OS then you could make sure theyre mounted. But im thinking thats probably not your issue now that im seeing is a xorg problem.....

---

### Post by CeejRab on 2013-09-16
any chance you tried to log in with command mode? (alt+ctrl+F1)? Maybe you could run commands more easily from here. 

i think im onto something with xorg, hold on :)

*update: Its very weird to have issues on a fresh install of ubuntu, especially when the liveCD works fine. Im puzzled but hey thats the fun of being a computer tech right? lol

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> well it sounds like you cant access disk utility from anything but a LiveCD and the live cd doesnt do any good in this instance because its acting as the host computer so mounting or unmounting there will only mount or unmount them to the liveCD not to the actual computer's ubuntu OS.

If you could access disk utility from the main OS then you could make sure theyre mounted. But im thinking thats probably not your issue now that im seeing is a xorg problem.....

I agree. Because after running just "mount" when in recovery mode this is what I got:

> /dev/sda5 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)

So it seems that my SSD which is /dev/sd5 gets mounted properly. Now, if its an xorg prolbem, I still don't understand why the liveCD would work without any problem. Its not as if the liveCD is displaying on a monitor which is not connected to my graphics card. 

In any case, I dont running gnome-control-center on recovery would work since X isnt even running. But I'm still hopefull I can with the help of people like you here can fix it! :D

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> any chance you tried to log in with command mode? (alt+ctrl+F1)? Maybe you could run commands more easily from here. 

i think im onto something with xorg, hold on :)

*update: Its very weird to have issues on a fresh install of ubuntu, especially when the liveCD works fine. Im puzzled but hey thats the fun of being a computer tech right? lol

Indeed it is. But like I said hopefully we can figure it out. I did try to swtich to a text terminal after getting a blank screen but it wouldn't work as well which is very puzzling.

---

### Post by CeejRab on 2013-09-16
exactly, so the ssd seems to be working fine.. Xorg may or may not be the problem, i think its drivers still but we'll see...

yeah i feel like this is a one on one tech support and im a total failure xD i just did the same thing yesterday, 3 pages of back and forth with someone trying to fix a desktop problem where there were black bars at the top and bottom. I finally helped them fix it though by sending the commands to reset the unity desktop. So, hopefully someone wiser will come along and help us both or i guess we are fighting together until then :) lol

BRB with more ideas. 

PS: How experienced with ubuntu are you? You seem pretty wellversed in linux

---

### Post by CeejRab on 2013-09-16
> **linuxnovice said:**
> Indeed it is. But like I said hopefully we can figure it out. I did try to swtich to a text terminal after getting a blank screen but it wouldn't work as well which is very puzzling.

*Facepalm*

---

### Post by linuxnovice on 2013-09-16
I joined in 2006 as linuxnovice, I not a novice anymore. I am a computer science P.hD student who does all his work in linux but likes games as well, hence the windows dual boot :) .

---

### Post by CeejRab on 2013-09-16
Heres a little something i found, not sure if it will work but its worth a try.

1) Login to "Recovery mode" (line 2 in grub)

2) You will come to a "Recovery Menu" , please
choose (5) root .. "Drop to root shell promtpt"
.. then <Enter>

You can now edit /etc/X11/xorg.conf or hopefully
use the xorg.conf.backup if you have it, or run
'dexconf' to make a basic xorg.conf .

---

### Post by CeejRab on 2013-09-16
> **linuxnovice said:**
> I joined in 2006 as linuxnovice, I not a novice anymore. I am a computer science P.hD student who does all his work in linux but likes games as well, hence the windows dual boot :) .

Haha nice, good for you! I dont have the official badge but you can see what ive done on my bio. 

Keep us (just me right now lol) posted on what youre trying so i dont offer the same idea youve already attempted ;)

---

### Post by CeejRab on 2013-09-16
you can try this as well, looks promising according to others with similar issues:

(each line is a separate command)

sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> you can try this as well, looks promising according to others with similar issues:

(each line is a separate command)

sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

I will try that in a bit. It takes a while to boot into liveCD and back into recovery mode. As per your earlier suggestions I was able to read/edit my xorg.conf file. I will paste it here in case it will help:

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 319.49  (buildmeister@swio-display-x64-rhel04-03)  Tue Aug 13 20:42:18 PDT 2013

# Warning: This file is autogenerated by nvidia-prime. All changes to this file will be lost.

Section "ServerLayout"
    Identifier     "layout"
    Screen      0  "nvidia" 0 0
    Inactive       "intel"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nvidia"
    Driver         "nvidia"
    BusID          "1:0:0"
EndSection

Section "Device"
    Identifier     "intel"
    Driver         "modesetting"
EndSection

Section "Screen"

    # Uncomment this line if your computer has no display devices connected to
    # the NVIDIA GPU.  Leave it commented if you have display devices
    # connected to the NVIDIA GPU that you would like to use.
    Identifier     "nvidia"
    Device         "nvidia"
    Monitor        "Monitor0"
    Option         "UseDisplayDevice" "none"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "intel"
    Device         "intel"
    Monitor        "Monitor0"
EndSection


I will not attempt to purge nvidia stuff and reinstall xserver and return back with the results.

---

### Post by CeejRab on 2013-09-16
ok looking pretty interesting, thanks for pasting that. I understand its slow switching back and forth from live CD. Do you have a tablet, smartphone, or different computer you could use the forums from? I feel bad for you switching back and forth!

---

### Post by linuxnovice on 2013-09-16
I have my laptop, but for stuff like pasting my xorg.conf file it is much easier for me to boot into liveCD and mount my SSD and just copy and paste it to the post rather than seeing and typing it through my laptop! Its fine really, I just want to get this damn thing to work after having spent yesterday fully putting this awesome system together.

In your commands, waht is the second line last two packages? I think theres a type there because I am getting an error of not being able to find xerver-xorg-core.

---

### Post by CeejRab on 2013-09-16
If youre referring to this:

sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

im not sure exactly, it looks fine to me but i didnt type it up its on a forum for the same issue youre having. 

I think ive narrowed down the problem... Im lead to believe you need to do a nomodset, ill get right back to you with how to do that in just a moment.

---

### Post by linuxnovice on 2013-09-16
Actually I have tried nomodset as well. If you check my first post, I link to a website from where I got the information in number 2 of the things I tried. Although I have not tried that since the reinstall.

---

### Post by CeejRab on 2013-09-16
oh ok sorry i didnt notice that. If you do want to retry it, heres something i found regarding the nomodset:

Reboot and keep your finger on the &#8220;SHIFT&#8221; key till you get the grub  menu. Highlight the first entry and replace &#8220;quiet splash&#8221; with  &#8220;nomodeset&#8221; .  Hit CTRL + X to continue booting. Once logged in install  the latest Graphics drivers. *System -> Administration -> Additional Drivers*

Did you attempt to purge the NVIDIA drivers? Im seeing some people had success with that approach...

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> oh ok sorry i didnt notice that. If you do want to retry it, heres something i found regarding the nomodset:

Reboot and keep your finger on the “SHIFT” key till you get the grub  menu. Highlight the first entry and replace “quiet splash” with  “nomodeset” .  Hit CTRL + X to continue booting. Once logged in install  the latest Graphics drivers. *System -> Administration -> Additional Drivers*

I will try that in a bit. But afte running your commands we have a progress! It's still not working, however instead of a blank screen after selecting Ubuntu 12.04 from the grub menu, I am getting this:

[     7.742599] nouveau E[ PGRAPH][0000:01:00:0] ROP0 ch 1 [0x000007fc92] 0x80000000 0xB0000001

and 3 more lines like that on both my monitors. So we have something different now. I will try the nomodeset and report what happends along with my new xorg.conf which I'm guessing would have been generated after running those commands.

---

### Post by CeejRab on 2013-09-16
Hey thats a step! not sure if its forward or backward, but, its a step!  lol

---

### Post by linuxnovice on 2013-09-16
OK! definetly progressing here! After I did the nomodeset I am able to get a shell with login name and I am able to login into my account in shell. However, when I run startx I get an error. Its too big to post here but the main is Fatal server error: no screans found. I am attempting to solve this now by the instructions [here]("http://www.youtube.com/watch?v=ReyT56rTWnA").

---

### Post by CeejRab on 2013-09-16
Awesome! I think that video tutorial should fix it, hopefully. If not i have some options ill post ;)

*addendum*
Heres a link to the fatal error fix if you need something more than the video:
[http://alexsleat.co.uk/2011/03/04/how-to-fix-fatal-server-error-no-screens-found-ubuntu/](http://alexsleat.co.uk/2011/03/04/how-to-fix-fatal-server-error-no-screens-found-ubuntu/)

---

### Post by linuxnovice on 2013-09-16
Hey,

So none of the other stuff really worked. I was able to get a GUI just once and login but that's it. After I rebooted its the same story again. I got tired of it and decided to reinstall the whole thing once again to start over. So this is where I am at. I reinstalled Ubuntu 12.04 LTS x64 on my SSD alongside Windows 7 and with a swap partition of 2GB. I rebooted the system and I didn't even try going the "quiet splash" version. I edited it (which is kind of a pain to do it everytime, is there a way to always have nomodeset instead of quite splash?) to nomodeset. My screen was filled with text but ended with a blank screen. The good part is I was able to switch tty and was able to login to a shell. I updated/upgraded everything, I did not however install any nvidia drivers. Right now if I run startx from tty1 I get this error: 

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

I remove the lock and ran startx again, but gave me a similar error:

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already runnnig.

So this is where I am at, I am not sure how to proceed. Do I install the nvidia driver from the nvidia website? Really I am completely lost and hoping someone could shed some light as to why a brand new system with a fresh install from a liveCD which WORKS is not able to login to the desktop.

Thanks.

---

### Post by CeejRab on 2013-09-16
hmm... Im pretty baffled. I found some articles saying your geforce card has issues with compatibility with the kernel but its not very frequent... I'll see what i can dig up, i have to go for now but i'll be subscribed to the thread and i'll keep working on it for you! 

Hopefully someone else will come along too with some brighter light bulbs than i have so far! :)

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> hmm... Im pretty baffled. I found some articles saying your geforce card has issues with compatibility with the kernel but its not very frequent... I'll see what i can dig up, i have to go for now but i'll be subscribed to the thread and i'll keep working on it for you! 

Hopefully someone else will come along too with some brighter light bulbs than i have so far! :)

Thanks a lot for your help! I really appreciate it. I'm taking a break from getting Ubuntu to work after having working on it for the past 9 hours, so my responses will not be as quick. I was also thinking maybe GTX 770 has issues with 12.04. I wish someone with this setup (GTX 770 with 12.04) would pitch in with their opinions. Perhaps I need 13.04 for this to work (which I really dont want to install). But that will be a last resort though.

---

### Post by linuxnovice on 2013-09-16
I gave in and installed 13.04 amd64 and everything just worked. It is sad that I couldnt get the system to work with 12.04 LTS which I thought would also support new hardware. Oh well.

---

### Post by CeejRab on 2013-09-16
That is very sad... Maybe it will be fixed by the time 13.04 expires in a few months and you can get back to what you wanted with the LTS release! 

Im sorry I couldn't help you much, its obviously something in the kernel/xorg/driver settings that works fine from the LiveCD but doesn't like being installed on your hardware setup. I enjoyed trying though, thanks for the screenshots and patience.

All the best with your setup, its an awesome machine! 

God bless

PS: better change your distro in your profile from precise pangolin to 13.04 :P lol

---

### Post by linuxnovice on 2013-09-16
> **CeejRab said:**
> That is very sad... Maybe it will be fixed by the time 13.04 expires in a few months and you can get back to what you wanted with the LTS release! 

Im sorry I couldn't help you much, its obviously something in the kernel/xorg/driver settings that works fine from the LiveCD but doesn't like being installed on your hardware setup. I enjoyed trying though, thanks for the screenshots and patience.

All the best with your setup, its an awesome machine! 

God bless

PS: better change your distro in your profile from precise pangolin to 13.04 :P lol

Thank you for sticking with me as well. I really appreciate your help. To be honest, I am starting to like 13.04 a bit, although the first thing I did is uninstall a bunch bloatware crap it came with that i don't need and will never use. It sucks that this is only supported till January 2014.

---

