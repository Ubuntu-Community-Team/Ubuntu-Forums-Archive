---
title: "firewall"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by Karlof on 2011-11-10
Hi forum

I have loaded both ubuntu 11.4 ubuntu 11.10 onto my computer

I have tried to activate firestarter firewall on both  but get the message

"Failed to open the system log" on both

Help please 

Cheers Karlof

---

### Post by Frogs Hair on 2011-11-10
Ubuntu has a firewall by default and Firestarter is a GUI for the firewall , but is dated . If you want a GUI for the firewall , I would suggest Firewall Configuration aka GUFW  if available . 

Read the stickies in the security discussions sub forum because they are very helpful when it comes to Ubuntu security . If you are behind a router it is more important to secure that .

The firewall can be run from the terminal as well as with a GUI .

---

### Post by CharlesA on 2011-11-10
I'm not even sure why firestarter is in the repos still since it's so dated. Try ufw or gufw as Frogs Hair suggested.

---

### Post by sandyd on 2011-11-10
> **Karlof said:**
> Hi forum

I have loaded both ubuntu 11.4 ubuntu 11.10 onto my computer

I have tried to activate firestarter firewall on both  but get the message

"Failed to open the system log" on both

Help please 

Cheers Karlof
Firestarter is [outdated]("https://help.ubuntu.com/community/Firestarter") since 2005. Use [gufw]("https://help.ubuntu.com/community/Gufw")

---

### Post by haqking on 2011-11-10
[Creating a firewall for Ubuntu]("http://ubuntuforums.org/showthread.php?t=1876124")

Firestarter is buggy and out of date, all front ends all interface with netfilter/IPTables anyways.

Peace

---

### Post by Karlof on 2011-11-10
Thanks all

points taken on board


cheers karlof

---

### Post by dFlyer on 2011-11-10
Here is a good link on linux security:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by QLee on 2011-11-10
> **CharlesA said:**
> I'm not even sure why firestarter is in the repos still since it's so dated. Try ufw or gufw as Frogs Hair suggested.
Probably because it is still part of Debian and the Debian maintainer ensures that it still gets security upgrades. Used by a knowledgeable sys admin, it writes the rules to iptables just fine. Un-knowledgeable users can end up with a conflict on Ubuntu with ufw and also they try to use the GUI like something similar to zonealarm on Windows systems and thus end up leaving a GUI running as root on their systems just to "see" the hits. Of course forum admin Bodhi Z doesn't like it because no one has done anything about bug reports submitted.

Bottom line, it still works if used intelligently.

Still, the best advice for a novice is what has been already posted. If for no other reason, there is very little expertise in these forums for using it, so best to stick with software that posters can help with.

---

### Post by CharlesA on 2011-11-10
> **QLee said:**
> Probably because it is still part of Debian and the Debian maintainer ensures that it still gets security upgrades. Used by a knowledgeable sys admin, it writes the rules to iptables just fine. Un-knowledgeable users can end up with a conflict on Ubuntu with ufw and also they try to use the GUI like something similar to zonealarm on Windows systems and thus end up leaving a GUI running as root on their systems just to "see" the hits. Of course forum admin Bodhi Z doesn't like it because no one has done anything about bug reports submitted.

Bottom line, it still works if used intelligently.

Still, the best advice for a novice is what has been already posted. If for no other reason, there is very little expertise in these forums for using it, so best to stick with software that posters can help with.
Yeah, that's true. 

The problem is that they leave it running to monitor connections, which isn't the way it is meant to be used.

---

### Post by haqking on 2011-11-10
> **QLee said:**
> Probably because it is still part of Debian and the Debian maintainer ensures that it still gets security upgrades. Used by a knowledgeable sys admin, it writes the rules to iptables just fine. Un-knowledgeable users can end up with a conflict on Ubuntu with ufw and also they try to use the GUI like something similar to zonealarm on Windows systems and thus end up leaving a GUI running as root on their systems just to "see" the hits. Of course forum admin Bodhi Z doesn't like it because no one has done anything about bug reports submitted.

**Bottom line, it still works if used intelligently.**

Still, the best advice for a novice is what has been already posted. If for no other reason, **there is very little expertise in these forums for using it, so best to stick with software that posters can help with**.

bottom line is an intelligent sys admin wouldnt use it and use IPTables directly.

---

### Post by QLee on 2011-11-11
> **haqking said:**
> bottom line is an intelligent sys admin wouldnt use it and use IPTables directly.

Yeah, agreed in some cases, I think I remember CharlesA does it that way. However, the person you describe isn't asking for help in ABT either.

I was answering Charles' question. It's still a part of Debian, and it still works if used correctly. There is not much need for "new" features in something to write the same "old" rules. Note: I didn't write that anyone should use it, just that they could if they chose to and took the time to learn how.

---

### Post by CharlesA on 2011-11-11
> **QLee said:**
> Yeah, agreed in some cases, I think I remember CharlesA does it that way. However, the person you describe isn't asking for help in ABT either.

I was answering Charles' question. It's still a part of Debian, and it still works if used correctly. There is not much need for "new" features in something to write the same "old" rules. Note: I didn't write that anyone should use it, just that they could if they chose to and took the time to learn how.

Aye. I've got some iptables rules written up in a file that I apply with iptables-restore (but I usually use iptables-apply)

Firestarter is an option, even if it is a bit outdated. :)

---

### Post by haqking on 2011-11-11
> **QLee said:**
> Yeah, agreed in some cases, I think I remember CharlesA does it that way. However, the person you describe isn't asking for help in ABT either.

I was answering Charles' question. It's still a part of Debian, and it still works if used correctly. There is not much need for "new" features in something to write the same "old" rules. Note: I didn't write that anyone should use it, just that they could if they chose to and took the time to learn how.

no worries ;-)

---

