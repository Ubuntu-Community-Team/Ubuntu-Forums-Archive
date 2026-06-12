---
title: "Total Dumbfound on Installing to Harddrive"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by benjamin6 on 2013-08-29
I'm sure this is very probably already something addressed on the forum, but my light grasp of deeper computer terminology makes it difficult for me to word this precisely, so I haven't been able to find an appropriate thread. 

After being frustrated with probable hardware conflicts on my Toshiba laptop with Precise Puppy Linux, I've decided to try out Ubuntu on a friend's recommendation. With some out of the way instructions, I managed to make a bootable USB drive by utilizing Grub4dos to make the .iso file bootable without extracting it. 

It boots up just fine, but I've been unable to install it to my harddrive. If I let the prompts go on their own accord, it wants to install on my USB stick by default. If I go into the parition settings to select it to install on my harddrive, it'll say something like "Can't find root directory" (or something) and won't be able to do it. 

Do I need to tweak the settings of the parition? It's ext2 and has lots of free space; only Puppy Precise is on it, with little other data files. Do I need to do something else like actually install it to the USB stick before I can then install it to my harddrive? 

I ask here since my first attempt at installation, even on just the USB, was monstrously slow, so I was totally unsure if it was even working. Secondarily, I don't think I can judge Ubuntu justly unless it's on my hardware, for all software like that is just going to drag in speed if it's on a slow USB stick, no? During one of my installs I did a forced shutdown due to it becoming so unresponsive. 

Any help towards me joining the arms of the brethren is much appreciate! (Or a simple URL to the thread my dum-dum mental computer vocabulary couldn't type out and find.)

-Benjamin

---

### Post by Petro Dawg on 2013-08-29
Lets start with a couple questions to make sure everyone is on the same page.

What happens if you remove the USB and let the computer start up normally without it?  Does the operating system on the hard-drive boot?  What is the current operating system?

Are you trying to do a dual-boot, or full Ubuntu only install on the hard-drive?

---

### Post by Jonathan Precise on 2013-08-29
benjamin6, Welcome to the forums!

I do not know much about grub4dos (I think that's only for windows). However I do know that you can burn a CD of Lubuntu (since you are using puppy linux, I'm assuming you installed it in older hardware. If you have newer hardware, I recommend plain Ubuntu). Once burned, reboot with the CD inside, and Lubuntu will start. Choose install Lubuntu, then choose "Erase Puppy Linux and Install Lubuntu", or "Erase Ubuntu 12.04 and install Lubuntu 13.04" (**Warning: This will erase ****_ALL YOUR DATA IN PUPPY LINUX!!!!!!!_** To not loose data, backup you important files, documents, etc.).

Note: Lubuntu looks different that Ubuntu (Ubuntu uses Unity, whereas Lubuntu uses LXDE. If you don't understand this part, don't worry! You don't have to!:))

---

### Post by benjamin6 on 2013-08-29
For the first questions:

I haven'ts tried removing the USB stick. If I do nothing at the BIOs screen, it automatically boots Precise Puppy Linux, my current operating system. To get Ubuntu to boot I have to hit F12 and choose to boot from my USB. It boots up just fine. 

As for Lubuntu, why that version? Oh, and Grub4dos is a boot tool packaged with Puppy Linux. If I'm correct, it allows you to create a special type of boot file on a drive that will tell the computer to boot the .iso on the device. In my case, I used the tool so that I could boot directly from the .iso file without having to do any special extraction, such as going through Unetbootin.

For the present, I want to dual-boot with Puppy Linux. I'm not sure yet if I want to stick with Ubuntu since I haven't had the chance to see what kind of power it would unleash from my hardware. It's a moderately older Toshiba laptop, though not too much since it came with MS Vista factory installed, to give an idea of its general production period.

---

### Post by BBQdave on 2013-08-29
> **benjamin6 said:**
> I want to dual-boot with Puppy Linux.

Perhaps I misunderstand...

Puppy Linux, you run from a usb stick and save work to another drive or open space on the hard drive of the machine - Puppy is plugged into. You can custom create your own Puppy USB stick with the applications you want - so each time you boot Puppy Linux USB stick, you do not have to reinstall applications you want. More info on that, you can gain from Puppy Linux site. Usually Puppy Linux is not installed to hardware - at least, that is not Puppy's use.

If you want to dual boot Ubuntu Unity and Vista, I would burn an ISO or follow the Ubuntu instructions for ISO on an USB Stick. Boot up Live Ubuntu ISO and test your hardware, if things are working OK, then you install. The partitioning set up of the Ubuntu install will help you keep VISTA and make space for Ubuntu.

With any install, [COLOR=#ff0000]**Please back up your data to a separate drive**[/COLOR] :)

---

### Post by Petro Dawg on 2013-08-29
I've had a lot of luck with creating good bootable USBs from ISO images with [UNetbootin]("http://unetbootin.sourceforge.net/"),  I would try using it before trying to configure a grub file with Grub4Dos.  Or just burn an ISO image to a CD and boot from that directly as previously suggested.  I have a feeling you issue stems from a problem with your grub configuration (my best guess anyway).

Also, the big determining factor on which 'buntu to use is dependent on how much RAM you have.

If you are running 512M - 1 Gig, I would suggest installing Lubuntu, if 1 to 2 Gig Xubuntu, and 2Gig+ you can probably use straight Ubuntu.  I

I run Ubuntu12.04(2D) on a Pentium 4 (2.8GHz) with 2G RAM nearly flawlessly.  I have run Xubuntu 12.10 before and I did like that a lot as well.

I personally keep SlackoPuppy 5.5 with me at all times on a keychain USB (also created with UNetbootin). I would suggest keeping a full install of 'buntu on your hard-drive, and using a bootable USB of Puppy if and when its needed (especially since you are having compatibility issues with puppy anyway).

---

### Post by Petro Dawg on 2013-08-29
> **BBQdave said:**
> Perhaps I misunderstand...

Puppy Linux, you run from a usb stick and save work to another drive or open space on the hard drive of the machine - Puppy is plugged into. You can custom create your own Puppy USB stick with the applications you want - so each time you boot Puppy Linux USB stick, you do not have to reinstall applications you want. More info on that, you can gain from Puppy Linux site. Usually Puppy Linux is not installed to hardware - at least, that is not Puppy's use.

If you want to dual boot Ubuntu Unity and Vista, I would burn an ISO or follow the Ubuntu instructions for ISO on an USB Stick. Boot up Live Ubuntu ISO and test your hardware, if things are working OK, then you install. The partitioning set up of the Ubuntu install will help you keep VISTA and make space for Ubuntu.

With any install, [COLOR=#ff0000]**Please back up your data to a separate drive**[/COLOR] :)

The newer Slacko and Precise Puppy Linux distros actually make pretty good stand alone full installations.  Yes, Puppy was originally intended to be more of a "rescue" option than a full install, but now they are not bad on their own (not to mention lightning fast). Installing updates has gotten much easier recently as well.

Running Puppy from USB as your **primary** OS is not a great idea, while Puppy takes measures to limit the read/write cycles, you still need to be worried about eventually "wearing out" the stick.  Also the save file size from a live session of Puppy is suggested not to exceed 2 GIG, so if you need more space, a hard-drive install is really the way to go.

---

### Post by 3rdalbum on 2013-08-30
"No Root Filesystem Specified" means that you haven't told Ubuntu where to be installed.

Select an empty partition to install Ubuntu to. Click Edit or Properties or whatever that button is called. Under the Mount Point pop-up menu, choose /

Click Ok and then Forward. The installation will begin.

---

### Post by Jonathan Precise on 2013-08-30
> **benjamin6 said:**
> For the present, I want to dual-boot with Puppy Linux. I'm not sure yet if I want to stick with Ubuntu since I haven't had the chance to see what kind of power it would unleash from my hardware. It's a moderately older Toshiba laptop, though not too much since it came with MS Vista factory installed, to give an idea of its general production period.

I have not had any luck with UNetBooting before (my computer go stuck in a black screen). So just burn the CD/DVD. Then select "Try Lubuntu". Once you have taken a look around and familiarized yourself with it, Double-click on "Install Lubuntu" (a desktop icon). If you want, you can choose "Install alongside Puppy Linux", or "Install alongside Ubuntu 12.04" (In some cases, when an OS is based on ubuntu, it just lists ubuntu. This is normal, as Precise puppy is based on Ubuntu 12.04.). If it is so good, that you decide to replace Puppy Linux with Lubuntu, then choose "Erase Puppy Linux and Install", or "Erase Ubuntu 12.04 and Install".

Edit: If Windows Vista was/is fast for you, you can use Ubuntu. If it was slow, then use Lubuntu.

Edit 2: If you still have Windows Vista, and you would like to conserve it, **_DO NOT CHOOSE "ERASE EVERYTHING AND INSTALL", OR "ERASE WINDOWS VISTA AND INSTALL"!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!_** If you no longer have Windows, then you can choose "****Erase everything and install". If you no longer want windows, choose "Erase Windows and install", or, if you want to _**eliminate both Vista and Puppy**_, choose "Erase everything and install"

---

### Post by benjamin6 on 2013-08-30
There's some confusion going on. 

I'm not running Puppy Precise from a USB stick. It's fully installed on my hardware as its sole OS. MS Vista ran so tremendously slow that it was useless, so I formatted the drive. 

I can get Ubuntu up and running from my USB stick just fine. It runs slow, I think, because it's not in my hardware. I want to install it so that it coexists with Puppy, meaning so that it doesn't format the drive. I'm not sure if I want to stick with Ubuntu yet or check out this "Lubuntu"; I think the only fair way to see is to install it on the hardware.

However, if I click Install Ubuntu and don't select a drive, it does it on the USB stick it's running from automatically. If I pull up the options where I choose which parition to install it on, it won't go through with doing it on the hardware drive Puppy is on. It's say "Root Directory Not Found/Defined/SomethingSomething."

---

### Post by 3rdalbum on 2013-08-31
> **benjamin6 said:**
> 
However, if I click Install Ubuntu and don't select a drive, it does it on the USB stick it's running from automatically. If I pull up the options where I choose which parition to install it on, it won't go through with doing it on the hardware drive Puppy is on. It's say "Root Directory Not Found/Defined/SomethingSomething."

Giving an exact error message is a lot easier for helpers to decipher. Please help those who are trying to help you.

"No Root Filesystem Specified" means that you haven't told Ubuntu where to be installed. I believe this is the error message you are describing?

Select an **empty** partition to install Ubuntu to (or downsize the Puppy partition downwards and create a new Ext4 partition in the newly-freed space). Click Edit or Properties or whatever that button is called. Under the Mount Point pop-up menu, choose /

Click Ok and then Forward. The installation will begin.

---

### Post by benjamin6 on 2013-08-31
Sorry about that. I was being lazy, I admit, since it was cumbersome it run Ubuntu as it is right now. Without a hardware install, it boots annoyingly, lags a lot, and usually requires me to do a forced shutdown. I've been dancing around that since I didn't want to go through all that drag for a quick error message read. 

Anyhow, so if I need a blank partition, I suppose it needs to be formatted a particular way? The one with Puppy on it is ext2, so Ubuntu prefers ext4? 

I'll try out Lubuntu. I'm using the Grub4dos method since Unetbootin won't work on my version of Puppy, though I did install Puppy onto a USB stick through that means within Vista (which is now gone). 

After that, I'll put Puppy into RAM-only mode, partition the drive further, and see what I can do. 

Thanks all for the advice so far.

---

### Post by Quackers on 2013-08-31
Are you now in an Ubuntu live cd/usb desktop? 
If so, run gparted and state your current partition layout as described by gparted (or enclose a screenshot).

---

### Post by Jonathan Precise on 2013-08-31
> **benjamin6 said:**
> There's some confusion going on. 

I'm not running Puppy Precise from a USB stick. It's fully installed on my hardware as its sole OS. MS Vista ran so tremendously slow that it was useless, so I formatted the drive. 

I can get Ubuntu up and running from my USB stick just fine. It runs slow, I think, because it's not in my hardware. I want to install it so that it coexists with Puppy, meaning so that it doesn't format the drive. I'm not sure if I want to stick with Ubuntu yet or check out this "Lubuntu"; I think the only fair way to see is to install it on the hardware.

However, if I click Install Ubuntu and don't select a drive, it does it on the USB stick it's running from automatically. If I pull up the options where I choose which parition to install it on, it won't go through with doing it on the hardware drive Puppy is on. It's say "Root Directory Not Found/Defined/SomethingSomething."

Run Lubuntu, and in the installation options, choose "Install alongside Puppy Linux", or "Install alongside Ubuntu 12.04". This is an automated installation, that only asks how much to re-size the existing partition. Drag the sliders according to what you prefer (remember that Lubuntu will need at least 3 to 5 GB for a full install). And you're done!!!

---

### Post by f-jack on 2013-08-31
You should use unetbootin to make the flash drive Ive had issues before using anyother way as ive installed ubuntu on 7 or so computers and i always get issues

---

### Post by benjamin6 on 2013-09-05
Sorry about the lack of further update. I've been procrastinating since Puppy Precise's vices have been tolerable. Today, however, I was just about to try to install Ubuntu and ran into another obstacle. 

I found out that I can repartition the drive while I'm using the OS. Because I thought Precise was all I would need, I settled for just one drive, and can't divide it up so that I can make a suitable drive for Ubuntu. 

On the Puppy forum, they told me to insert a bit of code before the OS booted up in order to make it run in RAM only, which would allow me to do things to the drives I otherwise wouldn't be able to, but apparently I can't do that now that I'm not booting from a USB. 

Thus, how can I more efficiently partition the drive? As of current, I think the problem with Ubuntu -- if I'm reading the above posts right -- is that I need an ext4 formatted drive for it to work in, and I need to partition a special drive for it, for Puppy is formatted to ext2. 

I know I could do a workaround such as backing up my files, reinstalling Puppy onto a USB, and then RAM booting it so that I could format and repartition the drives, but is there a more efficient and less Rube Goldberg workaround?

---

### Post by Jonathan Precise on 2013-09-05
> **benjamin6 said:**
> Sorry about the lack of further update. I've been procrastinating since Puppy Precise's vices have been tolerable. Today, however, I was just about to try to install Ubuntu and ran into another obstacle. 

I found out that I can repartition the drive while I'm using the OS. Because I thought Precise was all I would need, I settled for just one drive, and can't divide it up so that I can make a suitable drive for Ubuntu. 

On the Puppy forum, they told me to insert a bit of code before the OS booted up in order to make it run in RAM only, which would allow me to do things to the drives I otherwise wouldn't be able to, but apparently I can't do that now that I'm not booting from a USB. 

Thus, how can I more efficiently partition the drive? As of current, I think the problem with Ubuntu -- if I'm reading the above posts right -- is that I need an ext4 formatted drive for it to work in, and I need to partition a special drive for it, for Puppy is formatted to ext2. 

I know I could do a workaround such as backing up my files, reinstalling Puppy onto a USB, and then RAM booting it so that I could format and repartition the drives, but is there a more efficient and less Rube Goldberg workaround?

As with Lubuntu, Gparted should be included. Run it, and check for a swap partition. Right-click it, and select "swap-off". Exit, then run the Lubuntu installer. Follow my other directions from there.

---

### Post by benjamin6 on 2013-09-10
Awrighty, I continue being a newb. 

With a bit of stumbling, I managed to make my USB bootable for Lubuntu, booted it up, and used GParted to make an empty partition with the ext4 formatting. However, upon requesting it to install the same problem occurs. It says "No root file system defined." 

Where to from here? Ah, but at the finish line!

---

### Post by benjamin6 on 2013-09-12
I finally got it! All I had to do was edit the partition I wanted to install in and make "/" the root file system. However, that's still a bit of babbly gook to me. What does "/" mean? 

Anyhow, Lubuntu is looking good to me so far! It's not as fast as Puppy Precise, but the experience seems to be steadier and not susceptible to lag and crashes, so I'm liking it better overall. 

Hopefully now I can operating this way for the long-run with my computer. I wish I left Microsoft behind years ago.

---

### Post by Jonathan Precise on 2013-09-12
> **benjamin6 said:**
> What does "/" mean?

/ is the uppermost folder in the hard drive (called the root folder). Afterwards comes /home, /usr, /etc ... where home, usr, and etc are sub-folders of /.

Don't worry if you don't understand;)!

---

