---
title: "Ubuntu more unsafe than Open SUSE because of SUDO password policy?"
date: 2010-08-07
forum: Recurring Discussions
---

### Post by TheAlien on 2010-08-07
One person claims in a blog that Ubuntu is way less secure than Open SUSE. This is because the Ubuntu's default user account and SUDO shares the same password, unlike Open SUSE with separate default account and SUDO passwords. He claims that Ubuntu is therefore way less secure compared to Open SUSE, because a key-logger (for example) from malicious software can grab an Ubuntu machine's default account password and then get full root access trough SUDO.

Many people just use the Ubuntu's default account for everyday use. A workaround for this security hole in a default Ubuntu setup would be not to use the default account for any everyday and normal (Internet) use, except for system installs and updates, and instead create a new less privileged account for everyday and normal (Internet) use.

I haven't though about this actually. It scares me a bit, and it makes me want to run to Open SUSE. But I don't know if this is true and I would like some feedback on this issue first.

---

### Post by Bachstelze on 2010-08-07
This is rubbish. A keylogger could just as well record your root password on SuSE.

---

### Post by rookcifer on 2010-08-07
> **TheAlien said:**
> One person claims in a blog that Ubuntu is way less secure than Open SUSE. This is because the Ubuntu's default user account and SUDO shares the same password, unlike Open SUSE with separate default account and SUDO passwords.

OpenSuse doesn't use sudo (by default) at all, so that blogger is wrong.

>  He claims that Ubuntu is therefore way less secure compared to Open SUSE, because a key-logger (for example) from malicious software can grab an Ubuntu machine's default account password and then get full root access trough SUDO.

How does this person propose to get the keylogger installed?  A keylogger needs root (sudo) access to install itself.  It cannot install itself in a user account, contrary to popular belief.

> Many people just use the Ubuntu's default account for everyday use. A workaround for this security hole in a default Ubuntu setup would be not to use the default account for any everyday and normal (Internet) use, except for system installs and updates, and instead create a new less privileged account for everyday and normal (Internet) use.

If you wanna do that, that's cool.  But if you're going to do that on Ubuntu you need to do it on OpenSuse too because OpenSuse's default user account is also a member of the wheel (admin) group which means that the user can su to root.  There's *no* difference in that and how Ubuntu uses sudo by default.  The only difference is that on OpenSuse (and most other Linux distros) you type "su" while on Ubuntu you type "sudo."

> I haven't though about this actually. It scares me a bit, and it makes me want to run to Open SUSE. But I don't know if this is true and I would like some feedback on this issue first.

Basically your blogger doesn't know what he/she is talking about.

---

### Post by r2rX on 2010-08-07
So what establishes OpenSUSE as more secure than Debian/Ubuntu? Cause i've encountered quite a few articles that claim that OpenSUSE is the best for security.

One of my friends, at my old University, claims by OpenSUSE as well. One thing I do know is that Ubuntu doesn't have security programs installed by default (i.e SELinux or AppArmor).

Thus, what are the differences between Ubuntu and SUSE?

r2rX  :)

---

### Post by rookcifer on 2010-08-07
> **r2rX said:**
> So what establishes OpenSUSE as more secure than Debian/Ubuntu? Cause i've encountered quite a few articles that claim that OpenSUSE is the best for security.

One of my friends, at my old University, claims by OpenSUSE as well. One thing I do know is that Ubuntu doesn't have security programs installed by default (i.e SELinux or AppArmor).

Ubuntu has AppArmor installed by default.  Sure, there aren't many profiles enabled, but it's there.  You can download extra pre-made profiles from the repos and you can enable the Firefox profile which is already on your machine.

> Thus, what are the differences between Ubuntu and SUSE?


Very little where security is concerned.

If you want a mainstream distro that focuses more on out of the box security, then look into Fedora.

---

### Post by snowpine on 2010-08-07
> **TheAlien said:**
> One person claims in a blog...

I stopped reading there. :)

Defaults are just that. If your security needs are different from the default, Linux can easily be customized to your taste.

You should start by reading this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Rubi1200 on 2010-08-07
> **TheAlien said:**
> One person claims in a blog that Ubuntu is way less secure than Open SUSE.
 
If you are going to start a thread here with a line like that at least have the decency to link to the original article. 
 
I, for one, would like to read the original author's views in order to respond in an intelligent and coherent manner.
 
Finally, I concur with the viewpoints expressed by the previous posters and wish only to add that any operating system is only as weak or secure as you allow it to be.
 
Just my opinion :)

---

### Post by CharlesA on 2010-08-07
Original link would be nice. If you somehow got a keylogged installed, it needed root privlages to install, that means it already knows the sudo or root password. 

If you are really that paranoid about junk like that, just create a normal user then use **su** to change to the user with administrative rights whenever you need to do something that requires root permissions. Major pain in the butt tbh.

---

### Post by OpSecShellshock on 2010-08-07
User accounts that can use sudo are still normal accounts up until using sudo for an administrative task. At that point it doesn't matter that the password is the same because it has to be typed either way. On a single-user system it doesn't add any additional risk at all. Actually, it doesn't add any risk on multiple-user systems either unless people go around sharing their passwords and sessions. Even if it did present extra risk, there's no way to take advantage of it remotely unless there's a poorly configured server running.

---

### Post by TheAlien on 2010-08-07
I can only thank you for all your feedback! If you must have root access to be able to install a key-logger, then this blogger must be a troll or something. Please note that I'm from Windows, and on Windows you don't need administrative rights to install a key-logger.

---

### Post by CharlesA on 2010-08-07
> **TheAlien said:**
> I can only thank you for all your feedback! If you must have root access to be able to install a key-logger, then this blogger must be a troll or something. Please note that I'm from Windows, and on Windows you don't need administrative rights to install a key-logger.

Normally you do need admin rights, but since the default user on new Windows installs are admins, it might seem that they don't need those rights.

---

### Post by HPD2 on 2010-08-08
> **CharlesA said:**
> Normally you do need admin rights, but since the default user on new Windows installs are admins, it might seem that they don't need those rights.

To add to that, in windows 7 you need to allow a program to make changes to the system. You get a Yes/No prompt, as long as uac is enabled, that asks if you want to allow X program to do Y to your computer. If you do not have an admin account in windows 7 you get a box that prompts you for an admin password, similar to Ubuntu.

---

### Post by bodhi.zazen on 2010-08-08
> **TheAlien said:**
> One person claims in a blog that Ubuntu is way less secure than Open SUSE. This is because the Ubuntu's default user account and SUDO shares the same password, unlike Open SUSE with separate default account and SUDO passwords. He claims that Ubuntu is therefore way less secure compared to Open SUSE, because a key-logger (for example) from malicious software can grab an Ubuntu machine's default account password and then get full root access trough SUDO.

Many people just use the Ubuntu's default account for everyday use. A workaround for this security hole in a default Ubuntu setup would be not to use the default account for any everyday and normal (Internet) use, except for system installs and updates, and instead create a new less privileged account for everyday and normal (Internet) use.

I haven't though about this actually. It scares me a bit, and it makes me want to run to Open SUSE. But I don't know if this is true and I would like some feedback on this issue first.

Moved to recurring discussions. This has been discussed many many times, both in these forums and in various off site blogs.

There is no conclusive evidence that su is more or less secure then sudo, and the claim in the blog about a key logger or cracked account applies equally to su as sudo. If an administrative account is cracked, root access is not far behind, either via a key logger or other means (there are several methods all of which are trivial to execute).

The main advantage of sudo over su is:

1. Better logging.

2. su is all or none, sudo is far more configurable, allowing some commands to be run as root. 

See man sudo or man sudoers

[http://www.sudo.ws/sudo/intro.html](http://www.sudo.ws/sudo/intro.html)

No offence, but as has been mentioned already, most blogs are not the best source of security information, or at least you should confirm the source of the blog (some sites / blogs are obviously better then others).

---

### Post by Zorgoth on 2010-08-08
I can certainly create and run an executable, even make it run by default on my login without root access - so does Linux have some protection then against a user executable being able to log all keys?

---

### Post by bodhi.zazen on 2010-08-08
> **Zorgoth said:**
> I can certainly create and run an executable, even make it run by default on my login without root access - so does Linux have some protection then against a user executable being able to log all keys?

No, no OS has this kind of protection. If you write a key logger and execute it , it will by definition work on any OS.

Not to mention hardware key loggers which will also work on any OS. Some hardware key loggers are easier to detect (external) then others (internal).

Not to mention wireless/bluetooth which is a whole separate ball of wax, but of course those have a shorter range, but still wireless signals can be intercepted.

---

### Post by Tibuda on 2010-08-08
> **rookcifer said:**
> How does this person propose to get the keylogger installed?  A keylogger needs root (sudo) access to install itself.  It cannot install itself in a user account, contrary to popular belief.

Not really. It is not hard to install an app on the user home folder and launch it on login.

---

### Post by bodhi.zazen on 2010-08-08
> **danielrmt said:**
> Not really. It is not hard to install an app on the user home folder and launch it on login.

True ^^

---

### Post by rookcifer on 2010-08-09
> **danielrmt said:**
> Not really. It is not hard to install an app on the user home folder and launch it on login.

Do it then.  Write the code and post it here for evaluation.

---

### Post by KiwiNZ on 2010-08-09
> **rookcifer said:**
> Do it then.  Write the code and post it here for evaluation.

No.

---

### Post by Tibuda on 2010-08-09
> **rookcifer said:**
> Do it then.  Write the code and post it here for evaluation.

I'd get an infraction (Vader would kill me). But everything you need to mess is on your home folder.

---

### Post by Legendary_Bibo on 2010-08-09
> **rookcifer said:**
> Do it then.  Write the code and post it here for evaluation.

This is the code. Shhhh...don't tell the mods.

```

#!/usr/bin/env python

import keyboard
import some chocolate from germany (I'm hungry)

while keyboard_in_use = true:
    try l33t_h4x0rz_5k1llz:
        def(log_root_passowerd)
    if password_obtained = true:
        break

print "I am teh 3l33tz! I h4z H4x uR p4s5word!!!"

```

---

### Post by Zorgoth on 2010-08-09
My assessment on any situation involving a keylogger is this - if you have a keylogger installed on your system, your system is compromised.  No ifs, ands, or buts, su or sudo.  So there isn't a real difference.

---

### Post by Zorgoth on 2010-08-09
Out of curiosity, would it be possible to design a system where a keylogger would require root access to be installed?

My idea would be that only applications installed/authenticated by root would be able to tell what keys were being typed when they did not have keyboard focus, and "untrusted" programs would not be allowed to change keyboard focus, raise/lower/move/resize windows, or simulate  keyboard/mouse events - only the WM could do the window management for such untrusted applications.  

You would also need any process started by an untrusted process to be untrusted in the same way, since they could, for example, run "gnome-terminal -x my_evil_command," quite possibly without the user noticing.  

Also, probably it would be good to make it so letters and Shift+letters are not valid keyboard shortcuts for WM actions.

Would this be feasible?

---

### Post by bodhi.zazen on 2010-08-09
> **Zorgoth said:**
> My assessment on any situation involving a keylogger is this - if you have a keylogger installed on your system, your system is compromised.  No ifs, ands, or buts, su or sudo.  So there isn't a real difference.

In general this is true, but not always. There are legitimate uses for key loggers, it is just that as with any tool they can be abused as well.

---

### Post by Bachstelze on 2010-08-09
> **bodhi.zazen said:**
>  There are legitimate uses for key loggers

Namely?

---

### Post by sydbat on 2010-08-09
> **Bachstelze said:**
> Namely?Spying on employees.

I suppose you could also say they help you spy on your employees.

---

### Post by Bachstelze on 2010-08-09
> **sydbat said:**
> Spying on employees.

I suppose you could also say they help you spy on your employees.

And on your kids, and your spouse, etc.. True. I didn't consider spying as legitimate, my bad.

---

### Post by bodhi.zazen on 2010-08-09
"spying" or documenting , depending on your perspective I guess. I agree most people, myself included, find such tools intrusive and inappropriate (to say the least).

The first few lines on this page outline "legitimate" uses :

[http://www.bsacybersafety.com/threat/keylogger.cfm](http://www.bsacybersafety.com/threat/keylogger.cfm)

---

### Post by rookcifer on 2010-08-09
> **danielrmt said:**
> I'd get an infraction (Vader would kill me). But everything you need to mess is on your home folder.

OK, then send it to me privately and I will examine it and send it to some other coders.  I want to put this "user mode keylogger" thing to rest once and for all.

BTW, I am highly skeptical that a keylogger can be installed and be functional without needing to read/write root owned files.  However, some people whom I respect say it can be done.  However, no one has ever done it for some odd reason.  If it were so easy, why not?  That's my contention.

Again, I want to put this to rest with a POC.

---

