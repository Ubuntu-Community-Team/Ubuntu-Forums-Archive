---
title: "Are Virtualbox default settings safe ?"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by hebdave on 2014-05-05
High I have just set up virtualbox Ubuntu 12.04 guest on my Ubuntu host which is also 12.04. I wondered if I need to set my virtualbox up differently for 'questionable' sites with browsing or if it is okay with a new VB install ? Also I wondered how virtualbox differs from sandboxie with windows ? 

More precisely does virtualbox contain a threat of malware so it is trapped in one place on your virtual disk as Sandboxie does I think ? 

Many thanks indeed. :)

---

### Post by SeijiSensei on 2014-05-05
It's is "trapped" inside the virtual machine image, but that's all.  You should consider making a backup of the clean image you installed.  Then if something goes awry with the image you're using, you can blow it away and restore the backup.  By default the images are stored in the "VirtualBox VMs" directory in your home.

I have a network server that both my host and guest can see.  I store anything that matters on the server, so reverting to an old guest image doesn't lose anything of importance.

The guest communicates with the Internet the same way the host does.  In the default "NAT" [mode]("http://www.virtualbox.org/manual/ch06.html"), the host uses "network address translation" to forward on the guest's traffic the same way routers do.  With the identical OS, you have the same chance of getting an infection using the guest as the host.

In my case, with Firefox on Linux, that chance has been indistinguishable from zero for a very long time now.  But I don't visit many dodgy sites either.

---

### Post by hebdave on 2014-05-05
Okay thanks thats interesting :)

---

### Post by talz13 on 2014-05-05
Also, feel free to use VirtualBox's snapshots if you want to play with making changes, or anything else that you may want to revert afterwards:

[http://www.howtogeek.com/150258/how-to-save-time-by-using-snapshots-in-virtualbox/](http://www.howtogeek.com/150258/how-to-save-time-by-using-snapshots-in-virtualbox/)

Also, you can use the VirtualBox hard drive "immutable" or "write-through" modes so that no changes are saved to the disk image file after shutting down or rebooting the VM:

[http://www.virtuatopia.com/index.php/Understanding_and_Configuring_VirtualBox_Virtual_Hard_Disks#Normal.2C_Immutable_and_Write-Through_Disk_Images](http://www.virtuatopia.com/index.php/Understanding_and_Configuring_VirtualBox_Virtual_Hard_Disks#Normal.2C_Immutable_and_Write-Through_Disk_Images)

---

### Post by Dane_Jorgensen on 2014-05-05
Snapshots are a great option if you ever need to revert back.  Don't get too crazy with them as each one will take up drive space.

---

### Post by hebdave on 2014-05-06
Okay thanks for the advice :P

---

### Post by plurga on 2014-05-06
what version of VB do u have ? , in the VB web page u can check the bugs that ur version has or were fixed. 

[https://www.virtualbox.org/wiki/Changelog](https://www.virtualbox.org/wiki/Changelog)

---

