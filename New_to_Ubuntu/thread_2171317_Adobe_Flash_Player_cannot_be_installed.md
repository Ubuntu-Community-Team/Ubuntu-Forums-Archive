---
title: "Adobe Flash Player cannot be installed"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by Lambros_Boukouras on 2013-08-30
Hey guys,

as I have no clue how to fix this I will ask you.
I wanted to install the flash player, so I downloaded the tar.gz version
extracted the file,
opend the terminal and typed in sudo apt-get install flashplugin-installer
and he tells me that there are unfullfilled dependencies. He tells me that
it depends on libnss3-1d and libnss4-0d

What should i do?

Thank you so much.

---

### Post by Impavidus on 2013-08-30
(Thinking loudly) There's no need to download and extract the tar.gz file, running **sudo apt-get install flashplugin-installer** should be all you need. It depends on libnss3-1d and libnss4-0d, so the question is why these aren't installable.

By the way, which Ubuntu version is this?

---

### Post by Jonathan Precise on 2013-08-30
Try:

```
sudo apt-get install libnss3-1d libnss4-0 flashplugin-installer
```

If that fails, then:

```
sudo apt-get install adobe-flashplugin
```

Be sure to enable the Partner's repository (Canonical) first.

Also, post with code tags:
(CODE)Depends:
libnss3-1d
libnss4-0d
You have unmet dependencies.(/CODE)

Change the parenthesis () to brackets []:
```
Depends:
libnss3-1d
libnss4-0d
You have unmet dependencies.
```

---

