---
title: "Ubuntu not updating"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by jbcohen on 2013-02-17
[Solved]

Ubuntu will no longer allow me to update it - The error message is as follows:

w:failed to fetch CD Rom://Ubuntu 12.04.1 LTS_Percise Pagolin_-Release i386(20120817.1)/dits/percise/main/binary/-i386/Packages Please use apt-

I have recently set the updates to download and install automatically, could that be the reason that I can't get any updates?

---

### Post by snowpine on 2013-02-17
In the Software Center, go to Software Sources and uncheck the box for the CD-ROM.

---

### Post by jbcohen on 2013-02-17
I have Cinnamon Desktop running, I go to the unbuntu software centre and click Edit, Software sources and I see several tabs and nothing for CD Rom.

---

### Post by snowpine on 2013-02-17
Personally I would edit the file directly:

```
gsku gedit /etc/apt/sources.list
```

(if you're not a gedit user then substitute your favorite text editor)

Find the line that references the CD ROM and type a # symbol at the start of the line to comment it out. Save the file and you should be good to go.

---

### Post by deadflowr on 2013-02-17
Look in other software.
The CD stuff should be in the top area, uncheck it.

---

### Post by jbcohen on 2013-02-17
Thank you that solved the problem, however now I would like to go into the why.   Why would I want to put a check mark there?

---

### Post by snowpine on 2013-02-17
Some people do not have an internet connection, therefore they might choose to install packages from a CD-ROM.

---

### Post by varunendra on 2013-02-18
> **jbcohen said:**
> Thank you that solved the problem
jbcohen,
If you are satisfied with the solution, please consider marking the thread as [Solved].

The correct way to do so is -
Click on "**Thread Tools**" link above the top post on the page > Click on "**Mark this thread as solved**"

To see an example with screenshots, and how this helps others, follow the link in my signature.

Thank you for cooperating. :)

---

