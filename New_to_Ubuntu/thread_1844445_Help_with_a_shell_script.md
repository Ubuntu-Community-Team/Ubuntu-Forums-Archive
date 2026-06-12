---
title: "Help with a shell script"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by risegeek on 2011-09-15
Basically, I have a file containing roughly 30,000 emails, I've extracted them from a complex file structure. In my current file all emails are structured like below:

```

{F8DC1601-8568-437D-920D-8CC5FBFFE0A9}`F8.eml:email@.email.com
{F8DF7A92-40AB-45E8-ACE2-2207122280D9}`F8.eml:email@.email.com
{F8E2569E-DCD6-4AD4-943F-A3FB9B0F13A9}`F8.eml:email@.email.com
{F8E8C85E-B770-492D-B1E0-6D1BB6BF3621}`F8.eml:email@.email.com
{F8EB1649-1D21-4942-9763-0C331FD8F3F0}`F8.eml:email@.email.com
{F8EBDCAF-B321-40EF-981D-ABA0F815CD08}`F8.eml:email@.email.com
{F8EC584C-E503-4E68-A2A7-62908BB65694}`F8.eml:email@.email.com
{F8F05CD5-C827-4B2C-923D-27B796BF797B}`F8.eml:email@.email.com
{F8F38AF4-573D-42F8-A84E-FE02FFB66E46}`F8.eml:email@.email.com

```

I'd like to just print the email addresses and disregard any of the other information, I've took a shot at it using grep & awk but the lack of spaces is proving troublesome, anyone got any insight? Much appreciated!

---

### Post by sisco311 on 2011-09-15
You can use awk's -F option to define a field separator. As far as I can tell the e-mail addresses are after the colon:
```
awk -F: '{print $2}' file
```

---

### Post by fdrake on 2011-09-15
```

less file | cut -d ":" -f 2 | tee > newfile

```

previous command is shorter....

---

### Post by risegeek on 2011-09-15
Thanks guys, that has worked a treat :P I underestimate the power of the awk command :)

---

