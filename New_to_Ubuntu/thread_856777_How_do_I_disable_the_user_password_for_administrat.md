---
title: "How do I disable the user password for administrative tasks?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2008-07-11
Hello friends, trying to set up Ubuntu on this terminal and I need to know how to make the user password saved. I need to to install updates without requiring a password. 

While I know this hurts system security, if there is a new password people need to learn, it will be quickly denied. I need something that just works and blows XP out of the water, which it will once I am through configuring it.

EDIT: I'm at a loss here...maybe if I were to say I had a sound/flash/audio problem I would get attention :)

---

### Post by pHreaksYcle on 2008-07-11
*I posted the following a while ago but I think I used a bad title so here's the dupe:*

Hello friends, trying to set up Ubuntu on this terminal and I need to know how to make the user password saved. I need to to install updates without requiring a password.

While I know this hurts system security, if there is a new password people need to learn, it will be quickly denied. I need something that just works and blows XP out of the water, which it will once I am through configuring it.

---

### Post by lisati on 2008-07-11
Is that wise? This isn't Windows.......

---

### Post by LowSky on 2008-07-11
Well you have two problems, the first is you will make the system a security risk and could break the system, might I suggest that the computer doesn't update at all just turn them off entirely. Second My suggestion might work. Never tried it

[http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/)

---

### Post by LowSky on 2008-07-11
take a look here too

[http://ubuntuforums.org/showthread.php?t=167322](http://ubuntuforums.org/showthread.php?t=167322)

---

### Post by Bakon Jarser on 2008-07-11
I'm not sure if this will work, I haven't tried it.  System > Administration > Software Sources.  Click the updates tab at the top and select install updates without confirmation.

---

### Post by aysiu on 2008-07-11
> **Bakon Jarser said:**
> I'm not sure if this will work, I haven't tried it.  System > Administration > Software Sources.  Click the updates tab at the top and select install updates without confirmation.
That seems probably the best solution for this situation.

---

### Post by pHreaksYcle on 2008-07-11
EDIT: Now that I think about it, this will only make it come up automatically won't it? It will still ask for admin confirmation :(

I'm going with this solution, I appreciate it. Thank you! Linux will be run in yet another business environment.

Quote:
Originally Posted by Bakon Jarser View Post
I'm not sure if this will work, I haven't tried it. System > Administration > Software Sources. Click the updates tab at the top and select install updates without confirmation.
That seems probably the best solution for this situation.

---

### Post by aysiu on 2008-07-11
The other thing is that the way Ubuntu is set up with *sudo*, it isn't really one *more* password to install updates. It's kind of only one password. If you don't trust the users to all be in the *admin* group, you can edit the /etc/sudoers file to allow them privileges (and without a password) to Update Manager only.

Or... you can also set up a cron job at the root level to run a command like ```
sudo apt-get update && sudo apt-get dist-upgrade -y
``` at a certain time each day, regardless of what user is logged in.

---

### Post by pHreaksYcle on 2008-07-11
FYI there is one and only one user account in place on this system. It should be in the admin group already, being the only user right? (Maybe not haha)

---

### Post by aysiu on 2008-07-11
> **pHreaksYcle said:**
> FYI there is one and only one user account in place on this system. It should be in the admin group already, being the only user right? (Maybe not haha)
Oh, I thought based on what you said earlier (*While I know this hurts system security, if there is a new password people need to learn, it will be quickly denied.*) that this was for multiple users, including some folks who may not want to learn a new password.

If you have only one user, that user is in the *admin* group and can install updates with her or his own password, so there is no "new password... to learn."

---

### Post by pHreaksYcle on 2008-07-11
I must really blow at explaining things :P

What I am doing is installing fresh, as a dual-boot with XP, hoping to get it accepted full time. While this is going to be a pain in the *** for me, I see it as completely worth it. As of now, **there is no password on the XP side for anything. I need it like this on Ubuntu.** Thanks for your help thus far.

---

