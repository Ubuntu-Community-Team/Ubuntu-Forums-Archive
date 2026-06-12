---
title: "Unstable Ubuntu 1310"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by Nosphky on 2014-03-14
I want to move my wife's pc from XP to Ubuntu before the end of the month.  She has been using one of my cast-offs for about 3 years with an MSI motherboard and Intel Pentium Dual-core E5200 @ 2.5Ghz with 1G of RAM - running XP sp3 and connecting to my internet router using a Lynksys wireless USB device.  She just turns it on, starts Firefox and Thunderbird and does emails and browsing with seldom a problem.  I thought Ubuntu might give her the same experience.

I downloaded 1310 desktop (64 bit and 32 bit) - blew the iso's onto a couple of new Kingston Data 8Gb usb sticks and tested them both on my pc (running windows 7) in 'live' format.  All seemed fine and simple so I tried the 64bit version on the XP box as a 'live' version and all seemed to work well.

I used Gparted to shrink her NTFS partition to make space for Ubuntu, created a / partition of 40Gb exp4, 3Gb swap, and 10Gb /home partitions.  I used third option 'something else' during the installation, the wifi link established ok.  I deselected  download updates during installation to speed up the process but I noted that language packs amongst others were being downloaded.  After installation, the reboot was completed and then came the disappointment.

The display looked good, just as I had seen it in the 'live' trials but when I clicked on anything, the pc either froze up losing keyboard and mouse control or accepted the click and produced a garbaged screen.  The manual reset button on the pc became my best friend. After many attempts, I tried the advanced options in the boot manager, using the recovery mode initially and then completing the standard reboot.   This resulted in a good display but with larger icons (different screen resolution) and I was able to start 'Software updater' and check for updates.  Informed that I needed about 250Mb of updates I clicked to download and the wifi dropped out.  The drop-down menu in the top left of the screen showed that I was still connected to the wifi but an additional error dialog said I was disconnected and anyway, the download stopped.

 I got it back and the download completed about halfway and then dropped out again.  Getting it back involved physically removing the wireless usb devioce and replugging it.  When download was completed, the updates were installed and I rebooted.

This time the display was good and things seemed to work - no more frozen pc or garbaged display and I supposed the updates had removed the problems.  The wifi disconnects, I put down to 'one of those things'.

Testing at odd intervals over the next week, showed that the pc was prone to freeze at odd times at apparently random moments following a mouse click.  Unfortunately, one of these occasions was when I was demonstrating this super new system to my wife - sod's law.   

The other main problem was that when the previous session had been ubuntu, and current session was XP, the wifi while looking as though it was connected was in fact not able to connect to webpages or email servers.   It looked as though (in windows dialog boxes) the system was unable to determine the wireless usb device's IP address from the DHCP server.  The workaround was to physically remove the usb device and then replug it  and whenever I completed a session with ubuntu, I had to make sure the pc was reset before leaving it my wife.

Eventually it became clear that I could not leave this pc for her use in this state so I re-installed Ubuntu (using 32 bit version this time) - reformatting the partitions beforehand.

The reinstall went exactly like the first time even to the update dropping out the wifi just after clicking to download.   After installation I had to use recovery mode to get and install the updates because the pc either froze or garbaged the screen otherwise.  With updates installed, there is still the same tendency to freeze at random and the wifi still goes 'disconnect' (while showing connected) from time to time.

Although this pc must be 6 or 7 years' old, it works fine under XP but seems to have some driver troubles with Ubuntu.  Can anyone, please, suggest where I might start looking - and how ?

---

### Post by grahammechanical on 2014-03-14
I have not read your post. It is much too long and it does not make the problem (or is it problems?) stand out. Having different posts for different problems is a good thing to do. Sticking to the facts, supplying the symptoms, the machine's specifications and the version of Ubuntu are very helpful.

Problems with an installation that has been overwritten cannot be solved. The installation does not exist. Tell us about the problems you are having with the present installation. We get easily confused here.

So, which problem do I help you with? Wireless driver/Internet connection problem or video adapter driver problem?

By the way I am running Ubuntu 14.04 on an Intel Core2 Duo 2.40GHz with 1GB RAM and I have no problems connecting to the Internet or with the desktop display. A key component that is often overlooked is the graphic adapter. I am using an Nvidia GT220 with 1GB video memory. What graphic adapter do you have in that machine and how much video memory does it have?

If you can get to a desktop then go to System Settings>Software and Updates>Additional Drivers tab and wait until the utility finds drivers for your devices. It will find about five drivers for video. It may also find a driver for the Wireless adapter. Experiment with the different video drivers.

You may wonder why you need to experiment when you did not need to do that with XP. That is because you did not buy this machine with Ubuntu pre-installed. The retailer made sure that XP was working and was installed with all the correct drivers. That is not the situation with Linux distributions. The Linux developers are doing the best that they can in making Linux compatible with the great variety of hardware that is in use and in keeping up to date with the latest hardware. They are doing a good job but do not expect from Linux what you would expect from an OS that you paid lots of money for.

Regards.

---

### Post by mörgæs on 2014-03-15
With 1 GB of memory I recommend a clean install of 32 bit Lubuntu 13.10.

Forget wifi for now, only wired connection while installing (didn't the installer suggest that?)

Please post and tell if you get a stable system this way. Later we focus on the wifi.

---

### Post by Nosphky on 2014-03-16
Thanks for the 2 replies.  I didn't see a suggestion about wired connection for installation rather than wifi.  This pc doesn't have a graphics card it just uses the motherboard functionality.  Before going further, I'll see if I can get another gig of ram and a dedicated graphics card and then I'll try the suggestions for locating capable drivers.

---

### Post by Nosphky on 2014-03-20
Problem is solved.  Windows XP now replaced by Ubuntu.  

I installed a separate graphics card - re-installed 64 bit Ubuntu13.10 and all's now fine.  The graphics chips on the motherboard were apparently also Nvidia but I couldn't get any drivers to work them.  The new card is also nvidia and it worked right out of the box.

I also did the installation and updates with a wired connection to the router (as suggested above).  Subsequent connection via wifi work fine.

---

### Post by mörgæs on 2014-03-20
Good, please mark the thread 'solved'.

---

