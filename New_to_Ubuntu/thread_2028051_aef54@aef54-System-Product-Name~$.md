---
title: "aef54@aef54-System-Product-Name:~$"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by aef54 on 2012-07-17
When I open the terminal, the line where I can type my commands says:

aef54@aef54-System-Product-Name:~$

From what I've learned:
-aef54@aef54 are the name of the user and the computer, 
 ~ means I'm in the home directory and 
$ means I'm not superuser (otherwise it would be #)

However, what does this *-System-Product-Name* mean? I see that on [other websites](http://www.linuxcommand.org/index.php) people do not have such a long text when they open the terminal.

How can I edit it so that it just says:
*me@mycomp:~$ *
or something like that?

---

### Post by glennric on 2012-07-17
"aef54" is your user name.
"aef54-System-Product-Name" is your computer's hostname.
The "$" doesn't actually mean what you claim.  The "~" is your home directory.  The "$" is simply a character telling you that is where the end of the prompt is, and what you type will come after that.  What is displayed in the prompt can be modified by changed the PS1 variable in your .bashrc file.

In any case it seems that when you installed Ubuntu you selected "aef54" as your user name, and "aef54-System-Product-Name" as your hostname.

---

### Post by QIII on 2012-07-17
$ means that you are signed in as your user name and your privileges are such that you need to use sudo or gksudo to temporarily elevate privileges for commands that require elevated privileges.

# indicates root privileges for the session, which is best to avoid as a beginner.

You need to change your computer's name.  What you have is probably what it defaulted to when you were installing.

You can change the name as described in the following link, but there is an error:
[B]
Replace instances of "sudo gedit" with "gksudo gedit".[/B]  

See this [wiki:]("https://help.ubuntu.com/community/RootSudo")

"You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo  sets HOME=~root, and copies .Xauthority to a tmp directory.  This  prevents files in your home directory becoming owned by Root.  (AFAICT,  this is all that's special about the environment of the started process  with gksudo vs. sudo). "

Just get in the habit of using gksudo with graphical applications for everything.

In the following link, look at the section titled "Changing Your Host Name" and disregard the rest.  And remember to use gksudo.

[http://www.liberiangeek.net/2012/04/common-tasks-to-perform-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/common-tasks-to-perform-in-ubuntu-12-04-precise-pangolin/)

You will need to reboot for this to take effect.

---

### Post by sujitrjadhav on 2012-07-17
you may change your hostname using command 

```
sudo hostname *newhostname*

```

repalce *newhostname* with whatever you like.

---

### Post by glennric on 2012-07-17
> **QIII said:**
> $ means your privileges are not elevated to superuser.

# indicates elevated privileges.


Technically that is not true.  Technically a prompt ending with a "$" or with a "#" simply means that is how the prompt is set up for the user you are logged in as.  If you have modified your users prompt setting (by changing the PS1 variable in .bashrc) then you may see something else.  The default .bashrc terminates the prompt with a "$", and the default .bashrc for the root user terminates the prompt with a "#".  However, both can be changed.

---

### Post by QIII on 2012-07-17
Except for the fact that I carelessly used "superuser" rather than "root", technically it is true from the perspective of a new user until he makes the change - he'll see the default.  You used the word.

Assuming he is running with the defaults, that is what he will see.

You have presented a change to the default, which he is unlikely to have done.  Many defaults can be changed.

If he uses "su" to "become root", he'll get the # by default.  Not something I would recommend as a beginner.

By way of clarity, I have made the following change:

"$ means that you are signed in as your user name and your privileges are such  that you need to use sudo or gksudo to temporarily elevate privileges  for commands that require elevated privileges.
# indicates root privileges for the session, which is best to avoid as a beginner."

I think this provides an answer understandable to a new user without technical jargon.

---

### Post by anewguy on 2012-07-18
+1 - this is also true in some other Linux distros.  $ the default (which I might add most people don't change), # when you currently have root priviledges.  Heck, just get on your android device, open the terminal - default $ - type su - you'll get # meaning you have root priviledges (basically everything).

---

### Post by aef54 on 2012-07-18
> **sujitrjadhav said:**
> you may change your hostname using command 

```
sudo hostname *newhostname*

```repalce *newhostname* with whatever you like.
That solved it :)

Thanks to all of you for posting.

---

