---
title: "Sudo in a user's crontab"
date: 2011-08-22
forum: Programming Talk
---

### Post by subD on 2011-08-22
Is there a way to set up a user's crontab to have a command that needs sudo and run, and not have it run in root's crontab (why it can't is irrelevant, just wondering if this is at all possible). On an extended note, running any command from a crontab that would require input of a password.

---

### Post by Bachstelze on 2011-08-23
You can run it with gksudo instead of sudo if your system has X running. You will need to set the DISPLAY variable in your crontab to make it work. For text only, I don't think it can be done.

---

### Post by v8YKxgHe on 2011-08-23
Just prefix the command with 'sudo' and make sure in your /etc/sudoers file (edit it via 'visudo') that you can run the specified command without the need to enter your password.

---

### Post by Bachstelze on 2011-08-23
> **AlexC_ said:**
> Just prefix the command with 'sudo' and make sure in your /etc/sudoers file (edit it via 'visudo') that you can run the specified command without the need to enter your password.

The question was not just about sudo, but in general any program that asks for a passowrd. Removing the need to enter the password kind of defeats the point. ;)

---

### Post by v8YKxgHe on 2011-08-23
> **Bachstelze said:**
> The question was not just about sudo, but in general any program that asks for a passowrd. Removing the need to enter the password kind of defeats the point. ;)

He wants to run a command as root but without placing the command in roots crontab; so he would need sudos default behaviour to run as root.

Maybe I'm reading it wrong, but his question would be solved by my answer.

---

