---
title: "Need help re-installing Firestorm for Second Life"
date: 2017-03-12
forum: New to Ubuntu
---

### Post by apol1 on 2017-03-12
Hi, I need to update my Firestorm but it seems to me the only way to do this is to completely erase it and do a clean install. Ive followed their instructions on their site but still get nowhere

Can anyone help me? I think I have to delete some things from terminal but I don't know the commands

Can I update somehow?

Thx for your help :)

---

### Post by Perfect Storm on 2017-03-12
Please provide link and also post the commands you have used and its outcome.

Thanks.

---

### Post by apol1 on 2017-03-12
Im not really sure what to type into the terminal, is there a NUKE everything firestorm command I can try lol? Ive considered An easier OS but Im starting to get the hang of 16.04 thx though

---

### Post by Perfect Storm on 2017-03-12
This show to do it with 64-bit
```
cd ~/Downloads
tar xf Phoenix_FirestormOS-Releasex64_x86_64_5.0.1.52150.tar.xz
cd Phoenix_FirestormOS-Releasex64_x86_64_5.0.1.52150
sudo ./install.sh
```

---

### Post by apol1 on 2017-03-15
Here ya go :) **```
 **:~$ cd ~/Downloads
:~/Downloads$ tar xf Phoenix_FirestormOS-Releasex64_x86_64_5.0.1.52150.tar.xz
cd Phoenix_FirestormOS-Releasex64_x86_64_5.0.1.52150
:~/Downloads$ cd Phoenix_FirestormOS-Releasex64_x86_64_5.0.1.52150apollo@Neptune:~/Downloads/Phoenix_FirestormOS-Releasex64_x86_64_5.0.1.52150$ sudo ./install.sh
[sudo] password for: 
Enter the desired installation directory [/opt/firestorm-install]: 
 - Installing to /opt/firestorm-install
 - Installing menu entries in /usr/local/share/applications
apollo@Neptune:~/Downloads/Phoenix_FirestormOS-Releasex64_x86_64_5.0.1.52150$ **
``` **Im not sure whats its asking and my viewer is still reading 4.7.9.

---

### Post by Perfect Storm on 2017-03-15
It should now be installed and ready for you to launch. you might search Dash for the launcher.

You need to uninstall the previous version I think.

---

### Post by apol1 on 2017-03-17
I think I do, how do I uninstall the previous version?

---

### Post by Perfect Storm on 2017-03-17
How did you install the previous version+

EDIT: On a thought, try go to /opt/firestorm-install and see if yu can launchgame through there and see the right version.

---

