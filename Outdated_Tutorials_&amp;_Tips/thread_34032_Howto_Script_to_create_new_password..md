---
title: "Howto: Script to create new password."
date: 2005-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-05-13
This was originally posted by

[Sam](http://www.ubuntuforums.org/member.php?u=8058):
I made it adhear to the rules of the thread.


Just make a little script:

```
$ sudo gedit /usr/bin/change_password
```

Put these lines:

```
#! /bin/sh
passwd
echo -e \\nPress Enter to exit
read
```

Make this executable:

```
$ sudo chmod +x /usr/bin/change_password
```

Create a new launcher on a panel or a menu entry (use [smeg](http://ubuntuforums.org/showthread.php?t=29732)). Don't forget to tell the launcher to run in terminal.

---

### Post by Sam on 2005-05-13
Woot! Thank you to post it. :wink:

---

### Post by poofyhairguy on 2005-05-13
Its a good howto.

---

### Post by mrshark on 2005-05-14
[QUOTE=poofyhairguy]Its a good howto.[/QUOTE]
 [-X 
it lacks the way to move and exit from vi (a big difficulty for new users...)

once in vi (or vim), press "i" (without quotes) to start writing, and when finished press:
```
<ESC>
:
wq
```
or
```
<ESC>
ZZ
```
it's best using gedit, as all the other scripts on this forum... BTW, your contribute may be useful.

---

### Post by crazybill on 2005-05-15
True, but I think the easiest way to change a password is just to enter the terminal and 

```
**#passwd username**
```

(where username is the username that you want to change.)
Then you simple enter the new password twice

_EXAMPLE:_
```

[B]root@ubuntu4:/home/teacher # passwd crazybill
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully.[/B]

```

Note: the password does not show on the terminal when you type it.

---

### Post by mrbass on 2005-05-15
When choosing a new password don't forget to use Secure Password Generator (firefox extension) [http://jgillick.nettripper.com/](http://jgillick.nettripper.com/)

oops that homepage got wiped...looks like roundtwo bought them out...hope it's still free
[http://www.roundtwo.com/product/securepassword](http://www.roundtwo.com/product/securepassword)

---

