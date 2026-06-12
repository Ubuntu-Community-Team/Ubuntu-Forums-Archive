---
title: "Something Strange ???"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by bipolaric on 2012-03-17
Hi,

I installed Ubuntu 10.10 (Maverick Meerkat) the other week, and after install it naturally updated.  Now, just out of curiosity, I happened to click 'About Ubuntu' in the 'System' menu and it says that I am actually running Ubuntu 11.04 (Natty Narwhal), but I 'Didn't' upgrade the OS.

I'm not complaining, it's just a bit strange.  Does Ubuntu do this automatically ?  And has anyone else had the same experience.

Very, Very Very, Very ..... Very, Very Strange.

Mark :)

---

### Post by sammiev on 2012-03-17
> **bipolaric said:**
> Hi,

I installed Ubuntu 10.10 (Maverick Meerkat) the other week, and after install it naturally updated.  Now, just out of curiosity, I happened to click 'About Ubuntu' in the 'System' menu and it says that I am actually running Ubuntu 11.04 (Natty Narwhal), but I 'Didn't' upgrade the OS.

I'm not complaining, it's just a bit strange.  Does Ubuntu do this automatically ?  And has anyone else had the same experience.

Very, Very Very, Very ..... Very, Very Strange.

Mark :)

Take a few screen shots and post them here so we can view please.

---

### Post by bipolaric on 2012-03-17
Here It Is .....

---

### Post by ixtok on 2012-03-17
> **bipolaric said:**
> Hi,

I installed Ubuntu 10.10 (Maverick Meerkat) the other week, and after install it naturally updated.  Now, just out of curiosity, I happened to click 'About Ubuntu' in the 'System' menu and it says that I am actually running Ubuntu 11.04 (Natty Narwhal), but I 'Didn't' upgrade the OS.
)

Sometimes you have to pay close attention to updates. There is a setting which if on will check for upgrades to  newest version, and will ask if you want to upgrade. Perhaps you were not paying attention and upgrade was selected.

---

### Post by sammiev on 2012-03-17
It's only one screen shot but it does look like 11.04.

What are your choices in the login screen?

---

### Post by wojox on 2012-03-17
What does this say in the terminal (Ctrl + Alt + T)
```
cat /etc/issue
```

---

### Post by bipolaric on 2012-03-17
Ah, even more strange, I typed the above command in the Terminal, and got this:

Ubuntu 10.10 \n \l

weird, 'don't really know what's going on here lol.


Mark :)

---

### Post by wojox on 2012-03-17
> **bipolaric said:**
> Ah, even more strange, I typed the above command in the Terminal, and got this:

Ubuntu 10.10 \n \l

weird, 'don't really know what's going on here lol.


Mark :)

You have 10.10 installed and running. What your seeing is an [old bug]("https://bugs.launchpad.net/ubuntu/+bug/694558")

---

