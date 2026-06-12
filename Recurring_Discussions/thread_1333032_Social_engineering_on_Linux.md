---
title: "Social engineering on Linux"
date: 2009-11-21
forum: Recurring Discussions
---

### Post by Cuco3 on 2009-11-21
This article, titled ["Is 2009 the year of Linux malware?" ]("http://stevehanov.ca/%7Esmhanov/blog/?id=60")explains how Malware can be ran on a linux computer that can trick the user into giving control of their system to the program.

What do you guys think? Is this a serious threat? I was able to edit all those folder locations without a password prompt for authorization (considering they're all in my home folder, my account has permission to those folders).

---

### Post by aysiu on 2009-11-21
Anything that compromises your system is a serious threat. In the case of social engineering, the user is the serious threat or security vulnerability.

---

### Post by Cuco3 on 2009-11-21
> **aysiu said:**
> Anything that compromises your system is a serious threat. In the case of social engineering, the user is the serious threat or security vulnerability.Question: wouldn't a web browser just need to be pointed to the site in order for the site to execute the malware? Or does the user need to download and run the program manually?

---

### Post by Cuco3 on 2009-11-21
Cmon dude, I posted 3 minutes after you replied. Don't go all quite on me after offering a rather vague answer. ;)

---

### Post by aysiu on 2009-11-21
> **Cuco3 said:**
> Question: wouldn't a web browser just need to be pointed to the site in order for the site to execute the malware? Or does the user need to download and run the program manually?
Read the link you posted.

In order for the malware to run, it has to be installed to your home folder first. Who do you think installed it? The user. The user somehow had to be tricked into installing that malware and making it executable.

That's social engineering. It doesn't look for a flaw in the operating system software. It looks for a flaw in the user using the operating system - gullibility.

For more details, read [Reminder: Social engineering still works on Linux](http://ubuntuforums.org/showthread.php?t=1120670)

---

### Post by Cuco3 on 2009-11-21
Well, I read it again, but they're not very clear, either.
[I]
"Once **malware has its grubby code all over your home folder**, you are one fake dialog box away from giving it complete control over your system:"  [/I]---- that suggests the Malware put the code there, not the user being tricked into putting the code.

*"If you have ever run a program or script that wasn't included in your distribution*" --- suggest that the user runs it. I remember in Windows the web browser (Firefox) being able to run the Spyware and infect Windows just by directing the browser to site.

I know what Social Engineering is, but that doesn't answer my question; I'm just interested to know if the browser can run + install the Malware by pointing it to the site, like in Windows.

Your answer suggests that the User must manually download the spyware and install it by your constant reference to Social Engineering.

Either way, I can see you're not quite sure of the answer either (or at least my question), but thanks anyway. Can anyone answer my Q, please?

---

### Post by aysiu on 2009-11-21
I'm absolutely sure of your question. You want to know if those codes can be executed by just visiting a website.

The answer is they cannot.

The code getting its grubby self into your home folder requires user action.

Now, there is a caveat here. No matter what web browser you use, there are always new flaws and security holes that get discovered and patched. Before they get patched, these flaws often involve the ability for a malicious site to execute arbitrary code. So if you happen to visit dodgy websites taking advantage of a particular flaw that has not yet been patched in your web browser and that particular dodgy site is also tailored to execute code specifically targeted at Linux, then, yes it's possible that your computer could be compromised.

That has nothing to do with Linux and everything to do with your web browser.

If you're that paranoid, use AppArmor and Firefox with NoScript, and I promise you you're more likely to be hit by a bus than have your computer compromised simply by visiting a web page.
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
[http://noscript.net/](http://noscript.net/)

---

### Post by NoaHall on 2009-11-21
It can't cause major damage (loss of unimportant files, perhaps, but not to the core system or applications).
If the worst comes to worst(.conf files in your home are edited to causes damage), then it can be fixed in 1 simple command. "add user new". Then login to "new". Problem gone.

---

### Post by Cuco3 on 2009-11-21
Thank you very much Aysiu and NoaHall! I understand now. :)

---

