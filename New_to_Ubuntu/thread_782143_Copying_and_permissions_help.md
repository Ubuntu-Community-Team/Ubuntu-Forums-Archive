---
title: "Copying and permissions help"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by videocheez on 2008-05-04
I get so confused with linux whether i need to use the terminal and if i have to write sudo first or if i can go to places and simply copy a file to a certain directory.  

For example, I am playing with ipblock and creating a white list in the directory /var/cache/iplist.  If i navigate using the file browser to /var/cache/iplist i cannot create a file in this directory because a message pops up saying that i don't have permission.  I suppose i could use the terminal and type sudo first but i don't know all of the commands to edit the text file and then how save as a different file name.  Besides i type very slowly but I suppose i need to get more comfortable with the basic terminal commands because relatively simple tasks are taking too long to do because of my unfamiliarity with using the terminal.  Any help will be way appreciated.

Thx,

VC

---

### Post by gniltaws on 2008-05-04
Two ideas that should help:

1. When in command line and you want to edit a text file in a GUI type:```
sudo gedit _filename_here_
```  This will bring up a notepad-like text editor.

2. You can open up nautilus (the file manager) with admin privileges  from the command line by typing: ```
sudo nautilus
```

Enjoy.

---

### Post by bodhi.zazen on 2008-05-04
First you should use gksu for graphical applications (rather then sudo)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Second, better to explain permissions ...

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by videocheez on 2008-05-04
> **gniltaws said:**
> Two ideas that should help:

1. When in command line and you want to edit a text file in a GUI type:```
sudo gedit _filename_here_
```  This will bring up a notepad-like text editor.

2. You can open up nautilus (the file manager) with admin privileges  from the command line by typing: ```
sudo nautilus
```

Enjoy.

Thanks man.  Those two simple ideas are gonna go along way.:)

---

### Post by Oldsoldier2003 on 2008-05-04
> **videocheez said:**
> I get so confused with linux whether i need to use the terminal and if i have to write sudo first or if i can go to places and simply copy a file to a certain directory.  

For example, I am playing with ipblock and creating a white list in the directory /var/cache/iplist.  If i navigate using the file browser to /var/cache/iplist i cannot create a file in this directory because a message pops up saying that i don't have permission.  I suppose i could use the terminal and type sudo first but i don't know all of the commands to edit the text file and then how save as a different file name.  Besides i type very slowly but I suppose i need to get more comfortable with the basic terminal commands because relatively simple tasks are taking too long to do because of my unfamiliarity with using the terminal.  Any help will be way appreciated.

Thx,

VC
a rule of thumb. for the most part if its not in your home directory you'll need to use sudo.

There are exceptions but anytime you are making system wide configuration changes you can bet you'll need to use sudo.

---

### Post by Glaxed on 2008-05-04
If you really think that a directory should be available to you without root passwd, you may choose to chmod it I think.
**It would be a very BAD idea to recursively chmod 777 / or /var though.**

---

### Post by Oldsoldier2003 on 2008-05-04
> **Glaxed said:**
> If you really think that a directory should be available to you without root passwd, you may choose to chmod it I think.
**It would be a very BAD idea to recursively chmod 777 / or /var though.**

its a VERY bad idea to chown or chmod a directory that you did not create unless you know exactly what you are doing and exactly why you are doing it.

---

### Post by videocheez on 2008-05-05
> **bodhi.zazen said:**
> First you should use gksu for graphical applications (rather then sudo)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Second, better to explain permissions ...

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


Thanks for the info.  As i get used to using Ubuntu, I would like to learn what I'm doing and to do it the proper way.  On all 3 of my  ubuntu computers, I have one user name (account).  It the one that I set up when I first installed Ubuntu.  One of the articles that I read made me think that I should be working under a new user name in order to prevent hackers or my kids from screwing up my systems.  Is it necessary to set up other accounts if I'm the only one that uses these computers.  Please let me know.  As I study the articles that you have suggested, I may have some more questions but this is all now.

Thanks,

VC

---

