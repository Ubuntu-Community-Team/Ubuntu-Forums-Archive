---
title: "[SOLVED] PC Restarts Instead of Shutting Down"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Teasdale on 2008-09-10
We have Ubuntu on two PC's. On my son's, when you click "shut down," Ubuntu logs off, powers down, and then the PC shuts off.

On mine, Ubuntu logs off, powers down - and then stops right there, hanging on the Ubuntu screen. Okay, so I have to manually push the power button on the tower. I can live with that.

The problem is - doing that doesn't always shut off the PC, it triggers Ubuntu to restart! Because, in order to shut down, you have to hold the power button down for a few seconds until it goes off - but if you hold it down a tenth of a second too long, it restarts.

So, if there's a lightning storm (like there is now) and I want to turn off the PC's, most of the time, this one restarts - I have to go through the whole process of watching the black screen, logging in, waiting for all the programs to start up - all so I can try to turn it off again, meanwhile it's thundering and lightning.

Should I just pull the electrical plug after Ubuntu logs off instead of using the power button?

When I had WinXP on this PC, it would just shut itself off when I clicked "shut down." I miss those days.

---

### Post by Crafty Kisses on 2008-09-10
Have you checked your error logs?

---

### Post by Kellemora on 2008-09-10
Hi T

Restart is a function of the computers own BIOS!

It can be set to Reboot after power outage rather than remaining powered down or off.

These new buttons are NOT on and off switches, they merely signal the computer's internal program for how they are set.  
2 of my computers the front panel button has 3 options, a short quick press under 3 seconds, a medium length press 4 to 6 seconds and a long press over 7 seconds.
Normally, the long press over 7 seconds would shut the computer off completely, except I have it set to restart after power outage.
The Short press is geared for windows to log off and Shut Down normally then restart.
The Medium press is geared for windows or any OS to shut-down immediately and restart
The Long press would normally power down completely, instantly, if I didn't instruct the BIOS to restart after power outage.

Hope that makes sense!

TTUL
Gary

---

### Post by srt4play on 2008-09-10
Try shutting down with this in a terminal:

```
sudo shutdown -P now
```

---

### Post by Teasdale on 2008-09-10
> **srt4play said:**
> Try shutting down with this in a terminal:

```
sudo shutdown -P now
```

I'll try this first.


I figured it had something to do with a BIOS setting - although I can't imagine how something like that would change by installing Ubuntu. If I need to go into the BIOS, I'll wait until my son is here from college so I at least have some moral support. Hopefully the terminal command is all I'll need.

---

### Post by Teasdale on 2008-09-12
I tried the terminal command. It went to a black screen with a lot of writing on it (lots of things said "failed"?) and then it unloaded Ubuntu and went to the Ubuntu screen. I assumed it hadn't worked, so I left it like that and went to bed.

This morning, I clicked the power button on the PC tower (the screen still had the Ubuntu logo displayed) and held it, figuring it would restart - but it didn't, it actually shut off! So I think it worked!

I'd like to verify that before I put a "solved" label on this, though - I'll shut it down this way again tonight.

---

### Post by Teasdale on 2008-09-19
> **Teasdale said:**
> 
I'd like to verify that before I put a "solved" label on this, though - I'll shut it down this way again tonight.

I shut down the PC successfully with this terminal command again; I still have to press the power button, but at least that actually does shut down instead of restarting.

This is now solved - but I can't figure out how to edit the title.

---

### Post by Crafty Kisses on 2008-09-19
You can mark the thread solved in thread tools.

---

