---
title: "Need Help with Xamp /MySql Connection"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by vincej on 2011-11-30
Hi - I use 11.10 and recently installed Mysql successfully. I have also co-incidentally also installed ssh server for remote connection. 

I go to Localhost through my browser and I get a message:

"The server localhost:80 requires a username and password. The server says Xampp user"

But it refuses my Id & pw combo which I use for everything. 

Is there a default pw somewhere which I don't know about ?? 

Any ideas ??

Many thanks !!

---

### Post by wishyjr on 2011-12-01
when you install SQL, i think the installation process creates a 'database user' account on the computer. I'm not sure if there is a default user and password but looks like 'Xampp User' may be the user you need to login with. 

I also think that the default user for a MySQL db is 'root' for both user and passwd, try that (and then look into changing it ;) )

---

### Post by vincej on 2011-12-01
thanks for that - I've tried using the root username and password and thats a no go. 

Personally I think this has more to do with the fact that at the same time, roughly, I also installed ssh server and a vnc server. However, in all cases I always use the same id and pw. 

confused. 

Thanks

---

### Post by CoffeeRain on 2011-12-01
I installed XAMPP and it seemed straightforward. You might check the permissions on the XAMPP/htdocs directory. It all worked for me. Have you looked at the XAMPP control panel? Also, there may be a problem with your code connecting to the MySql database.

---

### Post by vincej on 2011-12-01
agreed - xampp is easy. My problem is that I can not even get to the phpinfo page ie xampp control panel as I am locked out with the message,  "server:80 requires authentication .... server says xampp"

I will see if there is anything in te config files, but I have never seen anything there before. 

thanks

---

### Post by vincej on 2011-12-01
solved ! 

when you install xampp on linux xampp is very 'helpful' in that it sets up a default user name of 'lampp'. 

it asks you for a password, sure, but it uses it's default user name ... so unless you're paying attention, which I obviosly wasn't you'll never get in. 


This contrasts with the Microsoft install where it asks you for both user name and password. I have installed xampp on MSFT many times and obviously was not paying attention.

---

