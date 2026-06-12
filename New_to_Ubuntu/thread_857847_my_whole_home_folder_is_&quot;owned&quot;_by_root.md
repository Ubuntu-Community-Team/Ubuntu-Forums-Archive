---
title: "my whole home folder is &quot;owned&quot; by root"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by spadhawk on 2008-07-12
ok what happened was I had another installation but it was masses up so i decided to reinstall i went with the live cd and made a "tar.gz" archive of my home folder and put it on flash media but i did it with sudo. so when i reinstalled i went to copy it to the home and it didn't copy so i used sudo to copy it then it sorta didn't work i had to change the file permissions the folder to me. and then it would let me log in but like 90% of it is still owned my root so programs cant use. how can i change the permissions of all m files in the home folder to me.

---

### Post by boblemur on 2008-07-12
you could do


sudo chown -R <your name> /home/<your name>

should do it :)

---

### Post by DGortze380 on 2008-07-12
permissions and ownership are two different (though connected) things.

sudo chown -R username /home/username
to change owner

sudo chmod 700 /home/username
to change permission for owner to read/write/execute and no access for anyone else other than root

---

### Post by Dr Small on 2008-07-12
Try:
```
sudo chown -R $USER:$USER /home/$USER
```

---

### Post by boblemur on 2008-07-12
when using cp you should keep in mind that cp dosent keep things like time stamps ownership or permissions unless you tell it to... use -a to keep them (i think its -a could be wrong)

---

### Post by spadhawk on 2008-07-13
> **DGortze380 said:**
> 
sudo chmod 700 /home/username
to change permission for owner to read/write/execute and no access for anyone else other than root

i think that cammand worked

---

### Post by aysiu on 2008-07-13
What's done is done, but I would have advised to do the *chown* but not the *chmod*. Not everything in your home directory is supposed to have the same permissions.

---

### Post by DGortze380 on 2008-07-13
> **aysiu said:**
> What's done is done, but I would have advised to do the *chown* but not the *chmod*. Not everything in your home directory is supposed to have the same permissions.

Didn't tell him to chmod everything. Actually, the first command I gave him was to chown. I explained both commands.  permissions can always be changed as needed if he runs into problems.

---

### Post by aysiu on 2008-07-13
> **DGortze380 said:**
> Didn't tell him to chmod everything. Actually, the first command I gave him was to chown. I explained both commands.  permissions can always be changed as needed if he runs into problems.
In post #3, you said [quote=You]sudo chmod 700 /home/username
to change permission for owner to read/write/execute and no access for anyone else other than root[/quote] And I'm saying that can break your installation, as not everything in your home directory is supposed to have the same permissions set.

---

