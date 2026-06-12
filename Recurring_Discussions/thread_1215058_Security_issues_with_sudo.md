---
title: "Security issues with sudo"
date: 2009-07-16
forum: Recurring Discussions
---

### Post by mihaiv on 2009-07-16
1. The problem
In Ubuntu gksu and sudo can be hijacked by an attacker who already has access to the current non-administrative account. In order to do that you can simply create a bin directory in your home folder, add that directory to PATH and create in it the scripts: gksu and sudo. The scripts would silently run any application the attacker wants with root privileges and start the application you wanted to start in the first place so that you won't notice a thing.
So, after the attacker application (got on a website with a firefox bug for example) gets access to your limited account all it has to do in order to get root access is the above and wait for you run something with administrative rights (like synaptic from the menu; at some point even the updater which runs automatically was [calling gksu with a relative path]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/194166")). This largely defeats the purpose of having a limited account on a desktop version of Ubuntu. The code to do this is very simple and even a script kiddie can make it if he doesn't find it somewhere on the internet.
I did test multiple times the things I said above.

2. The do it right solution
I don't know how to fix sudo but for gksu I have an idea and I posted it on the gksu bug I [submited a year and a half ago]("http://savannah.nongnu.org/bugs/?22374"). Even if you set a description gksu should show the complete path of the application it is running. The presence of the description still leaves easy social engineering attacks (people don't read all the text in a form or they don't understand linux commands) but an advanced user has a chance to realize he is hacked. A more complete solution would require not being able to modify menu entries for administrative applications and, of course, having absolute paths in those menu entries.
Sudo solutions might go in the direction of modifying the most used terminal in order to treat sudo specially but I find that very problematic. The simple, working, correct solution is to also lock the screen and show what you are executing.
There might be a system wide solution for any administrative start commands in a way that the system (kernel and some base applications) treats differently the sudo/gksu type of commands. It would not use the path to search for sudo but only its predefined location and the path used for the applications sudo runs would be only changeable with root access. But I understand too little about linux as a whole in order to realize all the implications of this.
There also is the simple and very restrictive solution of not having local user paths, only paths that are modifiable by root access.
The use of unlock on some ubuntu applications (User settings) puzzles me. The password prompt you get there does not lock the screen and it seems that you don't have a way to realize if it is the system asking you the password or an applications that looks just like "user settings" (it is very easy to create clones in open source). I haven't looked deeper into unlock but superficially it doesn't look like a solution for gksu problems.
Any solution without having an administrative (locked, grayed out, something that only a root application can do) screen where to enter the password and see exactly what you are running is prone to attacks where the random dialog appears and asks you for password (maybe it knows that you are running synaptic and somehow expect to be asked about password).

3. The sad solution
No gksu and sudo. Users log out and log in as root for administrative stuff. Of course they will end up using only root and here the limited account "protection" stops.

4. The "great new thing" solution
Get rid of the default limited user account on desktop installations. Even if that user account works properly in connection with doing administrative jobs its limitation don't prevent an attacker to do damage where it mostly matters for you. For 99% of the users their documents and most other things they care about are accessible/modifiable with the limited user account. This includes those secret pictures you have with your new girlfriend. Browser settings can also be altered without administrative rights, and of course browsing history, cache and saved passwords are not locked behind the "root door". There are things that the malware can't do on limited accounts like sniffing, key logging, reading your credit card from firefox memory but attackers can find creative ways around these limitations (can't they install addons without root access? don't those addons get to the firefox internals?).  For me, the part of the system for which I need root access is the part I care less about. For instance I installed the version of Ubuntu (9.04) I am talking from 2h ago (45 min of my time I think). On my desktop system (doing usual stuff: internet, music, pictures) if an attacker gets from limited account to root access he mostly can hide better from me (rootkits). But I am not really searching for him so I won't find him anyway.
As for limited access preventing users and applications to do stupid things. Users are not prevented too much to mess their system by root access (they need to type "sudo rm -fr /*" instead of "rm -fr /*"; saving a document in / by accident is not the biggest problem in the world; for deleting system files they could be prompted anyway). User applications are prevented to arbitrarily break the system but there is a long time since I've seen an application trying to break my system in any place other than the installer. Its true that default root access would allow applications to grow more ill behaved (like saving user settings in /usr) but we might find solutions for that without using a default limited account (at least not as limited as it is now; minimal set of restrictions, warnings, etc for properly behaving applications).
On Windows XP when I do not trust an application I get from the internet I do run it under a limited user account I created specifically for that purpose. That user account does not have access to my documents, my desktop, settings or anything else that matters for me. Things I save from that application go to that account documents and I copy them later from that location. People see me as an advanced user and, still, I have to admit that I don't find the method easy to use. But if the operating system would create such a user account for me and offer me some really easy entry points to it when I might need it (like asking: do you want to run this internet application: yes, no, under limited account.) I would use it all the time. Firefox can also be run under a special limited account (you could still save files only in a predefined location), maybe each tab in its process like chrome with higher limitations if you go on some blurry web sites (enabled for private browsing?).
I have installed my Windows XP system 3 years ago, I use it a lot and I like to experiment new things but still I haven't broken it. I did reinstall some linux systems in the mean time (it is related with understanding less linux (I did the "hard" windows experiments 12 years ago), going deeper into the system (I use sudo all the time), but mostly it is problematic updates (especially distribution upgrades)).

5. Linux security fundamentalists please read the above twice before posting :).

---

### Post by doas777 on 2009-07-16
when i test your linked bug report on gksu (the other one is fixed), I get this error:
"failed to run /home/testuser/.test2 as user root. The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator." (see attachment)

where .test2 contains
```
touch /test2.powned
synaptic
```
synaptic did not load either. it did work on my sudo-able account, but not as a normal user.


do you have instructions for reproducing your issue? I don't know if here is the right place to post them though. not sure.

It looks like you've given this a lot of thought. it might be kewl to write a formal paper on your thoughts and observations.

---

### Post by iponeverything on 2009-07-16
humm.. and how does one modify the PATH variable for administratively capable accounts on the system from a normal non-administrative account?

---

### Post by aysiu on 2009-07-16
It's been brought up before:
[What do you think about the 5 minute sudo window?](http://ubuntuforums.org/showthread.php?t=1056529)
[sudo privilege escalation flaw?](http://ubuntuforums.org/showthread.php?t=1051348)
[can programs run sudo ... without password within sudo's 15 minutes?](http://ubuntuforums.org/showthread.php?t=1045209)
[Gksudo and Ubuntu's security model](http://ubuntuforums.org/showthread.php?t=910201)
[If Ubuntu breaks the 10% market share barrier, should the sudo timeout go away?](http://ubuntuforums.org/showthread.php?t=925998)
[What do you think of the sudo timeout / grace period?](http://ubuntuforums.org/showthread.php?t=762866)
[How much of a security risk could the sudo timeout become?](http://ubuntuforums.org/showthread.php?t=709580)

---

### Post by bodhi.zazen on 2009-07-16
> **iponeverything said:**
> humm.. and how does one modify the PATH variable for administratively capable accounts on the system from a normal non-administrative account?

They do not.

The issue is preventing privilege escalation from a compromised account and the argument is circular, which is why it is in recurring discussions.

The argument is basically :

If I have compromised your account (and have root privileges) such that I can modify file foo I can then become root.

The part about needing ( root privileges already ) or ( that there is a **unspecified and theoretical** security flaw allowing a cracker to run arbitrary code) is left out, and people who do not understand that then freak out.

It is nothing but smoke and mirrors.

When confronted with ( ) people quickly back off and say well an admin account or what not.

Basically they take 'arbitrary code' and then give a specific example. I can run arbitrary code and modify file foo , thus file foo is a security problem or what not.

The whole discussion is a farse as the true security flaw is that which allowed arbitrary code in the first place and always remains hidden behind smoke and mirrors, unspecified.

"help the sky is falling"

It is an old discussion and full of partial or outright misinformation and lots of FUD.

If a system is compromised and you wish to prevent privilege escalation you need to use SELinux or Apprmor.

Better yet, re-install (make an image of the compromised OS for forensics).

---

