---
title: "403 for user website"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by ray3 on 2013-09-20
Hello everyone I have been teaching myself Linux and I have recently setup a local webserver on my network. Everything works if I run website under /var/www. I wanted to run site under /home/user/public_html. I enabled userdir my gave ownership or /home/me/public_html to myself and www-data group, set permissions to 755 but I was getting 403 error. After searching google I read that I had to set permissions to my home directory like so ```
sudo chmod o+rx
``` which allowed my to access my site. Here is where it gets weird, when I close my ssh session I receive the 403 error. I used ftp to connect to server and set permissions from my home directory to 755 and I was able to access site but once I close it I get the 403 error again. When I checked logs I see permission errors. I don't understand what I'm doing wrong.:confused:

---

### Post by TheFu on 2013-09-20
Could the home directory be encrypted?

---

### Post by ray3 on 2013-09-21
yes it is.

---

### Post by TheFu on 2013-09-21
> **ray3 said:**
> yes it is.

Well, if the directory is encrypted, then it is only decrypted when the same user is logged in. I can't think of any way to get around that besides putting files outside the encrypted storage, can you?

Seems to me THAT is sorta the point of having an encrypted HOME. ;)

---

### Post by ray3 on 2013-09-21
> **TheFu said:**
> Well, if the directory is encrypted, then it is only decrypted when the same user is logged in. I can't think of any way to get around that besides putting files outside the encrypted storage, can you?

Seems to me THAT is sorta the point of having an encrypted HOME. ;)

Yes I am able to move the site out of my home directory. Thanks for the info.

---

