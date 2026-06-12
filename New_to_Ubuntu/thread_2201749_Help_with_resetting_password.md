---
title: "Help with resetting password"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by Joe_Green on 2014-01-25
Hi there,

I'm new to Linux and I installed an old Ubuntu version 9.10 on a desktop. I think my friend changed the password for userA. Now my friend doesn't remember what new password is. UserA was set to login automatically, so everytime computer boots up, it doesn't ask for password but we cannot Update Ubutu to the new version as it keeps asking us for UserA's password. We also don't know what is password of the root user. 

The computer goes locks the screen after a while it is idle and then it asks us to login, but since we don't know the password we cannot login. So to get back in we just restart the computer. 

Is there any way we can reset the root's and userA's password so that we can update Ubuntu. I hope the answer is not to reformat and reinstalle newer version of Ubuntu.

Thanks and hope to hear from you.

Joe Green

---

### Post by deadflowr on 2014-01-25
This will guide you on resetting the user's password
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Forget about resetting the root password, as it's locked and disabled by default, anyway.

---

### Post by Joe_Green on 2014-01-26
Thank you.

---

### Post by Impavidus on 2014-01-26
9.10 is so old that, instead of upgrading to a later release, it's best to create a live disk of 13.10 and install that. 9.10 is unsupported and has been unsupported for almost three years. This means that applications, especially the web browser and that kind of stuff, are old and have known unpatched security holes. Upgrading to a supported release is a two-step procedure (9.10&#8594;10.04 LTS&#8594;12.04 LTS), which is cumbersome with unsupported releases.

Consider using Xubuntu or Lubuntu if the hardware is old.

---

