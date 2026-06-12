---
title: "Linux ubuntu install with VMware player"
date: 2005-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by abuelo on 2005-12-07
I started playing around with the free VMware player a week ago on Windows XP. You can download the player and a Pre-built Browser Appliance Virtual Machine from here: [http://www.vmware.com/download/player/]("http://www.vmware.com/download/player/"). The Vmware player and Pre-built  Appliance Virtual Machine install easily. The Browser Appliance gave me my first taste of Ubuntu. I liked it so much, I had to get a whole working system going. I downloaded the latest iso via BitTorrent, modified* a vmx file from [http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html]("http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html") and generated a vmdx file (instructions found on johnbokma's page also). After burning a CD with the iso installation file and copying the vm* files to a USB HD, I was ready to go. I doubled clicked on the vmx file and Linux Ubuntu started installing into the VM from the CD! Most VM's that I have seen are about 2GB. That was the default value for this vmx file. I choose 17.2 GB because I wanted some space to work. I would not consider anything less that 8 GB. Everything works perfectly on my Toshiba 6100 portable. Please note that I used 256 MB of RAM in the vmx file because It's half of the 512 MB that I have. 

Side note:

I had a different distribution of Linux installed with a dual boot lilo before. This Linux installation gave me many problems and I was scared to remove it. Finally, I tried and wiped out the lilo. and couldn't boot either system from the HD. After booting from a floppy into Windows I had to fix my MBR (risky business). This is why I like the VM some much. I have the a safety blanket to learn. Tomorrow I will burn a DVD with the whole VM as a backup (3.6 GB). Review and modify the vmx file as needed.

* vmx file:

config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Ubuntu.vmdk"
memsize = "256"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "ubuntu-5.10-install-i386.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.present = "FALSE"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Ubuntu"
guestOS = "ubuntu"
nvram = "Ubuntu.nvram"
MemTrimRate = "-1"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 5c cc 3d 4a 43 29-55 89 5c 28 1e 7e 06 58"
uuid.bios = "56 4d 5c cc 3d 4a 43 29-55 89 5c 28 1e 7e 06 58"
ethernet0.generatedAddress = "00:0c:29:7e:06:58"
ethernet0.generatedAddressOffset = "0"

tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"

uuid.action = "create"

checkpoint.vmState = ""


Thanks to the Ubuntu community for such a great Linux distribution!

Abuelo.

Edit1:

If the VMware player doesn't see the file, add the CD ROM drive letter as such:

ide1:0.fileName = "h:\ubuntu-5.10-install-i386.iso". I just had this problem with a dapper install.

---

