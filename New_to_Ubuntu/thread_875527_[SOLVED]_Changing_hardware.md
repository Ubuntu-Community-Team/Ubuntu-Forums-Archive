---
title: "[SOLVED] Changing hardware"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by DarchAengel on 2008-07-30
I just took the hard drive out of my Dell that was running Ubuntu HH.  I just put it into a Compaq Presario 6000.  When I start to boot it it goes to a text prompt, stays there for a minute or so then says that I need to configure the graphics card and and monitor.  No matter what I try it will go to a black screen and stay there.  Is there a way I can make it stay at the prompt screen so I can run the configuration commands?

---

### Post by tuxxy on 2008-07-30
Try opening a ttyl by pressing CTRL + ALT + F1

If you can get to a command line, do the following command to reconfigure the xorg.

```
sudo dpkg-reconfigure xserver-xorg
```

Complete the process and it should start if not try,

```
startx

```

---

### Post by DarchAengel on 2008-07-31
I got as far as typing Ctrl + Alt + F1 and got to the login prompt but it flickers and goes back to the low graphics warning way too quickly before I can finish logging in.  I need to find a way to freeze whatever it is that it's doing.

---

### Post by tuxxy on 2008-07-31
Try entering maintenance mode, so press the ESC when you first power up, after the BIOS display should display it. 

You have to do it in time before it boots into the normal kernal though, now select the recovery mode and try and run the command this method.

---

### Post by DarchAengel on 2008-07-31
I got to recovery mode.  It asked me what I wanted to to and I chose to go the root prompt.  I put in the xorg command.  I started the reconfigure process and got as far as the emulate 3 button mouse question.  Regardless of what I choose I get the following error:

```

xserver-xorg postinst warning: Overwriting possibly-customized configuration file; backup in /etc/x11/xorg.conf.20080731004443

```

It then goes back to the root prompt.  Did I screw up somewhere?

---

