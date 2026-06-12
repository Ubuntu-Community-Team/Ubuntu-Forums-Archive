---
title: "Unable to uninstall an installed package"
date: 2022-11-29
forum: New to Ubuntu
---

### Post by yvanou on 2022-11-29
Hi everyone,

I installed a package from source (*nodejs 14.21*) and *npm*.

I would like to uninstall both but when I use ```
sudo apt remove node
```, I have the error message ```
E: Impossible de trouver le paquet node
```.
The same for [I]npm.

[/I]When I type ```
node --version
``` however, I have the version ```
v14.21.1
```. Idem for npm. So, I suppose it is installed already.

I also tried ```
sudo dpkg --remove --force-remove-reinstreq npm
``` but it doesn't work neither.

**How can I uninstall a package that is not recognized by the system ?**

---

### Post by ian-weisser on 2022-11-29
How you uninstall software depends upon how you originally installed it.

How did you install node? Clearly you did not use apt or dpkg to do so.

---

### Post by Impavidus on 2022-11-29
If you installed software without using the package manager, it wasn't registered in the package manager's database and therefore the package manager is unaware of it. Naturally, it can't uninstall the software.

So, how did you install this software? Did it come with uninstall instructions? Do you at least have the install instructions, that we may reverse them?

---

### Post by yvanou on 2022-11-29
Hello,

Thanks for your quick answers.

Indeed, I first installed *nodejs v18* and *npm* with *apt* but it didn't work for what I wanted to do (i.e. install a software called *ganache-gui* which needs *nodejs* and *npm* to be installed). So, I uninstalled *nodejs v18* with "sudo apt remove nodejs" and then download sources on github for nodejs v14, and finally I build and install *node v14.* I tried again to install the *ganache-gui* software but it still didn't work. So I wanted to uninstall everything (i.e. *nodejs v14* and *npm*). But when I tried the "sudo apt remove ..." command, it says that the software is not installed on my computer. However, I can see the versions of these softwares.

---

### Post by yvanou on 2022-11-29
Hello all,
I found a thread that solved my problem I think: [https://stackoverflow.com/questions/32426601/how-can-i-completely-uninstall-nodejs-npm-and-node-in-ubuntu](https://stackoverflow.com/questions/32426601/how-can-i-completely-uninstall-nodejs-npm-and-node-in-ubuntu) (the third reply, on removing manually the files and directory)
Now, I got the following answer when I type "node --version" or "npm --version":

```
bash: /usr/local/bin/npm: Aucun fichier ou dossier de ce type
bash: /usr/local/bin/node: Aucun fichier ou dossier de ce type
```

That's what I wanted!! :P

---

