---
title: "Ubuntu won't start"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by LeonNic on 2013-01-23
I'm an absolute beginner. I tried to start Ubuntu in my computer from a CD but with no results. The computer tries to start but stalls in a few seconds. I have tried it in my laptop and  it worked ok. My computer:

AMD Athlon(tm) 64 Processor 3500+
 2.20 GHz 1.18 GB of RAM

I will strongly appreciate any help

---

### Post by oldfred on 2013-01-23
Welcome to the forums.

If live install works on another computer that should answer the usual questions of a good download and a good write to CD/DVD/Flash drive.

But video may be different between systems or other hardware issues that require different boot parameters. 
What video card/chip do you have? But I would try nomodeset first.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by LeonNic on 2013-01-23
I already posted this problem before and had no answers. Maybe it was nos explicit enough. When I try to start Ubuntu with the CD, it starts to load but in a few seconds stalls and there is no signal in the display. Maybe a video card problem as I have heard. My computer:

Compaq Presario 
AMD Athlon(tm) 64 Processor 3500+, 2.20 GHz, 1.18 GB of RAM
Graphics Nvidia Gforce 6150 LE

Thanks. I will appreciate any help in this matter

---

### Post by Easy Limits on 2013-01-23
When you say "start" do you mean you are trying to install Ubuntu on to your hard disk or run it as a live CD?

---

### Post by squakie on 2013-01-23
Please only open a single thread on a problem.  Opening more than 1 will just make reponses that much more confusing.

---

### Post by uRock on 2013-01-23
Duplicate threads merged.

> **LeonNic said:**
> I already posted this problem before and had no answers. Maybe it was nos explicit enough. When I try to start Ubuntu with the CD, it starts to load but in a few seconds stalls and there is no signal in the display. Maybe a video card problem as I have heard. My computer:

Compaq Presario 
AMD Athlon(tm) 64 Processor 3500+, 2.20 GHz, 1.18 GB of RAM
Graphics Nvidia Gforce 6150 LE

Thanks. I will appreciate any help in this matter

The post from oldfred has links explaining how to get your system to boot. Specifically,> How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by LeonNic on 2013-01-24
> **Easy Limits said:**
> When you say "start" do you mean you are trying to install Ubuntu on to your hard disk or run it as a live CD?

I wanted to run Ubunto as a live CD

---

### Post by oldfred on 2013-01-24
With nVidia you have to have nomodeset for both liveCD/DVD/Flash installer and first boot after install. 

Scrreen shots in links posted above show details but his is what I did:

       I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by LeonNic on 2013-01-24
Thank you very much uRock. I was able to start Ubunto from CD as a demo, but couldn't open internet. I have wifi at home and use a "Belkin Surf & Share Wireless USB Adapter" which I use with Windows, but I don't have the faintest idea on how to make it work with ubuntu. I will appreciate if you can tell me how. Thanks a lot.

> **uRock said:**
> Duplicate threads merged.



The post from oldfred has links explaining how to get your system to boot. Specifically,

---

### Post by squakie on 2013-01-25
If you are not going to install ubuntu, but want to use the cd only and have your currently non-working wireless work, it probably needs a driver installed.  Installing a driver would involve directly wiring your PC to the router to even get the driver.  A problem is that this would only be good for 1 session since the cd can not be updated.  Usually this would be accomplished via a USB device created with persistence.

However, since you are able to post here, you have access somewhere to the net.  So, let's find out what kind of adapter you have first.  Open a terminal window then:

lspci

Copy and paste the output from those back here and we can go from there.

Even if you have installed Ubuntu and the wireless doesn't work it will be the same process.

---

