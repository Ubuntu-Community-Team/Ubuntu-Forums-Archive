---
title: "[SOLVED] old pc"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by DarinB on 2008-06-01
i have an old pc P3 over 500 ram running gutsy...
i want to give it to my ex girlfriend's son...
the root user and password are mine can i change them before i give the pc away????

---

### Post by JoshuaRL on 2008-06-01
Do you mean your sudo user, or did you enable login-as-root?

---

### Post by quelx on 2008-06-01
create a new user

**System** > **Administration** > **Users and Groups**

**Add User** and fill in the details, click the **User Privileges** tab and check **Administer the System**

Log out and back in as the new user 

Run **Users and Groups** again. This time delete your old user.

**ALT-F2** and type *gksudo nautilus* and browse to **/home/** and make sure your folder is gone (if not, delete it if you want)

---

### Post by Joeb454 on 2008-06-01
If you enabled a root password you can change it by running ```
sudo -i
passwd
<change your password>
exit
``` At least I think you can :)

---

### Post by iaculallad on 2008-06-01
Since you are running Gutsy, disregard the "Unlock" option as specified by quelx when Adding New User. "Unlock" is a new feature for Hardy.

---

### Post by spiderbatdad on 2008-06-01
There is a usermod command and you would need to change the id # to 1000 of the new user name as well:[http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)

Why not do a clean install? Just a suggestion.

---

### Post by DarinB on 2008-06-01
i am not sure how i am running any of my machines. 
all i do know is that when i installed it asks for name password etc.
then i never did anything else.
under users and groups it has my name and almost all user privileges are given then root and it has no privileges.
i use my login and password for sudo.
i think i need some kind of tutorial on this stuff.
so how do i change this old pc so the kid can have full privileges sudo login   etc. and not find out my passwords?

---

### Post by JoshuaRL on 2008-06-01
Probably the easiest would be a fresh install like spiderbatdad suggested.  But if not, then go into System->Administration->Users and Groups.  You will want to add another user, make them a sudo-user, and then delete your user account from the computer.  That would do it.

---

### Post by iaculallad on 2008-06-01
You can not see any privileges for root (All unchecked check box), but it is there. As a root, it can do all commands.

Here are some guides for sudo:

[http://www.sudo.ws/sudo/](http://www.sudo.ws/sudo/)

[http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html](http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html)

---

### Post by DarinB on 2008-06-01
thanks i have learned a ton in just a few minutes and  i think ubuntu rocks compared to users and groups in win 2k server and xp. if i got it right the initial user has full privileges using sudo. ANd root is disabled by default or just hidden? What is the root password by default do i have to set that? the other question i have is shouldn't the password for sudo be different than the login password by default???

---

### Post by JoshuaRL on 2008-06-01
No.  That's the idea behind sudo users, they can use root privilidges when needed.  But they also stay in a limited user account otherwise.  That is a lot safer than the typical setup with Windows.

And yes, logging in as root is disabled by default.  That is another security measure Ubuntu has.  No need to set a root password.

---

### Post by iaculallad on 2008-06-01
> **DarinB said:**
>  if i got it right the initial user has full privileges using sudo. ANd root is disabled by default or just hidden? What is the root password by default do i have to set that? the other question i have is shouldn't the password for sudo be different than the login password by default???

Yes, the initial user configured/added has a privileges using sudo (provided, the user inputs the correct password). Root actually is not disabled or hidden but Root is disabled to login using the Login Menu by default for security purpose. Root's password by default is "auto-assigned" upon installation so the initial user can change it afterwards. 
The password for sudo is the same as the login password.

---

### Post by DarinB on 2008-06-02
thanks everybody and i found a great 
A treatise on users and groups on line.

---

