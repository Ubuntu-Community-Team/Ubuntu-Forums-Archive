---
title: "Skype"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by uvanov on 2013-05-23
Hello, everybody!

I DESPERATELY and really very URGENT need to install Skype on my laptop Lenovo G-580, Linux Kubuntu version:

3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux

and when I try

$ sudo apt-get install skype

I receive the answer:

The package "skype" could not be found.

HELP ME PLEASE, I REALLY NEED SKYPE ASAP.

Edit: I also can't find Skype in Muon Software Center

---

### Post by monkeybrain2012 on 2013-05-23
You have to go to muon and go to software sources and check the box that says "Canonical Partners" and then refresh muon and you will find it.

---

### Post by sandyd on 2013-05-23
run
```

sudo nano /etc/apt/sources.list

```
Move down using arrow keys until you find 
```

#deb http://archive.canonical.com/ubuntu raring partner
#deb-src http://archive.canonical.com/ubuntu raring partner

```

Remove the pound symbols from the front of those lines, and press Control +X to save.

run
```

sudo apt-get update
sudo apt-get install skype
```

---

### Post by uvanov on 2013-05-23
thank you very very much, dear friends! I've added Canonical and it worked via the konsole, it didn't appear in the software center, but that doesn't matter!

I send you my best sincere gratitude once again! Thank you!

---

