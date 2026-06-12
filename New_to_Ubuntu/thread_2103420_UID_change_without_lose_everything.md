---
title: "UID change without lose everything"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by patty92 on 2013-01-10
Hi,

im quite new to this forum, so hello @ all 

my question is, that i have to change my UID, but then i do, i lose my GUI.
i am using a xubuntu 12.10 
so what have i to do, that i dont lose anything untill I am changing my UID?
hope for quick answers  

regards,

patrick

---

### Post by patty92 on 2013-01-10
No ideas ? 
do you need specific details of my workstation or something?

regards,
patrick

---

### Post by steeldriver on 2013-01-10
what exactly are you trying to do, and what exactly do you mean by "lose my GUI"?

---

### Post by dannyboy79 on 2013-01-10
why do you want to change your user id? just curious as there may be another solution to your end goal

here's a little guide for changing [http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/)

---

### Post by iMac71 on 2013-01-10
Do you have any problem with file permissions or what else?

---

### Post by grahammechanical on 2013-01-10
Are you referring to the fact that our user ID is connected to our Home folder?

Are you thinking that if we change our user name then we will get a new home folder with that new name and the system will not access the settings in the original home folder connected to our original user name?

If so, then you will, be correct. You also need to change the name of the home folder.

>  -l, --login NEW_LOGIN
           The name of the user will be changed from LOGIN to NEW_LOGIN.
           Nothing else is changed. In particular, the user´s home directory
           name should probably be changed manually to reflect the new login
           name.

[http://manpages.ubuntu.com/manpages/hardy/man8/usermod.8.html]("http://manpages.ubuntu.com/manpages/hardy/man8/usermod.8.html")

I do not recommend this tutorial. I provide it for your information.

[http://www.ubuntututorials.com/change-username-ubuntu-12-04/]("http://www.ubuntututorials.com/change-username-ubuntu-12-04/")

Regards.

---

### Post by patty92 on 2013-06-28
worked perfectly fine after I upgraded to xubuntu 13.04. Thany you for your help.

---

