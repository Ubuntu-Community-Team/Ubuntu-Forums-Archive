---
title: "Can someone help compile this Canon driver for amd64"
date: 2011-01-06
forum: Packaging and Compiling Programs
---

### Post by bbellster on 2011-01-06
Hi, I have no experience compiling and am a relative noob to linux.  I am trying like mad to get the canon irc3580 network printer working on my 10.04 amd64 installation.  I downloaded the driver from Canon here: [http://support-sg.canon-asia.com/contents/SG/EN/0100270807.html](http://support-sg.canon-asia.com/contents/SG/EN/0100270807.html) (at the very bottom of page).

after untarring
I was able to successfully compile the -common package found in Source after installing Glade and a few other things.
The problem is with the second package I changed the architecture to amd64 in debian/control 
then I execute dpkg-buildpackage 
I get the error:

make[4]: Entering directory `/home/bell/Downloads/UFR_II_Printer_Driver_for_Linux_V220_uk_EN/Sources/cndrvcups-lb-2.20/cpca/cnpklib'
/bin/bash ../libtool --tag=CC   --mode=link gcc -O2 -Wall -fPIC -D_UFR2_ -Wall -g -O2 -shared -version-info 1:0:0 -Wl,-Bsymbolic-functions -o libcnpkufr2.la -rpath /usr/lib cnpklib.lo cnpkopt.lo cnpkproc.lo -lbuftool 
libtool: link: can not build a shared library
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.

Can someone help me out here??

---

### Post by ronnielsen1 on 2011-01-06
a deb might be easier
>                                                                                                     2.   CQue 2.0.0 Linux Driver DEB 64-bit (v2.0.0)                                                    [IMG]http://software.canon-europe.com/Images/triangle_right_gray.gif[/IMG]
                                                                                                                                                             
                                                                                                                                                           This driver is a Graphical User Interface based driver for use  on Linux with CUPS and foomatic. It is packaged in the DEB format for  use with Debian and Ubuntu.  This driver is for 64 bit versions of Linux  operating systems.                                            
                                                                                                                   
                                                                                                                                                                                                                                                                     Compatibility:
                                                                                                                                                       Operating system(s):                                                     
                                                    Linux
                                                                                                                                                         
                                                                                                                                                      Language(s):                                                     
                                                    English
[http://software.canon-europe.com/products/0010557.asp](http://software.canon-europe.com/products/0010557.asp)


The deb should be at:
[http://software.canon-europe.com/software/0040165.asp?model=](http://software.canon-europe.com/software/0040165.asp?model=)

---

### Post by ronnielsen1 on 2011-01-07
Did it help?

---

