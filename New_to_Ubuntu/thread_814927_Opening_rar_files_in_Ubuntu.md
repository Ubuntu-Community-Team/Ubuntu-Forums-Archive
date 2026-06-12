---
title: "Opening rar files in Ubuntu?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ronmac on 2008-06-01
Hi All
Have just loaded Ubuntu and some of my software is zipped with WinRar 
Can I get Ubuntu to use WinRar???? or can it be converted to suit.
Regards
Ron

---

### Post by SunnyRabbiera on 2008-06-01
You just need the unrar package, easy to get.
you can just use this page:
[here]("http://packages.ubuntu.com/hardy/unrar")
and install the package for your system...
there are two versions and since I dont know your processor or kernel I cannot advise as of yet what one to install.

---

### Post by sisco311 on 2008-06-01
You can install unrar from Synaptic.
System -> Administrator -> Synaptic Package Manager

---

### Post by billgoldberg on 2008-06-01
install p7zip-full

it's better than unrar

---

### Post by SunnyRabbiera on 2008-06-01
> **billgoldberg said:**
> install p7zip-full

it's better than unrar

yes that works too, I just wanted to cover the bases.
to the original poster, here is a guide you can use on how to install stuff in ubuntu.
[here]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by bumanie on 2008-06-01
> sudo apt-get install rar unrar Also agree with 7zip full, it unzips nearly every compression format.

---

### Post by sayakb on 2008-06-01
Or rather,
```
sudo apt-get install unrar-free
```

rar is a 40day evaluation shareware package.

---

### Post by SunnyRabbiera on 2008-06-01
> **LinuxIsInnovation said:**
> Or rather,
```
sudo apt-get install unrar-free
```

rar is a 40day evaluation shareware package.

I dont think the linux version of unrar does that, as I can still use mine.

---

### Post by sayakb on 2008-06-01
As I mentioned, rar is a 40-day trial.. Here's the synaptic description for package rar:
> Archiver for .rar files
This is the RAR archiver from Eugene Roshal. It supports multiple volume
archives and damage protection. It can also create SFX-archives. There are
versions which run on DOS, Windows (3.1x,95,NT), FreeBSD, BSDI.

This program is shareware and you must register it after 40 days of use.

---

### Post by SunnyRabbiera on 2008-06-01
> **LinuxIsInnovation said:**
> As I mentioned, rar is a 40-day trial.. Here's the synaptic description for package rar:

but thats the compression, he was asking about extracting.
we got better formats for compression anyway :D

---

### Post by sayakb on 2008-06-01
> **bumanie said:**
> sudo apt-get install rar unrar
Also agree with 7zip full, it unzips nearly every compression format.

> **SunnyRabbiera said:**
> but thats the compression, he was asking about extracting.
we got better formats for compression anyway :D

I was quoting on bumanie's comment. ;)
Sorry for not posting a quote.

---

### Post by Joeb454 on 2008-06-01
I just installed "rar" to open .rar files :)

It allowed me to use the default file extractor if I ever came across a .rar file (which for some reason after moving to Linux is less often :confused:)

---

### Post by Mud.Knee.Havoc on 2008-06-01
> **LinuxIsInnovation said:**
> As I mentioned, rar is a 40-day trial.. 

I've got unrar and unrar-free installed on my system and can extract rars by doubleclicking any of the parts (ie. something.rar, something.001, etc) in any file manager.

I don't compress anything with rar, though, which I believe is where the time limit comes in.

---

### Post by Joeb454 on 2008-06-01
Perhaps it's unrar I have installed then...oh looks like I have both installed

---

### Post by durand on 2008-06-01
> **Joeb454 said:**
> I just installed "rar" to open .rar files :)

It allowed me to use the default file extractor if I ever came across a .rar file (which for some reason after moving to Linux is less often :confused:)

In linux, we mainly use tar.gz and tar.bz2 files for compression. The file extractor will handle them fine without any changes.

---

### Post by sayakb on 2008-06-01
7z (As posted before) is quite efficient methinks.. better than anything else..

---

### Post by Joeb454 on 2008-06-01
> **durand said:**
> In linux, we mainly use tar.gz and tar.bz2 files for compression. The file extractor will handle them fine without any changes.

I know that ;) I just meant that on the internet, and from friends in general - it seems to be getting less common for me.

Never mind :D

---

### Post by shifty_powers on 2008-06-01
very rarely use tar.gz or otherwise for my own personal uses. find that winrar runs perfectly in wine anyways ;)

---

### Post by durand on 2008-06-01
Oh right, sorry!

---

