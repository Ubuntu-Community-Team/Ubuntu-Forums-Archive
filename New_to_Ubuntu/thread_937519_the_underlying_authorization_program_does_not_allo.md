---
title: "the underlying authorization program does not allow you to run this program"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by pspsampsp on 2008-10-03
ok so my problem is that i want to run the package manager and add/remove on my account in xubuntu. so i click on package manager and it asks me to enter my password to perform administrative tasks so i enter the root password and i get error "the underlying authorization program (sudo) does not allow you to run this program" what is the problem? can someone please help an ubuntu noob fix this.

ps. I am using the xfce desktop enviroment

I solved it by about an hour of googeling lol

i had to edit the sudoers file and add my name to the list using the visudo command. i added: "user   ALL = (ALL)    ALL"
thanks to everyone who tried to help me 
                                            Sam

---

### Post by cariboo on 2008-10-04
You just have to enter the password you created when you setup your distribution. Root is disabled in all ubuntu distributions. Have a look at this page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Jim

---

### Post by jerome1232 on 2008-10-04
Sounds like this user isn't in the admin group. Can you post the output of the command groups? And by the way it's asking for your users password, there is no root password in Ubuntu, that account is disabled.
```
groups
```

Is this your first user, the one you created when you first installed the os?

If you want this user to have admin privilages, you'll need to add the user to the admin group, either from your main account or by booting into a recovery console and running

```
adduser [usernamehere] admin
```

---

### Post by pspsampsp on 2008-10-04
the results for the groups command are:
sam adm dialout cdrom floppy audio dip video plugdev fuse lpadmin

i made my self admin but that didnt work. Ill attach a picture of the error message

---

### Post by jerome1232 on 2008-10-04
So when you type groups, admin is listed now?

You do have to logout then log back in for the new group to take affect.

---

### Post by sloggerkhan on 2008-10-04
and if you don't have admin powers to give yourself admin powers, do it from the root recovery console when you boot.

---

### Post by pspsampsp on 2008-10-04
ok the funny thing is i can use the su command in terminal to login as root it works but not for package manager or any other gui apps oh yea and i restarted my pc after i made myself admin

---

### Post by jerome1232 on 2008-10-04
So I take it you actually enabled the root account? Unfortunatly that's not a supported mode under Ubuntu, it's disabled by default for security reasons. sudo should still be working as normal though, did you make adjustments to the sudo program as well? You might want to have a look at that link that was given earlier.

---

### Post by pspsampsp on 2008-10-04
no i have to still type a password to do administrative tasks and stuff so its not a security risk and i wont accidently mess things up i think it was to the same effect as that link cariboo907 provided but at the time i didnt really understand how to do that as i have only been using ubuntu for 1 day now. thanks for all your help every one

---

