---
title: "Which user is administrator? how to delete users?"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by Bokaj on 2013-04-18
Hi

I am trying to install a software (Easyprot") on a ThinkStation Lenovo with Ubuntu.
I have managed to get the program running a few times but now I have some problems and cannot get the program up and running.

I am not sure what has gone wrong - for example there seems to be some problems with "exporting" a "root" to the baschr file and also sometimes I get the error message :  " "user" is not in the sudoers file. This incident will be reported" 
The installation procedure is described here: [http://easyprot.unige.ch/easyprot_installation](http://easyprot.unige.ch/easyprot_installation)

Since I have had the software running successfully I think the best thing is to erase everything and re-create a new user and re-install the program?
I have only had Ubuntu for a few weeks so I dont have any files I need to save,.
Question: Can I erase all users and all files (not Ubuntu and standard programs) and start over from the beginning?

Thank you!

---

### Post by Bokaj on 2013-04-18
And another question: how do I find out which of the users is the administrator...?

---

### Post by Bokaj on 2013-04-18
... and when locked in as administrator how do I delete other user accounts?

---

### Post by cortman on 2013-04-18
Nowhere in the instructions do I see anything about exporting a root to bashrc. It talks about exporting environment variables and then sourcing .bashrc, neither of which should be done as root, but as the easyprot user.  Did you have trouble adding the user easyprot? Please specify.

To answer your second question, a quick way is just to run this command as the user in question:

```
sudo -v
```

It will either work (and update the user's credentials) or else give a message saying that $user is not allowed to use sudo.

You can delete other accounts with the command userdel.

```
userdel user_name
```

Use it with -r to also remove all the user's files, including home directory.

```
userdel -r user_name
```

PS- It's better to just edit your original post with more questions, than to post replies to it.

Good luck!

---

### Post by Abhilashjoy on 2013-04-18
hi

Please reffer [http://askubuntu.com/questions/156409/how-do-i-add-or-delete-user-accounts](http://askubuntu.com/questions/156409/how-do-i-add-or-delete-user-accounts)

---

### Post by Bokaj on 2013-04-18
> **cortman said:**
> Nowhere in the instructions do I see anything about exporting a root to bashrc. It talks about exporting environment variables and then sourcing .bashrc, neither of which should be done as root, but as the easyprot user.  Did you have trouble adding the user easyprot? Please specify.

To answer your second question, a quick way is just to run this command as the user in question:

```
sudo -v
```

It will either work (and update the user's credentials) or else give a message saying that $user is not allowed to use sudo.

You can delete other accounts with the command userdel.

```
userdel user_name
```

Use it with -r to also remove all the user's files, including home directory.

```
userdel -r user_name
```

PS- It's better to just edit your original post with more questions, than to post replies to it.

Good luck!
Thank you!
The title of my thread is very misleading. Sorry (too late to change now right?)

One more question. I have created several users that appear when I start up the PC. In addition, I have created users using the terminal - these I can use by using the command "SU User". What are the difference between these two types of user accounts? Or are they the same?

---

### Post by philinux on 2013-04-18
On you first post.

click edit post then go advanced then change the title .

---

### Post by cortman on 2013-04-18
> **Bokaj said:**
> Thank you!
The title of my thread is very misleading. Sorry (too late to change now right?)

One more question. I have created several users that appear when I start up the PC. In addition, I have created users using the terminal - these I can use by using the command "SU User". What are the difference between these two types of user accounts? Or are they the same?

Glad to be of help. :)
There shouldn't be any difference between those. You're logging in to that account in the terminal when you use su (switch user).

---

### Post by Bokaj on 2013-04-19
Thanks again.
One minor complaint: I find that if I switch between users too frequently, or too many times, when I use the mouse (not the terminal) then Ubuntu often malfunctions - the graphics become a mess and I have to re-start.
But thanks again. I will probably be back with many more Ubuntu questions in the future ;-)

---

### Post by cortman on 2013-04-19
Not sure what the cause of the graphics problem is. You may need different drivers- if you want, feel free to start another thread on it.
If the issue is resolved go ahead and edit the thread title and add [SOLVED] to the beginning.
Good luck!

---

