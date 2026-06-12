---
title: "How much of a security risk could the sudo timeout become?"
date: 2008-02-27
forum: Recurring Discussions
---

### Post by aysiu on 2008-02-27
I'm not trying to spread FUD about Ubuntu's *sudo* implementation. I'm trying to understand it.

If I'm recalling correctly, the default is a 15-minute timeout from the first time you authenticate with *sudo* before you're prompted for a password again on another *sudo* command. Although it doesn't carry over into another terminal shell, it will carry over to other GUI applications, so if I launch Synaptic and authenticate during that launch, I don't have to authenticate with GDM setup or other *gksudo* programs for another 15 minutes.

I've never heard of this 15-minute timeout being exploited, but could it be?

And, if so, what would that exploit look like? Would it take advantage of some Javascript-related vulnerability in Firefox? How would an outside party be able to launch a *gksudo* or *sudo* command, and is there a way they could know that you were in the midst of the 15-minute grace period?

---

### Post by The Cog on 2008-02-28
It could be exploited. If you use (say) synaptic and then go to get a coffee then someone could sneak in and use any of the administration programs. It's not somethng that worries me too much.

Another thing I have noticed is that sometimes I SSH to a server and then use sudo, then disconnect after making the change I needed to. If I SSH back in within a short time (I assume its 15 minutes) then this **new** login doesn't have to give a password when using sudo. That feels utterly wrong to me but when I think about it, I needed to know the password to log in anyway so it doesn't really matter. Except that because I have expexted a password challenge and not looked at the screen, I have occasionally typed my password into a root bash prompt and thereby left it in bash_history. It's a good job my password isn't rm -rf /.

---

### Post by aysiu on 2008-02-28
> **The Cog said:**
> It could be exploited. If you use (say) synaptic and then go to get a coffee then someone could sneak in and use any of the administration programs. It's not somethng that worries me too much. I wasn't really thinking about a person physically walking up to your computer while you're away from it. I was thinking more about some kind of network-related breach. If someone has malicious intent, a little know-how, and physical access to your computer, your computer's pretty much compromised anyway.

---

### Post by astrotech226 on 2008-02-28
> **aysiu said:**
> I wasn't really thinking about a person physically walking up to your computer while you're away from it. I was thinking more about some kind of network-related breach. If someone has malicious intent, a little know-how, and physical access to your computer, your computer's pretty much compromised anyway.

I don't think there's much to worry about a network-related breach using sudo.  They would have to be able to run commands to do that.  If that was possible now, people could open up gedit and calculator on your screen.

Unless we see some remote code execution exploit, I really think they would need physical access.

---

### Post by aysiu on 2008-02-28
> **astrotech226 said:**
> 
Unless we see some remote code execution exploit, I really think they would need physical access. But aren't many of the flaws in Firefox (granted, usually patched within a week or a few days) related to remote code execution?

---

### Post by deepclutch on 2008-02-28
hrmm...then how the remote exploit work?atleast the hacker on the other end should know about sudo and esp should care about Linux as a whole too :lol: 
BTW,I too am curious about other "ways" other than browser that a hacker can get into ur system :-|

---

### Post by astrotech226 on 2008-02-28
> **aysiu said:**
> But aren't many of the flaws in Firefox (granted, usually patched within a week or a few days) related to remote code execution?

Yeah.  I guess they are.  I keep thinking about it in a way that if they perform a buffer overflow, they can only execute the code they supply.  But there's no reason that code couldn't run arbitrary commands.

---

### Post by aysiu on 2008-02-28
> **deepclutch said:**
> hrmm...then how the remote exploit work?atleast the hacker on the other end should know about sudo and esp should care about Linux as a whole too :lol: 
BTW,I too am curious about other "ways" other than browser that a hacker can get into ur system :-|
I don't really know. That's why I'm asking.

I'm hoping someone who knows the details of how exploits work can shed some light on this.

---

### Post by bodhi.zazen on 2008-02-28
It could be exploited either via physical access (and as you mentioned physical access = bust anyways) or remote access either via a VNC connection (shared desktop) or if they can authenticate to your X session (crack into X), for example it you are sloppy with Xhost.

Here is a *brief* overview of X security

[http://www.stderr.org/doc/lskb/html/10000100/kben10000106.html](http://www.stderr.org/doc/lskb/html/10000100/kben10000106.html)

Be very careful with X host and/or any type of VNC server you (may) run. Cracking into X is like physical access, if they can do that they likely already have root access (or means of user privilege escalation -> root)

---

### Post by aysiu on 2008-02-28
> **bodhi.zazen said:**
> It could be exploited either via physical access (and as you mentioned physical access = bust anyways) or remote access either via a VNC connection (shared desktop) or if they can authenticate to your X session (crack into X), for example it you are sloppy with Xhost.

Here is a *brief* overview of X security

[http://www.stderr.org/doc/lskb/html/10000100/kben10000106.html](http://www.stderr.org/doc/lskb/html/10000100/kben10000106.html)

Be very careful with X host and/or any type of VNC server you (may) run. Cracking into X is like physical access, if they can do that they likely already have root access (or means of user privilege escalation -> root)
So if you go with the Ubuntu defaults (not enabling a VNC server of some kind), then there's no danger of the timeout being exploited by a third-party? Even through some kind of browser exploit?

---

### Post by bodhi.zazen on 2008-02-28
I would not say no danger, how about minimal danger ? The primary risk is a misconfigured server (VNC or Xhost) or the cracker already has root access, and can thus crack into your X.

Depending on your level of paranoia, consider creating  a restricted user for daily access. You can then su to your admin user in a terminal and sudo or gksu from there. Yea it takes an additional step, but you can "protect" your admin account by using a restricted account for daily activity.

---

