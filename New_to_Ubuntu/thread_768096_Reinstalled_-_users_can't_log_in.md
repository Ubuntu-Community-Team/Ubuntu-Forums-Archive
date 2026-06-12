---
title: "Reinstalled - users can't log in"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by keymoo on 2008-04-26
Hi,

In gutsy my computer was partitioned as / and /home.

I have done a clean install of hardy and overwritten the / directory and have preserved the home directory. My user account starts up fine (can Administer the system) and all my documents are there. However when I add the older users back in and get them to use their old home directories I get permissions problems.

Do you know the best way to get the old users added and using their old home directories on a fresh install?

Thanks,
keymoo

---

### Post by zvacet on 2008-04-26
In terminal 

```
 sudo adduser username
```

and give them they old passwords.

---

### Post by keymoo on 2008-04-26
Thanks but that doesn't work. When I try to log in as the old users it says something about not having 644 permissions - I couldn't screenshot it because I was on the login screen.

---

### Post by keymoo on 2008-04-26
I did [FONT=Courier New]man chown[/FONT] as I've heard of that command before and changed the owner of the home directory to the user I created and it seems ok now.

Thanks anyway.

---

