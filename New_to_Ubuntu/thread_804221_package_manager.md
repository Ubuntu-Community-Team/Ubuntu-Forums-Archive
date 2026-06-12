---
title: "package manager"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by meirizal on 2008-05-22
I am a linux beginner, i use ubuntu 7.04 (feisty) on my pc but i cannot run package manager. there is an error massage on screen which says as below :

E: Type '--16:43:32--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

what should i do, thank you.

---

### Post by iaculallad on 2008-05-22
> **meirizal said:**
> I am a linux beginner, i use ubuntu 7.04 (feisty) on my pc but i cannot run package manager. there is an error massage on screen which says as below :

E: Type '--16:43:32--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

what should i do, thank you.

On your terminal, input this commands (If you're on Hardy):

**sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list**

[B]sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[/B]

---

### Post by oedha on 2008-05-22
check the content of your sources.list then pay attention on line 1 ( fix it or deactivate it by adding # )
in terminal type :==> sudo gedit /etc/apt/sources.list

---

### Post by meirizal on 2008-05-26
thank you so much for your post. since i use feisty on my pc, so i changed the word hardy by feisty and it works.

---

### Post by kesman on 2008-05-26
Great shot! =D Usually people don't try these kind of stuff on their own, which causes thousands of useless requests for help on these forums. Many people are uncapable of seeing the answer which is right there in front of their eyes.

---

