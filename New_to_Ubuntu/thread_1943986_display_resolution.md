---
title: "display resolution"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by mashavecher on 2012-03-20
Hi.
Need help very much. I've installed ubuntu on toshiba satellite l755-a2w, I have display resolution 800*600, while it' capable of 1366*768. How do I set it properly?
And one more thing my fan seems to have gone mad, heating and running full speed

---

### Post by IWantFroyo on 2012-03-20
Go to the "Display" or "Monitors" application, and change the resolution from there.

---

### Post by mashavecher on 2012-03-20
The problem is that in there I only have two options 640*480 and 800*600

---

### Post by sudodus on 2012-03-20
Hi mashavecher

I think you have problems with the graphics driver. What is your graphics chip? And what is your graphics driver?

Edit: Run the command
```
gksudo lshw>lshw.txt
```
and look at the output with for example
```
less lshw.txt
``` and look for the chapter about ***display*** for the hardware

And run the command ```
glxinfo|grep -i opengl
``` for the software. Install glxinfo if necessary with
```
sudo apt-get install mesa-utils
```

---

### Post by mashavecher on 2012-03-20
NVIDIA GeForce GT 525M 
Where do I look for the driver?

---

### Post by sudodus on 2012-03-20
> **mashavecher said:**
> NVIDIA GeForce GT 525M 
Where do I look for the driver?
With nvidia you should use the graphics driver, that is offered via the internal tool for proprietary drivers. Then it should work. I run nvidia without problems. GeForce GT 525M should perform quite well. See the ***edit*** in my previous post howto find out about the current driver.

You can run ```
jockey-gtk
``` to start the GUI application that offers proprietary drivers.

---

### Post by mashavecher on 2012-03-20
proprietary drivers offers nothing, says no proprietary drivers are in use on this system.

---

### Post by sudodus on 2012-03-20
> **mashavecher said:**
> proprietary drivers offers nothing, says no proprietary drivers are in use on this system.

gksudo lshw>lshw.txt and nothing happens, no output.

Maybe lshw is not installed, try to run it with
gksudo lshw and if it fails install with
```
sudo apt-get install lshw
```

Which version of Ubuntu are you running?

---

### Post by mashavecher on 2012-03-20
> **sudodus said:**
> Maybe lshw is not installed, try to run it with
gksudo lshw and if it fails install with
```
sudo apt-get install lshw
```

Which version of Ubuntu are you running?

10.04 install says newest version, then
gksudo lshw>lshw.txt asked for pswd in GUI window, which then disappeared and again no output

I've tried to place output of
less lshw.txt from computer running ubuntu, but I get connection reset by server. I'm writing from my MacBook.

I need ubuntu to run special software for my science

---

### Post by mashavecher on 2012-03-20
I know it's not the best way, but I have just installed 11.10 and everything looks beautiful.
I just need linux to run ARB.
Thank's anyway for help

---

