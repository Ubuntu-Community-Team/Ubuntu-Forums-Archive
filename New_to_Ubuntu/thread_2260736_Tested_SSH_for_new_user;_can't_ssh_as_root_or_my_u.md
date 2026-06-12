---
title: "Tested SSH for new user; can't ssh as root or my user now"
date: 2015-01-14
forum: New to Ubuntu
---

### Post by Yosef_Karo on 2015-01-14
Tried searching forums and google because I know the answer must be simple.  On my new dedi, I created a user and added him to /etc/ssh/sshd_config  Then I exited out of ssh to test to make sure that he would be able to ssh in.  It worked!  Problem is, I can't ssh in with my user name nor as root anymore.  I know the answer is simple but it's hard to search for "ssh for new user, can't ssh in anymore".

I appreciate the help. :)

Oh, I just appended:
Port 1234
PermitRootLogin no
AllowUsers jim

to /etc/ssh/sshd_config and did sudo service ssh reload

---

### Post by Lars Noodén on 2015-01-14
If you add AllowUsers or AllowGroups to sshd_config then any user or group not on the list cannot log in.  Can you log in as jim and then "su -l" to your regular user?

---

### Post by Yosef_Karo on 2015-01-14
Yes, I did login as 'jim' and then change to my user, but I really don't want to have to do this each time that I ssh in; plus, I want to be sure that the other ssh user that I gave access to will also be able to login (ssh in).  I want to be able to ssh in again as 'root' and then su - myusername.  Ohhh, after I did the AllowUsers jim now only 'jim' can login?  I think I understand now what is wrong.  However, what, or how should I edit AllowUsers so that Jim, root, and myself can ssh in?  Or should I use something other than 'AllowUsers"

---

### Post by Lars Noodén on 2015-01-14
If you use AllowUsers in your configuration, then it has to list all the users allowed to log in.  If it is used, then any users that are not listed cannot log in.  If you do not have [AllowUsers, AllowGroups, DenyUsers, or DenyGroups](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) then any non-root user will be able to log in.  Only the presence of one or more of those configuration directives will change that.  I would only use them in an environment with a lot of users where some or most are not allowed to log in remotely.  sshd works fine without those.

---

