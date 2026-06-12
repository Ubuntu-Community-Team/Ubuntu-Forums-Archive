---
title: "How to find UserName for current [Gnome] session?"
date: 2010-03-25
forum: Programming Talk
---

### Post by SteveDee on 2010-03-25
Consider this:-
If I run my program (myGambasApp) on Ubuntu on user "john" desktop session, I can use the Linux command "whoami" in myGambasApp to return the username for the current user (john).

If I launch myGambasApp using:-
 gksu myGambasApp
the command whoami (quite rightly) returns "root".

So my question is: how do I find the current Gnome session username when running myGambasApp with root privileges?

Clearly Gnome knows the answer, and I was hoping to find a file somewhere containing the current username.

---

### Post by cubeist on 2010-03-25
> **SteveDee said:**
> Consider this:-
If I run my program (myGambasApp) on Ubuntu on user "john" desktop session, I can use the Linux command "whoami" in myGambasApp to return the username for the current user (john).

If I launch myGambasApp using:-
 gksu myGambasApp
the command whoami (quite rightly) returns "root".

So my question is: how do I find the current Gnome session username when running myGambasApp with root privileges?

Clearly Gnome knows the answer, and I was hoping to find a file somewhere containing the current username.

First I would ask why you are running the program as root?  Most programs can be run in "user-space" and still accomplish root-type activities.

Anyway, the direct answer to your question is that there is no way to show which user is running the program, 'cause as far as the computer is concerned, root is running the program.

A (complex) work around may be to list all users on your system, but a simple solution is just run the program non-root.

---

### Post by SteveDee on 2010-03-25
Thanks for your reply cubeist.

My app changes file permissions, so I'm simply using Linux commands such as chown (e.g. Shell "chown " & UserName & FileName). Please advise if there is a better way to go.

I can use the Linux command "users" which works fine unless other users are also logged in (via switch user), then "users" returns all logged in users "helpfully" sorted in alpha order.

If I go direct to the file used by "users" (i.e. cat /var/log/wtmp) the last user name in this file seems to indicated the appropriate user for the active Gnome session.

There may be something easier to use in the /var/run/gdm directory, but so far I have not found it.

---

### Post by louis--taylor on 2010-03-25
Sorry if I have misinterpreted the question, but does:
```

import os
user = os.getlogin()
print user

```

work?

---

### Post by SteveDee on 2010-03-26
> **louis--taylor said:**
> Sorry if I have misinterpreted the question, but does:
```

import os
user = os.getlogin()
print user

```

work?

Thanks for your help.

I searched "python" AND "os.getlogon" via Ixquick and get the impression that this uses the same files that I have been looking at (i.e. utmp and wtmp).

At this site: [http://docs.python.org/library/os.html](http://docs.python.org/library/os.html) they say:-
 "For most purposes, it is more useful to use the environment variable LOGNAME to find out who the user is..."
So I think os.getlogon() may be a wrapper function for Linux command "logname".

I did try to use logname yesterday. Although it works directly in a terminal, when used in my Gambas code like this:-
```

EXEC ["logname"] TO strUser

```
nothing is returned. This could be a Gambas problem, but other related commands (e.g. users, whoami) do return data when used this way.

---

### Post by lavinog on 2010-03-26
It might be better to run the app as a user app, and let the application call commands that need root privileges with gksu.

I haven't looked much into it, but maybe policykit could be of some use:
[http://www.freedesktop.org/wiki/Software/PolicyKit](http://www.freedesktop.org/wiki/Software/PolicyKit)

---

### Post by akudewan on 2010-03-26
Hi,

As others have said, it may be better to run the program as a normal user, and use some workaround such as PolicyKit or perhaps simply creating a group that has the necessary privileges.

However, if you want to stick to your current method, I think you may be able to exploit the $DISPLAY environment variable. That's one thing the root user and the current user have in common.

So you could do something like this:
```
# dp=`echo $DISPLAY | cut -d '.' -f 1`
# actualusr=`who | grep $dp | cut -d ' ' -f 1 | tail -1`
```

I have used "cut" in the first statement so strip out the number after the dot (Eg: :0.0 becomes :0 ) I needed to do that in Archlinux, but it probably depends on how the system organizes the $DISPLAY variable.

Keep in mind that this is a very dirty way of doing things. Using some other workaround would be preferable.

Hope this helps.

---

### Post by cubeist on 2010-03-26
as lavinog mentioned, you can call specific root actions from a shell script with gksu or sudo.

One danger with running an entire program as root is that if anyone ever gains access to your system you are giving them a free backdoor to execute potentially malicious code... this may not be likely depending on your system set-up, network security, etc. but it is good to be aware of.

A second good reason to not run-as-root is in case you accidentally mistype something, especially with a -R !  This might sound insignificant, but many expert system admins have rued the day they didn't double check their code!

Also, FYI, you only need to sudo chown on system files. user files can be chown(ed) or chmod(ed) from within user-space (assuming you are the user that owns that file).

---

### Post by lavinog on 2010-03-26
Also you are doing the user a favor by not complicating the command line by requiring sudo.

Look at how the software-center works:
All you have to type is software-center and it handles getting root access for you.

> 
My app changes file permissions, so I'm simply using Linux commands such as chown (e.g. Shell "chown " & UserName & FileName). Please advise if there is a better way to go.

There might be a better solution if you gave us more details.  Is it a specific filename that you need to chown?  Are you trying to work around a bug such as not having permissions to write to a device...etc?

---

### Post by Barriehie on 2010-03-28
FWIW: /var/log/auth.log will have a listing of who su'ed to root and the terminal they're on.

---

