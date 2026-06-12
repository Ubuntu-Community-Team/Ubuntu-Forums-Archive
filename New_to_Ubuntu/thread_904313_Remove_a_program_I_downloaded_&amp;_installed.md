---
title: "Remove a program I downloaded &amp; installed?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by captgadget on 2008-08-29
I downloaded a deb file by name of Autopano Pro that I'd like to remove. I've tried
sudo apt-get remove --purge and it comes back "couldn't find package autopano". I've also tried sudo rm -r package_name and I get the same message. Can someone help me to remove this package?

---

### Post by SunnyRabbiera on 2008-08-29
is it listed in synaptic by any chance?

---

### Post by cscat on 2008-08-29
have you tried Synaptic?

try "sudo synaptic" now and type Ctrl-F and search for "Autopano". It will surely find it. Then right click on the package you've been looking for and ...

---

### Post by kellemes on 2008-08-29
If you just downloaded it you need to find it first. Where did you put it to begin with?
To search from a terminal window..
```
sudo updatedb
locate autopano
```

---

### Post by captgadget on 2008-08-29
I didn't use Synaptic. Here is a screenshot of what I have.

---

### Post by hyper_ch on 2008-08-29
do you still have the .deb file? If so run
```

sudo dpkg --purge NAME.deb

```

---

### Post by captgadget on 2008-08-29
This is the return on that:

---

### Post by kellemes on 2008-08-29
> **captgadget said:**
> This is the return on that:

Not much ;-)

---

