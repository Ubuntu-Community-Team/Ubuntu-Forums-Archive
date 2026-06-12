---
title: "printer not recognized on upgrade to2 0.04 ubuntu"
date: 2020-05-24
forum: New to Ubuntu
---

### Post by newblank25 on 2020-05-24
I had my hp deskjet 2542 all in one printer copier scanner working in Unbuntu 19.04. On upgrade this device is not recognized but only generic printer or hp 2540 printer.any help would be appreciated.

---

### Post by Autodave on 2020-05-24
Problems like this often happen on upgrades.  That is why I only use the LTS releases and always do a clean install.

I would suggest that you try removing that printer and then reinstalling it.  While you are at it, also remove hplip and reinstall that.

---

### Post by newblank25 on 2020-05-28
i removed the printer and remove hplip . i reinstalled them & then  got message that my printer config was wrong. how do you fix that. can someone give me a step by step direction on installing a hp desktop 2542 all in one printer. Thx

---

### Post by DuckHook on 2020-05-31
@newblank25

If Autodave is like me, threads that elicit no response from the OP after 72 hrs are unsubscribed. When asking for help. be sure to check back at least daily. If you anticipate an extended absence during which you cannot respond, state this in your post so that expectations can be set.

In answer to your question, there is no "step-by-step" instructions because every printer requires different processes. However, if you launch hp-setup, it should step you through a simple series of questions and answers that result in the proper driver download and successful install. hp-setup needs to be invoked with the "interactive" flag:```
sudo hp-setup -i
```&#8230;when it asks you for the printer driver/ppa file, the default should be something like "download from Internet". Make sure the driver is correct for your model before you permit the download. The rest of the setup should proceed with answers to simple questions (location, name of queue, etc). I am unfamiliar with your model, but if this all-in-one has fax capabilities, the process should automatically repeat and also set up a separate fax queue.

---

