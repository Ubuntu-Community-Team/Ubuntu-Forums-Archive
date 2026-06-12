---
title: "HOW TO: Install &amp; Optimize Ubuntu Netbook Edition on an Acer Aspire One 110"
date: 2010-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by tphive on 2010-11-07
This is a guide that I wrote to be included with netbooks of this model that I repair and sell, just in case the user should need to reinstall the OS at any point. It's a culmination of all the help I've received via the IRC, forums, and Google in my latest (and first real/excensive) Linux adventure.I know this is a very specific or proprietary guide, but since I took the time to make it,(and now the time to heavily edit it to format properly on these forums) I figured I should share it as well, just in case someone, sometime could benefit from it.

The specific netbook this involves (Acer Aspire One 110 [AOA-110]) has a very early generation Intel SSD (solid state drive) and on a normal OS installations it is severely hampered by it's slow write speeds. So we'll be making some tweaks to counter that, and in the end, have a solid machine.

NOTE: As nsche mentioned, these tweaks "should work on any Linux based system installed on one of these SSD based netbooks." Even newer solid states could benefit through longevity.

We'll also be using Ubuntu Netbook Edition 10.04 LTS instead of the latest 10.10 for two reasons; Long-Term-Service is an important thing when anything is to be sold; and two, (sorry Ubuntu devs) the sidebar on 10.10 is frankly awful; 10.04 is simply a more pleasurable experience both visually and functionally. Lastly, you might notice this is my first tutorial on these forums, and I would welcome any additional tips, tweaks, ideas, and/or constructive criticisms you might have. I'll try to keep this updated this with any useful information provided throughout the thread. Now, let's begin.




**Preparation**

*If you intend on installing from an USB DVD/CD drive, just burn the ISO to disk and skip preparation*


[LIST]
[*] You will need a USB thumbdrive or external HDD with at least 1GB of storage space


[*] Next, download and run the Universal USB Installer from here: [[COLOR="Blue"]http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/[/COLOR]]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")


[*] On the second screen it will ask you to select a distribution, find and select &#8216;Ubuntu Netbook Remix 10.04&#8217; from the list. (You may be tempted to opt for 10.10 but trust me, 10.04 is better, future versions beyond 10.10 may be better, but as of writing this, 10.04 suits this purpose best)


[*] Check the box &#8216;Download the iso&#8217;, and download. When complete, if it didn&#8217;t find it automatically, browse the installer to where you downloaded the ISO (if the text below the box is green, you already have the proper file)


[*] Select the drive letter of your USB storage device. (thumbdrive or external) Make sure you pick the right one and back up anything you want to keep from it. ANYTHING ON THE DRIVE WILL BE ERASED


[*] Finally, check the box to format the drive, and when you&#8217;re ready, click &#8216;Create&#8217;
[/LIST]

**Installation**
[LIST=1]

[*] Boot from  the prepared thumbdrive or external disk drive. Press F12 on the first screen. Then select the thumbdrive or disk from the list and press enter. (Should start with 'USB&#8217;)



[*] Once you&#8217;re at the Ubuntu start screen, choose Install Ubuntu and hit enter



[*] Continue through the pages for localization, keyboard layout, etc. 



[*] When you come to the screen that says: &#8220;Prepare disk space&#8221; (step 4 of 7) on top, choose &#8220;specify partitions manually (advanced)&#8221;



[*] Select and delete all partitions from the system drive, total size should be just under 8,000 MB (8GB) and the drive should be labeled as /dev/sda, any partitions will likely be /dev/sda1 and /dev/sda2.



[*] Now select New Table, and accept any prompts.



[*] Select &#8220;new partition&#8221; on the bottom of the screen.
```
Linux (will become /dev/sda1)
New partition should read: Primary
Size should be 7301 MB
Beginning of the disk
Use as ext4 file system
Mount Point should be  /  (root directory)
```
[*] Select &#8220;new partition&#8221; again.
```
Swap (will become /dev/sda2)
New Partition should read: Primary
Size should be:  769MB (1.5x the size of RAM)
Beginning
Use as &#8216;Swap&#8217;
```
It should look similar to this before proceeding to the next step: (DO NOT CLICK NEXT YET)
```
Devices     Mount  Type     Size
/dev/sda1     /    ext4     7300
/dev/sda2          Swap     768
```


[*] Press Ctrl+Alt+F2 to open the Terminal, we&#8217;re going to make a couple tweaks for better drive performance.

*_NOTE: Anytime throughout this Guide you see the word "Code", ignore it. It's part of the forum, not the guide._*

**a.**	Type:    ```
sudo mke2fs -t ext4 -O ^has_journal /dev/sda1
```
[I]This turns off journaling, which reduces writes to the drive, the weakness of this particular model.
[/I]

**b.**	Next, type:    ```
tune2fs &#8211;i 7d
```
[I]This forces the drive to be checked for any errors every seven days. Good thing to maintain stability.
[/I]

**c.**	Lastly type:    ```
tune2fs &#8211;c 15
```
[I]Similar to the previous, this forces the drive to be checked every fifteen mounts (boots). The effect of the two combined  is that every 7 days or 15 mounts, whichever comes first, it will check the drive for errors and attempt to fix them, should it find any.
[/I]



[*] Now that we&#8217;re done with the terminal, we can get back to the GUI (Graphical User Interface) by pressing Ctrl+Alt+F7



[*] If prompted, click continue. Then hit forward and you will see &#8220;Who are you?&#8221; (screen 5 of 7) fill out as desired.



[*] Click on install, and sit back. Like Alton Brown says: &#8220;Your patience WILL be rewarded!&#8221;



[*] Boot up Ubuntu, and we are going to make some performance enhancements.



[*] Open up a terminal window (found in Accessories, or press Ctrl-Alt-T)

**a.**	**Reduce swappiness**
In this installation the swap area is built in, inside the encrypted LVM volume, so we will be using our flash memory to write our swap data to and read from. Writing to flash memory is generally a little slow. The idea of reducing swappiness here is to cause the operating system to prefer not to use the swap area too much and prefer to use the memory modules instead. The operating system should be a lot faster if it uses the memory modules instead of the swap area.
By using this method, the swap area is still available to the operating system in case it is really needed. 


Open your /etc/sysctl.conf file with gedit text editor,
```
gksudo gedit /etc/sysctl.conf
```

At the bottom of the file, make a new line and add this
```
vm.swappiness=10
```
Save and exit.


*[SIZE="1"]See: [[COLOR="Blue"]Performance tuning with 'swappiness'[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27") - Ubuntu Community Docs.[/SIZE]*

________________________________________


**b.**	**Edit /etc/fstab with noatime option**
Theodore Ts'o, the lead developer of the ext series of file systems recommends mounting the file system with the noatime option when using in in flash memory sticks or SSD drives, please read this link, *[[COLOR="blue"]SSD&#8217;s, Journaling, and noatime/relatime[/COLOR]]("http://thunk.org/tytso/blog/category/computers/ssd/")*. I'm taking his advice.

Open the /etc/fstab file with gedit text editor,
```
gksudo gedit /etc/fstab
```
/etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=211f3838-e60b-4472-a58d-b58bdf6aea9d /               ext4    **[COLOR="Red"]noatime,[/COLOR]**errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=01156c98-0cae-4354-b989-eefb7bbd67fb none            swap    sw              0       0
```
Add &#8216;noatime,&#8217; where shown above. If it looks different, simply change the words 'relatime' to 'noatime' and save the changes before closing the file.


This means Ubuntu will no longer go to the extra work of updating the access time (atime) every time we open a file. To see what I mean, right-click on any file and click 'properties', and you'll see the last access time listed there.


[SIZE="1"]*from: [[COLOR="blue"]http://members.iinet.net/~herman546/p19.html[/COLOR]]("http://members.iinet.net/~herman546/p19.html")*[/SIZE]

________________________________________



[*] Install updates and enjoy! You now have installed a secure, portable operating system on your netbook.




**Optional:**
(Recommended)

**a.**	You can turn on the Ubuntu sound theme by clicking the speaker on the toolbar, then Sound Preferences --> Sound Effects tab --> Sound Theme drop-down box.


**b.**	VLC media player can be installed through the Ubuntu Software Center or via terminal:
```
sudo apt-get update
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```
**c.**	If you install VLC (Video Lan Client), and wish to have it handle all videos, a simple though brutal (also the only way that I found actually works) way to do this is by simply opening terminal and typing
```
sudo cp '/usr/share/applications/vlc.desktop' '/usr/share/applications/totem.desktop'
```
**d.**	If you&#8217;d like to install the internet browser Google Chrome, it can be found at [[COLOR="blue"]http://www.google.com/chrome/[/COLOR]]("http://www.google.com/chrome/") You can add it to the launch screen by clicking the + when hovering over the icon. (Found in Internet)[/LIST]

---

### Post by nsche on 2010-11-07
Thanks for the info.  I'll give it a try.

I use xubuntu on my 110 but your tuning thoughts are not unique to any particular distribution.  They should work on any Linux based system installed on one of these ssd based netbooks.

Thanks again
Norm

---

### Post by tphive on 2010-11-09
> **nsche said:**
> Thanks for the info.  I'll give it a try.

I use xubuntu on my 110 but your tuning thoughts are not unique to any particular distribution.  They should work on any Linux based system installed on one of these ssd based netbooks.

Thanks again
Norm

I'm glad someone's able to benefit from this already! :D

I've added a note reflecting your helpful input.

---

### Post by roomonster on 2010-11-23
Do you know if it is possible to remove journalling from a drive post installation?  I don't really want to reinstall everything unless I really have to ;)

Thanks for the guide it looks like it will be very useful.

Roomonster

---

