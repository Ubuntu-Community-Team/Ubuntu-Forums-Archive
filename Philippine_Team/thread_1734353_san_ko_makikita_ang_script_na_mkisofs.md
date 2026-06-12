---
title: "san ko makikita ang script na mkisofs?"
date: 2011-04-20
forum: Philippine Team
---

### Post by buntuts on 2011-04-20
saan directory ko makikita ang script na gumagana sa command na **mkisofs**?

---

### Post by jao_madn on 2011-04-20
> **buntuts said:**
> saan directory ko makikita ang script na gumagana sa command na **mkisofs**?

Pwedi mu ilaborate more kng anu ibig mu sabihin.

---

### Post by dsdeiz on 2011-04-20
I'm not familiar with "mkisofs", sorry. But if it's a command, maybe you can try this?
```
which mkisofs
```

Or if it's a package and you're looking for the files that belongs to it and what directory they are in, you can prolly do this:
```
dpkg -L mkisofs
```

You can pipe the output to grep if you're looking for a specific command. HTH. :D

---

### Post by buntuts on 2011-04-20
di pala bash script to.

its a command to create .iso files however, i'm not sure how to edit it. its an .exe file.
i do have gcc installed, how dyou edit this kind of files that are once compiled?

---

### Post by dsdeiz on 2011-04-20
I think yung kelangan mo is ung source instead. Hehe Try mo siguro:

```
apt-get source mkisofs
```

..then edit-edit or patch-patch, then compile ulet para makuha ung deb file na merong changes mo... :D

---

