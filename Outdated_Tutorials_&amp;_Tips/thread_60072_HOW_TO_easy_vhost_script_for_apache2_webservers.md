---
title: "HOW TO: easy vhost script for apache2 webservers"
date: 2005-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by sickdude on 2005-08-26
This little script i made for me so i can make and remove vhosts easy. this is only for apache2, your ubuntu box.

if you find any bugs let me hear because it works ok for me but i hope that you can use it to. 

have fun  :smile: 


get

members.lycos.nl/metalmini/ubuntu/vhostusers.sh

you might have to do this to
```
sudo mkdir /etc/apache2/conf
```

```
sudo ./vhostusers.sh
```

and follow the text on the screen

yourdomain.com add/remove vhost users & rotate passwd
  To create use: -c -C option
  To remove use: -d -D option
  To rotate passwd use: -p -P option


 O:)

---

### Post by majikstreet on 2005-08-26
[QUOTE=sickdude]This little script i made for me so i can make and remove vhosts easy. this is only for apache2, your ubuntu box.

if you find any bugs let me hear because it works ok for me but i hope that you can use it to. 

have fun  :smile: 


get

members.lycos.nl/metalmini/ubuntu/vhostusers.sh

you might have to do this to
```
sudo mkdir /etc/apache2/conf
```

```
sudo ./vhostusers.sh
```

and follow the text on the screen

yourdomain.com add/remove vhost users & rotate passwd
  To create use: -c -C option
  To remove use: -d -D option
  To rotate passwd use: -p -P option


 O:)[/QUOTE]
 It should be "sudo sh vhostusers.sh". 

Haven't tested it, but it looks promising!

majikstreet

---

