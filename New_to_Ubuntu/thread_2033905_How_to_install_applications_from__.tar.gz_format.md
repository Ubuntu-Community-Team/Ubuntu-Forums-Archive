---
title: "How to install applications from  .tar.gz format"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by isaiamuthan on 2012-07-27
Hai every one,
          I am new user to ubuntu....Am trying to install utorrent application in ubuntu...When i download the same,[SIZE=3] installer is in .tar.gz format[/SIZE]........

Any one please help me, [SIZE=4][COLOR=Blue]how to install the application in .tar.gz format?????[/COLOR][/SIZE]

Thanks in advance.

---

### Post by Kirboosy on 2012-07-27
I found this handy little [guide]("http://www.howopensource.com/2011/08/install-utorrent-in-ubuntu-fedora/") on compiling it.

I would recommend using [Deluge]("http://deluge-torrent.org/") or [Transmission]("http://www.transmissionbt.com/") instead of utorrent. Mainly because they are easy to install (through Software Center) and because they are open source. :)

Deluge has a really nice server piece as well in my opinion.

Hope that helps.

---

### Post by ajgreeny on 2012-07-27
Does it have to be utorrent, which as its Linux form does not have a GUI but is a command line application I think.  I gather it is possible to run the windows version of utorrent, which does have a GUI in wine, but I know nothing about it.  Transmission has always been great for my purposes, giving me d/l speeds to the maximum of my ISP's line speed, 850KB/s, so I have not looked any further.

There are lots of torrent client applications available in the repos along side the one you already have, transmission, so have a look at them and try a few to see which you prefer.

To answer your specific question, I'm afraid there is not single or simple answer.  A .tar.gz file is just an archive which could contain anything;  it might be a .deb package file which you could just double click to install like a setup.exe file in windows.

It might contain an excutable static binary, like the tar.gz archives of firefox, which you don't need to install; you simply unpack and then run the "firefox" executable from the archive, so you can even run it direct from your own /home.

It might contain a number of files including an INSTALL or README file with instructions on what to do, which may, for example, mean there is a .run file or similar which you execute in terminal to install the application.

Finally it could contain source code, which you have to compile and then install using terminal command, and which at your stage of Linux knowledge is probably several steps too far to make it worthwhile.

If you really want to take this further, double click on the tar.gz file to unpack it in archive manager (the linux equivalent of winzip) and tell us what files the archive contains.  I suspect it will be the linux command line application, which may not be what you are expecting, but let's go one step at a time.

---

### Post by Bufeu on 2012-07-27
I recommend you [Deluge]("http://deluge-torrent.org/") as BitTorrent-client. Fast, stable and have pretty the same settings in the menu as µTorrent have.
But you asked for help for installing µTorrent Server on Linux, and there you are:
1. Download the .tar.gz-file.
2. Extract it to the folder you want it installed.
3. Run the file *utserver*.
4. The configuration file settings.dat is created.
5. Open **[http://localhost:8080/gui](http://localhost:8080/gui)** via your web browser.

Downloaded files are saved into the folder you extracted µTorrent Server in. If &#956;Torent Server doesn't work after a reboot of the operating system, you must run the file utserver again.

---

### Post by Kirboosy on 2012-07-27
> **ajgreeny said:**
> To answer your specific question, I'm afraid there is not single or simple answer.  A .tar.gz file is just an archive which could contain anything;  it might be a .deb package file which you could just double click to install like a setup.exe file in windows.....

+1


I didn't think to ask what purpose the Original Poster had in mind with this torrent box.

OP What are your plans for this box?

---

### Post by hypnot0ad on 2012-07-27
> **Caboose885 said:**
> 

OP What are your plans for this box?

Should answer this.

Also qBittorrnt is the best torrent client imo.
Everyone named in here has given me problems on 
multiple machines and makes.
If you can learn how to use utrorrent you can use qBit.

---

