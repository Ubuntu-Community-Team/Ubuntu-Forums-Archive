---
title: "Wi Fi installation (without LAN)"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by teejavus on 2011-09-22
Just installed Oneiric Beta 1.

I have a broken lan port, so cannot connect to the network.

The network icon shows 

Wireless Networks
device not ready (firmware missing) 


Any suggestion to help me fix it ?

---

### Post by ratcheer on 2011-09-22
Run "sudo lspci -v" to determine the make and model of your wireless adapter. Then, you may be able to find the firmware and driver on the chipset maker's web site. If you do find what you need, installation instructions should come with it.

Tim

---

### Post by teejavus on 2011-09-23
Tried installing the deb files :
firmware-b43-installer:

dep :  b43-fwcutter (1:013-2)  

when i tried installing  b43-fwcutter (1:013-2) , the software central kept crashing

so installed  b43-fwcutter (1:013-2) from terminal, but firmware-b43-installer kept trying to connect to download : broadcom-wl-4.150.10.5.tar.bz2 which i had to download separately

unpacked the archive to find the wl_apsta_mimo.o file, and from that directory ran

sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o

followed by 

modprobe b43 

and voila it worked :)

---

