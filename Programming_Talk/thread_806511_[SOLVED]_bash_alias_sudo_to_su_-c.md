---
title: "[SOLVED] bash: alias sudo to su -c"
date: 2008-05-25
forum: Programming Talk
---

### Post by moep on 2008-05-25
Hello everyone,

I'm trying to build an alias or script that replaces sudo with su -c.

So far I've come up with this:

```
#!/bin/bash
su -c '$@'
```

saved as /bin/sudo and it's not really working at all. I'm getting prompted for the root password and nothing more happens.
For example I'm not getting any output from a program when executing this script over typing out the full su -c 'command here'. Where is the flaw here? :-s

---

### Post by jrib on 2008-05-25
Why would you do such a thing?

---

### Post by geirha on 2008-05-25
You really shouldn't do this. Any script expecting sudo to be sudo may stop working. I'd reccommend you just use su -c instead of overriding sudo.

The flaw in your script though, is that you have $@ inside ''-quotes. ''-quotes suppresses variable expansion.

---

### Post by moep on 2008-05-25
> **_jason said:**
> Why would you do such a thing?

I'm trying to turn one of my webdevelopment servers into a public webserver. 
After wiping the drive and installing hardy, I read up on a few threads about hardening ubuntu. One of them suggested to always use *su -c 'command'* instead of *sudo command*. 
It made sense to me because an attacker would have to know both the current user's password as well as the root password to do real damage — unlike with sudo, where the user's password alone is enough to gain full access to the box. 
I'm used so to typing a quick sudo that the "su -c 'command'" thing seemed like too much hassle to  write, thus this thread. Lazy, I know. ;)

> **geirha said:**
> You really shouldn't do this. Any script expecting sudo to be sudo may stop working. I'd reccommend you just use su -c instead of overriding sudo.

The flaw in your script though, is that you have $@ inside ''-quotes. ''-quotes suppresses variable expansion.

Thanks, I won't touch sudo then but I'd still like to alias *su -c 'command'* to *suc command* for convenience.
I've tried double-quotes but that doesn't work either. Escaping the single-quotes didn't work out either.

---

### Post by sisco311 on 2008-05-25
Add this line to the ~/.bashrc:
> alias suc='su -c '$@''
you need to log in and log out.

---

### Post by geirha on 2008-05-25
$@ doesn't handle quite as you might think. From bash's manpage:
```

       *      Expands to the positional parameters, starting from  one.   When
              the  expansion occurs within double quotes, it expands to a sin&#8208;
              gle word with the value of each parameter separated by the first
              character of the IFS special variable.  That is, "$*" is equiva&#8208;
              lent to "$1c$2c...", where c is the first character of the value
              of  the IFS variable.  If IFS is unset, the parameters are sepa&#8208;
              rated by spaces.  If IFS is  null,  the  parameters  are  joined
              without intervening separators.
       @      Expands  to  the positional parameters, starting from one.  When
              the  expansion  occurs  within  double  quotes,  each  parameter
              expands to a separate word.  That is, "$@" is equivalent to "$1"
              "$2" ...  If the double-quoted expansion occurs within  a  word,
              the  expansion  of  the  first  parameter  is  joined  with  the
              beginning part of the original word, and the  expansion  of  the
              last  parameter  is  joined  with  the last part of the original
              word.  When there are no  positional  parameters,  "$@"  and  $@
              expand to nothing (i.e., they are removed).

```
In other words, try with su -c "$*". As for an alias, I don't think you can get the quotes in, so you'd have to make the alias as: alias suc='su -c' and use it like: suc 'echo hello' ...

---

### Post by moep on 2008-05-25
> **geirha said:**
> $@ doesn't handle quite as you might think. From bash's manpage:
In other words, try with su -c "$*". As for an alias, I don't think you can get the quotes in, so you'd have to make the alias as: alias suc='su -c' and use it like: suc 'echo hello' ...

Thanks. I've tried to get around typing the quotes but as there's no way around it I'll just have to get used to typing out the full *su -c 'command'*. No biggie. :)

---

### Post by jrib on 2008-05-25
> **moep said:**
> Thanks. I've tried to get around typing the quotes but as there's no way around it I'll just have to get used to typing out the full *su -c 'command'*. No biggie. :)

You want ```
alias suc='su -c'
```.

However, your reasoning that the attacker needs to know two passwords is not that convincing.  You should be using ssh keys anyway and not allowing anyone to login remotely with just a password.

---

### Post by slavik on 2008-05-25
a hacker using sudo would have to know the password to the account with sudo priveledges ...

if you enable the root account, that doesn't make a difference whether the hacker has to know the password to an account with sudo rights or the root rights. sudo also allows you to configure who is allowed to do what (based on groups and/or usernames).

Not only that, you need only 1 sudo account (yours) which you won't be using much after setting up the server anyway.

---

### Post by mssever on 2008-05-25
Try
```
#!/bin/bash
exec su -c \'"$*"\'
```
I haven't tested this, so if it doesn't work, try some variations on the theme.

That said, I agree with the posters who question the wisdom of this. I'd actually argue that enabling a root password actually *reduces* security, because in order to get in, you need both a username and password. Now, every *nix system has a root account, so to gain root, you need only to obtain the password; you already know the username. To gain root on a system such as default Ubuntu, you need to find the username that has the sudo privileges you want, then obtain that password.

My server is configured such that SSH is the only way in, and SSH is configured to forbid password-based authentication. So the only way in is to possess the correct key.

---

### Post by moep on 2008-05-26
I agree that the server should have tunneled cleartext password authentication disabled, but unfortunately that's not an option for me as I will have to access the server on the campus from public machines. 

With that being said, I'll just create another locked down and chrooted user for this purpose and avoid administering the server from public machines altogether. 
I have of course altered the ssh port and installed denyhosts with very unforgiving settings, but all of that (including the su -c habit) wouldn't help when facing a keylogger.

Thanks for your input everyone.

---

### Post by DevOz on 2010-10-18
Try
```
echo <rootpassword> | su -c <command> root
```
This works for me.

---

