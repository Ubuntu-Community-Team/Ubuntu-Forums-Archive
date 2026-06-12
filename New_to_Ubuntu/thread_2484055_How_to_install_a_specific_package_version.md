---
title: "How to install a specific package version?"
date: 2023-02-16
forum: New to Ubuntu
---

### Post by hanji866 on 2023-02-16
I'm new to ubuntu

I'm currently running postfix-mysql version 3.6.4. I want to upgrade to 3.7.3. What is the proper procedure for this?

Thanks!
hanji

---

### Post by ActionParsnip on 2023-02-16
What is the output of:
```

lsb_release -a; uname -a

```

---

### Post by hanji866 on 2023-02-16
> **ActionParsnip said:**
> What is the output of:
```

lsb_release -a; uname -a

```

```
lsb_release -a; uname -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
Linux skylla2a.astarna.com 5.15.0-60-generic #66-Ubuntu SMP Fri Jan 20 14:29:49 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by ActionParsnip on 2023-02-16
postfix-mysql seems to be tied to postfix itself so you'll need to upgrade all of postfix too.

---

### Post by hanji866 on 2023-02-16
> **ActionParsnip said:**
> postfix-mysql seems to be tied to postfix itself so you'll need to upgrade all of postfix too.

That's okay. I just want to get the whole postfix system up to 3.7.4

Thanks
hanji

---

### Post by ActionParsnip on 2023-02-16
You may find a PPA on Launchpad.net. Otherwise you may have to upgrade to Lunar Lobster (Ubuntu 23.04) which has the version you want

---

### Post by Holger_Gehrke on 2023-02-16
Seems to me you have three options:

[LIST=1]
[*]become a tester for Ubuntu 23.04 which will include 3.7.4-2
[*]find a PPA; hopefully one that regularly fixes bugs / vulnerabilities. I haven't found one, but that doesn't mean there isn't one
[*]compile it from source yourself and then regularly get any fixes and compile it again and again and ...
[/LIST]

I'd probably go with option 3, but I am a hobbyist with too much time on my hand and a love of tinkering ...
Holger

---

### Post by Impavidus on 2023-02-16
I don't use postfix-mysql myself, so I know no details here.

What's the reason you want to upgrade from 3.6.4 to 3.7.3 (or higher)? If it is for some new feature, it's explained above. But if you read there's some security issue with 3.6.4 that has been fixed in 3.7.3, such security fixes should get backported on Ubuntu for packages in the main repository.

---

