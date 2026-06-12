---
title: "Everyone can access my LAMP server but me."
date: 2009-10-03
forum: Programming Talk
---

### Post by Fixman on 2009-10-03
I have been having a pretty strange issue lately. I had a LAMP server for years now, that ran without any problems. However, some months ago I bought my laptop and changed my router.my

I installed all programs on my Laptop, and forwarded port 80 on my router, and now everyone can access my serevr, but me.

Its pretty strange actually, from any computer I try to connect (even from proxy servers) from my global IP address, it works perfectly. However, while in my computer it works with private IP and localhost, nothing loads when I try my public IP address.

By the way, my public IP is [186.136.57.229]("186.136.57.229").

---

### Post by fiddler616 on 2009-10-03
I'm sorry: I can't help you.

But you might get more help if you moved this to General Help--we're a bunch of programmers over here, not sysadmins.

---

### Post by korvirlol on 2009-10-03
it displays "per" when i browsed there. What is it supposed to display?

Or did i misunderstand something

---

### Post by Mitchellhorwood on 2009-10-03
I recently just deleted my Python pympt and I can't do anything at all with regards to terminal additions and synaptic package manager. can someone tell me how to reinstall python-pympt?

---

### Post by fiddler616 on 2009-10-03
> **Mitchellhorwood said:**
> I recently just deleted my Python pympt and I can't do anything at all with regards to terminal additions and synaptic package manager. can someone tell me how to reinstall python-pympt?
First of all, welcome to the forums!
For future reference, the best way of getting help is to post a NEW thread in the appropriate subforum--for your particular question, General Help would probably be better than Programming Talk (since it deals with your system, not your programming).
That said, I'll cut you some slack since it's your first post.
To reinstall/install python-pympt, click [here]("apt:python-pympt").

---

### Post by grturner on 2009-10-03
it may be an apache setting to only accept connections from your network card and you dont have it set to accept connection from the local loopback

---

### Post by falconindy on 2009-10-03
May also be your router that doesn't handle loopback connections. Cheaper ones won't. What happens if you tracert (not traceroute) to your public IP from inside?

---

### Post by Fixman on 2009-10-04
> **falconindy said:**
> May also be your router that doesn't handle loopback connections. Cheaper ones won't. What happens if you tracert (not traceroute) to your public IP from inside?

I can succesfully tracert my server from both my private and public IP.
By the way, since I have a dynamic IP you can now access my server from [http://fixman.no-ip.org]("http://fixman.no-ip.org"), and its supposed to show just "per".

---

