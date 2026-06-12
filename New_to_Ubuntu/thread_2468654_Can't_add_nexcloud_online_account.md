---
title: "Can't add nexcloud online account"
date: 2021-11-06
forum: New to Ubuntu
---

### Post by turtho on 2021-11-06
Hello,

So i've been trying to use the online account GUI to sync all my files from my nextcloud account (from a provider).
So i try to add the nextcloud account but i get an error saying that the certificate is expired.
Anyway i click accept the certificate but even then i'm disconnected from the account and nothing else.
Anyone have input on this ?

---

### Post by ActionParsnip on 2021-11-06
Check your server side configuration with this
[https://linuxways.net/ubuntu/how-to-install-nextcloud-on-ubuntu-20-04-with-apache/](https://linuxways.net/ubuntu/how-to-install-nextcloud-on-ubuntu-20-04-with-apache/)

---

### Post by turtho on 2021-11-06
I don't have my own nextcloud server it's from a provider

---

### Post by ActionParsnip on 2021-11-06
Did you download the client from here
[https://nextcloud.com/install/#](https://nextcloud.com/install/#)

---

### Post by ActionParsnip on 2021-11-06
Did you download the client from here
[https://nextcloud.com/install/#](https://nextcloud.com/install/#)

---

### Post by turtho on 2021-11-06
Yes i did and i works fine, i'm just curious to what does it do to add an online account in ubuntu

---

### Post by ActionParsnip on 2021-11-07
Seems that you launch the client app and configure. Or is that where the problem lies?

---

### Post by TheFu on 2021-11-07
I found the Nextcloud integration in Ubuntu to **drastically impact performance**, system-wide.
Rather, I setup a webdav connection, which can be mounted/umounted as needed.  When it is mounted, it is still terribly slow and some things don't seem to work all the time.  Pushing files doesn't get noticed on other devices until I close/umount the connection. That makes it less useful too.

My setup follows a number of guides.  Using the ~/.NextCloud directory (which I had to exclude from my backup scripts) and ~/.davfs/ conig file.
In the /etc/fstab:
```
https://nextcloud.provider.com/nextcloud/remote.php/dav/files/user554/  /home/thefu/NextCloud davfs user,rw,noauto 0 0
```
and
~/.davfs2/secrets
looks like this:
```
/home/thefu/NextCloud  user554 "great423%$password-for the world"
```

I had to install a few packages - don't recall them now, but they were in the instructions.

---

### Post by naxal on 2021-11-09
> **turtho said:**
> Hello,

So i've been trying to use the online account GUI to sync all my files from my nextcloud account (from a provider).
So i try to add the nextcloud account but i get an error saying that the certificate is expired.
Anyway i click accept the certificate but even then i'm disconnected from the account and nothing else.
Anyone have input on this ?

Hello,

I am no expert with Linux but I too use NextCloud and it seems this issue is at your Service Providers end. Certificate in NextCloud is SSL and that is generated from Server end for securing the connection between Server - Client.

I use a self hosted NextCloud solution & at the time of server side installation and configuration, there is provision in server to run with strict SSL rules where server will refuse any and all communication if there is any issue certificate.

I wonder if that is the case here, have you raised this issue with the NextCloud provider?

Thanks.

---

### Post by TheFu on 2021-11-10
There are some reputable TLS testers in the world.  You can use an online tester ... which is probably better for any service provider when you open a ticket, so they can see the run/issue themselves.  Of course, there are LTS testers created in most scripting languages, like testssl (found in github).

Or you can use openssl ..
```
openssl s_client -crlf -verify_return_error -connect nc.domain.com:443
```
though this is mostly useful for checking which TLS version(s) are available and which are not.   For any website used today, really only TLS 1.3 should be enabled.  v1.2 is known cracked.

---

