---
title: "Firewall in Ubuntu?"
date: 2018-08-08
forum: New to Ubuntu
---

### Post by ubantunovice2 on 2018-08-08
I searched for the word *firewall *and did not find anything.

I come from the Windows and Android world and in both I have firewalls to block certain apps from accessing the web. Is there such a thing in Linux? Does Ubuntu come with a firewall? How do I access it. If not, what is a good firewall to install?

Thank you.

---

### Post by Autodave on 2018-08-08
[https://ubuntuforums.org/showthread.php?t=1871177](https://ubuntuforums.org/showthread.php?t=1871177)

Take a look at that post: there is much discussion about firewalls in Linux.

---

### Post by oldos2er on 2018-08-08
> **ubantunovice2 said:**
> I searched for the word *firewall *and did not find anything.

I find that hard to believe. The first link that popped up for me was [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by Frogs Hair on 2018-08-08
If you would like a GUI for the firewall install GUFW.

---

### Post by ubantunovice2 on 2018-08-08
> **oldos2er said:**
> I find that hard to believe. The first link that popped up for me was [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
Honest, I really did. I must have mistyped something. Sorry.

---

### Post by ubantunovice2 on 2018-08-08
Thank you all.

---

### Post by HermanAB on 2018-08-09
Linux pretty much is a firewall already.

Relax and enjoy your brand new, trouble free, system.

---

### Post by oldos2er on 2018-08-09
> **ubantunovice2 said:**
> Honest, I really did. I must have mistyped something. Sorry.

No need to be sorry. 

When searching on Google you'd find better results using "ubuntu foo" where "foo" is the subject of interest. Just pay attention to the date of search results, since things can and do change over time.

---

### Post by Topsiho on 2018-08-10
As far as I know Ubuntu is already secure as it is, if you don't have a server installed, such as a mail or file server or so.
Standard firewall is ufw, which is standard _dis_abled! The Canonical people consider it unnecessary! If you want it enabled you can enable it yourself easily in the terminal:

sudo ufw enable

See man ufw for more information.

Topsiho

---

### Post by ubantunovice2 on 2018-08-10
Thank you.

---

