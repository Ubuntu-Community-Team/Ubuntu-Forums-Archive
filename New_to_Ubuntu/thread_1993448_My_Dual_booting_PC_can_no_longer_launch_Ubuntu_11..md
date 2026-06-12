---
title: "My Dual booting PC can no longer launch Ubuntu 11.10"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by staib on 2012-06-02
Hi guys,

I have been trying and failing for days to launch Ubuntu from Grub on a dual OS machine but am having no luck... Can anyone help? The only significant change I have made to the system since the last time it worked is the swapping of a graphics card from a Radeon to an Nvidia GTX560. In another partition I have Windows 7 running and operating as expected, so am presuming this is not a hardware issue?

If I select the default first Grub option: Ubuntu 11.10, kernel 3.0.0-12-generic-pae
Then I get no further than a black screen.

If I select the second (recovery version) of the above, I see the mystical scrolling text, but it stop at:
[32.776125] eth0: no IPv6 routers present.

If I launch Ubuntu with the normal router cable unplugged then the load sequence simply stops at:
[22.605468] ppdev: user-space parallel port driver.

If at that point I plug in the cable...

after quite a while it reports:

[270.717662] at11....eth0 link is down
[272.256695] at11....eth0 link is up 100 Mbps full duplex

But then nothing more...

Any suggestions of how I might recover this situation gladly accepted!

Cheers,
Nick

---

### Post by staib on 2012-06-02
Not sure if this helps, but I just tried booting an old live CD (Mint) that I had, and that loaded itself with a nice stable internet connection...:confused:

---

### Post by inashdeen on 2012-06-02
Opps that Nvidia is the devil here , I suppose. apparently, you may need a driver to run that Nvidia on ubuntu. not really sure how to get you install the driver though.

---

### Post by Babyzilla on 2012-06-02
Hi Staib,

I know I am also newbie, but maybe you can try what I have did with my Ubuntu earlier...

I am also installing the Ubuntu side by side with Windows 7, and last time, I only get blue color screen when I try to run ubuntu.
So, what I did is that go to [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

and then, try download the wubi installer again. It will automatically delet your previous version and install a new one. I don't know about the datas that you saved there, but if you couldn't find another way, it's worth to try..

Goodluck then!^^:popcorn:

---

### Post by BladeOfFearer on 2012-06-02
Oops. Do you install Nvidia X.Org Driver after swapping ?

---

### Post by inashdeen on 2012-06-02
Curious: @BladeOfFearer . How do you actually install it when cannot run the Desktop?

---

### Post by staib on 2012-06-02
> **BladeOfFearer said:**
> Oops. Do you install Nvidia X.Org Driver after swapping ?
No - I had only swapped to improve fps on a Flight game in the Windows partition, but I didn't immediately check that Linux was also OK. I was assuming that Linux (Ubuntu) would at least recognise such a mainstream graphics board - allowing me to load it, before grabbing the drivers?

After seeing this morning that an old Mint live distro worked, I just tried their latest (v13) version, but was surprised to see that it also failed to install... could that be linked... or perhaps just a coincidence.

Am writing this on an older Mint (7) live CD which seemed OK earlier but is now dropping and then auto-connecting to the internet every few minutes. This is not via wi-fi, but via a cable... (sigh)...

If the worst comes to the worst I can remove personal files I hope via Mint, then reinstall Ubuntu into that partition. Just hoped that there might be an easier way :)

Cheers,
Nick

---

### Post by inashdeen on 2012-06-02
the internet problem in the mint was because a problem in that mint. it is an old version as i had seen. I do think that a ubuntu reinstallation is the best thing to do, since you cant really get te driver now, unless you can fix back the old graphic card and get it running first, then install the nvidia driver before you put in the driver. but wont it be easier if you just reformat ubuntu and backup the files before hand?

---

### Post by oldfred on 2012-06-02
With nVidia I have always had to add nomodeset to the grub line on first boot, before the nVidia driver is installed.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

