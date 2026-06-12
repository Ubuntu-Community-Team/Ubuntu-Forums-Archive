---
title: "Help with Ubuntu 12.04 - new Sky router"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by kev3 on 2014-02-17
I downloaded Ubuntu 10.4 over a month ago after buying a new desktop pc with no operating software. Things were going smoothly until my Sky router broke, and Sky sent me a new one, with a new password. I just couldn't remember how i managed to set my broadband connection with Ubuntu. So, have been looking all over the net for a solution and thought that i had found one, a website said to delete network manager (which i did, regretfully), and then things got confusing and i tried to re-install Ubuntu from the CD i had burned. My dilemma is this, should i try and re-install network manager (and hopefully someone will be able to explain how to add my new sky router), or should i try and re-install Ubuntu from scratch? I never knew just having a new router would be so much trouble - nothing has changed apart from my new router password! Any help would be very gratefully received.

---

### Post by howefield on 2014-02-17
> **kev3 said:**
> ... or should i try and re-install Ubuntu from scratch? 

If you do, bear in mind that 10.04 is no longer a supported version as it reached end of life last year.

You would probably be better using 12.04 which is the latest LTS release and can be upgraded to 14.04 in April which is the next LTS release.

---

### Post by kev3 on 2014-02-17
Don't know if i'll be able to, can't get the boot menu for some reason. Arrggghhh!

---

### Post by 3rdalbum on 2014-02-17
I agree with Howefield. Ubuntu 10.04 is way, way out of date, and it's reached End Of Life. Better to install Ubuntu 12.04 as it's still got more than three years of support - and you can upgrade it to the upcoming 14.04.

I'm sure you've learnt this already, but: It's very rare to be able to fix things by removing parts of the system. If somebody told you that you could fix something in Windows by going into the System32 folder and deleting several files there, I'm sure you wouldn't do it - you'd smell a rat.

To answer your question, once you've got your Ubuntu 12.04 set up, you just need to plug in your router via the Ethernet cable. That will connect you to the router automatically. Go to the Network Manager applet on the bar on the top of the screen, and come down to Connection Information. Find the "Default Route" number (it'll look something like "192.168.42.129") and copy and paste that number into Firefox's address bar. You should see a login page for the Sky router, and then you can log into it with the username and password described in the router's documentation. Follow the router's documentation from there on to put in the correct settings.

You might not even need to log into the router, it might just automatically know the right settings and use them.

---

### Post by howefield on 2014-02-17
I moved from Sky about a year ago, and all I remember on a fresh install is that the SSID would be recognised, try to connect and give me the password box. As simple as that.

I see that the hardware has changed since then.

> Plug your Sky Hub into your master phone socket using the microfilter provided.
Follow the simple step-by-step instructions in the set-up guide that came with your Sky Hub.
There’s no need to remember passwords. Simple and secure WiFi Protected Setup (WPS) makes it even easier for you to connect with any WPS enabled device. Just find your network and push the button on your router to connect.

---

### Post by kev3 on 2014-02-17
Thanks guys, any ideas as to what button to press once my pc boots? I've tried F12, F9, delete, esc and shift but to no avail.

---

### Post by kev3 on 2014-02-18
Can't believe the mistake i made when typing my post (only excuse i have is that i work nights!), i actually have 12.4 installed! Still in a dilemma though, how can i re-install network manager?

---

### Post by howefield on 2014-02-18
Glad you are on 12.04 :)


To reinstall network manager, probably be as simple as

```
sudo apt-get install network-manager
```

But you will need to either hard wire the computer to get a connection to download the package, or download the package with another computer and copy it to /var/cache/apt/archives/ and run the above command.

---

### Post by kev3 on 2014-02-19
Sorry for being green mate, what do i have to do to 'hard wire'?

---

### Post by howefield on 2014-02-19
Sorry, by hard wired, what I meant was if you have no connection to the internet due to removing network manager, you'll need to use an ethernet cable to the router in order to download the package.

---

### Post by kev3 on 2014-02-21
Thanks for all your help people, it just seems too much hassle having Ubuntu as an OS. Looking to get rid of it, anybody know what keys i might need to press to access the boot menu?

---

### Post by kev3 on 2014-02-22
It seems so difficult to remove Ubuntu, or at least re-install download manager. Please help folks.

---

### Post by intensedaz2 on 2014-02-23
Do you still have a Live CD (ubuntu installation disc)  Kev ?, if it was me i think i would connect my PC to the router via ethernet cable , pop the live cd into the pc , reboot and do a clean install.

---

### Post by kev3 on 2014-02-23
Think i will have to mate, will i encounter any problems with doing a clean install? I'm so green with this OS, i don't even know how to run a CD. It just automatically recognised the CD the first time i installed Ubuntu.

---

### Post by intensedaz2 on 2014-02-23
> **kev3 said:**
> Think i will have to mate, will i encounter any problems with doing a clean install
Hopefully not ;) , as i said , connect to the web via ethernet cable, put your cd into the drive and reboot.
You should now be given the option of trying or installing Ubuntu , install and fingers crossed you'll be good to go.

---

### Post by kev3 on 2014-02-24
Do i need to be connected to re-install the CD? The CD is in the CD drive, but when i start my pc (i press delete), i can't get the boot menu. Any ideas what i have to press? I've got a Gigabyte motherboard.

---

### Post by Vladlenin5000 on 2014-02-24
> **kev3 said:**
> Do i need to be connected to re-install the CD? The CD is in the CD drive, but when i start my pc (i press delete), i can't get the boot menu. Any ideas what i have to press? I've got a Gigabyte motherboard.

You can always change the boot order inside the BIOS but newer boards (let's say since 10 years ago *probably*) also allow access to the boot menu with a dedicated key. Gigabyte usually has F12 for that purpose. Once in the boot menu just select the CD-ROM option and it'll boot from the Ubuntu CD you already have in the drive.
You don't need an internet connection to install but it's highly recommended. With you can select the option to install updates which will save you considerable time later. You also may need "additional drivers" or proprietary firmware for your WiFi device and to have an internet connection is obviously required. This part you'll check after installing, not during the installation.

---

### Post by intensedaz2 on 2014-02-24
Dont modern pc's boot from the optical drive first anyway ? , not sure why you would have to press the delete key unless the boot order was different, from usb for instance.

If at all possible i would install connected to the net , as Vladlenin5000 has said it will save you time in the long run

---

### Post by Vladlenin5000 on 2014-02-24
They all boot from the optical drive. Are you saying it's the default? Hardly. The default is the system drive in all PCs with factory installed OSs. That's not the point anyway.
The point is booting from the CD and install it. What's weird here is the OP having installed it already presumably from a CD and now not being able to do exactly the same... And almost all BIOS/UEFI, whatever show the keys for BIOS/UEFI setup menus and boot order during post so the user don't have to ask (plus all the motherboards' manuals are available online and download in seconds)... Really, it makes no sense being stuck in that step.

---

### Post by intensedaz2 on 2014-02-24
No, not saying its the default. My point was why he would have to press the delete key.

---

### Post by kev3 on 2014-02-25
I've tried F12 as that's what it says to press when i boot, it didn't work and someone said to press ESC - that doesn't work either, tried almost every key on the keyboard, but it just boots up as normal - it's so frustrating!

---

### Post by intensedaz2 on 2014-02-25
What is the PC manufacturer Kev ?

---

### Post by Vladlenin5000 on 2014-02-25
All Gigabyte board I know of:
DEL > BIOS setup
F12 > Boot menu

What doesn't work exactly?
No boot menu > keyboard not recognized during post (can't access BIOS setup or Qflash either)
The menu comes up, you select boot from CD-ROM but it doesn't boot from the CD > CD isn't bootable or faulty drive

Needless to say nothing of this has to do with the OS.

---

### Post by intensedaz2 on 2014-02-25
Could this be a problem with the installation disc itself , Vlad ?

---

### Post by kev3 on 2014-02-25
AMD 3.9 BULLDOZER II X4 QUAD CORE FX 4130 CPU
8GB 1600mhz DDR3 RAM
1000GB
Integrated ATI RADEON HD 3000 Graphics HDMI , VGA, DVI
Gigabyte 78LMT-USB3 Motherboard & Drivers

---

### Post by kev3 on 2014-02-25
The installation disc worked, was online and everything worked fine. I then had a new Sky router and didn't really know what to click to enter my new password - just thought it would be as easy as it would have been with Windows. That's when i deleted Network Manager.

---

### Post by Vladlenin5000 on 2014-02-25
You probably just needed to select the new WiFi network name and enter the default password -and/or- you could have connected via Ethernet and configured the new router as you intended...

Now, to reinstall you also should connect via Ethernet if doable. Here's your startup screen during post. Confirm the keys for boot menu, BIOS and others (and read the edited part of my previous post):

---

### Post by kev3 on 2014-02-27
Thanks Vlad, i don't get a boot menu, and can't access BIOS setup. I'm not sure what Qflash is.

---

### Post by kev3 on 2014-02-27
That's the correct start-up screen by the way.Just noticed that as soon as i press F12 the keyboard light goes out.

---

### Post by kev3 on 2014-03-02
I've tried connnecting via Ethernet, but thinking i can't do this without network manager?

---

### Post by kev3 on 2014-03-10
Decided that the only option is to install Windows. Will i be given the option to delete Ubuntu, when i install Windows?

---

### Post by 3rdalbum on 2014-03-10
If you can't boot an Ubuntu CD then you won't be able to boot a Windows one either.

Yes, if you boot the Windows CD it gives you the ability to create and delete partitions. You can delete the Ubuntu one(s) and create a Windows one.

---

### Post by Vladlenin5000 on 2014-03-10
> **3rdalbum said:**
> If you can't boot an Ubuntu CD then you won't be able to boot a Windows one either.

Exactly!
Not so long ago I witness the same difficulty in other user who end up blaming the OS - Ubuntu - for something that has NOTHING to do with it or any other OS. I hope the OP understand this too.

---

### Post by kev3 on 2014-03-15
Just played about with some random keys and got the GNU GRUB, is this the boot menu? I've now got 5 options: 1.) Ubuntu with Linux 3.8.0-35-Generic 2.) Ubuntu with Linux 3.8.0-35-Generic (recovery mode) 3.) Previous Linux Versions 4.) Memory Test  (memtest 86+) 5.) Memory Test  (memtest 86+ Serial Console 115200). If i wish to delete Ubuntu and do a fresh install what do i do? Grateful for any help.

---

