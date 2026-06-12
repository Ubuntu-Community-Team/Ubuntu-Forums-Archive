---
title: "scan brother dcp7040 not work"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by joscastel on 2013-05-18
dcp7040 scan mode not reconize in kubuntu 12.10
I download the drivers from the link brscan3 models for 64bit (My PC is AMD athlon II x3 435 Procesor and my SO version Linux 3.5.0-30-generic)
I run the respective rpm comands to install the drivers
and I copied the files and subdirectory "sane" and their files:  from /usr/lib64 to /usr/lib but the problem was not solved.
Thanks in advance

---

### Post by Merrattic on 2013-05-18
If using kubuntu, why are you running rpm commands, should be using the dpkg commands?

USB or Network drivers ?  (How are you connected to your printer/scanner? Have you used the correct driver and instructions?)

---

### Post by joscastel on 2013-05-20
it is an USB drivers. And I used rpm due the files downloaded were rpm file. The others files are .deb files, Which files must i downloaded and work?
May i repeat the installation with .deb files or must do any previous process (example uninstall drivers installed via rpm) ?
Thanks in advanced

---

### Post by Merrattic on 2013-05-20
Ubuntu and variants use the debian packaging system (hence .deb files ;))

Not sure what impact installing the rpm files will have had, but running the install of the .deb will only overwrite the "same" files and may more likely put everything in the right place.

So go here:

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-5.amd64.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-5.amd64.deb&lang=English_gpl)

and follow this:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)

checking you have all the dependencies/requirements in place (8)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#101)

You will need to use **sudo** in front the  dpkg install command (4.3)

---

### Post by joscastel on 2013-05-20
i uninstall all B rothers Driver with the comands
sudo dpkg -r  brdcp7040lpr
sudo dpkg -r brscan-skey
sudo dpkg -r brscan3
sudo -r cupswrapperdcp7040

i download the files .deb
and instal those with the comands
sudo dpkg -i --force-all   nombrearchivo.deb

then i run the comand
sudo dpkg -l | grep Brother

and show me this information
ii  brdcp7040lpr                          2.0.2-1                                      i386         Brother DCP-7040 LPR driver
ii  brscan-skey                           0.2.4-0                                      amd64        Brother Linux scanner S-KEY tool
ii  brscan3                               0.2.11-5                                     amd64        Brother Scanner Driver
ii  cupswrapperdcp7040                    2.0.2-1                                      i386         Brother DCP7040 CUPS wrapper driver
ii  printer-driver-ptouch                 1.3-4ubuntu1                                 amd64        printer driver Brother P-touch label printers

I think all its OK
But when I try to run Simple Scan program send the error: cant connect with the scanner, but the test page print OK !

Thanks in advance

---

### Post by Merrattic on 2013-05-22
Printer and scanner very different things and use different drivers ;) Looks like you have scanner driver installed OK.

You may have a permissions issue. Open a terminal and try:
```
sudo simple-scan
```

Try connecting to scanner with xsane?
```
sudo apt-get install xsane
sudo xsane
```

Find the big Brother Printer and Scanner thread on the forum, there may be something more you have to do in config files to get PC & Scanner to talk (udev or similar ?)

[http://ubuntuforums.org/showthread.php?t=590793&highlight=brother](http://ubuntuforums.org/showthread.php?t=590793&highlight=brother)

also see Brother site about setting up for normal user:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

---

