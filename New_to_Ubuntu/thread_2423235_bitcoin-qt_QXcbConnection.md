---
title: "bitcoin-qt QXcbConnection"
date: 2019-07-19
forum: New to Ubuntu
---

### Post by walletcat on 2019-07-19
After the installation process I receive a notification
```
"Warning: The home dir /var/lib/bitcoin you specified can't be accessed: No such file or directory
Adding system user `bitcoin' (UID 113) ...
Adding new group `bitcoin' (GID 122) ...
Adding new user `bitcoin' (UID 113) with group `bitcoin' ...
Not creating home directory `/var/lib/bitcoin'.
bitcoind.service is a disabled or a static unit, not starting it. "
```


I started opening bitcoin-qt unsuccessfully
```
" sudo bitcoin-qt
QXcbConnection: Could not connect to display
Aborted (core dumped)"
```


I'm using Ubuntu 16.04
user sudo but not root
Is there any way to solve this problem?

---

### Post by walletcat on 2019-07-19
No support for this issue?

---

### Post by again? on 2019-07-19
Not something I use but I installed from a [ppa]("https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin") to look at.
When first run I am presented with this dialog to select a data directory.
[ATTACH=CONFIG]283640[/ATTACH]

Default is ~/.bitcoin which it will create.
From the error it appears you selected /var/lib/bitcoin... where the user does not 
have permissions to write.

Check your data directory in ~/.config/Bitcoin/Bitcoin-Qt.conf
```
grep strDataDir ~/.config/Bitcoin/Bitcoin-Qt.conf
```
eg
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] grep strDataDir ~/.config/Bitcoin/Bitcoin-Qt.conf**
strDataDir=/home/glen/.bitcoin
```


If I remove both directories **~/.bitcoin** and **~/.config/Bitcoin**
I get the dialog to chose my data directory again when starting bitcoin-qt.
Don't have bitcoin or a spare **250Gb** so can't test further.

[COLOR="#FF0000"]****Note link below****[/COLOR]
[Why should users never use normal sudo to start graphical applications?]("https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications")

---

