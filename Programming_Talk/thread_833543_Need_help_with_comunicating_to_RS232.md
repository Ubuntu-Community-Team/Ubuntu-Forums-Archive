---
title: "Need help with comunicating to RS232"
date: 2008-06-18
forum: Programming Talk
---

### Post by MR.UNOWEN on 2008-06-18
Hello,

I'm new to C++ and I need help figuring out how to send information to the rs232 port. It's going to be one way communication (PC to device). I've tried reading other tutorials, but none of them clearly explain what's going on in each part, so I often get lost. Could some write up a simple example of sending a single byte of data and show where you set up the baud rate and other stuff. Also what's the best way to produce a time delay in C++?

---

### Post by dtmilano on 2008-06-18
Check tcgetattr/tcsetattr (man or [here]("http://linux.about.com/library/cmd/blcmdl3_tcgetattr.ht")).

---

