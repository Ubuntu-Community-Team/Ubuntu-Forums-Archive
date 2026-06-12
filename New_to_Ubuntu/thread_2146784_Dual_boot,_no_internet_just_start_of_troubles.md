---
title: "Dual boot, no internet just start of troubles"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by blueboxer on 2013-05-19
Long ago a helpful gentlemen put Ubuntu 8.04 in some surplus space on my desktop computer. He set it up to dual boot, the other partitions being Windows XP. I have toyed with it since but done  nothing serious. I have just read that I'm overdue to upgrade - and maybe get serious.

But, several months ago I got a WiFi home hotspot to untangle the wires of five active household computers. Only later did I discover that the wireless adapter I got for the XP portion of my Ubuntu computer didn't work with Linux. So I bought a Netis WF-2120 labelled as working with Linux and installed it successfully in XP, but Ubuntu didn't notice it was there. And the driver CD didn't have Linux-specific instructions or a Linux-specific driver. I emailed the manufacturer and they sent me the code to enter. That's when I discovered that my original assistant had set things up so I couldn't meddle - there was no way to access the command prompt.

Honestly, no matter how far-fetched it sounds, this is the honest straight goods. And I need help.

In search of a driver, I downloaded Ubuntu 10.04 and 12.04 and burned them to live CDs and ran them to see if they might find the wireless. They didn't. But I am going to need them, I suspect. I got the MakeUseOf ebook on Ubuntu to guide me in installing the new versions. But the first thing 10.04 wanted to do (I am likely misinterpreting this, but I don't plan to trash a working computer even if it is half XP) was, it said, to reformat and repartition my computer - and the XP part is not expendable. Obviously the 8.04 obsolete version of Ubuntu is, and there are no personal records or settings in it - as mentioned, they're beyond my access.

So - I can't get Ubuntu on the internet to upgrade it until I can give it a driver for the computer's wireless adapter, and I can't get a command prompt to do that. I don't dare risk installing on the 8.04-->10.04-->12.04 route for fear it repartitions my whole hard disc and kills XP. And as is likely obvious, I don't want to use Ubuntu to learn to speak Geek, I want to see if I can use it as a productivity tool.

I am in Toronto, Canada but have no contact with any local group - I am "frail elderly" and constrained in my travel options, but have free time to talk, exchange computer messages, etc.

Advice and assistance would be very welcome.

---

### Post by ibjsb4 on 2013-05-19
First, 12.04 can be resource demanding.  Is your computer up to it?  Whats your computer specs?

---

### Post by rlcbm on 2013-05-19
you might need ndsiwrapper

---

### Post by blueboxer on 2013-05-19
Please gentlemen, this is beginner space. What is ndiswrapper and what do I do with it? Remember I c\n't get a command line to come up.
The computer is a dual core, couple of megs RAM, 160GB HD partitioned 4 x 28 GB(FAT max), balance ext3 for Ubuntu.

---

### Post by wildmanne39 on 2013-05-19
If you are still using 8.04 first use windows to download an updated ubuntu version you can do that by clicking on the ubuntu community tab at the top of the forum, then install it, I recommend lubuntu for those specs.

Then click on the report button when you have it installed and ask for this thread to be moved to networking.
Thanks

---

### Post by ibjsb4 on 2013-05-19
You do not want to format the balance ext3.  Leave it as free space and you will be given the option to install to that free space.

---

### Post by fantab on 2013-05-20
> **blueboxer said:**
> 
The computer is a dual core, couple of megs RAM, 160GB HD partitioned 4 x 28 GB(FAT max), balance ext3 for Ubuntu.

Firstly, both 8.04 and 10.04 versions of Ubuntu are 'dead'. They are no longer supported by Ubuntu.

Secondly, if you have RAM less than or equal to 1GB then [LUBUNTU]("http://lubuntu.net/") is your best bet, if less than 2GB then probably [XUBUNTU]("http://xubuntu.org/") is your friend. You must do better than "couple of megs RAM". Look up in XP and you will find exactly how much RAM/Memory you have. Are you willing to upgrade your RAM? If your Mother Board supports more RAM then I suggest you do consider adding a bigger RAM. If your Motherboard is INTEL or wahatever, check their support and see it there are any BIOS Upgrades you can perform. As this will probably solve your 'wireless' issue.

What make is your "dual core" Processor? if its Intel Pentium it may probably support 64bit. Some Pentiums did.

You must provide all the information about your machine to us so that we can guide you in the right direction.

---

### Post by blueboxer on 2013-05-20
Glad to see someone actually read all of my post. As noted I already have live CDs of 10.04 and 12.04 since I read that I needed to do the upgrades one step at a time.
 
The machine has an S-series Gigabyte board with Pentium Dual Core CPU E2160 @ 1.8 mhz (certified Vista capable), 2 meg of RAM, Award BIOS, dual boot XP and Ubuntu, Windows has 128 GB of the hard disc, balance of 32 is Ubuntu. While this is not fashionably humongous, it ought to be adequate for light occasional use. I am not a gamer, have a Win7 machine for entertainment and graphics.

Please note I am not going to run the upgrade until I can confirm that the editions I have will NOT disturb my Windows side in any way (moving partitions, reformatting, etc.) If it is the preferred way to go I can delete the 8.04 installation and leave that partition as free space.

Pleaxse also note that I can't get on the internet AND I do not have a command prompt (and no. clicking on the desktop will not bring it up) And I can't activate the wifi adapter I already have installed and working on the Windows side until I can get a prompt to install the driver.

If I can get away with it the easiest thing for me would to be simply install 10.04 over 8.04 then 12.04 over 10.04, but I gather this isn't possible. I'd like to look at 13.04 but notice that it is not an LTS distribution.

---

### Post by fantab on 2013-05-20
Since you say that your board is "certified vista capable" I will assume that the RAM is 2 gigs (GB) and not "2 meg" as you say. 2 gigs of Memory can run 64bit Ubuntu as your [Processor supports 64bit.]("http://ark.intel.com/products/29739/Intel-Pentium-Processor-E2160-%281M-Cache-1_80-GHz-800-MHz-FSB%29") Go to the Gigabyte website and check if you can upgrade your BIOS to a newer version. You can find out the current version of your BIOS by entering BIOS- Setup.

Secondly, you DON'T have to install 10.04 over your current 8.04 and then install 12.04. You CAN directly install 12.04 from CD. To use your existing 8.04 partition to install 12.04 you have to manually instruct the installer to do so, by chosing the option "SOMETHING ELSE" when you are asked about 'Installation Type'. 

After choosing 'Something Else' option at the subsequent dialog select your Ubuntu partition and click "CHANGE" option. Another dialog will open with additional options; here you will choose to format, from 'Use As' dropdown choose ext4 and choose mountpoint as "/". Continue with install.

If your Wifi adapter is ON then, during installation you will be asked to configure it, you can do so. However, I suggest before you acutually install ubuntu, first "TRY Ubuntu", when the desktop is ready try and establish connection. Perhaps this can help: [http://ubuntuforums.org/archive/index.php/t-2019516.html](http://ubuntuforums.org/archive/index.php/t-2019516.html)
Even if you can't at this stage we can help you with Wifi after installation.

Good Luck....

---

### Post by blueboxer on 2013-05-21
Thank you, Fantab, at least you have given m an assist well beyond the starting line.  Sorry about the megs/gigs bit; I started on an 8-bit, 64K computer for which anything with megs was a distant dream - only big business machines had that. (Yes, I remember 640K memory, and then Bill Gates quote made sense).

I am not going to fuss right now about going to 64-bit even if the board will support it; if I put Ubuntu on my 64-bit new laptop that will be soon enough.

Anyway, I reckon that if push comes to shove, 8.04 is expendable and I can repartition it to free space, then try to avoid accidentally having Ubuntu foul up my Windows partition on the new install.

No doubt I swill run into more trouble and be back shortly, but for the moment thank you for the clues.

---

### Post by valus on 2013-05-21
Do you realy cannot establish a wired internet connection? This will allow you to upgrade Ubuntu and to find a driver for your wireless adapter.

---

