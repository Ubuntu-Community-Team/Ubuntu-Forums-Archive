---
title: "liveusb"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-04
Hello, I am trying to make a liveusb to boot ubuntu, and possibly install over other things or dual boot-(thats optional) but it seems that every site I go to says I need different things, how would I do this from a 2GB apacer singlepartition flash drive?

---

### Post by snowpine on 2008-09-04
Hi there, there are a couple of different methods:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by hyperhopper on 2008-09-05
I am trying to install unetbooting here [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

and how do I use the executable to run it---it wants me to select a program to run it with...

it says there is no application installed for this file...

---

### Post by snowpine on 2008-09-05
> **hyperhopper said:**
> I am trying to install unetbooting here [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

and how do I use the executable to run it---it wants me to select a program to run it with...

it says there is no application installed for this file...

Here's what I did (perhaps not the most elegant solution, but whatever). I opened a terminal and typed:

```
gksu nautilus
```

Which opens a file browser as root (be careful!)
Then, find the downloaded unetbootin file. Right click, choose Properties, and under Permissions there's a little box you can check to make the file executable. Now you can double-click the icon to run it (hopefully). 

If you are trying to install from Windows, it will be different obviously. :)

---

