---
title: "Dell mini 9 and ubuntu questions"
date: 2015-08-07
forum: New to Ubuntu
---

### Post by daniel295 on 2015-08-07
Hello to everyone, I once had a Dell mini 9 that I loved but it met his untimely demise when the hard drive died and I lost interest in it. A few weeks ago I won an auction on eBay for a Dell mini 9 for 42.00. Great right? 

But. It was running Linux instead of Windows as the seller stated. From what I hear Linux is amazing but ive never used it and have no idea what to do. I've done some digging and I've found out that I'm running 8.04 hardy and I would like to update to the newest one for more stability and faster performance. How can I do that? I've tried to download chrome but I keep getting errors. 

Any help would greatly be appreciated. Thank you.

---

### Post by dino99 on 2015-08-07
Welcome Daniel,

i've found its specs: [http://www.pcworld.com/product/32155/dell-inspiron-mini-9.html](http://www.pcworld.com/product/32155/dell-inspiron-mini-9.html)

and i see 8 GB storage only, and no much ram; so it will be hard to install the actual ubuntu & the likes.
of course 'hardy' has died long ago so it cant be upgraded. But you can play with it to see that ubuntu is a graphical distro, so its not so different than xp for example.

That said you will have to choose/install one of the lightest distro around: [https://duckduckgo.com/?q=linux+light+distro&ia=about](https://duckduckgo.com/?q=linux+light+distro&ia=about)

---

### Post by TheFu on 2015-08-07
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - Learning Linux. Start by reading the first few links, then jump to the other sections and review the User Guides.

We cannot help with 8.04 or 10.04 releases. Support for both of those ended long ago.  You should install either 14.04 (preferred) or 12.04.  Do NOT install any other release.

Personally, I think you wasted your month.  For a little more, you could have gotten a used netbook with a much better CPU, sligjtly larger screen, more RAM ... 
Also - you need to get Lubuntu for that hardware, NOT stock, default, "Ubuntu." The norma Ubuntu will run very poorly on that hardware, if at all. The GPU is the main issue for the fancier distros.

---

### Post by Geoffrey_Arndt on 2015-08-07
You can get Lubuntu on [Http://www.distrowatch.com](Http://www.distrowatch.com) or at [http://lubuntu.net/](http://lubuntu.net/)

It isn't nearly as polished as Ubuntu or many other versions (distros) of Linux like "Linux Mint - Cinnamon" but it will definitely be more usable on that netbook.  ( 1 GiB ram really limits it to Lubuntu).

---

### Post by Bucky Ball on 2015-08-07
Be aware that 8.04 hasn't had security updates in years so might not be a good idea to spend a lot of time online with it.

As suggested, try Lubuntu 14.04 LTS. It is equally as polished as any other flavour of Ubuntu, just uses a different desktop environment. Sits on exactly the same kernel.

And agree with previous poster: 1Gb RAM limits your options. Can you plop 2Gb in, or 4 if it can handle? You are away then, except for the fact you are going to get only the slimmest of installs on that 8Gb storage. Probably think about an external drive/dongle to keep personal data. ;)

---

### Post by stalkingwolf on 2015-08-07
with 1 gb ram it will run mint 13 . however you will need to add additional drive space.  8 GB just dont leqave enough storage. id add a 64 gb card and use the 8 gb for storage.   I had an asus of that type  and a couple with i gb ram since.  The 9" i put a 32 gb card in and worked fine.  The others all had or have regular HDD's.

---

### Post by daniel295 on 2015-08-07
Thanks for the replies guys. 

I bought this mainly as a Web only kinda of netbook. I have a full desktop that I use for heavy work. 

I think I can upgrade the ram to 2gb. I also can grab a cheap 32gb flash drive as well. 

So should I be doing a clean install of the ubuntu versions you guys mentioned?

---

### Post by PaulW2U on 2015-08-07
> **daniel295 said:**
> So should I be doing a clean install of the ubuntu versions you guys mentioned?

**Definitely** a clean install. Don't waste your time trying to work out how to upgrade from 8.04.

---

### Post by daniel295 on 2015-08-07
Ok question, if I decided to keep the current software I have is there a way to get Google Chrome installed?

---

### Post by TheFu on 2015-08-07
> **daniel295 said:**
> Thanks for the replies guys. 

I bought this mainly as a Web only kinda of netbook. I have a full desktop that I use for heavy work. 

I think I can upgrade the ram to 2gb. I also can grab a cheap 32gb flash drive as well. 

So should I be doing a clean install of the ubuntu versions you guys mentioned?

For a web-only machine, I wouldn't put more than $10 into it. 32G SSD just isn't needed for this purpose. 8G is a little tight, but I'd try it for a month to see if that is an issue or not.  I ran Lubuntu as my desktop for 3 yrs with 10G of space. That same machine is using ... 

```
$ df
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        17G   13G  3.3G  79% /

```
today. ... less than 10G.  Just sayin'.

Actually, for a web-only machine there are better OS choices which take 1000x less storage.  TinyCorePlus, for example.

---

### Post by Vladlenin5000 on 2015-08-07
> **daniel295 said:**
> Ok question, if I decided to keep the current software I have is there a way to get Google Chrome installed?

If by current software you mean hardy then the answer is a huge NO. And - again - using it for anything online is very risky.

---

### Post by daniel295 on 2015-08-07
Well lubuntu it is. Anything I should be aware of? Thinking of downloading it to a USB drive and booting from that and going from there. I should be ok right? 

And thanks for the help so far.

---

### Post by roger_1960 on 2015-08-07
Hi

My vote would be to try chromixium.  Really lightweight desktop with Ubuntu 14.04 behind it. chromixium.org - the 32bit 1.5 release is great and changing from chromium to chrome is documented if you wish to do it.

Yes, boot whatever distro you are trying to a live session from a usb stick and test the hardware works before installing it.  I would not mess about with dual boots as 8.04 really is too old to keep.

---

### Post by daniel295 on 2015-08-07
Live session?

---

### Post by Bucky Ball on 2015-08-07
When you boot lubuntu you will get to a screen of options. One of them will be 'Try Lubuntu'. Try it and you will be at a desktop in a 'live' sessions, as in it is running 'live' from the install media. ;)

How are you going to create the USB? Try this:

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

---

### Post by sudodus on 2015-08-07
If you need more details about USB drives, how to select them, how to install into them and boot from them, see this link and links from it. Unetbootin is one of the tools to recommend.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by TheFu on 2015-08-07
> **Bucky Ball said:**
> When you boot lubuntu you will get to a screen of options. One of them will be 'Try Lubuntu'. Try it and you will be at a desktop in a 'live' sessions, as in it is running 'live' from the install media. ;)

How are you going to create the USB? Try this:

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

If you need to build the install/try USB flash drive from Windows, I've found **yumi** to be the easiest for multi-boot stuff. It is nice to have 1, 2, 5, 10, 20 different Linux ISOs there, ready to boot off a single flash drive. yumi is available at the unetbootin website too.

If you need to build the install/try USB flash drive from Linux (or any Unix), you can just use **dd** to shove the ISO onto any flash drive. It isn't pretty, but you don't need any special tools. It will effectively wipe the flash drive.  The other downside to using dd is it is not multi-boot. Only one ISO at a time.

The tool you use to build a bootable flash drive really isn't that important.  You should also be aware that some flash drives and some PCs just are not compatible for booting. I haven't figured out any way to know if one will work with the other or not. Sometimes new drives don't work, sometimes they do. Sometimes old drives dont' work, sometimes they do. I dunno. Cheap/expensive ... doesn't seem to matter either.

---

### Post by daniel295 on 2015-08-07
Ok so I'm leaning towards the chromium os so can I live session that? Also what's ddt? Sorry for all the questions just want to be sure of everything

---

### Post by Geoffrey_Arndt on 2015-08-07
Or just re-sell it and buy a Chromebook instead.    I know where you can get a lightly used Acer c710 (2gb ram, 16 gib SSd) for $50.00.

---

### Post by oldrocker99 on 2015-08-07
Ubuntu MATE is pretty much as lightweight as Lubuntu, and I like it better. Just my $0.02 worth.

---

### Post by TheFu on 2015-08-07
> **Geoffrey_Arndt said:**
> Or just re-sell it and buy a Chromebook instead.    I know where you can get a lightly used Acer c710 (2gb ram, 16 gib SSd) for $50.00.

I have a C720 - hate it. Wish I would have gotten a laptop with everything the same except with a real keyboard. Chromebook keyboards are missing some really important keys - like home/end/pgup/pgdn  AND the idiot designers put the GD power key where a DELETE key belongs!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I'm really pissed about the missing DEL key. To me, that is worth $50, easily.  Wish I'd have gotten the Dell with everything else equiv - except a 500G HDD, upgradeable RAM and a real keyboard for $80 more.  Cost me about $140 in upgrades to make this chromebook useful as a remote desktop device with very lite perl webapp programming capabilities.

I do love the battery, weight, size of the C720. Don't think I'll ever buy a normal laptop again.

---

### Post by daniel295 on 2015-08-07
Ok I've read about ubuntu mate and I think im going to go that route now. 

So download the image to a USB stick and boot from the USB correct? And from there I can do a live session and see if everything works correctly. Then if pleased with the software I can do a clean install correct? Should I just install over my current software?

---

### Post by Geoffrey_Arndt on 2015-08-07
TheFu . . . I basically use my Chromebook as a casual replacement for a couple tablets I have. (but not as a laptop replacement).  I really like 13-14" lite laptops (ultrabook style).   Seems best of both worlds

Daniel295, Ubuntu Mate sounds like a good plan, and if it doesn't work out, there's always Xubuntu, and/or Lubuntu.  But I agree the Mate desktop is lite enough to run on almost anything (and still has beaucoup functionality).

---

### Post by Bucky Ball on 2015-08-08
Just throwing this in ... choosing an open-source OS is a bit like buying an analogue product: you want after sales service. 

When choosing an OS, make sure there is a reasonably vibrant and friendly support community. The more exotic you go, the less likely it is such a community exists. 

Good luck. :)

---

### Post by gordintoronto on 2015-08-08
Good plan! However, you will have an ongoing struggle with the limited "disk" space. For example, just like Windows, the files downloaded for system updates don't get deleted automatically. (Part of the solution is to run the command: sudo apt-get clean) Chrome, all by itself, has an update about once a month, and it's 50 MB. Adds up over the course of a year.

I would start with Mate 15.04, since that is the first "official" member of the Ubuntu family. (Actually, if it was my computer, I would install Xubuntu 14.04. Different folks make different choices...)

The biggest test for the Live session is to see if the Wi-Fi works.


> **daniel295 said:**
> Ok I've read about ubuntu mate and I think im going to go that route now. 

So download the image to a USB stick and boot from the USB correct? And from there I can do a live session and see if everything works correctly. Then if pleased with the software I can do a clean install correct? Should I just install over my current software?

---

### Post by daniel295 on 2015-08-10
So I've successfully used yumi to get a live session of ubuntu mate. I like it so far but! No wifi. What can I do to correct this?

---

### Post by TheFu on 2015-08-10
> **daniel295 said:**
> No wifi. What can I do to correct this?

That's a little vague. More info please.  Perhaps 
**sudo lshw -C network** output?

---

### Post by daniel295 on 2015-08-10
Sorry about that, well the wifi signal finally connected but now I'm trying to install and I'm at the page that says erase my old ubuntu and reinstall and the next option is erase disk and install ubuntu. 

I selected erase disk and new page popped up and gave me this error 

[[IMG]http://i1105.photobucket.com/albums/h341/hoodykid/Mobile%20Uploads/IMAG0358.jpg[/IMG]](http://s1105.photobucket.com/user/hoodykid/media/Mobile%20Uploads/IMAG0358.jpg.html)

Now I'm at this page and have no idea what to do lol 

[[IMG]http://i1105.photobucket.com/albums/h341/hoodykid/Mobile%20Uploads/IMAG0359.jpg[/IMG]](http://s1105.photobucket.com/user/hoodykid/media/Mobile%20Uploads/IMAG0359.jpg.html)

---

### Post by daniel295 on 2015-08-10
Ok so I formatted the partition with the old ubuntu on it. Still working and confused. Just want to keep the thread updated

---

### Post by daniel295 on 2015-08-10
So I've given up for now. 

I got the partition issue worked out. Used 3gb for the root and 1gb for the swap. It Ran out of space during the installation. But after doing research it says 17.1gb but I can't find it. So posted this pic. Maybe you guys can give me some help. 

[[IMG]http://i1105.photobucket.com/albums/h341/hoodykid/Mobile%20Uploads/IMAG0360.jpg[/IMG]](http://s1105.photobucket.com/user/hoodykid/media/Mobile%20Uploads/IMAG0360.jpg.html)

---

### Post by TheFu on 2015-08-11
sudo parted -l

---

### Post by Bucky Ball on 2015-08-11
Please attach screen shots using 'Go Advanced' and the paperclip icon in the toolbar. Thanks. :)

If you are intending to overwrite the Ubuntu install, choose 'Something Else' at the partitioning options and manually delete and create partitions for the install.

/ = 20Gb
/home = as large as you like
/swap = 2Gb

If you are not using a /home partition, then / using the whole drive with /swap as a 2Gb partition at the end.

---

### Post by daniel295 on 2015-08-11
I'm assuming that I a total capacity of 17.1gb. It says I've used 2.3gb and gave 14.8gb left. My question is how can I access the 14.8gb?


On the do something else screen it's only showing maybe 3.1gb available but under disk usage analyzer I see 14.8gb available. 

So why can't I see that under the do something else option?

---

### Post by daniel295 on 2015-08-11
Ok now I see what's going on! The extra space is coming from my usb drive. Smh. So I'm assuming that my hard drive is only a 4gb? That's dreadful.

---

### Post by Bucky Ball on 2015-08-11
What other partitions do you have on there? Erase them all if you have backed everything up. Is there 17.1Gb of unallocated space?

Boot from live media, Try Ubuntu, launch Gparted. What are you seeing there? Take a screenshot and post it.

---

### Post by TheFu on 2015-08-11
If you don't actually post the requested information, how can we help?

---

### Post by Bucky Ball on 2015-08-11
> **TheFu said:**
> If you don't actually post the requested information, how can we help?

Sorry, missed that. Yes, post the output of the command in post #31, please.

---

### Post by daniel295 on 2015-08-11
I'm assuming that the disk usage analyzer is also including flash drive that plugged into the laptop. After checking the bios it says I have a 3.7 fixed hdd. Does that sound correct?

---

### Post by TheFu on 2015-08-11
> **daniel295 said:**
> I'm assuming that the disk usage analyzer is also including flash drive that plugged into the laptop. After checking the bios it says I have a 3.7 fixed hdd. Does that sound correct?

Please post the requested output from the command above.  There is a reason we asked for it.

---

### Post by daniel295 on 2015-08-11
Ubuntu mate is now installed, with 488mb to spare lol. Only issues is the lack of wifi connection. I'm going to troubleshoot that and go from there. Thanks guys.

---

### Post by Bucky Ball on 2015-08-11
Please mark the thread as solved. Thanks.

---

### Post by him610 on 2015-08-12
Hello daniel295,

You mentioned you would like to install Chrome on your Dell Mini-9. I recommend you consider Chromixium 1.5 that opens looking like a Chromebook, but has Ubuntu 14.02 underneath. It runs very well on an older netbook with only 8GB SSD. My netbook, Acer Aspire One has only 8GB, and Chromixium 1.5 runs just fine on it. Check it out; you will be glad you did.

Download from here [http://chromixium.org/]("http://chromixium.org/")

Other questions: [http://chromixium.freeforums.org/index.php]("http://chromixium.freeforums.org/index.php")

---

