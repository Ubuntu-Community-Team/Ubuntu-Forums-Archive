---
title: "How to upgrade Chrome on Ubuntu."
date: 2019-02-03
forum: New to Ubuntu
---

### Post by rocco.martinello on 2019-02-03
[COLOR=#000000][FONT=Liberation Serif]Hi to all,[/FONT][/COLOR]


[COLOR=#000000][FONT=Liberation Serif]I have Google Chrome 70.0.3538.67 on Ubuntu 18.10 Cosmic Cuttlefish and I would like to know how to upgrade it to the latest stable version (Chrome 72.0.3626).[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif]How can I do?
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Thank you in advance for your answers![/FONT][/COLOR]

---

### Post by VMC on 2019-02-03
Here's how I do it:
wget --no-check-certificate [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
then open terminal where file is located, and exec "sudo dpkg -i *deb"

---

### Post by rocco.martinello on 2019-02-03
> **VMC said:**
> Here's how I do it:
wget --no-check-certificate [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
then open terminal where file is located, and exec "sudo dpkg -i *deb"

Hi VMC and thank you very much for your answer!
Upgrade suceeded!!!

---

### Post by deadflowr on 2019-02-03
Chrome adds it's own repositories to Ubuntu when installed, so updates should be provided through Software Updater automatically.

---

### Post by rocco.martinello on 2019-02-03
> **deadflowr said:**
> Chrome adds it's own repositories to Ubuntu when installed, so updates should be provided through Software Updater automatically.
Hi deadflowr, initially Chrome received upgrades automatically, but now - I don't know why - it wasn't up to date.

---

### Post by deadflowr on 2019-02-03
You then run the update command to view where the updating is going up the creek.
```
sudo apt update
```
should tell a tale or two.

**Edit**:
Probably pointless to run it now since the package is updated so things should be back running normal.
But keep the update command in your back pocket for later time if the same happens again.

With chrome a common issue is the signing-keys getting mucked up.
So that you can usually fix with a simple (or not so simple depending on your take) one liner like
```
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt update
```
But that's just one common issue, there are probably a few not so common issues as well.
the update command can help suss those out.

---

