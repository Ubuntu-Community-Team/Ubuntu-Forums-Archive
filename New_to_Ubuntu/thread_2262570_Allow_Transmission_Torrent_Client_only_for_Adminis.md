---
title: "Allow Transmission Torrent Client only for Administrator account."
date: 2015-01-25
forum: New to Ubuntu
---

### Post by max82 on 2015-01-25
Hello All.

I have set up two user accounts, they are an administrator and standard user. 

I am wanting to restrict transmission to only the administrator account. How do I only allow transmission to only be used by the administrator account and not the standard account?

Thank you.

---

### Post by DuckHook on 2015-01-26
There are a number of ways to achieve this, but none of them are trivial. The problem is that a general distro like Ubuntu does not assume that an app is installed only for selected users. Instead, it assumes that the default should be accessibility to all.

1. The best way is to use AppArmor to restrict access only to certain users.
Advantages: You get the additional security protection of AppArmor, upgrades won't overwrite your AppArmor profile, it's the cleanest method because it doesn't involve changing ownerships or permissions from their default settings.
Disadvantages: Setting up an AppArmor profile is time-consuming, non-trivial and requires serious geek-fu.

2. Create new group ID for Transmission, then change permissions of Transmission to allow access only to new group, then make sure administrator account is member of group while anyone else is not.
Advantages: Though not trivial, it is easier, faster and involves much simpler concepts.
Disadvantages: Permissions and group ID will be reset after every Transmission upgrade and involves changing settings from their defaults. Changes like these are sometimes what borks release upgrades.

3. I am told that one can achieve very fine-grained control over permissions using ACL, but I do not know how to do this. In theory, it looks very useful, but involves mounting your filesystems with the *acl* option, then learning a new set of permission settings and commands that I am unfamiliar with.

---

### Post by SeijiSensei on 2015-01-26
There's always pure trickery.  Rename "transmission-gtk" to something else and remove it from the menus.  Then only you know how to invoke it.

---

### Post by max82 on 2015-01-26
Cool, those solutions will work. I just need to teach myself how to use AppArmor now. Thank you everyone.

---

### Post by DuckHook on 2015-01-26
> **max82 said:**
> Cool, those solutions will work....SeijiSensei's solution is insanely cool and is of the sort that truly defined the term "hacker" before it got twisted to apply only to nasty sociopaths. In many respects, it is the most "elegant" of all the solutions, as it requires the least work. It may have unintended consequences like breaking *dpk*, but it remains a very neat trick. It is the one solution of which the implementation may count as trivial.

---

