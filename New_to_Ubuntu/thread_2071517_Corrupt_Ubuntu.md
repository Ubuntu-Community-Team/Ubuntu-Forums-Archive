---
title: "Corrupt Ubuntu"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Remcotjuuh on 2012-10-15
Hey people,

I just installed my Ubuntu 64-bit and it runs fine. I have one question concerning the relieablity of my machine. When I burned the .iso on a CD I noticed that it was completely filled up, even though it's a 700MB disk and the .iso file was only 694MB. I later on realized that .iso files are compressed and that the acutal burned files may be larger. I installed it anyway thinking that things should work out and till now everything does.

My question: are there any things I should do or take care of concerning the possibility of missing files etc? The only real problem I experienced was that when I want to log in some white pixels show up at first in the background, but they disappear in an instance.

Thanks in advance!

---

### Post by JoshDempsey on 2012-10-15
Did you verify the disc before install?

It really doesn't matter anyway, I'd guess around 99.99% of ISOs are completely fine. About the white dots, it could be related to a number of other things.

---

### Post by Remcotjuuh on 2012-10-15
> **JoshDempsey said:**
> Did you verify the disc before install?

It really doesn't matter anyway, I'd guess around 99.99% of ISOs are completely fine. About the white dots, it could be related to a number of other things.

If you mean checking with to verify, yes, I check the contents of the disk and everything seemed good. I also checked the MD5 checksum, which wasn't the same as the one I downloaded from releases.ubuntu.com , so I'm kind of scared.

I also noticed that only 136 updates could be installed, and not the 140 updates I had with my previous 32-bit Ubuntu. Could this be caused by missing files?

---

### Post by MG&amp;TL on 2012-10-15
> **Remcotjuuh said:**
> If you mean checking with to verify, yes, I check the contents of the disk and everything seemed good. I also checked the MD5 checksum, which wasn't the same as the one I downloaded from releases.ubuntu.com , so I'm kind of scared.

I also noticed that only 136 updates could be installed, and not the 140 updates I had with my previous 32-bit Ubuntu. Could this be caused by missing files?

If the MD5sum is different, that's bad. That said, if you've got a working install, that's great. :)

Probably not. Missing files is probably more likely to cause things like non-working boot sequence and programs.

---

### Post by Cheesemill on 2012-10-15
ISO files aren't compressed. However, when you write an ISO file to a CD it closes the session on the CD meaning that nothing else can be written to the disk, this is why you will see 0MB free on your CD.

Also if these are the white dots you are talking about then they're meant to be there, it's part of the design of the logon screen.
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Ubuntu_12.04_login_fi.png/1024px-Ubuntu_12.04_login_fi.png[/IMG]

---

### Post by Remcotjuuh on 2012-10-15
> **Cheesemill said:**
> ISO files aren't compressed. However, when you write an ISO file to a CD it closes the session on the CD meaning that nothing else can be written to the disk, this is why you will see 0MB free on your CD.

Also if these are the white dots you are talking about then they're meant to be there, it's part of the design of the logon screen.
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Ubuntu_12.04_login_fi.png/1024px-Ubuntu_12.04_login_fi.png[/IMG]

Nope, the dots are larger and more randomly spreaded. If you tell how to make a screenshot on Ubuntu I can show it to you, if it's made in time, since they disappear after a few seconds anyway.

---

### Post by Cheesemill on 2012-10-15
Press the Print Screen button on your keyboard.

---

### Post by Remcotjuuh on 2012-10-15
> **MG&TL said:**
> If the MD5sum is different, that's bad. That said, if you've got a working install, that's great. :)

Probably not. Missing files is probably more likely to cause things like non-working boot sequence and programs.

Hmm, maybe I didn't check it well. It runs well now, exept for the wierd pixels as described.

---

### Post by Remcotjuuh on 2012-10-15
I printscreened it, but know I don't know how to get it into my dropbox. I feel such a noob right now ^^. I can say that the pixels don't disappear in few seconds, but after moving my crusor around.

---

### Post by Cheesemill on 2012-10-15
It should just save the screenshot into your ~/Pictures directory.

---

### Post by Remcotjuuh on 2012-10-15
I noticed I can make screenshots when logged in, but not in the log in screen. Well, it don't see those pixels as a real problem, since they disappear anyway.

The final strange thing was that when I was downloading a program (Wine Windows Program Loader, or however it is called in English) and then suddenly a prompt popped up saying I didn't accept the terms and conditions of some sort of font program. I don't think this is a real problem either, but who knows?

---

### Post by Swagman on 2012-10-15
If he pressed PrtScn then it should have given him a req in which he could choose to save the pic anywhere on his computer. I believe "Desktop" is the default.

I use Shutter & Ksnapshot for screenies

[img]http://img600.imageshack.us/img600/3666/screenshotapp.jpg[/img]

---

### Post by Remcotjuuh on 2012-10-15
I do get this message when logged in, and my default place to safe is pictures, but not when I'm in the log in screen.

---

