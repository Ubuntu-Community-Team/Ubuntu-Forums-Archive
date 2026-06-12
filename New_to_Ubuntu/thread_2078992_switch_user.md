---
title: "switch user"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by erikai on 2012-11-01
I'm using ubuntu on virtualbox. I'm trying to learn terminal commands. My problem is: I cannot switch to a different user (that i created using useradd). I can only switch from my user account to root and vice versa.

When I try to type
su bob, it would prompt for a password, then I enter the password. After that it would just show a new line with "S" displayed at the start. The same thing happens to the other users that I created as well.


Please help.

---

### Post by HiImTye on 2012-11-01
it shows something like this?
```
youruser@yourhost:~$ su bob
enter password for bob:
$
```

---

### Post by erikai on 2012-11-01
> **HiImTye said:**
> it shows something like this?
```
youruser@yourhost:~$ su bob
enter password for bob:
$
```

something like that.
let me copy it here

root@erika-desktop:/home/lisa#su bob
$
$
$

(after pressing enter repeatedly that shows up. Sorry I thought it was S but it was $ when I looked at it closely)


or like this if changing from my user account:

erika@erika-desktop:/home/lisa#su bob
Password:
$
$
$



I noticed that it would not ask for password when I am using root.

---

### Post by HiImTye on 2012-11-01
after you *su bob*, enter
```
echo $USER
```
that will output who is logged into the shell

---

### Post by erikai on 2012-11-01
> **HiImTye said:**
> after you *su bob*, enter
```
echo $USER
```
that will output who is logged into the shell

oh. it says bob. that means I'm logged in as bob right?

I feel so stupid.

---

### Post by HiImTye on 2012-11-01
yeah, I already knew that when I first responded, but it's better to have you show yourself, and it also demonstrated an issue with *useradd*. the best way to add users is in the *Users and Groups* tool, as it does everything that is necessary with groups, makes sure that user files are sorted (such as the .*bashrc* file that bob is missing), etc. I would remove bob and create him again in *Users and Groups*

---

### Post by Wim Sturkenboom on 2012-11-01
You have not defined a prompt for the user 'bob'. Check an existing .bashrc file (e.g. in your own home directory) with the one from user 'bob' and check for 'PS1'.

When being root, it will never prompt for a password when using _su_. There is no reason for it as root anyway can circumvent it.

Also, have a look at the difference between _su_ and _su -_. I far prefer the latter as the 'new' user's environment is taken into account.

---

### Post by erikai on 2012-11-01
thank you. Users and Groups tool is gui based? Ok let me find that.

---

### Post by HiImTye on 2012-11-01
> **erikai said:**
> thank you. Users and Groups tool is gui based?
it sure is! it's as easy as clicking a '+' then typing a name and (optionally, a) password!

---

### Post by erikai on 2012-11-01
> **Wim Sturkenboom said:**
> You have not defined a prompt for the user 'bob'. Check an existing .bashrc file (e.g. in your own home directory) with the one from user 'bob' and check for 'PS1'.

When being root, it will never prompt for a password when using _su_. There is no reason for it as root anyway can circumvent it.

Also, have a look at the difference between _su_ and _su -_. I far prefer the latter as the 'new' user's environment is taken into account.

what do I do with PS1 on the .bashrc file?

I cant find the difference between su and su - except for the prompt(?)

---

### Post by HiImTye on 2012-11-01
> **erikai said:**
> what do I do with PS1 on the .bashrc file?
that's not important if you make bob with *Users and Groups*
> I cant find the difference between su and su - except for the prompt(?)
the - makes su use the users environment. from *man su*
```
-, -l, --login
           Provide an environment similar to what the user would expect had
           the user logged in directly.

           When - is used, it must be specified as the last su option. The
           other forms (-l and --login) do not have this restriction.
```

---

### Post by erikai on 2012-11-01
> **HiImTye said:**
> it sure is! it's as easy as clicking a '+' then typing a name and (optionally, a) password!

thank you! :KS

---

### Post by HiImTye on 2012-11-01
you're welcome :D

---

