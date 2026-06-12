---
title: "Looking For An Applet For System Details."
date: 2012-12-21
forum: New to Ubuntu
---

### Post by sidmor on 2012-12-21
I'm setting up a system for Ubuntu and, being an old Windows guy, I'm spoiled by third party utilities such as SysInfo and Belarc Advisor that mine your Windows system for every conceivable technical resource existing in it. Is there a similar utility for Ubuntu that will tell me stuff such as precisely what hardware is present and resource uses?

---

### Post by haqking on 2012-12-21
> **sidmor said:**
> I'm setting up a system for Ubuntu and, being an old Windows guy, I'm spoiled by third party utilities such as SysInfo and Belarc Advisor that mine your Windows system for every conceivable technical resource existing in it. Is there a similar utility for Ubuntu that will tell me stuff such as precisely what hardware is present and resource uses?

```
sudo apt-get install hwinfo
```Though many DE such as KDE come with diff tools built in.

There are others such as lshw and lshw-gtk GUI front end to lshw. hardinfo, sysinfo.

many others

---

### Post by superdaveozzborn on 2012-12-21
I like Conky it is very nice and can show you many different types of stats on your desktop. give that a try [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by sidmor on 2012-12-24
> **haqking said:**
> ```
sudo apt-get install hwinfo
```Though many DE such as KDE come with diff tools built in.

There are others such as lshw and lshw-gtk GUI front end to lshw. hardinfo, sysinfo.

many others
Thanx, haqking. I want to use "lshw-gtk", but, when I run it, I get a message telling me that running it as a "normal user" may result in erroneous/incomplete info. Then, when I click to continue, the gui opens, but, is entirely empty of information. I thought that installing gawk might help, but, it didn't. Any suggestions? :)

---

### Post by sidmor on 2012-12-24
> **superdaveozzborn said:**
> I like Conky it is very nice and can show you many different types of stats on your desktop. give that a try [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Conky is very nice, SuperDave, thanx! What I am after right now is a similar utility for showing (preferably graphically) all the hardware in the system.

I suppose I should have said that I'm running Ubuntu 12.10.

Happy Holidays to you guys and all in the Ubuntu community who happen to read this!!! 

):P

---

### Post by haqking on 2012-12-24
> **sidmor said:**
> Thanx, haqking. I want to use "lshw-gtk", but, when I run it, I get a message telling me that running it as a "normal user" may result in erroneous/incomplete info. Then, when I click to continue, the gui opens, but, is entirely empty of information. I thought that installing gawk might help, but, it didn't. Any suggestions? :)

run it with sudo (elevated privelege)

---

### Post by sidmor on 2012-12-24
Haqking, when I enter "sudo lshw-gtk" I don't get the warning, but, the gui still opens completely empty. Hmmm??

---

### Post by haqking on 2012-12-24
> **sidmor said:**
> Haqking, when I enter "sudo lshw-gtk" I don't get the warning, but, the gui still opens completely empty. Hmmm??

does lshw work on its own in CLI without the gui ? (dont put gtk on end)

also it might be gtk-lshw

you can also install lshw-gui  but is been a while since i did anything with it.

---

### Post by Zill on 2012-12-24
sidmor:  Open a terminal (Ctrl-Alt-t) and run the following command:
```
sudo lshw -html > ~/Desktop/hardware.html
```
Click on the resulting file on your Desktop entitled "hardware.html" to see a listing of your hardware in a "user friendly" format via your web browser.

---

### Post by sidmor on 2012-12-25
Yes, haqking, all the specs are listed in terminal format. Zill's method seems to be about as good a graphical version this command as one is going to get.

---

### Post by sidmor on 2012-12-25
> **Zill said:**
> sidmor:  Open a terminal (Ctrl-Alt-t) and run the following command:
```
sudo lshw -html > ~/Desktop/hardware.html
```Click on the resulting file on your Desktop entitled "hardware.html" to see a listing of your hardware in a "user friendly" format via your web browser.
Zill, this results in a more readable version of "lshw". Thanx!

---

### Post by MishaX2 on 2012-12-25
Be sure to press the refresh button after you started lshw-gtk with root permissions. It should work then. For some reason it doesn't automatically scan at the startup of the program... I don't know why.

---

