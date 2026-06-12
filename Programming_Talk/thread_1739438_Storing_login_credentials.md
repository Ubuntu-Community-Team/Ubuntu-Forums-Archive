---
title: "Storing login credentials"
date: 2011-04-25
forum: Programming Talk
---

### Post by lavinog on 2011-04-25
I am working on a python project that accesses a database.

The program has the database login credentials in the connection function.

Security is not an issue with this project since anyone using the program has admin rights to the database anyway, however it made me wonder what best practice would be for something like this.

The easiest solution would be to have to program ask for the credentials.  Are there any other ideas?

---

### Post by BkkBonanza on 2011-04-26
If you're concerned about the credentials in the connection function then you could use an ssl connection to protect them. If you want them to be remembered by the program then you would have to use some encryption to keep them safe but at some point a connection needs to be authenticated, so short of storing the values you would have to prompt for them.

(As far as storing credentials the general wisdom is to salt+hash(encrypt) the password and only store the coded version so that someone able to read the database cannot find out the passwords. Then the password check in your app would salt+hash any password attempts and compare that to the database value. This won't work for the connection though as it's not going to take a hased value.)

---

### Post by simeon87 on 2011-04-26
> **BkkBonanza said:**
> If you're concerned about the credentials in the connection function then you could use an ssl connection to protect them. If you want them to be remembered by the program then you would have to use some encryption to keep them safe but at some point a connection needs to be authenticated, so short of storing the values you would have to prompt for them.

(As far as storing credentials the general wisdom is to salt+hash(encrypt) the password and only store the coded version so that someone able to read the database cannot find out the passwords. Then the password check in your app would salt+hash any password attempts and compare that to the database value. This won't work for the connection though as it's not going to take a hased value.)

Hashing is not the same as encrypting as you are suggesting. Encryption is intended to be reversible while hashing is not. I know this is a matter of terminology but passwords are hashed when storing them in a database and they are encrypted when you're storing them for in a personal digital safe (as you still want to obtain them by, for example, entering a master password to decrypt them).

---

### Post by BkkBonanza on 2011-04-26
Yes, understood. I meant to imply either depending on your circumstances, though from a user perspective not being able to reverse the password stored is preferred.

---

