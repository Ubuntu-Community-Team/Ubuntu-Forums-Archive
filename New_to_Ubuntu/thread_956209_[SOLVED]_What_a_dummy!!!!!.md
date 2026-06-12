---
title: "[SOLVED] What a dummy!!!!!"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by donaldshelton on 2008-10-23
[SIZE=6][SIZE=4]I was playing around, went to users and groups.  I went to my user profile.  For fun I went to password generator to see what kinds of passwords would be generated.  I evidently chose to save the one generated as my password without realizing it.  

I of course didn't write it down.  I can access the computer using anotheer user's account, but it doesn't have administrator privileges.  

Is it possible to get in to my account and get the password?

Don
[/SIZE]    
[/SIZE]

---

### Post by Sef on 2008-10-23
Read [Psychocats Reset Password]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by OutOfReach on 2008-10-23
Yes there is.
Boot up into thte Ubuntu Recovery Mode (Should be an option in the bootloader).
The when it is done loading and you get presented with a screen, choose 'Drop to Root Shell' (Or something along the lines of that). Then you'll be dropped into a root command line, if you know your username type in:
```

passwd YOUR_USER_NAME_HERE
```
Replace YOUR_USER_NAME_HERE with your username, of course.
It will ask you for a new UNIX password, type it in, (i think it asks you to confirm too), then do:
```
reboot
```
and go into normal Ubuntu this time and see if you can log in.

If you don't know your username you can try:
```

ls /home
```

---

