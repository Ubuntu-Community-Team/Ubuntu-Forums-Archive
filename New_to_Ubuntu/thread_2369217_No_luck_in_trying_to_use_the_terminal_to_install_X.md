---
title: "No luck in trying to use the terminal to install XPGnome"
date: 2017-08-20
forum: New to Ubuntu
---

### Post by 357mag on 2017-08-20
I have download XPGnome 1.0 and it's been copied to the desktop. I'm in the terminal:

tim@Micron:~Desktop$

All I get is No such file or directory...

I've entered things like:

installxpgnome.sh

xpgnome-1.0-zip

Doesn't go through cause Lubuntu keeps telling me No such file or directory.

---

### Post by jeremy31 on 2017-08-20
I doubt it will work with any supported version of Ubuntu.  The one site I found during a search said it wouldn't work in Ubuntu 12.04 but did work in Ubuntu 8.04.  Ubuntu 8.04 has been unsupported for 4 years now

---

### Post by kurt18947 on 2017-08-20
what does 'ls' tell you? If you're in the correct directory, installxpgnome.sh should show up. Every time I've gotten that message it was because I wasn't in the same directory as the desired file. In my case it would look something like this:

```
user1@AMD_Desktop:~/Desktop$
```

---

### Post by vasa1 on 2017-08-20
> **jeremy31 said:**
> I doubt it will work with any supported version of Ubuntu.  The one site I found during a search said it wouldn't work in Ubuntu 12.04 but did work in Ubuntu 8.04.  Ubuntu 8.04 has been unsupported for 4 years now+1 and if XPGnome is some sort of gtk theme, it won't work on 16.04 or later.

---

