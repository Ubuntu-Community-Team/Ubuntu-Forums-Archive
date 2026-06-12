---
title: "/var/log/auth.log Question Relating to Ubuntu 20.04"
date: 2021-12-12
forum: New to Ubuntu
---

### Post by bhubunt on 2021-12-12
Hi,

I just entered the var/log/auth.log command in my Ubuntu 20.04 terminal.

These are some of the results I didn't understand: 

- /etc/securetty no such file 

  [I believe this is a Ubuntu 20.04 bug of some sort but how to get rid of it?]

-unregistered Authentication Agent for unix-session: c1     disconnected from bus 

-gkr - pam  stashed password to try later in open session


Thanks.

---

### Post by schragge on 2021-12-15
> **bhubunt said:**
> I just entered the var/log/auth.log command in my Ubuntu 20.04 terminal.
You forgot to mention the *actual* command. **/var/log/auth.log** is a file.

> /etc/securetty no such file
**/etc/securetty** is a directory. It's provided by package **libpam-modules**. The package is *required.* That means it *must* be installed on every Ubuntu system including yours. If it isn't, your system is seriously broken.

> unregistered Authentication Agent for unix-session: c1     disconnected from bus
Looks like a **polkitd** crash, but you didn't provide enough information to be sure. A polkitd crash might prevent you from performing administrative tasks from the GUI, but probably would have no other ill effects.

> gkr-pam  stashed password to try later in open session
Again, not enough information. The message seems to come from **gdm-password**, but that's only my guess because you didn't provide the full log line. And this cannot be the only message from **gdm-password**, there should be more.

---

### Post by Holger_Gehrke on 2021-12-15
@schragge: Sorry, but /etc/security/ is a directory. /etc/secur**ett**y is a file (man 5 securetty for details). It's part of the package login and lists the terminals from which root may login. It is connected with pam; there's a module pam_securetty which allows you to reject root login if it's coming from a terminal not listed in that file.

Holger

---

### Post by schragge on 2021-12-16
Thanks. I stand corrected then.

---

### Post by bhubunt on 2021-12-19
So is it true that [COLOR=#000000]/etc/securetty no such file is a bug in [/COLOR][COLOR=#000000]Ubuntu 20.04? 

How does one get rid of it?[/COLOR]

---

### Post by Holger_Gehrke on 2021-12-19
It's not so much a bug as a consequence of the decision not to allow root login. You don't login as root, you login as a normal user and then temporarily act as root through sudo. Since you're not going to login as root, there's no need to include a file which tells the system which terminals are secure enough to allow login as root. Therefore the file /etc/securetty is not included in the package login anymore. It's still there on my system, but that started life as Ubuntu 16.10 and went through quite a few release upgrades since then.

I'm not quite sure what program leaves that message in your log but there is a module pam_securetty in the package libpam-modules. You could try finding the right configuration file in /etc/pam.d/ (it's /etc/pam.d/login on my system) and comment out the line that configures that module.

Holger

---

### Post by bhubunt on 2021-12-20
> **Holger_Gehrke said:**
> It's not so much a bug as a consequence of the decision not to allow root login. You don't login as root, you login as a normal user and then temporarily act as root through sudo. Since you're not going to login as root, there's no need to include a file which tells the system which terminals are secure enough to allow login as root. Therefore the file /etc/securetty is not included in the package login anymore. It's still there on my system, but that started life as Ubuntu 16.10 and went through quite a few release upgrades since then.

I'm not quite sure what program leaves that message in your log but there is a module pam_securetty in the package libpam-modules. You could try finding the right configuration file in /etc/pam.d/ (it's /etc/pam.d/login on my system) and comment out the line that configures that module.

Holger

Would you recommend root login then? Or is it better to simply execute sudo commands? What are the advantages or disadvantages and which is the safest way to proceed.

---

### Post by The Cog on 2021-12-20
Ubuntu (or Canonical, who curate Ubuntu) have decided that the more secure way is for users to log in as their own username, and then use sudo when necessary. There have been many discussions about this choice, both here and in other forums. I'm not going to launch into that discussion, other than to say that as far as I know, it is still against the policy of this forum to new users how to enable direct login as root. My advice would be to "go with the flow" and use sudo when using Ubuntu.
If you get too annoyed at using sudo over and over again in a session where you are doing lots of work as root, "sudo -i" will turn your terminal into a root login (use exit or ^D to exit back to being you). I do that quite often, but I am always aware which role working I'm in - user or root.

---

