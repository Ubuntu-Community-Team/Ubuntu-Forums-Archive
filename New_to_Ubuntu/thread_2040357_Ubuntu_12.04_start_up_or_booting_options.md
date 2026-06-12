---
title: "Ubuntu 12.04 start up or booting options"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by chitragurung on 2012-08-10
Hello,

I have just installed Ubuntu 12.04 in my dell mini 10 inspiron machine. Before it was 10.04. 

In the starting window it gives three options like
new version generic ( or something )
old version 
memory test or etc

As I noticed system has taken more space I believe, is it because of above or something else. Is it usual to come above options or something wrong.

---

### Post by drs305 on 2012-08-10
Yes, those are normal entries. The first is your current linux kernel. The second entry may be "Previous Linux versions". Under this submenu are previous kernels for the current OS. The third entry is a memory test entry which is seldom used - but the file the command uses doesn't take up much space.

Whenever a newer kernel is introduced to Ubuntu, the older one is moved to the submenu. It's a good idea to keep at least one older kernel on your system at least until you are sure the newer one is working correctly.

If you wish to remove older kernels, it will reduce the space used on your system but not by a large amount. Here is a link on removing kernels:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")
I recommend the Ubuntu Tweak option. It's a GUI app that can easily and safely remove old kernels and other unnecessary files.

---

### Post by chitragurung on 2012-08-10
Thank you so much. Now I understood.

---

