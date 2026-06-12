---
title: "sfill versus repeatedly copying big files - have I missed something?"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by Green_Mac on 2013-06-21
I'm using Ubuntu 13.04 on a Lenovo laptop dual booting with Windows 8.

I had a go at using sfill to wipe the free space on my hard drive, but it looked as if it was going to take about 14 days for it to complete a single pass (sfill -l -l -v /) of the 400 Gb of free space on my laptop.  Given that all sfill does is write random stuff into a file until the file fills the free space (as I understand it) I thought I'd try filling up the free space with something else.

I took my Ubuntu install CD and copied its contents to a folder on the hard drive (waste1) then copied the contents of that folder to a new folder called waste2, then copied both of them to new folder called waste3, then all three to waste4, and so on.  This way, I filled the disk in a few hours.

My question is, is this as secure as using sfill?

I appreciate that I am only talking about a single pass here, so not that secure anyway, but using sfill's default 38 passes would have taken about 18 months as far as I can tell.

Mac

---

