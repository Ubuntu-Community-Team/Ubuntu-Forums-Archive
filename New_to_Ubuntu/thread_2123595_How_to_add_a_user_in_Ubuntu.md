---
title: "How to add a user in Ubuntu"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by DanR01 on 2013-03-08
I'm compliling some software from source and it recommends creating a new user and group prior to executing make and make install. The command 

```
adduser <user>
```

does this but I don't really want a seperate directory created for the user nor do I want it to be added at login. Is there a command or switch that disables both of these? 

Thanks

---

### Post by cortman on 2013-03-08
You can remove the new user's home directory manually with rm, and [this]("http://askubuntu.com/questions/92349/how-do-i-hide-a-particular-user-from-the-lightdm-login-screen") shows how to remove them from the login screen.

---

### Post by coldcritter64 on 2013-03-08
I am not on an Ubuntu install atm, so cannot give you the correct command switches. I will however suggest you run the code,

```
man adduser
```

this will give you a description of the adduser command and its  switches, I am sure creating a user account without a home directory is one switch I've used in the past. Good luck.

---

### Post by DanR01 on 2013-03-08
Thanks for your swift replies.

---

### Post by coldcritter64 on 2013-03-08
OP, I just noted the "compiling from source" comment in your opening post. May I ask what software it is you are needing to compile ? I ask as beginners in Ubuntu will often **unnecessarily** compile software when there are more than adequate versions available in the repositories or in PPAs (personal package archives from ubuntu devs) hosted on launchpad.net. We may be able to make life much easier for you (and your package management system ;)) if a better option than building from source is available. Cheers.

---

### Post by DanR01 on 2013-03-08
The software is Gnunet version 0.9.5a (via subversion). I'm following the instructions here: [https://gnunet.org/ubuntu1204-gnunetgtk](https://gnunet.org/ubuntu1204-gnunetgtk)

There is an earlier version in the repos but I've been unable to get that package to work correctly on my system. I don't hold out particular hope that installing the later version will help but I thought I'd give it a try.

---

### Post by coldcritter64 on 2013-03-08
There is a gnunet ppa, but seems to be for older releases. Seeing as you've tried the repo version, compiling sounds about right :) Cheers.

---

