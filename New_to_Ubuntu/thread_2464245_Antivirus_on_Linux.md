---
title: "Antivirus on Linux"
date: 2021-06-27
forum: New to Ubuntu
---

### Post by jackdusty on 2021-06-27
Hi Guy's 

Whats you opinion about an antivirus program on Linux, I have heard many that say every desktop should have an AV protection and just as many say its not necessary, your views would be appreciated.





Thanks as always



Jack

---

### Post by dddman on 2021-06-27
I use browser protection

[https://addons.mozilla.org/en-US/firefox/addon/avg-online-security/](https://addons.mozilla.org/en-US/firefox/addon/avg-online-security/)

---

### Post by scorp123 on 2021-06-27
> **jackdusty said:**
>  I have heard many that say every desktop should have an AV protection... 

At work we have anti-virus on the Linux systems too... but not because we fear that Linux could be infected. It's more to stop Windows viruses from spreading. Because Linux systems might pass on infected files to Windows too, even if the Linux systems themselves are usually immune to those viruses. That's not to say that *"Linux is 100% safe"*. It is not. But Linux's security problems are *different* from Windows' security problems, e.g. they usually revolve around remote exploits, buffer overflows, unpatched systems that are vulnerable to remote attacks on network services that would be impossible if the system had been patched in time, etc.  Linux's security problems usually do not revolve around viruses ("virus" in the same sense as a Windows user would understand that term). 

The real question here is: What are you trying to achieve?

Are you trying to protect Windows systems from getting in contact with infected files? Then install anti-virus software on Linux systems too.

Are you trying to improve the security of your Linux systems? Then anti-virus software is borderline useless. You'd be better off subscribing to security mailing lists about "CVE" advisories and making sure all your Linux systems always have the latest patches. And make sure none of your Linux systems needlessly have any ports open towards the Internet, don't run any network service that you don't really need or use. And make sure the ones you do need and do use are properly configured and properly secured.

---

### Post by mIk3_08 on 2021-06-27
For me, This is not really necessary in Linux. If MS Windows really needs desktop antivirus it doesn't mean that Linux really needs it too. As far as I know; Linux Operating system is very different from MS Windows. Though Linux has minority of viruses and malware that exist for the operating system.
Linux is also known to be much more reliable than Windows or any operating system. In fact, On the official page of Ubuntu, a Linux based OS, it is said that Ubuntu is highly secure. A lot of people installed Ubuntu for the sole purpose of having a dependable OS when it comes to the security of their data and sensitive details. so, why you need av when it is not necessary.

---

### Post by monkeybrain20122 on 2021-06-27
+1 to mlk3_08. 

You don't really need AV in Linux, as for 'protecting Windows' I think it is a pretty poor reason. First of all Windows users should take care of their own security, I am not babysitting them. Secondly the kind of AV available on Linux (all for scanning Windows virus) are pretty bad anyway, clam comes to mind and that is garbage (on top of hogging your system's resource), if I really care about protecting Windows users I wouldn't count on it anyway, may as well tell Windows users to install a good AV software on their end.

---

### Post by Autodave on 2021-06-27
No AV used here.  I have a couple of machines open to the public.  Never had a virus in over 10 years.  Save you computing power for something useful.

---

### Post by scorp123 on 2021-06-27
> **monkeybrain20122 said:**
>  as for 'protecting Windows' I think it is a pretty poor reason. 

Management's decision, not mine. That's why I said: "at work".  At home I don't use any AV on Linux at all. What for? I'm not running anything that could get infected that way.

Managers are a funny illogical breed. The same kind of managers that mandates that AV software be installed on Linux are also the same managers who somehow forgot we still have some ancient Debian and Red Hat installations that have been EOL + EOS + unpatched for the last 10 years...

If anything bad were ever to happen then I'd expect those ancient EOL installations to be the first targets. There's so many potential attack vectors there... but none of which would be stopped by AV software  :D

---

### Post by monkeybrain20122 on 2021-06-27
> **scorp123 said:**
> Management's decision, not mine. That's why I said: "at work".  At home I don't use any AV on Linux at all. What for? I'm not running anything that could get infected that way.

Managers are a funny illogical breed. The same kind of managers that mandates that AV software be installed on Linux are also the same managers who somehow forgot we still have some ancient Debian and Red Hat installations that have been EOL + EOS + unpatched for the last 10 years...

If anything bad were ever to happen then I'd expect those ancient EOL installations to be the first targets. There's so many potential attack vectors there... but none of which would be stopped by AV software  :D

Managers are usually tech illiterate. :) Their firs priority is to get their behinds covered.

---

### Post by scorp123 on 2021-06-27
> **monkeybrain20122 said:**
> Managers are usually tech illiterate. :)

Very very much so. In their minds making sure there's *"AV software everywhere"* (even on Linux systems where this normally won't achieve much) is what will *"keep the company safe"*.  They totally don't understand that on Linux there are other security issues you should deal with first before getting worried by AV software ...

But oh well. :D

---

### Post by TheFu on 2021-06-27
Most security questions are answered in the "sticky" threads of the Security sub-forum here.
Lots of good security links there as well.

The only time I've run AV on Linux is when it was required by a contract for E&O professional insurance. The minute that client contract ended, I dropped the insurance and removed the AV.

There are people who will gladly accept your money for AV software running on Linux, but the system architecture and SOP makes AV unnecessary on Linux systems.  If you have daily, automatic, versioned, "pulled", validated and tested backups, then there is little reason to run AV that looks for Windows viruses on a linux system. Of course, you can run it on a file server accessed by Windows clients, if you like, but then why have Windows AV too?

The best AV is only 80% effective on any platform - most are closer to 50% effective, so a smart end-user is really a better solution. User training NOT to click links, not to visit suspicious websites, and not to open unexpected attachments is much more effective.  Plus, if an end-user doesn't have sudo or doesn't unlock sudo, there is really very little damage that a virus can cause to any Linux system.  About the worst they can do is delete all the files owned by the user.  But you have daily, automatic, backups, right?  Nothing will teach a user NOT to click on bad links faster than them freaking out because all their data is gone. They will be more careful going forward.

That's a good thing.

If management wants AV and you've spent 30 seconds trying to explain why it is a waste of time without success, then find the most expensive package you can find and recommend that. When they see it isn't $50, but $1500, then they might ask the better question, which is how can we mitigate these risks sufficiently so that AV isn't necessary. But the managers might not be the ones requiring AV. It could be part of a corporate insurance policy, then there is no choice.  Find the lightest AV you can.  Those contracts usually mandate a supported release, with current signatures, running on supported and patched OSes too.  That can be helpful when management doesn't want to upgrade that 4 yr old OS that is about to lose support. Contracts go both ways. Leverage them when you can.

And the answer is:
daily, automatic, versioned, "Pulled", validated, tested, backups.

Explain that "pushed" backups aren't as secure because the backup client has access to the backup storage.  Whereas with "pulled" backups, the backup server has access to the clients storage.  This is a 1000 clients to secure vs 20 backup servers to secure solution.  Give me the 20 backup servers, professionally managed, without any Luser's having access at all for security every day of the week.

---

### Post by math492m on 2021-06-28
i wouldn't use a Antivirus on Linux 

but if it makes you feel sefer then do it

---

### Post by Impavidus on 2021-06-28
> **TheFu said:**
> About the worst they can do is delete all the files owned by the user.

Or access sensitive information and pass it on to an outsider.

---

### Post by ActionParsnip on 2021-06-28
If you run an email or file server and want to protect Windows systems from each other then you should run antivirus, otherwise I wouldn't bother

---

### Post by TheFu on 2021-06-28
> **Impavidus said:**
> Or access sensitive information and pass it on to an outsider.

I consider exfil a different thing than a virus, but there are lots of ways for sensitive data to be leaked.  Any browser allowed to run javascript can leak data. [https://cloud.google.com/security/data-loss-prevention/preventing-data-exfiltration](https://cloud.google.com/security/data-loss-prevention/preventing-data-exfiltration)

I determined insider can do lots of damage easily.  Ask Snowden, regardless of the politics or right/wrong considerations.  

A CEO and IT guys at a company might be doing good by rotating a set of backups every week to an offsite location, but stop off at the grocery store, have their unencrypted disk/tape stolen from the vehicle, and thereby leak everything.  Companies have unencrypted laptops/phones stolen every day full of sensitive information - or automatic access into the corporate network.  
I've seen a team of thieves steal 2 smartphones while people were dining. Those phones were unlocked and had direct access into the corporate network (this was before policies caught up).  We traced those stolen devices from Europe - one ended up in central Africa and the other in Indonesia where the cellular companies don't honor blocking of stolen devices.  Not a big deal, right?  The information inside the contact DB was stolen. Some became targets for other illegal efforts, mainly spear phishing.

---

### Post by rsteinmetz70112 on 2021-06-28
I tend to run virus and spam scanners on a mail server. I also run a windows AV on the windows workstations, email is the primary way most viruses are spread and scanning it twice seems to me to be a reasonable precaution since scanners aren't 100% effective.

Just my 2 cents.

---

