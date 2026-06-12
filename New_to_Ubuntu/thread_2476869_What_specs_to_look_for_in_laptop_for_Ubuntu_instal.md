---
title: "What specs to look for in laptop for Ubuntu install"
date: 2022-07-10
forum: New to Ubuntu
---

### Post by rooster65 on 2022-07-10
Hi folks,

Apologies for asking such a newbie question. What specs should I look for/avoid in choosing a laptop to do a full install of Ubuntu? (eg SSD, ram, processor etc) I'd like to completely remove windoze after the install. Thanks.

---

### Post by Impavidus on 2022-07-10
As far as SSD, RAM and CPU are concerned, anything sold as new in the past 10 years is good enough to run Ubuntu. What you may have to pay attention to is graphics and wifi. Intel is fine, nvidia may take some effort to get working properly. I think Atheros wifi usually works out of the box, Broadcom has a reputation of taking some more effort. But I've no recent experience with them. Hardware that's less than a year old may be problematic, as the Linux drivers haven't been written yet.

BTW, "remove Windows after the install": if you want to remove Windows, you do so before the install. Or rather, you just overwrite it. Don't take the effort of installing as dual-boot if you don't want Windows. You can also buy a laptop with no Windows preinstalled, but I don't expect that will be cheaper.

---

### Post by rooster65 on 2022-07-10
> **Impavidus said:**
> As far as SSD, RAM and CPU are concerned, anything sold as new in the past 10 years is good enough to run Ubuntu. What you may have to pay attention to is graphics and wifi. Intel is fine, nvidia may take some effort to get working properly. I think Atheros wifi usually works out of the box, Broadcom has a reputation of taking some more effort. But I've no recent experience with them. Hardware that's less than a year old may be problematic, as the Linux drivers haven't been written yet.

BTW, "remove Windows after the install": if you want to remove Windows, you do so before the install. Or rather, you just overwrite it. Don't take the effort of installing as dual-boot if you don't want Windows. You can also buy a laptop with no Windows preinstalled, but I don't expect that will be cheaper.

Thanks for that.

---

### Post by ActionParsnip on 2022-07-10
Depends what you want to do with the system. A user wanting to use Gimp to manipulate 700Mb images will need a different system to someone who wants to browse the Web. Not enough information in the question.

---

### Post by grahammechanical on 2022-07-10
My recommendation would be to buy a laptop with Ubuntu preinstalled. Some well known suppliers offer high-end, high price machines but there are few suppliers that will offer well specified machines at a reasonable price. Check out this web site.

[https://www.omgubuntu.co.uk/](https://www.omgubuntu.co.uk/)

Check through the back posts and you will see the offerings of a few suppliers in the UK and the USA that will sell you a well specified machine with Ubuntu preinstalled. You will be able to increase the specification and will be offered Linux distributions other than Ubuntu.

Regards

---

### Post by mIk3_08 on 2022-07-10
> **rooster65 said:**
> Hi folks,
Apologies for asking such a newbie question. What specs should I look for/avoid in choosing a laptop to do a full install of Ubuntu? (eg SSD, ram, processor etc) I'd like to completely remove windoze after the install. Thanks.
Dell Laptops. Other Dell laptops comes with the pre-installed Linux Ubuntu Operating System. Actually, there are lots of laptop that can be installed with Linux Ubuntu Operating System. But nowadays, is far different from the old days in terms of installation of Linux because in my case now, Before it is so "handy" in terms of fresh installation of Linux Ubuntu Laptop. Now, I haven't seen anymore some of the codes, apps, drivers in the internet. I think it was hidden already by the developer/owner of the codes, apps, drivers for the machine laptop. Regards and cheers.

---

### Post by grahammechanical on 2022-07-10
The official hardware specifications:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

There are flavours of Ubuntu that will run on machines that have even lower hardware specifications. Kubuntu has a different desktop environment to Ubuntu and it is not a low specification desktop environment. It needs the same hardware level as Ubuntu.

[https://topnewreview.com/kubuntu-20-10-review/](https://topnewreview.com/kubuntu-20-10-review/)

In the Ubuntu, Linux and OS Chat section of this forum you can open a discussion on the problems that you will face trying to install Ubuntu in a dual boot configuration with Microsoft Windows.

Regards

---

### Post by TheFu on 2022-07-10
There are certain brands that seem to be better supported than others, but not all models of those brands are well supported.  Dell and Lenovo tend to do well of the big brands.  I've seen questionable issues with HP, Acer, Toshiba, Asus, and a few others.  But because my LUG hasn't done any installfests for a few years, my "they are to be avoided" list isn't current. YMMV.

The budget will determine how much overkill you can bring to the question.
The planned workloads will determine how happy you might be when going too cheap or too expensive.
Programmers will have different needs, but the needs vary wildly based on their development platform.

Avoid bleeding edge hardware.  Go for something at least 1 yr old. Getting last year's model is a good start.  Search the internet for "ubuntu install {vendor model}" and if there are some posts that say it was really easy with no workarounds, add that to your list for consideration.  Many very popular brands like HP or Acer have easy to very difficult workarounds to get the OS installed.  Do the research BEFORE buying. Look for problems, not all rosy posts.  "ubuntu won't install on toshiba cg5436" is the type of search.  Also look for post-install issues, especially network and wifi issues BEFORE buying.  Just because things worked on 20.04, that doesn't mean they work on 22.04. There have been a number of posts in these forums by people who upgraded and found their wifi doesn't work anymore.

Do you care about battery life?  If so, I'd stick with Intel CPUs. They have a long history of sipping power. Also, their iGPUs are probabaly "good enough" for everyone except video editors and gamers. If you don't do either, it will be fine.  If you do, then expect lower battery life, but get an AMD system with an iGPU, if not fully discrete GPU.  A discrete GPU will turn a laptop with 10 hrs of battery into a 2.5 hr use on a good day laptop.

So, a minimal, normal user, will be very happy with a 1 yr old Core i3/Ryzen 3 CPU, 8-16GB of RAM, NVMe SSD (say 240GB - 1TB), with wifi-5/6 and sufficient USB-A and USBc ports.  I'd want an external HDMI port, since I give presentations and HDMI is still the standard for connecting to projectors.  YMMV.  For me, a bonus is a 1Gbps ethernet port.  I don't want to carry around a USB-to-ethernet dongle anymore.  Ethernet is what I use at home, so the wifi is really not high on my list of needs.  If I need it, I can buy a $20 USB Wifi dongle.  For the built-in wifi chips, I prefer intel and avoid realtek.  Same for onboard ethernet.

Screen size is important to most people.  I found 13in with a 1080p resolution to be a good compromise.  11in @768p wasn't high enough resolution and 15in at 1080p is too bulky for international travel, IMHO.  I've traveled with 4in, 8in, 10in, 11in, 13in, and 15in devices.  10in is too large for a tablet and not large enough for a laptop.  For a tablet, 8in is "just right" for me.  
I miss my 13.3in Toshiba with a Core i3 and 1080p screen.  It was under 2 lbs, a beautiful light, device.  I'd swapped out the SSD for a larger one (still only 64G) and loved the battery life.  Alas, the 4G of RAM was always just a little tight and the keyboard was crap.  Bad keyboards that fail and need to be replaced every 2 yrs is still a huge problem for everyone, except Lenovo and Dell, methinks.  The cost to replace just the keyboard used to be around $30 and 5 minutes of my time. All these ultra-slim laptops changed that completely, regardless of screen size. When the keyboard goes bad, it usually makes more sense to buy a new laptop, sad to say.

I have a 15in dell laptop from 2010 that still works, BTW.  it is over 1in thick at the hinge and heavy.  It needs to be retired as the discrete GPU in it has faults which are seen during boot. But it is barely used and hasn't been moved in over a decade. The 2nd-gen Core i5 inside it is really slow now.  There is little reason for it to be a laptop.  I've had 4 other travel laptops in that time. 

When looking at CPUs, always compare a performance benchmark, so you have a way to know the relative speed between the different models.  Benchmarks all suck and lie, but they are better than nothing.  A current generation CPU should be in the over 5,000 passmark range.  Desktops for mid-range CPUs are around 20,000 passmarks as a comparison.  I have an 8th-gen Core i5 laptop in the 6500 passmark range and find it quite acceptable for almost everything, except video editing. It has 8GB of RAM.

Don't overlook used laptops either.  There will be a bunch of off-lease laptops flooding the market, since MSFT is pushing for Win11 to require TPM chips. Many systems don't, so all of those will be sold as used.  I saw a used 14in Dell with 16G, Core i5 (9th-gen), and SSD for $300 yesterday.

So, what's the workload and budget?

---

### Post by oldfred on 2022-07-10
Beware of Pluton systems. I saw a whole separate display at Costco promoting them.

Lenovo's new AMD Rembrandt powered laptops with Microsoft Pluton security co-processor are set by default to only trust Microsoft's key or the only boot Windows. ThinkPad Z13 
[https://www.phoronix.com/scan.php?page=news_item&px=Lenovo-Pluton-Windows-Default](https://www.phoronix.com/scan.php?page=news_item&px=Lenovo-Pluton-Windows-Default)

---

### Post by grahammechanical on 2022-07-10
There have been posts in this forum where the user has been advised to enter the UEFI and disable this and that. The user then replies saying that the UEFI on his machine is very restricted as to what options can be enabled/disabled by the user. So, checking how easy it is to enter the UEFI and what settings can be changed is something else to watch out for.

Most computer owners do not want to mess with the machine's hardware settings. And I can understand why suppliers would consider anyone who buys a computer as an idiot who should be kept as far away from the inner workings of their products as is possible.

Regards

---

### Post by mIk3_08 on 2022-07-11
> **TheFu said:**
> There are certain brands that seem to be better supported than others, but not all models of those brands are well supported.  Dell and Lenovo tend to do well of the big brands.  I've seen questionable issues with HP, Acer, Toshiba, Asus, and a few others.
I agree with you TheFu. I have this HP Elitebook running with Linux Ubuntu Operating System. I'm the one who configured all the device in this machine. The WiFi, Bluetooth, fingerprints and etc and it was not easy then. Maybe I'm just so blessed that I did it well to work all the attach devices in this HP machine. Thanks to the Linux dev. I'm so proud using this Linux Ubuntu machine now. My advise to all the newbie who decided to migrate from MS Windows to Linux world. Just have faith and keep fighting and just do good inside the Linux world. The real Human is really is here. Regards and cheers.

---

### Post by jmpmjmpm on 2022-08-13
Just purchased a 4 year old Lenovo thinkpad T470s with a 7th Gen i5. I threw in a 1TB WD Blue NVMe SSD and 20GB RAM. Very happy with the result, everything works out of the box including the touchscreen but except the fingerprint reader. Lenovo provides Linux bios updates from their website. Total cost was around £300 and I have a very well built, reliable machine with the best keyboard that exists in the laptop market.

---

