---
title: "PDF Reader"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-07-30
Ubuntu 14.04,two questions:

1) I can't view certain PDF files in Ubuntu, e.g. those used by South African Revenue Service (SARS). They sometimes have an extension of .ASPX, but if I change that to .PDF I can open the doc in Windows, but not in Ubuntu. Is there any software that I can download to be able to view these docs in Ubuntu?

2) Sometimes when I want to install new software, or updates to existing software, I am offered three choices with extensions .tar.gz, .deb and .rpm. What is the difference and which one should I choose for Ubuntu 14.04?

---

### Post by TheFu on 2014-07-30
ASPX - is an active server pages - normally something from a webserver -IIS usually (Windows-centric).  I've never seen it as a data file type.  It would be a mistake made either in downloading or in the webserver setup, IMHO.  But I honestly do not know.  I use evince and xournal to view PDF files, but tax forms seem to be created by people who don't care about cross-platform support.  I suppose you could load the Linux Adobe Reader.  Enable the Canonical Partner repo, then update, then install acroread package, if you want the Adobe version - I do NOT want any software from Adobe on any of my computers.

So the 2nd answer is **none.**  Ubuntu uses a package manager (for many, many, many reasons) and you should avoid installing any software directly using downloaded files.  Downloaded files to be installed break dependencies and will make your system get into "apt hell" (where system updates fail) soon.  You should find the package and install it through the package manager.  If the package isn't already available in the current repos, perhaps a PPA can be added with the package you desire?    PPAs extend the native package management system and don't break dependency checking and validation with other packages.  I hope that makes sense.

If you absolutely need to install software that is only available as a non-PPA, non-repo package - normally, this is only a software developer need - then start with the .deb file (you'll be responsible for manually patching the program moving forward).  This breaks the main reason that people like Linux - the centralized package management is a key reason I prefer it over the other options.

I hope that makes sense?

---

### Post by grahammechanical on 2014-07-30
Ubuntu is based upon Debian which uses the Debian packaging format. So, Ubuntu does too. Hence deb files. But Red Hat, and with it Fedora, uses the Red Hat Packaging format. Hence RPM. Software packaged as RPM is not suitable for Ubuntu.

And then we get to compression formats and tar.gz is one of those. Un-compressing a tar.gz archive is one thing. If it contains and application, then installing the application is something else.

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

Regards.

---

### Post by fonsi2099 on 2014-07-30
I have the same problem after the upgrade , 

No correlation with data compression or similar only after upgrade some PDF and .doc and  .ods are not readable.

thanks for any help

:popcorn:

---

### Post by monkeybrain20122 on 2014-07-30
Try running pdf-xchange viewer in Wine. I won't bother with acroread, it is unsupported and it is bloated and slow anyway.

---

### Post by TheFu on 2014-07-30
> **monkeybrain20122 said:**
> Try running pdf-xchange viewer in Wine. I won't bother with acroread, it is unsupported and it is bloated and slow anyway.

I've been burned by pdf-xchange not printing barcodes properly (online ticket purchases). Fortunately, the 5 tickets (without proper barcodes) were handled nicely by the location (parking and amusement park) to be a minimal hassle.  I specifically used pdf-xchange on a real, physical, Win7 box to print them.  Don't get me started about calling something an electronic-ticket, but still requiring a piece of paper for entry/redemption - idiots.

xournal allows annotations of PDF files - use Export to PDF to add them to a new PDF file, otherwise annotations are stored in an xoj? file.  However, it doesn't support search, which sucks - evince does. Guess that explains my choice of 2 PDF tools on Linux?

---

### Post by Dragonbite on 2014-07-30
I've given up on stand-alone PDF readers, and use Firefox's built-in PDF reader instead.

---

### Post by llamabr on 2014-07-31
Wine is rarely the correct solution.  And Firefox doesn't have a built in pdf reader.  Whatever you're using is an add-on, and is likely an adobe extension.

If you cannot find out what app to use, open a terminal, and tyep:

file *file-name*

and paste the output to us.

---

### Post by Dragonbite on 2014-07-31
It's still not the stand-alone Acrobat reader, and seems less bloated.

---

### Post by cressrt2 on 2014-07-31
I am still running 12.04, and the default for PDF files is the Document Viewer (Evince), is this not available with 14.04?

---

### Post by rsgangr on 2014-07-31
Last year I raised this issue with the SARS Helpdesk but never got past the "this needs to be escalated as a technical query" stage. In other words I never received an answer that was not Windows-centric.  The problem is that Flash Player 11.3 is required and the only solution I could find was the installation of the Chromium browser (you can find it in the repositories) followed by the Pepper Flash Player. This allows me to log into SARS and submit my Tax Returns. The last time I logged on was during February 2014 - I do not know whether the system has changed in the interim.  If you wish to follow this route have a look at the following: [http://ubuntuguide.net/install-pepper-flash-for-chromium-in-ubuntu-13-0412-1012-04](http://ubuntuguide.net/install-pepper-flash-for-chromium-in-ubuntu-13-0412-1012-04) [http://www.ubuntugeek.com/how-to-install-pepper-flash-for-chromium-web-browser-on-ubuntu-gnulinux.html](http://www.ubuntugeek.com/how-to-install-pepper-flash-for-chromium-web-browser-on-ubuntu-gnulinux.html)  The only alternative is to work from a Windows machine - Good luck!

---

### Post by monkeybrain20122 on 2014-07-31
> **llamabr said:**
> Wine is rarely the correct solution. And Firefox doesn't have a built in pdf reader. Whatever you're using is an add-on, and is likely an adobe extension.

If you cannot find out what app to use, open a terminal, and tyep:

file file-name

and paste the output to us.

Well I wish I don't have to use Wine but unfortunately I find using pdf-xchange viewer in Wine the only satisfactory solution to fill out some electronic forms. Okcular is OK (or use Libreoffice's draw for a dirty solution) but often the contents of textboxes don't render correctly and none of the PDF viewer in Linux supports scripts (say tax forms where columns add automatically).  I would prefer PDF-Xchange viewer in WiNE to Adobe's bloat ware if I have to (not to mention that acroread is no longer maintained). For reading PDFs evince does the job.

Yes, Firefox has a bult in PDF reader. Not sure which version of FF you are using but it has been having one for quite some times, though not as good as Chrome's.

---

### Post by cressrt2 on 2014-08-01
For basic form filling I normally use, flpsed, a small but effective programme.

---

### Post by jwn-2 on 2014-08-02
Now I have tried just about anything except Wine/pdf-exchange. I have installed Wine, but how on earth do you now install or run windows software with it. I have tried Control/Install new software, I tried running the install file (as well as some old stand allone DOS programmes for a test (which still run perfectly weel in Win7)), but abolutely nothing happens. I have tried double-clicking the file, I have tried right-click/open with Wine, I have tried opening it directly from Ubuntu, as well as with the Wine explorer. I have checked that the ownershiop is Me, and that the executable-flag is set. Absolutely no luck. What on earth am I doing wrong???

---

### Post by jwn-2 on 2014-08-02
I have posted this new Wine issue also as a new thread.

---

### Post by jwn-2 on 2014-08-07
I have at last got Foxit pdf viewer working in Wine and that seems to have done the trick.Thanks for all your suggestions guys. I will mark this as solved.

---

