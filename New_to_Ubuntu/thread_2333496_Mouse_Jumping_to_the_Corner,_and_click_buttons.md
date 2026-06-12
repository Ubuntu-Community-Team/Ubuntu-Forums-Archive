---
title: "Mouse Jumping to the Corner, and click buttons"
date: 2016-08-10
forum: New to Ubuntu
---

### Post by arukas2 on 2016-08-10
While searching I did find other people with mouse problem but not the same problem.  Majority of the posts I found had involved a laptop and/or touch pad, and the rest seem to be about virtualization.  I have a desktop and a normal mouse, and I was running the live CD.  My intent is to setup a dual boot system.  

Also, I don't understand quite how I would fix it.  I had to hard reset because the mouse is also clicking by itself.  

Anyone can shed light on what the issue is?  And how do I fix it ( I mean the process, with the mouse acting all funny)?

-Thanks

---

### Post by deadflowr on 2016-08-10
What model mouse?

---

### Post by arukas2 on 2016-08-10
It and old logitech 6500 mouse.

---

### Post by arukas2 on 2016-08-10
I unplugged the mouse, and I still have problem with the mouse clicking like made.  Its like someone is trying to click as fast as they can go the mouse.

---

### Post by arukas2 on 2016-08-10
I've been playing around with it some more.  It looks like it just the mouse is fine, then something loads up and then freaks out.

---

### Post by Peter_Horn on 2016-08-11
I had something similar a while back. It turned out to be a phantom second monitor. Went into display settings, disabled the second one and all is sweet.

---

### Post by arukas2 on 2016-08-11
What ever is causing the problem, it looks like it moves the mouse in the upper right column, and clicks like mad.  

The problem is it doesn't allow me to control the UI through the keyboard, how do I fix it?  The problem kind makes the UI unworkable.

---

### Post by &amp;KyT$0P# on 2016-08-11
In case it helps, since you have a working keyboard you can get into a Terminal with Ctrl-Alt-F1 (or through Ctrl-Alt-F6).

(Use Ctrl-Alt-F7 to get back to the GUI)

---

### Post by arukas2 on 2016-08-12
I don't understand exactly what I am suppose to do once I get to a terminal.  

Also, I ran the installer just to see what would happen, but the installer doesn't work because what ever is controller the mouse is causing problems.

I did installed Ubuntu on a virtual machine, and that seems to run perfectly for some reason.  no mouse issues there.  

I also read something about ps2 port causing problem because my computer doesn't have one.

---

### Post by arukas2 on 2016-08-12
I figured out my problem thanks to the help:

1)  The ctrl-atl-f1/f6 did not take me to a terminal, took a logon.
2)  A ctrl-alt-T (I think it was ctrl-alt)
3)  I had to type "sudo modprobe -r psmouse" to make the problem go way.

Anyone explain what that command is doing?  I sit just turning off the ps2 ports?

---

### Post by wildmanne39 on 2016-08-12
The command unloads the driver that controls your mouse but it is only for the current session when you reboot it will load that driver again.

If you want to stop it from loading permanently do:
```
echo "blacklist psmouse" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by mook765 on 2016-08-12
The command "sudo modprobe -r psmouse" removes the psmouse-module from the kernel.
You may open the terminal and type "man modprobe", this will lead you to the manual off the command.
to leave from the manual press just "q".

---

