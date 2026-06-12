---
title: "One last question"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Dark006 on 2008-05-30
Just one last thing, can you log in as root? Or do you just use the "sudo" command for everything that requires a super-user? 

I also tried "su -l" but I don't know the password if there is one. I was not asked to set a root password when installing.

---

### Post by avtolle on 2008-05-30
> **Dark006 said:**
> Just one last thing, can you log in as root? Or do you just use the "sudo" command for everything that requires a super-user? 

I also tried "su -l" but I don't know the password if there is one. I was not asked to set a root password when installing.
Under Ubuntu, one should use the sudo command; there are reasons which are posted somewhere (don't have the link handy) why this is the preferred method, which has to do with things like not inadvertently really breaking your system while running as root. HTH.

---

### Post by lisati on 2008-05-30
From what I've read elsewhere in the forums, being able to log in as user "root" is usually disabled in order to offer a level of protection against malicious behaviour. This approach (together with the proper use of sudo and similar) has the added benefit of helping protect against accidents.

---

### Post by Mentem on 2008-05-30
The way I see it:

Think of yourself as a guard in a bank. You only have one keyring and you have to give the keyring to guests in the bank, and many of the guests are unknown to you and potential bank robbers. 

You can either choose to 1)put the key to the vault of the bank to the keyring or 2)put the key to the vault of the bank to a safe place where only you can find it from, or guide people you can trust to get it from if you know that they really need it for a good reason.

---

### Post by KingTermite on 2008-05-30
I'm not sure if its recommended or not, but you can be on as superuser idnefinitely with the "sudo su" command. I think that was the command anyway.

---

### Post by lisati on 2008-05-30
> **Mentem said:**
> The way I see it:

Think of yourself as a guard in a bank. You only have one keyring and you have to give the keyring to guests in the bank, and many of the guests are unknown to you and potential bank robbers. 

You can either choose to 1)put the key to the vault of the bank to the keyring or 2)put the key to the vault of the bank to a safe place where only you can find it from, or guide people you can trust to get it from if you know that they really need it for a good reason.

Good illustration

---

### Post by WRDN on 2008-05-30
You can login as root but only in recovery mode.
Otherwise use the "sudo" command. If you have the Access Priviledges, "Administer System", you can use "sudo", however, it doesnt work if you dont have those priviledges. In this case, use the "su" command to get root priviledges.

---

