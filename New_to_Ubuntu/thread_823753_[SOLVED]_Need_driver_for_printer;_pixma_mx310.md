---
title: "[SOLVED] Need driver for printer; pixma mx310"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by grayesky on 2008-06-09
Hi, I'm trying this out because I've 'googled' for hours and haven't gotten anywhere.  I'm using ubuntu hardy heron 8.04.

I have a canon pixma mx310 all in one printer.  When I plug it in (usb) the printer is recognized, but when I try to print a test page I get the error 'client-error-document-format-not-supported'.  I don't know why I would get this message, other than the fact that there's no driver (I had hoped that there was a generic driver pre-installed).  I can't install the driver that comes on the setup CD because it's for windows.

I'm figuring that the driver is for windows too.  If I'm wrong, maybe I could copy the right files somewhere and get it to work, but I wouldn't know what or where to copy.

If anyone knows of a driver that works well for this printer and linux I'd like to know.  Since I'm an absolute beginner to linux, I would need some help installing it also.

Thank you.
Sky

---

### Post by Victormd on 2008-06-09
you can use the mx150 (or 160... I'm not at home so I can't check now) for that printer. I have a 465 and the 150 driver works fine... no scanner though, that's a different story...

---

### Post by grayesky on 2008-06-09
Ok, thanks for the quick response.

I spent a little more time looking for that driver, but I can't find it.  It's harder to search when I don't know what to do with the driver if I find it. 

Do you (or anyone else) have time to tell me where to get it, if the windows version will work, and/or how to install it?

Sky

---

### Post by bumanie on 2008-06-09
It is highly unlikely, to probably impossible that windows driver would work. Canon provide very little open source support. You will have to try the driver mentioned in the first answer. This site is probably your best bet if the other driver suggested soesn't work. [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

---

### Post by grayesky on 2008-06-09
OK then, now I know it will say 'linux' somewhere on the download.  Thank you.

The problem is that I can't find the driver for the mx150.  If I google "pixma mx150" I get spanish sites, and if I add a hyphen, "pixma mx-150" I get one russian site.  Searches using some and all of the words 'download', 'printer', 'driver', 'pixma', 'mx150', 'linux', 'ubuntu', and 'PLEASE GOD!?!', yield nothing useful.

I need to know where to look, then I need to know how to install it.
Sky

---

### Post by ardvark71 on 2008-06-09
> **grayesky said:**
> Hi, I'm trying this out because I've 'googled' for hours and haven't gotten anywhere.  I'm using ubuntu hardy heron 8.04.

I have a canon pixma mx310 all in one printer.  When I plug it in (usb) the printer is recognized, but when I try to print a test page I get the error 'client-error-document-format-not-supported'.  I don't know why I would get this message, other than the fact that there's no driver (I had hoped that there was a generic driver pre-installed).  I can't install the driver that comes on the setup CD because it's for windows.

I'm figuring that the driver is for windows too.  If I'm wrong, maybe I could copy the right files somewhere and get it to work, but I wouldn't know what or where to copy.

If anyone knows of a driver that works well for this printer and linux I'd like to know.  Since I'm an absolute beginner to linux, I would need some help installing it also.

Thank you.
Sky

Hi...

Here is the listing for the mx300 at linuxprinting.org, it may work for the 310....

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX300](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX300)

Drivers are included but all of them except one is in RPM format so you will need to download the "alien" package from the repositories (via Synaptic.) :)

I also imagine some compiling might be necessary as well unless it has an install script.

EDIT: Ok, nevermind, found the mx310 and information here...

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX310](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX310)

Best Regards...

---

### Post by stchman on 2008-06-09
> **grayesky said:**
> Hi, I'm trying this out because I've 'googled' for hours and haven't gotten anywhere.  I'm using ubuntu hardy heron 8.04.

I have a canon pixma mx310 all in one printer.  When I plug it in (usb) the printer is recognized, but when I try to print a test page I get the error 'client-error-document-format-not-supported'.  I don't know why I would get this message, other than the fact that there's no driver (I had hoped that there was a generic driver pre-installed).  I can't install the driver that comes on the setup CD because it's for windows.

I'm figuring that the driver is for windows too.  If I'm wrong, maybe I could copy the right files somewhere and get it to work, but I wouldn't know what or where to copy.

If anyone knows of a driver that works well for this printer and linux I'd like to know.  Since I'm an absolute beginner to linux, I would need some help installing it also.

Thank you.
Sky

That printer is reported to work only partially under Linux.  Good luck getting it to work well.

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX310](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MX310)

Blame Canon for not authoring a driver for it.

I don't mess with printers that are not in the openprinting database.  They usually won't work.

---

### Post by grayesky on 2008-06-09
Thank you ardvark71 and stchman.

It's now printing Ok on grayscale, so thats alright.

For anyone else, the driver is 'Canon PIXMA MP180 - CUPS+Gutenprint v5.0.2 Simplified'.  No link needed.

By the way, I'm only messing with this printer that's not in the database because it cost me as much as the linux distro did.

---

### Post by ardvark71 on 2008-06-09
> **grayesky said:**
> Searches using some and all of the words 'download', 'printer', 'driver', 'pixma', 'mx150', 'linux', 'ubuntu', and 'PLEASE GOD!?!', yield nothing useful.


Now I wouldn't say that. 

I think HE helped you plenty this day. ;)

Glad your problem was fixed. :)

Best Regards...

---

### Post by Eglo on 2009-09-04
under jaunty64bit worked printer well, but the scanner NOT.
i try a lot of driver her
[http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/)
and googled to much!

any idea how can use the scanner with Xsane?


best regards

---

### Post by jschlis82 on 2012-11-20
> **grayesky said:**
> Thank you ardvark71 and stchman.

It's now printing Ok on grayscale, so thats alright.

For anyone else, the driver is 'Canon PIXMA MP180 - CUPS+Gutenprint v5.0.2 Simplified'.  No link needed.

By the way, I'm only messing with this printer that's not in the database because it cost me as much as the linux distro did.
I tried the cannon mp180, and it didn't work tried the mp150 and it worked great.  Figured I share if the mp180 driver doesn't work for you.

---

