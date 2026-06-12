---
title: "Mysql - client program disapeared"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by vagelism on 2012-05-31
Hello to all!
I upgrade to 12.10 LTS and mySQL client program dissapeared. I installed it again threw the software center but I can not find it under programming menu like usual. 
Any Ideas? 
Thank you!

---

### Post by Senior_Buckethead on 2012-06-05
If you open synaptic, and in the search box type: mysql client
is mysql-client-5.5 box greened out?

If it isnt, you can install it via apt:
```

sudo apt-get update
sudo apt-get install mysql-client-5.5
sudo apt-get clean

```
 or if it is installed but you can uninstall it by typing:
```

sudo apt-get remove mysql-client-5.5
sudo apt-get purge mysql-client-5.5

```
above the update line above.
Or, if you fancy, you can uninstall/install via. synaptic.

Hope that helps

---

### Post by vagelism on 2012-06-05
> **Senior_Buckethead said:**
> If you open synaptic, and in the search box type: mysql client
is mysql-client-5.5 box greened out?

If it isnt, you can install it via apt:
```

sudo apt-get update
sudo apt-get install mysql-client-5.5
sudo apt-get clean

```
 or if it is installed but you can uninstall it by typing:
```

sudo apt-get remove mysql-client-5.5
sudo apt-get purge mysql-client-5.5

```
above the update line above.
Or, if you fancy, you can uninstall/install via. synaptic.

Hope that helps

The only that did was to remove my sql server and nothing else!!!

---

### Post by Senior_Buckethead on 2012-06-05
Oh dear God read the post properly!

---

### Post by vagelism on 2012-06-05
> **Senior_Buckethead said:**
> Oh dear God read the post properly!

I did! You and this command to remove...because I had it installed allready didnt remove only the client but also the server. 
Any way I will install it again!
Thank you!

---

