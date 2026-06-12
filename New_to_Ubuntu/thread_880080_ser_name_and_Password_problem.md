---
title: "ser name and Password problem"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by jevg on 2008-08-04
I have just installed Ubuntu on my windows XP machine in windows.
Installation has gone fine, however when trying to login I am unable to as my user name or password or both is being regected.
I decided to uninstall through Add/Remove in windows but windows does not accept the remove button click.

Is there anyway to reset the user name and password in order to login in. I appear to be stuck. I cant remove the application from windows in order to reinstall and reset the user/password
and I can't login either.

Please help

Jevg

---

### Post by cariboo on 2008-08-04
In the linux operating system user name's and passwords are case sensitive. Type your password and username exactly as you entered them during installation. If that doesn't work you can startup in recovery mode. Once you get to the menu, drop to a root shell and enter the following:

```
useradd -m <username> -p <password>
```

Where <username> is your user name and <password> is your password. This will create a new home directory for the user you just created.

Jim

---

### Post by sisco311 on 2008-08-04
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
in hardy (ubuntu 8.04) you will need to select the [I]root shell
[/I]option after the computer booted in recovery mode.

---

### Post by jevg on 2008-08-04
> **cariboo907 said:**
> In the linux operating system user name's and passwords are case sensitive. Type your password and username exactly as you entered them during installation. If that doesn't work you can startup in recovery mode. Once you get to the menu, drop to a root shell and enter the following:

```
useradd -m <username> -p <password>
```

Where <username> is your user name and <password> is your password. This will create a new home directory for the user you just created.

Jim

Thanks Jim
I will try that and get back. 

Joss

---

### Post by jevg on 2008-08-04
> **sisco311 said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
in hardy (ubuntu 8.04) you will need to select the [I]root shell
[/I]option after the computer booted in recovery mode.

Thanks a lot

All help is greatly appreciated

Joss

---

