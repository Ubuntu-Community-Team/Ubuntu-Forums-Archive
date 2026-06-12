---
title: "[SOLVED] Blank DVD says 4.7 GB but Brasero shows 4.3 GB. what gives?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by joneez on 2008-11-18
My DVD+R discs say 4.7 GB but brasero shows 4.3 GB, and my CD-R say 700 MB but show 650 MB. Is there a reason for this or am I missing something?

---

### Post by ciscosurfer on 2008-11-18
So this doesn't answer your question, but imo, Brasero as it stands currently is horribly botched. Search on **brasero** in the forums and you'll see what I mean.  Try using **gnomebaker** to burn data, **serpentine** to burn music, or **k3b** to burn either type.  I think k3b is the most mature of them all and is highly touted in the OSS community.  It's a qt app but runs fine under GNOME.

EDIT: The posts below me hit the nail on the head.

---

### Post by rampageoberon on 2008-11-18
manufacturers use 1mb = 1000kb but actually its 1Mib=1024kib

You can do the math :P

---

### Post by nhasian on 2008-11-18
> This is due to the classic difference between GB and GiB, KB and KiB.

Humans think 1KB = 1000 bytes while computers think 1 KB =1024 bytes (2 to the 10th power). To be more accurate (and avoid this confusion) 1024 bytes should be referred to as 1 KiB (kibibyte).

A DVD can hold approximately 4.7 GigaBytes (GB) but only 4.37 GibiBytes

[http://wiki.answers.com/Q/Why_is_a_4.7GB_DVD_only_able_to_use_4.3GB](http://wiki.answers.com/Q/Why_is_a_4.7GB_DVD_only_able_to_use_4.3GB)

---

### Post by dhtseany on 2008-11-18
Probably something related to situations similar to where ads refer to 1 gig as 1000 megabytes when in reality it's actually 1024 megabytes. Sorry if that was poorly worded but I'd suspect it's something do to with that. For example, my 60 gig HDD shows up as a 58.5GB volume instead of 60GB. 

Make sense?

Peace
Sean

---

### Post by scorp123 on 2008-11-18
> **joneez said:**
> My DVD+R discs say 4.7 GB  This is a classic example of "Marketing People's Lingo" vs. "IT Lingo".

_**According to marketing people:**_
[INDENT]1 Gigabyte = 1000 Megabytes = 1'000'000 Kilobytes = 1'000'000'000 Bytes[/INDENT]

**_So according to people in marketing, the math is:_**
[INDENT]4'700'000'000 Bytes = 4'700'000 Kilobytes = 4'700 Megabytes = 4.7 GB ...[/INDENT]

And that's what they write onto those DVD disks to make you buy them. But as everyone knows, the above math is deeply flawed. 

_**The truth is that you'd have to divide by 1024 and not 1000:**_
[INDENT][COLOR="Red"]4'700'000'000 Bytes[/COLOR] = 4'589'843 Kilobytes = 4482 Megabytes = _[COLOR="Red"]4.376 Gigabytes[/COLOR]_[/INDENT]

Marketing people are lying to you if they tell you that a DVD has room for "4.7 GB" .... your Linux programs however are telling you the truth.

And nope, I am not a fan of those new-style units like "GiB", "KiB" and what not. That's BS.  1 MB = 1024 KB.

---

### Post by dhtseany on 2008-11-18
> **scorp123 said:**
> 

And nope, I am not a fan of those new-style units like "GiB", "KiB" and what not. That's BS.  1 MB = 1024 KB.

Perfectly worded.

Peace
Sean

---

### Post by joneez on 2008-11-18
Thanks all, I learn somethin' every day! ):P

---

