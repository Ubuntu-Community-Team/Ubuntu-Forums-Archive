---
title: "[SOLVED] can't get past"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Rita G. on 2008-11-19
i'm trying to install something and get stuck at:

# mkdir ~/build  
     
............and...........

# cd ~/build

can anyone explain what these mean?

i know it's as root.....but the terminal does not do anything when i enter either one.

---

### Post by Crafty Kisses on 2008-11-19
Do you have the following package installed?
```
sudo apt-get install build-essential
```

---

### Post by kellemes on 2008-11-19
> **Rita G. said:**
> i'm trying to install something and get stuck at:

# mkdir ~/build  
     
............and...........

# cd ~/build

can anyone explain what these mean?

i know it's as root.....but the terminal does not do anything when i enter either one.

"mkdir ~/build" creates directory /home/<user>/build
"cd ~/build" moves you to directory /home/<user>/build

---

### Post by oldos2er on 2008-11-19
> **Rita G. said:**
> i'm trying to install something and get stuck at:

# mkdir ~/build  
     
............and...........

# cd ~/build

can anyone explain what these mean?

i know it's as root.....but the terminal does not do anything when i enter either one.

 You shouldn't be running these commands as root. And if the terminal gives you no feedback, it means the command completed successfully.

---

### Post by Rita G. on 2008-11-22
thank you all for replies 

i didn't realize that all i had to do was copy & paste these.

hehehe hee hee 

i feel so stooooooooooooopid!

---

