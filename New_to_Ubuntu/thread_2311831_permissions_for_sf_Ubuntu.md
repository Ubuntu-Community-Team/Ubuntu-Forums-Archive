---
title: "permissions for sf_Ubuntu"
date: 2016-01-30
forum: New to Ubuntu
---

### Post by h-dieter on 2016-01-30
Hello,

on my Laptop is Ubuntu 14.04.2 in Virtualbox (host is Win10) - so far, so good.

I get an error message:

 You do not have the permissions necessary to view the contents of sf_Ubuntu

Yes, I have install the guest adds
Yes, I have install the extension pack for the right VB-version
Yes, I have enter in the Ubuntu terminal xTerm: 
sudo adduser [my user name] vboxsf 

Then the terminal want my password ... O.K. ...

But I can't enter my password! After 3 attempts I get an error message from the terminal!

What is wrong here ?

Thanks for answer in advance.

Regards,
Dieter

PS: How can I upgrade from 14.04.2 to 14.04.3 without data lost ... from a iso-file?

---

### Post by steveo314 on 2016-02-01
See if this gives you any help with the sf_Ubuntu
[http://unix.stackexchange.com/questions/52667/file-permission-issues-with-shared-folders-under-virtual-box-ubuntu-guest-wind]("http://unix.stackexchange.com/questions/52667/file-permission-issues-with-shared-folders-under-virtual-box-ubuntu-guest-wind")

As far as 14.04.02 to 14.04.03:
run this in a terminal:
```
sudo apt-get update && apt-get dist-upgrade
```
the kernel will not be updated automatically though, you'll have to install a newer one manually.
the .02 and .03 are more for the iso images that you download from Ubuntu.

---

### Post by steeldriver on 2016-02-01
> **h-dieter said:**
> 
Yes, I have enter in the Ubuntu terminal xTerm: 
sudo adduser [my user name] vboxsf 

Then the terminal want my password ... O.K. ...

But I can't enter my password! **After 3 attempts I get an error message from the terminal!**

What is wrong here ?


If you are getting a "3 unsuccessful password attempts" message, that means exactly what it says: either you are mistyping the password or (more rarely) a keyboard layout snafu is mangling your password

---

### Post by h-dieter on 2016-02-03
Hello,

thanks for the reactions.

I'm a newbie in the Ubuntu-World ...

O.K. I have realized the password in terminal is type in 'blind'! ... Good if you know it  ;-)

Regards,
Dieter

---

