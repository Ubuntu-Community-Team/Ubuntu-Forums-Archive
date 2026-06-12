---
title: "Best Forensic Distro"
date: 2007-05-22
forum: Other OS Talk
---

### Post by LaRoza on 2007-05-22
Does anyone know of a good, free Linux distro that is used for forensic investigations? 

Specifically, I want it to:

1. Have a Bit stream copier
2. Have a good data recovery utility
3. Have a hex editor
4. Most important, not alter the original disk.

Thanks for any suggestions!

-edit So far I found FCCU GNU/Linux Forensic Boot CD, Peguinsleuth, any others?

---

### Post by smoker on 2007-05-22
i haven't tried this, but it looks interesting:
[http://penguinsleuth.org/index.php?option=com_wrapper&Itemid=39](http://penguinsleuth.org/index.php?option=com_wrapper&Itemid=39)

hope it helps

---

### Post by LaRoza on 2007-05-22
Thanks!

---

### Post by mips on 2007-05-22
> **LaRoza said:**
> 
4. Most important, not alter the original disk.

Thanks for any suggestions!



Best way not to alter disk is to use a hardware device between the pc&drive that disables "Write" access. 

It is actually a very simple little board that has the "Write" line hardwired to a high or low signal, can't remember.

---

### Post by LaRoza on 2007-05-22
I know about write blockers, but I do not know where to get one for free. I have very little money at this time, but I am interested in buying one soon, can you make a good recommendation? Thanks.

---

### Post by RAV TUX on 2007-05-23
> **LaRoza said:**
> Does anyone know of a good, free Linux distro that is used for forensic investigations? 

Specifically, I want it to:

1. Have a Bit stream copier
2. Have a good data recovery utility
3. Have a hex editor
4. Most important, not alter the original disk.

Thanks for any suggestions!

-edit So far I found FCCU GNU/Linux Forensic Boot CD, Peguinsleuth, any others?

There is only one choice for what you seek:
**[[B]Helix** ]("http://www.e-fense.com/helix/")[/B]

---

### Post by mips on 2007-05-23
> **LaRoza said:**
> I know about write blockers, but I do not know where to get one for free. I have very little money at this time, but I am interested in buying one soon, can you make a good recommendation? Thanks.

You could always google for something like DIY HD write blocker etc and build one yourself if you have the skills.

[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)
[http://www.forensicpc.com/index.asp](http://www.forensicpc.com/index.asp)
[http://www.digitalintelligence.com/index.php](http://www.digitalintelligence.com/index.php)

Edit: Linux "dd" has an issue with discs that have an odd number of sectors, these drives are rare though. BSD does not have this issue.
[http://www.cftt.nist.gov/Notes_on_dd_and_Odd_Sized_Disks4.doc](http://www.cftt.nist.gov/Notes_on_dd_and_Odd_Sized_Disks4.doc)
[https://www.blackhat.com/presentations/bh-usa-03/bh-us-03-willis-c/bh-us-03-willis.pdf](https://www.blackhat.com/presentations/bh-usa-03/bh-us-03-willis-c/bh-us-03-willis.pdf)  page10

---

### Post by LaRoza on 2007-05-23
> 
Edit: Linux "dd" has an issue with discs that have an odd number of sectors, these drives are rare though. BSD does not have this issue.

Thanks, I didn't know that.

---

### Post by techdude2007 on 2007-05-24
Check out BackTrack 2

---

### Post by RAV TUX on 2007-05-26
> **RAV TUX said:**
> There is only one choice for what you seek:
**[[B]Helix** ]("http://www.e-fense.com/helix/")[/B]

OP: have you tried **[B][[B]Helix**]("http://www.e-fense.com/helix/") [/B][/B]yet?

---

