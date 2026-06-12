---
title: "Running in Low Graphics Mode"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by richie42 on 2008-08-10
Hi,my Ubuntu version 8.04 computer was running fine, but now I shut it down. When I turned it back on, it is now running in low graphics mode, apparently the graphics card is not compatible wih Ubuntu. What is going on? I need help. I am running an NVIDIA card...

---

### Post by richie42 on 2008-08-10
Okay, I see that my graphics card driver cannot be supported by Ubuntu. Can I get some help. It was running good for three days and then this happened. What is going on?

---

### Post by tuxxy on 2008-08-10
Did you try and reinstall the driver? did you recently edit any settings for the device?

If the drivers did previously work but now fail you could try and reconfigure xorg from the terminal by entering this command

```
sudo dpkg-reconfigure xserver-xorg
```

Now try and enable the drivers again

---

### Post by richie42 on 2008-08-10
This shows up, do I say yes?

>       &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                                                                     &#9474; 
 &#9474; Rather than communicating directly with the video hardware, the X server  &#9474; 
 &#9474; may be configured to perform some operations, such as video mode          &#9474; 
 &#9474; switching, via the kernel's framebuffer driver.                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; In theory, either approach should work, but in practice, sometimes one    &#9474; 
 &#9474; does and the other does not.  Enabling this option is the safe bet, but   &#9474; 
 &#9474; feel free to turn it off if it appears to cause problems.                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Use kernel framebuffer device interface?  

---

### Post by richie42 on 2008-08-10
And for the record, I dont kinow how to do either for eother of your questions. (Yes, I am a n00b)

---

### Post by richie42 on 2008-08-10
I need help. I accidentally closed the window that the process was in, and when I went into terminal again, I got this:

```
richard@theSelbys:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for richard: 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
richard@theSelbys:~$ 

```

---

### Post by richie42 on 2008-08-10
Okay, I restarted the computer and I posted that code in agai, going through all the actions, I got this:

What does this mean

```

richard@theSelbys:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for richard: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080810215647
richard@theSelbys:~$ 






```

---

### Post by richie42 on 2008-08-10
Okay, I uninstalled and reinstalled the driver using EnvyNG and it is fine. Now, is there a problem that makes the computer "lose" the driver. This is just creating more questions than are solved. I am going to enable the driver and see what happens from there.

---

### Post by richie42 on 2008-08-10
Okay, I restarted the computer after enabling the driver. It is back to the same problem. No, intrestingly, the box that says "in use" is checked in Hardware drivers. Is thre a problem here, *yes* there is. Now, I need help in getting this graphics problem fixed.

---

### Post by richie42 on 2008-08-10
bump, Please i need help

---

### Post by tuxxy on 2008-08-11
If the driver works when you install through envy you could try reconfiguring the xorg and follow the process through, now install through envy and dont use the system > admin >hardware drivers?

---

### Post by pietjanjaap on 2008-08-11
With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by edog76 on 2008-08-11
You might try something along the lines I did, as your problem sounds similar.

[http://ubuntuforums.org/showthread.php?t=884395](http://ubuntuforums.org/showthread.php?t=884395)

EDIT: I'm a noob, so I can't do much more than offer my own learning experience.

---

