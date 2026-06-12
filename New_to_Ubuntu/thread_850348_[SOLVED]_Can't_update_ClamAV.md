---
title: "[SOLVED] Can't update ClamAV"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-07-05
Hi all,

  As per the suggestion given by the forum, i downloaded and installed ClamAV antivirus (to check my removable USB devices - as i used to share files with teammates). I cant update its signatures, as i was trying to do thru help - Update signatures, it prompts me error that "you must be a root to update". i don't know the exact command to update one particular "clamav" alone. 

  I also feel "sudo apt-get install update" installs all the updates for hardy heron and not for one particular thing. hope am right. Kindly help me. Thanks in advance.

---

### Post by Norm24 on 2008-07-05
```
sudo clamtk
```


Opening clam in terminal with the sudo command will allow you to update signatures.

---

### Post by tjwoosta on 2008-07-05
clamtk is a front end for clamav (a graphical interface)

but to update clamav without the GUI  just do this

```
sudo freshclam
```

anytime something says you have to be root, what it means is you have to use sudo before the command

---

### Post by mailtwogopal on 2008-07-06
hi guys,

 thanks a lot and it worked. after using "sudo freshclam" it updated. i tried opening "sudo clamtk" and i click "update signatures" with green button beside it (before it was not). i also got the message "signatures are upto date".

---

