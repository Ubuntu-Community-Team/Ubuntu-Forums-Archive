---
title: "Controlling Screen Brightness using C/C++"
date: 2009-06-29
forum: Programming Talk
---

### Post by hthakar on 2009-06-29
Hello,

I am developing a GUI in Ubuntu 9.04 using QT (C++). I need to control the screen brightness using a slide bar. 

I don't have any idea how to do this. Googling gave me this blog

[http://mankikannan.blogspot.com/2008/01/more-linux-fun-screen-brightness.html]("http://mankikannan.blogspot.com/2008/01/more-linux-fun-screen-brightness.html")

This states that there should be a file in **/sys/class/backlight/acpi_video0/brightness** but after looking i just found an empty folder /sys/class/backlight. 

I will appreciate any help.

Thank you,
Harsh.

---

### Post by PmDematagoda on 2009-06-29
There are already applications that do this, two examples are PowerDevil(written in Qt) and Gnome Power Manager(Using GTK+). Perhaps you should look at the source for these applications.

---

### Post by hthakar on 2009-07-01
I found the brightness file in /proc/acpi/video/VID1/LCD. On opening the file through text editor it says <not supported>. 

has Ubuntu 9.04 stopped supporting this file?  I am still going through the code for PowerDevil.

---

