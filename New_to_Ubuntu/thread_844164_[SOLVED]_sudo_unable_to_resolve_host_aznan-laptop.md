---
title: "[SOLVED] sudo: unable to resolve host aznan-laptop"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-29
I get this message before terminal prompt me the password everytime I run sudo command. As far as I remember, i never see this message before. What does it mean and how to prevent terminal shows this irritated message

---

### Post by drs305 on 2008-06-29
Your hosts file may be incorrect.
```

cat /etc/hosts
```

It normally looks something like:
```

127.0.0.1 localhost
127.0.1.1  computername

```

If it has been changed to something like:
```

127.0.0.1 localhost
127.0.1.1  computername.something-else-added-to-the-end

```
Then remove the period and everything afterward after making a backup:
```
sudo cp /etc/hosts /etc/hosts-bak1
gksudo gedit /etc/hosts
```

---

### Post by wariskampar on 2008-06-29
Thanks so much. Your solution solve my problem. However, I think the change in my /etc/hosts earlier was due to SAMBA config. If I delete the line after 'period', does it jeopardizing my SAMBA setting? (i deleted FAMILY which is my network domain)

---

### Post by drs305 on 2008-06-29
> **wariskampar said:**
> Thanks so much. Your solution solve my problem. However, I think the change in my /etc/hosts earlier was due to SAMBA config. If I delete the line after 'period', does it jeopardizing my SAMBA setting? (i deleted FAMILY which is my network domain)

It shouldn't. I don't know what app is appending the ".xxxxxx" but nobody has reported a problem changing it back. If you deleted the line or edited it but remember what it said, now would be a good time to recreate it as a comment. This would make the end result look like the following. If you have problems, you can uncomment the old line (remove the starting # symbol) and put a # symbol in front of the current line. 

```

127.0.0.1 localhost
127.0.1.1  computername
# 127.0.1.1  computername.whateverwasadded

```

---

### Post by ageer1 on 2008-06-29
Hi wariskampar,

Several of us have had this problem and I am curious as to if this occurs due to upgrading to Hardy rather than doing a fresh install. Which way did you get Hardy?

Thanks,
     Joe

---

### Post by drs305 on 2008-06-29
> **ageer1 said:**
> Hi wariskampar,

Several of us have had this problem and I am curious as to if this occurs due to upgrading to Hardy rather than doing a fresh install. Which way did you get Hardy?

Thanks,
     Joe

I have done it both ways but never had this problem. I remember someone suspecting two apps that were probably responsible for amending the line but don't recall what they were. 

Updated: Couldn't find any common link to the problem.

---

### Post by wariskampar on 2008-06-29
I fresh installed my Hardy Heron. This problem begin after I installed Samba some where last week. So I assume Samba was responsible for the changing because there was no other way Ubuntu know my domain w/o I told it first!

---

### Post by cariboo on 2008-06-29
If you do want to use a domain then do it this way:

```
127.0.1.1   hostname.domain      hostname
```

Jim

---

