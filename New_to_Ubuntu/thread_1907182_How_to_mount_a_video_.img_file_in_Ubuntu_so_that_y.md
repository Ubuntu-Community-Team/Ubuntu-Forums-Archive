---
title: "How to mount a video *.img file in Ubuntu so that you can use it"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-01-10
I searched first, and found this somewhat incomplete answer for mounting an IMG file on Ubuntu:
- [**How to mount .img file**]("http://ubuntuforums.org/showthread.php?t=1212372")

That thread suggested Acetoneiso, Power Iso, or the following commands:
```
$ mkdir ~/img 
$ mount -t udf filename.img ~/img -o loop
```However, I had recently installed Gmount-ISO and ISO Master, for this thread:
- [What player or converter do I use to play/convert a 'bin' and 'cue' video file?]("http://ubuntuforums.org/showthread.php?t=1905315")

So, I tried Gmount-ISO and ISO Master first - but neither would recognize the IMG file.

Luckily, based on information in that same thread, I also had just recently installed Furius ISO mount tool version 0.11.1.2 to mount bin/cue files and ISO images. 

It turns out Furious mounted the IMG file without any problems whatsoever!

Furius is now my favorite mounting tool because it mounted the following for me:

[LIST]
[*]bin files (associated with cue files)
[*]iso files
[*]img files
[/LIST]
In addition, just as you can convert bin/cue files to ISO files (using bchunk as shown in the referenced thread), I found by googling that you can convert the IMG to ISO using cd2iso as shown below:
- [Convert IMG to ISO in Ubuntu]("http://www.mopedia.co.uk/2008/02/convert-img-to-iso-in-ubuntu.html")
```

$ sudo aptitude install nrg2iso ccd2iso mdf2iso
$ ccd2iso file.img file.iso

```Any other suggestions are always welcome.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210605&stc=1&d=1326249078[/IMG]

---

