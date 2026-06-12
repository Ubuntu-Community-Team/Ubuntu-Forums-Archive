---
title: "Access File on Windows URN from Open SUSE Java Process"
date: 2014-11-04
forum: Programming Talk
---

### Post by stuson on 2014-11-04
Hi All,

Hi All,

This question is not strictly an Ubuntu one,   I'm sure its general Linux type question,  the platform I am trying to achieve it on is actually SUSE,   but  the community here  is very knowledgable so  here goes.

I would like to open a file for IO using a windows type URN ie \\<server>\<share>\filename.ext from a java process running in an app server.

I was rather hoping that a correctly configured samba client would allow it to happen, but that is either not the case or, I haven't found the correct configuration yet.

Has anyone any experience of doing this themselves?

I know I can just mount the windows disk and access that way, but I was hoping to not need that.

The process works perfectly well on a windows app server - the same appserver as it happens just running on a windows machine instead of LINUX. I can open the file and read it into memory etc.

I  create a File object with the URN as the argument and then I can use  things file  myFile.exists()  etc to check that the  file exists.  Then read it into a byte array with commons io.  This all works fine  when running  on windoze  but the file can't be seen when the same process is run on linux.



Cheers

Stewart

---

