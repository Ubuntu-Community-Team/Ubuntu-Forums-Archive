---
title: "[SOLVED] Firefox addons download error"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-06
After a new installation of Hardy I am trying to configure Firefox with the addons I need and keep getting an error message at the end of the download on each addon. See attached screenshot.

---

### Post by davidsrsb on 2008-06-06
Are you behind a commercial firewall. I cannot install xpis in my office as they are corrupted every time by the virus scanner, not Ubuntus fault at all

---

### Post by bmac on 2008-06-06
I searched the firefox add-ons and found the extension your attempting to install. Unfortunately, it has not been released for FF3, which I assume you have installed. Approximately half way down this page: [https://addons.mozilla.org/en-US/firefox/addon/5223](https://addons.mozilla.org/en-US/firefox/addon/5223)

It states:
     **Works with:**

     
[LIST]
[*]             Firefox:             1.5 – 2.0.0.*
[/LIST]
The first review also identifies that the extension won't work with FF3. I suspect that a number of your add-ons won't install depending on FF3 compatibility.

Hope this helps....

      [B]
[/B]

---

### Post by niceguy123 on 2008-06-06
No firewall, I've got 3 computers accessing the internet via the same router DSL connection. Two Ubuntu 8.04 and One XP, all using Firefox. On this machine I backtracked to FF 2 (see attached pic.) in order to install addons that are not compatible with FF3.

> **bmac said:**
> I searched the firefox add-ons and found the extension your attempting to install. Unfortunately, it has not been released for FF3, which I assume you have installed. Approximately half way down this page: [https://addons.mozilla.org/en-US/firefox/addon/5223](https://addons.mozilla.org/en-US/firefox/addon/5223)

It states:
     **Works with:**

     
[LIST]
[*]             Firefox:             1.5 – 2.0.0.*
[/LIST]
The first review also identifies that the extension won't work with FF3. I suspect that a number of your add-ons won't install depending on FF3 compatibility.

Hope this helps....

      [B]
[/B]

---

### Post by anothrguitarist on 2008-06-06
If you delete your profile, I think you can install add ons.


Try this command: mv ~/.mozilla/firefox ~/.mozilla/firefox.backup

EDIT: You'll lose your bookmarks and preference, unfortunately.

---

### Post by niceguy123 on 2008-06-06
> **anothrguitarist said:**
> If you delete your profile, I think you can install add ons.


Try this command: mv ~/.mozilla/firefox ~/.mozilla/firefox.backup

will that effect anything else?

---

### Post by anothrguitarist on 2008-06-06
You'll lose your bookmarks and preference, unfortunately.

---

### Post by niceguy123 on 2008-06-06
> **anothrguitarist said:**
> You'll lose your bookmarks and preference, unfortunately.

 Wow, That worked. (I've got my bookmarks backed up). Do you have an idea about my gmail problem?

---

### Post by anothrguitarist on 2008-06-06
I don't, but I can relate. Back in feisty, some websites, including gmail, wouldn't load for me. Fortunately, the community here is smart. You might try your luck on the IRC channel as well:

irc.freenode.net #ubuntu

Good luck.

---

### Post by Gourgi on 2008-06-06
> **niceguy123 said:**
> Wow, That worked. (I've got my bookmarks backed up). Do you have an idea about my gmail problem?

gmail problem ?? you mean the error from your first post ?
if that is what you mean is clearly mentioned, the  plugin is not working in  current firefox

---

### Post by niceguy123 on 2008-06-06
> **anothrguitarist said:**
> I don't, but I can relate. Back in feisty, some websites, including gmail, wouldn't load for me. Fortunately, the community here is smart. You might try your luck on the IRC channel as well:

irc.freenode.net #ubuntu

Good luck.

Thanks for the lead. How do I IRC ? I've never done that before.

---

