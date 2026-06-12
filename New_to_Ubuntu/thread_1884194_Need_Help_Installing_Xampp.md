---
title: "Need Help Installing Xampp"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by vincej on 2011-11-20
Hi I am very new to Ubuntu and Linix,

I have followed the instructions given on the Xampp site very carefully. See: [http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)

I have Xampp downloaded. However, when I go to extract the tar file into /opt I get a series of errors: 

"Cannot mkdir: Permission denied"

Looking at the permissions for /opt everything belongs to Root. Logging in as sudo makes no difference. 

Root is locked so I can not change owners or permissions and sudo does not grant me the authority to do it. 

So I seem to have hit a brick wall. The Xampp site seems to assume that you can write to /opt where as in Ubuntu you can not. 

So what have I done wrong ? 

Many, Many thanks  !

---

### Post by -LynX- on 2011-11-20
> **vincej said:**
> Hi I am very new to Ubuntu and Linix,

I have followed the instructions given on the Xampp site very carefully. See: [http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)

I have Xampp downloaded. However, when I go to extract the tar file into /opt I get a series of errors: 

"Cannot mkdir: Permission denied"

Looking at the permissions for /opt everything belongs to Root. Logging in as sudo makes no difference. 

Root is locked so I can not change owners or permissions and sudo does not grant me the authority to do it. 

So I seem to have hit a brick wall. The Xampp site seems to assume that you can write to /opt where as in Ubuntu you can not. 

So what have I done wrong ? 

Many, Many thanks  !

you need to extract XAMPP on your home folder, after that you can move that to /opt (by using sudo mv)

---

### Post by beew on 2011-11-20
You need root permission. Down load the tar.gz file to your home directory then run in the terminal

```
sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt
```

---

### Post by vincej on 2011-11-21
Thank you ! it worked perfectly ! The transition from Microsoft to Linux is not always easy !

---

