---
title: "Cannot type in Search Window of Dash (14.04)"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by swarup on 2014-04-24
I've just installed Ubuntu 14.04, and find that when I open dash and try to type something in the search window, most of the time it freezes after typing the very first letter and will not allow me to type any further. What is the solution for this?

---

### Post by swarup on 2014-04-29
Update: With continued use over several days, this issue seems to have resolved itself. Typing in Dash is normal now. (I have seen this issue persist in earlier distributions of unity, hence the concern.)

---

### Post by swarup on 2014-05-02
Again I am having the same problem. When I try to type in dash, it responds sporadically. Sometimes it responds, and sometimes not. Right now if I even click on the dash to open it, it doesn't open and instead freezes the whole computer until I click on some other icon to open that instead. If I close all other applications and open only dash, then it will open but will search only the home folder. If I select "applications" to search, it will not allow me to type anything.

---

### Post by Alecppt on 2014-05-02
I too have the same problem, using 3.14.2 kernel

---

### Post by pfeiffep on 2014-05-02
Possibly try booting to a previous kernel

```
pfeiffep@pete-HP:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
pfeiffep@pete-HP:~$ uname -a
Linux pete-HP **3.13.0-24-generic** #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by tuannb86 on 2014-05-04
I had same problem.

... I can type first letter in Dash box, it returned some result. 
If the mouse point focused in Ubuntu Dash Icon, i can type more.
But when the mouse point pointed out, i cant type anymore.

---

### Post by tuannb86 on 2014-05-04
And maybe i saw the problem.
When i close keyboard scim-anthy for a moment, it seem normally.

---

### Post by swarup on 2014-05-06
Tuannb86, you may have found the problem! I was using scim myself as well until turning it off just yesterday in favor of Fcitx. And now I see that the dash is working totally normally for the first time. Perhaps you are right that it was due to scim. I'll mark this thread as solved. Let us see how it goes moving forward.

---

### Post by svo-n on 2014-09-25
> **tuannb86 said:**
> And maybe i saw the problem.
When i close keyboard scim-anthy for a moment, it seem normally.

Hi! Please, how to close keyboard scim-anthy? Where?

---

