---
title: "Remote Desktop Only Works With Monitor Plugged In?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by akbr on 2008-07-03
I have a strange problem and would really appreciate some advice.

I am hoping to use the "Remote Desktop" function in Ubuntu 8.04 with a Windows VNC client (more specifically UltraVNC Viewer).

Here's the issue:

If I boot up my Ubuntu box connected to a display device, then I am able to connect up with VNC just fine.

If I boot up my Ubuntu box not connected to a display device, then VNC connections won't work. I know Ubuntu is running, because I can SSH in just fine.

I am sure the presence of the monitor connection is the determinative factor here.

What would cause VNC connections to fail in the absence of a physical monitor hookup?  Any ideas?

Thanks in advance!

---

### Post by superprash2003 on 2008-07-03
i remember reading a similar post before.. i dont know whether you could this a bug but yes remote desktop wont work without an attached monitor.. i dont think the previous poster got his answer..

---

### Post by akbr on 2008-07-03
> **superprash2003 said:**
> remote desktop wont work without an attached monitor.. i dont think the previous poster got his answer..

That's a bummer... any way to spoof this and convince Ubuntu that there is actually a monitor attached?

Do you have any suggestions for other VNC-like solutions?

---

### Post by jcr1 on 2008-07-03
could you cut an old monitor cable up and just plug the end into the pc... or just a whole cable?

But I guess it is the completion of being plugged into a monitor it recognise.

---

### Post by akbr on 2008-07-03
> **jcr1 said:**
> could you cut an old monitor cable up and just plug the end into the pc... or just a whole cable?

Hahah, get this:

If I boot my Ubuntu box plugged into a monitor, even if the monitor is completely powered off from boot, things work fine.

If I boot my Ubuntu box with a monitor cable plugged into the box, but with the other end dangling in the air, it doesn't work.

I'm so confused.

---

### Post by allarmguy on 2008-07-03
I use  vnc viewer and my ubuntu computer has no monitor atached...and has working since begining.

---

### Post by akbr on 2008-07-03
Hm... maybe it really is specific to me, then.

Is there any simple way to tell Ubuntu via the CLI to create a virtual display or any other such workaround?

---

### Post by waydownsouth on 2008-07-03
I'm having this exact problem also...

If you plug in the monitor after it has booted, you are faced with a screen saying that ubuntu couldn't find your display adaptor & should it use the low graphics mode... 640x480.

is there a way to force the display resolution without auto detection?

---

### Post by maxbear on 2008-07-08
Actually, I got the same problem.

It really make me surprise ubuntun doesn't work with remote desktop correctly if there is no monitor attached.

Here is the way that I work around it. I boot into recover mode, then select the monitor and change the reolsution (no plug and play). Then it will work for remote desktop. But If I connect all things locally again (mon, mouse, keyword....), the resoltuion will not work locally, so I need to boot into recover mode and select plug and play again.

It's so trouble. I got some pcs without mon, keyboard and mouse running win xp, they just work fine and never have any problem. I don't know why ubutnut will have such a problem there for a long time and never got any fix.

---

### Post by GavynRiebau on 2008-07-18
Ok I had this same problem and have found a solution that has worked for me:
(first make sure that vnc4server is installed)

1. ssh/putty into headless server
2. enter "vnc4server :1"
3. enter "export DISPLAY=:1"
4. enter "x-session-manager &"
5. exit the terminal/putty window and now you should be able to vnc into the monitorless server.

This could probably be put into a script somewhere so that it runs at startup but haven't bothered to figure that out yet, if anyone has an idea of how to do this?

---

### Post by AllGamer on 2011-03-19
i also got the same problem on only 1 of my machines (the one that has an nVidia card), all the other machines works fine

so i'm about to try this work around
[http://blog.olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/](http://blog.olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/)

i noticed that the machine exhibiting the problem, will boot up like a server (command lines only) when a monitor is not detected

but on other machines that has standard video cards, they will just default to 800x600 in VNC due the "unknown" display

---

