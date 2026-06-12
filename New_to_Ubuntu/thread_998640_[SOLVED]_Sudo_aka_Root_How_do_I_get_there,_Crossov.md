---
title: "[SOLVED] Sudo aka Root How do I get there, Crossover Issues"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Flirtilizer on 2008-12-01
I had some problems with Wine and Crossover.  I left Wine installed when I installed Crossover.  Don't know if that is a good or bad thing. :)

I tried to find this myself without posting a new thread but with the thirty million already here about root, that's a bit tough. :)

Can I log in as sudo?  Or Do I just put the sudo in front of the command.  I never setup an admin account when I installed and that has me confused..

I don't remember the command line commands to use to change from one user to the other, SH?  

When I uninstalled crossover I was given a command to run to totally remove crossover.  I'd like to do that then re-install it.

Been 5 years or more since I touched any version of Linux.  Looks like I'm very happy to be back.  Just replaced windows on  my notebook with Ubuntu.

---

### Post by SunnyRabbiera on 2008-12-01
no to use sudo most of the time you have to do command line, especially with installing softwares like crossover.
Ubuntu has disabled root by default, and for good reasons, most new users not knowing what to do go use the root account for their main account leaving the system wide open to attacks.
so ubuntu uses sudo, in many ways its better then root and in others more secure.

---

### Post by EXCiD3 on 2008-12-01
Sudo gives you root access when you run a command. You never want to login to the root account and thats why it is not setup to do so by default. Just run the command with sudo in front of it and type in your user's password to run the command with escalated priviledges. The user must be in the admin group in order to gain this priviledges however. This prevents you from logging in permanently and a rogue account could trash the system.

---

### Post by Flirtilizer on 2008-12-01
Okay that brings back some memories") How do I put the password in, just sude password command?

Thanks.

---

### Post by hellion0 on 2008-12-01
Do "sudo (command)" in a terminal, and it will prompt you for your password, then execute the command if you're allowed.

---

### Post by lazyart on 2008-12-01
if you are launching a graphical application, use gksudo instead.

---

