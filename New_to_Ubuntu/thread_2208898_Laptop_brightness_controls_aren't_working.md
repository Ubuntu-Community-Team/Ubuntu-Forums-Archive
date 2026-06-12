---
title: "Laptop brightness controls aren't working"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by jason66 on 2014-03-02
Hey, so it's my first day using ubuntu!!!  All of my drivers worked with no problem.  The only problem is my brightness controls. When i use my fn keys to change my brightness, a scale comes up from ubuntu but the screen stays the same.  I'm using a dell latitude 3450.

---

### Post by varunendra on 2014-03-03
Welcome to the forums Jason! :)

To let us see your video brightness settings, please show us some command outputs. Please open a terminal (Ctrl-Alt-T) and run the following codes in it one-by-one (you may copy-paste it using your mouse cursor) -
```
uname -mr
lsmod | egrep 'wmi|acpi'
cat /proc/cmdline
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
Copy-paste the outputs in your next post here.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by artie3 on 2014-03-05
The op might not understand how to copy and paste to and from terminal and/or how to post the results here on the forum. I'm a newbie too, and had the same issue. Fortunately for me, I had a mentor next door who helped me immensely. 

In Windows, the Dell specific driver called 'Dell Quickset' allows the Fn keys to function. The is no similar utility program for Ubuntu, so your Fn keys can't work. 

All the functions can be duplicated with command line controls however.

And, my Fn keys in my Dell laptop do function after installing the latest Daily Build of 14.04. The developers have improved the new version of Ubuntu by providing proper support for the Fn keys on Dell Systems.

I can't reccomend changing to 14.04 as it's rumored to be unstable and is only a Beta version. But, when 14.04 is released in April, you will likely want to use it. 

GL.

Artie

PS:There is also a utility program that allows the screen brightness to function, but it is a stand alone program, it does not use the Fn keys to control the screen brightness directly.





here

---

### Post by raja.genupula on 2014-03-05
have you gone through xbacklight ?

---

