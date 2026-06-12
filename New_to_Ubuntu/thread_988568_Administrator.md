---
title: "Administrator"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by kevb8ll on 2008-11-20
I have 8.04 and KDE4 installed. I want to give myself administrator access. According to the help page I select system/administration - but that option isn't available logged in as me.

How do I enable it.

The problem has occurred because I can't get my wifi to work and have been going backwards.

:mad:

---

### Post by taurus on 2008-11-20
Are you the original user that you created during the installing process?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bapoumba on 2008-11-20
Assuming kevb8ll is your login, boot in recovery mode, then
```
adduser kevb8ll admin
reboot
```

Careful, you'll be root with a # prompt.

---

### Post by kevb8ll on 2008-11-20
So I'm not going mad in not seeing that option then?

When I have run that command, my login (kevin) will be admin permanently?

---

### Post by bapoumba on 2008-11-20
> **kevb8ll said:**
> So I'm not going mad in not seeing that option then?

When I have run that command, my login (kevin) will be admin permanently?
No, but your user kevin will be able to gain admin privileges when needed, either with sudo in CLI or gksudo in GUI (see taurus's link in post #2).

---

### Post by kevb8ll on 2008-11-20
Ok having just read that I can see possible problems.

So to log in occasionally as an admin I use "root" instead of kevin?

Sorry about the thicky questions.

---

### Post by SuperSonic4 on 2008-11-20
You could change it so root is enabled but it's not wise and nobody here is allowed to tell you why either.

Log in as user and if you want to do a command as root  do ```
sudo <command>
``` in a terminal or ```
kdesu <program> [file]
```

---

### Post by bapoumba on 2008-11-20
> **kevb8ll said:**
> Ok having just read that I can see possible problems.

So to log in occasionally as an admin I use "root" instead of kevin?

Sorry about the thicky questions.

Nope, you are still kevin, but transiently gain admin rights when needed.
No need to login as root, Ubuntu choose to use sudo/gksudo.

Edit: sudo/kdesu as pointed out in the previous post, as you are using Kubuntu.

---

### Post by kevb8ll on 2008-11-20
Ok. So sudo is a temporary key to unlock admin rights and when the command is completed it "re-locks" things so I don't mess it up?

Just referring to supersonic's post. Within a terminal (konsole) do I use sudo or kdesu?

I want to follow these instructions:

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

As they seem the nearest explanation to my wifi problem. I have the same card family.

---

### Post by SuperSonic4 on 2008-11-20
In Konsole use sudo

and that is exactly what it does (Y)

You should get away with opening konsole and copy and pasting the instructions.

---

### Post by bapoumba on 2008-11-20
> **kevb8ll said:**
> Ok. So sudo is a temporary key to unlock admin rights and when the command is completed it "re-locks" things so I don't mess it up?

By default, you gain admin rights for 5 mins (otoh) or until you close the terminal/application window.

---

### Post by kevb8ll on 2008-11-20
Thanks guys.

---

### Post by bodhi.zazen on 2008-11-20
> **kevb8ll said:**
> Thanks guys.

[indent]... and gals ;)[/indent]

---

### Post by adaptr on 2008-11-20
> **bapoumba said:**
> By default, you gain admin rights for 5 mins (otoh) or until you close the terminal/application window.
10 minutes. Sudo hardcode.
And not until the application closes either - 10 minutes, guv'.

On the earlier post - **adm **joins you to the wheel group needed for sudo rights, not admin.

Unless Ubuntu changed all that out from under the 20-year-old Unix standards in one release, as it is wont to do.

---

### Post by jken146 on 2008-11-20
> **adaptr said:**
> 10 minutes. Sudo hardcode.
And not until the application closes either - 10 minutes, guv'.

On the earlier post - **adm **joins you to the wheel group needed for sudo rights, not admin.

Unless Ubuntu changed all that out from under the 20-year-old Unix standards in one release, as it is wont to do.

Ubuntu doesn't use wheel.  The group for sudoers is is admin

---

### Post by cariboo on 2008-11-20
If youy are running Intrepid (v8.10) there are drivers natively available for you network card.

Jim

---

### Post by bapoumba on 2008-11-21
> **adaptr said:**
> 10 minutes. Sudo hardcode.

> timestamp_timeout
                       Number of minutes that can elapse before sudo will ask for a passwd again. The default is **15**.

15, my bad.

---

