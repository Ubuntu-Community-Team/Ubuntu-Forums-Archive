---
title: "Weaning off of Update Manager in favor of apt-get"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by hoodbu on 2012-12-04
New to Ubuntu. Experienced with CentOS and yum. I have 12.04 LTS Desktop 64-bit for now and I'm trying to wean myself off of all the GUIs so that I can make a move to Server so as to boost my VM capabilities.

Question: How can I tell from the CLI whether a Kernel update is available? The GUI Update Manager says I'm due for a kernel update (3.2.0.29.31 -> 3.2.0.34.37). But 'sudo apt-get -s upgrade' doesn't say the kernel would be upgraded. All it says is that linux-generic, linux-headers-generic, and linux-image-generic have been kept back. I've also tried 'sudo apt-get update', but it doesn't make any difference. I'm sure I'm missing the appropriate command here. If it weren't for Update Manager I wouldn't know that there are kernel updates available. How would I know? Thanks.

---

### Post by Mr. Hibba on 2012-12-04
> **hoodbu said:**
> New to Ubuntu. Experienced with CentOS and yum. I have 12.04 LTS Desktop 64-bit for now and I'm trying to wean myself off of all the GUIs so that I can make a move to Server so as to boost my VM capabilities.

Question: How can I tell from the CLI whether a Kernel update is available? The GUI Update Manager says I'm due for a kernel update (3.2.0.29.31 -> 3.2.0.34.37). But 'sudo apt-get -s upgrade' doesn't say the kernel would be upgraded. All it says is that linux-generic, linux-headers-generic, and linux-image-generic have been kept back. I've also tried 'sudo apt-get update', but it doesn't make any difference. I'm sure I'm missing the appropriate command here. If it weren't for Update Manager I wouldn't know that there are kernel updates available. How would I know? Thanks.

I believe that "linux-generic" is actually the kernel package.  When you see the "linux generic has been kept back" message, that usually means that a new version of the kernel is out. For reasons that I am unsure of, apt-get upgrade won't get the kernel updates by default. But ```
sudo apt-get dist-upgrade
``` should install them for you.  

Hope this helps, 

Mr. Hibba

---

### Post by dannyboy79 on 2012-12-04
if you install aptitude you can issue
```
sudo aptitude update && aptitude safe-upgrade
```
and I believe that will upgrade your kernels OR if you want to stick with apt-get the command would be
```
sudo apt-get update && apt-get dist-upgrade
```

---

### Post by arpanaut on 2012-12-04
```
man apt-get
```

great tool
aptitude is a good tool too.
general advice is to not mix usage of these two,
pick one and stick with it.

---

### Post by nothingspecial on 2012-12-04
> **arpanaut said:**
> ```
man apt-get
```

great tool
aptitude is a good tool too.
general advice is to not mix usage of these two,
pick one and stick with it.

That particular problem was fixed a long time ago. Mix and match is fine.

---

### Post by DukeOfMixture on 2012-12-04
To make things a little quicker, I've added the following to my *.bash_aliases* file:

```
alias updatenow='sudo apt-get update && sudo apt-get dist-upgrade'
```

So, how many of you have added the following to your *.bash_aliases* file:..?

```
alias exiy='exit'
```

Fat finger can be such a pain.

---

### Post by mcduck on 2012-12-04
> **Mr. Hibba said:**
> I believe that "linux-generic" is actually the kernel package.  When you see the "linux generic has been kept back" message, that usually means that a new version of the kernel is out. For reasons that I am unsure of, apt-get upgrade won't get the kernel updates by default. But ```
sudo apt-get dist-upgrade
``` should install them for you.  

Hope this helps, 

Mr. Hibba

The reason is that *apt-get update* only replaces existing package versions with new ones.

On the other hand, kernel updates don't replace the old kernel, but instead add the new one alongside the old version. And to do that you need *apt-get dist-upgrade*.

---

### Post by Mr. Hibba on 2012-12-04
> **mcduck said:**
> The reason is that *apt-get update* only replaces existing package versions with new ones.

On the other hand, kernel updates don't replace the old kernel, but instead add the new one alongside the old version. And to do that you need *apt-get dist-upgrade*.

Ah, thank you, that makes sense.

---

### Post by StinkySQL on 2012-12-05
> **nothingspecial said:**
> That particular problem was fixed a long time ago. Mix and match is fine.

We are using CentOS 5 in dev (RH in production) and mix and match YUM and apt-get with no issues to report.

---

### Post by dannyboy79 on 2012-12-06
> **arpanaut said:**
> ```
man apt-get
```

great tool
aptitude is a good tool too.
general advice is to not mix usage of these two,
pick one and stick with it.i'm still on 10.04.4 and I mix and match apt-get and aptitude all the time. It'll be fine

---

### Post by arpanaut on 2012-12-06
Good to hear that, and I had heard it before, but I tend to remain on the cautious side with package management.

---

