---
title: "I've tried to install the latest nvidia driver and after reboot I got black screen"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by Matt92HUN on 2013-09-26
Ubuntu version is 13.04, the only interaction that black screen allows is to turn the computer off. I've tried things I've found, for example the things mentioned [here]("http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver"), but it's complaining about the file system being read-only. Also, nvidia-settings says the --uninstall command is not available.

Edit: I've managed to fix it. I don't know, if that's the case if you only have Ubuntu on your hard drive, but before logging in, I have iptions to start Ubuntu, or Windows, or other. There's an option "Advanced options for ubuntu". There you can pick your version with (restore mode) after it. There I chose "network" and once that started, I chose root. I typed "login", entered my username, then my password. Typed "cd Downloads", "ls", then I've checked the name of the driver's installer. Then typed "sudo ./'driver name'.run -uninstall". After that finished I typed "sudo reboot", and it sort of worked, except I didn't have the sidebar and the topbar, guess Ubuntu's equivalent of explorer. I've followed the instructions for manual installation [here]("http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html"), then typed "dconf reset -f /org/compiz/", then "unity --reset-icons &disown". It didn't work inmediately, but I entered "unity --reset-icons &disown" again, and that fixed the sidebar too.

---

### Post by ThoseTimesAreGone on 2013-09-27
i was using linux mint that is based on 13.04. nvidia card here too... same problem as you. installed nvidia driver and was greeted with a black screen. fixed it by following advice of BAO2 on this forum;

[http://ubuntuforums.org/showthread.php?t=2152518](http://ubuntuforums.org/showthread.php?t=2152518)

lmk if it helps or not b/c others who see the thread will benefit from it.

Also i dont know if it will work now that you have made changes to your system... You might have to reinstall and try again... thats what i did. either way works perfect now.

---

### Post by deadflowr on 2013-09-27
How did you install the driver in the first place?
Through the repos or from a run file from nvidia?
If from a run file look here
[http://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](http://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)

If from the repos try
```
sudo apt-get purge nvidia*
```

When it has been removed try rebooting, and if successful getting a normal Ubuntu screen, open the program software updater and let it run for updates.
Install whatever comes up.
Then try installing the drivers again.
Look over this to see if anything here can help you out.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by buzzingrobot on 2013-09-27
The recommended way to install and remove Nvidia drivers is via the Additional Drivers tab in Software Sources (check the menu in the Software Center app.)

I've found that fixing problems when using another installation method typically requires first backing out the install completely and cleanly, which can be difficult. More is involved than smiply deleting files.

I've also found that Nvidia installs often, for some reason, do not execute the nvidia-xconfig command, which creates the required xorg.conf file. This can result in a reboot to a black screen, or to a screen with error messages.  So, now, when an Nvidia install says it is complete, I open a terminal and run "sudo nvidia-xconfig".

---

### Post by buzzingrobot on 2013-09-27
> **Saint_Sakura_ said:**
> 

So, if I  and the girls at my school are using nVideo 304 which is the recommended driver in 'Additional Drivers' in 12.04LTS, we should not risk upgrading to a higher number from a download?


If it works, it is not to be fixed.


Unless you have a specific problem that you know a new release will correct, I think there's no advantage in moving to a newer release simply for the sake of moving.

---

### Post by Saint_Sakura_ on 2013-09-27
&#12371;&#12435;&#12400;&#12435;&#12399; buzzingrobot&#12288;&#12373;&#12435;&#12289;:p

Thank you for your clear advice. I will tell the other girls at school on Monday.


&#12376;&#12419;&#12397;&#12290;&#32854;&#26716; Saint Sakura:popcorn:

---

### Post by Matt92HUN on 2013-09-28
My problem is I can't even log in. The only option I have is to log in in command line, but then whatever I try, it's complaining about the file-system being read-only. Is there a solution for that?
When I trieddrivername.run -uninstall, it said "command not found". I've installed it from the .run file, because with the other drivers I couldn't run games, which I remember to have worked earlier, in an other version of Ubuntu with also manually installed latest driver.

---

### Post by Matt92HUN on 2013-09-28
OK, I've enabled network, and that fixed the read-only problem, but dist-upgrade still haven't fixed the black screen.

---

### Post by The Cog on 2013-09-28
I've had that read-only problem a few times. I often find that what fixes it is running fsck (a filesystem checker) on the partitions. This is best done from the live CD. Boot the installer CD and choose to try before installing. Once in the desktop, open a command prompt and run the command
```
sudo blkid
```
This lists all the disk partitions and their type. Here's mine for example:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b6518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531775     9764864   83  Linux
/dev/sda2        19531776    39063551     9765888   83  Linux
/dev/sda3        39063552    58595327     9765888   83  Linux
/dev/sda4        58597374  1953523711   947463169    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5        58597376    78127103     9764864   82  Linux swap / Solaris
/dev/sda6        78129152   136720383    29295616   83  Linux
/dev/sda7       136722432   195313663    29295616   83  Linux
/dev/sda8       195315712   781250559   292967424   83  Linux

```
Then for each linux type partition, run fsck on it by device name. Like this:
```
sudo fsck -a /dev/sda1
sudo fsck -a /dev/sda2
```
etc. For partitions 1, 2, 3, 6, 7, 8 in my case.

---

### Post by Matt92HUN on 2013-09-28
Got as far as uninstalling the driver, now it logs in, but the sidebar is missing as well as some other features.
P.S.: Don't worry about the mess of posts here, I'll edit the first once I get somewhere.

---

### Post by Matt92HUN on 2013-09-28
> **The Cog said:**
> I've had that read-only problem a few times. I often find that what fixes it is running fsck (a filesystem checker) on the partitions. This is best done from the live CD. Boot the installer CD and choose to try before installing. Once in the desktop, open a command prompt and run the command
```
sudo blkid
```
This lists all the disk partitions and their type. Here's mine for example:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b6518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531775     9764864   83  Linux
/dev/sda2        19531776    39063551     9765888   83  Linux
/dev/sda3        39063552    58595327     9765888   83  Linux
/dev/sda4        58597374  1953523711   947463169    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5        58597376    78127103     9764864   82  Linux swap / Solaris
/dev/sda6        78129152   136720383    29295616   83  Linux
/dev/sda7       136722432   195313663    29295616   83  Linux
/dev/sda8       195315712   781250559   292967424   83  Linux

```
Then for each linux type partition, run fsck on it by device name. Like this:
```
sudo fsck -a /dev/sda1
sudo fsck -a /dev/sda2
```
etc. For partitions 1, 2, 3, 6, 7, 8 in my case.
I got that sorted by starting the network.

---

### Post by Matt92HUN on 2013-09-28
Everything seems to be working now, I'm editing the main post and marking this solved.

---

### Post by Askel on 2013-09-28
nice that you had it working again. my solution when I get the blackscreen from nvidia-drivers has been to activate optimus in the biossettings. this has disabled nvidia so I can reboot, deactivade optimus again and then install another nvidiadriver.

---

### Post by tim21 on 2013-09-28
Matt
Did you ever get the driver/nVidia card to work or did you just leave it uninstalled?
Tim

---

### Post by Matt92HUN on 2013-09-29
I did, it works now.

---

