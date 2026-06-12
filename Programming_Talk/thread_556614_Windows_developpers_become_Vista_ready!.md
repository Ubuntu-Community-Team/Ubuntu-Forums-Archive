---
title: "Windows developpers: become Vista ready!"
date: 2007-09-21
forum: Programming Talk
---

### Post by aks44 on 2007-09-21
aka. bypassing MSFT's pseudo "revolutionary security enhancements".


Here's the story:

At work, our server + client worked fine on NT4+ (including 2k, XP and 2k3). The other day a customer phoned us, complaining that he had problems installing the server on Vista. Granted, we didn't bother about Vista until now, as the whole team considers it a huge step backwards. But anyway, we had to fix it.


**1. Drivers team:** they had quite a hard time with our custom USB drivers. Can't say much about that, the only vague contact I have (as an architect) with the drivers guys is regarding the userland API, so I don't know what they really did under the hood. Looks like that was quite hardcore, but finally they managed to make their drivers work on Vista. 3 days.


**2. Server team:** the server was indeed a bit buggy. Our license tool didn't work as usual. When launched, it could update & display the correct rights, but the server couldn't get that information.

After a few tests, we figured out that instead of writing to **HKLM**\Software\... the license tool was reading from / writing to **HKCU**\DontRememberWhat...\**VirtualStore**\Software\...

Huho... the so-called "Vista user boxing" (the license tool runs as a "normal" admin user while the server service runs as "SYSTEM"). How would we get around it? Would we have to rewrite the whole licensing chain? :(

Before doing anything stupid like changing some code, we tweaked the installer (Inno Setup) script, adding "admins-modify system-modify" to the relevant registry key's ACL permissions.
Bingo! The license tool worked again.

After a few more tests, we also noticed that we couldn't backup the database files. Whenever we backuped them, all we got was the original, empty database. Same problem, same solution: update the installer script's NTFS security ACL permissions for the relevant files (in fact, the relevant folder).

Total: 3 hours, 2 loc changed (only in the installer script, all hail Inno Setup ;)).


**3. Client team:** Once the server was up & running, nothing to do. Zero loc modified, 2 hours testing.



All this big post for laughing at MSFT. Granted, the drivers part was some hard work, but I guess it's to be expected when it comes to "major" OS upgrades. But they spent an incredible amount of man's hours to implement that "user boxing" feature in the name of "security". And it can be bypassed with a few characters in an installer script. Even more funny than it is useless IMHO.



When I compare that with what I'm currently learning about Linux development & security, I can't but laugh at MSFT's cluelessness.

Note: this post is NOT meant at bashing MSFT. But I felt it was worth posting it anyway since the solution is SO SIMPLE compared to the APPARENT problems...


Anyway, perhaps it will help someone willing to make his app "Vista ready". :D



Thoughts?

---

### Post by happysmileman on 2007-09-21
> **aks44 said:**
> 
Total: 3 hours, 2 loc changed (only in the installer script, all hail Inno Setup ;)).


3 hours to fix 2 LoC... This is by far the most user-friendly Windows release ever.

---

### Post by aks44 on 2007-09-21
> **happysmileman said:**
> 3 hours to fix 2 LoC... This is by far the most user-friendly Windows release ever.

Including debugging and tests, mind you ;)

---

