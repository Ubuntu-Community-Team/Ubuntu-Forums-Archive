---
title: "Execute script without sudo ?"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by NikTh on 2012-06-03
Hi , 
I wanted to test something so did all below .. tell me were is the mistake please .

1) i create a script with nano 
```
nano system-update 
```i add lines 
```

!#/bin/bash
sudo apt-get update ; sudo apt-get upgrade
exit 0 
```save the file 

2) i add the system-update to /usr/bin/ 
3) i give execute permissions with chmod 
```
sudo chmod a+x /usr/bin/system-update 
```4) i modify /etc/sudoers with 
```
sudo su 
visudo 
```and add this line to the end 
```
username local_hostname = NOPASSWD: /usr/bin/system-update 
```save the file , exit from terminall 

Not work . 
When i run on terminal ```
system-update
``` it keeps asking for password. 
Where is the mistake ? 
Ubuntu 12.04 
Thanks

---

### Post by Cheesemill on 2012-06-03
You still have to use sudo, it just won't ask you for a password.

---

### Post by NikTh on 2012-06-03
> **Cheesemill said:**
> You still have to use sudo, it just won't ask you for a password.
Hi , 
i know that  , but if i want to run it without sudo ? 
just like this 
```
update-system
```
is that possible or not ? 
To bypass sudo inside the script.. 
Thanks .

---

### Post by Cheesemill on 2012-06-03
Change your script to:
```
!#/bin/bash
apt-get update ; apt-get upgrade
exit 0
```And then just run:
```
sudo update-system
```


Or leave your script as it is and add apt-get to your sudoers file with a NOPASSWD declaration.

---

### Post by NikTh on 2012-06-03
Hi , 
maybe i hadn't explained well , 
i  already did what  you mentioned , but i ask if its possible to run the script **without sudo first**. 
Just like this.. 
```
update-system
``` 
Thanks

---

### Post by Cheesemill on 2012-06-03
> **NikTh said:**
> Hi , 
maybe i hadn't explained well , 
i  already did what  you mentioned , but i ask if its possible to run the script **without sudo first**. 
Just like this.. 
```
update-system
```Thanks
If you add apt-get to the sudoers file then yes.

---

### Post by NikTh on 2012-06-03
> **Cheesemill said:**
> If you add apt-get to the sudoers file then yes.

Hi , 
ok , i get it now. (i think) 
I cannot bypass sudo inside a script , but i can add a program ( like apt-get in my example) to bypass sudo password prompt . 

I guess that the same not apply to linux - unix commands .. for example (sudo rm )
only for programs like apt-get.
Thanks

Ok i think i will mark this thread as solved then.

---

