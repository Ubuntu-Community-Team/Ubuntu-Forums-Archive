---
title: "performing multiple sudo apt-get install commands in one go"
date: 2007-04-08
forum: Programming Talk
---

### Post by itsalmostreal on 2007-04-08
I've recently built a machine to run ubuntu for myself, and a few of my friends are looking to do the same. 

to get everything running, the programs i wanted, and all the codecs necessary to play my media from my old g5, i had to perform many "sudo apt-get install" or "sudo aptitude install" commands. im looking for a way to combine all the commands into a single script, so i can rerun them on other machines.

i'm not looking to go back and find all the commands i ran, but rather figure out a way to build a list from scratch.

simply put, i want to be able to run a single command line script that will then run all the scripts i have listed in it. im not sure this is possible, but i would hope it is. and a plus would be to have the program automatically answer yes  whenever the install programs ask if you for permission to use disk space.

thanks!

---

### Post by Swab on 2007-04-08
Well you can specify as many packages as you like on one go...

```
apt-get install package1 package2 package3
```

---

### Post by itsalmostreal on 2007-04-08
thanks for the reply!

 i've definitely seen that in some guides. is there any way to write a script that performs all those installs for you?

this way you could type all the packages into a script file, save it, and then run it with a short command (ie: install_all)...

---

### Post by Swab on 2007-04-08
```

#!/bin/bash
apt-get install package1 package2 package3

```

Save that as installscript.sh or whatever... call is with: sudo ./installscript.sh

---

### Post by nhandler on 2007-04-08
You also need to make sure you chmod +x installscript.sh. That will give make the script executable.

---

### Post by itsalmostreal on 2007-04-08
okay, i'll call that a ridiculously simple solution. thanks!

---

