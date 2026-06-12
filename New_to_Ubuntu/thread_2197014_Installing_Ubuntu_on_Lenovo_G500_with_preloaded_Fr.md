---
title: "Installing Ubuntu on Lenovo G500 with preloaded FreeDos - so many problems!"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by cappuccinoandchoco on 2014-01-01
Hello everyone,

I searched the forums, looking for similar issues, but haven't found what I needed. 

So here's the background info:
I bought my mum a new Lenovo G500 laptop that came with only FreeDos on it. I've been trying for 2 days now to install Ubuntu. I tried by burning ISO to a DVD, but it didn't work and I since I ran out of DVDs, I turned to a USB stick. 

I downloaded iso from Ubuntu official page ( I tried to download ISO via Unetbootin, too) and burned it to the usb using Unetbootin, but I was getting either 'isolinux.bin Invalid or missing' or 'Invalid or Corrupt Kernel Image' message for the first 5-6 times I tried.  I tried different ISO-to-USB burners, different Ubuntu versions, different formatting options...

I finally download ISO for 12.04 through Torrents and it worked, BUT after the installation, I got a message telling me it didn't manage to read/open apt package, something like that, because the package is not authentic. 
So I downloaded another one from Torrents, but it wasn't good as when I started the installation process, the graphics looked 'broken'. 2 times I got a black screen after the BIOS screen.

I really don't understand it, why is Ubuntu so hard to install?! Even when the package files come from their own official website?

If anyone can help me and spare me this misery, please advise!

Thanks!

---

### Post by fantab on 2014-01-02
Sounds like a bad 'burn' to me.
Download the latest version of Ubuntu, which is 13.10, perferably via torrent. [See HERE]("http://www.ubuntu.com/download/alternative-downloads") for torrent download.
Then do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded .iso to verify its integrity.
Burn the verified ubuntu.iso to the USB.
Install.

> ...the graphics looked 'broken'. 2 times I got a black screen after the BIOS screen

What Graphics Card do you have on the laptop?
You should use '[NOMODESET']("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997") option during boot to use 'failsafe graphics mode'. Later after installing Ubuntu successfully you have to boot Ubuntu again with 'nomodeset' and install appropriate 'graphic drivers'.

---

### Post by mörgæs on 2014-01-02
Are you able to run a live boot?

---

### Post by cappuccinoandchoco on 2014-01-02
Hi, 

yes, but how is it possible to have 15 bad burns? Especially when the iso is downloaded from official page?

I tried everything you mentioned, except for MD5SUM check, which I'm going to do now, and that's my last attempt, I'm too tired of download-wait-burn-install-fail routine.

> **fantab said:**
> Sounds like a bad 'burn' to me.
Download the latest version of Ubuntu, which is 13.10, perferably via torrent. [See HERE]("http://www.ubuntu.com/download/alternative-downloads") for torrent download.
Then do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded .iso to verify its integrity.
Burn the verified ubuntu.iso to the USB.
Install.


What Graphics Card do you have on the laptop?
You should use '[NOMODESET']("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997") option during boot to use 'failsafe graphics mode'. Later after installing Ubuntu successfully you have to boot Ubuntu again with 'nomodeset' and install appropriate 'graphic drivers'.

---

### Post by cappuccinoandchoco on 2014-01-02
Not sure what you mean by that, I made a bootable USB and burned the iso to it with the help of Unetbootin, I think that's it. When I get in BIOS, I choose boot from USB device and then after that it's either:
a) Invalid Kernel image
b) black screen after choosing to install Ubuntu
c) it starts installing Ubuntu but then it gives me a message that there's a part it's not able to copy from CD, sth like that.

> **mörgæs said:**
> Are you able to run a live boot?

---

### Post by mörgæs on 2014-01-02
Probably better to try installing the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") (using a USB stick).

---

### Post by cappuccinoandchoco on 2014-01-02
That requires internet access during installation? Since the laptop is new, it doesn't have wifi driver installed, so I don't have internet access...

> **mörgæs said:**
> Probably better to try installing the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") (using a USB stick).

---

### Post by holycow131415 on 2014-01-02
> **cappuccinoandchoco said:**
> That requires internet access during installation? Since the laptop is new, it doesn't have wifi driver installed, so I don't have internet access...

Plug it into your router via cat5 cable.

---

### Post by cappuccinoandchoco on 2014-01-02
I just downloaded 3 new ISOs, via torrents. I checked MD5SUM for all of them and none of them match. Wasted data and time.

Plugging in the cable doesn't work. I think I'm going to give up on Ubuntu for now. Maybe one day when the things get a lot more simple and straightforward, I will give it a chance again.

---

### Post by fantab on 2014-01-02
> **cappuccinoandchoco said:**
> Hi, 

yes, but how is it possible to have 15 bad burns? Especially when the iso is downloaded from official page?

I tried everything you mentioned, except for MD5SUM check, which I'm going to do now, and that's my last attempt, I'm too tired of download-wait-burn-install-fail routine.

All the errors you describe in your first post relate to either a bad download or a bad burn, except where you got a 'black screen'.
It is not impossible to have 15 bad burns or downloads.

Have you tried 'nomodeset' option?
Do you have UEFI or 'legacy BIOS'?
Is there a OEM pre-loaded SSD in the picture?
Post the hardware specs of your laptop?

---

### Post by mörgæs on 2014-01-02
The minimal ISO is 30 MB. Much less risk of an error here.
Yes, all installs should be done with wired internet access, both minimal and full size.

---

### Post by sudodus on 2014-01-02
> **holycow131415 said:**
> Plug it into your router via cat5 cable.

+1

I think this is the solution. Get an ethernet cable (cat5 or similar) and get a wired internet connection. That reduces the risk of bad downloads very much. Particularly, it should be OK via torrent because checksums are used in the torrent process.

Good luck :-)

---

### Post by chkneater on 2014-01-02
Always burn at the slowest speed!!!!

---

### Post by fantab on 2014-01-02
> **cappuccinoandchoco said:**
> I **just downloaded 3 new ISOs, via torrents. I checked MD5SUM for all of them and none of them match**. Wasted data and time.

Plugging in the cable doesn't work. I think I'm going to give up on Ubuntu for now. Maybe one day when the things get a lot more simple and straightforward, I will give it a chance again.

That is really strange. But atleast we know what the problem is. 
When downloading with 'torrent' check and re-check your download.
The problem is not related to Ubuntu so much as it has to do with your downloads.

> **fantab said:**
> All the errors you describe in your first post relate to either a bad download or a bad burn, except where you got a 'black screen'.
It is not impossible to have 15 bad burns or downloads.

Have you tried 'nomodeset' option?
Do you have UEFI or 'legacy BIOS'?
Is there a OEM pre-loaded SSD in the picture?
Post the hardware specs of your laptop?

---

### Post by PGodinho on 2014-07-29
Hello did you find a way to install ubuntu in your Lenovo G500?

---

### Post by sotiris2 on 2014-07-29
What problem do you face PGodinho? The OP's problems had more to do with his internet connection rather than the Levono G500. I would suggest you make your own thread where you describe your own problem.

---

