---
title: "Any module/program similar to Android SuperSU?"
date: 2016-09-26
forum: Recurring Discussions
---

### Post by bombastic2 on 2016-09-26
I first tried Linux some 10+ years ago with I think Mandrake but disappointed with limited third party softwares support.

Fast forwards to today, I found stunning large repos in official or non-official repos such as AUR, PPA where I have no problem finding almost anything I need. A good time to switch back to Linux, I think.

However, what really annoys me is the outright annoying POLKIT password prompt for every single admin task, every software add/remove. This is far more ridiculous and worst than Windows Vista UAC that so many users complaints about!

I know I can get rid of it by "root ALL=(ALL:ALL) NOPASSWD: ALL". 

Thanks in advance for security risk warning. But I know the balance between UX(user-experience) and security measures.

Locking my door with 20 locks does make it more secure, but it is annoying and ridiculous.

I do find Android implementation of superuser or Windows 7 and above UAC more elegance and user-friendly than constant "stupid" password prompts. 

Is there a program similar to Android SuperSU available to Linux? Where we can simply grant SU to a program we are running with just mouse click?

Example: Allow 'Synaptic' root access for: This session only - 20 minutes - permanently.

If there is no such program exist, I pray some highly trained programmers here will write one and upload to the official repo.

Another rant is, opened windows don't seem to remember last state. Every time I fire up a program, like PCMANFM, DOLPHIN, NAUTILUS, LXTASK......etc. they will always reset to default state: positioned to top-left and sometimes to default windows size. 

I have to drag the opened windows to center and resize every single time. In Windows platform, this never happen.

What config I can set to make it behaves like what I want(the last state)?

Thank you all!

---

### Post by TheFu on 2016-09-26
sudo does what you want already. Just need to set it up.  You can specify which commands should always "just work without bothering you."  You can even specify the specific options allowed to those commands, if you want. [https://askubuntu.com/questions/39281/how-to-run-an-application-using-sudo-without-a-password](https://askubuntu.com/questions/39281/how-to-run-an-application-using-sudo-without-a-password) has a detailed answer and there is always the sudoers manpage with even more details.  It really is an amazing manpage - one of the best I've ever seen.

Linux is highly flexible, even when we choose to do something odd.

BTW, if you use the GUI, you only get 10% of the power from the OS. Use the CLI for the other 90% - that applies to Windows which is more 50/50, not 10/90.

Also, did your mother ever tell you that "You catch more flies with honey than you do with vinegar."

---

### Post by DuckHook on 2016-09-27
*Thread moved to **Recurring Discussions** as the more appropriate forum.*

This topic has been beaten to death so many times that it now qualifies as a zombie. I intend to get involved only this one time and note the following:

> **bombastic2 said:**
> &#8230;I know the balance between UX(user-experience) and security measures.&#8230;actually, I highly doubt that you do, as evidenced by your next few statements&#8230;> Locking my door with 20 locks does make it more secure, but it is annoying and ridiculous.&#8230;a false analogy if there ever was one. If your idea of authentication is the equivalent of redundant door locks, then you don't understand the role or purpose of authentication.> I do find Android implementation of superuser or Windows 7 and above UAC more elegance and user-friendly than constant "stupid" password prompts.&#8230;this not only confirms your misconception of what authentication does&#8213;it cites the worst possible examples to undermine your point. The fact is that Windows is a cesspool of malware precisely because it chooses to enable user laziness and sloppiness over proper security, and Android has quickly turned into another malware cesspit because it breaks the very security model that you are ranting against: one that gives Linux at least a fighting chance.> Is there a program similar to Android SuperSU available to Linux? Where we can simply grant SU to a program we are running with just mouse click?

Example: Allow 'Synaptic' root access for: This session only - 20 minutes - permanently.

If there is no such program exist, I pray some highly trained programmers here will write one and upload to the official repo.This is Linux, which was founded on the principle that if you consider such an app valuable, you are free to write it yourself. TheFu has already given you relatively simple instructions that will allow you to destroy Ubuntu's security model completely if that's what you are after. However, if you expect the community to actually *cater* to your security shortfalls and break our *collective* security model just to validate your misconceptions&#8213;that ain't happenin'.> Another rant is, opened windows don't seem to remember last state. Every time I fire up a program, like PCMANFM, DOLPHIN, NAUTILUS, LXTASK......etc. they will always reset to default state: positioned to top-left and sometimes to default windows size. 

I have to drag the opened windows to center and resize every single time. In Windows platform, this never happen.

What config I can set to make it behaves like what I want(the last state)?Chat subforums are not the place for such a help request. I would suggest that you post a separate and specific help request on only this issue in the General Help forum. However, I caution you against continuing in your rant mode. This is a forum of volunteer Linux enthusiasts. You are unlikely to get useful, polite, or even any responses with the strategy that you have been using. And, like all posters, you are expected to adhere to the [Forum CoC]("https://ubuntuforums.org/misc.php?do=showrules")

---

