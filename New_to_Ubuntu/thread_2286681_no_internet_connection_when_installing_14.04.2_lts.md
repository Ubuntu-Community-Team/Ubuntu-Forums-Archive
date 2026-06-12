---
title: "no internet connection when installing 14.04.2 lts"
date: 2015-07-13
forum: New to Ubuntu
---

### Post by Broad_ripple on 2015-07-13
Okay, I have searched all over the net and here and can find no info on how to fix this.

I have been trying to install 14.04.2 LTS to a virgin Samsung 256GB SSD 3D-NAND. No matter what distro I try, the connect to internet for updates box at the beginning of the install is "Xed" out. I am unable to install updates during the install. When 14.04.2 comes up, it is displaying as though I am using an old CGA video card (huge icons, crude display). The install is so basic I can't really use it. When I check on network, it says not connected (after install). I can't download updates or anything. The install is unusable.

Going back to W7P, internet connection is fine (WIFI). Why is the connect to internet box for updates "Xed" out when the connection is working in windows? I am unable to change the "X". It is grayed out (inactive).

Please help.

Bill

---

### Post by Broad_ripple on 2015-07-13
Okay, I have searched all over the net and here and can find no info on how to fix this.

I have been trying to install 14.04.2 LTS to a virgin Samsung 256GB SSD 3D-NAND. No matter what distro I try, the connect to internet for updates box at the beginning of the install is "Xed" out. I am unable to install updates during the install. When 14.04.2 comes up, it is displaying as though I am using an old CGA video card (huge icons, crude display). The install is so basic I can't really use it. When I check on network, it says not connected (after install). I can't download updates or anything. The install is unusable.

Going back to W7P, internet connection is fine (WIFI). Why is the connect to internet box for updates "Xed" out when the connection is working in windows? I am unable to change the "X". It is grayed out (inactive).

Please help.

Bill

---

### Post by Geoffrey_Arndt on 2015-07-13
1).   What device (laptop/desktop) & model PC is this SSD going into? 
2).   What are the specs on that device?  Especially video card/chipset, etc.
3).   What are the specs for the parent device (PC)'s network hardware (broadcom, atheros, intel . . etc.)

The internet option is grayed out because the installer application does not "see" a  recognized internet connection . . . if you had something like "genuine" Intel Wireless, it would not be grayed out.   An ethernet connection would immediately fix that (in most cases).

The display is crude because you have a gpu or integrated video chipset that is not supported by Ubuntu "out of the box" . . . for example, if Nvidia or ATI video, you will need the proprietary drivers (which are easy to install with a few tips once we have some very minimum info about your hardware.

PS - almost forgot:

4).  Does your PC use standard bios or uefi?  (probably uefi if newer than 2010).   UEFI may require different install process.
5).  Is this a dual-boot system, and if so, what is the other OS?

---

### Post by VMC on 2015-07-14
A couple of things to check. Open a terminal (Ctrl+Alt+t), then type:
 ```

ifconfig -a
dmesg | grep eth
lspci | grep Ethernet
cat /etc/networking/interfaces
``` What's the output from each of the four?

Edit: I just realized you have wifi. I'm not sure what to expect, since I don't use wifi. Or not at the moment. Maybe someone will come along who does.

---

### Post by oldos2er on 2015-07-14
Threads merged. Please don't create duplicate threads for the same question, it dilutes the community's ability to help.

---

### Post by Broad_ripple on 2015-07-15
> **Geoffrey_Arndt said:**
> 

1).   What device (laptop/desktop) & model PC is this SSD going into?

It is an [COLOR=#333333][FONT=Helvetica neue]**HP Envy Phoenix Desktop 810-145QE i7-4790 3.6GHz 16GB RAM 2TB HDD + 16GB mSSD on board cache BluRay nvidia GTX745 Windows 7 Pro OS  **[/FONT][/COLOR](pasted from ebay).[COLOR=#333333][FONT=Helvetica neue][B]
[/B][/FONT][/COLOR][COLOR=#333333][FONT=Helvetica neue][B]
[/B][/FONT][/COLOR]My old computer lasted 12 years and was an HP with a Pentium 4 (paid more for it than I did this one). It was good while it lasted but finally gave out. This new HP is a refurb and I got a good deal on it from ebay. Though the on-board Ethernet gave out quite quick (unable to start device, Code 10). This happened after a bios upgrade. Going back to original bios didn't fix that code 10.[COLOR=#333333][FONT=Helvetica neue][B]
[/B][/FONT][/COLOR]
2).   What are the specs on that device?  Especially video card/chipset, etc. 

Couldn't find chip set. Video card is nvidia GTX745 w/4GB cache.

3).   What are the specs for the parent device (PC)'s network hardware (broadcom, atheros, intel . . etc.)

I took you suggestion and yesterday bought a pci-e NIC card and then reinstalled. Install updates was active (not gray) and the box was auto checked. Not sure that it did much though, as I immediately checked for updates online after the install and they took twice as long as the install itself did (there must have been lots of stuff to update).

The internet option is grayed out because the installer application does not "see" a  recognized internet connection . . . if you had something like "genuine" Intel Wireless, it would not be grayed out.   An ethernet connection would immediately fix that (in most cases).

The display is crude because you have a gpu or integrated video chipset that is not supported by Ubuntu "out of the box" . . . for example, if Nvidia or ATI video, you will need the proprietary drivers (which are easy to install with a few tips once we have some very minimum info about your hardware.

PS - almost forgot:

4).  Does your PC use standard bios or uefi?  (probably uefi if newer than 2010).   UEFI may require different install process.

The PC uses uefi. But Ubuntu did install okay last night. 

5).  Is this a dual-boot system, and if so, what is the other OS?

Right now I am not intending to dual boot. I plan on going into setup on restart then select which drive to boot from to choose which OS to use (each drive will be dedicated to a specific OS). Even if I was using dual boot (and have before) I would still need to restart. It only takes me a few seconds to change the bios to select which drive to use. I will leave the hdd with W7P as is and install Ubuntu on the ssd as a stand alone system. I won't be switching them often.

I am still experiencing the CGA type display. You mentioned I would need to install a proprietary driver if I was using an nvidia card. Can you help me with this? The video card is an nvidia GTX745.

Also, I have installed a Hauppauge HVR-1265 HDTV TV Tuner card (it is absolutely wonderful under Win 7). The research I did online before buying this card said that most all Hauppauge tV tuner cards are supported by Ubuntu. But I am not sure how to get the Linux/Ubuntu driver for it (and install it). Can you help with this, too?

I started with Ubuntu 12.04, moved to 14.04 and now looking to use 14.04.2 LTS as my latest distro. Do you think that 14.04.2 is a good choice? Or do you think some of the later versions are better?

Thanks so much for all your help (really). I am sure to learn some new things!

Bill

---

### Post by Broad_ripple on 2015-07-15
Wow, most of what I wrote to you did not come over on that post. What I did was use "reply with quote". Then under each question you asked, I wrote my responses. But I see that only what I wrote under your item 5 was sent! It's a real shame as it was quite a detailed letter.

Computer is a [COLOR=#333333][FONT=Helvetica neue]**HP Envy Phoenix 810-145QE i7-4790 3.6GHz 16GB RAM 2TB HDD +16GB mSSD BluRay Nvidia GTX745 w$GB cache Windows 7 Pro OS **[/FONT][/COLOR](pasted from ebay).

 Took your suggestion and last night bought a NIC card (the on board is not working). Install went well and updates was checked and not grayed out. So that part is okay now. 

Just need some help with the video card and TV tuner card.

What a disappointment the majority of the previous post was lost!


[COLOR=#333333][FONT=Helvetica neue][B]


[/B][/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2015-07-15
Well what is the on board wifi card? You probably just need a driver (e.g some Broadcom cards don't work out of the box without installing additional packages) Since your external wifi card is working you can download additional packages required for the on board card with it.

Once installed OS, go to the dash, look for Software & Updates and check the Additional drivers tab see what it recommends.

Just to give us more info, run 

```
lshw -C network
```

and let's have a look at the outputs.

---

