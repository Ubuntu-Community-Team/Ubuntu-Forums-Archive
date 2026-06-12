---
title: "waltop  file format"
date: 2010-12-18
forum: Programming Talk
---

### Post by blackest_knight on 2010-12-18
hi i'm looking for information about the waltop file format i know it has a simple 32 byte header followed by a number of data packets of 6 bytes each 
the first 4 are x and y pen coordinates the next 2 are a mystery but seem to be for byte 5 there is a value of 13,14,15,16 usually fairly consistent which i think might be pressure, the 6th byte is usually  87 although sometimes it is 0. I think 0 might be an indication of a pause in writing the document. 

I think it should be possible to make an approximate conversion from a svg file to top each line statement records a stroke x1 y1 x2 y2 and although the next two bytes are missing i think they can be defaulted to using say 13 ,87 

There seems to be no checking of the file so any body or section of body can be attached to the header and it will be accepted as a valid top file.

so whats so good about top? it is about the only input format accepted by myscript notes which can turn hand written notes into a text file.
this program works fine in wine (it isn't ocr it recognises the stroke directions to figure out what letters you are writing)

my medion tablet puts out top files natively which can be written on the pad and uploaded to a computer.

I have a silvercrest digital pen which does a memory dump in which pages are embedded this can be retrieved using m210c or m210c-qt which saves the pages in svg format (which myscript notes can't read) theres a number of devices which identify as pegasus note taker. 


In windows it gets worse.
The "note manager" supplied with the pen has its own formats. From note manager you can save a page as a pegvf file which can only be read by note manager. To transfer files to myscript notes lite it has a plugin so myscriptnotes lite can understand the file sent to it but although note manager attempts to send pages to myscript notes if its installed myscript notes can't read them. I was forced to rename myscriptnotes folder so it would start myscript notes lite instead.

so handwritten notes with a digital pen -> text file and graphics in linux is what this is about. there are 2 paths that could be taken convert from the memory dump or convert from an svg file. The svg file format conversion might be the most useful.

---

### Post by Favux on 2010-12-18
Hi blackest_knight,

You might want to talk to Nikolai Kondrashov.  He's working on the Waltop's (among other tablets) on the kernel side:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20100905225009.GB10805%40barra.bne.redhat.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20100905225009.GB10805%40barra.bne.redhat.com&forum_name=linuxwacom-devel)

and the X side:  [http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTinUx-fqsFhLFVzm7BjaySK8RgX-d6fB5oAC-rto%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTinUx-fqsFhLFVzm7BjaySK8RgX-d6fB5oAC-rto%40mail.gmail.com&forum_name=linuxwacom-devel)

---

### Post by blackest_knight on 2010-12-18
Thanks favux i've sent him an email, also did the same with waltop so i might have more info soon

---

