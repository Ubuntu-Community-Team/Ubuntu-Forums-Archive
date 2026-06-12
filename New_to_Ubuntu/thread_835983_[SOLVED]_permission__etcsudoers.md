---
title: "[SOLVED] permission  /etc/sudoers"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by mobyu on 2008-06-21
I'm using xubuntu on hardy.
I tryed to change the permission of /etc/sudoers. and I could do that.
But now , I can't undo this operation.

```

$ sudo chmod 777 /etc/sudoers                                                   
$ sudo vi /etc/sudoers                                                          
sudo: /etc/sudoers is mode 0777, should be 0440                                 
$ vi /etc/sudoers                                                               
$ sudo chmod 440 /etc/sudoers                                                   
sudo: /etc/sudoers is mode 0777, should be 0440                                 
$ chmod 440 /etc/sudoers                                                        
chmod: changing permissions of `/etc/sudoers': Operation not permitted          
$ sudo chmod 440 /etc/sudoers                                                   
sudo: /etc/sudoers is mode 0777, should be 0440                                 
$ sudo chmod 0440 /etc/sudoers                                                  
sudo: /etc/sudoers is mode 0777, should be 0440                                 
$ chmod 0440 /etc/sudoers                                                       
chmod: changing permissions of `/etc/sudoers': Operation not permitted  
$ ls -la /etc/sudoers                                          
-rwxrwxrwx 1 root root 501 2008-06-21 14:09 /etc/sudoers


```

---

### Post by sdennie on 2008-06-21
I think you will probably need to boot into recovery mode from the boot menu and run:

```

chmod 0440 /etc/sudoers

```

---

### Post by AndThenWhat on 2008-06-21
Maybe try:

```
sudo -s -H
```

and CD'ing into the directory to edit the file(s) ?

---

### Post by mobyu on 2008-06-21
Thanks vor. it's just what I need.
yes,I can do that.I can login recovery mode ,and root shell with no password.

---

