---
title: "Vim Across Linux and Windows"
date: 2007-12-26
forum: Programming Talk
---

### Post by Lutherian on 2007-12-26
Hi, as a lot of programmers live in the vim environment I thought it would be useful to post thise question here.

I have Gvim Portable on a flash drive (alway drive e:\) which runs under windows.

I then have a desktop running Ubuntu.

I save my work as a session file and try to get around the problems by using the 

	:set sessionoptions+=unix,slash

so the forward/backward slash issue is circumvented.

Another problem arises though:

vim sessions saved on the windows machine will contain reference to a path structures such as

e:\my-docs\work-stuff

whilst a session saved on the linux system would have a a path as

/home/joeblogs/work-stuff.

any ofcourse opening the across the two system yeilds errors.

Is there a way to make vim sessions saved with *relative* paths instead of absolute paths?

Thanks guys!

---

