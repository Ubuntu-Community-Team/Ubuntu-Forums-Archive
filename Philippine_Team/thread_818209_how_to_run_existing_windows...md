---
title: "how to run existing windows?.."
date: 2008-06-04
forum: Philippine Team
---

### Post by butchoy on 2008-06-04
nadis-kubre ko ang virtualbox nung isang araw... meron bang paraan na pwede kong i-run ung existing windows ko sa loob ng virtualbox? ayaw ko na kasing mag-install...... thanks...

---

### Post by benhur99ph on 2008-06-06
Hmmm... di ko po masyado ma-gets ang question mo. Are you saying that naka-dual boot ka at gusto mo i-run ung isang boot option mo, which is windows on your ubuntu via virtualbox?

I think, its not possible, but I might be wrong. Anyway, kasi ang setup ko ngaun eh Ubuntu ang primary OS ko and I run Winxp using Virtualbox. So far naman satisfied ako sa performance --- especially using the "seamless mode". 

I suggest na, install mo nalang via virtualbox... mas madali kasi.. pede mo i-backup ung image ng Virtual machine mo, so anytime na masira mo ang windows mo... pede mo sya ulit i-run kasi may backup ka... no hassles..

---

### Post by pendletone on 2008-06-07
Hi butchoy! Hindi mo pwedeng i-run ang existing windows installation mo sa virtualbox coz virtualbox stores its virtual machines in single VDI files (and its contents in XML), as opposed to a normal windows installation which consists of thousands of files that are not contained inside a VM. In order to run a windows VM, you have to create a virtual machine first and *install* windows inside it. In short, you really have to install windows inside a virtual machine.

Hope that helps! :)

---

### Post by jeffimperial on 2008-06-07
> **butchoy said:**
> nadis-kubre ko ang virtualbox nung isang araw... meron bang paraan na pwede kong i-run ung existing windows ko sa loob ng virtualbox? ayaw ko na kasing mag-install...... thanks...

Kung ang naka-install na Virtualbox mo ay 1.5.0, pwede mong gawin ang iniisip mo. Kailangan mong in-run ang vbox using a separate physical partition. That would entail creating a .VMDK file.
A nice howto here -->[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

Pero pwede mo 'tong gawin gamit ang [VMServer]("http://www.vmware.com/products/server/") (free). Meron syang virtualizer program (also free) na gagawa ng kopya ng pre-existing OS mo sa loob ng VMserver.

---

