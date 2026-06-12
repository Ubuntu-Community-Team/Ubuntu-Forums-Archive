---
title: "Recommend Inexpensive Hardware for trying Linux"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by shai3 on 2013-11-15
I'm a longtime Mac user ready to give Linux a chance. I'm a Drupal developer that uses Linux servers every day and I'm comfortable at the command line. I use MacOS X Terminal a lot. But controlling a server is different than using it as a desktop. But I'm ready to give it a try.

I'm also testing on behalf of the local high school which can no longer afford Macs. They are ready to jump in to Windows and I'm yelling and screaming "No! Linux/Ubuntu is what you want." But when people ask me if I've ever used it and I sheepishly say "No" they role their eyes. I need some cred here.

Yes, I  know I can try out Linux on my Mac but I don't want to. This Linux adventure is enough of a distraction from work as it is and I don't want to duel boot my work computer or otherwise fuss with a work environment that is working OK.

If I ultimately make the move to Linux, I'll get a desktop and I'll get one with decent specs. But in testing mode, I want to see, for the school, if the cheepo ones can pull their weight, and I don't want to lay down a lot of cash if I decide to stick with my Mac for work.

So do advise on hardware. What do you think of this:
[http://www.amazon.com/Acer-C710-2847-Chromebook-5400RPM-USB3-0/dp/B00AG0BLWU/](http://www.amazon.com/Acer-C710-2847-Chromebook-5400RPM-USB3-0/dp/B00AG0BLWU/)

It's a Chromebook; I'd wipe the chrome and install Linux. I've read about Crouton, but I don't like the lack of security. Other ideas?

Shai

---

### Post by ian-weisser on 2013-11-15
Recommended hardware: A USB stick.

Boot your Mac from the USB without any change to OSX, and no risk: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
The instructions tell you how to boot from the USB when it's ready.
Simply use it for the live environment, don't install onto your Mac's hard drive.

---

### Post by Eleutharios on 2013-11-15
You can always run Ubuntu from a live USB drive (Not sure if you're aware of this already, so sorry if you are). That would allow you to get a feeling for it without messing up your current setup. Go to [http://www.pendrivelinux.com](http://www.pendrivelinux.com) and get the Universal USB Installer. This will let you create a bootable USB drive that you can use to either install Ubuntu or just run it like a normal OS from the drive. It may not be the ideal solution for testing performance, but you should be able to get a hang of the using Ubuntu just fine and it's a lot cheaper than buying a new computer! As for performance, any modern PC should be able to run it just fine. I recently installed Ubuntu on my old 2008 Toshiba and it ran much faster than Windows 7. Just my two cents, but I'd give this a try before buying any new hardware.

---

### Post by tgalati4 on 2013-11-15
Go through the school district's computer trash pile--you can probably piece together several machines to test different distros on.

---

### Post by shai3 on 2013-11-15
Thanks everyone! Great ideas! I've got an unused partition on an USB2 external HDD with plenty of space. I think I'll use that to get started.

---

### Post by 1clue on 2013-11-15
I don't like any of those options.  The USB stick will be horribly slow, and the cheap hardware is cheap.  You're getting a deal on the operating system, don't skimp on hardware or it will just be obsolete that much faster.  ***Edit:**  If a school that's scrapped for money threw out a computer, there's probably a good reason for that.  A full-scale Ubuntu is not really any faster than Windows would be, and depending on special effects and any other junk you put on it it could be considerably slower.*

I'd recommend a virtual machine on your mac.  I use Parallels on my mac, but VMware has free software for the mac I understand.  Either one will let you install a VM on hardware you consider to be current, give it significant RAM and disk space and go full screen so it's pretty much like running it on your mac, only you can switch to your mac apps and back without rebooting.

---

### Post by mörgæs on 2013-11-16
+1 for finding some discarded (or cheap used) hardware, Install Lubuntu 13.10 and get some experience. New hardware is likely overkill, and support is often best for semi-old gear (say 4-8 years). 

I assume you don't need fast gaming-class graphics.

---

### Post by mörgæs on 2013-11-16
> **1clue said:**
>  *If a school that's scrapped for money threw out a computer, there's probably a good reason for that.*

Yes, the reason is usually a Windows install falling apart and grinding to a halt, not hardware itself.

---

### Post by Lars Noodén on 2013-11-16
If you draw up any plans to discuss, you might look at pricing RaspberryPi thin clients running Edubuntu, Skolelinux, K12LTSP, or LTSP.  Even if you go with the old hardware, it can be interesting to look at what it will cost when they wear out.

---

### Post by coldraven on 2013-11-16
> **shai3 said:**
> Thanks everyone! Great ideas! I've got an unused partition on an USB2 external HDD with plenty of space. I think I'll use that to get started.

I would not recommend using that, you may lose any data that is on the HDD.
Do you have any SD cards lying around? I use Unetbootin to make a 1GB card bootable and it works fine for trying or installing Ubuntu.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by angelsimon on 2013-11-16
If you want to try Linux, I recommend you using a Virtual Machine. You can try VirtualBox or VMware. So you can initialize your "Linux PC" from your original OS (Windows, Mac, other Linux OS, etc).
You access your second OS from a file using a program. So, there is no risk of ruin your primary OS.

Hope this helps

PS: You can also buy a Raspberry Pi that works with Debian or others kind of Linux distros. They're very inexpensive.

---

### Post by BBQdave on 2013-11-16
A side thought, depending on the age of the Macs, the school might be able to load FOSS applications. They could save money with an application such as Libre Office. Depending on the students' needs, and if the Macs are still supported.

A lot of business that are resetting company hardware, often are willing to donate hardware. I have helped a few non-profit orgs with 2 year old hardware from business's retooling.

Once you have tested and drawn up a plan for OS and hardware needed, the school could have a Mac *bake sale* and coupled with local community support (from individuals and business's), funds could be raised for hardware and implementation of the new system.

Additional thought: You know, I do not think you have a bad idea with Chrome books. The school my daughter attends, uses Google services for school information and communication. I do not think you could get less expensive hardware, than a Chrome book. If you could set up an in school back up for data (saving the expense of Google data storage). You would need to research applications available (and appropriate) for students. Google may even have inexpensive school services, along with the purchases of student Chrome books.

---

### Post by SeijiSensei on 2013-11-16
I've been playing with a Raspberry Pi running [Raspbian]("http://www.raspbian.org/"), the Debian derivative for the Pi.  It's okay but runs pretty slowly since the Pi only has an ARM processor with 512MB of memory.  I'm actually thinking about using the Pi as a server rather than a desktop client.  I've tried it out with sharing files over NFS from a large external hard drive, and it performed well, even streaming video over wifi to a computer connected to my TV.

Linux runs fine on older hardware if you pick the right distribution.  Even Kubuntu runs on the now eight-year-old Inspiron laptop my daughter once used in high school.  I agree with the suggestion of running Lubuntu for a start.  I'm using it to write this on an ASUS Eeepc 1201n with a dual-core Atom and 2 GB of memory.  It's a bit slow at times, but using the proprietary NVIDIA driver with the Ion adapter in this machine makes a big difference when playing videos encoded in H.264.

If the school cannot make a computer available, I'd look on ebay for something like [this](http://www.ebay.com/itm/GENERIC-COMPUTER-PENTIUM-DUAL-CORE-E5700-3-00-GHZ-2-GB-CDRW-Used-Free-Shipping-/131042106901?pt=Desktop_PCs&hash=item1e82b7de15).  It's much more powerful than a Pi and, at fifty bucks or so, cheaper than assembling a [Pi]("http://www.amazon.com/gp/product/B009SQQF9C/") once you add in a [memory card]("http://www.amazon.com/gp/product/B003WIRFD2/1"), [wifi adaptor]("http://www.amazon.com/gp/product/B003MTTJOY/"), [external USB hard drive]("http://www.amazon.com/gp/product/B00812F7O8/"), and a [case]("http://www.amazon.com/gp/product/B00A42HTLC/").  All together that ran me about $96 at Amazon. I've since bought a USB hub to handle all those devices.  One nice thing about the Pi is that includes a video adapter that supports high-def over HDMI.

---

### Post by Iowan on 2013-11-16
> **SeijiSensei said:**
> I've been playing with a Raspberry Pi running [Raspbian]("http://www.raspbian.org/"), the Debian derivative for the Pi.  It's okay but runs pretty slowly since the Pi only has 512MB of memory.The BeagleBone Black is a similar device. It has a faster processor, onboard storage, and an Ubuntu version available (comes with Angstrom) - but the 512M RAM will still limit it's performance. I haven't had a chance to get acquainted with mine, yet.

---

### Post by heir4c on 2013-11-16
You can also use client pc's like this one: [http://www.aliexpress.com/item/MINI-PC-thin-client-XCY-L-19X-AMD-E350-MINI-PC-DESKTOP-COMPUTER-Ultra-NetTop-Graphics/1363858089.html](http://www.aliexpress.com/item/MINI-PC-thin-client-XCY-L-19X-AMD-E350-MINI-PC-DESKTOP-COMPUTER-Ultra-NetTop-Graphics/1363858089.html)

(I use at the moment a AMD APU E-350 on a (secondhand) Asus motherboard E35M1-M (without a extra graphics card and 2 old Laptop HD 5200rpm and 4GB RAM) and have Ubuntu 14.04 on it. It works really fine on that. Even a movie run smooth on this 'thing'. It's not a client PC but a self build with secondhand hardware.)

The client PC's are cheap and you can connect the old monitors on it.

---

### Post by squakie on 2013-11-16
I don't "plug" products very oftern, but rather than getting a Chromebook for that much money, why not just look at something in a bare-bone kit, like [this one]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=8529750&csid=_61") from Tigerdirect.  Case, cpu, memory, disk - well pretty much everything except a mouse, keyboard and perhaps some form of monitor (if the mb has hdmi you can just use a hdtv).  Very much more than enough to try things out on - you could add more memory later, etc., as you deem needed.  You'll probably want an optical drive as well - Micro Center has some as low as $15.  

Also, don't be afraid to look at refurbished computers from places like TigerDirect, Micro Center, etc..  Sometimes you can buy more than enough hardware for what you want to try very inexpensively.

---

### Post by PJs Ronin on 2013-11-17
Try your local mom and pop computer repair store/garage/loft.   They often have old hardware that can make a viable system for pretty much pennies.

---

### Post by OrangeCrate on 2013-11-17
I second the advice to use USB drives to test distros. They're cheap and convenient, since you can use 4 or 8 GB sticks. I've used them many times to download and play with other distributions.

---

### Post by shai3 on 2013-11-17
I ended up downloading and installing VMWare 6 for Mac as a 30-day trial. I wasn't sure if the free VMWare Player would be enough. For my purposes now the 30-day trial is great.

VMWare has been fantastic. I downloaded Ubuntu 13.10 on my own. Then in VMWare I selected that file during the create machine process and used their "Easy Install." Wifi worked instantly. Bluetooth works flawlessly. Even my hated "Magic Mouse" (which I hate because of its unreliable right-click); it works too. That mouse, via Mac system settings, has its right click set to the left click, and the virtual machine knows that too!

Apparently Ubuntu 13.10 has a broken clock; I was fussing with that when an update pop-up message appeared. I updated Ubuntu and that was fixed.

All is not wonderful... I'm going to post a write-up in a different thread.

---

### Post by mörgæs on 2013-11-17
Please mark the thread 'solved', even though there might be other problems.

---

### Post by shai3 on 2013-11-17
I'd be happy to mark this thread as "solved ". But I can't find where to do that. True I'm using an iPhone right now. But I did click on the advanced section and did not do a quick reply. But still can't find a way to market as solved.

---

### Post by philinux on 2013-11-17
Top of the page Thread Tools.

---

### Post by 1clue on 2013-11-17
For the record, VMware Player is fine for normal use.

---

