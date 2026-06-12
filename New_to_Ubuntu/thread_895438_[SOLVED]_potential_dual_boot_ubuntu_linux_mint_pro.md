---
title: "[SOLVED] potential dual boot ubuntu/ linux mint problem"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-20
Hi
I dual booted linux mint today but have been made aware of a potential problem
As Mint and Ubuntu are almost identical (mint is really ubuntu apparently) there could be problems when updating due to the similarily of the two distros
I have been warned that this is a particular problem if the user names are the same (and yes I did make them the same :rolleyes:)
How do I change a user and the home directory?
When I change my user name in Mint (don't want to risk it in ubuntu I've spent to much time tinkering with it..)it says that the user name will change but the home directory will stay
is this a problem? (I have fairly limited HDD space)
can the user directory be deleted afterwards without altering the system?
why am I such a numpty:lolflag: again...

---

### Post by sandysandy on 2008-08-20
both systems are independent of each other. so updating one should not affect the other.

---

### Post by coffeecat on 2008-08-20
> **LTFC2020 said:**
> As Mint and Ubuntu are almost identical (mint is really ubuntu apparently) there could be problems when updating due to the similarily of the two distros
I have been warned that this is a particular problem if the user names are the same (and yes I did make them the same :rolleyes:)

If you are referring to my warning about a problem with menu.lst in [your other thread]("http://ubuntuforums.org/showthread.php?t=895170"), you have misunderstood. I did **not** say that there is a problem if the user names are the same. In fact it's better if they are. See my second post in the other thread, especially the bit about UIDs. I strongly advise you **not** to create extra accounts until you have understood UIDs.

Also, you may wish to re-read my post about the menu.lst problem. I really am at a loss as why you should think it was about usernames.

---

### Post by coffeecat on 2008-08-20
> **sandysandy said:**
> both systems are independent of each other. so updating one should not affect the other.

Have a look at my post in the thread I link to in the previous post. It's an extremely obscure bug which **may** bite if you have two installations of Hardy on the same machine, or Hardy and the latest Mint. I only posted about it because the OP had set up a dual-boot with Hardy and Mint.

---

### Post by LTFC2020 on 2008-08-20
"I find that useful because it helps me to remember who I am.  At my age that's becoming important to me"
A1 to that coffee cat
thanks for the help
will leave as is

---

