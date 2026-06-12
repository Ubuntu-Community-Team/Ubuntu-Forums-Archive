---
title: "How is Ubuntu performance on external SSD vs internal SSD?"
date: 2021-12-28
forum: New to Ubuntu
---

### Post by robinbanks777 on 2021-12-28
Hello, I am thinking about running Ubuntu on an external SSD, however I am not sure if the performance will be any good. The reason it matters is because I want to use it for video editing, programing ETC. I can't install it directly beacuse the computer I want to use it on belongs to the school and it would mess up their files. I've also run Ubuntu on usb but it also has worse preformence. That's why I am worried about running it on an SSD. Thanks for reading my question.

---

### Post by oldfred on 2021-12-28
I just posted this, as a not too scientific test of speeds.
[https://ubuntuforums.org/showthread.php?t=2470308&p=14072692#post14072692](https://ubuntuforums.org/showthread.php?t=2470308&p=14072692#post14072692)

While not as fast as internal SSD, I was surprised at how well it worked.
I also found USB3 flash drives to be slow, and old USB2 flash drives to be impossibly slow.

---

### Post by TheFu on 2021-12-28
NVMe is 8x faster than USB 3.1 just in the bus performance.
Only you can decide if that performance is sufficient.

"Programming" isn't specific enough. Which language? Which tools?  How much data?

I've programmed using a chromebook in 2011 and it was more than sufficient.  Many people program using Raspberry Pi 2 computers with USB2 storage.

The only answer for these sorts of questions can be "it depends."

Flash storage all has performance issues and write counts.  SSDs are flash, just like a MicroSD card is flash or a USB3 storage stick is flash. What's different is the technology and performance of writing and reading the storage. That's why the connection to/from the storage to the computer matters.

The fastest SSD connected through a USB2 port will not be impressive.

---

### Post by robinbanks777 on 2021-12-28
Thank you both for responding. I'm pretty sure the computer has a USB 3.1 port and some USB type c ports. As for programming I am really not sure but I will probably be using python but I will also want to do some machine learning stuff like with tensor. I don't know what exactly yet.

---

### Post by oldfred on 2021-12-28
I do not see much advantage to using NVMe in an external USB adapter. 
They run hotter, and USB3 port then is bottleneck. And NVMe is still more expensive.

My 2016 build had a M.2 slot. But NVMe was real expensive then, so added M.2 SSD drive. 
Then recently wanted larger drive & NVMe was not that much more. But SSD had been quick. I think I notice NVMe drive is faster than SSD booting & loading large files, but not a lot faster than SSD. 
But my main speed issue is between chair & keyboard & I think that is getting slower. :)

---

### Post by mIk3_08 on 2021-12-29
> **robinbanks777 said:**
> Hello, I am thinking about running Ubuntu on an external SSD, however I am not sure if the performance will be any good. The reason it matters is because I want to use it for video editing, programing ETC. I can't install it directly beacuse the computer I want to use it on belongs to the school and it would mess up their files. I've also run Ubuntu on usb but it also has worse preformence. That's why I am worried about running it on an SSD. Thanks for reading my question. 
I have run my Linux Ubuntu Operating System using SSD and its more faster and more smoother than my Linux Ubuntu Operating System on hdd. And I'm running this for years using SSD and so far I haven't encountered any major trouble on my Linux Ubuntu Operating System in related to my SSD. So far so Good. So Good Luck and Advance Happy New Year. Cheers.

---

### Post by Impavidus on 2021-12-29
For programming you only really need a text editor to edit source code. You can do that on a 30 year old computer with a floppy drive just as well as on a modern computer with internal SSD. Running the program may be a different matter, depending on what kind of program you write. Some programs work better if they have fast access to storage.

Video editing is a different matter. Video editing software is quite heavy, so from an external drive it may take some time to load it. Once loaded, it should run as well as if stored on an internal drive. Video files are quite big, so loading them from external drive may be a bit slower than first copying them to the internal drive. Finally, depending on RAM available, your video editing software may need swap. Then you want the fastest storage you can get. But if the videos are small or you have plenty of RAM, that should be no issue.

So, in short, an external drive will be a bit slower, causing software to take more time to load, but once loaded, it will run equally fast. Loading or writing large files (like videos) will take a bit longer on external drives.

---

### Post by TheFu on 2021-12-29
> **robinbanks777 said:**
> Thank you both for responding. I'm pretty sure the computer has a USB 3.1 port and some USB type c ports. As for programming I am really not sure but I will probably be using python but I will also want to do some machine learning stuff like with tensor. I don't know what exactly yet.

People program with python on raspberry pi-0 computers.
I've never used tensor, but if it is anything like CFD, then more CPU, more RAM, more bandwidth for I/O, the better. There's no way we can get enough of that. Open your wallet.  If you just want to play around, use USB.  IF you want to be serious, look into Infiniband with banks of NVMe storage.

The USB storage protocol isn't designed for 50 different processes to access the same storage. It usually works, but not all that well. 10 yrs ago, it didn't even work all that well, even with USB3 devices.

Don't confuse theoretical bus throughput with actual storage read/write performance.  Those are usually extremely different.
I have 3 SSDs connected to 3 different systems.  2 use the SATA3 bus for the SSDs and 1 uses an x3 NVMe.  The SATA SSDs can be tested from between 100 Mbps to 550 Mbps, even though the bus they connect into is (SATA1, 2, 3 ... at 1.5Gbps, 3Gbps or 6Gbps) respectively.  SATA1 is sufficient.  OTOH, NVMe should be around 3500 Mbps - jumping up to 32,000 Mbps for x4 speeds.  I think some of the newer versions available today get over 50Gbps.  Few home users will have NVMe connections that support that throughput.  USB3.1 is 5Gbps. USB 3.2 is 10Gbps - in theory.  Nobody gets the theoretical bandwidth. There is always overhead and tiny faults that are corrected in hardware ... or the bus is shared with other devices in the system.  For example, if I have an x8 PCIe CPU in my system, then the NVMe connection is limited to x2. They have to share the bus.

For normal use, I 100% agree with oldfred that any external SSD going over USB isn't worth using NVMe SSD connections, unless you plan to put that SSD into another computer in the next 12 months.  As always, computer storage prices are always dropping and in a year, we'll have 1TB NVMe for 30% less than today. Use a SATA SSD - it will still be 4x faster than spinning HDDs.  I have a few old, slow, SATA SSD devices that are in USB enclosures.  These were cheap when I bought them and don't have the long life that typical, branded, SSDs of today provide. Still, they  are low power, silent, and significantly faster than any cheap flash or spinning-rush storage.

BTW, it is usually much cheaper to get the SATA SSD separate from the USB 3.2 enclosure.  A USB 3.1 vs 3.2 enclosure is another question.  If the price is within $10, I'd get the v3.2 version, no question. I only have 2 USB 3.2 ports (they are red) on 2 of my systems.  But at least I'll know that any performance issues on USB 3.1 ports isn't due to a slow controller.  It is sorta like how USB3 vs USB2 is very clearly a win for USB3 connectors.

Video editing is completely different.  More speed, faster access to storage is always desired.  Professional video editors often setup banks of RAID0 NVMe storage to make writing huge 8K video files as fast as possible  I've seeing setups with 16 NVMe devices in RAID0 and the rendering process still took hours.  There is always a trade-off between faster access, connectivity and use by multiple systems concurrently. RAID0 was never used as anything except scratch storage. Nothing was left in that storage overnight, since if just 1 of the devices has a tiny failure, everything would be lost.  There are lots of methods to make storage "appear" to be faster, but still gaining redundancy. Some of these aren't well-supported on Linux, but we have other methods that are.

For someone just trying out Linux for the first time, best to keep the outlay as low cost as possible, until the real desires are known later.  If it were me, I'd never run the OS over USB3. There are lots of performance trade-offs with USB storage that SATA protocols don't make. It is a different command set.  The location of data can be on USB disks.  I only use USB for backup storage, never for main data or the OS, unless it is an emergency boot to fix something else, but there are lots of people happily running a web browser OS off a USB flash drive with a separate "permanent" storage partition for their data. Everyone has to compromise.

---

