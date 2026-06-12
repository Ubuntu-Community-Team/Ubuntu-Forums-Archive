---
title: "Ubuntu 12.04 kernel panic crash journal"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by Derelinquat fenestras on 2013-06-19
Hello all,

The following is a journal I kept while trying to rescue a broken system.  It is my hope that this thread will illustrate a couple things:

1) the importance of backing up your files!  (I seem to be slow to learn this...)
2) show that when using Ubuntu (or other Linux systems) the power is truly in your hands

I'm also hoping that this account will help beginners who may not know what to do when/if a crash occurs... at least where to start... I could maybe be considered an intermediate user so hopefully this account may give ideas of what to/what not to do...
And maybe my floundering will entertain advanced users!;)

I should also mention that this journal was written on a separate system, therefore I was unable to provide output of any of the entered commands... so sorry, not optimistic that this will be very technically useful...
 
Without further ado, I present:

[SIZE=4]**2013 Kernel Panic Crash Fiasco:**[/SIZE]

> 04/12/13
****'s computer crashed with:
** kernelpanic - not syncing VFS unable to mount root fs on unknown-block(0,0)**


Ran memtest


**[COLOR=#000000][FONT=Times New Roman][SIZE=3]Changed memory chip[/SIZE][/FONT][/COLOR]**
**[COLOR=#000000][FONT=Times New Roman][SIZE=3]bootup in recovery mode[/SIZE][/FONT][/COLOR]**
**[COLOR=#000000][FONT=Times New Roman][SIZE=3]Attach Ethernet[/SIZE][/FONT][/COLOR]**


**In Recovery Menu:**
**Enable networking**


**run dpkg &#8594; fix broken packages**
doesn't look like anything important is getting fixed
...multiple broken packages though...


...again with kernel panic...


force restart...
reopen in recovery mode...
reenable networking...
Update GRUB bootloader


Drop to root shell prompt


sudo apt-get autoremove &#8594; failed
sudo dpkg &#8211;configure -a &#8594; setting up a bunch of things... 
...interestingly:
_update-initramfs:  generating/boot/initrd.img-3.2.0-39-generic_


attempting
sudo apt-get autoclean... success, but nothing to clean
attempting
sudo apt-get autoremove... success...only opera... removing...
    &#8594; had to reinstall to remove?...leaving it alone... it's fixed...
attempting:
sudo apt-get update &#8594; success
attempting:
sudo apt-get upgrade &#8594; linux genericheaders/images in dist-upgrade... hopefully a good sign &#8594;AAAAHHHHH!!! again with kernel panic!


Forced restart...  next thing i'm going to do is go straight for dist-upgrade...
...monitor not working... forced restart
...removing battery...  eventually got the screen to work... recovery mode failed to load...
forced shut down... researching removing screen...
attempting to start computer again...
monitor working... computer is not... try again...  failed... remove battery after forced shut down...
Success... back in recovery mode...


Enabling networking... success
Dropping to root shell prompt
attempting:
sudo apt-get dist-upgrade... failed....


prompt remains at flashing cursor underscore after reading state information... attempting soft reboot... failed... hard restart... no screen... don't think its a hardware screen problem...


Next time will go strait for dist-upgrade... seems to have the packages we need... best option apparent...


Kernel panic... try again... success


attempting:
sudo apt-get dist-upgrade... running! Yay!... failed... waaaa!


Will try dpkg  next time...  wasted my whole day on this ****...


04/17/13


Okay... So far I've tried the above...to no avail... I've read that the computer running out of memory can cause this kind of crash... explains a lot...


Anyway next step is this:


Copy files from /home/jacob to/media/Expansion\ Drive


    &#8594; may need to research how to copy entire directory... may not be feasible given the instability of the system... otherwise 1 at a time


command thus far:


sudo cp /home/jacob/<folder>/<file(s)/media/Expansion\ Drive


we'll see if it all plays out


then find a way to reinstall ubuntu....may need new hard drive or format hard drive, the reinstall... May take more research...  


5/2013


Was unable to get the computer to maintain stable operations...


From the recovery console/rootterminal...


ran alternating dpkg (from recoveryconsole menu) followed by sudo apt-get install -f (root terminal)until there were no more errors/updates to install.


System would crash when running, so each time had to restart/rerun above commands multiple times until no more errors....


eventually kernel was updated to newest version!  Yay!


Ran update-grub


restart...


success!  Ubuntu booted normally...


but...
after login and system running for several minutes, 1 of 3 things happen


either screen gets scramled &#8594;mulitple colors, characters, flashing cursors
or 
screen freezes... not sure if thesystem has crashed, but mouse cursor frozen/no response from keyboard commands
or
Kernel panic output screen...


grrrr.... though I had fixed it...


restart....


Logged into recovery console from normal login screen to attempt to copy files to external hard drive...
permission denied even with 


sudo chmod commands....


ran 


sudo nautilus...


nautilus opens &#8594; runs slow &#8594; system promptly crashed as above...


restart &#8594; recovery console &#8594;installed PcmanFM (very fast/light file manager)


sudo apt-get install pcmanfm


success...


ran sudo pcmanfm


file manager opens...  since I was unable to copy files to the external hard drive, began copying files to several flash drives....


working successfully, however system keeps crashing at intermittent intervals... must keep track of the files so on restart I can pick up where I left off...


Finally recovered all of the files....shut down...


Created boot disk for Ubuntu 12.04 &#8594;attempting fresh install


Boot disk boots successfully... crashesduring &#8220;fetching&#8221; step... leaving it alone


 If anyone is still reading this, I would like to enter a final plea for help.
If anyone has any ideas or may be able to diagnose the problem with this system, I would rather not scrap this system.

Thank you... If anyone has further questions I will try to answer them to the best of my ability

---

