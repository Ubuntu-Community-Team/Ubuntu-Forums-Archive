---
title: "Installing Ubuntu on UEFI / secure boot"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by GaryTheCat on 2012-11-26
I've been an Ubuntu user for a few years now having dual booted with windows.

What I'd like to do now is to get a new PC and have it just running Ubuntu.

So.

What is the best way to set up partitions etc to make distro upgrades as simple as possible in the future? I know there's a way to create /home in a different partition and then mount it so no data is lost when a new USB/CD is used to upgrade to the next release but I don't know how to do it.

All new machines seem to ship with Win8 - I'm aware of issues with UEFI and secure boot but is installing Ubuntu alone as simple as disabling secure boot in UEFI and then proceeding as normal with installation USB/CD?

Many thanks

G

---

### Post by audiomick on 2012-11-26
> **GaryTheCat said:**
> ... a way to create /home in a different partition and then mount it so no data is lost when a new USB/CD is used to upgrade to the next release ...

That is pretty easy. During the install, when you get to the part where you can choose "use the whole drive" or "install next to windows" there is an option "something else". Or at least that is what it was called on the 12.04 installer, I think. Anyway, the aim is to get to the manual partitioning option. In there, simply set up the partitions you want and choose the mount point you want. Depending on how big the drive is, maybe 15GB mounted at /. That is where the system goes. A bit bigger than your RAM as a swap partition. You can't choose the mount point when you have designated that partition as swap space. The system can only mount it as swap, so you don't get a choice. The rest of your space mounted at /home. If you have a monster big drive, maybe you could divide it up a bit and make a couple of data partitions. You would then have to invent a mount point for them. The other ones I have mentioned are in a drop down list in the installer. I have, for instance, a partition mounted at /home/basement.

If there is already a windows on there, you should use the windows tools to shrink the windows partitions to make room for your Linux install. I believe it is a good idea to start windows a couple of times after doing that to let it have a chance to run the disk checking tool if it wants to. 

> All new machines seem to ship with Win8 - I'm aware of issues with UEFI and secure boot but is installing Ubuntu alone as simple as disabling secure boot in UEFI and then proceeding as normal with installation USB/CD?

I am really not sure about this, but I read just the other day of someone who was worried about exactly that, and then discovered that his new motherboard did not have any problems. I think that if it is not advertised as "Win8 ready", then you don't have a problem, and I think you are right about just disabling the secure boot, but I am really only guessing.

---

### Post by grahammechanical on 2012-11-26
If you are only going to have Ubuntu on the machine then you do not have to disable secure boot. You have to install 12.10. See this:

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

Keep in mind that UEFI and secure boot are all very new. You will end up with more knowledge of this than many here. Certainly more knowledge than me.

I installed Ubuntu on the single blank hard disk in a machine I built myself. The install created two primary partitions. Ubuntu was put in the first partition. The second primary partition was an extended partition which contained a logical partition that was the swap partition.

Later, I had to re-install so I used the opportunity to create a separate /home partition. Actually, I broke the OS when I messed up trying to create a separate /home partition. That is why I had to re-install.

I shrunk the first primary partition to 20GB and I gave it the mount point of /. In the unallocated remaining space I created another primary partition which I gave the mount point of /home. It had to be formatted of course.

So, I had Ubuntu in the 20GB partition and all my data and stuff in the 200GB /home partition. Which is the kind of set up you are looking for.

Since then I have shrunk my /home partition to make the extended partition larger so that I could create 10 -15 GB partitions that I could use to test different Ubuntu installations. I have 2 x 12.04, 1 x 12.10 and 1 x 13.04 and I am about to install another 13.04 to test the ISO image.

All except one 12.04 are in logical partitions inside the extended partition.

UEFI and Secure boot are the least of the problems.

The problems come from dual booting with Windows 7 and Windows 8 where Windows has already used up the maximum of 4 primary partitions or has converted the partitions to something called dynamic partitions which the Ubuntu installer cannot use.

[http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx]("http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx")


[http://support.microsoft.com/kb/309044]("http://support.microsoft.com/kb/309044")

Regards.

---

### Post by mörgæs on 2012-11-26
> **GaryTheCat said:**
> ... get a new PC and ...

Have you thought of some new-ish but used gear? As Buntu is far more efficient than Windows on the same hardware you could maybe do with something which is not brand new.

---

### Post by GaryTheCat on 2012-11-26
That's interesting about 12.10 - Do I take it to mean that as it supports secure boot out of the box that it "should" be possible to dual boot / single boot the machine just as one normally would with previous releases?

G

---

### Post by GaryTheCat on 2012-11-26
> **mörgæs said:**
> Have you thought of some new-ish but used gear? As Buntu is far more efficient than Windows on the same hardware you could maybe do with something which is not brand new.

That's not a bad idea - but it seems that a lot of sellers are putting Win8 on machines assuming it's what the customers want?

Personally I think it looks and feels awful.

---

### Post by audiomick on 2012-11-26
> **GaryTheCat said:**
> ... it "should" be possible to dual boot / single boot the machine just as one normally would with previous releases?

Can't say for sure, and I haven't read that link yet, but I know that Canonical is at least working in that direction. I don't know where it was, but I read something about it just recently. 

If you do use UEFI instead of BIOS, then I believe you can use GUID partitions tables, which would remove the need for primary, extended and logical partitions.

[http://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")

---

### Post by grahammechanical on 2012-11-26
I assumed that the blogger was one of the developers working on secure boot for UBuntu. He says this:

> The 12.10 release is the first version of Ubuntu that supports Secure Boot out of the box.

He also says this:

> This first release gives us preliminary support for booting on Secure Boot, but there's more work to be done to provide a full solution that's sustainable over the long term.

What you want to do should be viewed as an experiment. This blog might interest you:

[http://arapulido.com/2012/11/05/ubuntu-certification-101-bios/]("http://arapulido.com/2012/11/05/ubuntu-certification-101-bios/")

Regards.

---

### Post by oldfred on 2012-11-26
Several have posted that the 64 bit version of Ubuntu 12.10 does install without any issue on their system. Others have had issues. Some will not work at all.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

    
It is important to use the 64 bit version of 12.10 as it has the new grub2 2.00 that has the changes for secure boot. Grub2 2.00 is also supposed to be released for 12.04 with the next point release in Jan.

You also have to boot from the UEFI menu in UEFI mode not BIOS/legacy/AHCI mode. 

Grub2's os-prober does not create a correct efi chain load entry to Windows. It still creates a BIOS type entry. But Boot-Repair can fix that or convert an incorrect BIOS type install to efi. Or you can manually add a correct efi chain entry.  I think you can only incorrectly install the BIOS type install with secure boot off anyway.

Windows only boots from gpt partitions with UEFI, or if you have Windows booting from UEFI you have to have gpt partitioning.

       [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
I do not think this was secure boot 
       Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

---

### Post by GaryTheCat on 2012-11-26
My personal semi-noob summary of this discussion thus far is that I'm probably better off buying a PC with Win7 on it to overcome the UEFI problem.

Does that sound reasonable?

---

### Post by oldfred on 2012-11-26
Maybe?

Some have posted with newer Windows 7 installed in UEFI mode. But most Windows 7 have BIOS/MBR even if they have UEFI type BIOS. 

I think most if not all  Intel recent i-series chips had UEFI enabled motherboards, but many just were in legacy/BIOS/AHCI mode.

New computers are all Windows 8. So if you can find a Windows 7 computer it should be on sale as old inventory.

And then you are back to the issue of 4 primary partitions all being used. It seems almost all Windows 7 installs use all 4 primary partitions and you have to work around that issue.

---

### Post by GaryTheCat on 2012-11-26
It's such a pain - being arm-locked into lining the pockets of microsoft.  I've tried looking for naked hardware (minus installed OS) but all I can find in the laptop department are 'pigs' - I suspect anything 'decent' is about as easy to find as teddy bear droppings.

It's a bit of a leap of faith to spend several hundred GBP to potentially turn something into a paperweight.

---

### Post by mörgæs on 2012-11-27
> **GaryTheCat said:**
> That's not a bad idea - but it seems that a lot of sellers are putting Win8 on machines assuming it's what the customers want?

Personally I think it looks and feels awful.


I meant some 2-3 years old hardware from the a private seller like Ebay.

---

### Post by JKyleOKC on 2012-11-27
> **GaryTheCat said:**
> My personal semi-noob summary of this discussion thus far is that I'm probably better off buying a PC with Win7 on it to overcome the UEFI problem.The last box I bought came with Win7 installed at the factory. It also used UEFI and dropped me into this confusing world.

I finally got it sorted with the help of Fred and Yann, but finding a Win7 machine is no guarantee. If the HDD is bigger than 1 TB, the odds are that it uses the gpt partitioning and if it does, then Windows requires UEFI. The only thing that avoiding Win8 assures is that you won't have to deal with Secure Boot.

And these days it's difficult to find a machine without Win8 installed at the factory!

---

### Post by audiomick on 2012-11-27
> **JKyleOKC said:**
> 
And these days it's difficult to find a machine without Win8 installed at the factory!

The best way I know is to have a computer shop put one together for you, and don't order a windows with it, or buy the bits and put it together yourself (which I haven't be game to try myself yet...).

That is all well and good for a desktop, but if you want a laptop, your chances are pretty slim unless you go to one of those places offering pre-installed Linux.

---

### Post by YannBuntu on 2012-11-27
In France, we can order new laptops (which are preinstalled with Ubuntu, or sold without OS) via several retailers on internet. Eg, i bought a Clevo i3 one for only 400$ one year ago, and it works perfectly with 12.04 and 12.10. Maybe you also have some Clevo retailers in your country...

We (ubuntu-fr) also maintain a list of Ubuntu computers vendors: [http://doc.ubuntu-fr.org/ordinateur_vendu_avec_ubuntu](http://doc.ubuntu-fr.org/ordinateur_vendu_avec_ubuntu) , maybe there is one maintained by your LoCo Team.

---

### Post by the.phantom on 2012-11-28
what i did was just got a barebones kit from a online vendor. amd 64 bit quad 3 gig, 8 gig ddr3 memory, and a 64 gig ssd desktop. yep it is pleanty fast and about $300. took a few hours and installed mint on it.

you would be surprised if you just ask around and think you might find a friend that has done it before? it is not that difficult to do !
i use to do like you did and buy a OEM system, now make what i want and can upgrade and not have to get a new system !
right now helping a friend 2k miles away build one close to mine and he has no experience and it is up and working and installing now  as i type.
(ya a few big e-mails with pics)

save money and build what you want and if you need more power, just upgrade it !
one system had a onboard ati card and would not cut it so just upgraded to a nvidia 210 and does all i want .

tigerdirect and newegg are places to look. just google a bit and see if the hardeware is compatable with ubuntu or whatever you use.

only about 8 basic parts to a computer and just follow the diagram to plug into the correct places and off you go !
run a memory test, check cpu/mobo temps and then install

or talk to a computer store and have him build one up for you and specify NO OPERATING SYSTEM ( good for at least $100 off the price)

---

### Post by tir2 on 2013-10-26
> **audiomick said:**
> your chances are pretty slim unless you go to one of those places offering pre-installed Linux.ows

If you are not an expert, I have to agree with Michael: You may (currently) face major problems with installing Linux to notebook.
Some of my list with Acer Aspire E1-572:
- Ubuntu didn't recognize Windows 8 boot! So the default option is that it will remove it
- There is minus sign ("-") on next to a partition. This does **not** mean that you can decrease the partition size. It means that you will remove the partition. And no it does not ask if you are sure and no there is no built-in mechanism to undo what you just did.
- Ubuntu has issues, such as shutdown never finishes, so by default it will not leave your hard drives into stable state but will start fixing them after you restart with power switch.
- Fedora does not boot at all even if safe booting has been disabled from BIOS, so Ubuntu is at least in better shape than the Fedora.
- Ubuntu was not able to format my USB thumb drive.
- You may not be able to create bootup disk of USB thumb drive unless it is empty. Well solution to this and previous was to delete all files. Trivial if you figure that out.
- Linux distributions are designed for DVD drive. By default notebook do not have one, so you have to at least copy-paste files from the ISO image to USB drive (trivial)
- Sometimes copy-paste does not work, use then another software to extract instead.

So, yes, with older and desktop hardware Linux may be easy, but with newer and notebook hardware use Linux only if you have an expert installing it or you have nothing to loose if you fail.

---

### Post by oldfred on 2013-10-26
Older systems only had BIOS with MBR(msdos) partitioning. Relatively simple but still an operating system install where backups are important.

Now you have many more options and many systems also need UEFI/BIOS setting changes.

Now you have UEFI with secure boot, UEFI without secure boot and CSM/BIOS/Legacy as boot options. With UEFI you have to have gpt partitioning but with CSM (if all systems) you can have MBR.
If reinstalling Windows in BIOS mode it does not correctly change gpt to MBR, it leaves backup gpt partition table and then Linux does not know if drive is MBR or gpt.

Windows  also has always on hibernation for fast boot which prevents Linux from even seeing the NTFS partition.

Many new UEFI systems also have Intel SRT with a small SSD or Ultrabooks. The RAID that SRT uses is not correctly recognized by grub so it does not install correctly. And Ultrabooks use dual video and some auto switch and some manually switch so correct video settings may be an issue for both install and first boot.

How you boot install flash drive is how it installs, either UEFI or CSM/BIOS mode. And you really need both Windows & Ubuntu in same boot mode. 

Even some Windows 7 systems installed in BIOS mode have motherboards with UEFI and have to know to install in BIOS mode.

---

