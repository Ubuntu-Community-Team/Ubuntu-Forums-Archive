---
title: "enviornment variables, export, and .bashrc ..."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Tsadkiel on 2008-07-16
greetings everyone,

     i recently installed some analysis software on a computer at work in Ubuntu, but something isn't right and i was hoping you could help.

when i installed this software i set the environment variables (i think thats what they are called... variables which add to PATH and LD_LIBRARY_PATH) in the .bashrc.  when i opened a new terminal and checked them with echo, they returned the proper values.  but when i ran make the error returned stated that i hadn't set the environment variables yet.

so i then set the variables in the terminal via export and tried make again.  this time it worked and installed properly... however, when i exited the terminal and tried to run the software, it fails unless i reset the variables again with export...

can someone tell me what is going on here?  shouldn't ubuntu be pulling the environment variables directly from .bashrc every time?  how can i set the environment variables such that they load with every new terminal?

thanks,
Tsadkiel

---

### Post by nhandler on 2008-07-16
When you modify your ~/.bashrc file, the changes are not applied right away. You either need to logout and then log back in, or you can type the following command:

```
source ~/.bashrc
```

Both of these methods will apply the changes you made to your ~/.bashrc file. This should also cause your environment variables to be set properly.

---

### Post by Tsadkiel on 2008-07-17
i have tried restarting the computer... no effect.  i also read elsewhere about a text file /etc/envrionment.  what is this anyway?

---

### Post by unutbu on 2008-07-17
Perhaps try this:

Edit ~/.profile:
Add
```

PATH=$PATH:path/you/want/to/add 
LD_LIBRARY_PATH=$HOME/lib       
export PATH LD_LIBRARY_PATH
```
Change the paths to suit your need.

Log out, then log back in.
Open a terminal and type
```

echo $PATH
echo $LD_LIBRARY_PATH
```
Did it work?

/etc/environment is read by the gdm startup script /etc/init.d/gdm. It sets PATH and LANG globally. You could set it there, but if you ever re-install the operating system, you might lose those custom configurations.
Therefore, it might be better to figure out how to change these variables from within your home account.

---

