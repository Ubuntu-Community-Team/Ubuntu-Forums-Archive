---
title: "C# Service Application in Ubuntu"
date: 2009-11-24
forum: Programming Talk
---

### Post by tvks on 2009-11-24
Hi,

I have written an C# application which is a **Service application**. It has the facility to get minimized to **System tray**. It has a **_Web browser control_** and two buttons.

I want to use this **_exe_** in Ubuntu. It should work the same like in Windows. Is this possible ?

Thanx for any valuable comments.

Regards,

tvks

---

### Post by Zugzwang on 2009-11-24
Why don't you just try? Install the mono framework and execute your program by running "mono <yourexecutable.exe>" in the terminal. Look in the stickies for how to install it.

---

### Post by tvks on 2009-11-24
Hi Zugzwang,

Thanks a lot for this quick reply. When I executed this command :

```
mono /home/abc.exe
```

I got this following error:
```

libgluezilla not found. To have webbrowser support, you need libgluezilla installed
```

When I try searching for libgluezilla I get this already installed :
```

libmono-mozilla0.1-cil
Mono Mozilla library

```
Not sure what to do ?

Regards,
tvks

---

### Post by Zugzwang on 2009-11-25
> **tvks said:**
> 
When I try searching for libgluezilla I get this already installed :
```

libmono-mozilla0.1-cil
Mono Mozilla library

```
Not sure what to do ?


That's a different library and thus won't help you. However, there seems to be "libgluezilla" available for Ubuntu, so I would suppose that you try that: [http://packages.ubuntu.com/search?keywords=libgluezilla&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libgluezilla&searchon=names&suite=all&section=all)

---

