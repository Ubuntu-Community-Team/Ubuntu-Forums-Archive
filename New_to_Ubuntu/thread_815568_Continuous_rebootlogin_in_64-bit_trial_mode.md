---
title: "Continuous reboot/login in 64-bit trial mode"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by DBell5 on 2008-06-01
I just downloaded Desktop 8.04, AMD 64-bit version, for my HP Athlon PC. Before installing completely, I wanted to run the trial mode, booting Ubuntu from the CD I made.

Kernel loads, and the startup window comes up, asking for a user id. Says "User UBUNTU will log in in ... seconds"

If I let the timer run out, the system resets, monitor gets <no signal>, and Ubuntu starts back up, to repeat the same cycle.

Any idea what's happening?

Dave

---

### Post by Joeb454 on 2008-06-01
Are you sure your Processor is 64-bit compatible? And did you check the CD for defects?

(Only 1 more question) What speed did you burn the CD at?

---

### Post by DBell5 on 2008-06-01
> **Joeb454 said:**
> Are you sure your Processor is 64-bit compatible?
Well, the sticker says "AMD 64 Athlon X2", and I'm running Windows XP x64, so yeah, pretty sure.  :{)

> **Joeb454 said:**
> And did you check the CD for defects?
Ah - that I didn't do! I've seen something to that effect; is it in the auto-run (under Windows) menu?

> **Joeb454 said:**
> What speed did you burn the CD at?
Didn't notice. I think the default was 24x.

Dave

---

### Post by Joeb454 on 2008-06-01
Ok I think it's an option on the boot menu of the CD to check for defects, could be mistaken though.

And I'm guessing it's a bad burn - you could try re-burning the CD at 1-4x speed instead, which reduces the risk of bad burns.

Also If you wanted to try a different app - I'll recommend [ImgBurn]("http://www.imgburn.com")

---

### Post by DBell5 on 2008-06-01
> **Joeb454 said:**
> Ok I think it's an option on the boot menu of the CD to check for defects, could be mistaken though.

And I'm guessing it's a bad burn - you could try re-burning the CD at 1-4x speed instead, which reduces the risk of bad burns.

Also If you wanted to try a different app - I'll recommend [ImgBurn]("http://www.imgburn.com")

Well, that's two coasters...
The original disk integrity-checked OK, but I burned a new one at minimum speed (16X for this drive) anyway. Got the same problem.

Anyone?

Dave

---

### Post by Gershnag on 2008-06-06
I'm having the exact same problem with Athlon 64 X2 Dual Core processor, using the 8.0.4 release.

I've run various scans, and everything seems to be OK.
I've tried both server and client 64-bit, doing from-scratch installes.  No difference.

When I do enter the uname and passwd that I created at start, the screen briefly goes black, then the beige color, then back again to the 'user ubuntu' message.

It does not reject the uname/passwd, it appears to accept them, and something just causes it to get thrown back.

I tried an invalid uname/passwd, and I get a message about invalid username/password.

I did ctl-alt-F1 to get to command line prompt, and I'm logged in as myself.  How do I get the graphics client to restart?
The server is already running.

---

### Post by Joeb454 on 2008-06-06
You mean the X session? Ctrl+Alt+F7 :)

---

