---
title: "[UbuntuServer12.04] &quot;Too many levels of symbolic links&quot;"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Banana937 on 2012-10-12
I have two users, barrett (the root user, only sudo user) and mcsa. mcsa is a user I made for friends so they could access my minecraft server without also getting access to all of my other services. In mcsa, I created a symlink to the folder "bukkit", and when I log in as mcsa and attempt to open the folder, it says:

```
-bash: cd: bukkit: Too many levels of symbolic links
```

I access the server via SSH on a Mac using Terminal, and typically directories are blue text, however this directory has red text with a black highlight to it. Definitely strange. I've never encountered this problem before. How might I fix it?

---

### Post by Gone fishing on 2012-10-13
I wonder if you made a mistake when making the symlink so that the link looks at itself? 

Have a look at this

[http://superuser.com/questions/322319/when-creating-a-symbolic-link-how-do-i-troubleshoot-too-many-levels-of-symboli](http://superuser.com/questions/322319/when-creating-a-symbolic-link-how-do-i-troubleshoot-too-many-levels-of-symboli)

---

