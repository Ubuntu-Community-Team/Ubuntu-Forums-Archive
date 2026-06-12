---
title: "How to undo &quot;chmod -R 755 MyFolder /&quot; command"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by FRomao on 2012-12-02
Please it's second time I've made same error. First one took me one week of searching but at the end I've to reinstall Ubuntu from the beginning... This time I hope someone can help me.  When trying to install a program on my computer, in my partition /opt used the command:  sudo chmod -R 755 MyFolder / The idea was to change the permissions of MyFolder and all folders within MyFolder But it seems to me that the space between MyFolder and / was fatal ... How can I go back? The other time I reboot the laptop and never had access to it. Now I can still surf the net, but I can not open a terminal window gives the following error: There was an Error creating the child process for this terminal getpt failed: No such file or directory and two boxes:  Profile preferences Relaunch  Relaunch and no point in messing preferences do not know ...  If someone can explain exactly why this happens also apreciate  My learning curve of Linux is being difficult but I do not give up.

---

### Post by vanadium on 2012-12-02
As yo experienced the first time, this is a fatal error. There is no way to restore the correct permissions for all several thousand files on your system. Have a good backup of your personal files, and then reinstall. In less than an hour, your system will be up again.

---

### Post by Zill on 2012-12-02
> **FRomao said:**
> ...When trying to install a program on my computer, in my partition /opt used the command:  sudo chmod -R 755 MyFolder...
Once you have reinstalled Ubuntu and got a working system again I strongly suggest that you do not try to install programs manually until you gain more experience with Linux.  Just stick to the Software Center (or Synaptic) and only install deb packages from the standard default repos and you should have a very stable system. :-)

---

### Post by FRomao on 2012-12-02
Thank you both Vanadium and Zill.

Next step: startover....

Thats life...

Zill software center has the program (GNS3) but it's an old version and I need the updated one


FRomao

---

### Post by squakie on 2012-12-02
After you are back up and running, post back here and we'll try to give you instructions so you can install what you need.

---

### Post by nothingspecial on 2012-12-02
> **squakie said:**
> After you are back up and running, post back here and we'll try to give you instructions so you can install what you need.

But make a new thread with a relevant title.

---

### Post by squakie on 2012-12-02
> **nothingspecial said:**
> But make a new thread with a relevant title.

Sorry about that - I didn't think of that.

---

