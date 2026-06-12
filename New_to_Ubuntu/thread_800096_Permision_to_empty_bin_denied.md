---
title: "Permision to empty bin denied"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by nnjond on 2008-05-19
Permision to empty bin denied. How can I empty it?

---

### Post by Majorix on 2008-05-19
```
rm -rf ~/.Trash
```
Will empty your user's trashbin. But I don't know why you can't do it graphically.

EDIT: Now checking, I can't see the .Trash folder. Did they remove it?

---

### Post by bluefrog on 2008-05-19
if you are using 8.04
sudo rm -r .local/share/Trash

---

### Post by drs305 on 2008-05-19
In hardy the trash is now located in /home/username/.local/share/Trash/files

---

### Post by nnjond on 2008-05-19
Thanks. Has left one folder in the bin?

nnjond@nnjond-desktop:~$ sudo rm -r .local/share/Trash
rm: cannot remove `.local/share/Trash': No such file or directory
nnjond@nnjond-desktop:~$

---

### Post by drs305 on 2008-05-19
```
rm -r ~/.local/share/Trash/files
```

---

### Post by nnjond on 2008-05-19
nnjond@nnjond-desktop:~$ rm -r ~/.local/share/Trash/files
rm: cannot remove `/home/nnjond/.local/share/Trash/files': No such file or directory
nnjond@nnjond-desktop:~$ 

???

---

### Post by drs305 on 2008-05-19
If I understand, you still have a file in your local trash that you can't remove? It's possible there is a folder or file in the trash that is not owned by you. Try:
```
sudo rm -r /home/nnjond/.local/share/Trash/files
```

If that doesn't work, give us the results of 
```
sudo find /home/nnjond | grep Trash
```

---

### Post by nnjond on 2008-05-19
nnjond@nnjond-desktop:~$ sudo rm -r /home/nnjond/.local/share/Trash/files
[sudo] password for nnjond: 
rm: cannot remove `/home/nnjond/.local/share/Trash/files': No such file or directory
nnjond@nnjond-desktop:~$ sudo find /home/nnjond | grep Trash
/home/nnjond/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fnnjond%2F.Trash.xml
/home/nnjond/.nautilus/metafiles/trash:%2F%2F%2Fmedia_disk_.Trash-1000_Backup%2520Ubuntu.xml
/home/nnjond/.evolution/mail/local/.#evolution.sbd/Trash.cmeta
/home/nnjond/.evolution/mail/config/et-expanded-mbox:_home_nnjond_.evolution_mail_local_._23evolution_Trash
nnjond@nnjond-desktop:~$

---

### Post by drs305 on 2008-05-19
nnjond

I'll send you a PM. Check your inbox.

Note: In the next post, nnjond figured out what I was saying. (Clicking on my name and sending a private message. You read messages by clicking on this page's upper right link Private Messages)



nnjond: I've sent you some more messages.

---

### Post by nnjond on 2008-05-19
I don't understand the last post. The folder in my Wastebasket contains some files I would like to be rid of. Thanks for your help.

---

