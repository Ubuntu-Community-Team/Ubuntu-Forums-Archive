---
title: "Old PC Purchase With Ubuntu"
date: 2017-05-21
forum: New to Ubuntu
---

### Post by jstar1 on 2017-05-21
Well, I finally am posting about this. Purchased a used PC with Ubantu - in Hebrew - I need it to be in English interface - locked out - no password and extremely not Ubantu savvy. I have a legit copy of Windows 7 that I would prefer using at this point because I am not able to navigate well in this interface. Suggestions as a last ditch effort? WWYD?
Thanks - star

---

### Post by TheFu on 2017-05-21
Welcome to our forums.

You can change the language used. It is in the menus somewhere.  I don't use stock Ubuntu, so can't tell you where. Also, Hebrew would be an issue for me too.  If you look through the "ubuntu desktop guide", there should be a section on changing the language and keyboard. The icons should be the same.  That would be the fast way.

Or you can wipe the OS and load a fresh Ubuntu.  Only non-UEFI systems, that shouldn't be hard.  Just be certain to back up any data you want to keep. For an older PC, Lubuntu would running better.  Ubuntu-Mate for a slightly newer PC works well and has a nice, intuitive interface.

If you want Win7, then just load Win7.  

While most people don't load the OS onto their PCs, it isn't THAT hard most of the time.  

Be certain to patch ASAP regardless of the OS you run.  I patch every Saturday morning.  I guess with Windows, you get pushed patches monthly?  I don't know. Don't use Windows much and when MSFT changed from a privacy policy to a non-privacy policy about 16 months ago, I stopped patching my remaining Win7 box and locked down the network to reduce the risk it will be hacked. So far, so good.

WWID?  I'd wipe the current OS and load Ubuntu-Mate.  You are in an Ubuntu forum, after all.  It is your PC and your choice.

---

### Post by jstar1 on 2017-05-21
cant change the language or install anything (tried updating the browser) because every installation is asking me for passwords which obviously I do not have........is it possible to reset Admin passwords? At least this would give me some idea where everything is. I don't even know what version of Ubuntu I'm running...

---

### Post by oldfred on 2017-05-21
You should be able to change password:

 [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by TheFu on 2017-05-21
Ah. Sorry, you said that and I forgot.  I suspect you might not have the correct keyboard to enter the password, even if you knew it.  Resetting the admin password isn't hard for a techy person, but it is multi-stepped and extreme attention to detail is needed.  But in the end, you wouldn't be able to trust the system. The person who installed the OS could have setup multiple remote access methods that would be hard to find, even for someone like me (20+ yrs as a Unix admin).

Best to wipe the OS and load a fresh copy of ubuntu-mate. That usually means making a bootable flash drive. Everything on the flash drive will be wiped, so don't expect any data on it to be there later. Backup if you want it retained.  [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) tries to explain the process. I use a tool called **yumi** to make mutli-boot flash drives, but it doesn't have all the explicit instructions someone new would likely need.  Being new isn't a big issue. We all were at some point.

BTW, there are youtube videos for almost everything someone could want to do with Linux.  If you learn that way, it can be a good solution.  

Get the 16.04 version of Ubuntu-mate. This has 5 yrs of support, unlike the current release (17.04) which only has 9 months.  You and I are better off staying with LTS releases.  Those happen every even year, in April. Ignore all other releases.  10.04, 12.04, 14.04 and 16.04 are LTS releases. See the pattern?

---

### Post by TheFu on 2017-05-21
Hey  Oldfred - do you have other recommendations for the issue?  Which ubuntu?  Loading Win7? Etc?  Bet Star1 would appreciate some more views.

---

### Post by Autodave on 2017-05-21
Not knowing any specs, I would do a clean install of either Xubuntu or the lighter Lubuntu. Either one of them is way likelier to be faster than Windows.

You will not need a password to wipe what is on there and start over, but you may need to go into the BIOS and change or pick the boot order to get it to boot from your USB drive. If it has a DVD drive, that would be great: you can boot from a DVD then. You will need to d-l a copy of the OS of your choice and then install it on the USB or DVD as an .iso file: it cannot be merely copied.

Hopefully, if you need to get into the BIOS it will be in English!

If you still prefer Win 7, just stick in the disc and reboot the machine: you should need to worry about Ubuntu being on there now.

---

### Post by oldfred on 2017-05-21
If OP wants further suggestions, best to know details of system.
Brand/model/video card/chip, amount of RAM etc.

A used PC can be just a few years old and Windows 8 with UEFI hardware was released in Oct 2012. For those just about any system can be installed and it is up to the user on what he likes. Note that the WannaCry virus was mostly Windows 7 that were not updated.

But some are lightweight systems or very old BIOS based systems with 2GB of RAM or less. Then lighter weight operating systems are better choices.

But on my 2006 laptop Core2 Duo with only 1.5GB of RAM, I originally ran 32 bit and it came with XP. But installed 12.04 Ubuntu 64bit, but used fallback or the older Gnome panel as the lighter weight gui. Unity was just too slow and not really usable. 
Just to test I installed 16.04 64 bit and Unity was usable, very surprised, just not a fan of Unity.
With only 1.5GB of RAM I could only load one larger app and a couple of smaller apps before it started using swap and got slow. But that was my normal way to work, few apps, few tabs so not normally using a lot of resources. Those that want everything open all the time, do need more RAM.

---

### Post by jstar1 on 2017-05-21
I am trying to figure things out - it's like greek. Totally. Ack. And am in the boonies with no computer teckies around. Will try afresh in the a.m. and post results. Thank you all for assisting.

---

### Post by jstar1 on 2017-05-22
Hi - Dell Optiplex 760

[h=2][/h]                 
[LIST]
[*]                                                                                                  Per Processor Size                                                             
                                                                                                                                          6 MB                                                                                                 

[*]                                                                                                  Installed Size                                                             
                                                                                                                                          6 MB                                                                                                 
[/LIST]
[h=2]RAM[/h]                 
[LIST]
[*]                                                                                                  Memory Speed                                                             
                                                                                                                                          800 MHz                                                                                                 

[*]                                                                                                  Technology                                                             
                                                                                                                                          DDR2 SDRAM                                                                                                 

[*]                                                                                                  Installed Size                                                             
                                                                                                                                          2 GB                                                                                                 
[/LIST]
[h=2]Storage[/h]                 
[LIST]
[*]                                                                                                  Interface Type                                                             
                                                                                                                                          Serial ATA-300                                                                                                 
[/LIST]
[h=2]Memory[/h]                 
[LIST]
[*]                                                                                                  Max Supported Size                                                             
                                                                                                                                          8 GB                                                                                                 

[*]                                                                                                  Form Factor                                                             
                                                                                                                                          DIMM 240-pin                                                                                                 
[/LIST]
[h=2]Hard Drive[/h]                 
[LIST]
[*]                                                                                                  Spindle Speed                                                             
                                                                                                                                          7200 rpm                                                                                                 

[*]                                                                                                  Installed Qty                                                             
                                                                                                                                          1                                                                                                 
[/LIST]
[h=2]Storage Controller[/h]                 
[LIST]
[*]                                                                                                  Interface Type                                                             
                                                                                                                                          Serial ATA-300                                                                                                 

[*]                                                                                                  Type                                                             
                                                                                                                                          Serial ATA                                                                                                 

[*]                                                                                                  Installed Qty                                                             
                                                                                                                                          1                                                                                                 
[/LIST]
[h=2]Processor[/h]                 
[LIST]
[*]                                                                                                  Installed Qty                                                             
                                                                                                                                          1                                                                                                 

[*]                                                                                                  Max Supported Qty                                                             
                                                                                                                                          1                                                                                                 

[*]                                                                                                  Type                                                             
                                                                                                                                          Core 2 Duo                                                                                                 

[*]                                                                                                  Processor Number                                                             
                                                                                                                                          E8400                                                                                                 

[*]                                                                                                  Manufacturer                                                             
                                                                                                                                          Intel                                                                                                 

[*]                                                                                                  Clock Speed                                                             
                                                                                                                                          3 GHz                                                                                                 
[/LIST]
[h=2]Header[/h]                 
[LIST]
[*]                                                                                                  Product Line                                                             
                                                                                                                                          Dell OptiPlex                                                                                                 

[*]                                                                                                  Model                                                             
                                                                                                                                          760                                                                                                 

[*]                                                                                                  Packaged Quantity                                                             
                                                                                                                                          1                                                                                                 

[*]                                                                                                  Compatibility                                                             
                                                                                                                                          PC                                                                                                 
[/LIST]

---

### Post by mastablasta on 2017-05-22
Ubuntu or Kubuntu (looks more like Windows) should run fine. Xubuntu will run faster than the other two (it uses less ram, and has an overall lighter desktop).

Windows 7 will run good as well. if you want widnows, use widnows install disk, reformat the drive to NTFS and install the WIndows 7 os on it.

you can also reinstall Ubuntu (or other versions) if you want. they are free to download, and easy to install if you use the erase disk and install ubuntu option. you would mostly be clicking the continue button. here is how install looks like: [https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

you might benefit from upgrading ram to at least 4 GB, but it all depends what you want to do on the PC.

Windows 7 is supported until 2019, Ubuntu 16.04 LTS (Long Term Support) is supported until 2021, next year 18.04 LTS comes out which will be supported until 2023... And older 14.04 LTS is supported (like windows 7) until 2019.

install and use what works best for you.

---

### Post by jstar1 on 2017-05-22
Thank you. If only I knew Linux. It's not so simple to pick up and really you need to know it to get the full enjoyment out of Ubuntu. What I've been seeing in the few hours I've been using it is that it's nifty and sophisticated. I was able to change the language, in the end it was a matter of rebooting. Will be considering the Windows only because it's more familiar and time is of essence so have to take this into consideration. Good tip on the NFTS hopefully things will go smoother. Will definitely be keeping Ubuntu as a go-to if only to pick up some new skills. :)

---

### Post by joey. on 2017-05-23
Hey I recently got a Dell optiplex here & Ubuntu ran fine when I installed it. Programs loaded pretty fast on 64bit Ubuntu

Edit: 
You should be able to hold down shift after bios screen & change password from shell for a user account only need the users name.

---

