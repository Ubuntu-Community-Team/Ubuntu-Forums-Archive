---
title: "password asked when boot up"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by Lalaith on 2012-01-15
Hi, 

I've been using 11.10 as a dual boot since october with Unity. From a week or so everytime I boot up, Ubuntu asks my password twice even I'm already inside ubuntu (it's not the unlock-screen password). 
I think this started when I executed the Ubuntu One app for the first time about a week ago to back up my data. It may be important to say that I only have one user account so I'm always booting as admin.
Also, Ubuntu asks me again my password when I enter banshee (before it didn't happen).

Do you know why is it asking me for the password? Is it important? If not, how can I get rid of this annoying message?

Thank you in advance. :)

---

### Post by lechien73 on 2012-01-15
Is this like a gksudo password, or is it your keyring password?

---

### Post by Lalaith on 2012-01-16
The message asks me about keyring password. (is it different than sudo password?)

---

### Post by nhasian on 2012-01-16
If you change the keyring password to an empty password it will stop asking you for the keyring password during bootup.

Go to System -> Preferences -> Passwords and Encryption Keys, which will display the following dialogue. 

From here, select “Passwords: Login” -> right-mouse click -> and select “Change Password”.

---

### Post by Lalaith on 2012-01-16
Thanks a lot. :)

In my case, the UbuntuOne password was the first password that the keyring had to store, and I think that's why I was never before asked for it.

With Unity, I had to search from the dash all the system aplications and there I found the "passwords and keys" app. 

I found also some information that may help to others to learn what is the keyring password.
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)
[http://mexpolk.wordpress.com/2008/02/06/ubuntu-change-default-keyring-password/](http://mexpolk.wordpress.com/2008/02/06/ubuntu-change-default-keyring-password/)

Thanks again! :popcorn:

---

