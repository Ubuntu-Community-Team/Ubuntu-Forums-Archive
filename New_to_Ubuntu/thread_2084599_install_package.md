---
title: "install package"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by termvrl on 2012-11-15
hi all,

i want to ask. what is the different between, 
apt-get install, ./configure, make & make install. 

im new into ubuntu. dont understand how to install software.

Thanks.

---

### Post by Mr_JMM on 2012-11-15
Whilst I'm not 100% on all those I'll attempt to save you some grief.

To install software you can:
1. Use the Software center, search through all apps, click install, enter password, done.

2. If you know the name of the application use sudo apt-get install [package name] e.g. ```
sudo apt-get install synaptic
```.

3. Use either option above to install synaptic package manager and browse through that, select packages, press install.

4. Download a .deb file from a website e.g. Google's Chrome, once downloaded click on it to install it, it will open software manager.

Nice and easy.

---

### Post by Frogs Hair on 2012-11-15
If you are new to Ubuntu stick to the software center. ```
sudo apt-get install package-name
``` achieves the same result as the software center but with the terminal instead of the GUI.You are installing debian or .deb package from the Ubuntu repository either way. 

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)  

```
./configure, make & make install.
``` This is a command used when compiling/building an application from a tar.gz or similar package.  It is used when a package is not available in the repository and these packages usually have instructions included and will vary from application to application. The average user should not have to compile/build applications.

---

### Post by termvrl on 2012-11-15
hi
thanks for your reply.
if im using CLI, where can i find the software center.
or i need to turn on GUI at the first place?

thanks.

---

### Post by termvrl on 2012-11-15
hi Frogs & Mr_JMM,

ok. now i understand. 
Thanks!

---

