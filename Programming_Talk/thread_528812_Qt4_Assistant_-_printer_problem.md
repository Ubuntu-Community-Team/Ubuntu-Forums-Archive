---
title: "Qt4 Assistant - printer problem"
date: 2007-08-18
forum: Programming Talk
---

### Post by earonoff on 2007-08-18
I've installed Qt4.3.0 directly from Trolltech into my Kubuntu (Feisty) system. All works great with one minor exception: Qt Assistant has much valuable documentation and it should have the capability to send this documentation to the printer (I have an HP C4180). However the Print command in Assistant does not work as it shows no printers available, A workaround is to Copy and Paste into Kate or OpenOffice. Is there any way to make Qt Assistant aware of the printer in the system?

Tnx much.
Ethan
[email]earonoff@ca.rr.com[/email]

---

### Post by earonoff on 2007-08-20
I found a solution to my problem: I suspect that it may work for anyone with  a similar problem who is using Qt 4.3.0 or later.

It is based on information  in the following two sites:

[http://trollte4ch.com/developer/notes/changes/changes-4.3.0/](http://trollte4ch.com/developer/notes/changes/changes-4.3.0/)

and

[www.cs.brown.edu/system/printing/env.html](www.cs.brown.edu/system/printing/env.html)

In the .profile file I added the lines

PRINTER=myprinter
export PRINTER

In  my system myprinter is HPPhotoSmartC4180

Now I am able to print out the Qt Assistant and the other Qt Documentation files on my system printer.

There may be other, better, solutions to this problem.

---

