---
title: "Monitor Out of Range"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by P4r4b014 on 2008-08-21
I recently bought a new gfx for my xp boot on my desktop. When I booted into ubuntu i was delighted to see that there were some linux drivers waiting for me. I installed them and restarted.
Now all I can see is, monitor out of range, on my monitor.

Help?

---

### Post by P4r4b014 on 2008-08-21
anybody please? my desktop is useless right now

---

### Post by forger on 2008-08-21
1) What is your graphics card brand/model?
2) What is your monitor brand/model?
3) Is it LCD? Is it connected through VGA or DVI?

Click New Reply in the forum when you are ready to reply.

Post the output of these commands in terminal(Applications > Accessories > Terminal):
```

lspci

```

Also click the "Attachments" (clip) button and upload this file:
 **/var/log/Xorg.0.log**

---

### Post by forger on 2008-08-21
If you can't paste the log file and/or the output of lspci, I hope you have a working internet connection, do the following within the terminal(console):

```
sudo apt-get update
sudo apt-get install pastebinit
lspci > /tmp/topaste
cat /var/log/Xorg.0.log >> /tmp/topaste
pastebinit -i /tmp/topaste

```

Do the commands **exactly** as they appear, it will return a link to pastebin.com

Reply with the pastebin.com link here :)

---

### Post by P4r4b014 on 2008-08-21
I actually can't even see the login screen

---

### Post by forger on 2008-08-21
Well at least answer these:
1) What is your graphics card brand/model?
2) What is your monitor brand/model?
3) Is it LCD? Is it connected through VGA or DVI?

In order to do the other things, try restarting and pressing Esc every second or so, this will show the GRUB boot menu, choose your linux kernel with **(recovery mode)**, it should boot up to a root console, check if this works (i.e. you have internet connection):
```
/etc/init.d/networking restart
sleep 15
apt-get update
```

---

### Post by sherin on 2008-08-21
i would suggest logging in rescue mode and reconfigure xserver. 
Or if you are comfortable with the hard way, try editing xorg.conf  to suit your card/ monitor specifications

---

### Post by tarps87 on 2008-08-21
Try pressing ctrl+alt+F1, if this works login and type:```

sudo dpkg-reconfigure xserver-xorg
```
You can press escape of the keyboard and mouse settings which should keep the original settings, then set the monitor settings.
I hope this helps

---

### Post by prshah on 2008-08-21
> **P4r4b014 said:**
> anybody please? my desktop is useless right now

This error is related to the refresh rate being out of range of your monitor. 

Try pressing Ctrl-Alt-Numpad- and/or Ctrl+Alt+Numpad+ repeatedly; this will keep changing resolutions in an attempt to find one that works. You will have to wait about 2-3 seconds between each press. If you find a resolution that works, post back on how to make it permanent and/or how to get a suitable refresh rate at which ever resolution you like.

---

### Post by tarps87 on 2008-08-21
> **prshah said:**
> This error is related to the refresh rate being out of range of your monitor. 

Try pressing Ctrl-Alt-Numpad- and/or Ctrl+Alt+Numpad+ repeatedly; this will keep changing resolutions in an attempt to find one that works. You will have to wait about 2-3 seconds between each press. If you find a resolution that works, post back on how to make it permanent and/or how to get a suitable refresh rate at which ever resolution you like.

I never knew that, thanks

---

### Post by prshah on 2008-08-21
> **tarps87 said:**
> I never knew that, thanks

Did it work?

---

### Post by tarps87 on 2008-08-21
I don't know, I'm not the op. I've just had the problem before and your way is quicker than having to reconfigure the xorg file, so it will be useful when I do it again.

---

### Post by prshah on 2008-08-21
> **tarps87 said:**
> I don't know, I'm not the op. I've just had the problem before and your way is quicker than having to reconfigure the xorg file, so it will be useful when I do it again.

Oops, beg your pardon. Glad I was (or actually, may be) of assistance. Now to wait for OP's status...

---

