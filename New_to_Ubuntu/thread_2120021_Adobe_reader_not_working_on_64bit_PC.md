---
title: "Adobe reader not working on 64bit PC"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by rtroxel on 2013-02-25
**adobe reader not working on 64bit**             
                                                                I'm returning to Linux after several years, so I'm a semi-newbie with this OS.

I've had trouble installing Adobe Reader on Ubuntu 12.10. My PC is a  64-bit model and I tried the two command strings below. I don't  understand the message I keep getting, because the .bin file should be  in clear view. During my last attempt, I tried installing the Reader in  the Desktop directory, with the following results:

roy@roy-EP45-UD3L:~/Desktop$ sudo apt-get install AdbeRdr9.5.4-1_i486linux_enu.bin
[sudo] password for roy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package AdbeRdr9.5.4-1_i486linux_enu.bin
E: Couldn't find any package by regex 'AdbeRdr9.5.4-1_i486linux_enu.bin'

roy@roy-EP45-UD3L:~/Desktop$  apt-get install AdbeRdr9.5.4-1_i486linux_enu.bin
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Any help would be appreciated!

Thanks in advance,

Roy

---

### Post by sandyd on 2013-02-25
Are you looking to open PDF files in Ubuntu?
If so - just double click on the PDF file - Ubuntu includes a PDF reader by default.

Else, if you need functions that only Adobe Reader can provide...

[LIST=1]
[*]Open the Software Center
[*]Go to Edit -> Software Sources
[*]Click on the 'Other Software' tab
[*]Put a checkmark beside the two entries that say 'Canonical Partners', and click close
[*]Open a terminal, and run ```
sudo apt-get update
``` (your password is invisible)
[*]run ```
sudo apt-get install acroread
```
[/LIST]
and Adobe acrobat should be installed .

---

### Post by mgngapyin on 2013-02-25
I think acroread is not present in Ubuntu 12.10.

To install the AdbeRdr9.5.4-1_i486linux_enu.bin file,

first go to the folder the file is in, 

```
cd Downloads
``` 

where Downloads is the "Downloads" folder. [other examples - 
cd ~/Desktop where Desktop is the file location]

make .bin file as executable 

```
chmod +x AdbeRdr9.5.4-1_i486linux_enu.bin
```

install the file (you may need to use "sudo" command because it installs to /opt/ folder.)

```
sudo ./AdbeRdr9.5.4-1_i486linux_enu.bin
```

---

### Post by TheFu on 2013-02-25
> **sandyd said:**
> Are you looking to open PDF files in Ubuntu?
If so - just double click on the PDF file - Ubuntu includes a PDF reader by default

Very few people should run Adobe tools anymore due to security issues. [https://krebsonsecurity.com/tag/adobe-reader/](https://krebsonsecurity.com/tag/adobe-reader/)  Adobe reader is one of the top 2 attack vectors used to compromise computers around the world.  Best to avoid using it at all. BTW, Java is the other.

There are good alternatives to Adobe Reader/Acrobat on every platform, including Linux.  If you search these forums, you will find those alternatives.  For creating PDFs, LibreOffice is pretty good.  For marking up PDFs, [http://ubuntuforums.org/showthread.php?t=1609430](http://ubuntuforums.org/showthread.php?t=1609430) has some suggestions with pros/cons for each.

You might want to review [http://ubuntuforums.org/showthread.php?t=2079447](http://ubuntuforums.org/showthread.php?t=2079447) which describes dependency issues with Adobe Reader on x64 Ubuntu.
A .bin file usually means it includes an installer.  For most people, directly installing a tool is a bad idea, because it doesn't become managed by the package management system on Ubuntu.  That means YOU will need to manually patch that program from now on.  Using the **apt-get** instructions above would be highly, highly, highly recommended over manually handling software updates.  For many people, this is the #1 reason to switch to Linux - much simplified package, patch and application management.

Many Windows programs work well under WINE too.  I use Free **PDF-Xchange** (Win version)this way and routinely markup PDFs to be shared with others.

---

### Post by rtroxel on 2013-02-25
> **mgngapyin said:**
> I think acroread is not present in Ubuntu 12.10.

To install the AdbeRdr9.5.4-1_i486linux_enu.bin file,

first go to the folder the file is in, 

```
cd Downloads
``` 

where Downloads is the "Downloads" folder. [other examples - 
cd ~/Desktop where Desktop is the file location]

make .bin file as executable 

```
chmod +x AdbeRdr9.5.4-1_i486linux_enu.bin
```

install the file (you may need to use "sudo" command because it installs to /opt/ folder.)

```
sudo ./AdbeRdr9.5.4-1_i486linux_enu.bin
```
Many thanks! This worked the first time.

Roy

---

