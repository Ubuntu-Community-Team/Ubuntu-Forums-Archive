---
title: "HP printer doesn't detect Ubuntu PC"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by mtman on 2011-12-11
I am new to Ubuntu...having purchased a rebuilt PC from fregeek here in portland.  I purchased an HP 6500 printer, scanner etc., but have been unable to make the scanner, copier work...any ideas?  I already called freegeek, they suggested i call HP...they informed me it would cost $149 to download a driver?...is there another way?

Thanks...mtman

---

### Post by bluexrider on 2011-12-11
> **mtman said:**
> I am new to Ubuntu...having purchased a rebuilt PC from fregeek here in portland.  I purchased an HP 6500 printer, scanner etc., but have been unable to make the scanner, copier work...any ideas?  I already called freegeek, they suggested i call HP...they informed me it would cost $149 to download a driver?...is there another way?

Thanks...mtman

You should be able to download the correct printer drivers here

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Use the drop down boxes to locate the proper application

---

### Post by asifnaz on 2011-12-11
> **mtman said:**
> I am new to Ubuntu...having purchased a rebuilt PC from fregeek here in portland.  I purchased an HP 6500 printer, scanner etc., but have been unable to make the scanner, copier work...any ideas?  I already called freegeek, they suggested i call HP...they informed me it would cost $149 to download a driver?...is there another way?

Thanks...mtman

paste output of
```

lspci 
```

---

### Post by Mark Phelps on 2011-12-11
Sorry to be discouraging, but if you check that HP link for supported printers, you'll see that even though the HP65xx series is listed, only PRINTING is supported -- scanning and faxing are not.

I have an HP 8510 and it is in the same situation.

---

### Post by JKyleOKC on 2011-12-11
I have a slightly similar situation with an all-in-one printer-scanner-fax although it's not from HP, and solved the problem completely by installing VirtualBox, creating a virtual machine in it, and loading Windows XP Pro into the VM. I then installed the printer and scanner into that VM, using the manufacturer's CD, and tagged it for sharing across my local network. The VM is set up to load automatically when the box boots, and the printer is installed into the Xubuntu host as a "network printer" via the VM.

To scan, I "remote" into the VM and use the Windows scan drivers. VirtualBox allows me to access directories on the host system directly from the guest system, so I can put the scans into my Linux directories just as if I were scanning direct from the host. By configuring the VM's network interface for "host only" access, I don't expose the Windows system to the Big Bad Internet.

It sounds ridiculous, but it does work and gives me access to all the device features, which the manufacturer's Linux drivers failed to do. It might work for you.

---

### Post by bluexrider on 2011-12-11
> **JKyleOKC said:**
> I have a slightly similar situation with an all-in-one printer-scanner-fax although it's not from HP, and solved the problem completely by installing VirtualBox, creating a virtual machine in it, and loading Windows XP Pro into the VM. I then installed the printer and scanner into that VM, using the manufacturer's CD, and tagged it for sharing across my local network. The VM is set up to load automatically when the box boots, and the printer is installed into the Xubuntu host as a "network printer" via the VM.

To scan, I "remote" into the VM and use the Windows scan drivers. VirtualBox allows me to access directories on the host system directly from the guest system, so I can put the scans into my Linux directories just as if I were scanning direct from the host. By configuring the VM's network interface for "host only" access, I don't expose the Windows system to the Big Bad Internet.

It sounds ridiculous, but it does work and gives me access to all the device features, which the manufacturer's Linux drivers failed to do. It might work for you.

At least this is a workaround until Linux Drivers are available.

---

### Post by colin.p on 2011-12-11
> **Mark Phelps said:**
> Sorry to be discouraging, but if you check that HP link for supported printers, you'll see that even though the HP65xx series is listed, only PRINTING is supported -- scanning and faxing are not.

I have an HP 8510 and it is in the same situation.

Perhaps I'm missing something here, but I have an officejet 6500 e709 wireless printer connected by cat5 to my router and I can print, fax, copy and scan from all three of my lucid computers, as well, of course, from the windows machines. I am using hplip 3.10.2, from the repositories.
Been that was since jaunty or maybe it was karmic, but you get the picture.

edit: if the printer is close by, you can use fax, scan and copy direct from the printer's control panel.

---

