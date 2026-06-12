---
title: "OpenGraphiti freeglut (./graphiti): failed to open display"
date: 2018-05-27
forum: New to Ubuntu
---

### Post by park3300mit on 2018-05-27
I'm trying to install and run this program called the "OpenGraphiti."
I am on Windows 10 using Ubuntu. It has Intel Graphics.

I typed this into the Ubuntu console after:
```
./graphiti
```

It returns 
```
freeglut (./graphiti): failed to open display ''
```

Also, if I run
```
glxinfo
```
It says
```
Error: unable to open display
```

Please help me.

---

### Post by again? on 2018-05-27
Are you running Ubuntu on Windows 10 natively or in a virtual machine?

---

### Post by park3300mit on 2018-05-28
I think natively

---

### Post by again? on 2018-05-28
I haven't used Windows in 10 years nor am I familiar with OpenGraphiti.
Maybe you need to state the DISPLAY to use when running graphical applications.
Note "**echo "export DISPLAY=:0.0" >> ~/.bashrc**" from the following article.
[how-to-run-run-the-native-ubuntu-desktop-on-windows-10]("https://www.zdnet.com/article/how-to-run-run-the-native-ubuntu-desktop-on-windows-10/")
The article is almost 2 years old so it may pay to search for something more recent.

**[COLOR="#FF0000"]Edit[/COLOR]**: This article appears to be more complete and up to date.
[https://www.pcgamer.com/linux-in-windows-10/](https://www.pcgamer.com/linux-in-windows-10/)

---

### Post by park3300mit on 2018-05-28
Thank you so much! The article helped me solve the problems with "Unable to open display" and "Failed to Open Display." ... 
But I got another problem. I get an error saying:
> no module named scripts.demo
Even though I do have the demo.py file in the directory.

---

### Post by again? on 2018-05-28
> **park3300mit said:**
> Thank you so much! The article helped me solve the problems with "Unable to open display" and "Failed to Open Display." ... 
But I got another problem. I get an error saying:

Even though I do have the demo.py file in the directory.
As said, I'm not familiar with OpenGraphiti which this particular error seems to relate to.
Someone else may be able to help or you may have better luck on an OpenGraphiti forum.

---

### Post by park3300mit on 2018-05-28
I fixed the problem that I mentioned, but I ran into another problem that you might (?) recognize?

```
X Error of failed request:  BadRequest (invalid request code or no such operation)  Major opcode of failed request:  149 (GLX)
  Minor opcode of failed request:  169 ()
  Serial number of failed request:  162
  Current serial number in output stream:  162
```

Have you seen this by any chance..?
Thank you again

---

### Post by again? on 2018-05-28
I think you may have a better chance of running linux graphical applications in a virtual machine install of ubuntu.

---

