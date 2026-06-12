---
title: "[SOLVED] Can You help me uninstall this code please?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-24
Ubunteros,

I was visiting a Ubuntu Forum web page and got info on installing my webcam. Said info thus far hasn't worked.

"For people who are having issues with the webcam using Ubuntu-8.10.

Try to install linux-backports-modules-$(uname -r) first, and see how it works out. It can solve a lot of driver issues. Of course, if it did nothing for you, then remove the linux-backports-modules-$(uname -r) before continuing.

Copy paste this command into your terminal:-
Code:

sudo apt-get install linux-backports-modules-$(uname -r)"


I cut and pasted the "sudo" command into terminal and re-booted but nothing worked. Before I move to step to I need to uninstall this sudo command.

CAN SOMEONE TELL ME PLEASE HOW TO UNINSTALL THIS COMMAND PLEASE?

THANK YOU VERY MUCH!!!

---

### Post by lswest on 2008-11-24
just replacing "install" with "remove" should do it, unless it installed anything else or removed some previous version.  Also, I don't know if you *need* to remove it, but that should do it.

---

### Post by Coreigh on 2008-11-24
You entered the command as typed?
> sudo apt-get install linux-backports-modules-$(uname -r)

Did you execute the command? (press enter key) Or did the terminal window give a response ? Success or error?

To check to see if the backports package is in fact installed type the following in a terminal, it is only a query and will not change anything
```
sudo dpkg -l | grep backports
```

It will ask for your password but if it returns no other information then there is nothing to "un-do."

If it does return a listing of installed packages then they can be removed this way:
```
sudo apt-get remove <packagename>
```
Where <packagename> is changed to whtever you want to remove.

:!: USE CAUTION. Do not remove package that you don't know you added. You can easily damage or break the system and have to re-install.


Also use caution when copying commands when you aren't clear on what they do. In the case of apt-get you can use the -s switch to "dry run" and see what will happen if you run the command.
Example: **[COLOR="SeaGreen"]sudo apt-get [COLOR="Red"]-s[/COLOR] install linux-backports-modules-$(uname -r)[/COLOR]**

---

### Post by suomalainen on 2008-11-24
lswest,

That seemed to do it Thank You. P.S. I sent you a "thank you" so your thank you tally has just increased.

---

### Post by lswest on 2008-11-24
> **suomalainen said:**
> lswest,

That seemed to do it Thank You. P.S. I sent you a "thank you" so your thank you tally has just increased.

Sent me a thank you? :P  You just have to click the red medal at the bottom of the post that helped.  Either way, I'm not here for the thanks tally, so don't worry about it.

Anyways, I'm glad I could help, and good luck with the rest of the process (whatever had you install the backport modules).
Lswest

---

