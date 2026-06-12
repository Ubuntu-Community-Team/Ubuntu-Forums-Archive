---
title: "Help to install please!"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by Toni_Vines on 2013-10-05
Hi! I'm absolutely new to this so bear with me please! I have Mint 15 installed on an old AMD machine and it has problems with Cinnnamon. I have Ubuntu 13.04 i386 on a DVD and want to install this replacing Mint. The DVD is designed to run from Windows so I have no idea how to get it to work here. Can this be done or do I need to download a different version? I'm hoping I can get it to work from the terminal. Could anyone guide me through the process please? Remember, I've never done this before so be gentle with me! 
Thanking you,
Toni Vines.

---

### Post by heir4c on 2013-10-05
Welcome to the forum,

First give some info about your hardware. CPU, RAM, Graphics Card.
Then: Better to use is the 12.04 version. That's the LTS (Long Term Support of 5 years), because the versions between the LTS versions (every 2 years) are limited in support.
Can you boot up with the DVD? (you have installed Mint so do the same) 
How more info you give how better people can help.
ThanX

---

### Post by coldraven on 2013-10-05
Can you tell us more about the PC? If it is old then Ubuntu 13.04 might not run very well, it uses a lot of resources.

---

### Post by Bashing-om on 2013-10-05
Toni_Vines; Hi ! Welcome to the forums.

As you advise "old AMD machine and it has problems with Cinnnamon." Let us not even consider the flagship editions of ubuntu;
Rather consider versions of 'buntu that use less resources - I like lubuntu.
Process:
Lubuntu availability -> top of thread tool -> "ubuntu Community" -> Get Lubuntu -> follow down load instructions;
Burn the .iso image to CD;
Verify the integrity of the .iso file; (md5sum)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Set in bios to boot the cd drive as the 1st boot priority;
Boot the install(live)CD to "try ubuntu" mode;
Play around with Lubuntu, testing that all performs as expected, and you like that desk top;
Hit the install icon on the desk top -> answer a few simple set up questions ->
- Need to Have a wired inter net connection -
20 minutes and you are up and running on Lubuntu !

This is using the install wizard to take care of installing a standard install to the hard drive as you choose;
Stand alone Lubuntu ,, at the install screen choose "install Lubuntu erasing entire disk" The installer will do just that .. wipe the hard disk and install only Lubuntu onto that selected hard disk. No fuss, no muss over and done with ! 

This I think is the better install for a new beginner. Once you are aware and want/need to make alterations in the way 'buntu is installed you will have attained the knowledge to do else as you want.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by newb85 on 2013-10-05
Agreed.  Cinnamon is based on Gnome 3, which needs basically the same resources as Unity (used in Ubuntu).

If you like Mint, though, you should consider the Mate version of Mint.  Mate is based on Gnome 2, which will have similar resource requirements to LXDE (used in Lubuntu).

---

### Post by Toni_Vines on 2013-10-05
Thank you all for your input. Here is what I've got: My machine is an old AMD Athlone. 0.5 gig RAM, Graphics card is Intel 82740 (i1740). APG graphics accelerator.
I think I will go with newb85's advice and try Mate.
Cheers,
Toni.

---

### Post by Bashing-om on 2013-10-05
Toni_Vines;
With 512 megs of ram .. that will "run" .. not real well, but should run. Is that box's ram expandable ? You will see a remarkable difference with more ram installed. Now-a-days Ram chips are cheap.

[INDENT][INDENT]the more the merrier 
[/INDENT][/INDENT]

---

### Post by Rob Sayer on 2013-10-06
Mint with the Mate desktop won't run well in a 1/2Gb machine either.  I tried it on a 1Gb netbook.  It was *pitiful*. 

While most Mint versions are ubuntu based, their tech support is awful  compared to ubuntu's.  I would not recommend mint to relatively  inexperienced users for that reason.

I haven't tried lubuntu but I have tried xubuntu with the xfce desktop.  It may work in 1/2Gb.  I'd probably recommend lubuntu as well.

You often get people here with problems installing/using linux on older machines with limited RAM.  They've heard you can run linux better with a small memory space, I guess.

Unfortunately, what they didn't hear is that technically linux is just the kernel.  Which does indeed run in a small space.  But the desktop user interface that most linux distros use does not run in a small space.

For example, I installed ubuntu with the unity desktop ... which I would also expect to work like mint w/cinnamon as far as hardware usage goes ... on a 4Gb i3 based laptop.  I yanked it.  Too dang slow.  I wouldn't consider unity/cinnamon on my 1Gb netbook ... running kubuntu just fine with some speedier settings ... period.

---

### Post by wubiNathan on 2013-10-06
Have you tried LXDE at all?

Once again, I recommend Lubuntu or Xubuntu.  Uniity isvery Graphics-heavy, so it even runs slow on my 4gb machine. (however, I dont think it was unity)

Download Lubuntu at [http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso), Burn it to a DVD, and install.  it should work fine.

---

### Post by Toni_Vines on 2013-10-06
OK, I have Lubuntu iso on a CD. I have two options, I can install it alongside XP on this machine and I can also install it on my other machine that has Mint on it. Firstly, My other machine does not have a bootable CD tray so can I install it and wipe Mint from the terminal window? And on this machine I've started the install process but hit a problem in that it required me to set up the partition alongside XP. I have no idea how to do this I'm afraid! 
Thanking you,
Toni.

---

### Post by Bashing-om on 2013-10-06
Toni_Vines; Better late than never !

What is your position now ? .. As you have chosen to install alongside, should have no problem. The installer is smart and the install wizard, I expect, will take care of everything for a standard dual boot with Windows.

Additional advise is pending.

[INDENT][INDENT]you can do this too
[/INDENT][/INDENT]

---

### Post by Toni_Vines on 2013-10-07
I have Mint 15 installed on an old AMD computer and I wish to change this for Lubuntu. Unfortunately this computer does not have a bootable CD drive. Is there any way out of this please? 
Thanking you,
Toni. 
P.S. My computer spec is: AMD Athlone XP2000, 0.5 gig RAM, Intel 82740 APG graphics.

---

### Post by ibjsb4 on 2013-10-07
I have never used it

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=net+boot&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=net+boot&sa=Search&cof=FORID:9)

What is the make and model of your computer?

---

### Post by Lars Noodén on 2013-10-07
If you can boot from USB, you could try installing from a USB stick:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you can't boot from USB, even after fiddling with the BIOS, your remaining option would be PXE boot also known as netboot.

---

### Post by mörgæs on 2013-10-07
Another option is moving the hard disk to another computer, install there and move it back.

---

### Post by howefield on 2013-10-07
Threads merged.

---

