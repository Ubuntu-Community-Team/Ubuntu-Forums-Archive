---
title: "Running as Super-User"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by lol_u died on 2008-08-30
Hey people. Ok So i managed to get past the text editor when ever I click on the ati driver installer for Ubuntu 8.04 (Hardy). And Now it gives me options. Either Run in Terminal or just run. I choose terminal first and it asked me to be in Super-User. Which I SHOULD be because I am the ONLY user on this computer xD And then I tried the Regular run option and still! It asks me to be in super-user. please help me! I need to know how to make myself super-user even though I'm the only user on this particular computer!
:guitar:

---

### Post by Joeb454 on 2008-08-30
Hit Alt+F2 and enter ```
gksudo gedit /path/to/your/file
``` Naturally - replace the last part with the correct path

---

### Post by drs305 on 2008-08-30
As to why you aren't automatically the superuser, this will answer some of your questions:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by lol_u died on 2008-08-30
No Non of these worked.

---

### Post by kellemes on 2008-08-30
> **lol_u died said:**
> No Non of these worked.

You should read the link *drs305* gave you, it explains it all.

---

### Post by PriceChild on 2008-08-30
Sounds like you're installing a driver from outside the repositories... which probably isnt a good idea if you're not sure about what you're doing.

Check out [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto) and see if that helps.

---

### Post by Joeb454 on 2008-08-30
If you need the latest drivers for something, then you could try using EnvyNG

---

### Post by Vivaldi Gloria on 2008-08-30
> **lol_u died said:**
> when ever I click on the ati driver installer for Ubuntu 8.04

Have you looked at

Top panel, System menu > admin. > Hardware drivers

---

