---
title: "Editing Files with Bash"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by Brian_Strauch on 2014-11-30
I am on a high school computer security team which corrects vulnerabilities in Ubuntu. We have a time limit, so I often use bash scripts to quickly take care of a few basic tasks at the start of the competition. Another mundane task I would like to take care of is editing the password aging controls in /etc/login.defs. Below is a portion of the initial file as well as the result that I would like to obtain:

```
# Password aging controls:
#
#       PASS_MAX_DAYS   Maximum number of days a password may be used.
#       PASS_MIN_DAYS   Minimum number of days allowed between password changes.
#       PASS_WARN_AGE   Number of days warning given before a password expires.
#
PASS_MAX_DAYS   99999
PASS_MIN_DAYS   0
PASS_WARN_AGE   7

---[ CHANGE TO ]---

PASS_MAX_DAYS   30
PASS_MIN_DAYS   7
PASS_WARN_AGE   14
```

I would like to do this without changing all of the 99999's, 0's, and 7's in the entire file. The initial values may also be different, so a good approach may be to find the variable names (like PASS_MAX_DAYS) and change the number directly after it.

I have experimented with sed, which may be an option, but I've so far been unable to figure out how to change these specific values.

Thanks for the help!

---

### Post by nerdtron on 2014-11-30
I hope this is not homework as we are not allowed here to do homework duty. :)

You can delete the lines, then add them back with the correct values.

See my terminal:
```
kenneth@nerdtron:~$ cat sample
PASS_MAX_DAYS   99999
PASS_MIN_DAYS   0
PASS_WARN_AGE   7
kenneth@nerdtron:~$ sed -i /PASS_MAX_DAYS/d sample
kenneth@nerdtron:~$ sed -i /PASS_MIN_DAYS/d sample
kenneth@nerdtron:~$ sed -i /PASS_WARN_AGE/d sample
kenneth@nerdtron:~$ cat << EOF >> sample
> PASS_MAX_DAYS   30
> PASS_MIN_DAYS   7
> PASS_WARN_AGE   14
> EOF
kenneth@nerdtron:~$ cat sample
PASS_MAX_DAYS   30
PASS_MIN_DAYS   7
PASS_WARN_AGE   14
kenneth@nerdtron:~$ 
```

---

### Post by Brian_Strauch on 2014-11-30
Wow, that was much easier than expected. And no worries, this isn't homework!

This may also be another approach

```
sudo sed '/PASS_MAX_DAYS/ c\PASS_MAX_DAYS   30' /etc/login.defs
sudo sed '/PASS_MIN_DAYS/ c\PASS_MIN_DAYS   7'  /etc/login.defs
sudo sed '/PASS_WARN_AGE/ c\PASS_WARN_AGE   14' /etc/login.defs
```

---

