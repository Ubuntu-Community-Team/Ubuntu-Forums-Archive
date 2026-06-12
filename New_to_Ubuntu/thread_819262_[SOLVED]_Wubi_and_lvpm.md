---
title: "[SOLVED] Wubi and lvpm"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-06-05
Hi All,'

When I installed ubuntu I used wubi...selected the 15 gig option but now would like to extend it to 30 gigs. 

Checked in the wubi section and someone recommended lvpm. Downloaded it and selected the option to increase the boot size...rather brief ...it shows increase to 5000..what number should I pick to get my 30 gigs.

Another thing when I choose to cancel it would not...had to finally go to restart to get window to close.

Anyone have any exp with program ?

Bikinguy

---

### Post by chrisdugdale on 2008-06-05
Backup your data before working with partitions! Easy way to work with partitions :: you can just boot into Ubuntu and use the System>Administration>Partition Editor to alter partitions any time. If it's not there in the list, use System>Administration>Synaptic Package Manager;  search for gparted and check mark it. Then click Apply on the toolbar. That will add Partition Editor to your menu as above. 

The lvpm is a mystery to me somewhat, though I can work it out when i must use it, I've no suggestions about that way to change things tonight.

---

### Post by bikinguy77388 on 2008-06-05
Hi All,

After googling it this app appears to be geared towards turning a virtual install into a stand alone install.

Any input on this ?

thanks,
bikinguy

---

### Post by bikinguy77388 on 2008-06-05
Chris,

I am gonig to leave this alone at this time. Does not appear to extend the virtual size just converts to a regular install.

bikinguy

---

### Post by chrisdugdale on 2008-06-05
I read that this is what happens. In wubi I know you can remove the Ubuntu stuff just by running a normal remove (Control Panel>Add/Remove Programs) under windows. That should let you then just reinstall by popping the Live cd in while windows is running. Make sure you reboot after uninstalling. Then you can just start from where you started. Sorry, wasn't clear that you hadn't done a hard disk install. Running under Wubi doesn't actually partition your hard disk or change the setup at all.

---

### Post by Paqman on 2008-06-05
> **bikinguy77388 said:**
> Chris,

I am gonig to leave this alone at this time. Does not appear to extend the virtual size just converts to a regular install.

bikinguy

No, LVPM can do both. Have a read of [this page](http://lubi.sourceforge.net/lvpm.html). You want the part about "Resizing virtual disks using LVPM"

---

