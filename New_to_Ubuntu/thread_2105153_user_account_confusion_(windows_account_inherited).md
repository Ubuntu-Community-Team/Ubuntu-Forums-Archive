---
title: "user account confusion (windows account inherited?)"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by Frankels on 2013-01-15
Hi, I just installed ubuntu 12.04 from windows using wubi. Somehow the windows user account name got into ubuntu and now there is confusion in ubuntu over the user:
the folder in the home directory has the right name: frankels, and the login name in terminal is good (frankels@ubuntu). This is the name I told wubi to use. But the name on the taskbar is the windows account (erik), and this wrong name is also the only administrator account under user accounts (erik). in fact there is no other account. It's almost as if I'm logged in as two users at once!?
Ubuntu seems to have inherited the windows username somehow.
I just want frankels and nothing else... how do I change this?
I hope I don't need a reinstall...

---

### Post by TheFu on 2013-01-15
I'd like to help, but don't understand enough to help.  I've never used WUBI myself.  Seems strange to still being wubi as a Linux user since 2008.  The output from these commands will help me (and others) understand the situation better.

Open a terminal, then copy/paste these commands into it 1 at a time, then copy/paste the results back here.

$ **env | grep HOME**
$ **egrep -i 'frank|erik' /etc/passwd**
$ **cd ; pwd ; id**

When you copy/paste, leave the first '$' out. That denotes that the command works as an end user.  If I'd used a '#', then you'd be running as the "root" user.  These are just information gathering commands.  To understand what each does before you run them, use the **man {command} **command. **man pwd** for example.

I think you may have something mixed in the password file. That is easy to fix.  The actual passwords are stored encrypted in a different file, which nobody needs.

Another thought ... did you start up Ubuntu from the erik Wnidwos account, perhaps?

---

### Post by Bölvaður on 2013-01-15
After executing those commands go to the dash.
In the dash (the search bar which pops up after clicking the meta/super/windows button) look for *users and groups* and see if you can shed some light on this matter from there.

I am curious what really is up.

---

### Post by Frankels on 2013-01-15
frankels@ubuntu:~$ env | grep HOME
HOME=/home/frankels
frankels@ubuntu:~$ egrep -i 'frankels|erik' /etc/passwd
frankels:x:1000:1000:Erik,,,:/home/frankels:/bin/bash
frankels@ubuntu:~$ cd;pwd;id
/home/frankels
uid=1000(frankels) gid=1000(frankels) groups=1000(frankels),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)

mean face above should be : x attached but it makes a :x  :)

additional information: this is a laptop with a busted graphics card so I booted in safe mode (actually I start booting in safe graphics mode and then continue normal boot which somehow gives me relatively good graphics, I guess it stops using the graphics card or bypasses it) but I don't think that has anything to do with the log in.

wubi was the quickest and easiest way to make this a dual boot system.

I do not start ubuntu from windows. I did however install from windows using wubi. 

from dash I can only access 'user accounts', not 'users and groups'. Erik is the only account there and it is administrator, but it uses the frankels passwrd :)

thanks for the quick response by the way, I hope there's an easy fix

---

### Post by sandyd on 2013-01-15
The username shown in User Accounts is _not_ your Linux account name - it is just the full name that the Ubuntu refers to you as.

Its like having a nickname (username) and a real name that Ubuntu uses for most content, instead of your username.

You can easily change the name by unlocking the 'User Accounts' settings, and clicking your name.

---

### Post by Frankels on 2013-01-15
SOLVED it :)
thanks guys, it was so simple and right in front of me...I feel a bit ashamed :)

---

### Post by Bölvaður on 2013-01-15
> **Frankels said:**
>  I hope there's an easy fix
You cannot get an easier fix than this.
Go back into *User Accounts *and rename the full name of the account to frankel or what ever you want the name of that account to be. It's not frankel's password, it is frankel's account with a different alias (full name).

---

### Post by TheFu on 2013-01-15
> **Frankels said:**
> SOLVED it :)
thanks guys, it was so simple and right in front of me...I feel a bit ashamed :)

I wish all of them were this easy!  As with anything, *we don't know what we don't know.  *You have nothing to be ashamed about at all.

I hope you looked up what each command did and have a little better understanding why I asked for each to be run.  They were different views of the same information, right?  

Editing the password file was the fix, correct?
To check this, run that** egrep** command again. If you post it inside a "code" block, none of the smilies will happen. In the advanced editor, there's a '#' symbol that will create a code block, like this: ```
egrep -i 'frank|erik' /etc/passwd
```

---

