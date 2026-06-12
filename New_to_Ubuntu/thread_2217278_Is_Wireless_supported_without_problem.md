---
title: "Is Wireless supported without problem?"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by Tar_Ni on 2014-04-16
Hi,

I am planning on buying a new laptop for about 300$ on a clearance sale, I intend to remove Windows 8.1 and install Ubuntu 14.04 LTS on it as soon as I get it but will Ubuntu support wireless out-the-box?

I am an unexperienced user and my fear is that wifi will not work. Will I be able to connect to my wifi network for the installation and does Ubuntu support just about every wireless card ou of the box like Windows?

Thanks.

---

### Post by jbaerboc on 2014-04-16
Hi there Tar_Ni, from my personaly experience most wifi devices will work fine out of the box. That being said, your best bet is to find out what kind of wireless card that laptop has and then post it here. That'll allow us to give you a more definitive answer.

---

### Post by Tar_Ni on 2014-04-16
Hi,

Thanks for your reply.

The thing is that I still don't know what laptop I will buy. The clearance sale starting tommorow are solding a couple of ''cheap'' models Windows 8.1 preinstalled for 300$.

That's why I wondered if Ubuntu 14.04 support many kind of wireless card out of the box, and if I will be able to connect on my wireless network for installation of Ubuntu.

---

### Post by su:bhatta on 2014-04-16
This link should give you a rough idea: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by mörgæs on 2014-04-16
Installation should always be done using wired internet access. 

If the built-in wireless card does not support Buntu you can just use a cheap USB wifi adaptor.

---

### Post by baphomet2 on 2014-04-16
The only wireless adaptor that I've run into that isn't supported out of the box is certain Broadcoms.  For those you can just cable connect to your network, install the Broadcom driver via the "additional drivers" tool, reboot and now your wireless works.  I haven't had any problems with Intel wireless cards/adaptors.

---

### Post by su:bhatta on 2014-04-16
> **mörgæs said:**
> Installation should always be done using wired internet access. 


Hi mörgæs, any particular reason for this? 
I have never done that, but luckily, never faced a problem thus far.

I fact, I've often installed without connecting to any network (offline installation), then rebooted and updated the system.

---

### Post by monkeybrain20122 on 2014-04-16
> **mörgæs said:**
> Installation should always be done using wired internet access. 

If the built-in wireless card does not support Buntu you can just use a cheap USB wifi adaptor.

That may not be possible. I don't have any wired internet access and many people are in the same situation (shared internet with router out of reach)

Yes usb wifi card would be handy if the internal card needs to install driver to activate (broadcom mostly), use the dongle to install and connect, then activate the internal card, remove the dongle and reboot. I did that with several laptops with broadcom wifi cards.

---

### Post by monkeybrain20122 on 2014-04-16
> **Tar_Ni said:**
> Hi,
That's why I wondered if Ubuntu 14.04 support many kind of wireless card out of the box, and if I will be able to connect on my wireless network for installation of Ubuntu.

Pretty much, unless it is a broadcom card and for that you may need to do additional work to get it working. For some models you just need to install the driver, but for some there may be additional challenges, so it is best to avoid broadcom if possible.

---

### Post by baphomet2 on 2014-04-16
It is fine to install over wireless, but it does run the risk of installation aborting if you get interference/signal loss.  There is less chance of that on a wired connection which is why it is the safer/best practice.

---

### Post by sammiev on 2014-04-16
Create an ISO to a USB and select try before you install. Then you will have a pretty good idea what is working and not.

---

### Post by Tar_Ni on 2014-04-16
I don't have access to a wired internet connection, only Wifi by a network I don't really have access to, provided in my room by the landlord.

That's why I hope that the Ubuntu kernel drivers will suport the wifi card out of the box, whichever it is, on the new laptop I will purchase. If Ubuntu does support a wide range of card, than I guess I stand a very good chance. That was my initial question.

That would be convenient for me..


> **sammiev said:**
> Create an ISO to a USB and select try before you install. Then you will have a pretty good idea what is working and not.

That may be a solution. I just hope not to be stuck with Windows because of an unsuported wifi card. I hope it will not be the case.

---

### Post by mörgæs on 2014-04-16
Installing with wired connection is not necessary, but it prevents many problems.

[LIST]
[*]Many cards, not only Broadcoms, need additional drivers.
[*]The wifi connection could be slow and/or unstable, especially with the old 802.11 B and G standards.
[*]The user might need to search or post in Ubuntuforums or do other kinds of troubleshooting.
[/LIST]
I always recommend a wired connection because I don't know who will be reading my advice in the future. It might be a beginner taking his first steps into the Buntu world, and I want his first encounter (that is, the installation) to be as safe and smooth as possible. Bringing the portable to a place with wired connection is often a good investment.

= = =
Tar_Ni, I think you should just try. If it fails then you have to give it a go again at some friend's place.

---

### Post by wildmanne39 on 2014-04-16
Ubuntu supports a lot of wireless devices but with each new release and update many of them need a little tweaking. 

The newer the hardware the more likely support has not arrived yet for your wireless card.

Broadcom cards are usually very stable and supported nicely, but they require firmware after installation in many cases due to legal reasons.

During the time that I have worked with wireless issues about three years now, I have seen devices that are supported well begin to have a hard time to get them to work and many that were not supported know work well, it just depends on the kernel and your particular device, but most can be made to work.

---

### Post by Tar_Ni on 2014-04-16
Thanks guys for all your replies.

I will try it and see what happens. I will start a new thread if I have problem making it work.

Have a nice day. :)

---

### Post by mörgæs on 2014-04-16
Ok, but first please mark this one 'solved'.

---

