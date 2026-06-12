---
title: "overheating shut down"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by protpisys on 2014-07-08
why does my computer overheat and shut off when I watch videos. I'm dual booting an old Toshiba Satellite w/Vista. which never overheats or shuts off in the middle of a video.

---

### Post by tgalati4 on 2014-07-08
What is the graphics card?

```
lspci | grep VGA
```

It's possible that in linux your video is being rendered in software, by the CPU and in Vista, it is being rendered by the graphics GPU, and thus the CPU stays cool.

---

### Post by protpisys on 2014-07-08
would that be the ATI Radeon X1250 perhaps?

---

### Post by claracc on 2014-07-09
Perhaps these two links can help you to solve the problem?:

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by sp40140 on 2014-07-11
Also, you might want to install power management app. Do you have AMD cpu on the machine?
try tlp and see if it helps
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

---

