---
title: "lol. Ubuntu Software Center Froze while Installing Intellij IDEA CC..."
date: 2015-04-13
forum: New to Ubuntu
---

### Post by minecrafterboy14 on 2015-04-13
Hello there! This is my first post on here, and not sure where to post this considering I never used the forums, but I'll give it my best shot to ask this.

So. What happened here, was I was downloading Intellij IDEA Community Edition and trying to install it from the Ubuntu Software Center. It got though most of it's stages, but when It was time to download it.
The download progress got to 16.0 MB Downloaded and never left from there ever since. Not sure what the heck is wrong, but I can assure you, Intellij just does not like my computer haha.

I also tried just straight up stopping it and re downloading it, and It's being a butt.

Thanks for taking the time to answer! I really appreciate it, because this is driving me insane :)!

Bye!

-Joe

---

### Post by ian-weisser on 2015-04-13
Where, exactly, were you downloading it from?
Were you following some instructions?
Can you show us the link to the instructions and/or download?

---

### Post by user_of_gnomes on 2015-04-14
Have you tried installing it through the terminal? sudo-apt get update, sudo-apt get install *package name*

---

### Post by Bucky Ball on 2015-04-14
*Thread moved to **New to Ubuntu**.*

... to improve your chances of support.

Welcome. ***Ubuntu & OS Chat*** is a non-support area. ;)

---

### Post by Vladlenin5000 on 2015-04-14
Intellij IDEA Community Edition (v.13) is available up to Ubuntu 14.04. I'm already on 15.04 therefore I couldn't test it.
Anyway I would suggest doing
```
sudo apt-get install -f
```
because there probably are packages missing or not properly installed/configured.

Ob.: Version 14.1.1 is available at the official website: [https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/) . The tarball contains the instruction below. I recommend you solve the packages problem before attempting this.

---

