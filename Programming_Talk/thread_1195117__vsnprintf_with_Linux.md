---
title: "_vsnprintf with Linux?"
date: 2009-06-23
forum: Programming Talk
---

### Post by wbest on 2009-06-23
I'm working on porting some C++ code from Windows to Linux.
 
I ran into an error with the function _vsnprint(...), which I believe may be in the Windows API.  Any suggestions as to fixing this, WITHOUT Wine?
 
I'm trying to avoid wine as much as possible, it doesn't have the compiling abilities I need it to have right now, unless you have suggestions for quickly compiling things in Wine (Also be advised I cannot connect to Synaptic or download files offline, this is for work and they have these restrictions about download files and programs that you need to be able to get your work done).

---

### Post by jonobr on 2009-06-23
Hello


I recommend you post this in the programming section.

Post there move by a lot slower and are looked over by geniuses.

---

### Post by wbest on 2009-06-23
I'm working on porting some C++ code from Windows to Linux.

I ran into an error with the function _vsnprint(...), which I believe may be in the Windows API. Any suggestions as to fixing this, WITHOUT Wine?

I'm trying to avoid wine as much as possible, it doesn't have the compiling abilities I need it to have right now, unless you have suggestions for quickly compiling things in Wine (Also be advised I cannot connect to Synaptic or download files offline, this is for work and they have these restrictions about download files and programs that you need to be able to get your work done).

---

### Post by wbest on 2009-06-23
Moved.
 
I don't know why I never thought of putting thing there before...Laziness I suppose.

---

### Post by Zugzwang on 2009-06-23
Just drop the leading "_", vsnprintf is also available in Linux:

[http://opengroup.org/onlinepubs/007908799/xsh/vsprintf.html](http://opengroup.org/onlinepubs/007908799/xsh/vsprintf.html)

---

### Post by dwhitney67 on 2009-06-23
Look at the man-page for vsnprintf.
```

man vsnprintf

```

---

### Post by nvteighen on 2009-06-23
The **_vsnprintf** function does exist, but it's meant to be private (it's a static function). Use **vsnprintf**.

---

### Post by Sef on 2009-06-23
Merged duplicate posts.

---

