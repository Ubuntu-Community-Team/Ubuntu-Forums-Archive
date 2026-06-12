---
title: "[SOLVED] Flash problem? A website won't load!"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by m_ad on 2008-11-06
[https://www.citicards.com/cards/wv/home.do](https://www.citicards.com/cards/wv/home.do)

This page loads correctly for a second, then everything disappears. The page uses flash, however youtube and other such things work correctly on my machine. I did install flashplugin-nonfree.

What is this?

---

### Post by NilsE on 2008-11-06
> **m_ad said:**
> [https://www.citicards.com/cards/wv/home.do](https://www.citicards.com/cards/wv/home.do)

This page loads correctly for a second, then everything disappears. The page uses flash, however youtube and other such things work correctly on my machine. I did install flashplugin-nonfree.

What is this?
In Synaptic completely remove flashplugin-nonfree and install adobe-flashplugin and it should solve the problem.

---

### Post by m_ad on 2008-11-06
Thanks, now it displays the content but I can't type in the textboxes :/

---

### Post by desperado665 on 2008-11-06
Install the Firefox plugin "User Agent Switcher" and set it to IE7. It will install to your firefox tools menu. That is the only way I have been able to access my account at citibank. I just tested your link with agent enabled and it works fine.

---

### Post by eolson on 2008-11-06
+1

---

### Post by fignig on 2008-11-06
> **NilsE said:**
> In Synaptic completely remove flashplugin-nonfree and install adobe-flashplugin and it should solve the problem.

there is no adobe-flashplugin in synaptic, don't lie..

---

### Post by NilsE on 2008-11-06
> **fignig said:**
> there is no adobe-flashplugin in synaptic, don't lie..

Nice guy, if I was wrong it is called a mistake not a lie..

Actually it is for 8.10 in the partner repo

It can also be downloaded from the Adobe site (DEB file for Ubuntu)

---

### Post by m_ad on 2008-11-07
Thanks, this works.

---

