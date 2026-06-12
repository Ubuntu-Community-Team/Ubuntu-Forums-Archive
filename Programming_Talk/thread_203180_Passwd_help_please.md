---
title: "Passwd help please"
date: 2006-06-24
forum: Programming Talk
---

### Post by profediego on 2006-06-24
Hi everyone...

I decided i am currently experimenting on shell scrpting using kdialogs, the thing is this, how can i use  passwd to change a password for a user but passing the parameters user and password to passwd.  I hope you inderstand what i am sayin.   my english is terrible i know.

i mean, i can for example do this

user=Juancho
passwd $user

and then the system ask for the new password, but i want to pass the password as a parameter to passwd as i did in the example with the user.  I already read the man for passwd but i can understand how.

Thanks for your help

---

### Post by David_T on 2006-06-24
There is no way to do it with this implementation of passwd, though I guess there are some implementations on RedHat that let you use an --stdin option and pipe in the password unencrypted.

---

