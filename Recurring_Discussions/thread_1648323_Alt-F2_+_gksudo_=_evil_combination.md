---
title: "Alt-F2 + gksudo = evil combination?"
date: 2010-12-18
forum: Recurring Discussions
---

### Post by DZ* on 2010-12-18
One often talked about Windows flaw is that privilege escalation is relatively easy to achieve. 

In Ubuntu, Alt-F2 + gksudo (Run Application dialog) allows a rogue user owned process to run arbitrary commands as root, once a user enters the password. 

The 15 min authentication window is granted to any process that runs without TTY.

For example a simple line in a script that contains the following will wake up once in a minute and once the authentication is granted it will execute "EvilCommands" (confirmed to work)

```
while [ true ]; do sudo sh -c 'EvilCommands' ; sleep 60; done
```

Why is that a default behavior in Ubuntu (that can be changed by adding requiretty to sudoers)? Fedora comes with requiretty enabled. I haven't checked other distros.

---

### Post by CharlesA on 2010-12-18
The key is that it prompts for a password.

You'd have to get a malicious program on the machine in the first place.

---

### Post by DZ* on 2010-12-18
> **CharlesA said:**
> The key is that it prompts for a password.

gksudo that a user starts does, but a malicious program is just sitting there waiting for it to happen.

> **CharlesA said:**
> You'd have to get a malicious program on the machine in the first place.

I agree, but the issue I'm talking about is privilege escalation. The context of this problem is conditional on the fact that a user already have a rogue program running.

---

### Post by CharlesA on 2010-12-18
> **DZ* said:**
> gksudo that a user starts does, but a malicious program is just sitting there waiting for it to happen.

How do you mean? A malicious program would need to be placed on the target machine, given execute permission, and then started for it to work. By default, files don't have execute permission.

> I agree, but the issue I'm talking about about is privilege escalation. The context of this problem is conditional on the fact that a user already have a rogue program running.

Exactly. It requires them to start the program somehow, and as downloaded files aren't executable, it wouldn't be a threat, unless they made it executable themselves.

---

### Post by bodhi.zazen on 2010-12-18
*Thread moved to **Recurring Discussions**.*

This topic comes up from time to time and has been discussed many times.

If a cracker has access to an administrative account, one that has access to "root", sudo, su, or Windows, root access is not far behind by any number of methods.

For a cracker to "take advantage" of this they would already have to have access to your account, either as root, in which case why bother, or as your user, in which case there are hundreds of theoretical methods of privilege escalation.

If this bothers you either create an account not in the admin group for day-to-day user or change the timeout of sudo.

---

### Post by iponeverything on 2010-12-18
"Alt-F2 + gksudo = evil combination?"

no 

Administrative user + weak password = evil combination


Did the bad guy get access from a weak password? If so they don't need wait they can sudo when they feel like it.

Did the bad guy get access from physical access, then you have bigger problems. 

Did the bad guy get access from a remote exploit, see #2

---

### Post by JustinR on 2010-12-18
Most gksudo commands, like running Synaptic require the user password any way, so whats the problem?

---

### Post by DZ* on 2010-12-19
> **JustinR said:**
> Most gksudo commands, like running Synaptic require the user password any way, so whats the problem?

That *is* the problem. Unless you start it from a terminal, for the next 15 min you are essentially logged in as root into a graphical desktop.

---

### Post by sydbat on 2010-12-19
> **DZ* said:**
> That *is* the problem. Unless you start it from a terminal, for the next 15 min you are essentially logged in as root into a graphical desktop.I see. I imagine [this]("http://www.youtube.com/watch?v=r9ObLGRq33o") is what you are worried about...

---

### Post by imbjr on 2010-12-19
> **DZ* said:**
> One often talked about Windows flaw is that privilege escalation is relatively easy to achieve. 

In Ubuntu, Alt-F2 + gksudo (Run Application dialog) allows a rogue user owned process to run arbitrary commands as root, once a user enters the password. 

The 15 min authentication window is granted to any process that runs without TTY.

For example a simple line in a script that contains the following will wake up once in a minute and once the authentication is granted it will execute "EvilCommands" (confirmed to work)

```
while [ true ]; do sudo sh -c 'EvilCommands' ; sleep 60; done
```

Why is that a default behavior in Ubuntu (that can be changed by adding requiretty to sudoers)? Fedora comes with requiretty enabled. I haven't checked other distros.

I may be wrong, but surely the EviCommands script does not have access to the same shell that's been granted root privileges. So when your malware cron job kicks in, it's not got the umph do to its evil will.

---

### Post by DZ* on 2010-12-19
> **bodhi.zazen said:**
> *Thread moved to **Recurring Discussions**.*

This topic comes up from time to time and has been discussed many times.

If a cracker has access to an administrative account, one that has access to "root", sudo, su, or Windows, root access is not far behind by any number of methods.

For a cracker to "take advantage" of this they would already have to have access to your account, either as root, in which case why bother, or as your user, in which case there are hundreds of theoretical methods of privilege escalation.

If this bothers you either create an account not in the admin group for day-to-day user or change the timeout of sudo.

Distros like Fedora create root account first, then a regular user, but Fedora won't allow root to login into GUI. You'd presumably be switching to root from a terminal with su when needed. In contrast to that, Ubuntu by default allows a user in admin group to go to menus, pick something like Gparted from there, enter the password, and for the next 15 min that user is basically logged into GUI as root: any process without TTY can do whatever it wants. I understand that there are multiple ways to remedy this. I'm questioning security of Ubuntu' default GUI authentication mechanism.

---

### Post by DZ* on 2010-12-19
> **imbjr said:**
> I may be wrong, but surely the EviCommands script does not have access to the same shell that's been granted root privileges. So when your malware cron job kicks in, it's not got the umph do to its evil will.

In my example, root access is being granted to a process without a TTY, that's the whole point. 

To verify that it works, make a bash script, replace EviCommands with 

'date >> /ItWorks.txt'

and add it to Startup Applications (from menus in Gnome)

Relogin and run Gparted, selected from the menu. It will ask for password. After you enter it, the script will start writing date to a file "/ItWorks.txt".

This is a normally forbidden location.

---

### Post by CharlesA on 2010-12-19
The thing is that you need to execute a malicious program/script/whatever for it to cause any damage.

Normal files don't have execute permission and, if something was somehow added to startup applications or a crontab without you knowing, you have bigger problems.

---

### Post by DZ* on 2010-12-19
> **CharlesA said:**
> The thing is that you need to execute a malicious program/script/whatever for it to cause any damage.

Normal files don't have execute permission and, if something was somehow added to startup applications or a crontab without you knowing, you have bigger problems.

It doesn't need to be a script added to autostart or crontab. Any user owned process without a TTY will have elevated permissions. I think the idea of sandboxing normally benign applications (like firefox) originates from similar concerns.

---

### Post by bodhi.zazen on 2010-12-19
> **DZ* said:**
> It doesn't need to be a script added to autostart or crontab. Any user owned process without a TTY will have elevated permissions. I think the idea of sandboxing normally benign applications (like firefox) originates from similar concerns.

For this 'exploit' to work either your system was already compromised or the cracker has physical access, either way you loose.

You are trying to prevent privilege escalation from an account that both :

[list=number][*]Has already been compromised.
[*]Has root access.[/list]

Preventing such privilege escalation is next to impossible, does not matter if you use su or sudo, if your admin account is compromised you need to reinstall your machine and restore any data from a know good backup.

From a security perspective you need to prevent #1, whatever it was that gave a cracker access in the first place.

Again if this bothers you, I have already told you how to 'fix' the 'problem', but you still have not fixes the other few hundred methods of privilege escalation nor have you addressed the primary security flaw, that which gave access to a cracker in the first place. A cracker can simply access you machine yet again and perform additional exploits, or use the back door they installed, or whatever.

---

### Post by JustinR on 2010-12-19
> **DZ* said:**
> That *is* the problem. Unless you start it from a terminal, for the next 15 min you are essentially logged in as root into a graphical desktop.

What user program requires administrator privileges?

---

### Post by Kalimol on 2010-12-20
I don't think that's DZ's point. I think it's like, you run GParted, which doesn't run from a terminal shell and asks for a password through gksudo at launch. Now you're logged in as an administrator in the GUI. Another userspace app, something you've installed unaware of its evils, takes advantage of this to dink with your system.

It doesn't add up, though. Just because I'm running GParted doesn't mean I can launch Nautilus and start deleting files outside of my Home directory. Alternately, a malicious app could do plenty of personal damage from your Home folder, and an unkown Firefox extension could wire the contents of your bank account to Nigeria. I don't see how the - yeah, a bit paranoid - approach Fedora takes really helps anything. It's an extra annoyance, it's likely to dissuade less savvy users, who make up the greater part of Ubuntu's "market," and the *more* savvy users aren't going to be satisfied with the defaults anyway.

---

