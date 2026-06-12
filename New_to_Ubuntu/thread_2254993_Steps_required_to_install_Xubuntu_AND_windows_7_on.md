---
title: "Steps required to install Xubuntu AND windows 7 on an old laptop"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by tillie on 2014-12-01
Hi everyone!

The computer of my girlfriend is becoming really slow, and I want to help her out by:

1. Reinstalling windows 7 with all her favorite programs and files + adding office package (that she doesn't have at the moment)
2. Installing Xubuntu, 
3. Making it possible for her to choose Windows or Xubutu on the start up, without having to press any buttons when starting up (because that would freak her out). 
4. Making it possible for her to use Chrome (including flash), Tixati (for downloading movies) and VLC player on her Xubuntu install. 
5. Letting her use the slower OS of Windows 7 for using microsoft office and other programs. 

The idea is that Xubuntu will be the fast OS, on which she can use internet and watch movies without it having to take ages, and that the Windows 7 OS can be used for professional work etc. 

**Is this possible?** I'm particularly worried about point 3. I really want her to be able to choose easily between the two OS's. 

Then some extra notes: the Xubuntu install doesn't need much space. Just 10 GB, of which at least 7 for files/downloads would be fine. 

**What would be the steps to do this?** Ofc I will provide extra information, e.g. hardware info etc. if necessary.

---

### Post by Gordonbp531 on 2014-12-01
The usual way is Windows first, then Xubuntu.
If the computer is UEFI enabled, then you should use the 64bit version of Xubuntu.

BTW, why should your GF have to use MS Office for "professional" work? Have you looked at the latest version of [LibreOffice]("https://www.libreoffice.org/")?

---

### Post by nerdtron on 2014-12-01
It's an old laptop, probably using the usual BIOS.

1-2
Just install windows 7 first. Then when you install Xubuntu, it should detect that windows 7 is installed and you will have and option to install alongside it.

3 - If the dual boot installation is successful, upon boot up you'll have the option to choose which OS to boot up, you'll press the arrow keys to choose and hit enter key to proceed.

4 - Sure. Just install Chrome and VLC in Xubuntu

5 - yes, Just install them in windows 7

---

### Post by tillie on 2014-12-04
> **Gordonbp531 said:**
> BTW, why should your GF have to use MS Office for "professional" work? Have you looked at the latest version of [LibreOffice]("https://www.libreoffice.org/")?

I'm aware of Libre Office and have worked with Linux. Unfortunately I personally feel it's no match next to Microsoft Office, but yes, indeed, on the Xubuntu install she will be able to use Libre Office.

---

### Post by sandyd on 2014-12-04
> **tillie said:**
> Hi everyone!

The computer of my girlfriend is becoming really slow, and I want to help her out by:

1. Reinstalling windows 7 with all her favorite programs and files + adding office package (that she doesn't have at the moment)
2. Installing Xubuntu, 
3. Making it possible for her to choose Windows or Xubutu on the start up, without having to press any buttons when starting up (because that would freak her out). 
4. Making it possible for her to use Chrome (including flash), Tixati (for downloading movies) and VLC player on her Xubuntu install. 
5. Letting her use the slower OS of Windows 7 for using microsoft office and other programs. 

The idea is that Xubuntu will be the fast OS, on which she can use internet and watch movies without it having to take ages, and that the Windows 7 OS can be used for professional work etc. 

**Is this possible?** I'm particularly worried about point 3. I really want her to be able to choose easily between the two OS's. 

Then some extra notes: the Xubuntu install doesn't need much space. Just 10 GB, of which at least 7 for files/downloads would be fine. 

**What would be the steps to do this?** Ofc I will provide extra information, e.g. hardware info etc. if necessary.
[LIST=1]
[*]When installing Windows 7, make sure you create a partition (or just leave space) for Ubuntu. You can do it after installation in Control Panel -> Administrative Tools -> Computer Management -> Disk Manager if you wish
[*]Install Xubuntu in the partition (or free space) you created during the installation, or manually through disk manager. Select 'Custom Install' when partitioning, and you can fiddle with the space for each of the partitions there
[*]Grub has a nice menu that allows you to select using up/down arrow keys. LILO kind of does the same
[*]
[LIST]
[*]Chrome - yes (just go to the chrome site and install), 
[*]VLC - yes (Go to the software center and install)
[*]Tixati - go to [http://www.tixati.com/download/linux.html](http://www.tixati.com/download/linux.html), download and install 64-bit Normal Install .deb File. Transmission works quite well as a minimal torrent client as well
[/LIST]
[*]Handled by grub
[/LIST]


Side note #1: I suggest backing up before tinkering
Side note #2: I dont know if her laptop can handle it, but try setting up a Windows 7 Virtualbox VM and seeing if it can run her programs without lagging heavily

---

### Post by mastablasta on 2014-12-05
> **Gordonbp531 said:**
> 
BTW, why should your GF have to use MS Office for "professional" work? Have you looked at the latest version of [LibreOffice]("https://www.libreoffice.org/")?

I have and no it is still quite far away from MS office, and at the same time compatibility is quite rubbish (aside from writer where it is quite descent).

> **tillie said:**
> 

**Is this possible?** I'm particularly worried about point 3. I really want her to be able to choose easily between the two OS's. 

Grub will still require to select the OS and press a key. I hope that won't cause her any panic attack :P

> 
Then some extra notes: the Xubuntu install doesn't need much space. Just 10 GB, of which at least 7 for files/downloads would be fine. 

I would say give it at least 20-25 GB. 10 GB is really small (unless she will do all the work in CLI only :) ). with 10 GB install you will be left with about 2-3 GB free on install. but that will fill up after system updates and if you install programs. and if you save any data (e.g. downloads). anyway you will soon reach the 10 GB mark. also create a separate "data" partition NTFS formatted that will be used to store data from Linux as well as from windows.
> 
**What would be the steps to do this?** Ofc I will provide extra information, e.g. hardware info etc. if necessary.

might be a good idea. they are always interesting to read. if windows 7 is on relatively new hardware with enough ram (4GB) there is no good reason for it to be slow. I suggest installing good antivirus protection there (say a firewall such as Comodo and maybe some antivirus such as avast or avira)


and finally I doubt anyone would boot into linux after work just to do a bit of surfing. the boot just takes longer than launching browser. again with enough ram on win7 and good install Linux might be better option in virtualbox as a very safe browsing machine.

---

