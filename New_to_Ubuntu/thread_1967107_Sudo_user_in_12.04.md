---
title: "Sudo user in 12.04"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Covalent Bond on 2012-04-27
I know this has been discussed in the past, but I remain uncertain exactly what to do.  I installed 12.04 and added an account as a standard user, but would like to be able to add or get software, however, I am unable to use the sudo command, and do not want to switch to the administrator user unless absolutely necessary.  Is there a simpe way for me to add my standard user to the sudoer list?  As an aside, I know just enough to be dangerous, so it is best to use the simplest method for me.
 
CB

---

### Post by jerome1232 on 2012-04-27
By adding your user to the sudoer's list, your user will effectively become an "administer" account. In Ubuntu, an administer account is simply one that can use sudo.

The difference is in Ubuntu, your not running with elevated rights all the time, only when you use sudo (or an app asks for your password) does your user get those elevated rights.

---

### Post by joetait on 2012-04-27
At the risk of almost repeating what Jerome has said, if you go to system settings -> user accounts and then change your user account from standard to administrator then you should be able to use sudo.

---

### Post by Covalent Bond on 2012-04-27
Thank you; I did not think the solution was so simple.  I did as recommended, and it worked fine.

CB

---

### Post by joetait on 2012-04-28
FYI you can use the tools at the top of the thread to mark it as solved, which is useful for other people to know it has been sorted.

---

### Post by grahammechanical on 2012-04-28
this link will explain why you are safe with Ubuntu even if you are logged in as administrator.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Basically, we are only administrator when we need to authenticate an action and we use our log in password to authenticate the action. Once the action has ended, we revert back to being a standard user.

We do not need to have an administrator account and a standard account, not in Ubuntu. The one account serves as both when it is needed.

Regards.

---

