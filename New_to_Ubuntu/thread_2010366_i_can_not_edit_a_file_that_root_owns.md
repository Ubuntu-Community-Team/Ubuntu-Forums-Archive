---
title: "i can not edit a file that root owns"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by ihsankocak on 2012-06-25
hi all, i even loginned as root and when trying to change it says:Sorry, could not change the permissions of "resolv.conf": Error setting permissions: Operation not permitted

1.owner of the file is root
2.i logined as root

it still rejects to change the permission of the file.
any helps please?

---

### Post by Paqman on 2012-06-25
On Ubuntu it's normally neither possible nor necessary to log in as root. When you say you logged in as root, what exactly did you do?

Normally all you need to do to take on root's powers is:
[LIST=1]
[*]Preface a terminal command with sudo OR
[*]Launch a graphical app with the preface gksudo (or kdesu for KDE)
[/LIST]
You can do these from your normal account if it's an administrator account (which the first account on the machine will be).

---

### Post by ihsankocak on 2012-06-25
> **Paqman said:**
> On Ubuntu it's normally neither possible nor necessary to log in as root. When you say you logged in as root, what exactly did you do?

Normally all you need to do to take on root's powers is:
[LIST=1]
[*]Preface a terminal command with sudo OR
[*]Launch a graphical app with the preface gksudo (or kdesu for KDE)
[/LIST]
You can do these from your normal account if it's an administrator account (which the first account on the machine will be).

i unlocked the root user by:
sudo passwd -u rootthen i logged in as root

---

### Post by nipunshakya on 2012-06-25
> **ihsankocak said:**
> hi all, i even loginned as root and when trying to change it says:Sorry, could not change the permissions of "resolv.conf": Error setting permissions: Operation not permitted

1.owner of the file is root
2.i logined as root

it still rejects to change the permission of the file.
any helps please?
 Welcome with your first post...
at your terminal, in order to edit any file, type sudo before the command... for example, if your file is abc.txt located at /usr/bin, in terminal type **sudo gedit /usr/bin/abc.txt**

---

### Post by ihsankocak on 2012-06-25
> **WinuxUser said:**
> Welcome with your first post...
at your terminal, in order to edit any file, type sudo before the command... for example, if your file is abc.txt located at /usr/bin, in terminal type **sudo gedit /usr/bin/abc.txt**

thank you.i tried sudo gedit /etc/resolv.conf, i could edit the file but it did not allow to save it i t said:You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by steeldriver on 2012-06-25
Hi what version of Ubuntu are you running? recent desktop versions use the resolvconf service in which case /etc/resolv.conf is a symlink and is not meant to be edited directly

What exactly are you trying to do?

---

### Post by bab1 on 2012-06-25
> **Paqman said:**
> 
[LIST=1]
[*]Preface a terminal command with sudo OR
[*]Launch a graphical app with the preface gksudo (or kdesu for KDE)
[/LIST]
You can do these from your normal account if it's an administrator account (which the first account on the machine will be).

As @Paqman says: [COLOR="Blue"]Launch a _graphical_ app with the preface **_gksudo_** (or kdesu for KDE)[/COLOR]

---

### Post by Paqman on 2012-06-25
> **ihsankocak said:**
> i unlocked the root user by:
sudo passwd -u rootthen i logged in as root

Ok, log out and log in to your regular user account then do it the way I described above.

Ubuntu does not use the root account, which is why it doesn't have a password by default.

---

### Post by ihsankocak on 2012-06-25
> **steeldriver said:**
> Hi what version of Ubuntu are you running? recent desktop versions use the resolvconf service in which case /etc/resolv.conf is a symlink and is not meant to be edited directly

What exactly are you trying to do?
it is Ubuntu 11.04. i am trying to change dns servers to 4.2.2.1 and 4.2.2.2

---

### Post by ihsankocak on 2012-06-25
> **Paqman said:**
> Ok, log back out and do it the way I described above.

Ubuntu does not use the root account, which is why it doesn't have a password by default.
ok Paqman i will try it.

---

### Post by nipunshakya on 2012-06-25
Its strange that i can totally edit the resolv.conf file in my ubuntu 12.04 using the same command and save it...
why don't you change your directory  to /etc using **cd /etc. **then copy the file to Desktop using [B]```
 sudo cp /etc/resolv.conf ~/Desktop/

``` , [/B]modify it and then put it back to /etc  using the same copy command??

---

### Post by ajgreeny on 2012-06-25
You can change dns servers with the network manager icon in your panel..

Right click on it, choose Edit connections.  Go to the ipv4 tab and change the Method box to **Automatic (DHCP) addresses only**.  In the DNS servers box enter **4.2.2.1,4.2.2.2** (note the comma between the two server addresses).

---

### Post by ihsankocak on 2012-06-25
> **ihsankocak said:**
> ok Paqman i will try it.
i used gksudo but it says the same thing:operation not permitted

---

### Post by ihsankocak on 2012-06-25
> **WinuxUser said:**
> Its strange that i can totally edit the resolv.conf file in my ubuntu 12.04 using the same command and save it...
why don't you change your directory  to /etc using **cd /etc. **then copy the file to Desktop using [B]```
 sudo cp /etc/resolv.conf ~/Desktop/

``` , [/B]modify it and then put it back to /etc  using the same copy command??
i tried it but this time it does not allows to copy file into etc.

---

### Post by ihsankocak on 2012-06-25
> **ajgreeny said:**
> You can change dns servers with the network manager icon in your panel..

Right click on it, choose Edit connections.  Go to the ipv4 tab and change the Method box to **Automatic (DHCP) addresses only**.  In the DNS servers box enter **4.2.2.1,4.2.2.2** (note the comma between the two server addresses).
at the begining i tried it but the save button is inactive evenif i wrote down the dns adresses.

---

### Post by ajgreeny on 2012-06-25
> **ihsankocak said:**
> at the begining i tried it but the save button is inactive evenif i wrote down the dns adresses.
I wonder if any of your problems now are due to your enabling the root account.  I have never needed that in 7 years of using ubuntu, so may be quite wrong, but it all seems very odd that you can not do what you ought to be able to using **sudo**.

---

### Post by ihsankocak on 2012-06-25
> **ajgreeny said:**
> I wonder if any of your problems now are due to your enabling the root account.  I have never needed that in 7 years of using ubuntu, so may be quite wrong, but it all seems very odd that you can not do what you ought to be able to using **sudo**.

no, this problem occured before i openned root account.indeed i opened root account inorder to solve this problem.

---

### Post by Paqman on 2012-06-25
OK, let's rule some stuff out. Create a brand new administrator account, log into it and see if you can achieve anything.

---

### Post by ihsankocak on 2012-06-25
> **Paqman said:**
> OK, let's rule some stuff out. Create a brand new administrator account, log into it and see if you can achieve anything.
hi, i added by sudo adduser abc2, sudo adduser abc2 admin. and same issues occur.

---

### Post by steeldriver on 2012-06-25
can you try

```
ls -l /etc/resolv.conf

lsattr /etc/resolv.conf
```

---

### Post by Paqman on 2012-06-25
> **ihsankocak said:**
> hi, i added by sudo adduser abc2, sudo adduser abc2 admin. and same issues occur.

You would need to set them up as administrators, not regular users. Add them to the admin group, or use Users and Groups to change the account type to administrator.

---

### Post by ihsankocak on 2012-06-25
> **steeldriver said:**
> can you try

```
ls -l /etc/resolv.conf

lsattr /etc/resolv.conf
```

they gave these results:
-rw-r--r-- 1 root root 92 2012-06-24 22:16 /etc/resolv.conf
-----a-----------e- /etc/resolv.conf

---

### Post by steeldriver on 2012-06-25
hmm.. so it looks like your file has the 'append only' attribute set? I don't really know why that would happen - is this a standard system or have you done any kind of hardening / security related stuff?

this is beyond my paygrade unfortunately

---

### Post by ihsankocak on 2012-06-25
> **Paqman said:**
> You would need to set them up as administrators, not regular users. Add them to the admin group, or use Users and Groups to change the account type to administrator.
i changed user into adminisrators but it says again:you dont have permission

---

### Post by ihsankocak on 2012-06-25
> **steeldriver said:**
> hmm.. so it looks like your file has the 'append only' attribute set? I don't really know why that would happen - is this a standard system or have you done any kind of hardening / security related stuff?

this is beyond my paygrade unfortunately
thank you for your help i didnt do any kind of hardening but maybe i changed it, i do not know.

---

### Post by steeldriver on 2012-06-25
well you should be able to remove it with 'sudo chattr -a /etc/resolv.conf' but I don't know what other consequences there might be - use at your own risk

or with the "a" attribute still set you should still be able to *append* a nameserver, e.g.

```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
```

however as mentioned before I think the new way of doing things discourages direct user modification and will likely overwrite any changes when you reboot (and/or restart network-manager)

---

### Post by ihsankocak on 2012-06-26
> **steeldriver said:**
> well you should be able to remove it with 'sudo chattr -a /etc/resolv.conf' but I don't know what other consequences there might be - use at your own risk

or with the "a" attribute still set you should still be able to *append* a nameserver, e.g.

```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
```however as mentioned before I think the new way of doing things discourages direct user modification and will likely overwrite any changes when you reboot (and/or restart network-manager)

it worked thank you very much Steeldriver

---

