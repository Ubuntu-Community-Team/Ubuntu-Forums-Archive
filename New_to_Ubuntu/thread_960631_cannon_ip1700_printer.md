---
title: "cannon ip1700 printer"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by jtmedin on 2008-10-27
Am unable to install drivers for the ip1700. Have you? Where do i stant? TIA

---

### Post by dracayr on 2008-10-27
[http://blog.indodx.com/archives/how-to-install-canon-ip1700-printers-drivers-in-ubuntu.jsp](http://blog.indodx.com/archives/how-to-install-canon-ip1700-printers-drivers-in-ubuntu.jsp)

EDIT: sorry about the picture...

dracayr

---

### Post by ad_267 on 2008-10-27
Looks like that website is run by a 14 year old.

I had a Canon ip1600 which was a real pain to set up. I got rid of it and am using a HP with no problems now. 

I had to use the ip2200 drivers to get the Canon to work. According to this page, [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700), the 2200 drivers should work with the ip1700 too. They are rpm packages, not debs, so you have to use alien to convert them. That's explained here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

---

### Post by jtmedin on 2008-10-29
> **ad_267 said:**
> Looks like that website is run by a 14 year old.

I had a Canon ip1600 which was a real pain to set up. I got rid of it and am using a HP with no problems now. 

I had to use the ip2200 drivers to get the Canon to work. According to this page, [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700), the 2200 drivers should work with the ip1700 too. They are rpm packages, not debs, so you have to use alien to convert them. That's explained here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

Everything went ok until i got to step 6 then i got a broken pipe & failure. I did make a mistake downloading from //software. I had a lower-case file name. Think that may be the problem? TIA

---

### Post by ad_267 on 2008-10-30
I don't think that would be the problem. What do you mean by broken pipe? What error do you get?

---

### Post by jtmedin on 2008-10-30
> **ad_267 said:**
> I don't think that would be the problem. What do you mean by broken pipe? What error do you get?

(Reading database ... 164129 files and directories currently installed.)
Preparing to replace cnijfilter-common 2.60-2 (using cnijfilter-common_2.60-2_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Unpacking cnijfilter-ip2200 (from cnijfilter-ip2200_2.60-2_i386.deb) ...
Setting up cnijfilter-common (2.60-2) ...

The above came from file temp which i had '>temp'


dpkg: error processing cnijfilter-ip2200_2.60-2_i386.deb (--install):
 trying to overwrite `/usr/lib/libcnbpcnclui256.so.3.2.0', which is also in package libcnbj-2.6
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 cnijfilter-ip2200_2.60-2_i386.deb

The above came to the terminal pane.

---

### Post by jtmedin on 2008-10-30
> **ad_267 said:**
> I don't think that would be the problem. What do you mean by broken pipe? What error do you get?

Here is a complete listing of the output of terminal. Did notice in step 5 that scripts were not converted & --scripts was suggested.

bgtk1.2 libgtk1.2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
libxml1 is already the newest version.
libpng12-0 is already the newest version.
libgtk1.2 is already the newest version.
libgtk1.2-common is already the newest version.
libgtk1.2-common set to manually installed.
The following packages were automatically installed and are no longer required:
  cupsddk cupsddk-drivers
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libpng12-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 171kB of archives.
After this operation, 504kB of additional disk space will be used.
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)]
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)]
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)]
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)]
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libpng12-dev 1.2.15~beta5-3 [171kB]
Fetched 171kB in 2min26s (1170B/s)                                             
Selecting previously deselected package libpng12-dev.
(Reading database ... 164129 files and directories currently installed.)
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-3_i386.deb) ...
Setting up libpng12-dev (1.2.15~beta5-3) ...
ted@ted-desktop:~$ cd cannon
ted@ted-desktop:~/cannon$ ls
canon
ted@ted-desktop:~/cannon$ wget [http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz](http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz) 
--13:22:18--  [http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz](http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz)
           => `iP2200_Linux_260.tar.gz'
Resolving software.canon-europe.com... 217.150.145.30
Connecting to software.canon-europe.com|217.150.145.30|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,358,123 (11M) [application/x-gzip]

100%[====================================>] 11,358,123   221.68K/s    ETA 00:00

13:23:11 (210.62 KB/s) - `iP2200_Linux_260.tar.gz' saved [11358123/11358123]

ted@ted-desktop:~/cannon$ ls
canon  iP2200_Linux_260.tar.gz
ted@ted-desktop:~/cannon$ tar -xvzf iP2200_Linux_260.tar.gz
cnijfilter-common-2.60-1.i386.rpm
cnijfilter-common-2.60-1.src.rpm
cnijfilter-ip2200-2.60-1.i386.rpm
cnijfilter-ip2200-lprng-2.60-1.i386.rpm
ted@ted-desktop:~/cannon$ sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip2200-2.60-1.i386.rpm
cnijfilter-common_2.60-2_i386.deb generated
Warning: Skipping conversion of scripts in package cnijfilter-ip2200: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
cnijfilter-ip2200_2.60-2_i386.deb generated
ted@ted-desktop:~/cannon$ ls
canon                              cnijfilter-ip2200-2.60-1.i386.rpm
cnijfilter-common-2.60-1.i386.rpm  cnijfilter-ip2200_2.60-2_i386.deb
cnijfilter-common-2.60-1.src.rpm   cnijfilter-ip2200-lprng-2.60-1.i386.rpm
cnijfilter-common_2.60-2_i386.deb  iP2200_Linux_260.tar.gz
ted@ted-desktop:~/cannon$ sudo dpkg -i *.deb
(Reading database ... 164148 files and directories currently installed.)
Preparing to replace cnijfilter-common 2.60-2 (using cnijfilter-common_2.60-2_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Unpacking cnijfilter-ip2200 (from cnijfilter-ip2200_2.60-2_i386.deb) ...
dpkg: error processing cnijfilter-ip2200_2.60-2_i386.deb (--install):
 trying to overwrite `/usr/lib/libcnbpcnclui256.so.3.2.0', which is also in package libcnbj-2.6
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Setting up cnijfilter-common (2.60-2) ...
Errors were encountered while processing:
 cnijfilter-ip2200_2.60-2_i386.deb
ted@ted-desktop:~/cannon$

---

### Post by lhb1142 on 2008-10-30
> **jtmedin said:**
> Am unable to install drivers for the ip1700. Have you? Where do i stant? TIA
Try this:

< [http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/](http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/) >

I hope this helps you.

---

### Post by ad_267 on 2008-10-30
If you try that way, make sure you remove the packages you just installed (If they did install at all). You can just search for cnijfilter in Synaptic.

---

### Post by baAng on 2008-12-13
Hello all..

For your information, you can use iP1800 driver for iP1700. I've been  trying all those tips and solutions but i found this solutions is the best.

Actually, this driver is from Canon Australia with the .rpm format. Luckily, a kind hearted person has "alien"ed it for all.

**Step One**

Connect your printer (your printer must be connected in order to proceed)

[B]Step Two
[/B]
Install your package. Get it here
[cnijfilter-ip1800_2.70-2_i386.deb]("http://www.box.net/shared/x4avbcfzft") **(Gusty & Earlier)**
[cnijfilter-ip1800_2.70-2_i386-hardy.deb]("http://www.box.net/shared/4qnsdbmdl1") **(Hardy)**

You can install it through GDebi by double-clicking on them or by using this command through terminal

```
sudo dpkg -i /driver/download/location/file_name.deb
```

*This driver is subject to the terms of the Canon IJ Printer Driver License, which you must read and agree to before installing. It's the GNU General Public License v2 with additional copyright notices and disclaimers.*

**Step Three**

Configure your CUPS. go to this web interface [CUPS]("http://localhost:631/").

Click Administration --> Add Printers 
In this section, put your printer name (iP1800/iP1700), 
Location usb://Canon/iP1700 and Description is up to you.
In the second section, choose Canon --> Continue
In the last section, choose Canon iP1800 series Ver. 2.70 (en)

**Step Four**

Restart your CUPS by using this command

```
sudo /usr/sbin/invoke-rc.d  cupsys restart
```

Now, your iP1700/iP1800 printer is ready to eat papers 
:guitar:

---

