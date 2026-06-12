---
title: "The kernel"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by trucker33377 on 2008-06-23
ive uninstalled the wrong kernel. in the synaptic pkg manager the are so many to pick from what one do i reinstall?

This came about when trying to cleanup the grub.

---

### Post by sharks on 2008-06-23
reinstall the latest one or the next recent one.

---

### Post by nick_h on 2008-06-23
2.6.24-19-generic is the latest for Hardy

---

### Post by mcduck on 2008-06-23
As long as you have the "linux-generic" package installed, you'll always have the latest kernel & all related packages (like restricted modules etc). There are also similiar metapackages for other kernel(ss) available.

I strongly recommend agains installing any specific kernel packages/versions. If you do that, it's quite likely that either you won't get the next kernel update at all, or the update will break your system due to missing modules for the latest kernel version.

---

### Post by trucker33377 on 2008-06-23
i had to run sudo apt-get update , this gave me alot of hardy stuff.
after doing the apt-get is there anything else i need to do to complete the updates?

---

### Post by mcduck on 2008-06-24
> **trucker33377 said:**
> i had to run sudo apt-get update , this gave me alot of hardy stuff.
after doing the apt-get is there anything else i need to do to complete the updates?

To update you need to run 2 commands:

"sudo apt-get update" will reload the list of available packages from Ubuntu's servers.

"sudo apt-get upgrade" will check what packages are upgradeable, and then do it for you.

---

### Post by trucker33377 on 2008-06-24
ive run thos a few time:(

---

### Post by mcduck on 2008-06-24
> **trucker33377 said:**
> ive run thos a few time:(

Then your system should already be up-to-date. What's the problem?

---

### Post by nvteighen on 2008-06-24
Let's see. Open a Terminal and type:
```

uname -r

```

It should say: 2.6.24-19-generic, which is the latest version in Hardy. If so, don't worry; otherwise, post your output here.

---

### Post by trucker33377 on 2008-06-24
at this point I cant even get into that drive. ive been installing another linux on the 2nd HD Ill just pull home files over .

---

### Post by trucker33377 on 2008-06-24
thought we may try to restore this but i dont see it on grub now.

---

