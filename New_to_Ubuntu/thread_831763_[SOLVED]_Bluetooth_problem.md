---
title: "[SOLVED] Bluetooth problem"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-17
Hy all. I have a Asus F3T-AP008 laptop with a built in bluetooth module and I have some problem with it.I can't send files to the computer from my phone, but vice versa it works.I can bond my phone with my computer, but when I try to send files it says "sending  failed". I heard that is a bug in Hardy,did somebody managed to fix it?

---

### Post by subzero316 on 2008-06-17
Install** OBEX **from the synaptics:KS

---

### Post by Troll_the_Great on 2008-06-17
It doesn't work... I installed Obex and no use, I get the same message. :(

---

### Post by scotcella on 2008-06-17
No advice, but I have had the exact same problem!! Even though repeated posted haven't cleared it up!

I'll be watching this thread and hope someone is able to help us!

---

### Post by Troll_the_Great on 2008-06-17
:(:(:(:(:(:(
I hope so too.

---

### Post by Troll_the_Great on 2008-07-01
Nobody?:(

---

### Post by Troll_the_Great on 2008-07-06
Come on guys!I can't believe nobody uses bluetooth in Hardy...

---

### Post by sayakb on 2008-07-06
This works for me ;) :
Activate bluetooth on both PC and Phone. Right click on bluetooth in notification area and click **Browse device.** Find your phone in the list and press **Connect**. Enter Passkey on both sides and the phone will open up in a file browser.

---

### Post by Troll_the_Great on 2008-07-06
A big thanks to you LinuxIsInnovation for your tip.It's working!!!I can finely use my bluetooth.But do you have any idea why can't I just send it directly?

---

### Post by sayakb on 2008-07-06
I'm not sure about this but this probably is a bluez_utils bug. I tried everything: replaced bluez_utils with a previous version, installed obexpushd but none worked for me. Pairing up the devices seems to be the only solution that works. 
Glad I could help :)

EDIT: Please mark the thread as solved.

---

### Post by Troll_the_Great on 2008-07-06
I have another question.This method will work for any phone, or only for smartphones (I have a Nokia N 93).

---

### Post by sayakb on 2008-07-06
Works on my N73 and Moto L2. **Doesn't  **work on my 3230. So I'm not quite sure.

---

### Post by Troll_the_Great on 2008-07-06
Ok, I think we'll live and see :).Thanks again for your answers.
Cheers!

---

