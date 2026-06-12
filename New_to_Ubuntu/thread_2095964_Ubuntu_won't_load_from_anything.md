---
title: "Ubuntu won't load from anything"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by davidtrickett on 2012-12-18
I have an AMD 64 bit cpu & a Nvidia GTX460 video card. I have Windows XP64, XP32 & 7 on different HDD's.

I am trying to install Ubuntu 12.04 - preferably 64 bit.

The machine flatly refuses to load any version beyond 10.04 from either CD/DVD or usb. I have checked the downloads with md5sum & all seem ok - also the 32 bit versions work fine on another machine.

I have tried nomodeset with all versions - no effect.

I have succeeded in installing 10.04 and this seem ok - it also happily picks up all my other os's.

After going through the long process of updating to 12 from that I find that it will not boot from grub even with nomodeset. I have persuaded it to boot in recovery mode, but the size & shape of the display is almost unusable.

I know that there are issues with this graphics card, and have tried the advice at [http://askubuntu.com/questions/140760/ubuntu-12-04-nvidia-gtx-460-video-card-installation](http://askubuntu.com/questions/140760/ubuntu-12-04-nvidia-gtx-460-video-card-installation). Once I had figured out how to kill X (!) at the first attempt it went into a sulk because I had the wrong CC variable. Eventually I managed to sort this, but then it didn't like my kernel! At that point I gave up - it should not be necessary to go into lengthy & complex command line operations to do something as simple as installing video drivers.

Can anyone at least suggest a way of persuading 12.04 64 bit (or 32 for that matter) to load up from DVD or usb? 

Thanks

---

### Post by grahammechanical on 2012-12-18
You are right

> it should not be necessary to go into lengthy & complex command line operations to do something as simple as installing video drivers.

The problem, in my opinion, has been Nvidia drivers being buggy. I have had working installs of 12.10 break when the Nvidia driver was updated to a newer version. I have a fresh 12.04 install that breaks when I try to activate what Additional Drivers calls Nvidia-current. I have my original 12.04 install working with an older Nvidia driver which I will not update.

I use the Nouveau open source driver on my 12.10 install and in my 13.04 install that I am testing.

Try to get into the 12.04 install using recovery mode and use the Additional Drivers utility to de-activate the Nvidia driver or activate one of the experimental ones.

Also can you give any information that might give us a clue as to why the 12.04 Live session does not load?

Oh, by the way, I find that Recovery Mode>Resume sometimes gets me to a working desktop. It loads the OS using the open source video driver. Better than Recovery>Fail Safe mode.

Regards.

---

### Post by davidtrickett on 2012-12-19
Graham (I assume!)

Thanks for this.

My main problem is the failure to load the live session from usb or cd/dvd. I'll do some more work on this & get back to you with more detail.

David

---

### Post by davidtrickett on 2012-12-19
Hello again.

I've now had a more detailed look at what it happening. This refers to 12.04 32 bit - please take my word that it is more or less the same with _anything _after 10.x.

Loaded it on to a usb stick - tested on another machine & works fine.

On the problem machine trying to boot from this it goes so far and stops with this last line:

[7.621696] sr 7:0:1:0: Attached scsi generic sg6 type 5

Replacing splash in the command line with nomodeset results in more or less the same thing - last lines are 

[7.535521] sr 7:0:1:0: Attached scsi generic sg6 type 5
[7.537521][drm] Initialised drm 1.1.0 20060810

The only other difference is that without nomodeset the screen resolution increases before the last screen.

I do have photographs of these screens but I don't know how to attach them to this!

I don't have any problems booting from other boot devices - indeed U 10.04 works fine.

Any ideas?

David

PS I'm also in London.

---

### Post by mysteriousdarren on 2012-12-19
I used the alternate install cd on both laptops that were having trouble booting from the regular one. Lubuntu and Ubuntu simply wouldn't boot. I had to downgrade to 12.04 and it worked. Using a usb to boot from has saved me from headaches in the past.

---

