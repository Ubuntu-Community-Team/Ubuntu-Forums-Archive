---
title: "Login shell"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by vaibhav on 2012-06-05
When I press Ctrl+Atl+F1 and login using the character-only terminal screen, I see some messages like "Welcome...", "23 packages can be upgraded", etc. which I don't see when I open a terminal window in GUI. How are these two login processes different?

---

### Post by matt_symes on 2012-06-05
Hi

It because when you login from the console it's an interactive login shell and when you start gnome terminal it's just an interactive shell. PAM adds extra information to the interactive login shell.

For an example look in /etc/update-motd.d. This is the message of the day folder and contains a number of scripts that are run to generate the message you see when you login to the console.

```
matthew@matthew-Aspire-7540 /etc/update-motd.d
 % ls
00-header  10-help-text  90-updates-available  91-release-upgrade  98-fsck-at-reboot  98-reboot-required  99-footer
matthew@matthew-Aspire-7540 /etc/update-motd.
```

One of them is 90-updates-available and this displays the updates avaliable for you when you login.

```
matthew@matthew-Aspire-7540 /etc/update-motd.d
 % cat 90-updates-available 
#!/bin/sh

if [ -x /usr/lib/update-notifier/update-motd-updates-available ]; then
    exec /usr/lib/update-notifier/update-motd-updates-available
fi
matthew@matthew-Aspire-7540 /etc/update-motd.d
```

You can run the file directly.

```
matthew@matthew-Aspire-7540 /etc/update-motd.d
 % /usr/lib/update-notifier/update-motd-updates-available

9 packages can be updated.
0 updates are security updates.

matthew@matthew-Aspire-7540 /etc/update-motd.d
 % 
```

So the reason why is because it's an interactive login shell and gnome terminal is not.

Kind regards

---

### Post by vaibhav on 2012-06-06
Thanks a ton! That was really helpful.

---

### Post by jwbrase on 2012-06-06
I'll add that you can get a login shell in a normal terminal by invoking your shell with a certain option, generally "-l" or "--login".

---

