---
title: "Ubuntu 12.04 / Zioper Softphone Uninstall"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by rjhzxc on 2012-11-23
Hi Folks
I'm new to Linux and wonder if anyone has experience with the above. Zoiper is proving to be a bit user-hostile to me. I cannot configure it properly nor can I remove Zoiper from Ubuntu.
Any advice on uninstallation of Zoiper would be particularly useful.


Regards
Rob

Asterisk 11
Ubuntu 12.04
Zoiper 219

---

### Post by COMECON on 2012-11-23
You can either open the Software Center, search for **Zopier** and uninstall it, or open a Terminal (**Dash > Terminal**) and run: *sudo apt-get remove zoiper*.

---

### Post by rjhzxc on 2012-11-23
Thanks Comecon.
Unfortunately I can't find it in Software Centre and sudo apt-get remove zoiper reports
E: Unable to locate package Zoiper

R.

---

### Post by ajgreeny on 2012-11-23
How did you install it in the first place, as that will affect how you should remove it.

---

### Post by 3rdalbum on 2012-11-23
Zoiper comes precompiled inside a tarball, not a Debian package.

You need to find the instructions for removing Zoiper - there's no single procedure that works on all programs installed in this way. The Zoiper site seems to only have instructions for Windows users but I bet the removal instructions for Linux are inside that tarball (.tar.gz) that you downloaded.

---

### Post by ZoiperSupport on 2012-11-27
Hello,


I am with the Zoiper Support team.

Zoiper Classic is never installed, it is an executable that you have to extract from the archive and put in a safe location. 

This is why it can not be uninstalled by apt. 

To remove Zoiper Classic you would need to take the following steps:

1. make sure Zoiper is not working:
- check your notification area - if there is a little Zoiper icon please right-click it and select Exit.
- open a terminal and type :

ps -a | grep -i zoiper

Is there a Zoiper process running? You could just kill it with 

kill -9 <process-id>

2. Find the directory where you extracted the archive and remove it.

3. Then clean all config files of Zoiper. They are kept in your home folder. The correct path is:

~/.zoiper


Would you like to share the issues that you experienced with Zoiper? Zoiper Support team could assist you in finding a suitable solution.

For more Zoiper related reports  or requests, do not hesitate to contact us directly on support @ zoiper . com   :)

---

