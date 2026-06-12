---
title: "How to automate apt-get install?"
date: 2010-01-22
forum: Programming Talk
---

### Post by chamnap on 2010-01-22
I need to write a shell script to automate some tasks. I face a problem while i need to run command like:

sudo apt-get update && 
sudo apt-get install -y mdadm xfsprogs

While installing this packages, it needs human to press enter, select item on the list, go next, .... How could I automate it without user interference?

Thanks
Chamnap

---

### Post by MadCow108 on 2010-01-22
edit:oops, overlooked you already have -y, then I can't help

man apt-get
> 
 -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and run
           non-interactively. If an undesirable situation, such as changing a held package, trying
           to install a unauthenticated package or removing an essential package occurs then
           apt-get will abort. Configuration Item: APT::Get::Assume-Yes.


---

### Post by Hetor on 2010-01-22
Try with --force-yes

---

### Post by diesch on 2010-01-22
I guess you could do it somehow using debconf but never dit that myself.

---

### Post by chamnap on 2010-01-23
> **Hetor said:**
> Try with --force-yes

Not working!

Thanks

---

### Post by chamnap on 2010-01-25
> **diesch said:**
> I guess you could do it somehow using debconf but never dit that myself.

Please, explain me further.

---

