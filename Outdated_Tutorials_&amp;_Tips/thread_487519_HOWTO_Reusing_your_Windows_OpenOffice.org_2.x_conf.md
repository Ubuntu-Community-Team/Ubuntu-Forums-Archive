---
title: "HOWTO: Reusing your Windows OpenOffice.org 2.x configuration"
date: 2007-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by nvteighen on 2007-06-29
This is for those users that have been using OpenOffice.org 2.x in Windows and want to use the same toolbar, spelling, etc. configuration in Ubuntu.

NOTE: It seems that Macros can't be exported this way... 

Instructions are given for Windows XP, I'm not sure if Vista has the same folder structure... Anyway, it can't be so difficult to find out where configuration files are.

1. In Windows, go to:
C:\Documents and Settings\[user]\Application Data\OpenOffice,org2\

2. You'll see a single folder called "user". Copy it into your most reliable external storage device.

3. In Ubuntu, go to the terminal and type:
```

nautilus /.openoffice.org2

```

4. Replace the "user" folder with the one you got from Windows.

5. It works! You'll have all your settings working again.

---

