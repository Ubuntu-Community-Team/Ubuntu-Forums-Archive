---
title: "Installing imagemagick"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by AvengerX9 on 2013-04-23
I tried to install imagemagick with this command

> sudo apt-get install imagemagick

It installed, but how can I find the path to my imagemagick, and is that all ? Is it working now ?

I tried *display*, but it came up with this error

> display: unable to open X server `' @ error/display.c/DisplayImageCommand/426.

Thanks

---

### Post by oldos2er on 2013-04-23
The package *imagemagick* is a set of CLI tools. ```
man imagemagick
```

---

### Post by varunendra on 2013-04-23
> **oldos2er said:**
> The package *imagemagick* is a set of CLI tools. ```
man imagemagick
```
..and the most commonly used commands from the package are 'convert' and 'mogrify'.

However, the command 'display' should have brought up a GUI application that comes with it. Not sure why the error came up.

For both general and advanced usage, this page (and the linked ones) can be very useful : [http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

---

### Post by AvengerX9 on 2013-04-23
Thanks :)

---

