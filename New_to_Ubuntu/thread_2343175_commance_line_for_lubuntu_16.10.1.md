---
title: "commance line for lubuntu 16.10.1"
date: 2016-11-14
forum: New to Ubuntu
---

### Post by linux28 on 2016-11-14
Hello

Apologies if I have posted in the wrong place :)

I use lubuntu 16.04.1 and I would like to update to lubuntu 16.10.1, is there a command line i can use to do so or do i need to install via a usb stick?

Any help appreciated :)

---

### Post by ian-weisser on 2016-11-14
1) Open a Terminal
2) Run the command: ```
do-release-upgrade
```
3) Allow at least an hour for your release-upgrade. Do not poweroff/suspend/hibernate while the release upgrade is installing. Pay attention occasionally - the release-upgrade-installer will ask you several questions.

---

### Post by linux28 on 2016-11-14
thank you so much for your quick reply :)

---

### Post by DuckHook on 2016-11-14
```
do-release-upgrade
```...must be run with *sudo*. Otherwise, *ian-weisser's* instructions are good to go.

Do you know that 16.04 is an LTS release and will be supported for 5 years, whereas 16.10 is sort of a power user's release and will only be supported for 9 months? It is not necessary to always upgrade to the latest release and is not, in fact, recommended for general users.

---

### Post by linux28 on 2016-11-14
I didnt know that so won't update after all, thanks for the info :)

---

### Post by deadflowr on 2016-11-14
No need for sudo to run do-release-upgrade as do-release-upgrade will ask for the administrative password when the time comes.

---

### Post by oldos2er on 2016-11-14
There is no 16.10.1 (and never will be), the next version release will be 17.04 in April 2017.

---

