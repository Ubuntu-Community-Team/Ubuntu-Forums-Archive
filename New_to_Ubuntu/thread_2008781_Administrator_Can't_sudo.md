---
title: "Administrator Can't sudo?"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by mapes12 on 2012-06-23
I'm running 12.04 64bit. I've set up a new Admnistrator user account. The new user logs into their account, launches Terminal to execute a sudo command but Terminal returns a response saying that "the user can't be found on the sudoers list" and refuses to execute the command.

Any ideas please?

Mark

---

### Post by d.atanasov on 2012-06-23
How did you created the administrator account ?

---

### Post by U202E on 2012-06-23
(maybe you could use google)
maybe this will help:
press ctrl+alt+f1, login and do your thing.
and does the second admin use the same sudo password?

or you could change the sudo password,
<snip>

---

### Post by mapes12 on 2012-06-23
> How did you created the administrator account ?Logged onto my own account (Administrator that was created when the system was installed) then System Settings>Administration>User accounts i.e. the GUI way.

---

### Post by HiImTye on 2012-06-23
please don't tell people to set or change their root password
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

1. how did you make the admin account?
2. paste the command and its' output into your response then highlight it and click the '#' at the top to encase it in code tags

---

### Post by raja.genupula on 2012-06-23
```
sudo usermod -aG sudo <username>
```

then try again .

---

