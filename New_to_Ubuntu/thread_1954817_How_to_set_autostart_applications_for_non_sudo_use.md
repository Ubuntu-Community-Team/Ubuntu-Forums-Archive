---
title: "How to set autostart applications for non sudo users"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by jellaby on 2012-04-08
Problem: I don't know how to make it so that when a non sudo user logs in, Firestarter automatically starts up...or any application for that matter.

Context: If I'm going to make a jump to linux from windows, I need to be more familiar with Linux security. It's my one reservation in making a complete jump. From what I understand, not logging in as root user is the first step. Now that I have my account set up, I want to be able to surf the internet with a good firewall, but it won't let me start it up. I don't know why.

I'm a very new user with Lucid, so talk slowly and use small words. ;)

---

### Post by GWBouge on 2012-04-08
For one, Firestarter isn't a firewall, just a front-end for the one already in Ubuntu, iptables, to make it easier to set up rules.

Second, Firestarter hasn't been updated since 2005, I'd use something more current.  Check out gufw.

A little more info in this thread:  [http://ubuntuforums.org/showthread.php?t=1421187]("http://ubuntuforums.org/showthread.php?t=1421187")

---

### Post by jellaby on 2012-04-08
Thanks for the advice. I do appreciate it. However, it doesn't really answer my question.

---

### Post by GWBouge on 2012-04-09
Ah, might have been a bit short on the explanation, sorry, lol.

From a security standpoint, iptables (the actual firewall) doesn't rely on Firestarter or gufw.  As in, you don't *have* to start the GUI, the firewall starts with the OS.  You only need the GUI to make life easier when adding rules and such, and only an admin (sudo-enabled) account can do it.

For startup apps, the simple way in Lucid:  System -> Preferences -> Startup Applications (I think, been a while since I've used Lucid ...)

You *may* be able to auto-start a GUI program that requires root privileges by using gksu in the command field, such as 'gksu firestarter', but you'll be prompted for your password again after you log in, and a non-sudo user doesn't have the permissions to do that.

> From what I understand, not logging in as root user is the first step.

By default, the root account is disabled on Ubuntu.  Don't confuse the 'root' account with one belonging to the 'admin' group, such as the one you created when you installed Ubuntu.  The 'root' account is similar to the 'Administrator' account on Windows, as in once you're in, it doesn't need authorization to do anything.  Admin users, however, can gain root-level privileges (such as with using 'sudo' in the terminal) for tasks, which requires your password.

TL;DNR
The firewall starts with the OS, so you don't need to worry about having a non-sudo user starting the GUI app to load it up, and only sudoers can run apps/programs/commands that do system-level tasks.

---

### Post by jellaby on 2012-04-09
That's very helpful. I downloaded gufw and am playing around with it,  but even though I've enabled denial of all incoming and outgoing  traffic, my computer can still access the internet through firefox. What  am I missing? 

My current laptop has Vista on it, and in Vista, you block all outgoing  traffic and then create a rule for every program you want to make it  through the firewall. Because of my experiences with Vista's firewall, I  assumed that denying all incoming and outgoing traffic would basically  pinch off everything...including my Ubuntu update manager. This is the  way it is in Vista. Is it different with Ubuntu?

---

### Post by GWBouge on 2012-04-09
Hmm ... should be working as you expected it to.  I just installed gufw to make sure, clicked the lock on the bottom right to make changes, Status -> On, Incoming -> Deny, Outgoing -> Deny, refreshed a page in Firefox and:  Server not found.  I even rebooted to make sure it stuck, first thing I did was crank up Firefox and goto Ubuntu Forums, and nothing got out as expected.

Not sure I can help beyond that, maybe someone else can expand on what might be going on.

Edit:
Just to make sure, you downloaded/installed gufw from the Software Center?

---

### Post by ravinfy on 2012-04-09
Someone wrote a review on Software Center that gufw hasn`t worked on Ubuntu versions prior to 11.04! 

Perhaps you should try another program?

---

### Post by jellaby on 2012-04-09
> **ravinfy said:**
> Someone wrote a review on Software Center that gufw hasn`t worked on Ubuntu versions prior to 11.04! 

Perhaps you should try another program?
This article demonstrates installing gufw on Ubuntu 8.1

[http://www.dedoimedo.com/computers/gufw.html](http://www.dedoimedo.com/computers/gufw.html)

---

### Post by jellaby on 2012-04-09
> **GWBouge said:**
> Hmm ... should be working as you expected it to.  I just installed gufw to make sure, clicked the lock on the bottom right to make changes, Status -> On, Incoming -> Deny, Outgoing -> Deny, refreshed a page in Firefox and:  Server not found.  I even rebooted to make sure it stuck, first thing I did was crank up Firefox and goto Ubuntu Forums, and nothing got out as expected.

Not sure I can help beyond that, maybe someone else can expand on what might be going on.

Edit:
Just to make sure, you downloaded/installed gufw from the Software Center?
Yes, I downloaded it from the software center. I'll figure out why it's not working later...I have another question:

When I download and configure software like gufw with an account in the admin group, does that mean that all users on that system (whether in the admin group or not) will be under that same firewall configuration? What if I want different configurations for different accounts? Do I need to grant root rights to each account I want to have a different firewall configuration?

---

### Post by jerome1232 on 2012-04-09
It's probably because you still have firestarter installed, which has it's own set of rules in iptables which are placed before gufw's, therefore overriding it.


You'll need to completely remove firestarter before you can use gufw.

---

### Post by philinux on 2012-04-09
> **jellaby said:**
> Problem: I don't know how to make it so that when a non sudo user logs in, Firestarter automatically starts up...or any application for that matter.

Context: If I'm going to make a jump to linux from windows, I need to be more familiar with Linux security. It's my one reservation in making a complete jump. From what I understand, not logging in as root user is the first step. Now that I have my account set up, I want to be able to surf the internet with a good firewall, but it won't let me start it up. I don't know why.

I'm a very new user with Lucid, so talk slowly and use small words. ;)

Please read this .

 [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by jellaby on 2012-04-09
Thanks for the resource. It's a useful one.

---

