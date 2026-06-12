---
title: "Permission denied even as root user"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by kris19 on 2014-07-14
Hello, 

I'm attempting to install Nagios on my machine, however I need to verify my config files. This itself hasn't been a problem the last times I've needed to verify the files, but suddenly it's telling me that I don't have permission, now that doesn't make sense as I started each session by becoming the root user with sudo -s so I don't understand why I don't have permission.

All help is appreciated (and desperately needed :P)

---

### Post by steeldriver on 2014-07-14
Hello and welcome to the forums

Please copy and paste the commands you are typing and the exact error messages between ```
... [&#8725;CODE] tags

BTW you should probably be using

[CODE]
sudo -i

```

rather than sudo -s

---

### Post by kris19 on 2014-07-14
Ah okay,

Just tried sudo -i to no avail, and the code I'm putting in is ```
/etc/nagios3/nagios.cfg -v
``` and it returns -bash: /etc/nagios3/nagios.cfg: Permission denied

---

### Post by steeldriver on 2014-07-14
Is /etc/nagios3/nagios.cfg actually an executable file? or a **configuration **file that you want to **edit**? if the latter, you should be specifying an editor to use e.g.

```

sudo nano /etc/nagios3/nagios.cfg

```

---

### Post by kris19 on 2014-07-14
No it's a configuration file that I want to verify before I can restart Nagios to let the changes I've already made come through. I've already edited it through ```
vim /etc/nagios3/nagios.cfg
``` and now all I want to do is verify it or I can't restart Nagios.

---

### Post by Vladlenin5000 on 2014-07-14
> **kris19 said:**
>  and now all I want to do is verify it or I can't restart Nagios.

What do you mean by "verify"? Conf files are editor using a text editor like you did, save, exit, done...

---

### Post by steeldriver on 2014-07-14
OK well I don't use nagios, but probably what you want is something like

```

**nagios3 **-v /etc/nagios3/nagios.cfg

```

(similar to running sshd -t to validate changes to an sshd_config file). The file name is probably optional if that's the default config file location.

---

### Post by SeijiSensei on 2014-07-14
The way to "verify" your configuration is to try starting up Nagios and dealing with any errors that it throws.  You get the "permission denied" error because you are trying to execute a file that is not executable.

---

### Post by kris19 on 2014-07-14
> Conf files are editor using a text editor like you did, save, exit, done...

The problem is I know that and wish it was that easy, I've edited the config expecting that to be it but no, I just get more errors thrown at me.

I got the idea of verifying into my head from the nagios webclient which is telling me "always verify configuration files using the -v command-line option before starting or restarting nagios."

I'm starting to go bald over this now...

---

### Post by Dragonbite on 2014-07-14
Wouldn't switching to the root user use ```
sudo su
``` and then continue with your command?

I think you can verify who you are currently (user or root) by typing ```
whoami
``` while ```
who
``` may or may not list you as root (as well as everybody else on the box at that time).

---

### Post by SeijiSensei on 2014-07-14
> **kris19 said:**
> I got the idea of verifying into my head from the nagios webclient which is telling me "always verify configuration files using the -v command-line option before starting or restarting nagios."

Does nagios have a command-line client?  Maybe that error means you should run "name_of_nagios_client -v" from the command line to see what errors are thrown.

By the way, passing that specific error string through Google finds this item in the Nagios documentation: [http://nagios.sourceforge.net/docs/3_0/verifyconfig.html](http://nagios.sourceforge.net/docs/3_0/verifyconfig.html)

Looks like that is the answer to your question.

If a program fails with an error string like this one did, searching Google for the error text should be your first step to diagnosing what's wrong.

---

### Post by yancek on 2014-07-14
> vim /etc/nagios3/nagios.cfg

I'm not sure if I am reading your post correctly but, it seems you edited this file and saved the changes and are a little 'paranoid' or worried the changes weren't saved, is that about it?  If that's all, use the same command to open the file and look for your changes.

If you are starting nagios and getting errors, it would help if you posted them here so someone familiar with it would be able to help.

---

