---
title: "Having problems resetting password and creating new password"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by chazbaruela on 2012-01-20
Hi I have been having trouble resetting my password. I have tried using the passwd command at the root recovery mode screen but it gives me an authentication token manipulation error. It seems that my user password was somehow deleted without my knowledge. I don't know what happened because my user password used to work when I was updating the computer but now it doesn't work and doesn't show up in user accounts. I have posted some pictures of what i see when i try to create a new password in user accounts. Can someone please help me figure out what the problem is?

---

### Post by grahammechanical on 2012-01-20
First, you need to unlock the utility. Click on the button that says Unlock and type in your password. This security stops anyone who is not an administrator from changing passwords and deleting user accounts.

Second, when you now click on the password field/panel the dialog that appears (changing password for ) will have at the top a panel called Action. From the drop-down menu you can select (a) Set a password now. (b) Log in without a password. (c) Disable this account.

The Changing password dialog that you are seeing is an inactive panel because you have not unlocked the User Accounts utility.

You see, in Ubuntu even though we are set up as an administrator we do not need administrator privileges all the time. So, we are not given them. We are working as a standard user until such a time as we do something that requires administrator privileges. Then we are asked to authenticate and for the purpose of that particular task we are effectively the administrator. Once the task is completed we revert back to being a standard user.

In this way unauthorised people who get access to the machine while we are logged in cannot make unauthorised changes to the system. Such as deleting passwords. Without the administrator password they could not unlock the User Accounts utility. You will notice that if you leave this utility open it will lock itself. It is on a timer.

Regards.

---

### Post by chazbaruela on 2012-01-23
Thanks but that is one of the problems that I am having. I did try to do the unlock button but since my password doesn't work anymore because of its changing or being deleted on its own I can't unlock anything. If you can think of anything else to help I would appreciate it.

---

### Post by chazbaruela on 2012-01-24
Oh, it works now.  My password is working again for some reason. Thanks for your help,I really appreciate it.

---

