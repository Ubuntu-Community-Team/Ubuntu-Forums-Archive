---
title: "Ubuntu terminal"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by davidc60 on 2011-12-19
Hi,
I have just installed Ubuntui 11.10 on to my hard drive. I have just opened the terminal to run 'sudo apt-get install kubuntu-desktop' (and the similar command for lubuntu and xubuntu) but I am getting a message returned saying that it cannot recognize this command or kubuntu-desktop  etc. I have correctly given my root password (its the only one I have at this stage).
Do I need to have configured the terminal or sudo in someway beforehand in order to be able to successfully run this command?
Thanks,
davidc

---

### Post by MartijnNL on 2011-12-19
It should normally work. Are you sure you did not make any typos? And I assume you didn't type the single quotes as well?

---

### Post by davidc60 on 2011-12-19
Thanks for your prompt reply. No typos and no single quotes. I'll keep trying but in the meantime do you know of any other way to achieve the same result (other than downloading the ISO's)?
davidc

---

### Post by MartijnNL on 2011-12-19
If you have a normal desktop Ubuntu, the easiest way would be to use the Software Center or Synaptic Package Manager. Both allow you to install software using a graphical interface. They can be found in the menu's. (But I don't use Unity, do I can't tell you exactly where to find them.)

---

### Post by howefield on 2011-12-19
On the off chance that you haven't, did you do an apt-get update beforehand ?

---

### Post by Lars Noodén on 2011-12-19
You could try in Synaptic or in the Software Center instead.

Out of curiosity, what is the exact error message that you get with [apt-get](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html)?  Can you paste it here?

---

### Post by davidc60 on 2011-12-19
Note in reply to Howefield - No, I didn't get an apt-get update beforehand. As it happens I've got some updates being downloaded as I write. Perhaps they will include one for apt-get unless I have to specifically request it?
In any event, I will run the command again shortly and will post any 'error' messages that may be returned. If this still doesn't work then I'll try the suggestion about Synaptic (I have not seen any reference to installs for the complete kubuntu/lubuntu/xubuntu OS's  in the Software Center but I'll double-check)
Thanks,
davidc

---

### Post by MartijnNL on 2011-12-19
Howefield means that you should run

```
sudo apt-get update
``` before you try to install any software. This updates the database of available software on your computer.

---

### Post by davidc60 on 2011-12-19
Thanks guys for all your replies. The updates are now installed and I've run the terminal again and I seem to be in business at least as far as getting Kubuntu installed. I'm really very new to all this - I'll remember the advice about sudo apt-get update for the future. Thanks,
davidc

---

