---
title: "Mplayer display"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by nnjond on 2008-06-29
Hi, Can anyone help me?

My Mplayer display won't fullscreen; It's stuck on postage stamp.

---

### Post by pytheas22 on 2008-06-29
How are you trying to make it full screen?

---

### Post by neurostu on 2008-06-29
Did you try F11, that usually makes things go fullscreen.

---

### Post by kuja on 2008-06-29
Pressing 'F' should take it to full screen. If you have difficulty doing this, it may be an issue with the vo driver. Try starting mplayer like "mplayer -vo xv somefile.avi", important part being -vo xv. If this fails, it's probably a problem with video acceleration. In which case this page might come in handy: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

