---
title: "Help required installing Brother printer"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by john18 on 2012-12-21
Very new at this.  I am trying to install a Brother MFC-J4510DW  multi-function printer using the Brother Solutions Center as a resource  for drivers and instruction.  As a precondition to doing the actual  download and installation, I am required to do the following: 
   1.   ia32-libs or libstdc++ is required to be installed.
                    Where do I find these and what command do I use to install?
   2.  "sudo mkdir /usr/share/cups/model" command (as it is) is required before                      installation
                    This I was able to do.
   3.  "sudo aa-complain cuspd" command is required before the installation.
                     To this I got the following response.
                                   john@johnslinux:/$ sudo aa-complain cupsd
                                   sudo: aa-complain: command not found
                      Did not even ask for PW.  How do I deal with this?
Dispite  the above issues, I tried to install the driver I downloaded from the  Brother site as instructed with the following result:
                 john@johnslinux:/$ sudo dpkg -i --force-all mfcj4510dwlpr-3.0.0-1.i386.deb
                 [sudo] password for john: 
                 dpkg: error processing mfcj4510dwlpr-3.0.0-1.i386.deb (--install):
                 cannot access archive: No such file or directory
                 Errors were encountered while processing:
                 mfcj4510dwlpr-3.0.0-1.i386.deb
                 john@johnslinux:/$ 
        Note that I did this with the file "mfcj4510dwlpr-3.0.0-1.i386.deb" located in 
        john/Downloads.  Should I have moved it to some other place first?

Thanks,
John H.
Motherboard: ASRock Z77 Pro4
Processor:  Intel core I5-3570K
OS:  Ubuntu 12.10

---

### Post by lykwydchykyn on 2012-12-21
You need to run the dpkg command either in the same directory as the file, or give it a full path.  So it would be:
```

sudo dpkg -i /home/john/Downloads/<deb file>

```

ia32-libs is in the repositories.  It's only necessary if you're running 64-bit Ubuntu.  Probably it's just easier to run the dpkg command, then run:
```

sudo apt-get -f install

```

to grab the dependencies.  Not sure about the other cups commands; I just installed a brother printer last month and I don't remember having to do any of that.  Can you link to the page where you're getting these instructions?

---

### Post by kurt18947 on 2012-12-21
There is a simple and for me foolproof way to install Brother printers.  It's a shell script that will pull in the appropriate packages, install them and ask what sort of connection you want to use.  Here is Brother's info and download link.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

This is not a GUI but if you have any familiarity with the command line it's pretty simple.  If you want, you can search my user name and 'brother' going back a few weeks/months for further posts re  using this tool.  Installing the scanner is not as straight forward.

---

