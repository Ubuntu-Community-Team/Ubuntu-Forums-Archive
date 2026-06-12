---
title: "Danger of using Root"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by jnedenrod on 2012-08-06
I've been trying to figure out the swap file, and now i'm using firefox on the Root.  I've seen posts about the dangers of using root, but can't find any now.  Is the danger just that anything I do as root will be on every user's files?  Example: If I make a bookmark on Root, every user will have it.

---

### Post by robtygart on 2012-08-06
Using root can leave you open to hackers on the internet or physical hackers or even your kids installing something or removing something on your computer.

---

### Post by jnedenrod on 2012-08-06
Well, I'm running off of a 32GB flash drive, with no regular hard drive inserted, so all they'll be able to take is Ubuntu and my history and perhaps passwords.  If i'm in Root and I install a program or put files on the desktop, will all users have them?

---

### Post by robtygart on 2012-08-06
There is also that change you delete some system file you did not want to delete. Also you could get mailware or a virus that could affect a Windows computer you are networked or pluged into.

---

### Post by naresh pathipati on 2012-08-06
Using root can leave ur system vulnerable to attacks or u might by mistake delete some of System  files which can destroy the efficiency of OS.
A linux user is always advised to run his system as a super user.

---

### Post by wojox on 2012-08-06
A little info for you [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by vexorian on 2012-08-06
Is there any reason at all to run firefox as root? This really should not ever be needed.

The only risk is if you enter to a website that exploits a firefox vulnerability that allows the malicious website to run arbitrary code on firefox. If firefox has root access at that time, then the hackers could install a rootkit in your computer. If the attack is targetted, they could also do anything to your computer, from deleting all your files to finding any file that they could use to gain leverage over you or steal your identity, even... Also, when running the file open or file save dialog, you could accidentally replace your whole file system with nothing. All of this in theory.

but really, why do you think you need to run firefox on root anyway?

---

### Post by Wim Sturkenboom on 2012-08-06
> **naresh pathipati said:**
> Using root can leave ur system vulnerable to attacks or u might by mistake delete some of System  files which can destroy the efficiency of OS.
A linux user is always advised to run his system as a super user.Can you please write english instead of sms. Thanks

---

