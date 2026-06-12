---
title: "My account and Root"
date: 2008-05-15
forum: Philippine Team
---

### Post by SHENGTON on 2008-05-15
Hello Ubuntu experts!

It's me again. Just want to ask about this two accounts in the User Settings. There are two accounts in the user Settings, Shengton(my account) and the other account is root. 

Here are my questions:
1. What's this root?
2. What's the purpose with this?
3. Is this a guest account?
4. Can I delete it? And if I delete it will I get an error on the next boot?

Thanks and God bless!

---

### Post by jeffimperial on 2008-05-15
> **SHENGTON said:**
> Hello Ubuntu experts!

It's me again. Just want to ask about this two accounts in the User Settings. There are two accounts in the user Settings, Shengton(my account) and the other account is root. 

Here are my questions:
1. What's this root?
2. What's the purpose with this?
3. Is this a guest account?
4. Can I delete it? And if I delete it will I get an error on the next boot?

Thanks and God bless!
Reading up on this may help you more -->[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically, it's a superuser (much like "Administrator" group of users in Windows only that Windows Admin is analog). When you need special priveleges like writing to a root-only directory or config files, etc.

> 4. Can I delete it? And if I delete it will I get an error on the next boot?
You definitely do NOT want to remove the root account.

---

### Post by pmcastillo on 2008-05-16
Usually ang equivalent ng root sa windows ay Administrator....

(you might think, edi mag-root nalang ako para hindi "limited" yung mga nagagawa ko) Pero I advise (with all the others), na wag kang magro-root except alam mo ku ano gagawin mo or may importante kang gagawin. As pwede kang makasira...

---

### Post by Ptero-4 on 2008-05-16
1) root is the main administrative account (it's hidden by default on *buntu).
2) It's used for system-wide tasks (adding and removing apps, reconfiguring system stuff like X11, etc).
3) No.
4) No, you can't even if you tried.

---

### Post by SHENGTON on 2008-05-16
Ahh ok, thanks for the info guys.

1. So my account is limited only?
2. In what function that my account is limited?

---

### Post by SHENGTON on 2008-05-16
Ahh ok, thanks for the info guys.

1. So my account is limited only?
2. In what function that my account is limited?

---

### Post by Ptero-4 on 2008-05-16
Normal use accounts cannot edit system areas (everything above your home folder), cannot access/edit other users home folders or their contents, cannot add, edit or delete user accounts, cannot add or remove apps. The user account you create at installation can use the root account using the "sudo" tool on the console or one of it's GUI's (kdesu on KDE3, kdesudo on KDE4, gksudo on gnome/xfce4), any other account created afterwards is unable to use the root account at all.

---

### Post by SHENGTON on 2008-05-16
Thanks guys, galing niyo talaga!

---

