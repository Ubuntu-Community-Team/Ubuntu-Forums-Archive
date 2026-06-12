---
title: "14,10 last update - random freeze"
date: 2014-12-20
forum: New to Ubuntu
---

### Post by Rrory on 2014-12-20
My laptop is freezing randomly since the last update,  I use both Firefox and Chrome browsers, when i play youtube video, but equally when I'm reading yahoo mail...I have to push the off button and restart  which I know isn't a good thing....

---

### Post by carl4926 on 2014-12-20
Try the previous kernel from the grub menu

---

### Post by flaymond on 2014-12-20
What hardware specs do you have?

---

### Post by Bucky Ball on 2014-12-20
There's been a few threads regarding this after the most recent 14.10 update. Try the previous kernel for the moment and try the new one again after the next update, perhaps.

When the machine freezes you could try restarting by hitting control+alt+F1. This should put you at a cli. Log into that then:

```
sudo reboot -h now
```

---

### Post by Rrory on 2014-12-20
Tried Ctrl +alt+F1   didn't work. And I cant use the previous kernel as due to my install (I installed Ubuntu alongside the UEFI partition) I had a tiny /boot and eliminated the extra kernels to give me some space, so I could  update...Arg..if I did a fresh install from my flashdrive would this solve my partition problems...

---

### Post by maximCH on 2014-12-25
I have the exact same problem. This has been happening since kernel 3.13.0-41. I have gone back to -40 and since them I'm up for 20h. Usually I had the freeze anywhere between 3 and 15 hours.

Also Ctrl-Alt-F1 or any Alt-SysRq combinations will not work. There's nothing in the logfiles either that's of any use.

---

