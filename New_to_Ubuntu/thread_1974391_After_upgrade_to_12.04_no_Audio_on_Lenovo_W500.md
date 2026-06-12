---
title: "After upgrade to 12.04 no Audio on Lenovo W500"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by Wukiblue on 2012-05-06
Hi all, 

after upgrading to 12.04 I have no audio any more when streaming videos on my W500 (on Oeneric everything worked perfect!!).

Who can help?

---

### Post by Wukiblue on 2012-05-08
Checked with alsamixer, but speakers are enabled and at +0 db.
I have clear sound and signal on head phone out, but my laptop speakers are dead.

I use
- Advanced linix sound architecture driver v 1.0.24

HDA-Intel - HDA Intel                                   &#9474;
&#9474;                      HDA Intel at 0xfc220000 irq 49                          &#9474;

[ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control            &#9474;
&#9474;                      ThinkPad Console Audio Control at EC reg 0x30, fw 7VHT14&#9474;




Can some one help?

---

### Post by iMurshaq on 2012-05-09
Here is a page on debugging sound problems on wiki.ubuntu.com

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by iMurshaq on 2012-05-09
Also try using the command below and post your output. If there is not a large list that appears then the sound modules weren't installed.

```
find /lib/modules/`uname -r` | grep snd
```

---

### Post by Wukiblue on 2012-05-09
Many thanks for the hints.

I ran "find /lib/modules/`uname -r` | grep snd" and received a long list of installed modules. So this seems to be OK.

Then I tried "system settings", "sound","speakers" and figured out that the output volume was set to 10%. After moving the lever to 100% , everything was OK and I had audio sound on both headphone and speakers.

Thank you for the guidance!!

---

### Post by iMurshaq on 2012-05-09
Happy to help, also you should change the prefix of this thread to solved.

---

