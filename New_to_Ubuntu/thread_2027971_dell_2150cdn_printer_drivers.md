---
title: "dell 2150cdn printer drivers"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by patelhe on 2012-07-17
Just migrated to Ubuntu 10.04....can not get my printer to work.  None of the native dell drivers seem to work from add printer.

Dell support has rpm for redhat which I tried to use alien to convert to deb.  Gave me an error about AMD 64 architecture.  Was able to convert to tar.gs then deb....but no go.

Any ideas.

Have gigabyte MB.  AMD Phenom x64.

---

### Post by mapes12 on 2012-07-17
What printer do you have?

---

### Post by patelhe on 2012-07-17
Dell 2150cdn

---

### Post by jmfal on 2012-07-17
Welcome to Ubuntu

Take a look at this:

[http://search.dell.com/results.aspx?c=us&l=en&s=gen&cat=sup&k=ubuntu+drivers&rpp=12&p=1&rf=all&nk=f&ira=False&~srd=False&ipsys=False&advsrch=False&~ck=tab]("http://search.dell.com/results.aspx?c=us&l=en&s=gen&cat=sup&k=ubuntu+drivers&rpp=12&p=1&rf=all&nk=f&ira=False&%7Esrd=False&ipsys=False&advsrch=False&%7Eck=tab")

---

### Post by patelhe on 2012-07-17
Checked that already...That is where I got the redhat linux drivers.  Do not work.  Any workaround?

---

### Post by annnomius on 2012-08-04
i dont have one of these printers, but i downloaded the rpm from dell (actually contains several rpms, but one appears to be the drivers: Dell-2150-Color-Printer-1.0-1.i686.rpm). expandin this rpm using

* rpm2cpio Dell-2150-Color-Printer-1.0-1.i686.rpm | cpio --extract --make-directories*

reveals cups executable filters meant to be placed in 
/usr/lib/cups/filter/Dell_2150_Color_Printer/ 
and also reveals a "dlut" file meant to be placed in 
/usr/share/cups/Dell/dlut/ 
and the ppd files in 
/usr/share/cups/model/Dell/  

you might try placing these files by hand and see if that works. 
note that the filters are executable and depend on certain shared libraries (use ldd to see)--they may be expecting x86 libraries and hence you have problems on amd64?  

curious how it works out... 
::ann

---

### Post by chris129 on 2012-08-24
This works, at least on 11.10(32-bit). Thanks, ann!
Presumably there would be a good chance of it also working on 64-bit as long as any necessary 32-bit libraries are installed...

---

### Post by chris129 on 2012-08-26
For 64-bit system, additionally installing
```
sudo apt-get install ia32-libs
```
will do the trick.

---

### Post by jeffmitri on 2013-01-10
I also have the dell 2150cdn printer and can't seem to get it working on Ubuntu 12.04/32bit. I have to upload a PPD file because the printer driver does not show up in the list. 

I keep getting this error File "/usr/lib/cups/filter/Dell_2150_Color_Printer/DLM_MF" not available: No such file or directory

Does anyone know how to fix this issue? Do I need to install DLM_MF? If, so, how do i install it?

Please help, I don't want to have to switch to Windows, just to get my new printer to work.

---

### Post by annnomius on 2013-01-22
hi jeff,

i tried to respond to your pm, but i'm not sure if it went thru.

> I keep getting this error File "/usr/lib/cups/filter/Dell_2150_Color_Printer/DLM_MF" not available: No such file or directorycan you provide a listing of your /usr/lib/cups/filter/Dell_2150_Color_Printer directory? if all the other executable files are there, you probably accidentally missed the DLM_MF file.

::ann

---

### Post by Fundamental Unity on 2013-07-15
I succesfully installed the drivers on 13.04 64-bit. I followed annnomius' directions with one exception: I had to unzip the ppd files using gunzip before they were recognized. For example, for the 2150cdn ppd, I typed the lines:

```

sudo cp path/to/extracted_files/usr/share/cups/model/Dell/Dell_2150cdn_Color_Printer.ppd.gz /usr/share/cups/model/Dell/Dell_2150cdn_Color_Printer.ppd.gz
sudo gunzip /usr/share/cups/model/Dell/Dell_2150cdn_Color_Printer.ppd.gz

```

Everything else, I was able to copy as-is.

After getting everything into place, I went to the printers control panel and clicked Add. Next I selected Network printer, Find network printer, the printer I wanted to add (after waiting for it to come up on the list), and finally AppSocket/JetDirect via DNS-SD. After searching for the driver, I clicked through two short configuration dialogs and was able to successfully print a test page.

I already had ia32-libs installed, but if I hadn't they would probably have been necessary.

---

### Post by ludovicscn on 2013-08-23
Hi,

I managed to install this printer using the RPM provided by DELL on a 64bits arch (on Debian, but it's quite the same under ubuntu)
1- I create a bootable USB stick with a 32bits arch distro (debian) and installed alien on it.
2-I used alien to create a .deb from the RPM
3-On my 64bits distro, I activated multi-arch 
4-I installed the created rpm with the 32-bits dependancies
It has been working perfectly since. Hope it will help.

here's a link to the i386 .deb [https://www.dropbox.com/sh/nh2s5netswlh0cw/1htNBGNwHs](https://www.dropbox.com/sh/nh2s5netswlh0cw/1htNBGNwHs)

---

### Post by maxweld on 2014-07-09
Having successfully managed to follow the above advice I have my Dell 2150cdn working fine on my 12.04 64bit machine. However, I now have a 14.04 machine and seem unable to get this to work. 

Is there something different about 14.04? Has anyone managed to configure this printer to work under 14.04 64bit?

Thanks in advance...

---

### Post by maxweld on 2014-07-10
Solved - I am using the Generic PCL 6/PCL XL Printer Foomatic/pxlcolor driver.

So I have ignored all teh Dell drivers, performed a standard install of the printer and then, when it cannot find the printer drivers automatically, at the point it offers the option to choose the printer driver from the database, I select a Make of Generic, and then the Generic PCL 6/PCL XL Printer Foomatic/pxlcolor driver is recommended.

Seems to work well.

---

