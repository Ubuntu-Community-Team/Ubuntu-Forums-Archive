---
title: "When I plug in LCD monitor to laptop, linux crashes"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by hanzj on 2012-06-01
With my LCD monitor plugged in via VGA cable to my laptop, I get all the way to my login screen, but after I enter my username and password and press enter, all I see is a black screen.

If I startup Linux without the external LCD monitor plugged in, everything seems to work fine. But when I plug in the LCD monitor, the computer crashes.

This is strange. When I boot into my Windows partition, the external LCD monitor does not cause any problems.

Could any one help me figure out what's going on?

---

### Post by inashdeen on 2012-06-01
First off, may you share you pc specification?
RAM, hard disk, graphic card. most issue are related to graphic cards.

---

### Post by hanzj on 2012-06-01
inashdeen,
Thanks for your reply. Sure, happy to give information.

Intel Pentium P6200 @ 2.13 GHz
4GB ram (3.8 usable)

How can I give you hard drive info and graphics card details in Win7?

---

### Post by Shadius on 2012-06-01
> **hanzj said:**
> inashdeen,
Thanks for your reply. Sure, happy to give information.

Intel Pentium P6200 @ 2.13 GHz
4GB ram (3.8 usable)

How can I give you hard drive info and graphics card details in Win7?

For the hard drive, just go into **My Computer** and tell us the overall space. 

For the graphics card, go to **Start**>**Control Panel**>**Appearance and Personalization**>**Personalization **>**Display Settings**>**Advanced Settings**>**Adapter** tab.

---

### Post by hanzj on 2012-06-01
Thanks, Shadius.

C: Drive has 53 GB free of 162 GB

Adapter type is Intel HD Graphics (Pentium). Total available graphics memory: 1696 MB. Dedicated video memory: 64 MB. System video memory: 0 mb. Shared system memory: 1632 MB.

Thanks!

UDPATE: I realized that my Windows-specific info probably doesn't help, as the hanging happens in Linux partition and not Windows. On the Linux partition, I have about 60 GB free.

---

### Post by Shadius on 2012-06-01
Does it crash if you try using a LiveCD? Puzzling...

---

### Post by hanzj on 2012-06-02
Dear Shadius and others,

When I plugged in the Live USB, there is no problems. Should I reinstall linux? I don't mind, if only it will help solve things.

---

### Post by Shadius on 2012-06-02
> **hanzj said:**
> Dear Shadius and others,

When I plugged in the Live USB, there is no problems. Should I reinstall linux? I don't mind, if only it will help solve things.

I'd say reinstall as a last resort, but if you've backed up your data and don't mind doing the reinstallation, then I think that would solve the issue.

---

### Post by hanzj on 2012-06-02
shadius,
yes, reinstalling should be the last resort. I think it would be good to figure out what is going on. 

Generally speaking, is this  a hardware problem? Or a software problem?
Can we pinpoint what exactly is causing the issue?

Would it help if I could copy and paste the messages that appear after I power on the computer and before I reach the Linux login screen? What about the messages that appear when I choose restart/power-off? If these messages are helpful, is there a way to paste them here, or must I take a photograph with my digital camera?

---

### Post by Shadius on 2012-06-02
> **hanzj said:**
> shadius,
yes, reinstalling should be the last resort. I think it would be good to figure out what is going on. 

Generally speaking, is this  a hardware problem? Or a software problem?
Can we pinpoint what exactly is causing the issue?

Would it help if I could copy and paste the messages that appear after I power on the computer and before I reach the Linux login screen? What about the messages that appear when I choose restart/power-off? If these messages are helpful, is there a way to paste them here, or must I take a photograph with my digital camera?

It might be helpful to see the messages, but I don't think I would know how to move forward with the error messages since I solved the same issue by reinstalling, but perhaps another user might know of a way. Couldn't hurt to post the error messages. Try and get them with whatever method you can. I'm thinking it's a hardware driver issue.

---

