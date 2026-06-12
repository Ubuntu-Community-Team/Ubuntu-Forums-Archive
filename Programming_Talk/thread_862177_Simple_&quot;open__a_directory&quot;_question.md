---
title: "Simple &quot;open  a directory&quot; question"
date: 2008-07-17
forum: Programming Talk
---

### Post by blooddrunk on 2008-07-17
As you've probably read I am developing a PAM application. The only thing that is left to do is make it open the home directory of the user. The user is authenticated, the session is started, how do I make the application open in a new terminal or GUI the home directory of the user that is authenticated?
10x

---

### Post by dwhitney67 on 2008-07-17
Without more details, your question might prove difficult for anyone to answer properly.

Once the user has logged in, you can insert any application you want to start up in the user's ~/.profile file.  On some *nix systems, the file ~/.bash_profile can also be used.

If you want to start up applications for all users, then add statements to /etc/profile or add shell scripts to /etc/profile.d.

The command to launch a Gnome terminal is 'gnome-terminal'.

---

### Post by blooddrunk on 2008-07-17
The problem is that when you launch any command, it opens it as the logged user,not the authenticated one. The application is started by the user, then he types in his username(which can be different) and username, this is checked on a server and if everything is correct, that user is authenticated. Once his session starts, he should be able to access his home directory as it is in passwd.

For example:
You start you log in as John. Then you start the application and write your (office)username: Peter. When you are authenticated, it should open Peter's home directory: /home/peter (for example)

---

### Post by dwhitney67 on 2008-07-17
Try something like:

```
gnome-terminal -e "su - peter" &
```

Of course, this will prompt the user for peter's password.

---

