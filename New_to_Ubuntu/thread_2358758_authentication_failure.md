---
title: "authentication failure"
date: 2017-04-17
forum: New to Ubuntu
---

### Post by jon80 on 2017-04-17
I am just trying to change to *su* using the command *sudo su* on my ubuntu-based unix terminal, and, somehow I get authentication failure when I am logged on with my only user on the machine.

Does the *root* come bundled with a secret logon, and, why is this please, who supports such level of permissions that are set by the original scripting programmers that prepare the install scripts, if you could check for me?

What support options are there and are these paid options for escalation?

NOTE: I am unable to post screenshots from my virtual machine, I am probably being naive, but I have not yet found the right command or key sequence for this.

---

### Post by wildmanne39 on 2017-04-17
At this forum there is no paid serves we are all volunteer help on the forum, you can get paid support by looking at this link.
[https://www.ubuntu.com/support/plans-and-pricing](https://www.ubuntu.com/support/plans-and-pricing)

---

### Post by Impavidus on 2017-04-17
On a normal Ubuntu system, there is no login for root. The root user exists, but there's no password set and login as root is impossible. It is however possible to run a shell as the root user, by using for example **sudo su** or more commonly **sudo -i**. In either case, you have to enter the password of the user invoking the sudo command, and it will only work if that user has permission to use sudo.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

