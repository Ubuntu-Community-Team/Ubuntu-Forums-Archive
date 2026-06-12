---
title: "[SOLVED] Can I edit &amp;quot;/etc/passwd&amp;quot; ?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-09
I tested Flumotion and already removed it (purged), but rkhunter detected a new password and user for flumotion. 

Here is the rkhunter log.

```
[12:15:26]   Checking for passwd file                        [ Found ]
[12:15:26] Info: Found password file: /etc/passwd
[12:15:26]   Checking for root equivalent (UID 0) accounts   [ None found ]
[12:15:26] Info: Found shadow file: /etc/shadow
[12:15:26]   Checking for passwordless accounts              [ None found ]
[12:15:26] Info: Starting test name 'passwd_changes'
[12:15:27]   Checking for passwd file changes                [ Warning ]
[12:15:27] Warning: Users have been added to the passwd file:
[12:15:27]          flumotion:x:115:129:Flumotion Streaming Server,,,:/var/run/flumotion:/usr/sbin/nologin
[12:15:27] Info: Starting test name 'group_changes'
[12:15:27]   Checking for group file changes                 [ Warning ]
[12:15:27] Warning: Groups have been added to the group file:
[12:15:27]          flumotion:x:129:
```

Can I edit the passwd file to remove this entry, using the command below or should I leave it there? What happens if I just delete the flumotion group in the Groups Manager?

```
gksudo gedit /etc/passwd
```

---

### Post by Malac on 2008-09-09
From the passwd man page:>  -e, --expire
           Immediately expire an account´s password. This in effect can force
           a user to change his/her password at the user´s next login.You should be able to edit /etc/passwd but should also check /etc/shadow and /etc/group for references to it.

---

### Post by lovinglinux on 2008-09-09
> **Malac said:**
> You should be able to edit /etc/passwd but should also check /etc/shadow and /etc/group for references to it.

Thanks. It worked.

---

