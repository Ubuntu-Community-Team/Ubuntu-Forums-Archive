---
title: "A password is always necessary ?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by fr34k on 2008-12-02
It may be the tradition from unix days . 
Why is every account forcing to have a password. 
There should have been an option for blank password.
Is there an option , did i miss it ?

---

### Post by jpkotta on 2008-12-02
There is no null password option.  It is deliberately hard to do, but can be done.  Why do you want no password?  You can make Ubuntu automatically log you in, and it is very wrong to configure sudo to work without passwords.  This is not just a security thing - it is a good thing to know when you are about to do something as root.

---

### Post by nhasian on 2008-12-02
i believe if you remove the password it automatically disables the account.

you can have your ubuntu auto log you in so you dont have to enter your password to use the pc.

go to System/Administration/Login Window then under the Security tab you can enable automatic login.

---

### Post by fr34k on 2008-12-02
No , not the sudo account.

I was trying to set one from the "users" group with a blank password. 

I enabled automatic login option for that user . But still it requires password when loggin in . So, what exactly does automatic login option do?

---

### Post by Paqman on 2008-12-02
> **fr34k said:**
> 
I enabled automatic login option for that user . But still it requires password when loggin in . So, what exactly does automatic login option do?

Make sure you enable "timed login", it'll wait a few seconds for someone else to log in, and if they don't it'll automatically log that person in.

---

### Post by fr34k on 2008-12-02
> **Paqman said:**
> Make sure you enable "timed login", it'll wait a few seconds for someone else to log in, and if they don't it'll automatically log that person in.


Ok. That clarifies automatic logging in. I checked it out.

But what i originally intended was a situation where users could login without the burden of remembering a username and password. 

By using face browser, the username can be displayed. Still, the user needs to remember his password.

---

### Post by Paqman on 2008-12-02
> **fr34k said:**
> 
But what i originally intended was a situation where users could login without the burden of remembering a username and password. 


Afraid that's not really possible. Linux is designed as a multi-user system, knowing your username and password is just part of that.

---

### Post by jpkotta on 2008-12-03
It is possible to have a null password.  I've never done it in Ubuntu but I have done it in Linux (actually uClinux).  But I don't think there is any way of not having the "burden" of a username.

---

### Post by Temposs on 2008-12-03
If you're using Ubuntu 8.10, you could use a guest session when a user of the computer doesn't have an account/know a password for an account.

From [http://www.ubuntu.com/news/ubuntu-8.10-desktop:](http://www.ubuntu.com/news/ubuntu-8.10-desktop:)

> Guest Sessions

In a world of 'always on' pervasive computing it is more likely that users lend their computers to colleagues or friends at conferences, cafes or at parties so they can check email, etc. Guest sessions allow users to lock down a session easily so a guest can use the full system without interference with programs or data. 

---

### Post by fr34k on 2008-12-06
Its a bad practice to have a user account with no password with the security risks involved . I accept it.
I asked whether its possible because Windows allows me to do so and i have users associated with my system who prefer this way.

About Guest account,as far as i know,it can be accessed only from User Switcher of a permanent account in intrepid. So a guest cannot log on his own and has no write permission anywhere.

---

