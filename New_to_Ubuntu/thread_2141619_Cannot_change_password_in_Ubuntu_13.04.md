---
title: "Cannot change password in Ubuntu 13.04"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by Yash Pal on 2013-05-03
I installed Ubuntu 13.04 on a laptop - Dell Inspiron-M5010- dual booting with Windows7. 

Ubuntu appears to be working fine. However, I had to change the password for some reason but it won't change. The output of the terminal is:

   [FONT=courier new][COLOR=#800080][SIZE=2]yashpal@yashpal-Inspiron-M5010:~$ sudo passwd[/SIZE]
[/COLOR][/FONT]
[FONT=courier new][COLOR=#800080][SIZE=2][sudo] password for yashpal: [/SIZE] [/COLOR]
[/FONT]
[FONT=courier new][COLOR=#800080][SIZE=2]Enter new UNIX password: [/SIZE] [/COLOR][/FONT]
[FONT=courier new][COLOR=#800080][SIZE=2]Retype new UNIX password: [/SIZE] [/COLOR][/FONT]
[FONT=courier new][COLOR=#800080][SIZE=2]passwd: password updated successfully[/SIZE][/COLOR][/FONT]

[FONT=courier new][COLOR=#800080][SIZE=2]yashpal@yashpal-Inspiron-M5010:~$ 

[/SIZE][/COLOR][SIZE=2]but the password does not change[/SIZE][COLOR=#800080][SIZE=2]

[/SIZE][/COLOR][FONT=arial][SIZE=2]I tried to change it 3 times, 2nd time after "sudo apt-get update", to no effect.

Could anyone help me?[/SIZE][/FONT][COLOR=#800080][SIZE=2]
[/SIZE] [/COLOR][/FONT]

---

### Post by lovebluesky2009 on 2013-05-03
maybe
```
sudo passwd [FONT=courier new][COLOR=#800080][SIZE=2]yashpal[/SIZE][/COLOR][/FONT]
```
is helpful

---

### Post by Cheesemill on 2013-05-03
By using sudo you have changed roots password which is usually disabled, not your own.

To change your users password you just need to do...
```
passwd
```

---

### Post by PowerBarry43 on 2013-05-03
Hi there

either passwd or sudo passwd username will work.

passwd is you choosing to change your password and will require you to enter your current one whereas sudo passwd username is a forced password change allowing you to change any local user password without knowing the current one.

Hope this helps!

Barry

---

### Post by slickymaster on 2013-05-03
> **PowerBarry43 said:**
> Hi there

either passwd or sudo passwd username will work.

passwd is you choosing to change your password and will require you to enter your current one whereas sudo passwd username is a forced password change allowing you to change any local user password without knowing the current one.

Hope this helps!

Barry

See Cheesemill's post.

**sudo** executes commands as root, so running ```
sudo passwd
``` you will be resetting the actual root's password. Using the ```
passwd
``` command changes the password _of the current logged-in user_.
If you want to change password for another Ubuntu user, then you'll have to use sudo, because you'll be changing the password of a non logged-in user and you'll need to have the privileges as super user to do so:
```
sudo passwd john_doe
```

---

### Post by Yash Pal on 2013-05-03
[COLOR=#000000][FONT=DejaVu Sans][SIZE=2]Thanks to lovebluesky2009, Cheesemill, PowerBarry43 &slickymaster for [/SIZE][/FONT][/COLOR][FONT=DejaVu Sans][SIZE=2]help and for explaining the nuances of the command.[/SIZE][/FONT]

 &#8220;[FONT=DejaVu Sans][SIZE=2][FONT=DejaVu Sans]sudo passwd yashpal&#8221; [/FONT][FONT=DejaVu Sans]did the trick.[/FONT][/SIZE][/FONT] 
 
 [FONT=DejaVu Sans][SIZE=2][FONT=DejaVu Sans]solved[/FONT][/SIZE][/FONT]

---

### Post by slickymaster on 2013-05-03
> **Yash Pal said:**
> [COLOR=#000000][FONT=DejaVu Sans][SIZE=2]Thanks to lovebluesky2009, Cheesemill, PowerBarry43 &slickymaster for [/SIZE][/FONT][/COLOR][FONT=DejaVu Sans][SIZE=2]help and for explaining the nuances of the command.[/SIZE][/FONT]

 “[FONT=DejaVu Sans][SIZE=2][FONT=DejaVu Sans]sudo passwd yashpal” [/FONT][FONT=DejaVu Sans]did the trick.[/FONT][/SIZE][/FONT] 
 
 [FONT=DejaVu Sans][SIZE=2][FONT=DejaVu Sans]solved[/FONT][/SIZE][/FONT]

Don't have to thank. People here are always willing and glad to help.

_Don't post 'solved' on a thread, as it will not mark it as solved_. See my signature as how to mark a thread as solved.

---

### Post by Onesimus on 2013-05-03
I have found that I am unable to change my password using the System Settings->User Accounts.  So it has been useful to find a different way to change the password.  Many thanks

---

