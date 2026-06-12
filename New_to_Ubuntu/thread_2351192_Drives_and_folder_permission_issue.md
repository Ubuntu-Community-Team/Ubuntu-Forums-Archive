---
title: "Drives and folder permission issue"
date: 2017-01-31
forum: New to Ubuntu
---

### Post by crazzyshooter on 2017-01-31
Hello,

I need some help regarding user permissions. I have installed Ubuntu mate 16.04 and i have created 4 different Ext4 partitions. **I can't copy-paste files and create new folders in other partitions. **

How can i give permission to my current user?


Please see this: [URL="http://i.imgur.com/0F6l2XE.png"]http://i.imgur.com/0F6l2XE.png

[/URL]Need your help. :(

---

### Post by Keith_Helms on 2017-02-01
```

sudo chown -R yourid:yourgroup /media/bioshock

```

---

### Post by Dennis N on 2017-02-01
All you need to do is change the owner and group of each mount point folder:

Suppose tom is your user name.
Open the terminal, then use these commands, one at a time. you will be asked for your user password:

```
cd /media/bioshock/
sudo chown -R tom:tom Data/
sudo chown -R tom:tom Softwares/ 
sudo chown -R tom:tom Media/

```
Now all normal actions will be permitted.

---

### Post by crazzyshooter on 2017-02-01
> **Keith_Helms said:**
> ```

sudo chown -R yourid:yourgroup /media/bioshock

```

> **Dennis N said:**
> All you need to do is change the owner and group of each mount point folder:

Suppose tom is your user name.
Open the terminal, then use these commands, one at a time. you will be asked for your user password:

```
cd /media/bioshock/
sudo chown -R tom:tom Data/
sudo chown -R tom:tom Softwares/ 
sudo chown -R tom:tom Media/

```
Now all normal actions will be permitted.

Thank you so much guys, you both saved me. I am using ubuntu mate with compiz effect and loving it... hehe!! :P

---

