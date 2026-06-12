---
title: "[SOLVED] firefox won't load certain sites"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by libertyblues on 2008-07-29
english wikipedia, reddit, others... mostly sites that I use often.

flashes connected/stopped/waiting at the bottom

version 3.0.1

I uninstalled and reinstalled it with sudo aptitude remove/install... not really sure what else to try.

has anyone else run into something like this? :confused:

Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008

EDIT: This does not happen with Opera.

SOLVED: I think it was the noscript plugin... but it never blocked those sites before... and wasn't give me the option to allow them, but whatever.

---

### Post by SunnyRabbiera on 2008-07-29
unusual, I know for certain wikipedia works under firefox 3...
are you having connection issues?
have you tried to install an alternate browser to verify?

---

### Post by LowSky on 2008-07-29
No problems with website, try deleting the .firefox folder from your /home partition. and restarting firefox.

Are you sure you can get on the internet?
Does this happen with another browser like Opera?

---

### Post by libertyblues on 2008-07-29
yeah I'm on the internet right now with Opera. Where exactly is .firefox? 

is it in home? I tried sudo rm /home/.firefox and /home/username/.firefox and got "no such file..."

---

### Post by libertyblues on 2008-07-29
yeah i'm using opera for now

---

### Post by billgoldberg on 2008-07-29
.firefox is a hidden file.

Press "ctrl + h" to view them.


Could one of the firefox add-ons be causing problems?

Try disabling them.

---

### Post by gjoellee on 2008-07-29
> **billgoldberg said:**
> .firefox is a hidden file.

Press "ctrl + h" to view them.


.firefox doesn't exist for me...by default it is .mozilla

---

### Post by gjoellee on 2008-07-29
this tweak may fix your problem: 

1.Type “about:config” into the address bar and hit return. Scroll down and look for the following entries:
 network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests
 Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.
 2. Alter the entries as follows:
 Set “network.http.pipelining” to “true”
 Set “network.http.proxy.pipelining” to “true”
 Set “network.http.pipelining.maxrequests” to some number like 30. This means it will make 30 requests at once.
 3. Lastly right-click anywhere and select New-> Integer. Name it “nglayout.initialpaint.delay” and set its value to “0&#8243;. This value is the amount of time the browser waits before it acts on information it receives.

---

### Post by t0p on 2008-07-29
I have to agree with the other responders: I'm using Firefox 3, and I don't experience any of the problems reported by libertyblue.

Just to be sure: I tried accessing Wikipedia (en) and had no problem.

**libertyblue**: maybe your problem lies with an aspect of your installation?

---

### Post by libertyblues on 2008-07-29
ah, thanks, I think it was one of the addons. Now I just have to figure out which one it was!

---

