---
title: "Ubuntu install will not work."
date: 2012-06-07
forum: New to Ubuntu
---

### Post by biokuk on 2012-06-07
Sorry to be a pain here but as an absolute beginner I'm trying to get Ubuntu to simply work on a separate, dedicated machine, and I get problems on boot. It just doesn't work. Both version 10/ something and the latest 12/ something. Both versions work fine off the live CD. I install it and nothings happening, it locks up/freezes on the boot procedure.

Yet, I install XP Pro and that boots no problem. I ask a Q elsewhere on these forums and get one answer, which didn't help much. (But thanks anyway, guy.) 

What do I need to do to get some concrete help, plz?

I'm looking at Mint currently....

---

### Post by arochester on 2012-06-07
How much RAM (memory) do you have?

Have you tried the Alternate disk, instead of the Desktop Disk? It is just an install and works with much less memory.

---

### Post by traditionalist on 2012-06-07
> **biokuk said:**
> Sorry to be a pain here but as an absolute beginner I'm trying to get Ubuntu to simply work on a separate, dedicated machine, and I get problems on boot. It just doesn't work. Both version 10/ something and the latest 12/ something. Both versions work fine off the live CD. I install it and nothings happening, it locks up/freezes on the boot procedure.

Yet, I install XP Pro and that boots no problem. I ask a Q elsewhere on these forums and get one answer, which didn't help much. (But thanks anyway, guy.) 

What do I need to do to get some concrete help, plz?

I'm looking at Mint currently....

Some things don't work on some machines for various reasons.  You need to post some information about your machine before anybody can give you sensible help, for instance;

System =  Ubuntu 12. 04 Precise pangolin 64 BIT.

Machine = Motherboard or machine type?
Graphics = Graphic card or integrated graphics?
RAM =  How much RAM
Desktop Environment = ?  For instance, GNOME Classic

Or something like this

[[IMG]http://img534.imageshack.us/img534/5209/selection017.th.png[/IMG]]("http://img534.imageshack.us/i/selection017.png/")

---

### Post by steeldriver on 2012-06-07
people tried to help you in your previous thread and you didn't respond

[http://ubuntuforums.org/showthread.php?p=11989001#post11989001](http://ubuntuforums.org/showthread.php?p=11989001#post11989001)

like oldfred said in the previous thread, we need more info from you in order to help

---

### Post by biokuk on 2012-06-07
Thanks for your fast reply: )
Have 1GB ram on new machine.(soon to be upgraded)

'Alternate disc' I know nothing about. I simply downloaded the appropriate files, burnt them to CD, whatever, and tried installing. Seemed to install OK, but wouldn't boot successfully.

I've got Ubuntu working fine on my main machine, in a 13GB partition. So I get another PC, thinking that a dedicated Ubuntu machine would be really good. But nothing is working yet. Except off the CD. And XP Pro, which proves the PC is OK I presume, but that's exactly what I am trying to escape from: )

---

### Post by traditionalist on 2012-06-07
> **biokuk said:**
> Thanks for your fast reply: )
Have 1GB ram on new machine.(soon to be upgraded)

'Alternate disc' I know nothing about. I simply downloaded the appropriate files, burnt them to CD, whatever, and tried installing. Seemed to install OK, but wouldn't boot successfully.

I've got Ubuntu working fine on my main machine, in a 13GB partition. So I get another PC, thinking that a dedicated Ubuntu machine would be really good. But nothing is working yet. Except off the CD. And XP Pro, which proves the PC is OK I presume, but that's exactly what I am trying to escape from: )

That is not enough information to give you any help.

What sort of machine is it?

---

### Post by biokuk on 2012-06-07
OK. Hands up! I didn't clock the responses to my original Q. Was expecting email prompts... Apologies to the respondents.

Point is I don't know very much about my current 'new' machine because I can't get online and do a Belarc audit for example. I know it is an AMD M/B, Winfast from 2007 with 160GB Hard drive and 1 GB ram. But not much more right now.

I try to add a pic of the innards here.[IMG]http://i1212.photobucket.com/albums/cc459/bicyclz/DSCN0352.jpg[/IMG]

At least you can see the fan is working: )
If not my newbie brain yet....

---

### Post by steeldriver on 2012-06-07
hi biokuk - since you can boot OK with the LiveCD you could do that and then open a terminal and type

```
sudo lshw -short > ~/myhardware.txt

```

then you can open that file and copy and paste the results here so we can see if there are any red flag hardware components

---

### Post by traditionalist on 2012-06-07
> **steeldriver said:**
> hi biokuk - since you can boot OK with the LiveCD you could do that and then open a terminal and type

```
sudo lshw -short > ~/myhardware.txt

```then you can open that file and copy and paste the results here so we can see if there are any red flag hardware components

He wont know how to do that!

That command line produces a file called "myhardware.txt"  in your home folder. You can open it with a normal text editor.

It should look like this;

[[IMG]http://img96.imageshack.us/img96/3690/selection025.th.png[/IMG]]("http://img96.imageshack.us/i/selection025.png/")


When you copy and paste it here, it looks like this;


H/W path                Device      Class       Description
===========================================================
                                    system      P55A-UD7 ()
/0                                  bus         P55A-UD7
/0/0                                memory      128KiB BIOS
/0/4                                processor   Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
/0/4/a                              memory      64KiB L1 cache
/0/4/b                              memory      8MiB L2 cache
/0/16                               memory      8GiB System Memory
/0/16/0                             memory      2GiB DIMM 1333 MHz (0.8 ns)
/0/16/1                             memory      2GiB DIMM 1333 MHz (0.8 ns)
/0/16/2                             memory      2GiB DIMM 1333 MHz (0.8 ns)
/0/16/3                             memory      2GiB DIMM 1333 MHz (0.8 ns)
/0/100                              bridge      Core Processor DMI
/0/100/3                            bridge      Core Processor PCI Express Root Port 1
/0/100/3/0                          bridge      NF200 PCIe 2.0 switch
/0/100/3/0/0                        bridge      NF200 PCIe 2.0 switch
/0/100/3/0/0/0                      display     Cypress LE [Radeon HD 5800 Series]
/0/100/3/0/0/0.1                    multimedia  Cypress HDMI Audio [Radeon HD 5800 Series]
/0/100/3/0/2                        bridge      NF200 PCIe 2.0 switch
/0/100/3/0/2/0                      bridge      PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
/0/100/3/0/2/0/1                    bridge      PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
/0/100/3/0/2/0/1/0      scsi6       storage     88SE9128 PCIe SATA 6 Gb/s RAID controller
/0/100/3/0/2/0/1/0/0    /dev/sdc    disk        60GB ADATA SSD S599 6
/0/100/3/0/2/0/1/0/0/1  /dev/sdc1   volume      55GiB EXT4 volume
/0/100/3/0/2/0/1/0/1                processor   SCSI Processor
/0/100/3/0/2/0/5                    bridge      PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
/0/100/3/0/2/0/5/0                  bus         uPD720200 USB 3.0 Host Controller
/0/100/3/0/2/0/7                    bridge      PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
/0/100/3/0/2/0/9                    bridge      PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
/0/100/3/0/3                        bridge      NF200 PCIe 2.0 switch
/0/100/8                            generic     Core Processor System Management Registers
/0/100/8.1                          generic     Core Processor Semaphore and Scratchpad Registers
/0/100/8.2                          generic     Core Processor System Control and Status Registers
/0/100/8.3                          generic     Core Processor Miscellaneous Registers
/0/100/10                           generic     Core Processor QPI Link
/0/100/10.1                         generic     Core Processor QPI Routing and Protocol Registers
/0/100/1a                           bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1a.1                         bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1a.2                         bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1a.7                         bus         5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1b                           multimedia  5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                           bridge      5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c/0             eth0        network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2                         bridge      5 Series/3400 Series Chipset PCI Express Root Port 3
/0/100/1c.2/0                       storage     JMB363 SATA/IDE Controller
/0/100/1c.2/0.1                     storage     JMB363 SATA/IDE Controller
/0/100/1c.3                         bridge      5 Series/3400 Series Chipset PCI Express Root Port 4
/0/100/1c.3/0                       storage     JMB363 SATA/IDE Controller
/0/100/1c.3/0.1                     storage     JMB363 SATA/IDE Controller
/0/100/1d                           bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.1                         bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.2                         bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.3                         bus         5 Series/3400 Series Chipset USB Universal Host Controller
/0/100/1d.7                         bus         5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                           bridge      82801 PCI Bridge
/0/100/1e/6                         bus         TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
/0/100/1f                           bridge      5 Series Chipset LPC Interface Controller
/0/100/1f.2             scsi0       storage     5 Series/3400 Series Chipset 6 port SATA AHCI Controller
/0/100/1f.2/0           /dev/cdrom  disk        DVDRAM GH24LS50
/0/100/1f.2/1           /dev/sda    disk        1TB SAMSUNG HD103SI
/0/100/1f.2/1/1         /dev/sda1   volume      931GiB EXT4 volume
/0/100/1f.2/0.0.0       /dev/sdb    disk        1TB SAMSUNG HD103SI
/0/100/1f.2/0.0.0/1     /dev/sdb1   volume      9538MiB Linux swap volume
/0/100/1f.2/0.0.0/2     /dev/sdb2   volume      922GiB EXT4 volume
/0/100/1f.3                         bus         5 Series/3400 Series Chipset SMBus Controller
/0/101                              bridge      Core Processor QuickPath Architecture Generic Non-Core Registers
/0/102                              bridge      Core Processor QuickPath Architecture System Address Decoder
/0/103                              bridge      Core Processor QPI Link 0
/0/104                              bridge      Core Processor QPI Physical 0
/0/105                              bridge      Core Processor Integrated Memory Controller
/0/106                              bridge      Core Processor Integrated Memory Controller Target Address Decoder
/0/107                              bridge      Core Processor Integrated Memory Controller Test Registers
/0/108                              bridge      Core Processor Integrated Memory Controller Channel 0 Control Registers
/0/109                              bridge      Core Processor Integrated Memory Controller Channel 0 Address Registers
/0/10a                              bridge      Core Processor Integrated Memory Controller Channel 0 Rank Registers
/0/10b                              bridge      Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
/0/10c                              bridge      Core Processor Integrated Memory Controller Channel 1 Control Registers
/0/10d                              bridge      Core Processor Integrated Memory Controller Channel 1 Address Registers
/0/10e                              bridge      Core Processor Integrated Memory Controller Channel 1 Rank Registers
/0/10f                              bridge      Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
/0/1                    scsi22      storage     
/0/1/0.0.0              /dev/sdd    disk        Ultra HS-SD/MMC
/0/1/0.0.0/0            /dev/sdd    disk

---

### Post by biokuk on 2012-06-08
Sorry you guys but it's all 'Double Dutch' to me. (Excuse me my good Dutch friends.)

I've spent weeks on this, and bought a 'new' 'old' PC to do it on. IE a dedicated Linux PC. I'm getting nowhere with Ubuntu and Suse and the forums ain't helping, for whatever reason. Me just a beginner with Linux, but trying my best.

Right now a £100 or whatever Windows 7 OS looks very good to me. Works out of the box as they say. (I presume) Without having criticism from people who know a lot more than me for simply asking innocent Qs about Ubuntu. I thought Ubuntu etc. was for people trying to escape the MS stranglehold on OS's. 

Escape doesn't work for me anyway. Not being a Houdini I will now buy the MS OS and at least be confident that it works... Without being looked down on by Ubuntu forums bitchers about newbies, who after all are beginners, and know nothing much when they start. This is a salutary lesson for me.

John.

---

### Post by QIII on 2012-06-08
John --
 
You are not being looked down apon. You are being asked questions that will help people sort out your issues. We cannot make guesses in the dark or conjure magical solutions. We need the information to begin to understand the issue.
 
The same questions are asked on Windows help forums -- since Windows doesn't just "always work" either.
 
If you are told something that is just double Dutch to you, ask for an explanation. You have every right to. You should not be greeted with any "Linux snobbery". 
 
So, right now, we have to work out what hardware you have. A method for doing that was presented. If you do not understand how to accomplish it, simply ask for clarification. We are all human. We tend, as all humans do, to give answers that make perfect sense to us but may be obscure or confusing to others. It is nobody's intent to be aloof.  You get answers you understand with Windows because you are familiar with Windows and the answers make general sense without further explanation.  You are not familiar with Linux, and we don't expect you to be.
 
I think traditionalist did a fair job of explaining the task. Could you please attempt the suggestion and provide us some feedback? You do not need to know what all the gibberish in that file means. We do.

---

