---
title: "Passowrds on Shares"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by wabbit46 on 2008-06-01
When I try to access a share folder it asks me for a password.

I have no idea what password I should enter. My security level in Samba is set to SHARE

Regards,

Roger

---

### Post by IHATEDLINK on 2008-06-01
> **wabbit46 said:**
> When I try to access a share folder it asks me for a password.

I have no idea what password I should enter. My security level in Samba is set to SHARE

Regards,

Roger

Just enter your Ubuntu username and password.

---

### Post by wabbit46 on 2008-06-01
I have tried that it does not work.

---

### Post by moffa on 2008-06-01
Try user name: guest
password: [blank]

if that doesn't work, try forcing the user to the guest account in the share like:

[home share]
path=/home/me
force user = guest
guest ok = yes

and then try connecting

---

### Post by sisco311 on 2008-06-01
Set up a samba password from the terminal:
```
sudo smbpasswd ***username***
```Set up a samba password for a windows user:
```
sudo useradd **windowsusername**
sudo smbpasswd ***windowsusername***
```

---

### Post by wabbit46 on 2008-06-02
Thanks for your advice but the command:-

sudo smbpasswd username

advises be it cannot find my username

---

### Post by sisco311 on 2008-06-02
You need to replace username with your user name:
```
sudo smbpasswd wabbit46
```
assuming that wabbit46 is your user name in ubuntu.

---

### Post by wabbit46 on 2008-06-02
I have tried using my Ubuntu username but it appears not to be contained in the smbpasswd file.

---

### Post by sisco311 on 2008-06-02
Sorry, I forgot the -a option:
```
sudo smbpasswd -a username
```

EDIT: In order to the changes take effect, restart samba:
```
sudo /etc/init.d/samba restart
```
or reboot the computer.

---

### Post by wabbit46 on 2008-06-03
I have tried using the command sudo smbpasswd -a username and it appears to work.

However when I try the command sudo /etc/init.d/samba restart, it advises me it cannot find samba.

What I want to do is connect my Ubuntu box to a computer running Vista and share the files contained on the Vista machine.

I would appreciate any ideas on what is wrong. eg is my distro faulty.

---

