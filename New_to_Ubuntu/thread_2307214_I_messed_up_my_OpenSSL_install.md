---
title: "I messed up my OpenSSL install"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by james188 on 2015-12-22
Hello everyone,

This is the guide that I was following when I screwed things up: [http://hardenubuntu.com/server-setup/fix-openssl-heartbleed/](http://hardenubuntu.com/server-setup/fix-openssl-heartbleed/)

This is what I did:

openssl version -v 
openssl version -b

The above commands indicated that openssl needed to be updated, so I ran the following commands:

sudo apt-get update
sudo apt-get upgrade openssl libssl-dev 
apt-cache policy openssl libssl-dev

openssl version -b

The above command returned a newer build date.

I then ran the following command:

sudo ln -sf /usr/local/ssl/bin/openssl `which openssl`

Which was a big mistake! I guess I should get some more sleep.

If I run the following commands:

openssl version -v 
openssl version -b

It says: The program 'openssl' is currently not installed. You can install it by typing: sudo apt-get install openssl

When I run sudo apt-get install openssl

I get:

Reading package lists... Done 
Building dependency tree Reading state information... Done 
openssl is already the newest version.

What have I done!

Can someone please help?

Thank you,
James

---

### Post by kevdog on 2015-12-22
just remove the symbolic link to openssl.  

To find out your openssl binaries try:
sudo updatedb
locate openssl

---

### Post by james188 on 2015-12-23
> **kevdog said:**
> just remove the symbolic link to openssl.  

To find out your openssl binaries try:
sudo updatedb
locate openssl

Thanks for the reply.

I really have no clue how to remove the link. 

Would I use the following command:   rm /usr/local/ssl/bin/openssl `which openssl`

Thanks,
James

---

### Post by steeldriver on 2015-12-23
I think you have *overwritten* /usr/bin/openssl with a link to a (probably non-existent) file

You *could* remove the link - but then there's be nothing there (symlinks aren't like filesystem mounts). I suggest re-installing the package

```

sudo apt-get install --reinstall openssl

```

---

### Post by james188 on 2015-12-23
> **steeldriver said:**
> I think you have *overwritten* /usr/bin/openssl with a link to a (probably non-existent) file

You *could* remove the link - but then there's be nothing there (symlinks aren't like filesystem mounts). I suggest re-installing the package

```

sudo apt-get install --reinstall openssl

```

Problem fixed!

Thank you

---

### Post by sandyd on 2015-12-23
By the way, OpenSSL is already patched on Ubuntu versions. See [http://www.ubuntu.com/usn/usn-2165-1/](http://www.ubuntu.com/usn/usn-2165-1/)

---

### Post by james188 on 2015-12-25
> **sandyd said:**
> By the way, OpenSSL is already patched on Ubuntu versions. See [http://www.ubuntu.com/usn/usn-2165-1/](http://www.ubuntu.com/usn/usn-2165-1/)

Thank you

---

