---
title: "Changing login background very easily"
date: 2015-01-27
forum: New to Ubuntu
---

### Post by Vekszor on 2015-01-27
Hello there I am new to Ubuntu, I was trying to change login screen the other day and searched the forum and found quite a few different solutions, from installing programs, tweaks, or typing complicated commands in terminal. But then, _I found the solution myself_, one which I couldn't find on this forum so I wanted to share my discovery here with you, it is nothing special, it is just easy.

So, that purple default login background picture is located in "/usr/share/backgrounds/" and is called warty-final-ubuntu.png . So my idea was just to put another png picture there with that name and restart os.
So I went to terminal, did "sudo -i", became root, went to "/usr/share/backgrounds" and using commands cp (copy) and mv (move) I renamed original picture to warty2.png, and new picture of my choice to warty-final-ubuntu.png . exit terminal, restart, and it works.

---

### Post by mooreted on 2015-01-27
Sometimes the simple answer is the best answer.

---

