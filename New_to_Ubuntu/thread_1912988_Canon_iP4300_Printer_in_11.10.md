---
title: "Canon iP4300 Printer in 11.10?"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-21
Another upgrade - another treasure hunt with the Canon printer...

Actually, it works quite well under CUPS, so I shouldn't complain.

But I would like to see it work again with the Canon driver & I am not there yet.

Canon Australia doesn't have Linux drivers for iP4300 any more (sad) but they are still available from Canon Europe.
[http://software.canon-europe.com/](http://software.canon-europe.com/)

I downloaded Linux_Print_Filterv270.tgz OK.
Extracted & converted cnijfilter-common-2.70-2.src.rpm & cnijfilter-ip4300-2.70-2.i386.rpm to .debs.

Tried to follow the latest instructions I could find (but I know they are out of date) which I reproduced here in 2008:
[http://ubuntuforums.org/showpost.php?p=5661732&postcount=8](http://ubuntuforums.org/showpost.php?p=5661732&postcount=8)

I checked I had (or added) libxml1 (have libxml2) : libpng12-0 : libpng12-dev (added) : libgtk1.2 (have libgtk-3-0) : libgtk-common (have libgtk-3-common).

I installed the common package first with sudo dpkg -i cnijfilter-common_2.70-3_i386.deb
then the specific with sudo dpkg -i cnijfilter-ip4300_2.70-3_i386.deb

Is that suffix change correct??

So far - so good, I think.

Then we get to the bit about library links, which I knew was out of date last time:
[http://ubuntuforums.org/showpost.php?p=11395656&postcount=14](http://ubuntuforums.org/showpost.php?p=11395656&postcount=14)

So I checked that the tiff & png library links are just like I found in that post & created new links with:
sudo ln -s /usr/lib/i386-linux-gnu/libtiff.so.4 /usr/lib/i386-linux-gnu/libtiff.so.3
sudo ln -s /usr/lib/i386-linux-gnu/libpng.so /usr/lib/i386-linux-gnu/libpng.so.3

Surprisingly, I could not "Add a printer" simply in System > Admin > Printing - there is no button for that now!
I went to [http://localhost:631/printers/](http://localhost:631/printers/) & couldn't add from there either.

In the end, I went to [http://localhost:631/admin](http://localhost:631/admin) & found "Add printer" there...
That seemed to go OK & I selected the prefered driver, which was the Canon...2.70...

Next I tried to Print a Test page but that failed.
I found the error log which says: Canon_iP4300_Canon: File "/usr/lib/cups/filter/pstocanonij" not available: No such file or directory

I also remembered the Troubleshooter available for printing & ran that by going System Settings > Printers > Print Test Page > Print Error > Diagnose > Forward etc...

That confirmed the Cups Error Log: Printer iP4300 requires the '/usr/lib/cups/filter/pstocanonij' program but that is not currently installed.

I looked in /usr/lib/cups/filter and there is no pstocanonij there.
Searching Nautilus doesn't find it anywhere.

Looking in cnijfilter-common-2.70-2.src.rpm then I can see a folder pstocanonij with a file pstocanonij.c (source code)...

Where do I go from there?

Obviously I have spent hours searching & found endless references to this problem but no clear solutions.
Several people reported success downloading the driver from Canon Asia instead.
They seem to be older versions (?) but I suppose I could try that or even reinstalling from the previous downloads I had which worked in 11.04.

But if there is a simple solution to running the lastest versions, already installed, that would be preferable.

Any ideas?

Thanks!

---

### Post by 2CV67 on 2012-01-22
I checked back through my notes from 2008 & saw that I used the Australian driver last time & that it was cnijfilter-common-2.70-1.i386.rpm not cnijfilter-common-2.70-2.i386.rpm.

So I tried completely removing all canon drivers via Synapt, then installing the Australian -common- filter.

But this threw up warnings about broken packages and specifically package libcupsys2 not being installed.
There is no libcupsys* available in Synapt now.
Googling, as usual, shows hundreds of Canon/Linux users with the same problem.
Solutions were mentioned then which give error 404 now.
There were also complicated solutions involving rewriting .deb packages but that seems an unnecessary can of worms to open today.
Maybe (dream on...) the latest Canon download has fixed that problem, since I have now removed the old Australian -common- & reinstalled all the latest downloads without seeing any warnings about libsys.

Attempting Test Page still shows I need pstocanonij though...

Solutions?

---

### Post by 2CV67 on 2012-02-18
Bump?

Attempting Test Page still shows I need pstocanonij...

---

### Post by Roving Sign on 2012-02-18
May not be much help - but I've had some luck using adjacent models drivers.

For instance - I got a i3600 running with the 4100 driver (i think that was the one)

---

### Post by 2CV67 on 2012-02-20
Well - a minor miracle seems to have happened!

Digging around in Ask Ubuntu, I found the references below.

I would like to know more of the background, but it looks as though one Michael Gruz has set up a PPA which allows you to install a huge range of Canon drivers via Synapt, which WORK - just like that!

I followed these steps:
1. Add the PPA to Synapt & accept that it is untrusted or whatever.
2. Reload Synapt.
3. Search 'cnijfilter'
4. Remove what I had, in my case cnijfilter-common & cnijfilter-ip4300 (if I remember right).
5. Install latest cnijfilter-common & cnijfilter-ip4300series
6. System Tools > Printing > Add > Follow all the defaults.

And it just works!

The guy deserves a medal !

Links:
[http://askubuntu.com/questions/97869/how-do-i-get-my-canon-mx420-printer-working](http://askubuntu.com/questions/97869/how-do-i-get-my-canon-mx420-printer-working)
[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)
[https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)

---

### Post by 2CV67 on 2012-02-27
One snag with this new Canon driver at the moment is that it won't print duplex.

The same printer using the default CUPS/Gutenprint driver does print the same test documents OK as duplex (printing  .odg from LibO & printing .pdf from Evince).

I set duplex in both the applications & in both the printer properties.

I am still digging on this one, but with no success yet.

Any ideas?

---

### Post by riopiedra on 2012-03-14
> **Roving Sign said:**
> May not be much help - but I've had some luck using adjacent models drivers.

For instance - I got a i3600 running with the 4100 driver (i think that was the one)


For me it was the 4600 driver.

---

### Post by 2CV67 on 2012-04-21
Bump...

Still not printing Duplex with Michael Gruz's Canon drivers... (see post #6)

Still no idea why...

Anybody?

Thanks!

---

