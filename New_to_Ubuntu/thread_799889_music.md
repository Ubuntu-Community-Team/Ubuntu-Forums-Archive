---
title: "music"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by mrv1330 on 2008-05-19
I'm new to ubuntu. I'm looking for a program that I can use to download music. I used to use ares with my old computer. I installed frostwire, but for some reason it acts like i did not install it. It won't open or run. What should i use for music, or how can i fix programs that i install to open?

---

### Post by atomkarinca on 2008-05-19
To fix Frostwire you should install java. Open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

then select installed jre from alternatives:

```
sudo update-alternatives --config-java
```

select the one with jre, now start Frostwire. Other than Frostwire there are other protocols like 

aMule for ed2k:

```
sudo apt-get install amule
```

Deluge Torrent for bittorrent:

```
sudo apt-get install deluge-torrent
```

and linuxdcpp for dc++:

```
sudo apt-get install linuxdcpp
```

---

### Post by mrv1330 on 2008-05-19
i keep getting a message that says "E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct this problem." How do i do this??

---

### Post by atomkarinca on 2008-05-19
In the terminal type:

```
sudo dpkg --configure -a
```

---

### Post by SunnyRabbiera on 2008-05-19
yeh frostwire will work once you get regular java installed.
that error you got is common, but its an easy fix.

---

### Post by mrv1330 on 2008-05-19
thanks! No how do I get to the alternatives to select the installed jre?

---

### Post by SunnyRabbiera on 2008-05-19
well if you install the regular java it should work, if you need a base guide to install new software in ubuntu use this guide:
[here]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by atomkarinca on 2008-05-19
> **mrv1330 said:**
> thanks! No how do I get to the alternatives to select the installed jre?
[FONT=monospace]
```
[/FONT]sudo update-alternatives --config-java 
```

---

### Post by mrv1330 on 2008-05-19
thanks allot its working great now... appreciate it

---

### Post by atomkarinca on 2008-05-19
No problem.

---

