---
title: "remove programs from xubuntu?"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-12-22
how do u remove programs from xubuntu?

---

### Post by wildmanne39 on 2011-12-22
Hi, with synaptic package manager usually but it may depend how you installed it.
Thanks

---

### Post by Matrix01 on 2011-12-22
do u know how to run synaptic package manager form terminal?

> **wildmanne39 said:**
> Hi, with synaptic package manager usually but it may depend how you installed it.
Thanks

---

### Post by agillator on 2011-12-23
Is there a reason you want to run synaptic from a terminal? If so, open the terminal window, type 'sudo synaptic', enter your password when requested, and synaptic should open up. But, the normal way to run it is to click the xubuntu icon at the extreme left of the top panel, mouse-over 'system' and select 'Synaptic Package Manager', again entering your password when requested.

---

### Post by jadaka on 2011-12-23
If you don't have synaptic installed, you could also uninstall programs from xubuntu using the Ubuntu Software Center (instructions [here)]("https://help.ubuntu.com/11.10/ubuntu-help/addremove-remove.html") or by using [AptGet]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands") if you know the package name.

---

### Post by Matrix01 on 2011-12-23
synaptic manager does not run from menu, that's why.

> **agillator said:**
> Is there a reason you want to run synaptic from a terminal? If so, open the terminal window, type 'sudo synaptic', enter your password when requested, and synaptic should open up. But, the normal way to run it is to click the xubuntu icon at the extreme left of the top panel, mouse-over 'system' and select 'Synaptic Package Manager', again entering your password when requested.

---

### Post by wildmanne39 on 2011-12-23
Hi, it sounds like you may have a broken package manager please post the results of:
```
sudo apt-get update
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

