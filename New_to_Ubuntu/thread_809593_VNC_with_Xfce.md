---
title: "VNC with Xfce"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by guilly on 2008-05-27
Has anyone been successful at doing this? It seems the only way I can connect remotely is by creating a new session and then from the log on screen selecting remote session. If I use VNC or any other application I get an error message saying the machine is not accepting any new connections? I have the proper ports opened on my router and I have configure firestarter as well.

Are there any logs that can be looked at to get more of a detailed error as to what exactly is happenign when trying to connect?? I dont know if it matters but I'm running Kubuntu on my client and Ubuntu on my server with xfce interface.

Thank you

---

### Post by quelx on 2008-05-27
Are you trying to connect to the desktop active on the server itself or create a new X session (like a terminal server?)

---

### Post by guilly on 2008-05-27
> **quelx said:**
> Are you trying to connect to the desktop active on the server itself or create a new X session (like a terminal server?)

I'm trying to connect to the server from the desktop itself. If I use vnc from the desktop I get the error message but If I logout and go to create new session I can connect no problem. 

Hope that answers your question.

---

### Post by quelx on 2008-05-27
try these steps

```
sudo apt-get install vnc4server
sudo vncpasswd
```

now edit your **/etc/X11/xorg.conf** adding the following lines

```

Section "Module"
.
.
Load "vnc"
.
.
EndSection
Section "Screen"
.
.
 Option      "PasswordFile"    "/root/.vnc/passwd"
.
.
EndSection

```

restart X and point your VNC client to ip.adr.es.s:0

---

### Post by guilly on 2008-05-27
> **quelx said:**
> try these steps

```
sudo apt-get install vnc4server
sudo vncpasswd
```

now edit your **/etc/X11/xorg.conf** adding the following lines

```

Section "Module"
.
.
Load "vnc"
.
.
EndSection
Section "Screen"
.
.
 Option      "PasswordFile"    "/root/.vnc/passwd"
.
.
EndSection

```

restart X and point your VNC client to ip.adr.es.s:0

Now it seems to be crashing my X Server when I connect to it. A window comes up for a second or so then just crashes. Is there something else that may need to be configured in the xorg?

---

### Post by quelx on 2008-05-27
Oops, have a look at the X error logs  then just comment out those lines (**#** in front) and 

```
less /var/log/Xorg.0.log
```

can you paste the lines where is complains (**EE** lines)

EDIT:
Just tried it on my xfce lappy and noticed that sudo still puts stuff in your home folder, so you need to move the .vnc directory to the root folder

```
sudo mv ~/.vnc /root/
```

EDIT:EDIT:

It worked for me after I moved the .vnc directory to the right place, you could just change the line in the xorg.conf but it seems better to have the file tucked away in the root users folder.

---

### Post by guilly on 2008-05-27
I took a look at the log and couldn't seem to find any lines with (EE). If you would like I can upload the entire log. I moved the root folder to the vnc directoy but it still seemed to crash as well....

---

### Post by quelx on 2008-05-27
Please attach your log, it may help.

---

### Post by guilly on 2008-05-27
> **quelx said:**
> Please attach your log, it may help.

Here it is. I will check back tomorrow.

Thanks for your help

---

### Post by quelx on 2008-05-27
Is this with or without the VNC module loaded (or trying to load)?

Does xfce load when you comment out the two vnc lines?

I didn't see anything unusual (including any hint of vnc modules loading or not loading)

and snippets from /etc/X11/xorg.conf
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        Option          "PasswordFile"  "/root/.vnc/passwd"
EndSection
.
.
Section "Module"
        Load            "glx"
        Load            "vnc"
EndSection
```

The **only** two lines that need to be added are lines with **vnc** in them, they just need to be in the correct sections.

For reference (I'm not showing off) here is the relevant parts of my log.  Something regarding vnc should show up here, even if it breaks, it should have an **EE** line with something about not finding **libvnc.so**

/var/log/Xorg.0.log
```
(II) LoadModule: "vnc"
(II) Loading /usr/lib/xorg/modules/extensions//libvnc.so
(II) Module vnc: vendor="RealVNC Ltd"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension VNC
```

---

### Post by guilly on 2008-05-28
That was with the vnc module loaded. Maybe I didn't put it in the right place though. I just simply took the code you gave me and put it at the end of my xorg.conf file. I'm not very familiar with xorg. So it's possible that it wasn't placed in the right section.

---

