---
title: "Is there a way to know if i'm running a 32bit app on my 64bit system?"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by Deuced on 2011-12-11
As topic's title says,is there a way to know that i'm running a 32bit program onto my ubuntu 11.10 64bit system?

In windows 7 64bit,for example,all the 32bit processes shown in the task manager have a little *

[IMG]http://www.ranorex.com/images/task-manager-Ta.png[/IMG]

Thank you :)

---

### Post by kio_http on 2011-12-11
If you download from represitories e.g Ubuntu Software Center, unlike in Windows everything is x86-64 (64 bit) on a 64 bit installation and 32 bit on an 32 bit installation of Ubuntu.

---

### Post by sandyd on 2011-12-11
For more technical terms (like you installed the 32bit app by yourself...).


[LIST=1]
[*]Find the path to the binary (i.e. /bin/cp, or /usr/bin/kmess, or w/e).
[*]Type "file" /path/to/binary. (without quotes)
[/LIST]
It will show the programs arch in the output.
The last example in the screenshot shows the output of file if it is not a binary (but a script)
[[URL=http://imageshack.us/photo/my-images/14/snapshot23q.jpg/][IMG]http://img14.imageshack.us/img14/4140/snapshot23q.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/14/snapshot23q.jpg/")
[/URL]

---

### Post by victor9098 on 2011-12-11
The easiest way for me is to check via Synaptic. Ubuntu 11.10 has 'multiarch' support, so a 64 bit install can run 32 bit versions when there is not 64 bit in the repo's. A good example of this is Skype, there is only an i386 version available to both 32 bit and 64 bit in the Ubuntu repo's.

If you use Synaptic, just look for the installed application, maybe getting the full name of it from system monitor, then on a 64 bit install all 32 bit versions will be listed with i386 after the name.

---

### Post by Deuced on 2011-12-12
ok,thank you all!

---

