---
title: "Removing Museeq"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by baos on 2008-06-29
When I try to remove Museeq in the Add/Remove area I get this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am a newbie, please help.

---

### Post by sayakb on 2008-06-29
Open a terminal (Applications->Accessories->Terminal)
Type in:
```
sudo dpkg --configure -a
```
Provide your password (if asked for)
And then try removing Museeq again.

---

### Post by baos on 2008-06-29
Now it says it wont let me remove it because it is dependant on other progams. It says I must use Synaptic package manager??

---

### Post by adobrakic on 2008-06-29
System > Administrator > Synaptic Package Manager and find it in there.

have you tried 
```

sudo apt-get purge museeq

``` 

in terminal?

---

### Post by baos on 2008-06-29
I really miss soulseek and I can't get museeq to work. Can anyone give me a walkthrough? I tried museteup but may have not done it correctly.

---

### Post by jah- on 2008-12-28
I installed museek from synaptic package manager and it requires a password inorder to connect.. the host is localhost:2240, I am not sure what to type in to the password panel.. can someone please help?
Also, what is a daemon?

Thank you :)

---

