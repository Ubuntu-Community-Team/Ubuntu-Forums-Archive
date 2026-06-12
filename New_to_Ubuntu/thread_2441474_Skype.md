---
title: "Skype"
date: 2020-04-23
forum: New to Ubuntu
---

### Post by hallyguitar on 2020-04-23
Hi, i am having a problem with Skype. When i do a test call id doesn't pick up my mic. The mic seems to be working as i can tell with pulse audio. I also have zoom and the mic works perfectly in that,
Please help i'm new to this.

---

### Post by mastablasta on 2020-04-24
1. check skype in settings if correct mic (or mic input) is chosen.
2. check in sound mixer to see that correct  mic input is selected as default.
3. check in sound mixer to see if correct mic is selected for Skype application.

4. run alsamixer in CLI, then check to make sure the mic volume is turned up.
5. in system settings check mic volume. try to test it there.

if you run skype from terminal, it will give you error outputs. there are also some error logs available. perhaps in the hidden ./skype folder in your /home? it's beena while since i messed around with skype because ever since 10.04 came out back in 2010 it has always been working out of the box with default settings.

that's about all i can think of right now.

i use Kubuntu and while mic worked well in Skype it didn't work in CS:GO game. after trying various settings etc. i found that wrong input was defaulted in that game. perhaps this is similar situation but in reverse.

---

### Post by hallyguitar on 2020-04-24
Thank you so much, that worked a treat.
Its taken me 3 days to sort that out.

---

