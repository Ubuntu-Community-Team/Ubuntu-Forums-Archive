---
title: "update macchanger???"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by Vanity on 2011-11-05
what is the command to update macchanger? I input sudo apt-get update macchanger but it doesnt find the command. 

when I install it gives me a warning that not all files were installed. 

can anyone help me out here?

V-

---

### Post by davdo2004 on 2011-11-05
sudo apt-get -u install macchanger

---

### Post by Vanity on 2011-11-05
after inserting 
```
sudo apt-get -u install macchanger
```I get the same errors. I attached a screen shot of the output from terminal.

---

### Post by Vanity on 2011-11-05
okay so i see the screen shot didnt upload ooops I will get it on there tonight but does anyone have any idea why macchanger wont update?

---

### Post by dFlyer on 2011-11-05
can you tell with the out put of the following command is:

sudo apt-get -f install

This should fix anything that may be broken.

---

### Post by Vanity on 2011-11-06
It seemed to take. no errors or warnings the bottom of the command line says "the following packages were installed and are no longer required: linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic.


However this doesnt exactly solve my problem because when I input the command to change my mac address, sudo macchanger -m 00:11:22:33:44:55 mon0" it still gives me a command not found output. 

is that the wrong code?

V_

---

### Post by Script Warlock on 2011-11-06
hmm are you playing with aircrack-ng or something?

---

