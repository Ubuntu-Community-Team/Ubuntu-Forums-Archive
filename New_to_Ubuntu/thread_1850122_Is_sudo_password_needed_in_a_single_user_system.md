---
title: "Is sudo password needed in a single user system ?"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by linuxyogi on 2011-09-25
Hi,

I am the only user of both my PCs. In other words no one other than me has physical access to those PCs.

So, is there a need for sudo password ? This topic may have been discussed before but I want new (2011) views & ideas.

My suggestion, sudo should ask for a  password only in case of of a app installation/removal.

Why not follow WIN 7 ?  Just asking for confirmtion, no need to enter password.
  
You guys think ......

---

### Post by xtjacob on 2011-09-25
Well it could be useful in the event your system was compromised from an outside source. If you don't have a sudo password, then they could do many nasty things. If you do have a sudo password, then they won't get very far, unless they figure it out.

---

### Post by lisati on 2011-09-25
I agree that the requirement for a password can sometimes seem counter-intuitive on a single-user system. 

I haven't bothered disabling the requirement for a sudo password on my system. For me, the benefit of doing so is that I have a safety net against the possibility of doing something silly. It doesn't remove PEBKAC errors completely but it can slow me down.

---

### Post by linuxyogi on 2011-09-25
@[xtjacob]("http://ubuntuforums.org/member.php?u=654317")  @[[COLOR=#d40000]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635")

Why not follow WIN 7 ???

 Just asking for confirmtion, no need to enter password.

---

### Post by hansdown on 2011-09-25
Hi linuxyogi.

Are you considering a password-less login?

That is o.k., if you feel safe, that your machine is not used by anyone else.

You still need to authenticate all installs.

Running as root though, is not advisable.

Hope I understood you correctly.

---

### Post by linuxyogi on 2011-09-25
> **hansdown said:**
> Hi linuxyogi.

Are you considering a password-less login?

That is o.k., if you feel safe, that your machine is not used by anyone else.

You still need to authenticate all installs.

Running as root though, is not advisable.

Windows7 runs as root. Not too secure.

Hope I understood you correctly.

No, my PCs are are already configured for auto login.

I am not at all in favor of running as root.

All I am sugesting is Ubuntu just ask a yes or no confirmation (Like WIN 7) instead of asking for the sudo password everytime.

^ Will that compromise security ?

---

### Post by xtjacob on 2011-09-25
Couldn't a hacker just write a script to hijack it and answer yes every time then, thus bypassing the end user?

---

### Post by thatguruguy on 2011-09-25
I've already had a laptop stolen.  Never again will I have a PC that doesn't have passwords.

---

### Post by linuxyogi on 2011-09-25
> **xtjacob said:**
> Couldn't a hacker just write a script to hijack it and answer yes every time then, thus bypassing the end user?

If thats a possibility, I don't have a problem with entering passwords:lolflag:

---

### Post by hansdown on 2011-09-25
> **thatguruguy said:**
> I've already had a laptop stolen.  Never again will I have a PC that doesn't have passwords.

That is my way of looking at it, too, thatguruguy.

---

### Post by linuxyogi on 2011-09-25
> **thatguruguy said:**
> I've already had a laptop stolen.  Never again will I have a PC that doesn't have passwords.

Sorry to hear that. My suggestion was limited to Desktops.

---

### Post by Frogs Hair on 2011-09-25
Passwords are optional on Windows , but using a strong password for each account user or administrator is suggested . I am a single user but I have never found using passwords annoying . I do understand it could be for some users .

---

### Post by BlinkinCat on 2011-09-25
> **Frogs Hair said:**
> Passwords are optional on Windows , but using a strong password for each account user or administrator is suggested . I am a single user but I have never found using passwords annoying . I do understand it could be for some users .

I don't have any problem using passwords either - :)

---

### Post by hansdown on 2011-09-25
```
All I am sugesting is Ubuntu just ask a yes or no confirmation (Like WIN 7) instead of asking for the sudo password everytime.

^ Will that compromise security ?
```

It would, if you login, then leave your computer unattended.

---

### Post by linuxyogi on 2011-09-26
> It would, if you login, then leave your computer unattended.

How ? I am not selecting Yes or No so the process (even if malicious) remains stuck.

Its a different issue in case of updates. I always update as soon as they appear.

---

### Post by technosysind on 2011-09-26
I would also recommend that you carry on with passwords. Just stops you from making any unwanted change.

---

### Post by mcduck on 2011-09-26
I would never even consider managing any computer connected to the Internet (or any other network) like a single-user system.

At best it's a system you are *trying to* keep as a single-user system. And that's where features like password confirmation for admin tasks are important.

---

### Post by mcduck on 2011-09-26
> **linuxyogi said:**
> How ? I am not selecting Yes or No so the process (even if malicious) remains stuck.

Its a different issue in case of updates. I always update as soon as they appear.

Key presses and mouse movements can be simulated through software and scripts. A mere mouse click to confirm an admin tasks definitely is not a security feature.

---

### Post by Paqman on 2011-09-26
> **linuxyogi said:**
> 
I am the only user of both my PCs. In other words no one other than me has physical access to those PCs.


No one else may have physical access, but billions of computers and people have access to your machine through the internet. Do you trust every single one of those billions of people? If so, then you don't need a password.

---

### Post by linuxyogi on 2011-09-26
> **mcduck said:**
> I would never even consider managing any computer connected to the Internet (or any other network) like a single-user system.


NO, I was not talking about single user system s like Puppy Linux. 

> **mcduck said:**
> 
At best it's a system you are *trying to* keep as a single-user system. 

Yes that's what I meant.

> **Paqman said:**
> No one else may have physical access, but billions of computers and people have access to your machine through the internet. Do you trust every single one of those billions of people? If so, then you don't need a password.

But isn't Ubuntu locked (all ports) by default & ufw makes it even more secure. So why the concern ?

---

### Post by haqking on 2011-09-26
> **linuxyogi said:**
> 

But isn't Ubuntu locked (all ports) by default & ufw makes it even more secure. So why the concern ?

All ports are closed by default in that no services are listening on any, when you add or start a service then you can use UFW/GUFW if you wish to protect them, UFW/GUFW is merely an interface to IPTables/netfilter which is the built in firewall in the kernel.

Passwords exist regardless of a single user, as it prevents services or scripts running under admin privelege.

regardless of any security layer, the user is the weakest link in any system.  As soon as you connect your machine to the outside world then it is not a single user system (or at least has the potential to no longer be)

Use passwords, use strong complex ones, use SUDO

---

### Post by linuxyogi on 2011-09-26
> **haqking said:**
> 

Use passwords, use strong complex ones, use SUDO

Already doing that atm. I type my complex password whenever asked.

---

### Post by haqking on 2011-09-26
> **linuxyogi said:**
> Already doing that atm. I type my complex password whenever asked.

cool then the, should sudo password be used question is a moot point.

It exists to help keep the canonical security model's integrity intact.

Security is a layered approach and is a process not a product. Use as many layers as feasible without compromising usability, Passwords/passphrases being a fundamental layer.

if you remove them then you are opening a window to allow all the bugs and nasties to fly in and annoy you ;-)

---

### Post by philinux on 2011-09-26
> **linuxyogi said:**
> Hi,

I am the only user of both my PCs. In other words no one other than me has physical access to those PCs.

So, is there a need for sudo password ? This topic may have been discussed before but I want new (2011) views & ideas.

My suggestion, sudo should ask for a  password only in case of of a app installation/removal.

Why not follow WIN 7 ?  Just asking for confirmtion, no need to enter password.
  
You guys think ......

On windows the advice has always been to not connect to the net as the admin user but as a limited user. To limit damage caused by malware etc from using browser. Ubuntu in effect does this. I'll keep my single user system at the default settings. YMMV. :p

---

