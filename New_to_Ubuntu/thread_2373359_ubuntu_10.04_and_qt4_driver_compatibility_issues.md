---
title: "ubuntu 10.04 and qt4 driver compatibility issues"
date: 2017-10-05
forum: New to Ubuntu
---

### Post by fahad789 on 2017-10-05
Hi,

First of all, i am a beginner in Ubuntu. I need to sort out an issue in an existing Ubuntu 10.04 system which runs qt4 package. I just updated one qt4 (*.pro) program and cant be build due to the compiler error as shown below. 
[COLOR=#008000][FONT=Verdana]make: g++: Command not found 
[/FONT][/COLOR][COLOR=#008000][FONT=Verdana]make: *** [main.o] Error 127 
Exited with code 2.
[/FONT][/COLOR]I tried to install gcc drivers and all, but still some compatibility issues are there and the issue still persists. There is no option for updating Ubuntu, since i have to maintain the same OS. Please guide me some options to solve this issue, i am fed up trying to solve this.

Regards,
Fahad. H

---

### Post by su:bhatta on 2017-10-05
There is no support for Ubuntu 10.04 anymore.
Maybe somebody more experienced will be able to get this straightened.

But with 10.04, it will be difficult to get compatibility issues sorted.

[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

### Post by Impavidus on 2017-10-05
You should never have encountered such an old system. But you have.

You have to install g++, the compiler. Your release is no longer supported, so you may not be able to install from the repositories directly, but you may be able to use the server for old releases.
[https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

And complain to the person who ordered you to do stuff on such an old system.

---

### Post by Autodave on 2017-10-05
"There is no option for updating Ubuntu, since i have to maintain the  same OS. Please guide me some options to solve this issue, i am fed up  trying to solve this."

Why isn't there an option of upgrading? You cannot maintain anything that is too old to get "parts" for: whether it be a piece of machinery or an OS.

---

### Post by wildmanne39 on 2017-10-05
You will need to upgrade to a supported version of Ubuntu, I recommend 16.04, we can not in good conscience provide support for a system that will leave your computer vulnerable to attacks. We do not support this old of a Operating System so this thread is being closed!

---

