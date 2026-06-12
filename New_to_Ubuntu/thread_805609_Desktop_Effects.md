---
title: "Desktop Effects"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by jayz_sg on 2008-05-24
Hello,

I am trying to enable my desktop effects for my user, but everytime I try i get a message, unable to enable desktop effects. However my root account(ubuntu) is able to enable this setting. So i tot that is may be coz of some group issue. So i made sure that this acct belongs to the same groups of that of ubuntu, but still the same. I tried searching for this, but I nv came across this prob where only certain user can enable desktop effects. Thanks in advance.

---

### Post by meborc on 2008-05-24
root account? you mean using sudo? cuz there is no root account by default in ubuntu... the account you made during the installation is your user account, not the root account...

more info - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by philinux on 2008-05-24
> **jayz_sg said:**
> Hello,

I am trying to enable my desktop effects for my user, but everytime I try i get a message, unable to enable desktop effects. However my root account(ubuntu) is able to enable this setting. So i tot that is may be coz of some group issue. So i made sure that this acct belongs to the same groups of that of ubuntu, but still the same. I tried searching for this, but I nv came across this prob where only certain user can enable desktop effects. Thanks in advance.

How exactly are you trying to turn them on. What are your system specs?

---

### Post by jayz_sg on 2008-05-24
> **meborc said:**
> root account? you mean using sudo? cuz there is no root account by default in ubuntu... the account you made during the installation is your user account, not the root account...

more info - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

ok i think i should have been more clear. 1stly I did not install ubuntu into my system. I am using a pendrive using persistance mode. By default there is a user called live user, which has the username ubuntu.

---

### Post by jayz_sg on 2008-05-24
> **philinux said:**
> How exactly are you trying to turn them on. What are your system specs?

I went to system > perference > appearence then I clicked on the visual effects tab and clicked on the 2nd radio button which says normal. After a while there will be a error message which says: Desktop effects could not be enabled

---

### Post by philinux on 2008-05-24
Ok so it sounds like a graphics driver issue.

System>Admin>Hardware Drivers should have an option?

---

### Post by jayz_sg on 2008-05-24
> **philinux said:**
> Ok so it sounds like a graphics driver issue.

System>Admin>Hardware Drivers should have an option?

I'm very new to linux. However I really dun think it's a driver issue. Coz like I said, it works perfectly fine in one user. But all other users which I create it's not working.

---

