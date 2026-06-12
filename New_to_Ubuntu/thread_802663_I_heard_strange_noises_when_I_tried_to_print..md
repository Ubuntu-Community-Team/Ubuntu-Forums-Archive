---
title: "I heard strange noises when I tried to print."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by sashag on 2008-05-21
Hi

After I got the new Ubuntu 8.04 running, I saw that it had 
'found' my Lexmark Z55 printer. So I tried to print something
out to see if the printer also worked with Ubuntu. However,
when I tried to print a part of my resume, I heard this 'squealing' sound coming from my Lexmark printer, even when
I turned it off.

The first time I printed out the resume, the paper did start to
be fed into the printer and I thought that it would then print.
It didn't print, it just started squealing. I've tried various
Linux OS's, and so far, Ubuntu has come the closest to actually
printing something. Now, if I can get Ubuntu to actually print
without sounding 'annoyed' at me, I would be able to make Ubuntu
my primary OS:)

Do I need to download any 'drivers' for Lexmark Z55 in Ubuntu
to make it work properly? I had to install the 'flash' plugin
in order to listen to my favorite radio station, so I figured
that I would have to do the same for making the printer run.
The thing that I did find interesting, was that with the PC 
Linux OS that I already have installed on my computer, it had
the 'flash' plugin already installed. Hope that someone can
help mw with that. Thanks.

---

### Post by nick_h on 2008-05-21
The Lexmark Z55 does work with Ubuntu 8.04 but the wrong driver is installed by default.

The first step is to go into System->Administration->Printing and delete it.

Now go to the Lexmark website and download a file called CJLZ55LE-CUPS-1.0-1.TAR.GZ from the Drivers and Downloads section (select a Linux distribution such as Mandrake).

The bad news is that the driver is intended for rpm distributions.  Have a look at the thread [HOWTO: Lexmark Printers](http://ubuntuforums.org/showthread.php?t=49714).  This will guide you through the process of extracting rpm files from the download.

Follow the first 5 commands to extract 2 rpm files.  Change filenames to the ones for the Z55.  I then ran the alien commands without the -t flag to produce deb files.  These can be installed with dpkg or by clicking on them in nautilus.  The ldconfig line is no longer necessary but you will need to unzip the ppd file.

Once this is done you can install the printer from System->Administration->Printing.  When you are asked to select a ppd file select the one in /usr/share/cups/model instead of one from the database.

---

### Post by sashag on 2008-05-22
Hi!

Thanks Nick for the great info! Unfortunately, not being a 'techie' myself, I doubt that I will be able to make all the necessary changes in order to get the printer working in Ubuntu Linux. Even with you step-by-step help in getting the required files, etc., unfortunately, I'll have to stay with Windows XP unless I can get another affordable printer that does have the needed drivers to run Ubuntu Linux. I will still print out the info you gave me, and when I have more time, I'll take a stab at the directions. Thanks again!

---

### Post by walker9010 on 2008-05-22
While those directions seem complicated, its not actually that bad. Each $ denotes a new line, while the words to the right of the # are comments written by the author to let you know what you are doing. When you exclude those, you are just typing a few commands to "extract" the driver (like unzipping on a windows PC) and then installing the driver. 

Here's a link to the file you need to download (its the first one):

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:339:0:0&searchLang=en&os_group=Mandrake&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:339:0:0&searchLang=en&os_group=Mandrake&target=)

---

### Post by stchman on 2008-05-22
> **sashag said:**
> Hi

After I got the new Ubuntu 8.04 running, I saw that it had 
'found' my Lexmark Z55 printer. So I tried to print something
out to see if the printer also worked with Ubuntu. However,
when I tried to print a part of my resume, I heard this 'squealing' sound coming from my Lexmark printer, even when
I turned it off.

The first time I printed out the resume, the paper did start to
be fed into the printer and I thought that it would then print.
It didn't print, it just started squealing. I've tried various
Linux OS's, and so far, Ubuntu has come the closest to actually
printing something. Now, if I can get Ubuntu to actually print
without sounding 'annoyed' at me, I would be able to make Ubuntu
my primary OS:)

Do I need to download any 'drivers' for Lexmark Z55 in Ubuntu
to make it work properly? I had to install the 'flash' plugin
in order to listen to my favorite radio station, so I figured
that I would have to do the same for making the printer run.
The thing that I did find interesting, was that with the PC 
Linux OS that I already have installed on my computer, it had
the 'flash' plugin already installed. Hope that someone can
help mw with that. Thanks.

The Lexmark Z55 is considered a "paperweight" to Linux.

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z55](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z55)

---

### Post by nick_h on 2008-05-23
> Unfortunately, not being a 'techie' myself, I doubt that I will be able to make all the necessary changes in order to get the printer working in Ubuntu Linux.

I have just written an easy to follow step-by-step guide to installing the Z55:
[HOWTO: Install Lexmark Z55 printer](http://ubuntuforums.org/showthread.php?t=803958)

Hopefully this should make the process easier for you.  The printer works well with the correct drivers installed, and as walker9010 mentioned, the installation is not really very complicated.

---

