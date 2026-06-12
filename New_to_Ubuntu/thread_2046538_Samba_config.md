---
title: "Samba config"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by wiradog on 2012-08-23
Hi Guys

I have just started to go through the process of configuring SAMBA for use with my Ubuntu 12.04 NAS.
I have had a go some years ago configuring SAMBA for a desktop version of Ubuntu, and got in quite a muddle. So I am more than keen to make sure I back up the original config.

[ATTACH]223064[/ATTACH]

Can anyone tell me why the above command does not work?
I am using this build to try and learn command line script and wean myself off the Windows mouse.

:-\"

---

### Post by Morbius1 on 2012-08-23
My first guess is that you didn't precede the cp command with a sudo:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

---

### Post by wiradog on 2012-08-23
Thanks Morbius 1,

I have been following the instruction on Sitepoint and they must have assumed that I was logged on with root privileges.

Good one, now for the tricky part-SAMBA

#-o

---

