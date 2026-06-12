---
title: "Please explain /dev folder &amp; /orbit___"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-03-13
Greetings & Salutations!   You good folks have helped me solve several problems, & I'm really having fun with my Ubuntu 11.04 w/ Unity OS!!  I think I'm ready to learn more deeply.

Chasing down a persistent problem w/ my webcam not showing up for Skype, I looked for /dev/video0 and found it.  It's empty.  Curiosity kicked in & I started clicking on other files in /dev.   Most of them are empty, or so it says:  0 kb in file.  Is this as it should be?  Can anyone explain the raison d'etre of the /dev folder & its various contents?

One file in /dev is called [COLOR=Navy]core[COLOR=Black] & I'm surprised to see that it contains 128TB.  That's terrabytes, right?  My HDD isn't that big, so what is this & how does it fit?

In the sidebar list of folders when I click my Home Folder is one called:  [COLOR=Navy]orbit____  [COLOR=Black]where the underline is my name.  What is it?  Do I need it?  Why was it created?  Should I mess with it?

Thanks for expanding my U-wareness!!   
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by idoitprone on 2012-03-13
> **BlueAZ said:**
> Greetings & Salutations!   You good folks have helped me solve several problems, & I'm really having fun with my Ubuntu 11.04 w/ Unity OS!!  I think I'm ready to learn more deeply.

Chasing down a persistent problem w/ my webcam not showing up for Skype, I looked for /dev/video0 and found it.  It's empty.  Curiosity kicked in & I started clicking on other files in /dev.   Most of them are empty, or so it says:  0 kb in file.  Is this as it should be?  Can anyone explain the raison d'etre of the /dev folder & its various contents?

One file in /dev is called [COLOR=Navy]core[COLOR=Black] & I'm surprised to see that it contains 128TB.  That's terrabytes, right?  My HDD isn't that big, so what is this & how does it fit?

In the sidebar list of folders when I click my Home Folder is one called:  [COLOR=Navy]orbit____  [COLOR=Black]where the underline is my name.  What is it?  Do I need it?  Why was it created?  Should I mess with it?

Thanks for expanding my U-wareness!!   
[/COLOR][/COLOR][/COLOR][/COLOR]
/dev is a special file, dont worry and dont mess with it, cuz you can mess around with your hardware from that dir
[http://linux.about.com/od/lsa_guide/a/gdelsa18.htm](http://linux.about.com/od/lsa_guide/a/gdelsa18.htm)

there is some useful files in there for different purposes
/dev/null is a file if you want you put to be ignore

output > /dev/null

if you want random num
cat /dev/random > towateverfileyoufeellikeit

/orbit_ file. seems like a program like making files at the root dir

---

### Post by jerome1232 on 2012-03-13
"orbit_____" on your launcher sounds like a volume that's mounted, you have a usb stick in the computer? A cdrom perhaps? Any removable media you insert will show up on the launcher.

But I'm just taking a guess based on what you said.

---

### Post by doctorzeus on 2012-03-13
> **idoitprone said:**
> /dev is a special file, dont worry and dont mess with it, cuz you can mess around with your hardware from that dir
[http://linux.about.com/od/lsa_guide/a/gdelsa18.htm](http://linux.about.com/od/lsa_guide/a/gdelsa18.htm)

there is some useful files in there for different purposes
/dev/null is a file if you want you put to be ignore

output > /dev/null

if you want random num
cat /dev/random > towateverfileyoufeellikeit

/orbit_ file. seems like a program like making files at the root dir

Or if you want to launch a missile you go (you may need root access): :lolflag:

```
launch /dev/icbm
```

But in all seriousness you may want to look at the Linux / directory structure (very useful to help understand how the system works):

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

One other cool thing you should try:

```
echo Hello World! > /dev/tty1
```

And then check tty1 (ctrl+alt+F1), (ctrl+alt+F7 to get back..)

---

### Post by BlueAZ on 2012-03-13
> **jerome1232 said:**
> "orbit_____" on your launcher sounds like a volume that's mounted, you have a usb stick in the computer? A cdrom perhaps? Any removable media you insert will show up on the launcher.

But I'm just taking a guess based on what you said.
Thanks Jerome1232.  I opened the orbit- folder & here's what I found:  2 files called bonobo-activation-blah, blah  and a bunch of files starting with linc-blah, blah.  Do you know what bonobo is?  Could this be something I installed accidentally?  [as in, I really don't know what I'm doing yet...]

---

