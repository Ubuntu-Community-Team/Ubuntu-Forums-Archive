---
title: "Sudoers List"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by JohnnyMc on 2013-03-27
I have the understanding that you should use a non-administrator account for normal use.  So I do that.  Problem is: sometimes I need to use 'sudo', but the non-administrator accout that I am using is not on the "sudoers list".  How do I add a user to the sudoers list?  Thank you, John

---

### Post by ManamiVixen on 2013-03-27
To answer that question is to talk to the administrator of your computer or to login to the admin account. There is no way for a non-sudo user to add himself without administrative privilges. Thats the whole point of a restricted account. To keep users who may not be up to the challenge of managing a computer from causing trouble or as part of a lockdown for security measures.

---

### Post by El Tito on 2013-03-27
The theory is [here]("http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line"), but I agree with @ManamiVixen; if you are not the admin of that computer, talk to him.

---

### Post by cariboo on 2013-03-28
You could always use su to switch to the users that does have sudo privileges:

```
su <sudo-user>
```

where <sudo-user> = the system administrator, and of course you have to know the administrator password, then use sudo to run the command you need. This only works in a terminal btw.

---

### Post by JohnnyMc on 2013-03-28
ManamiVixen and El Tito, sorry, I did not make my post that clear: I am the administrator of the computer, but use a non-admin user account for normal use as I believe that is recommended practice.

cariboo907, thank you.  I did manage to do that and accomplished what I had set out to do, but am still wondering how to add the non-admin user to the "sudoers list" ( it would eliminate a step ).

BTW: When I get the message that I am not on the list, the message goes on to say that the incident will be reported.  To whom is it being reported? and how? e-mail, log file?

Thanks again for the help!

---

### Post by nothingspecial on 2013-03-28
Well if you are the administrator you may as well use the administrator account. There's nothing wrong with this. It's the root account it's not advisable to run as. An administrator account uses sudo to _temporarily_ elevate to root privaledges but just as a normal user the rest of the time.

---

### Post by schragge on 2013-03-28
By adding non-admin users to the sudo group you will turn them into admin users. The only difference between admin and non-admin accounts on default Ubuntu installation is their (in)ability to use sudo. Sure, you can add a non-admin user to the sudo group,  but then there's no point in using yet another account. The situation when more than one account are members of sudo group usually only occurs when the system is administered by several people, each of them working under their own account.

 That said you can define some fine-grained sudo policy by creating custom rules in */etc/sudoers* for different users/groups, but I guess this goes beyond the scope of your question.

---

### Post by JohnnyMc on 2013-03-28
Thank you, nothingspecial and schragge for clearing that up for me! Makes things a little easier!

---

### Post by Ghost_Mazal on 2013-03-29
To easily add your account to the sudo group log in with the account that has sudo priviliges and execute the following in terminal:

> sudo addgroup username sudo

You will be prompted for the password of the administrator account.

And replace username with the name of your account that you use.
I always have a backup sudo user so that if something goes wrong on my account I have a second one that can execute sudo command to fix my main account.

---

### Post by Cheesemill on 2013-03-29
> **JohnnyMc said:**
> BTW: When I get the message that I am not on the list, the message goes on to say that the incident will be reported.  To whom is it being reported? and how? e-mail, log file?

[http://xkcd.com/838/](http://xkcd.com/838/)

---

### Post by JohnnyMc on 2013-03-30
That's funny, Cheesemill.

---

