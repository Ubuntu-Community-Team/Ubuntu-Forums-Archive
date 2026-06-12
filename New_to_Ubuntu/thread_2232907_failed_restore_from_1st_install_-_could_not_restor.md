---
title: "failed restore from 1st install - could not restore"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by smokingates on 2014-07-05
O.S : Ubuntu 14.04LTS

i am trying to restore ubuntu to how it was when i first installed it. i made a backup as the very first thing i did after a fresh install 3 days ago and now when i try to restore to that backup i get the following in a window that says restore finished which is a bit ironic... "could not restore the following files. Please make sure you are able to write to them." - /home/user/.encryptfs - when I went to that .dir i was able to create a new untitled folder but was unable to send it to trash - the option simply wasnt there. Thank you in advance.

---

### Post by nadarockyraccoon on 2014-07-07
you're having some permission issues, are you running the recovery as a root user with sudo? Open a terminal and type:
```
sudo nautilus
```

give a password and then navigate to the directory in question. you should be able to delete that untitled folder now, and possibly change the permissions on the directory, though I don't recommend doing that. This will just verify that a limited permision folder exsists in that directory and you need to be root or logged in as that user to edit it's content.

---

