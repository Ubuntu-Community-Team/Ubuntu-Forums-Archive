---
title: "Unable to login in 11.10"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by abhijitsharma806 on 2012-01-09
Hi Friends

I create one user and i remove the password,

but when i trying to login in graphically it asking for password. But it is not asking password

in text mode. I create 2 users in different method one is graphically another is text based.

using following command.

#useradd -d /home/scan -m scan
#passwd -d scan
# chage  -l scan
Last password change                    : Jan 09, 2012
Password expires                    : never
Password inactive                    : never
Account expires                        : never
Minimum number of days between password change        : 0
Maximum number of days between password change        : 99999
Number of days of warning before password expires    : 7

another guest user is in graphically.

can anyone tell me what is the error.

Thanks
ABHIJIT.

---

### Post by lechien73 on 2012-01-09
Hello & welcome to the forums,

Try going to the Dash menu (the Ubuntu icon on the sidebar).

Type **Users and Groups** and select the applet

Select the user you want to change and, next to the password field, click **Change**

Check the box that says **Do not ask for a password on login**

You can also change automatic login preferences from the user accounts applet, which is accessed by clicking on your username at the top right of the screen, and choosing **User Accounts**

---

### Post by Frogs Hair on 2012-01-09
In case you would need to reset a password . [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by grahammechanical on 2012-01-09
Please explain more fully what you mean by "text mode?" Are you referring to the terminal?

It does not matter how you create a user account. The information is stored in the same file or document. The graphical user interface is doing the same thing as the commands that you used.

We do not need to log in to a terminal and there are commands that we can use without needing a password word but there are other commands that will not work unless we put the word sudo in front of the command and then put in our password when we are asked to put it in.

The login screen will always ask for a password. If you have set a user to log in without a password all that user needs to do is click on their user name and press enter to log in. We always get a log in screen if there are more than one user. We also get a log in screen if there is only one user. But if we set that one user to log in automatically then the desktop will load without going to a log in screen.

Regards.

---

