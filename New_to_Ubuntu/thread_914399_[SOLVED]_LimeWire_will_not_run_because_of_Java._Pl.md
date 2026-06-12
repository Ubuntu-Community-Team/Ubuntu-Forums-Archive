---
title: "[SOLVED] LimeWire will not run because of Java. Please help."
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Lizard_King on 2008-09-08
I have been surfing this site and others all day long trying to learn how to run LimeWire, but so far have found nothing that has helped. 

This is the error I get when I try to run LimeWire Pro:

LimeWire needs the Java Runtime Enviroment 5.0 or above. Click OK to go to [www.java.com](www.java.com), where you can install Java.

I have the latest Java installed.

---

### Post by starcannon on 2008-09-08
System>Administration>Synaptic Package Manager

Search: sun-java

uninstall sun-java6 and install sun-java5

that should fix you, the same is necessary if you want to use Blackboard(a learning community setup for college students)

GL

---

### Post by Lizard_King on 2008-09-08
Thank you for your quick response, but unfortunately it did not help.

---

### Post by ddarsow on 2008-09-08
> **starcannon said:**
> System>Administration>Synaptic Package Manager

Search: sun-java

uninstall sun-java6 and install sun-java5

that should fix you, the same is necessary if you want to use Blackboard(a learning community setup for college students)

GL

This is not absolutely accurate; I am running java6 and use Blackboard on a daily basis without issue.

---

### Post by ninch on 2008-09-08
what ubuntu version are you running?

make sure that you installed all the sun-java6 types, like -bin, -jre, -plugin


If this still is not helping, you may have to install wine, which is basically a way to run windows programs on ubuntu.

hope this helps,

---

### Post by rossjman1 on 2008-09-08
or just use frostwire

---

### Post by Lizard_King on 2008-09-08
> what ubuntu version are you running?
The latest version, 8.04- the Hardy Heron - released in April 2008.


Still doesn't work.


I keep getting this error message.

E: sun-java6-doc: subprocess post-installation script returned error exit status 1

---

### Post by D3M0L1$H3® on 2008-09-08
LimeWire's not good, man. Use BitTorrent; uTorrent. have you tried installing Java in WINE, then LimeWire in WINE? there is OPENJava in synaptic, try installing that. Or, asd they said, used frostwire.
*cough*uTorrent!*cough*

---

### Post by Lizard_King on 2008-09-08
I don't really need to use LimeWire, but I need to know what causes the errors so I can learn to use Ubuntu like a pro.

---

### Post by D3M0L1$H3® on 2008-09-08
> **Lizard_King said:**
> I don't really need to use LimeWire, but I need to know what causes the errors so I can learn to use Ubuntu like a pro.

Wow. I don't think LimeWire errors are going to help you with that.
But can you post what happens when yo try to install and such?
Just saying it doesn't work won't help us help you.
Details, and I'll be glad to help.
:)

---

### Post by Therion on 2008-09-08
> **Lizard_King said:**
> I don't really need to use LimeWire, but I need to know what causes the errors so I can learn to use Ubuntu like a pro.
I don't remember what version of LimeWire it was, but I do remember there being a problem with one release that had many complaining about it's inability to recognize that Java was installed.  The "iced tea" plugin MIGHT get you up and running, but I suggest you forget Limewire and install Frostwire instead.  Seriously. It's the open source, cross platform, version of Limewire Pro.  

Believe me when I tell you: You'll never look back.

---

### Post by Lizard_King on 2008-09-08
Tried to install Wine and got this message.

*E: sun-java6-doc: subprocess post-installation script returned error exit status 1*

---

### Post by D3M0L1$H3® on 2008-09-08
> **Lizard_King said:**
> Tried to install Wine and got this message.

*E: sun-java6-doc: subprocess post-installation script returned error exit status 1*

That's what happens when you try to isntall WINE? or when you try to install Java in WINE?
That looks like your Java attempts screwed up while installing, or they messed up halfway through and were suddenly ended.

---

### Post by Lizard_King on 2008-09-08
Now I'm getting this when I try to run Synaptic Package Manager.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now everything I do gets this error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Therion on 2008-09-08
> **Lizard_King said:**
> Now I'm getting this when I try to run Synaptic Package Manager.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Open a Termial.
Enter the following:```
dpkg --configure -a
```

---

### Post by D3M0L1$H3® on 2008-09-08
> **Therion said:**
> Open a Termial.
Enter the following:```
dpkg --configure -a
```
The terminal usually assumes that's obvious?
BTW, when the terminal tells you to run something, do it.
How long have you had the installation? Looks like you gots some issues.

---

### Post by Lizard_King on 2008-09-08
> Open a Termial.
Enter the following:
Code: dpkg --configure -a


I got this message: *requested operation requires superuser privilege*

I installed Ubuntu this morning.

---

### Post by D3M0L1$H3® on 2008-09-08
> **Lizard_King said:**
> I got this message: *requested operation requires superuser privilege*

```
sudo su -
```
Enter your password (it wont show that you're typing it
then try it.

---

### Post by Lizard_King on 2008-09-08
> **D3M0L1$H3® said:**
> Wow. I don't think LimeWire errors are going to help you with that.
But can you post what happens when yo try to install and such?
Just saying it doesn't work won't help us help you.
Details, and I'll be glad to help.
:)

I was joking.

---

### Post by D3M0L1$H3® on 2008-09-09
okay. did the it work? if so, mark as solved

---

### Post by Lizard_King on 2008-09-09
With over 12,000 online users you would think someone could have helped me, but nooooo, I had to start all over and reinstall the OS.

I am joking by the way. Thanks for your help.

---

