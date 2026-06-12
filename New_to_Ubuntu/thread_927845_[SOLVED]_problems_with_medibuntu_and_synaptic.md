---
title: "[SOLVED] problems with medibuntu and synaptic"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by zanuvio on 2008-09-23
hi i tried to add the medibuntu repositories through the command line as per the instructions on ubuntu.com. as i went through the process i got the following error message:

david@dreamweaver:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
E: Type ‘--13:28:08--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
david@dreamweaver:~$ sudo apt-get update
E: Type ‘--13:28:08--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

since this happened i havent been able to open synaptic either, any ideas?

---

### Post by sisco311 on 2008-09-23
post the output of:
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by Elfy on 2008-09-23
Hi run this to remove the file

```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```

Then rerun the commands to get the medibuntu repos

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

That should do it - run each command seperately.

---

### Post by zanuvio on 2008-09-23
> **sisco311 said:**
> post the output of:
```
cat /etc/apt/sources.list.d/medibuntu.list
```

here it is: 

--13:41:43--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list.2'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

    0K                                                       100%   20.71 MB/s

13:41:44 (20.71 MB/s) - `hardy.list.2' saved [226/226]

---

### Post by Elfy on 2008-09-23
Yes - it's wrong :), follow my post.

---

### Post by zanuvio on 2008-09-23
i tried what you suggested, seems like the same problem again, the output was;

E: Type ‘--17:59:10--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by Elfy on 2008-09-23
Can you run this command

```
ls /etc/apt/sources.list.d/medi*
```

I think it will show more than one hardy list, paste the result please

---

### Post by zanuvio on 2008-09-23
i ran the command as i understood it:

david@dreamweaver:~$ ls etc/apt/sources.list.d/medi*
ls: cannot access etc/apt/sources.list.d/medi*: No such file or directory

---

### Post by Elfy on 2008-09-23
Run this command it should open the file to edit 

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

If there is anything in the file delete it and paste this in, save and close 

> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Once the file has been saved run

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by zanuvio on 2008-09-23
That seems to have done the trick, thanks very much!!

---

### Post by oldos2er on 2008-09-23
> **zanuvio said:**
> i ran the command as i understood it:

david@dreamweaver:~$ ls etc/apt/sources.list.d/medi*
ls: cannot access etc/apt/sources.list.d/medi*: No such file or directory

 Just FYI, this didn't work because you left out the leading "/". The command should be ls /etc/apt/sources.list.d/medi*

---

### Post by zanuvio on 2008-09-23
ok, thanks.. im a bit new to the command line but that makes sense:)

---

