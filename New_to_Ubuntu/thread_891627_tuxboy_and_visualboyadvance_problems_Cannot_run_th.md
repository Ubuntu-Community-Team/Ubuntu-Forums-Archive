---
title: "tuxboy and visualboyadvance problems? Cannot run them?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Pascal11110 on 2008-08-16
I have them both on my desktop (they are both gameboy emulators) and I am trying to run them, how do I do it?

---

### Post by Pascal11110 on 2008-08-16
How do I run programs that have downloaded that are on my desktop? For example mI have a tuxboy.1686 and a VisualBoyAdvance.exe

---

### Post by CautionaryX on 2008-08-16
please only one thread at a time for your question.

reported.

---

### Post by dje on 2008-08-16
VisualBoyAdvance.exe is a windows program which does not run natively in Linux. It **may** run in wine, to install wine run the following in a terminal (applications >> accessories >> terminal):
```
sudo apt-get install wine
```
then double click on VisualBoyAdvance.exe. to check compatibility check at [http://appdb.winehq.com]("http://appdb.winehq.com")

dje

---

### Post by Pascal11110 on 2008-08-16
Well I already have wine, and nothing happens when I click on the .exe file

---

### Post by overdrank on 2008-08-16
Thread closed duplicate [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?p=5600975#post5600975)
Please do not create multiple threads on the same issue.

---

### Post by dje on 2008-08-16
> **Pascal11110 said:**
> Well I already have wine, and nothing happens when I click on the .exe file

have you checked the compatibility at [http://appdb.winehq.com]("http://appdb.winehq.com")? also please run this from the terminal and post the output:
```
wine $HOME/Desktop/VisualBoyAdvance.exe
```

dje

---

### Post by dje on 2008-08-16
Ignore previous post there is a native version of VisualBoyAdvance, in a terminal do:
```
sudo apt-get install visualboyadvance
```
in future it's always a good idea to check the repositories and please dont double post ;)

dje

---

### Post by CautionaryX on 2008-08-16
Also, have you checked the repositories for any GBA emulators? VisualBoyAdvance is in the repositories, no need to use WINE.

```
sudo apt-get install visualboyadvance visualboyadvance-gtk
```

Try that and see if it works.

EDIT: dje beat me to it

---

