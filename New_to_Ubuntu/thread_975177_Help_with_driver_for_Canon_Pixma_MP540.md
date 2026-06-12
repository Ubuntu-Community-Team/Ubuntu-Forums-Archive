---
title: "Help with driver for Canon Pixma MP540"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by OisinT on 2008-11-08
Hi, I have a canon MP540 and although ubuntu sees the printer, any jobs just queue and the printer shows as idle.
I am guessing the correct drivers aren't installed, but don't really know where to start installing the correct ones.
Any help is appreciated!

---

### Post by thunk77 on 2008-11-08
I think this might be of some help.

[http://forums.linux-foundation.org/read.php?25,2111](http://forums.linux-foundation.org/read.php?25,2111)

---

### Post by OisinT on 2008-11-08
The MP450 is quite a bit different to the MP540 I think.

---

### Post by thunk77 on 2008-11-08
Well the other threads i found don't look very promising..

[http://forums.linux-foundation.org/read.php?25,7198](http://forums.linux-foundation.org/read.php?25,7198)
[http://www.turboprint.info/support/viewtopic.php?t=398](http://www.turboprint.info/support/viewtopic.php?t=398)

I'm sorry but i don't have that particular printer, so I can't be more helpful.

Have you tried the workaround for 450?

---

### Post by OisinT on 2008-11-08
yeah it doesn't work. thanks tho

---

### Post by lmasmith on 2008-12-10
This page has links to MP540 drivers:

[http://software.canon-europe.com/products/0010641.asp](http://software.canon-europe.com/products/0010641.asp)

So now if someone could just tell me how to use these files for Ubuntu it would save me a fair bit of time and effort because i'm really not very good at installing software on linux :-)

leon

---

### Post by OisinT on 2008-12-11
> **lmasmith said:**
> This page has links to MP540 drivers:

[http://software.canon-europe.com/products/0010641.asp](http://software.canon-europe.com/products/0010641.asp)

So now if someone could just tell me how to use these files for Ubuntu it would save me a fair bit of time and effort because i'm really not very good at installing software on linux :-)

leon
noticed that and thought the exact same thing :)

---

### Post by OisinT on 2008-12-11
I tried just opening the debfile and installing it that way but it says 'wrong architecture i386'

It might work for you tho, try downloading the debian.  Then unpack it.
Unpack MP540_debian_printer.tar
go into the unpacked file and click on both cnijfilter-common_3.00-1_i386.deb  &  cnijfilter-mp540series_3.00-1_i386.deb

good luck - wish mine was working :P

---

### Post by feodo on 2008-12-14
> **OisinT said:**
> Hi, I have a canon MP540 and although ubuntu sees the printer, any jobs just queue and the printer shows as idle.
I am guessing the correct drivers aren't installed, but don't really know where to start installing the correct ones.
Any help is appreciated!

Hi, 

My printer works, when I do next steps.
1.Go to Canon-pages and download new Debian Linux-drivers.
2. Install them.
3. Go to Application/Add and remove aplications. There are two "printing"-services. Install both.
4. Go back to "Addminstration/Printing".
5. Remove "MP540"-driver.
6. Install new printer and choose first one "USB..."(cnijusb:/dev/usb/lp0).
7. Choose "Canon" and driver "MP540 ver-3.00".

I did these steps and my printer works oK.

---

### Post by bayvista on 2008-12-16
Can't find Debian drivers on the Canon page. Pls give me a pointer.

---

### Post by Sangaho on 2008-12-16
They seem to have removed it from the driver page. No clue why :o

Here's a link to the linux driver I found using Google's cache:
[http://software.canon-europe.com/software/0031324.asp]("http://software.canon-europe.com/software/0031324.asp")

---

### Post by lmasmith on 2008-12-28
Dear Feodo,
It's step 2 from your instructions below that trips me up - could you expand on this please :-)


> **feodo said:**
> Hi, 

My printer works, when I do next steps.
1.Go to Canon-pages and download new Debian Linux-drivers.
2. Install them.
3. Go to Application/Add and remove aplications. There are two "printing"-services. Install both.
4. Go back to "Addminstration/Printing".
5. Remove "MP540"-driver.
6. Install new printer and choose first one "USB..."(cnijusb:/dev/usb/lp0).
7. Choose "Canon" and driver "MP540 ver-3.00".

I did these steps and my printer works oK.

---

### Post by gcmelzi on 2009-01-02
Hi lmasmith, this is the way I've done it:

gian@VecchioMulo:~/CanonMP540/Printer$ ls
cnijfilter-common-3.00             cnijfilter-common-3.00-1.tar.gz
[COLOR="Magenta"]cnijfilter-common_3.00-1_i386.deb[/COLOR]  [COLOR="Magenta"]cnijfilter-mp540series_3.00-1_i386.deb[/COLOR]
gian@VecchioMulo:~/CanonMP540/Printer$ [COLOR="Magenta"]sudo dpkg -i cnijfilter-common_3.00-1_i386.deb [/COLOR]
[sudo] password for gian: 
Selezionato il pacchetto cnijfilter-common, che non lo era.
(Lettura del database ... 186088 file e directory attualmente installati.)
Spacchetto cnijfilter-common (da cnijfilter-common_3.00-1_i386.deb) ...
Configuro cnijfilter-common (3.00-1) ...
gian@VecchioMulo:~/CanonMP540/Printer$ [COLOR="Magenta"]sudo dpkg -i cnijfilter-mp540series_3.00-1_i386.deb [/COLOR]
Selezionato il pacchetto cnijfilter-mp540series, che non lo era.
(Lettura del database ... 186098 file e directory attualmente installati.)
Spacchetto cnijfilter-mp540series (da cnijfilter-mp540series_3.00-1_i386.deb) ...
Configuro cnijfilter-mp540series (3.00-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
gian@VecchioMulo:~/CanonMP540/Printer$ 

Printer now works (600x600), I'm looking to get even scanner working.
Happy new year.

---

### Post by gcmelzi on 2009-01-02
Follow this link: 
[COLOR="Blue"]http://mp610.blogspot.com/2008/10/canon-pixma-scanners-are-now-network.html[/COLOR]
and you'll be able to get the scanner working with SANE.

---

### Post by OisinT on 2009-01-08
> **lmasmith said:**
> Dear Feodo,
It's step 2 from your instructions below that trips me up - could you expand on this please :-)
unfortunately there doesn't seem to be a 64bit driver yet... that might be the problem you're having installing.

---

### Post by Industrial on 2009-01-17
The i386 drivers seem to work fine on my amd64 system. I had to install the deb files with the --force-architecture flag though. Also the cnijfilter-common_3.00-1_i386.deb install had an unmet dependancy which I fixed with a sudo apt-get install <dependancy-name>.

So, my code was:

 sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb

which chucked up the dependency issue. Fixed with:

 sudo apt-get install libcupsys2

Then, I was able to run:

 sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb

and

 sudo dpkg -i --force-architecture cnijfilter-mp540series_3.00-1_i386.deb

Then I followed the rest of feodo's steps.

Hope this helps!

---

### Post by OisinT on 2009-01-18
> **Industrial said:**
> The i386 drivers seem to work fine on my amd64 system. I had to install the deb files with the --force-architecture flag though. Also the cnijfilter-common_3.00-1_i386.deb install had an unmet dependancy which I fixed with a sudo apt-get install <dependancy-name>.

So, my code was:

 sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb

which chucked up the dependency issue. Fixed with:

 sudo apt-get install libcupsys2

Then, I was able to run:

 sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb

and

 sudo dpkg -i --force-architecture cnijfilter-mp540series_3.00-1_i386.deb

Then I followed the rest of feodo's steps.

Hope this helps!
You are a legend.  Thank you!

---

### Post by lmasmith on 2009-02-04
Hey thanks a heap everyone.  Feodo, Gcmelzi and Industrial most especially.  I followed Industrial's installating code except I didn't have quite the same dependencies, but otherwise did as Feodo described.  Now to get it scanning as well... (thanks in advance to Gcmelzi!).
It's taken a while to get there, but better late than never ;-)
Just have to remember that sudo dpkg  trick next time I come up against a .deb file.

---

### Post by pfum on 2009-05-06
hey, thx everyone for this thread. I've followed all the instructions and got the preinter perfeclty working on ubuntu 9.04. I've also installed the 2 scangear packages but can't still get Xsane to detect it...
 can someone tell me how u did it. thx

---

### Post by ron-toro on 2009-08-29
this worked great for [COLOR="Red"]8.04 but having issues with 9.10[/COLOR]the printer setup. has anyone had any luck getting the scan function to work?

**9.10 issue:**
sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb 
      cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
      Package libcupsys2 is not installed.

Install libcupsys2
      sudo apt-get install libcupsys2
  Package libcupsys2 is a virtual package provided by:
  libcups2 1.4.1-5ubuntu2.4

Install libcups2
sudo apt-get install libcups2
libcups2 is already the newest version.

???? where do i go from here?


> **feodo said:**
> Hi, 

My printer works, when I do next steps.
1.Go to Canon-pages and download new Debian Linux-drivers.
2. Install them.
3. Go to Application/Add and remove aplications. There are two "printing"-services. Install both.
4. Go back to "Addminstration/Printing".
5. Remove "MP540"-driver.
6. Install new printer and choose first one "USB..."(cnijusb:/dev/usb/lp0).
7. Choose "Canon" and driver "MP540 ver-3.00".

I did these steps and my printer works oK.

---

### Post by Marg on 2009-09-04
For scanning I got it working as follows:
After extracting the download from Canon there will be a MP540_debian_scangear.tar, which contains 
scangearmp-common_1.20-1_i386.deb (install this first)
scangearmp-mp540series_1.20-1_i386 deb (then install this)

now open a terminal and type scangearmp
this opens the scangear software

---

### Post by Marg on 2009-09-05
p.s I couldn't get the scanner to work with Sane and found that 
it can use the Canon Scangear software instead (installed as above).

---

### Post by bvpainter on 2009-09-19
This works for me. Thanks a lot for posting it. The problem really had me stumped.

> **feodo said:**
> Hi, 

My printer works, when I do next steps.
1.Go to Canon-pages and download new Debian Linux-drivers.
2. Install them.
3. Go to Application/Add and remove aplications. There are two "printing"-services. Install both.
4. Go back to "Addminstration/Printing".
5. Remove "MP540"-driver.
6. Install new printer and choose first one "USB..."(cnijusb:/dev/usb/lp0).
7. Choose "Canon" and driver "MP540 ver-3.00".

I did these steps and my printer works oK.

---

### Post by plaurentiu on 2009-10-13
In Ubuntu 9.10 Karmic libcupsys2 is actually renamed to libcups2 so when trying to install with:

[FONT="Courier New"]
sudo apt-get install libcupsys2[/FONT]

will result in:

[FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Note, selecting libcups2 instead of libcupsys2**
libcups2 is already the newest version.[/FONT]

What you need is to install a transitional package including the names for the libcupsys2.

For example this: [FONT="Courier New"]libcupsys2_1.3.9-17ubuntu3.1_all.deb[/FONT]

You can get it from here:
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)

It worked like a breeze for me.

And, by the way, the scanning with MP540 works out of the box with Xsane in Ubuntu 9.10

---

### Post by almikul on 2009-10-29
> **plaurentiu said:**
> In Ubuntu 9.10 Karmic libcupsys2 is actually renamed to libcups2 so when trying to install with:
...
What you need is to install a transitional package including the names for the libcupsys2.

For example this: [FONT="Courier New"]libcupsys2_1.3.9-17ubuntu3.1_all.deb[/FONT]
...
It worked like a breeze for me.
Will this package work with cups 1.4.1? 

What I did is modified the dependencies in *.deb as described in this tutorial:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=35136](http://forums.linuxmint.com/viewtopic.php?f=42&t=35136)

I just changed libcupsys2 to libcups2, and the packages installed without a problem.

---

### Post by Ganymedes on 2009-11-07
Thank you!

Got it working with 64-bit Ubuntu version 9.10 by following these instructions.

---

### Post by nelio2k on 2009-11-07
> **plaurentiu said:**
> In Ubuntu 9.10 Karmic libcupsys2 is actually renamed to libcups2 so when trying to install with:

[FONT="Courier New"]
sudo apt-get install libcupsys2[/FONT]

will result in:

[FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Note, selecting libcups2 instead of libcupsys2**
libcups2 is already the newest version.[/FONT]

What you need is to install a transitional package including the names for the libcupsys2.

For example this: [FONT="Courier New"]libcupsys2_1.3.9-17ubuntu3.1_all.deb[/FONT]

You can get it from here:
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)

It worked like a breeze for me.

And, by the way, the scanning with MP540 works out of the box with Xsane in Ubuntu 9.10

Thanks for this. You are a lifesaver. Ubuntu's built-in driver doesn't work with the canon iP2600.
The drivers here 
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)
for ip2600, needs this transitional package to work.

---

### Post by ron-toro on 2010-03-15
This was it. Thanks for the tip. I had it set up on 8.04 and I was following the steps I used before, and just couldn't figure out what "I was doing wrong"


> **plaurentiu said:**
> In Ubuntu 9.10 Karmic libcupsys2 is actually renamed to libcups2 so when trying to install with:

[FONT="Courier New"]
sudo apt-get install libcupsys2[/FONT]

will result in:

[FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Note, selecting libcups2 instead of libcupsys2**
libcups2 is already the newest version.[/FONT]

What you need is to install a transitional package including the names for the libcupsys2.

For example this: [FONT="Courier New"]libcupsys2_1.3.9-17ubuntu3.1_all.deb[/FONT]

You can get it from here:
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)

It worked like a breeze for me.

And, by the way, the scanning with MP540 works out of the box with Xsane in Ubuntu 9.10

---

### Post by areidster on 2010-10-27
Hi, followed this thread and tried to get my MP540 working but come to the conclusion that Canon's drivers do not work with newly installed latest Ubuntu 10.10.  Anyone any experience with this?

---

### Post by Ganymedes on 2010-10-27
Don't know, but with 10.04 they did work.

---

### Post by s4ms3milia on 2010-12-27
I am using this Canon Pixma MP540 since Ubuntu 8.04 and got it working somehow with any version.

Right now i am using maverick 64bit. I am using the .deb packages provided by Canon:

[FONT=Courier New]cnijfilter-common_3.00-1_i386.deb       
scangearmp-common_1.20-1_i386.deb
cnijfilter-mp540series_3.00-1_i386.deb  
scangearmp-mp540series_1.20-1_i386.deb[/FONT]

i was able to install them using [FONT=Courier New]sudo dpkg -i --force architecture --force depends *.deb 

[FONT=Verdana]works for me..[/FONT]
[/FONT]

---

### Post by apocalysse on 2011-03-19
p { margin-bottom: 0.21cm; }a:link {  }&#65279;Ciao a tutti vi spiego come ho risolto il problema con la mia Pixma 540 sulla mia UBU 10.04

ho prima scaricato ed installato il file libcupsys2_1.3.9-17ubuntu3.9_all.deb dal sito [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/) anche se ubuntu 10.04 mi diceva fosse giinstallato.

Successivamente ho scaricato i driver dal sito della canon ed ho installato sia il pacchetto per la stampante che quello per lo scanner.

Ora tutto funziona.

Prima di installare libcupsys2_1.3.9-17ubuntu3.9_all.deb mi dava sempre errore delle dipendenze oppure mi installava la stampante, me la faceva usare, ma successivamente mi dava errore nel controllo delle dipendenze con sudo apt-get -f install.

Spero di esservi stato di aiuto

Ciao a tutti

---

### Post by jatatar on 2011-03-22
In Asia, lots of Canon product drivers are available for linux in rpm and deb files.  I searched for and found the MG8100 series drivers for ubuntu without much trouble.  

Found and installed .deb files from this site

[http://http://www.canon.com.au/en-AU/Support-Services/Drivers-and-Downloads]("http://www.canon.com.au/en-AU/Support-Services/Drivers-and-Downloads")

The scanner and printer drivers are both available.  The link to the download page for the MG8100 is here

[http://support-au.canon.com.au/P/search?model=PIXMA+MG8150&menu=download&filter=0&tagname=g_os&g_os=Linux]("http://support-au.canon.com.au/P/search?model=PIXMA+MG8150&menu=download&filter=0&tagname=g_os&g_os=Linux")

Download the tar.gz files extract and run from directory:

```
sudo ./install.sh 
```

Canon MG8120 printer installed and working!!

---

### Post by M_Krikke on 2011-07-02
Hello,

I tried to install the drivers for the MP540 on Ubuntu version 11.04 but it doesn't seem to work. I changed the libcupsys file and built the .deb files again but the "cnijfilter-mp540series_3.00-1_i386.deb" still gives an error at installation, because it's not allowed to change something of the "cnijfilter-common_..." file.

In any case, when I connect the printer, the MP540-driver is not available in the list. Also, other MP5xx drivers do not seem to work. Does anyone know how to solve this?

Cheers,
Kristof

---

### Post by jtarin on 2011-07-02
> **M_Krikke said:**
> Hello,

I tried to install the drivers for the MP540 on Ubuntu version 11.04 but it doesn't seem to work. I changed the libcupsys file and built the .deb files again but the "cnijfilter-mp540series_3.00-1_i386.deb" still gives an error at installation, because it's not allowed to change something of the "cnijfilter-common_..." file.

In any case, when I connect the printer, the MP540-driver is not available in the list. Also, other MP5xx drivers do not seem to work. Does anyone know how to solve this?

Cheers,
KristofTell us how you installed...details and you need to give the exact error message.....we could guess for another 30 pages.:P

---

### Post by M_Krikke on 2011-07-05
I tried to install these packages:

cnijfilter-common_3.00-1_i386.deb 
scangearmp-common_1.20-1_i386.deb
cnijfilter-mp540series_3.00-1_i386.deb 
scangearmp-mp540series_1.20-1_i386.deb

The two scangearmp-files were installed correctly.
Edit: I installed them by double clicking, so they opened in the software centre and I installed it there.
But for the two "cnijfilter"-files, there was the problem of the dependencies on libcupsys2. This I solved by renaming and rebuilding it, like it was suggested by almikul. Then I could install "cnijfilter-common_3.00-1_i386.deb", but I got an error when installing "cnijfilter-mp540series_3.00-1_i386.deb" with this this log-file:

(It's in Dutch but I translated the important parts)
```

Installation cnijfilter-mp540series_3.00-1-i386.deb

(Database inlezen ... (read database)
(Database inlezen ... 5% 
(Database inlezen ... 10% 
(Database inlezen ... 15% 
(Database inlezen ... 20% 
(Database inlezen ... 25% 
(Database inlezen ... 30% 
(Database inlezen ... 35% 
(Database inlezen ... 40% 
(Database inlezen ... 45% 
(Database inlezen ... 50% 
(Database inlezen ... 55% 
(Database inlezen ... 60% 
(Database inlezen ... 65% 
(Database inlezen ... 70% 
(Database inlezen ... 75% 
(Database inlezen ... 80% 
(Database inlezen ... 85% 
(Database inlezen ... 90% 
(Database inlezen ... 95% 
(Database inlezen ... 100% 
(Database inlezen ... 141478 files and directories currently installed.) 
Uitpakken van cnijfilter-mp540series (uit .../cnijfilter-mp540series_3.00-1-i386.deb) ... 
dpkg: fout bij afhandelen van /home/marc/Documenten/cnijfilter-mp540series_3.00-1-i386.deb (--install): (error when treating ...)
 trying to overwrite '/control', which is also in package cnijfilter-common 3.00-1 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Fouten gevonden tijdens behandelen van: (errors found when treating ...)
 /home/marc/Documenten/cnijfilter-mp540series_3.00-1-i386.deb

```

So when ignoring this error and connecting the printer, I installed it at the "Printing"-thing, looking in the database for the appropriate driver, but no MP540 appears. Only MP500, MP520-drivers, but they do not work as I tried them already.

---

### Post by M_Krikke on 2011-07-09
If someone has an idea how to solve this, please let it know, because the printer is still not working and we need it actually.

---

### Post by jtarin on 2011-07-09
Can you post the link where you got this file.....cnijfilter-mp540series_3.00-1-i386.deb?

Nevermind...found it. I see a.ppd file in there you will need for sure....have you tried setting this up in CUPS? For my printer it's a matter of installing the driver then the filter/.ppd which I normally do manually through CUPS.

---

### Post by M_Krikke on 2011-07-18
How do I work with CUPS? I don't know how to do this.

edit: Also I don't know how I can get this .ppd file.

---

### Post by fpraya on 2011-08-17
> **M_Krikke said:**
> How do I work with CUPS? I don't know how to do this.

edit: Also I don't know how I can get this .ppd file.

Hello M_Krikke. Could you finally install and get Canon Pixma MP540 up and running? I do have the same problem under ubuntu 11.04 (my first ubuntu contact, absolute beginner...).  Thanks

---

### Post by demonipuch on 2011-08-18
Hello fpraya

Here is a simple way to install your printer. Open a terminal and run these commands :
```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-mp540series
```
Open then your web browser : [http://localhost:631/admin](http://localhost:631/admin)
Enter your login and password, click "Add printer" and select your printer in the list.

---

### Post by fpraya on 2011-08-18
Thanks demonipuch for the info. I followed your suggestions and all processes ran ok. The problem is that at the end, a huge number of printers is shown, but MP540 printer is not among them. Any idea? thanks.

---

### Post by bwallum on 2011-08-19
Try and download the driver from here:-

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP540.aspx?DLtcmuri=tcm:14-738689&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP540.aspx?DLtcmuri=tcm:14-738689&page=1&type=download)

You will receive a Debian file compressed as a tar file.

When it is downloaded extract it with a right click and select extract.

Double click on the two .deb files and install using Ubuntu Software Centre. 

The MP540 then becomes available in Printing. Remove any previous attempts at a driver for the printer before installing the .deb files.

---

### Post by M_Krikke on 2011-08-29
I still haven't received new information on how to install this driver, which didn't work as I've told before. So my printer is still not working. Any help on this is greatly appreciated.

---

### Post by bwallum on 2011-08-31
Which bit of my suggestion did you have difficulty with? I'll try and stick with this until you get up and running.

---

### Post by hpne on 2012-03-27
> **demonipuch said:**
> Hello fpraya

Here is a simple way to install your printer. Open a terminal and run these commands :
```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-mp540series
```
Open then your web browser : [http://localhost:631/admin](http://localhost:631/admin)
Enter your login and password, click "Add printer" and select your printer in the list.

This worked for me fine. Thank you!

---

