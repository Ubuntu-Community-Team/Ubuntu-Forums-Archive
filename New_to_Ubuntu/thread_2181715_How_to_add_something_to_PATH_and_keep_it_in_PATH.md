---
title: "How to add something to PATH and keep it in PATH"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by adam20 on 2013-10-18
So the code I use is

PATH=$PATH: path/to/program   (< no space, though...stupid emoticons). 

I then echo $PATH and see my directory there, but when I exit the existing terminal and start it back up -it's removed from PATH.

---

### Post by tgalati4 on 2013-10-18
There are several places that you can put it:

/etc/profile
.profile
.bash_login
(I'm sure that I am missing a few!)

Each has a slightly different use case.

Some light reading:

[http://askubuntu.com/questions/3744/how-do-i-modify-my-path-so-that-the-changes-are-available-in-every-terminal-sess](http://askubuntu.com/questions/3744/how-do-i-modify-my-path-so-that-the-changes-are-available-in-every-terminal-sess)
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
[http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path](http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path)

What you do in a terminal, stays in the terminal!  If you started any jobs or scripts in a terminal and kill the terminal, then those jobs will die as well.  This happens with any environment variables that you define in a terminal session as well. (Something about Process Locality and Inheritance.)

---

### Post by adam20 on 2013-10-18
so then why do usr/bin and /bin always remain in PATH?  Would putting them in these folders keep the program in PATH?

---

### Post by JKyleOKC on 2013-10-18
They are set up in the original copy of PATH when the user profile is initiallu created, and then preserved by the "$PATH:" part of your command to add a new directory. You can put your add-to-path command in the hidden file "$HOME/.profile" to make sure it's run every time you log in.

---

### Post by Dennis N on 2013-10-18
> **adam20 said:**
> so then why do usr/bin and /bin always remain in PATH?  Would putting them in these folders keep the program in PATH?

If you create the directory **[FONT=Courier New]~/bin[/FONT]** it is added automatically to your $PATH by the system. So you can put scripts in there for use by bash, and you will be the owner of those files.

---

