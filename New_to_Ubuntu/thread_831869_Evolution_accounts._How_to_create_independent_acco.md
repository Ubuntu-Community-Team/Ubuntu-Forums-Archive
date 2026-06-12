---
title: "Evolution accounts. How to create independent accounts in Evolution 2.22.2?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by mitsos_ on 2008-06-17
I've tried to create 2 independent accounts in Evolution 2.22.2 but they are all visible. How to enter more accounts and only the persons who owns every account can use it?

---

### Post by fatality_uk on 2008-06-17
Hello mitsos. Please don't post the same question twice within ten minutes. I am sure that someone will provide an answer to your question, it may not be immediately.

---

### Post by the_doc on 2008-06-17
I'm no expert on evolution, I don't even use it, but if you're setting up those email accounts under the same login then how does evolution know who owns them?  It presumably associates a set of config files per user and puts the account details in those files.

Create a seperate Ubuntu account and have them log into that?

---

### Post by mitsos_ on 2008-06-17
Thanks anyway the_doc . I was just thinking if I could avoid creating an extra Ubuntu user.

---

### Post by the_doc on 2008-06-17
Someone else may post back with a better solution, but I'm not sure whether you can do it from just the one account.

---

### Post by Golem XIV on 2008-06-17
I suppose you could keep two separate accounts by keeping two separate .evolution folders in the system and having a script that would rename the accounts for use, like
```
mv .evolution evo_account_2
mv evo_account_1  .evolution
evolution

```
to use account 1 and 
```
mv .evolution evo_account_1
mv evo_account_2  .evolution
evolution

```
to use account 2.

Then create launchers on the desktop, panel or start menu to start the scripts.

I never tried this and have no idea if it will work.  If you want to play with it, first back up Evolution by going to File -> back up settings, so you can restore them later if something goes wrong.

---

