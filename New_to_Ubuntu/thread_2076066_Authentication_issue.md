---
title: "Authentication issue"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by Jazzeck on 2012-10-25
Hi. I have a problem authenticating when i want to update. Right now I have 480 updates in my update manager, but I simply cannot authenticate. It's just saying "Authentication attempt was unsuccessful. Please try again". Im using the same password for my user login (or whatever it's called). And I can't remember that I've ever used another password. Is there at least a way to reset it?
I'm using 12.04, by the way.
I hope someone can help!

---

### Post by NikTh on 2012-10-25
Hi , 

please open a terminal and try from there . With CTRL+ALT+T you can open a terminal . 
Keep all other applications closed. 

Then give this command 
```
sudo apt-get update
``` 
it will ask for your password , write it carefully cuz nothing will show up (like you not write). 

If you see results other than "password incorrect" , then apply this command too 
```
sudo apt-get dist-upgrade
``` and be patient until all (480) updates installed successfully.

Thanks

---

### Post by Jazzeck on 2012-10-25
It just says that my password is incorrect???????? WTF!! Why would it be any different from the one I use at login?
But thank you very much for your help. I hope you know what to do next...
By the way, it's also saying something about 3 incorrect password attempts. Am I totally f...ed now?

---

### Post by danielbauwens on 2012-10-25
Are you the owner of the computer? Or are you a sub user?
It may be that you need the admin (root) to login to update the packages.

Daniel

---

### Post by Jazzeck on 2012-10-25
> **danielbauwens said:**
> Are you the owner of the computer? Or are you a sub user?
It may be that you need the admin (root) to login to update the packages.

Daniel

I'm the owner of the computer, and I haven't had any problems updating until now. But I can't tell if this is the password I've been using all the time. It's a long time since I have had this computer in use, since I have got myself a MacBook (thank God!!). Hence the many updates. 
I just cannot see what password it wants me to use. I have tried all the ones I can imagine.

---

### Post by NikTh on 2012-10-25
Ok ,
in case you have forgot your password , you can follow this guide : 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

to reset it. Read carefully the guide . You will need only to boot from the recovery mode. 

Thanks

---

### Post by Jazzeck on 2012-10-25
> **NikTh said:**
> Ok ,
in case you have forgot your password , you can follow this guide : 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

to reset it. Read carefully the guide . You will need only to boot from the recovery mode. 

Thanks

Wohooo. It works! Thank you so much!:)

---

