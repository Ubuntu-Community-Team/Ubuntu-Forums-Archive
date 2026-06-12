---
title: "---About PATH value about login"
date: 2010-11-21
forum: Programming Talk
---

### Post by bzhao on 2010-11-21
Hi all,

   I login from virtual terminal(available with Alt-F1-6) as a common user. I found that the /sbin/ and /usr/sbin are included in the PATH value. 
   But if login by "su - this_user", /sbin and /usr/sbin are not included in the PATH value.

   I did trace the problem and found that the file /etc/login.defs is controlling this.
   the conttrolling lines are:
ENV_SUPATH	PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV_PATH	PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
  
   So problem is why the file cannot control the login from virtual terminal?
what is difference between the 2 login ways mentioned above?


Bill Z

---

### Post by saulgoode on 2010-11-21
> **bzhao said:**
>    I did trace the problem and found that the file /etc/login.defs is controlling this.
:
:
So problem is why the file cannot control the login from virtual terminal?

The login.defs PATH settings can be -- and typically are -- superseded by instructions provided in any of /etc/profile, ~/.bash_profile,  ~/.bash_login,  and ~/.profile 
  
> **bzhao said:**
> what is difference between the 2 login ways mentioned above?

The difference is that 'su - *this_user*' is not an actual login, so *this_user*'s startup scripts which get executed are different.

For logins:
[INDENT]/etc/profile
~/.bash_profile
~/.profile[/INDENT]

For non-logins:
[INDENT]~/.bashrc[/INDENT]

If you want to use 'su' to login as another user, use the '-l' or '--login' options (the man page for 'su' is misleading about this).

---

### Post by bzhao on 2010-11-22
> **saulgoode said:**
> The login.defs PATH settings can be -- and typically are -- superseded by instructions provided in any of /etc/profile, ~/.bash_profile,  ~/.bash_login,  and ~/.profile 
  


The difference is that 'su - *this_user*' is not an actual login, so *this_user*'s startup scripts which get executed are different.

For logins:
[INDENT]/etc/profile
~/.bash_profile
~/.profile[/INDENT]

For non-logins:
[INDENT]~/.bashrc[/INDENT]

If you want to use 'su' to login as another user, use the '-l' or '--login' options (the man page for 'su' is misleading about this).

Sir
 I did test, the -l and - have the same function.

Bill Z

---

