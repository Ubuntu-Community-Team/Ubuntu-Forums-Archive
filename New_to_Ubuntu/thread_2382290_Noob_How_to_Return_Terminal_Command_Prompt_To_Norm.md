---
title: "Noob: How to Return Terminal Command Prompt To Normal"
date: 2018-01-11
forum: New to Ubuntu
---

### Post by bbyrdhouse on 2018-01-11
Hi,

After trying to install some new icons my command prompt in Terminal looks like this:
```
me@my-computer: usr/share/icons$
```How do I return it to normal:
```
me@my-computer: $
```Sorry for the idiot question ... but thank you for your help :)

---

### Post by steeldriver on 2018-01-11
It looks like you just changed your working directory to usr/share/icons

If so, you can change back to your home directory (which is the default) by typing

```

cd

```

or

```

cd ~

```

---

### Post by bbyrdhouse on 2018-01-11
Thank you very much

---

### Post by again? on 2018-01-11
You may care to have a read of this command line tutorial.
[https://ryanstutorials.net/linuxtutorial/commandline.php](https://ryanstutorials.net/linuxtutorial/commandline.php)

---

### Post by rvprepper on 2018-01-13
I type exit. [COLOR=#000000] [/COLOR]

---

### Post by ajgreeny on 2018-01-13
> **rvprepper said:**
> I type exit. [COLOR=#000000] [/COLOR]

That will only close the terminal or quit the session if using a command line system; it will not return the command prompt to your default which is normally username@hostname~$

---

### Post by oldos2er on 2018-01-14
> **rvprepper said:**
> I type exit. 

See the linuxcommand.org link in my signature, it's a tutorial to learn the command line geared toward new users.

---

### Post by genericvii143 on 2018-01-16
But i suggest before you use command use  [command name ] --help  and ready what its does.
cd .
cd .. 
cd ~ 

Good luck.

---

