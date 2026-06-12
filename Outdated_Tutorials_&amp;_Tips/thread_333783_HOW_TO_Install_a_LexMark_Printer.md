---
title: "HOW TO Install a LexMark Printer"
date: 2007-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by peterLinux on 2007-01-07
Hi All :

It took me an hour and some research to get my color laser printer working on a ubuntu-server.

Env:
Ubuntu Server (No X!) edgy 6.10 fully patched (Named bc IP: 192.168.10.2)
Lexmark C510 networked (192.168.10.21)

Installing CUPS
apt-get install cupsys cupsys-client cupsys-driver-gutenprint defoma fontconfig foomatic-db foomatic-filters libcupsimage2 libexpat1 libfontconfig1 libfreetype6 libjpeg62 libpaper1 libpng12-0 libslp1 libtiff4 patch perl perl-modules ttf-bitstream-vera ucf

Not much else to say about that...

Then I went to [http://www.lexmark.ca](http://www.lexmark.ca) and followed the link to the Debian print-driver for my printer. Copied the link and downloaded it on the print server.

cd /usr/local/src
wget [http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.deb](http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.deb)

dpkg -i /usr/local/src/print-drivers-linux-glibc2-x86.deb

/usr/local/lexmark/setup.lexprint

All went fine -so far- I have done this before (On a SuSE) so my next command was lexprint...
Which returned:
License Agreement was not accepted.

Bump...

I googled a bit saw a couple people asking the same question but no answer...
After a bit of digging on my local server I found the simple solution.

Run:
/usr/lexprint/bin/license_agreement

Every member of the "print admin" group should run this little 'script', It displays the License Agreement and at the bottom of it you have to sign your life away by typing 'agree'
After that lexprint works :-)

I tweaked the cupsd.conf a bit and finished of with making 2 virtual devices/queues for my color printer.

First search your 'printer type' in my case that is 10LC510

cd /usr/lexprint/bin/
./supported_printers | grep C510
  Lexmark C510               10LC510          automatic

Make the devices/queues

./mkdevice -d lexcolor -i 192.168.10.21 -c "LexMark C510" -p 1
./mkqueue -d lexcolor -q color -p 10LC510 -l automatic -o "banner_page=no duplex=long_edge"

./mkdevice -d lexbw -i 192.168.10.21 -c "LexMark C510" -p 1
./mkqueue -d lexbw -q bw -p 10LC510 -l automatic -o "banner_page=no duplex=long_edge print_mode=black"


And start printing.

Tip: on the 'workstations' go to /etc/cups
Make a file called
client.conf
with 1 line in it:
ServerName *YouServer*

And restart cups locally.

Printers on the print server will show up in System Setting (KUBUNTU)

Enjoy

Peter

---

### Post by RichBR549 on 2007-01-16
Thanks, Peter. 

 I've failed to find any help that worked or was complete enough to get my Ubuntu machine working with my home networked C510n.  ](*,) 

But this worked great!  Thanks.

I missed the "banner=no" so I kept getting banners printed.  Fixed that.  Now need to see why I can't print PDF files.

Thanks, again.

Rich

---

### Post by peterLinux on 2007-01-16
Your welcome.
By the way this works for all (most) Dell printers too
as they are rebranded LexMark's anyway...

I can print PDFs, make sure you have a printable PDF to test with
Some PDFs are 'protected' and cannot be printed...

Peter

---

### Post by RichBR549 on 2007-01-17
I was trying to use Evince for printing my PDF files and it still doesn't work.  It would not even print a PDF I created myself.

So, I loaded Acrobat Reader and it prints PDF's perfectly, even in color.   I'll have to see if I can make it the default. 

Thanks again for the help.

-Rich

---

### Post by aip on 2007-01-17
Thanks for the nice Howto Peter!

I hope it will be very useful to my friends C910 as well. 

As I'm a newbee I have some clarifying questions about your description; 

"*I tweaked the cupsd.conf a bit*" - Is this what you are describing later by creating the client.conf file or ?

"*ServerName _YouServer_*" - Im I supposed to use the name _*YouServer*_ or do I have to change it to any corresponding local servername ?

The installation will be on a desktop edgy 6.10, not a server, may I then use the graphical tools in gnome to define the new printer device/queue, as well ??

-Thanks in advance!
/Anders

---

### Post by peterLinux on 2007-01-23
YouServer needs to read YourServer it is the name of the CUPS print server in your network.
If you run everything from 1 desktop than that box is the CUPS server and you do not need the client.conf in that case.

The tweaks in cupsd.conf are typical for my env.
It is to give others access to the admin section of CUPS.
Nothing relate to get a Lexmark/Dell printer going...

Peter

---

### Post by Asanga on 2007-11-07
Well 

I had nasty time in setting up my Lexmark E332n

I found a some what better way to do this

go tot_ [http://localhost:631/admin](http://localhost:631/admin)_ in u r browse. then u r redirected to CUPS web interface.this is much easier


Or there is a nice doc about CUPS @ _[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)_

---

