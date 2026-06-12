---
title: "im locked out as administrator"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by mhrpinca on 2008-05-04
im locked out of my system as administrator. im new and of course it was accidental heres what i did system, administrator,users and groups,properties,user privileges,and then i unticked administer the system oooooops. now i cant sudo any thing i cant update i cant run synaptic basically i cant admin my system so what do i do to fix it??????? telling me how dumb it was to do that wont fix it so please refrain from heckling me. thanks

---

### Post by aysiu on 2008-05-04
This will help you:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by PinkFloyd102489 on 2008-05-04
Easier way to do it is this:

1. Boot into the Recovery Console to gain root access.
2. Type "startx" with no quotes
3. This will start up GDM so you can point and click.
4. It should log straight into the desktop so go to the Users and Groups window and edit the permissions for your username.
5. You can either kill off GDM, su to your username, and startx again or reboot and choose the normal boot option.

Hope it helps.

---

### Post by zvacet on 2008-05-04
In recovery mode 

```
adduser username admin
```

---

### Post by davarino on 2008-05-04
Aysiu's answer is quite comprehensive and will give you a good education in what is going wrong. Aysiu is one of the most observant and helpful thinkers we have in Ubuntu.

It would be best for you to follow his advice and check both of the critical files, even though the problem is probably in the /etc/group file.

By the way, he gives a very simple one-line command line fix just before the end of the article: a fix that will work in the vast majority of lock-out cases.

---

### Post by mhrpinca on 2008-05-04
yep none of it is working did i mention im using ubuntu 8.04
and when i run recovery i get a screen called recovery menu. so
i tried the option to drop to root shell prompt it didnt ask for a password and i tried the link [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
i was denied and had to type sudo im pretty new so ive tried a few diferant sugestions i may be making it worse startx warned me that i was runing th e session as a privilegd user  and when i hit continue it droped back down to acomand prompt so????? i duno

---

### Post by mhrpinca on 2008-05-04
thanks Aysiu and pinkfloyd but no luck as i said im using 8.04
on my lap top as well as both desk tops can i copy the file from one of those machines and replace the file im trying to fix on my laptop????? and if so how?

---

### Post by forumache on 2008-05-04
OK, let's start it step by step.

You said that you entered in Recovery Mode, and you are root now.

1. type what zvacet said: adduser yourusernamehere admin
2. enter into a new console (Ctrl+F2) and try to log on as you
3. now do something like sudo touch /onefile (should ask for your password and then create onefile in /) Be sure that you tried this as your username, we want to try if the username can sudo. If you try it as root, it will succeed, but it is irrelevant for our test
4. if step 3 is a success, you are not locked anymore

Try, and if problems arise try to be as descriptive as possible.

Good luck,
Dan.

---

### Post by aysiu on 2008-05-04
Yeah, I think we need to tackle the problems one at a time.

First of all, does recovery mode work? In other words, when you select the recovery mode option from the boot menu, are you taken to a prompt that looks like ```
root@ubuntu:~$
```

---

### Post by mhrpinca on 2008-05-04
here is what solved the problem Tiede gave me this in a similar post: "gpasswd -a username groupname" my name in place of user name and admin in place of groupname it added me back to the addmin group worked yay..... thanks guys

---

