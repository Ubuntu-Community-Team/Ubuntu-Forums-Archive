---
title: "Password doesn't work."
date: 2014-06-04
forum: New to Ubuntu
---

### Post by Sprinkman on 2014-06-04
I installed Ubuntu Server 14.04 on my laptop to test and learn for my server install in the near future.  After the install it asked me to set up a user name and password.  after the install was complete, it asked me for the user name and password. I entered them as I did during the setup and it will not accept them.  I don't know what to do.  I'm lost.

---

### Post by Tadaen_Sylvermane on 2014-06-05
Don't take this as rude, took me a few tries to figure this one out myself. Put your regular OS back in place on the laptop and use VirtualBox to learn what to do with the os. Bare metal is last step unless you really have zero choice.

To the password. Load up a live disk, chroot into the server install and make a new password. Also make sure caps lock isn't accidentally on. I've done that one before as well.

---

### Post by lisati on 2014-06-05
Passwords in Ubuntu are case sensitive. 'Password' is seen as different to 'password' and 'passWord'

Hope this helps.

---

### Post by nativehound on 2014-06-05
It's pretty easy to fix with this guide.
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password]("http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password")

---

### Post by Sprinkman on 2014-06-05
I found out what it was. When I chose a password, I used the left shift button to capitalize one of the letters.  When I was having trouble with the password, I was using the right shift.  Wow! touchy! I am using an old laptop to learn more about Ubuntu server.  I have a couple other computers that I use for everything else.  I am trying to learn how to setup a server for web hosting or even gaming so I can put it in a colo. any suggestions?

> **lisati said:**
> Passwords in Ubuntu are case sensitive. 'Password' is seen as different to 'password' and 'passWord'

Hope this helps.
I found out that Ubuntu sees the two shift keys as different keys.  Oops.
Thank you

I was told I can use webmin.  Is this a good hosting setup?

---

### Post by deadflowr on 2014-06-05
Merged posts.

I don't know how your keyboard is set up, but I use both shifts and on all my machines, they do the same exact thing as the other key.
Left shift = capitalize 
right shift = capitalize 

Maybe one was set as compose...

---

### Post by Sprinkman on 2014-06-09
Funny. I set my key board to default US. Both shift keys are independent.

---

### Post by DuckHook on 2014-06-09
> **Sprinkman said:**
> Funny. I set my key board to default US. Both shift keys are independent.Left and right shifts actually yield different capitalization codes. To see this, in a terminal, do:```
sudo showkey
```then press your left and right shift keys (you can leave showkey using <ctrl>+<c>). On my keyboard, left shift returns 42, but right shift returns 54. If some config file deep in the guts of your installation parses password entries by keycode instead of ascii letter code, then it is quite possible that passwords capitalized using the left versus right shift keys may be interpreted as different inputs. This is especially relevant for keyboard layouts that are non-English and Linux may treat the default-US keyboard in like manner for the sake of consistency.

---

