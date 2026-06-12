---
title: "Freenet uninstall"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by stueau on 2008-05-13
I've just [posted a thread]("http://ubuntuforums.org/showthread.php?p=4947624#post4947624") about java running constantly in the background and I think it may be to do with 'Freenet' that I installed a few days ago. I'm wanting to uninstall it to check and have found [this]("http://uninstallfreenet.awardspace.info/") guide for the unistall in windows. Could somebody translate this into linux talk for me?

Many thanks in advance.


[EDIT: apologies for clogging the board, but I've managed to uninstall freenet myself. Found the uninstaller... doh! This also appears to solved the problem mentioned in the other thread aswell]

---

### Post by Ux64 on 2009-04-04
> **stueau said:**
> [EDIT: apologies for clogging the board, but I've managed to uninstall freenet myself. Found the uninstaller... doh! This also appears to solved the problem mentioned in the other thread aswell]

You didn't find where you found uninstaller. But for Ubuntu, and Freenet 0.7 default installation case you'll get rid of it giving following commands.

```

cd ~/Freenet/Uinstaller
java -jar uninstaller.jar

```

It's always nice how something was solved in case someone else is looking for some solution to the problem you described.

---

### Post by cocolocko on 2009-05-14
Hi @ all,

i also want to uninstall FREENET but i dont have the
folder /Uninstaller.
Does someone know how to uninstall the programm?
Thanks

Greetings

---

### Post by mlnease on 2009-07-24
> **Ux64 said:**
> You didn't find where you found uninstaller. But for Ubuntu, and Freenet 0.7 default installation case you'll get rid of it giving following commands.

```

cd ~/Freenet/Uinstaller
java -jar uninstaller.jar

```

It's always nice how something was solved in case someone else is looking for some solution to the problem you described.

Thanks for this--please note miskey in first line:  "cd ~/Freenet/Uinstaller" should be "cd ~/Freenet/Uninstaller".

Thanks again.

mn

---

### Post by eival on 2009-09-12
i too couldnt find the uninstall option, but the codes in this thread did it for me, thanks:popcorn:

---

### Post by jimmyjammy on 2009-11-26
when u say the codes did it for you...well, I am a complete newbie with Ubuntu...where do I put those codes?? I too cant uninstall Freenet...thanks

---

### Post by cariboo on 2009-11-26
Open an Applications-->Accessories-->Terminal and enter the commands in the terminal.

> cd ~/Freenet/Uinstaller
java -jar uninstaller.jar

cd = change directory, ~/ = your home directory /Freenet/Uninstaller = the path to the uninstaller file. 

The second command runs the uninstaller application.

---

### Post by Luke1972 on 2009-11-27
Thanks for the easy to follow instructions.

---

### Post by Ningbojoe on 2009-12-22
Thanks for this thread, it helped me as well.

---

### Post by pressman57 on 2010-03-28
Thanks for the thread. Sometimes the obvious is not so obvious.

---

