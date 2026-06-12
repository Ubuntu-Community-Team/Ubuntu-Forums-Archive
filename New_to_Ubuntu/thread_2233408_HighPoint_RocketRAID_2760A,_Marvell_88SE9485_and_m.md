---
title: "HighPoint RocketRAID 2760A, Marvell 88SE9485 and mvsas issues"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by colin20 on 2014-07-08
I have a HighPoint RocketRAID 2760A card that I'm having a few issues with. The card is supposed to use Marvell 88SE9485 chips which from my understanding of it should be supported by the mvsas driver in the Linux kernel. From what I gather online others using this card or those chips have had more of a smooth plug and play experience. I'd tried quite a few different Ubuntu and Kernel versions and each time I experience the same issue. I can see the drives connected to the cards with lsblk but if I try to interact with them then I get a variety of errors depending on which drive I try to access. The drives and backplane themselves appear to be functional as I can access to a few drives at a time by connecting the an SFF 8087 connector directly to the motherboard.

**Solution**

The issue was that I was using RocketRAID 276x Controller BIOS v1.1 and 4TB hard drives. I found the most recent version of the BIOS at "http://www.highpoint-tech.com/USA_new/CS-PCI-E_2_0_x16_Configuration.html" which has a Readme.txt which details:

   v1.3 10/29/2012
       * Fixed a compatibility issue with some SAS HDDs. 
       
   v1.2 04/20/2012
       * Support over 2TB HDD.
       * Create Array with "Keep old data" as default.       
   
   v1.1 09/08/2010
       *Support RR2760A.
       *Fix crash problem when there're more disks to create RAID10/RAID50.
       *Modify RR2760A crash problem when create RAIDs.    
       *Fix cannot boot problem after create RAID in setup.
       *Fix cannot find the first channels problem while cold boot.

   v1.0 04/26/2010
       * First release.

If it was having an issue with the drives being over 4TB then I'd expect  some indication of that such as listing the drives as being of an  unsupported size but there was none. Although the drives appeared to be fine in the card's BIOS and were correctly detected as being 4TB they were not working properly with the v1.1 BIOS.

After downloading the current latest firmware from "http://www.highpoint-tech.com/BIOS_Driver/RR276x/bios/RR276x-BIOS-v1.3-121029.zip" I learned that I needed to install it with DOS.

I downloaded FreeDOS from "http://www.freedos.org/download/download/fdbasecd.iso" and UNetbootin from "http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe". I used Unetbootin to create a bootable FreeDOS USB and copied the BIOS files to it. After booting to the USB I selected the fdos option. The drive booted into A but the contents of the USB were on C. After changing to the directory that the BIOS update files were in running go.bat resolved this problem.

---

