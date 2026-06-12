---
title: "permission denied on samba share"
date: 2017-01-10
forum: New to Ubuntu
---

### Post by jho78 on 2017-01-10
I am in the process of creating a Samba share and have run into a permissions issue I believe. I can create a new folder in the share, but if I try to create another file/folder in the new folder.. I get a permission denied error.


I have created the share by following these 2 guides [https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html) and [https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/](https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/) (I did not go past step 3 on securing the share)


I have mounted it by typing in 
```
:sudo mount -t cifs //server_address/share //mnt/local_folder

```

I ran a ls -l on the test folder I made the results are
```
 drwxr-xr-x+ 2 nobody nogroup 0 Jan 10 00:07 test_folder 
``` 

but when I try to create a folder within the newly created test_folder I get
```

mkdir: cannot create directory ‘test_folder_nested’: Permission denied
```


I have tried sudo mkdir.. but I get the same permission denied.


Thank you in advance for your help

---

### Post by TheFu on 2017-01-11
What file system is directly running on the storage?

---

