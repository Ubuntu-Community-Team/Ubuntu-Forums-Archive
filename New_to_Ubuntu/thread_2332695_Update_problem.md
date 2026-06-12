---
title: "Update problem"
date: 2016-08-03
forum: New to Ubuntu
---

### Post by ioujojo on 2016-08-03
Hello, I'm new at ubuntu.I did an update yesterday that i didn't complete 
and next day the screen shows only this (in the picture) and i can't write or do anything.
I'd appreciate if someone could help me.

---

### Post by Bucky Ball on 2016-08-03
Welcome. If you hold Control+Alt and tap F1, do you get a big terminal and a login prompt? If so, try:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

... and reboot. This *will not* upgrade your installed release to a newer one. Which release are you using?

Post back any errors between code tags, please (see the link in my signature).

---

### Post by ioujojo on 2016-08-03
Apparently i'm clueless so I do not know if I am doing any of that right but after login it asks me for a password.
And do I put all these codes or one of them? Please forgive my questions :confused:

I should mention that at the login screen I couldn't go with Ctrl+Alt+F1 but with Fn+Alt+F1.And I pressed it by accident trying to put it.

```

[ATTACH=CONFIG]270547[/ATTACH]
```

---

### Post by grahammechanical on 2016-08-03
You are at a Linux command line. Enter your normal user name. You will be asked to enter your password. Enter your usual Ubuntu password. Now you can run those commands. And we run them one at a time. After the first command you will be asked to enter your password again but tnot for the next two passwords.

For commands like these we need administrator privileges. The "sudo" part of the command triggers the request for our user password and then once the password is entered we can work as administrator. After a period of time the administrator privileges will expire.

If we run those commands without "sudo" we will be told we do not have the authority to run those commands.

Regards

---

### Post by Bucky Ball on 2016-08-03
^^^
As above. Thanks.

---

### Post by ioujojo on 2016-08-03
Thank you both so much!!!!!!!
I did everything and that comes up:
```
[ATTACH=CONFIG]270553[/ATTACH]
```
Then I shut down and restart pc but same thing happens as in the first post!

---

### Post by ioujojo on 2016-08-03
Ok I'm officialy stupid.It was saying at the end to run 

```
sudo dpkg --configure -a
```

and I just saw it. I put it and now something is happening....I am waiting and I'll write when it stops!!!
Again many many thanks to both of you!!!!

---

### Post by ioujojo on 2016-08-03
Ok! Problem solved!
Pc restarted at its normal!!! You guys do a great job!
Thank you !!!!!!! :o

---

### Post by Bucky Ball on 2016-08-03
Excellent news and we try. ;) You can help others by marking the thread as solved. See Thread Tools> top right or link in my signature.

Enjoy (and keep those commands handy for a quick update/upgrade; I use Zim for that stuff, in the repositories :)).

---

