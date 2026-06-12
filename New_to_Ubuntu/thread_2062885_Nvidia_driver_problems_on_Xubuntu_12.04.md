---
title: "Nvidia driver problems on Xubuntu 12.04"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by garrett5200 on 2012-09-25
Hi all,

I'm trying to install Xubuntu 12.04 64bit on a [[COLOR="RoyalBlue"]Gateway GT5432[/COLOR]]("http://support.gateway.com/s/PC/R/1009464/1009464sp2.shtml") with an Nvidia Geforc 7950 GT OC graphics card.  During the live install I had problems with the video and had to run nomodeset which fixed the problem for the live-cd.

After the install the system would hang on a black screen after grub finished.  I've tried to [[COLOR="RoyalBlue"]add nomodeset[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132") during the grub loader to try and repeat what I did during the live CD, but I still get a black screen.

Finally I tried to update my drivers:

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

from tty1, but that doesn't solve the problem either.

Since this is the third install I've done with this setup in the last 3 days I decided this time it would be better to ask for help before I make a bigger mess of it.

Any help would be greatly appreciated

---

### Post by Bashing-om on 2012-09-25
garrett5200; Hi ! Welcome to the forum.

You are doing well.

In addition to installing the proprietary driver, in terminal do these commands:
```
sudo modprob nvidia
sudo nvidia-xconfig
sudo reboot
```Do you now have a GUI ?[INDENT]hth <==BDQ

[/INDENT]

---

### Post by HiImTye on 2012-09-26
> **Bashing-om said:**
> garrett5200; Hi ! Welcome to the forum.

You are doing well.

In addition to installing the proprietary driver, in terminal do these commands:
```
sudo modprob **nvida**
sudo nvidia-xconfig
sudo reboot
```Do you now have a GUI ?[INDENT]hth <==BDQ

[/INDENT]
make sure that that is 'nvidia' :D

---

### Post by garrett5200 on 2012-09-26
Thanks for the help.  Unfortunately I'm still getting a black screen.  

I couldn't find the modprob command, so I ran modprobe.  Hopefully that's right.  It didn't seem to produce any errors when I ran it.

Also, should I still be editing grub when I load it to add "nomodeset"?  I've tried booting with and without editing, and it doesn't seem to have much affect.  Currently Grub line I'm editing looks like this:

 /linux /boot/vmlinuz-3.2.0-29-generic root=UUID=7a605d73-acfd-4fb7-a534-4cb35cfa94cf ro quiet splash $vt_handoff

If I edit the line should I remove anything, and does it matter where I add nomodetest?  I've tried a couple of variations (deleting quiet splash, deleting $vt_handoff, etc), and it mostly just gives me a black screen, or a flashing cursor.  At one point last night I was able to get to the splash screen of the GUI where it hung for 10 minutes and wouldn't go farther.  Unfortunately I haven't been able to repeat that.

---

### Post by garrett5200 on 2012-09-26
After digging around in jockey-text the problem looks like it might be that the system wants to use nvidia_173, which gives me a blank screen.

I can get it to use nvidia_current, but it is disabled.  I'm not sure how it can be disabled and in use, but there it is.  Rebooting with these settings results in the following message "could not write bytes: Broken pipe".

Trying to enable nvidia_current in jockey only gives me an error.

---

### Post by Bashing-om on 2012-09-26
recon ya got both the proprietary and opensource drivers loaded ? Can only have one or the other ..not both on the system at same time...

As to "nomodeset" We want a better permanent option ..if it works to get you booted up we still need to get an "appropriate" driver.... with "nomodest" in use ..runs in a degraded state.

I'll check back in --in a little while.

[INDENT]BDQ
[/INDENT]

---

### Post by garrett5200 on 2012-09-27
Thanks Bashing-om

I'm not sure how to know how many drivers I have loaded short of jockey-text.  Based on that their are a hand full of video drivers, but they are all disabled and not in use.  Is there another way I could be going about finding them?

---

### Post by Bashing-om on 2012-09-27
Run these two terminal commands and we see what we got.
```
sudo lshw -C display 
lspci | grep VGA

```note the VGA is upper case....remember linux is always case sensitive.

by the by ---can you boot up with the recovery mode option in the grub boot menu ?[INDENT]just try'n to help ==>BDQ

[/INDENT]

---

### Post by doktorOblivion on 2012-09-27
Bashing-om is correct.  Boot up in recovery, normally this defaults the driver to SVGA and you will see something.  Then you can login and install the nvidia-current driver.  That usually works.

---

### Post by garrett5200 on 2012-09-28
Digging around in Grub a little I finally found my way into the GUI, but still haven't been able to load the NVIDIA drivers.  I'm not sure if it's still relevant, but here are the results of lshw and lspci

 sudo lshw -C display 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G71 [GeForce 7950 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:e0000000-efffffff memory:fb000000-fbffffff ioport:ac00(size=128) memory:fc000000-fc01ffff

lspci | grep VGA
02:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7950 GT] (rev a1)

---

### Post by Bashing-om on 2012-09-28
yeah, looks like a problem...see the display as "unclaimed" and the configuration has no driver loaded. What to do what to do!

  Your card is seen ...but not loaded...// do you have two monitors ? FYI my radeon card supports two monitors ..I have but one ,,, and "display 1" is  "unclaimed".

You are making progress... soon be a guru ...huh?

Let's see what we can find out to determine what is going on
```
jockey-text -l
sudo lspci
sudo lshw -C video
modinfo GeForce 7950 GT
```According to this howto, the open source driver " Nouveau" is not to be removed.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

then we will see bout loading the current Nvidia driver:
```
jockey-text -e xorg:nvidia_current
```[INDENT]Making progress, soon get to the bottom of this <==BDQ

[/INDENT]

---

### Post by BicyclerBoy on 2012-09-28
The nVidia proprietary driver can **not** load with "nomodeset".

None of the main video drivers work with nomodeset.

The jockey tool never worked properly in the past (with nVidia). But seems to be okay on 12.04.

What does nvidia-settings report ?

Then post /var/log/Xorg.0.log file..

---

### Post by garrett5200 on 2012-10-04
Thanks everyone for the help.  The issue ended up being hardware related.  I got a warning while trying to install 10.04 about a lack of power. As soon as I rechecked the power supply cables everything worked out without a hitch.

---

### Post by Bashing-om on 2012-10-04
Well, all is well that ends well !
Glad you found the problem..

[INDENT]happy ubuntu'n <==BDQ

[/INDENT]

---

