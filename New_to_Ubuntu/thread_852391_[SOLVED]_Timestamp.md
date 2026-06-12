---
title: "[SOLVED] Timestamp"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by NikS on 2008-07-07
When I'm trying to install something or anything related to sudo, I am getting a message:
```

niks@Zion:~$ sudo apt-get install wine
sudo: timestamp too far in the future: Jul  8 06:00:05 2008
```

I just adjusted my clock manually to show correct time, Is this related to it??
Will it be cleared after 6:00:25 in the morning here??
Its 01:07:00 right now here!!

Otherwise, What shall i do?

---

### Post by tamoneya on 2008-07-07
make sure you set the correct time zone.  If you set your local time is say 2PM and you set your clock to 2PM GMT then you will be "in the future" since india is ahead of GMT.

---

### Post by NikS on 2008-07-07
Timezone selected is correct!!
May be it was correct even for the previous time setting, So still, I was in the future!!!
:)

So its surely cause of that,
I think I should wait till I return to present then (past 6 amin reality??)
& if I dont access sudo, it wont check for time! so past 6 am, It should work!!

:?
ok I'l wait n see!!

---

### Post by Malac on 2008-07-07
```
sudo -k
``` should sort it out, this clears the sudo timestamp

See: ```
man sudo
```

---

### Post by NikS on 2008-07-07
> **Malac said:**
> ```
sudo -k
``` should sort it out, this clears the sudo timestamp

See: ```
man sudo
```

It worked..
Thanks!!
Saved me 5 hours!!
:)

---

### Post by Malac on 2008-07-07
> **NikS said:**
> It worked..
Thanks!!
Saved me 5 hours!!
:)
You're Welcome :D

---

