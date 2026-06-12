---
title: "Ubuntu 8.04 (UE 1.8) sh command"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by _aXXe_ on 2008-07-19
I downloaded the bonic/seti home program which is an .sh

I have the program, bonic, which is the LINUX version of Seti-home, in a directory that I can change to but I can't get the file to function. 
How do I get the file to work?

The file is as follows:

bonic_ubuntu_5.10.45_i686-pc-linux-gnu.sh

I've tried:

bonic_ubuntu_5.1045_i686-pc-linux-gnu.sh

sudo bonix_ubuntu_5.10.45_i686-pc-linux-gnu.sh

sudo sh bonic_ubuntu_5.10.45_i686-pc-linux-gnu.sh

Either the file isn't found or the command fails.

What did I miss?

---

### Post by phidia on 2008-07-19
Try  ./bonic_ubuntu_5.10.45_i686-pc-linux-gnu.sh you may need to preface that with sudo but try as user 1st.

---

### Post by iaculallad on 2008-07-19
Or, make it executable first:

```
cd location_of_bonic_ubuntu_5.10.45_i686-pc-linux-gnu.sh
sudo chmod +x bonic_ubuntu_5.10.45_i686-pc-linux-gnu.sh
sudo ./bonic_ubuntu_5.10.45_i686-pc-linux-gnu.sh
```

---

### Post by _aXXe_ on 2008-07-19
I appreciate both of the responses, however I'm still not getting the result I expect. I typed and did "cut and paste" with no effect.
I'm still puzzled. I installed this program before in 7.10 so I'm just over looking something.

---

### Post by scorp123 on 2008-07-19
> **_aXXe_ said:**
> I appreciate both of the responses, however I'm still not getting the result I expect. I typed and did "cut and paste" with no effect.
I'm still puzzled. I installed this program before in 7.10 so I'm just over looking something. Can you please supply the output from an "ls -al" from the location where this file is stored?

---

### Post by _aXXe_ on 2008-07-19
chris@UbuntuUE:~/download$ ls -al
total 4180
drwxr-xr-x  2 chris chris    4096 2008-07-19 19:11 .
drwxr-xr-x 46 chris chris    4096 2008-07-19 16:16 ..
-rw-r--r--  1 chris chris 4256389 2008-07-18 18:06 boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
chris@UbuntuUE:~/download$

---

### Post by scorp123 on 2008-07-20
> **_aXXe_ said:**
> chris@UbuntuUE:~/download$ ls -al
total 4180
drwxr-xr-x  2 chris chris    4096 2008-07-19 19:11 .
drwxr-xr-x 46 chris chris    4096 2008-07-19 16:16 ..
-rw-r--r--  1 chris chris 4256389 2008-07-18 18:06 boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
chris@UbuntuUE:~/download$ ```
cd ~/download
chmod 755 ./*.sh
sudo bash ./boinc_ubuntu_5.10.45_i686-pc-linux-gnu.sh
``` If anything goes wrong, don't forget to copy & paste the exact output here.

---

