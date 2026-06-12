---
title: "My Ubuntu Software Center hanging"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by amr elsayed on 2012-06-24
My Ubuntu  10.04 Software Center has been hanging on installation of skype.
How can ifix this ?:confused:

---

### Post by raja.genupula on 2012-06-24
have you tried to install it from the terminal ??

are you getting same behavior for other installation with the Software center .

---

### Post by jllipke on 2012-06-25
He means to go into terminal and type in 

```
sudo apt-get install skype
```

When it is finished downloading it will be in your Internet menu in the applications.

---

### Post by NikTh on 2012-06-25
If this is a problem only with Skype , then your threads title is wrong. If you facing that also with other applications then Ok. 
You must know that Skype its closed source application of microsoft. One of the disadvantages of that is , we don't know how to test it and fix it.  If it works then works , if not ... you don't have many options. 
For the problem of installation check out the terminal . Open it , try to install it from there and note any errors might help.
```
sudo apt-get purge skype skype-bin 
sudo apt-get update 
apt-cache policy skype
```see the result of last command . It must say **installed: (none)**
then proceed with installation
```
sudo apt-get install skype
```

---

