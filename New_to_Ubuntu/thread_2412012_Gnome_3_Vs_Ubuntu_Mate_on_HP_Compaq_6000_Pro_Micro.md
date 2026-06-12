---
title: "Gnome 3 Vs Ubuntu Mate on HP Compaq 6000 Pro Microtower"
date: 2019-02-07
forum: New to Ubuntu
---

### Post by maghdalena2 on 2019-02-07
I hope this is the right place; I'm a newbie to Linux and Mint so thought this might be the best place to ask. If not, please redirect me, please.


As you know, the life cycle of Windows 7 is coming to an end next January, and since we don't really want to move to Windows 10 because of what I've been hearing of privacy issue violations and update issues, so we're considering the Linux option. 


We're between 2 Distros, Ubuntu and Mint. Here's the conundrum I'm facing. We have a refurbished HP Compaq 6000 Pro Microtower with a two TB hard drive and are thinking of getting another next Christmas season. It's either going to be an SSD, which I would prefer or another HDD. We don't want to get rid of Windows 7 because there are some programs that run under that that just won't run under Linux (PrintMaster 18, Publisher, but most of the stuff that we'd be doing would be under Linux. 


I've been hearing a lot of scare stories on this forum and YouTube about the dangers of dual-booting alongside Windows 7(I think it's legacy, not UEFI because I'm not seeing any EFI anywhere in the disk management partition. I *was* thinking of dual-booting with Windows 10, but then I started hearing those scare stories, both about Windows 10 and about dual-booting and I really don't know what I'm doing, so I'm thinking of getting either a regular, mechanical hard drive or an SSD. 


I have all my files on our external hard drive, a Seagate Backup Plus 3 TB USB 3.0 Desktop External Hard Drive (STCA3000101). I redirected the Windows libraries to that drive, and would like to do that with the Linux files, I guess it's the "Home" directory/folder if I can. I understand that that's different that you just move the whole folder not the documents, pictures, music, video. Is that right?


Anyway, this is the breakdown of what our system has right now: 


Windows 7 Professional, 64 bit SP1.
Intel Core 2 Duo 3.00 GHz. (Wolfdale 43 technology
RAM: 8GB Memory on DDR3, with a limit of 16 GB
HP 3048h motherboard with Intel. (I know it's a little long in the tooth)
Integrated Video(No video card other than what's on the MB
Dell E771e CRT monitor(that's outlasted 2 computers already :))
2 TB HDD
Seagate 3 TB External USB HDD
HP DVD-R/RW Optical Drive ATA(According to Speccy)
Real Tek High Definition Audio (Integrated on the MB, I'm assuming)

Our printer btw is an Epson WF-3640 (Workforce All in One Printer)


I'm assuming the hardware is too old for the Gnome DE but is it too old for Ubuntu Mate? Or XFCE/Xubuntu? What would anyone advise for my environment? I like Gnome, but I really like Ubuntu Mate, but I have no confidence there won't be freezing issues. I'd be willing to go for XFCE/Xubuntu.

Also, I don't know if it's off-topic or not, but how do you verify the iso(once it's downloaded) with Windows 7? I have no idea how to do that. Total Newbie here.


I hope I haven't been too long-winded.


Any help would be appreciated.
Thanks for your time and patience.
Sincerely yours,
Maghdalena Logan

---

### Post by Impavidus on 2019-02-07
The CPU may be 10 years old, but is not bad. 8GB ram is plenty, so if you have reasonable graphics, it should run any flavour of Ubuntu. I run Xubuntu on a computer with far worse specs.

Regarding scare stories, dual booting isn't as easy as it was with Windows XP, but with Windows 7 and legacy booting it shouldn't be too hard. Keeping them on separate hard drives makes it even simpler, but you do have to know what you're doing. It's often best to disconnect the Windows drive while installing to the Ubuntu drive.

---

### Post by Claus7 on 2019-02-07
Hello,

I do not know if virtualbox can be an option as well. You could switch to ubuntu as main OS and then add the version of windows you want under virtualbox. Yet, you should check if you can work out the programs inside virtualbox as you used to, and the rest can take place under linux.

Things change so Lubuntu might be an option as well. In old times Xubuntu was among the best solutions for low ram consumption. Lubuntu is a strong candidate as well, yet i) it is also a matter of taste ii) Lubuntu gets a great update, so I do not know the newest versions how will behave.

Regards!

---

### Post by maghdalena2 on 2019-02-08
> **Impavidus said:**
> The CPU may be 10 years old, but is not bad. 8GB ram is plenty, so if you have reasonable graphics, it should run any flavour of Ubuntu. I run Xubuntu on a computer with far worse specs.

Regarding scare stories, dual booting isn't as easy as it was with Windows XP, but with Windows 7 and legacy booting it shouldn't be too hard. Keeping them on separate hard drives makes it even simpler, but you do have to know what you're doing. It's often best to disconnect the Windows drive while installing to the Ubuntu drive.

I looked up the graphics. It said the Intel GMA 4500. It said the "Shared memory was 384 MB. Is that right. I don't know if that's acceleration or what, but that should be enough I think. 

I was planning on having someone we know to install the SSD drive(since I looked up SSD drives and it the power supply should be able to support it better than a standard mechanical drive, but it can manage both, but there seems to be more "wiggle room" with an SSD drive. So, I'm thinking maybe he should install Ubuntu on it as well.  And the OS's they work with are Linux, Windows and Unix, so they should be familiar with either Unbuntu or Mint, which ever one we end up going with.

So thanks for the advice. I'm not as confident of connecting and disconnecting the cables of the hard drive, at this point of time, at least. It does help.

Thanks again,
Maghdalena

---

### Post by maghdalena2 on 2019-02-08
> **Claus7 said:**
> Hello,

I do not know if virtualbox can be an option as well. You could switch to ubuntu as main OS and then add the version of windows you want under virtualbox. Yet, you should check if you can work out the programs inside virtualbox as you used to, and the rest can take place under linux.

Things change so Lubuntu might be an option as well. In old times Xubuntu was among the best solutions for low ram consumption. Lubuntu is a strong candidate as well, yet i) it is also a matter of taste ii) Lubuntu gets a great update, so I do not know the newest versions how will behave.

Regards!

Thanks for the advice. The only thing I can do is try it out and see how it works. I can at least try it in Windows 7 Pro. I still feel more comfortable having Windows 7 on one drive since I can use PrintMaster on it and it's all set up, and then Linux on the 2nd drive, probably an SSD drive, though. Lubuntu is something to consider, but my favorite is still Ubuntu Mate. My computer came with Windows 7 Professional (which comes with XP Mode-which should work as long as the virtualization is enabled. They seem to have changed from only allowing hardware-assisted virtualization to allowing Intel virtualization and AMD virtualization in addition to it. But something to consider. Thanks. :)

Have a great day!
Maghdalena

---

### Post by oldrocker99 on 2019-02-08
I highly recommend Ubuntu MATE. It's lightweight, very configurable, easy to learn, lets first time users install software directly from the Welcome program, most suitable for new users and experienced hands, and a lot of in-the-know users like it. It's the DE I fell in love with, GNOME 2.3, when I started with Hardy Heron, 8.04, all those years ago, and it's been improved again and again.

MATE (MAH-tay) is maintained by the Ubuntu MATE developers, so you always will have the newest version. At least burn a live USB and give it a whirl.

---

### Post by lammert-nijhof on 2019-02-10
Using a modern 2 TB HDD (150-200 MB/s) or a SSD on your SATA-2 connection (300MB/s), you can run any Ubuntu distro in 8 GB. I recommend Ubuntu Mate 18.04, but that is based partly on efficiency but more on personal taste.
I personally use Ubuntu Mate on a 2008 HP dc5850. It has a 4 core AMD Phenom II X4 B97 at 3.2 GHz and also 8 GB, but DDR2 at 800 MHz 

 BUT you have to check again your SATA connection, I did see, the motherboard has SATA-2 and that would limit the SSD to <300 MB/s. I had the same issue, so I did buy a SATA-3 PCIe X1 card for $8 from China to avoid the SATA-2 limit. However now my SSD is limited by the PCIe 2.0 bus, which is in theory max 500 MB/s. In practice my SSD runs now at ~400 MB/s, probably caused my whole chain DDR2 -> PCIe 2.0 -> Cheap SATA-3 card -> SSD. You probably also have the same older PCIe 2.0 bus. So if you buy a SSD, you could almost ignore its speed as a selection criteria. 

I did buy a 128 GB SPCC SSD for $21 from Newegg during the end of 2018. For Linux, its programs and normal data 128 GB is enough and for huge amounts of data (like many HD videos, many Virtual Machines e.d) you could use a part of the 2 TB or share a NTFS partition. 

In 2017 I did run that HP with an 2-core AMD Phenom II X2 B59 at 3.4 GHz and I had no problems. I use a lot of virtual machines also Windows 7 and 10 and it runs and did run fine also with the 2-core. Most of the perceived responsiveness depends on your storage setup. You do not need it, but you could use the distro with the BTRFS file system and LZO compression, that would give you a speed advantage of say a factor 1.7 due to the reduction of the number of bytes transferred to/from HDD or SSD due to the compression. I even used that LZO compression and BTRFS with a 3.0 GHz Pentium 4 CPU. 
On top of that, among others BTRFS protects against file corruption, allows snapshots and makes efficient use of the _free memory as disk cache_.

---

### Post by maghdalena2 on 2019-02-11
Thanks for your response. I heard about Ubuntu Mate from Joe Collins over at YouTube and EzeeLinux, and he really spoke well of that and Linux Mint, and I really liked what I saw of Mint's Mate. In fact, it was one of my first choices, because I wasn't sure our refurbished computer could handle Cinnamon/Gnome 3 because the motherboard, processor and bios are a little 'long in the tooth".

Yes, I do believe that my hard drive, that is the internal is a SATA-2. My external drive is SATA-3, but runs at the SATA 2 speed, since my USB is USB not USB 3 (attached with USB) All our files are on the external hard drive, which I really find helpful. I'm thinking of putting our Linux files, on the external drive. I think it was a 3 TB drive, more or less, anyway. 

Ok. What is this SATA-3 Pcie X1 card? Is that like an adapter to go from SATA-2 to SATA 3? That sounds like a good option, but where do you recommend I get one? And as far as speed, I could probably live with the speed it has. I'm guessing that you're probably right, having an older one. This is what I'm getting from Speccy:

PCI-E
Slot Usage	Available
Data lanes	x1
Slot Designation	PCI EXPRESS x1 SLOT 2 (PCIEx1 2)
Characteristics	3.3V, PME, SMBus
Slot Number	2

I'm not sure exactly if that's a 2.0 bus, but I'm guessing it is. 

I actually made a partition for Windows 10, but after hearing what Joe Collins said about newbies dual-booting, and that there could be problems, I'm kinda "chickening out". The partition's still there, and formatted for NTFS, but I'm not doing anything with it right now. I *was* thinking of using the partition for a virtual machine to learn Linux on assuming on if I can actually figure out how to download via bit torrent. (I've never used a torrent program before) I have Deluge, but I have no idea how to use it, I'm that much of a newbie. 

What's a BTRFS file system? I've never heard of that or LZO compression either. Could you explain that in English?   I'm not as tech savvy as I would like to be. I'm sure the people I'd have installing the SSD drive would know, but I have no idea what that means.

Again, thanks. It's nice to have options. :)

Maghdalena

---

### Post by maghdalena2 on 2019-02-11
I've heard of Hardy Heron, and I know a lot of people speak well of Mate. It's definitely up there with my choices of DE, and my first choice for Ubuntu DE, to be honest. I've heard it's lower on the resources too, at least as regards the "OS". I've heard that Cinnamon (Mint) and Gnome 3 can be a little heavy and "piggy" on the resources. I do like it a lot, and it's nice I can tinker with it.  I remember vaguely when I was dipping my toes into Linux 13-15 years ago, that people squawked when Gnome 3 came out. They really loved the Gnome 2 DE better, and of course Unity. But my preference is Mate too. 

I'm really considering downloading an iso, but which do you recommend, a mirror or torrent, because I"ve never downloaded a torrent file before, and have no idea how to use a torrent application (I have Deluge on my Windows 7 and installed. So what do I do now?

Thanks again for the kind words. :)
Maghdalena

---

### Post by Claus7 on 2019-02-11
Hello,

Hardy Heron is an old release of ubuntu, so it is not recommended, yet if downloaded it should work. Mirror is nice as well. Since you mention matter of taste, then this is totally subjective. I think that you should make up your mind and then choose: what I mean is that testing might be the best solution, since anyone has different likes and dislikes.

Regards!

---

### Post by oldrocker99 on 2019-02-11
I certainly wasn't recommending that people install Hardy Heron, Ubuntu **8**.04. Kind of out of date...

---

### Post by Dennis N on 2019-02-11
> I have Deluge on my Windows 7 and installed. So what do I do now?
To use a torrent, you first download the torrent file. Then open the torrent file with Deluge. Deluge will then try to download the .iso file for you. This can be fast or slow depending on the number of users. Direct download of current Ubuntu release from it's servers is often faster.

Don't think about using Ubuntu 8.04. Can't be updated to insure your system is safe, and cannot use current versions of web browsers.

---

### Post by maghdalena2 on 2019-02-11
Thanks. I think I used to have Hardy Heron, a long time ago. I think I pitched it because I figured it wasn't safe, old kernel and all. I agree the best way is to test different desktop environments in live to see how the hardware takes it, lol. So, downloading by the mirror is safe then? I don't exactly get the verifying thingie, though. Is downloading through torrent safer or easier, since I've never done it before. 13 years ago, I used to either request disks or bought them, but I'm a little broke, and I want to learn to do it for myself, if you know what I mean.

---

### Post by maghdalena2 on 2019-02-12
Yeah, OK. Thanks. I recently pitched a lot of my Linux Live CDs/DVDs, because they were all old, and thus, unsafe, security-wise. I used to have Mepis. Shame the project was abandoned. It had everything, so overwhelming, but it was nice. That's the first Distro I was introduced to (from "Free Software for Dummies") I'm getting over my pack-rat days, lol! ;)

Thanks for the directions. So I can download Ubuntu Mate and Xbuntu then open them (one at a time, of course) *then* open them with Deluge. Thanks!

---

### Post by Geoffrey_Arndt on 2019-02-12
As info, like the storied "Phoenix" of legend . . . . _**Mepis still lives**_ . . . . in the form of MX Linux.  Is #2 on the Distrowatch "hit parade".  (See Distrowatch link at bottom of this message)

Also, since you have PLENTY of time before Win7 loses support, you can visit a few key websites and learn the ABC's of Linux and Ubuntu.

For many newbies and PC challenged . . . remember that "youtube" is your friend.   A few of my favorite channels include videos by:

>  Joe Collins
>  Chris Titus Tech
>  LearnLinux.tv
>  Linux Quest
>  Linux Tex
>  Matt Hartley
>  Tux Digital
>  XPS Tech

There are many others, but I know these are well supported by the content creators and offer info more suited for beginner to intermediate users versus system or IT admins.

Plus, you can use the built-in search box on the Youtube website pages to search for specific videos of topics such as:

"How to Download and Use Torrents in Ubuntu" . . . OR . . . "How to Install Ubuntu to an External SSD" . . . . etc, etc.etc.

[https://distrowatch.com/table.php?distribution=mx](https://distrowatch.com/table.php?distribution=mx)
[URL="https://distrowatch.com/table.php?distribution=mx"]

[/URL]

---

