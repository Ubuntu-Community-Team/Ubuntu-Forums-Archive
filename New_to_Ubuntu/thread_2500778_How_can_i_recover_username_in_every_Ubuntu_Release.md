---
title: "How can i recover username in every Ubuntu Release from first to last"
date: 2024-09-11
forum: New to Ubuntu
---

### Post by amoalabuba on 2024-09-11
In this situation: i don`t have it and i don`t have access to it

---

### Post by TheFu on 2024-09-12
You cannot. It is not possible without access to the password DB (which can be local or remote).

Just to be clear, there aren't any default usernames in Linux for humans and only humans have direct logins allowed, so knowing/guessing all the non-human accounts, which there are many, many, thousands due to the Unix security model, and which are on any system are very dependent on the installed packages there. On a typical Linux computer, there are less than 100 useraccounts, but 98 of those are for system dæmons, not humans.  Dæmon accounts don't allow logins.

Perhaps you are seeking all the possible usernames on any Linux system?   If that's the case, there are millions possible because the limits for allowed usernames allow any 1-32 character alphanumeric usename. It just needs to begin with a-z.  I'm not even certain if 32 characters is the maximum length.

"b" is a valid username, but so is "casdfasd8fasdf809789asdf8972323"   <--- that's 32 characters.  That's length limit is for the tool that created user accounts, but the OS it self allows 256 characters for a username.   Of course, there is a numeric limit for the number of concurrent users allowed on any system. The max is 4 billion, but the system admin can limit it through config files, if she likes. A common limit is 32K, just to prevent automatic user-creation tools from doing too much harm, I guess.

---

### Post by ActionParsnip on 2024-09-12
is this a dupe of [https://ubuntuforums.org/showthread.php?t=2500775](https://ubuntuforums.org/showthread.php?t=2500775) ?

---

### Post by coffeecat on 2024-09-12
> **ActionParsnip said:**
> is this a dupe of [https://ubuntuforums.org/showthread.php?t=2500775](https://ubuntuforums.org/showthread.php?t=2500775) ?

It does appear to be a duplicate post from a duplicate account. I will close this thread pending investigation and review.

Thanks.

---

