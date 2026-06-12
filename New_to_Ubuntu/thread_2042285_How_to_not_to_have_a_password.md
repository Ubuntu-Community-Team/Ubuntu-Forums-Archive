---
title: "How to not to have a password?"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by NeoBoot on 2012-08-14
Quick question: how do I use Ubuntu without having a password? Autologin works, but having to type it each time I install something is annoying. The laptop belongs to me and me alone, so I don't worry about some other user scrambling my data.

---

### Post by Frogs Hair on 2012-08-14
Hello and Welcome

Though I wouldn't recommend removing the password because the possible of theft and possible exposure to something malicious on the internet you can look at the link and so a follow up search. 
  [http://askubuntu.com/questions/136264/ubuntu-12-04-lts-passwords](http://askubuntu.com/questions/136264/ubuntu-12-04-lts-passwords)

---

### Post by deadflowr on 2012-08-14
> **NeoBoot said:**
> Quick question: how do I use Ubuntu without having a password? Autologin works, but having to type it each time I install something is annoying. The laptop belongs to me and me alone, so I don't worry about some other user scrambling my data.

I agree with frogs hair, that even though you're the only user of your system locally, running a system without any password will leave your system just as vulnerable to remote attacks.If not more so, as someone can easy take full control of your system and even lock you out. Running without a password will allow anyone at anytime to have freewill with your data, regardless to whether they are sitting directly at it, or half a planet away.
However, aside from a very basic length requirement, passwords can be as dumb-down(weak) or complex(strong) as you want them to be.

---

### Post by wildmanne39 on 2012-08-14
Hi, I have seen many posts and people can not install applications or run commands that need privileges after removing there password, so I believe you will break your system.
Thanks

---

### Post by mansonfan78 on 2012-08-14
You could also follow the instructions here: [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)  to change how often you're asked for a password.  That way, you still have a password but it won't bug you as often.

---

### Post by cryptotheslow on 2012-08-14
wildmanne39 is right.

Setting your main / admin privilege account to have no password causes all manner of problems when running Ubuntu. Every time a graphical prompt for authorisation pops up (some software updates, user or group changes etc.) they will not accept no password or a blank password and you end up stuck without resorting to command line to get things done - which will defeat the time savings you think you made by not having a password.

You could run as root - but how to do so is not allowed by this forum as it is not the Ubuntu way.

Unless you thoroughly understand how to completely jail your applications using apparmour, selinux or some other sand-boxing technique - I'd humbly suggest that you don't know enough to know why what you are asking to do is very dangerous to yourself.

I know that sounds like an asinine reply, it really wasn't meant that way :/

---

### Post by HermanAB on 2012-08-15
Hmm, the short answer is: Don't do that.

and the longer part:
...since you will eventualy be very sorry you did, where eventually can be anything from minutes to months.

The problem is that the scenario you describe of you being the only user of your system, is a falacy that only applies to a standalone mechanical typewriter with no network connectivity.

---

### Post by Moose on 2012-08-15
Is it that hard to type in your pw when you install stuff? I agree with everyone else. Take your password off and your pc will be more vulnerable to crap.
 
-Anarchy

---

### Post by NeoBoot on 2012-08-15
> **deadflowr said:**
> I agree with frogs hair, that even though you're the only user of your system locally, running a system without any password will leave your system just as vulnerable to remote attacks.If not more so, as someone can easy take full control of your system and even lock you out.
But how the heck is anyone supposed to get on my machine? Does Ubuntu run terminal services by default with my user account being allowed to connect remotely? If that's true, then the problem is not my wish to use Ubuntu without password but the insecure setup.

---

### Post by Elfy on 2012-08-15
You will not get support for running your system without any password here.

Sorry

---

### Post by Wim Sturkenboom on 2012-08-15
> **NeoBoot said:**
> But how the heck is anyone supposed to get on my machine? Does Ubuntu run terminal services by default with my user account being allowed to connect remotely? If that's true, then the problem is not my wish to use Ubuntu without password but the insecure setup.There are always vulnerabilities that can be exploited.

> **Elfy said:**
> You will not get support for running your system without any password here.
Ha, a new rule on the forum? Or just your personal opinion. If the former, please provide a link.

---

