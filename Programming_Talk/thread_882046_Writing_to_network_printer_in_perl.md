---
title: "Writing to network printer in perl"
date: 2008-08-06
forum: Programming Talk
---

### Post by ludgot on 2008-08-06
I have a perl snippet that will write ascii files to a printer connected
to the parallel port of my pc opening as follows: open (P,">>","/dev/lp0")..
The printer now has been installed under a print server defined in CUPS
as lpd://192.168.123.4/lpt1 i.e running under control of the Line Printer
Daemon and TCP/IP in a local network.
 How do I open (and write to) the printer in the new scenario in perl? I am on Ubuntu 8.04.

---

### Post by pdwerryhouse on 2008-08-08
There is a CUPS perl module, but its documentation is non-existant and hence I can't guarantee it'll help you do what you want.

Honestly, I think you're better off just piping what you want to print to lpr (or maybe running it through enscript first):

```
open(PRINTER,"|lpr -Pprintername");
print PRINTER "whatever\n";
close(PRINTER);

```

---

