---
title: "NGINX installation problem"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by Kaelung on 2014-08-12
Hello everyboy,

I'm hopping you could help to solve this because I've tried many things and I'm now running out of ideas...

I have a Ubuntu 14.04 server where I want install nginx. I've already completed an installation of nginx but I was forced to uninstall it. It's where I've done something bad:
I've uninstalled nginx using apt-get purge nginx and then, remove the nginx folder in /etc.
But now I have to install it again and of course apt-get install nging giving me no error but when I try to launch it I have a Error: /etc/nginx/nginx.conf No such file or directory.
There is no nginx folder creatde in /etc during installation.
I'm wondering how to solve this, I don't know Ubuntu well...

Could someone help me please?

Thank in advance,

Ps: forgive my english...

Kaelung

---

### Post by JetStorm on 2014-08-12
Try the following:

**sudo apt-get --purge remove nginx***

 but be careful not to remove something else because of the asterisk at the end

After that install it again with:
**sudo apt-get install nginx**

---

### Post by Kaelung on 2014-08-12
JetStorm,

Thanks for your rapid answer.

I've done sudo apt-get remove --purge nginx*
It gave me: after this operation 95.2ko will be removed ==> Ok

Then, sudo apt-get install nginx
It gave me: after this operation 95,2ko of free space will be used ==> Ok

And again it gave me a /etc/nginx/nginx.conf no such file or directory...

It's strange because I think there must be a remanent file who stay and say something like "don't create /etc/nginx, folder already there"

Have you any idea?

Many thanks again

Kaelung

---

### Post by JetStorm on 2014-08-12
The file size you reported seems too small for all the nginx related packages.
On a default installation (apt-get install nginx) it should install at least these two packages as well:
nginx-common 
nginx-core

Paste the list of packages that are getting removed from apt-get --purge remove nginx

And before that you can try installing these two packages:
nginx-common 
nginx-core

---

### Post by Kaelung on 2014-08-12
JetSorm,

I've done a manual instal of package -core and -common.
It says: 0 updated, 0 new installed, 0 to removed, 2 not updated. (for the two package)

I've try "apt-get remove -u --purge nginx
It say: following package will be remove: nginx*
0 updated, 0new installed, 1 to removed, 2 not updated
after this operation 95,2 ko of disc space will be free

Thanks,
Kaelung

---

### Post by sandyd on 2014-08-12
try
```

sudo apt-get purge nginx nginx-*
sudo apt-get -o Dpkg::Options::="--force-confmiss" install --reinstall nginx
```

---

### Post by Kaelung on 2014-08-12
Sandyd thanks a lot!! you save me from my headache!
It worked!
the purge nginx nginx-* removed 1200 ko and the second command line tell that /etc/nginx don't exist so create new one!

I can continue my installation now ^^

Thanks again for your precious help,
Kaelung

---

