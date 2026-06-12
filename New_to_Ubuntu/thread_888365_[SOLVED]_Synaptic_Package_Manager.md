---
title: "[SOLVED] Synaptic Package Manager"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by gunner ra on 2008-08-13
Hi Guys I tried to install Opera. However I cannot access Synaptic; I get this error: : Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.? Any advice please The Gunner

---

### Post by null byte on 2008-08-13
Please paste the content of /etc/apt/sources.list and /etc/apt/sources.list.d/medibuntu.list

---

### Post by iaculallad on 2008-08-13
> **gunner ra said:**
> Hi Guys I tried to install Opera. However I cannot access Synaptic; I get this error: : Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.? Any advice please The Gunner

Open your terminal and edit the file medibuntu.list:

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

Select all texts inside the file and delete it. Save file and close. Now, back in your terminal, input the following codes below (Assuming your using Hardy):

Add the Repository:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```Add the GPG Key:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
Then try installing Opera.

---

### Post by gunner ra on 2008-08-13
Thank you for you replies, Nullbyte & Jacullad. Jaculla you are an star your explanation was clear & concise and worked a treat. Thanks Guys Gunner:)

---

