---
title: "Update Manager Error"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by biglesca on 2013-04-15
Greetings to you all,

I have a persistent error in my update manager that I can't resolve on my own. I'm hoping someone can assist me.

Here is the error message:

"An error ocurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what went wrong. The error message was 'Error: BrokenCount > 0' This usually means that your installed packages have unmet dependencies."

Can anyone lend a hand, please?

---

### Post by sp-1070 on 2013-04-15
Try to go into a terminal and do  sudo apt-get update && sudo apt-get upgrade.

After that you should open the software center and check what it says and get back to us here.

---

### Post by slickymaster on 2013-04-15
See [this]("http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies"). Most probably you'll find a solution there.

---

### Post by biglesca on 2013-04-16
> **sp-1070 said:**
> Try to go into a terminal and do  sudo apt-get update && sudo apt-get upgrade.

After that you should open the software center and check what it says and get back to us here.

I did what you suggested and once I opened the Software Center, here are the messages I received:

[ATTACH=CONFIG]241451[/ATTACH] [ATTACH=CONFIG]241450[/ATTACH]

---

### Post by slickymaster on 2013-04-16
See the link in my previous post. Did you tried any of the solutions offered there?

---

### Post by sp-1070 on 2013-04-17
[http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)

---

### Post by siddharth007 on 2013-04-17
If it is about unmet dependencies try this command on the terminal
```
***apt-get install -f***
```

You might also have encountered this error because the Inodes on your storage might be used up i.e. in other words the disk might be full.Try with this command
```
***df -i***
```
This will tell you the Inodes used/free.

---

### Post by schragge on 2013-04-17
Also, please post the results of suggested terminal commands back here. E.g. one of your screenshots shows that in order to repair the package catalog, Ubuntu Software Center tried to remove *aptdaemon*, but couldn't because USC itself depends on it. It would be helpful to see what actual *apt-get* actions were executed and what error messages you were getting for each of them.

---

