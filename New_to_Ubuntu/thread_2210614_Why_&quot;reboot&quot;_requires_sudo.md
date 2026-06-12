---
title: "Why &quot;reboot&quot; requires sudo?"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by spectatorx on 2014-03-11
I always wonder why "reboot" command in terminal requires sudo to be executed? Rebooting from gui doesn't require so high privileges to do reboot.

---

### Post by david98 on 2014-03-11
[COLOR=#000000][FONT=Arial]When using the GUI, you are (typically) sitting in front of the computer you are working on. However, when using a terminal, you might be physically on one machine and remotely using another. You might have *many* terminal windows open to *many* different machines. What if you accidentally type reboot in the wrong one? That action could range from an inconvenience to a complete disaster.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]By using sudo it forces you to use a password. If you type in the wrong password it gives you an error and hopefully you realize that you are in the wrong terminal. [/FONT][/COLOR]

---

### Post by buzzingrobot on 2014-03-12
I think we should be prompted to escalate to reboot via the GUI.

Remember, too, that, at its core, Linux, like Unix, is a multi-user system.  It's designed to allow multiple users to run on a single installation simultaneously.  You could, if you chose, buy keyboards, mice, displays, etc., for several people and set them all up to run on one Linux installation on one box.

That's why the concept of root and regular users exists, and why users must temporaily escalate their privileges to perform operations that could affect other users or the entire system.  In this case, you don't want one user rebooting a machine while other people are using it. (Traditionally, one person would be the root user who would grant users the ability to escalate their privileges, e.g., run commands with sudo.  If a user abused that, it could easily be taken away.)

There are also reasons why one person might create and simultaneously use multiple accounts on one machine.  If more than one of those accounts has been logged into, I'd prefer that the an attempt to restart in another user session should require privilege escalation.  I don't believe Ubuntu does, though.

---

### Post by grahammechanical on 2014-03-12
I will not swear to it but I think that if we have switched users from the first logged in user then, the Shutdown in the second user will actually work like a log out and not a true Shutdown. I have not experimented with this for a couple of years.

Regards.

---

### Post by cmcanulty on 2014-03-12
yes I think it only requires sudo if another user is also logged on

---

### Post by lykwydchykyn on 2014-03-13
Here's the technical explanation:

Shutdown/reboot on Linux requires root access.  "reboot" is a simple, low-level terminal command, so it requires elevation in order to do a root action like that.

When you shutdown through the GUI, your request goes through a service called "ConsoleKit", which is basically a framework for granting permissions for different actions to users.  Assuming ConsoleKit is configured to allow you to reboot, it takes care of elevating your request at the low level and performing the reboot. 

There are ways to reboot from the terminal via ConsoleKit, but they're a bit ugly.  See some examples here: [http://forums.debian.net/viewtopic.php?f=16&t=58094](http://forums.debian.net/viewtopic.php?f=16&t=58094)

---

