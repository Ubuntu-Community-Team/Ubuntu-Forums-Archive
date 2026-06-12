---
title: "[SOLVED] Cannot empty trash!"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by beanstalker on 2008-07-19
I recently attempted to delete a folder containing wireless drivers, but I cannot now empty the Trash. I cannot now move or alter the folder or its contents despite the fact that the permissions of the files are both read & write. However the folder permissions are Access only and I cannot change this. Does anybody know how I can fix this? I have tried accessing the Trash via gksu nautilus but when T attempt to navigate to the trash the system becomes unresponsive and I have to crash.

Any help would be greatly appreciated.

Cheers,
Jack

---

### Post by Dr Small on 2008-07-19
Open a terminal and try:
```
sudo rm -R ~/.Trash
```

---

### Post by oilchangeguy on 2008-07-19
> **beanstalker said:**
> I recently attempted to delete a folder containing wireless drivers, but I cannot now empty the Trash. I cannot now move or alter the folder or its contents despite the fact that the permissions of the files are both read & write. However the folder permissions are Access only and I cannot change this. Does anybody know how I can fix this? I have tried accessing the Trash via gksu nautilus but when T attempt to navigate to the trash the system becomes unresponsive and I have to crash.

Any help would be greatly appreciated.

Cheers,
Jack

have you tried to reboot the computer?

---

### Post by drs305 on 2008-07-19
If you are in hardy and the files are in your user's trash:
```

gksu nautilus ~/.local/share/Trash/

```

Delete the 'Files' folder or any of the files inside it. If you delete the entire Files folder, delete the Info folder as well.

---

### Post by beanstalker on 2008-07-19
Thanks, I have just tried that and I get the following error:
 
> jack@ubuntu:~$ sudo rm -R ~/.Trash
[sudo] password for jack: 
rm: cannot remove `/home/jack/.Trash': No such file or directory
jack@ubuntu:~$ 


---

### Post by Dr Small on 2008-07-19
> **beanstalker said:**
> Thanks, I have just tried that and I get the following error:
Please read drs305's post. It appears that Hardy has moved the Trash directory! :O

---

### Post by beanstalker on 2008-07-19
Thanks drs305, that worked perfectly, 
Thanks,
Jack

---

### Post by drs305 on 2008-07-19
> **Dr Small said:**
> Please read drs305's post. It appears that Hardy has moved the Trash directory! :O

Yes it did, but all previous versions are located where you indicated ;-)

---

### Post by Dr Small on 2008-07-19
> **drs305 said:**
> Yes it did, but all previous versions are located where you indicated ;-)
Yeah, I haven't used Ubuntu since Feisty, so... :D

---

### Post by cjc160 on 2008-07-22
gksu nautilus ~/.local/share/Trash/


Thanks man, I've been trying to find an "empty trash" command for a few hours now and this is the first command I found that actually works.

---

### Post by Dr Small on 2008-07-22
> **cjc160 said:**
> gksu nautilus ~/.local/share/Trash/


Thanks man, I've been trying to find an "empty trash" command for a few hours now and this is the first command I found that actually works.
You can also use:
```
rm -R ~/.local/share/Trash
```

---

