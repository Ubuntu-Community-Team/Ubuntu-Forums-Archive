---
title: "ubuntu 11.04 installation"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-01-09
hi friends,

Iam having 8o GB hard drive and i created 4 partition,
in c: windows vista (20GB)
in d:software (20GB)
in e:songs (20GB)
in f:movies (20GB)

I really bored with windows and i tried to install ubuntu 11.04
i formated c drive and installed ubuntu 11.04 in it.
after booting, i cant access (mount) d,e,f drives.
it shows "lost+found" error.

---

### Post by Double.J on 2012-01-09
> **pmohankumar said:**
> hi friends,

Iam having 8o GB hard drive and i created 4 partition,
in c: windows vista (20GB)
in d:software (20GB)
in e:songs (20GB)
in f:movies (20GB)

I really bored with windows and i tried to install ubuntu 11.04
i formated c drive and installed ubuntu 11.04 in it.
after booting, i cant access (mount) d,e,f drives.
it shows "lost+found" error.

Hi there! could you show the output of
```

sudo parted
p

```
Thanks :)

---

### Post by grahammechanical on 2012-01-09
Hi

When you open the File Manager do you see a panel on the left? Linux does not use labels like drive d:, drive e;, or drive f:. That is the Microsoft language. In Linux we use the word "partiton."

In the left hand panel of the File Manager do you see there lines under the title Devices? They each should be called 20GB File system and there should be an icon of a disk drive alongside each of them. Click on each of those lines in turn and an arrow will appear alongside. Those partitions will now be mounted and you will be able to access the files and documents in them.

Regards.

---

