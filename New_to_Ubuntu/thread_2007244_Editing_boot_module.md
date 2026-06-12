---
title: "Editing boot module"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by d4bs on 2012-06-20
First off i would like to thank everyone for such a rich and informative forum. I am very sorry i have not posted earlier but i have been doing a lot of reading and as a complete noob i am unable to help anyone with problems :(

My basic hurdle is this:

I am trying to add modules to the boot file so of course, it will load when restarting.
I enter: vi /etc/modules but i am unsure how to add and save the files needed.

I am trying to follow a tutorial for usb over ip if that is any help.

Sorry if i am a little sketchy as i am just finding my feet with Linux.

Any help or pointers would be much appreciated.

Kind regards

---

### Post by MG&amp;TL on 2012-06-20
*vi *is an advanced editor for those that need it.

I suggest using nano, that's much easier and has tips at the bottom. Just type to write, use the arrow keys to navigate, hit Ctrl-O to save, and Ctrl-X to quit.

```
sudo nano /etc/modules
```...can you also post your tutorial link, it may not be the "ubuntu way" of doing things.

---

### Post by d4bs on 2012-06-20
Thank you very much, i was following this tutorial that is specific to my version:

h t t p://www.howtoforge.com/how-to-set-up-a-usb-over-ip-server-and-client-with-ubuntu-10.04

Regards

---

