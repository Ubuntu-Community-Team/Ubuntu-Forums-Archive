---
title: "Dual Booting w/ Crypto"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by mevets on 2008-07-03
So I have decided I wanted to encrypt my Linux partition when I heard about airports doing searches of laptops in the US (seriously, what the hell). I know the alternate installer offers the option to encrypt you / partition. It then asks you for the password during boot. This is the solution I am looking for, not a truecrypt one. The only way to have the alternate installer, as far as I can tell, setup an install with crypto is if you agree to wipe the entire disk and use guided partitioning. This isnt going to play well if I planned on dual booting and had windows already installed and just wanted to resize the NTFS partition. When I tried to troubleshoot this problem I figured I could erase the entire disk and setup linux with crypto, then reboot to a liveCD and resize the crypto root partition enough to fit windows on the left over space. Then install Windows, it would ruin the MBR, but I'd later go in and hopefully run a tool to restore it.

The problem with this plan is that I dont think that I can resize the encrypted partition. So, what is the best way of going about setting up a win/linux dual boot w/ linux encrypted?

---

### Post by hyper_ch on 2008-07-03
> **mevets said:**
> So I have decided I wanted to encrypt my Linux partition when I heard about airports doing searches of laptops in the US (seriously, what the hell).
When entering the US and you still have windows on it, I also recommend to
(1) set teh grub timeout to "0"
(2) boot by default the Windows install

Rationale: Very likely the people at the airport aren't that savy. Hence you show them a notebook that has a normal windows installation... they might look for some files on there (so maybe put some family pictures on there... maybe a few other docs and stuff...

so if they find nothing on the "normal" windows installation, it's very likely they won't even check if there is another OS installed...

Well, I have not tested it but I know enough people that think that Windows is the only thing on a computer ;

> **mevets said:**
> The only way to have the alternate installer, as far as I can tell, setup an install with crypto is if you agree to wipe the entire disk and use guided partitioning.
Nope... there are other options also... it might be that you need to manually partition.

In that case you will need to create at least 3 partitiones, maybe 4...

(1) swap --> just make a partition for it.... don't put any file format or anything on it
(2) boot --> make it about 100mb... that should be able to hold 4-5 kernels... use as filesystem ext3 and mountpoint /boot and set the bootable flag to on
(3) root --> size depends whether you want to setup a seperate home (recommended). 10 GB should be enough... I have enough space so I make mine 30 GB (one never knows....) see here as example:
[IMG]http://www.sjau.ch/bug_231451/03root.png[/IMG]
(4) /home --> see point (3)

once you get back to the main partition menu, select on top to "configure encrypted volumes
[IMG]http://www.sjau.ch/bug_231451/04configure.png[/IMG]

that will then format the encrypted partitions and setup an initial password.

After that, you will notice in the main partition menu that you have new devices there... select the new "root" partition, make it to ext3 and mountpoint "/".... then select the new "home" partition, make it to ext3 and mountpoint "/home" --> this will take some time.

then go on with "finish partitioning and writing changes to disk". 

you will get a warning about swap - which you can ignore and just continue...

the reason why we skip swap here is because of a bug ( [https://bugs.launchpad.net/ubuntu/+bug/231451](https://bugs.launchpad.net/ubuntu/+bug/231451) ) but we can setup swap later on manually ;)

So, that will now create an "unused" swap partition, an unencrypted "/boot" partition (bootable), an encrypted "/" partition and an encrypted "/home" partition.

Once that works, you can generate a keyfile, add the keyfile to the /home partition and then have it auto-uncrypted with it, so that at boot time you only have to enter the password once.

The encrypted swap is also fairly to setup then...

I'll probably write a complete guide later on ;)

---

### Post by mevets on 2008-07-03
Thanks for the extensive guide! I didnt realize encrypted was an option under Use as. Thanks!

---

