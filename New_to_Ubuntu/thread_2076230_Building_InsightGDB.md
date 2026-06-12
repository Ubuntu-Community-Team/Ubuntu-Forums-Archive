---
title: "Building Insight/GDB"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by Aspras on 2012-10-25
I am trying to build an arm targeted Insight/GDB version 6.8-1. 
I configured with parameters *--target=arm-none-eabi --disable-werror*.
I then execute make all, [this]("http://pastie.org/pastes/5115684/text") is the output.

Coming from windows I kind of feel lost so any help would be appreciated :)

---

### Post by Aspras on 2012-10-28
Managed to get further by installing a few libraries which took care of most of the problems I was facing.
However make still returns an exit status of 1 and as usual I can't figure out what the cause is. [Here]("http://pastebin.com/raw.php?i=w0Pv0eaU") is the output near the end.

---

