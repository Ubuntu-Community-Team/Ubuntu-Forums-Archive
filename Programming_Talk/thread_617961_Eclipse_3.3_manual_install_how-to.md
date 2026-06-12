---
title: "Eclipse 3.3 manual install how-to?"
date: 2007-11-19
forum: Programming Talk
---

### Post by kenbob on 2007-11-19
Ok, since eclipse 3.2 is available on Gusty and I need eclipse 3.3, can anyone tell me how they manually configured eclipse 3.3?

I downloaded "eclipse-SDK-3.3-linux-gtk.tar.gz" and then unpacked it using tar xzf eclipse-SDK-3.3-linux-gtk.tar.gz and it created the eclipse directory. But what more do I need to configure and how do you start eclipse on gusty? I tried ./eclipse without success.
thanks,
kb

---

### Post by jespdj on 2007-11-20
It's really easy, you just unpack it in a directory and run it. No special, magic configuration commands are necessary. But you already tried that and for some reason it didn't work.

Tell us more details: What happened when you tried to run it? Did you get an error message? If so, then what's the error message?

Ofcourse you need to have Java installed. Eclipse probably doesn't work with the default GNU Java which is included with Ubuntu. Install Sun's Java:
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

---

### Post by [h2o] on 2007-11-20
I thought Eclipse shipped with a JDK/JRE? Or maybe that is only on Windows.
Anyway... to use Eclipse you should be using the Sun JDK, since the GCJ-version made it all sluggish.

---

### Post by jespdj on 2007-11-21
More info: [https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

