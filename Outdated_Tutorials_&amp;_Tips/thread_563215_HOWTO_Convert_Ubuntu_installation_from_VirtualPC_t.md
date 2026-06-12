---
title: "HOWTO: Convert Ubuntu installation from VirtualPC to VMWare server"
date: 2007-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Phillip.Blenkinsopp on 2007-09-29
I have an Ubuntu 6.06 server installation that I've been running in Virtual PC (2004 + 2007) on a Windows host for a while. I had a few requests for copies of the installation for running in VMWare so I investigated converting my VM from Virtual PC to VMWare.

I used VMWare server as it’s free to download and run and has a pretty full set of features.

VMWare provides an import function to convert Virtual PC images into VMWare images but it only works if the guest OS is Windows. Attempting to use the importer on my VirtualPC/Ubuntu installation gave an error saying that boot.ini could not be found.

VMWare also have a standalone convertor program that claims experimental support for converting linux virtual machines from VirtualPC to VMWare but unfortunately this is only in the enterprise version of the convertor that has to be paid for.

I couldn't find any pointers on the web for how to do the conversion manually so I thought I'd post the method that I used. It was bitty, I used an Ubuntu LiveCD and SystemRescueCD LiveCD, I used a lot of disc space on the host and the exact method might not work for you, but hopefully it will save you some effort.

Virtual PC and VMWare Server simulate slightly different sets of hardware. I booted the Ubuntu 7.04 LiveCD in the VMWare environment and used lshw, lspci and lsmod in both environments to investigate the simulated hardware and modules needed. It turned out that VMWare wanted the following modules on top of the ones that were in use on Virtual PC:

agpgart
intel_agp
md_mod
mii
mptbase
mptscsih
mptspi
pci_hotplug
pcnet32
scsi_mod
sg
shpchp
vga16fb
vgastate

All of these modules were available in the Ubuntu 6.06 installation that I wanted to convert so they were not a problem. So on to the conversion.

The basic process is:
setup networking
transfer partitions from Virtual PC to host
create new VM in VMWare
transfer partitions from host to new VM
reinstall grub
boot new VM.

In more detail:

1. I installed the Windows loopback network adapter in the host to avoid sending the entire VM over a physical network. On XP the loopback adapter is installed from the Control Panel’s Add Hardware applet. When the wizard asks, click “Yes I have connected the hardware”.  Next select Add new hardware device from the Installed Hardware list. On the next page select Install the hardware that I manually select from a list.  When the list of device categories appears select Network Device, then Microsoft and Microsoft Loopback Adapter. You should now find that the host PC has an additional network adapter. Enable the adapter and it will give itself an IP address on the 169.254.x.x subnet, e.g. 169.254.178.211.

2. From Windows Explorer I shared a folder on the host (e.g. //169.254.178.211/share); this will be used to store images of the virtual PC hard disc contents.

3. From the Virtual PC settings dialogue I mapped the first network adapter of the VM to the newly created loopback adapter.

4. I booted the Virtual PC VM from the SystemRescueCD.

5. I configured the network adapter on the Virtual PC VM using “[FONT="Courier New"]ifconfig eth0 169.254.1.1[/FONT]”

6. In the Virtual PC VM I created a mount point for the shared host folder – “[FONT="Courier New"]mkdir /mnt/win[/FONT]”

7. In the Virtual PC VM I mounted the shared host folder
e.g.
 "[FONT="Courier New"]mount -t smbfs –o lfs,username=x,password=y //169.254.178.211/share /mnt/win[/FONT]"

8. I had two partitions in my VirtualPC image, /dev/hda5 containing /boot in an EXT3 filesystem and /dev/hda6 containing the rest of the system in an EXT3 filesystem on top of a logical volume called root on a volume group called Ubuntu. I copied /dev/hda5 to the host shared folder using "[FONT="Courier New"]dd if=/dev/hda5 bs=1024000 > /mnt/win/hda5[/FONT]"

9. I activated the logical volume with  "[FONT="Courier New"]vgchange –a y Ubuntu[/FONT]" and then copied /dev/Ubuntu/root to the host shared folder using "[FONT="Courier New"]dd if=/dev/Ubuntu/root bs=1024000 > /mnt/win/root[/FONT]". I’d planned to use partimage but I couldn’t get it to work with an LVM partition.

10. I now shutdown the Virtual PC VM.

11. I created a new VM in the VMWare environment making sure to select IDE discs for the new VM (VMWare offers IDE or SCSI, Virtual PC supports IDE only). I configured the VMWare networks and VM network adapter settings to allow the new VM and host to talk to each other directly.

12. I booted the SystemRescueCD LiveCD in the new VMWare VM and used parted to create partitions that matched those in my VirtualPC VM.
e.g. 
[FONT="Courier New"]parted
> mkpart logical 0 256MB 
> mkpart logical 256MB 3GB[/FONT]

13. On the VMWare VM I created a physical volume in the second new partition with "[FONT="Courier New"]pvcreate /dev/hda6[/FONT]"

14. On the VMWare VM I created a volume group containing the new physical volume, e.g. "[FONT="Courier New"]vgcreate Ubuntu /dev/hda6 -s 4MB[/FONT]"

15. On the VMWare VM I activated the volume group with "[FONT="Courier New"]vgchange -a y Ubuntu[/FONT]"

16. On the VMWare VM I created a logical volume with "[FONT="Courier New"]lvcreate -l715 -nroot Ubuntu[/FONT]". I now had an active logical volume to transfer my virtual PC image into.

17. On the VMWare VM I activated the network interface, e.g. "[FONT="Courier New"]dhcpcd eth0[/FONT]" (VMWare has a built in DHCP server).

18. On the VMWare VM I created a mount point for the shared host folder, e.g. "[FONT="Courier New"]mkdir /mnt/win[/FONT]"

19. On the VMWare VM I mounted the shared host folder, e.g.
"[FONT="Courier New"]mount -t smbfs -o lfs,username=x,password=y //169.254.178.211/share /mnt/win[/FONT]"

20. On the VMWare VM I transferred the stored partitions to the new VM, 
e.g.
[FONT="Courier New"]dd of=/dev/hda5 bs=1024000 < /mnt/win/hda5
dd of=/dev/Ubuntu/root bs=1024000 < /mnt/win/root[/FONT]

22. Finally I reinstalled grub on the new virtual hard disc (I did this from the Ubuntu LiveCD, I imagine that grub is on SystemRescueCD).
e.g.
[FONT="Courier New"]grub
> root (hd0,4)
> setup (hd0)[/FONT]

23. I then rebooted the VMWare VM and the brain transplant was complete!

Good luck.
Phil

---

