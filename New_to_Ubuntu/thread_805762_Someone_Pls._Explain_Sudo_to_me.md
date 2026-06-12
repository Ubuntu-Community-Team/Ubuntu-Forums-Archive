---
title: "Someone Pls. Explain Sudo to me"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by iggy00 on 2008-05-24
I moved to linux for more security over windows, for one reason. In windows, you log in as a user, and usually the user has administrative rights and can do anything. 

In linux, and especially ubuntu, I am finding out that there is this thing called "sudo." With sudo, you can grant rights to the user, just like in windows. That seems to make it less secure. 

For example, let's say I have a linux system with just a regular user, and no sudo. A person gets my password, and they can log in as me. But that's all they can do: wreck my files. They can't do anything really too damaging without the root password.

Now let's say I have a linux system where the user has sudo. A person gets my password and breaks in, and now they can do all kinds of damage with sudo that they couldn't do before. 

So I don't understand the purpose of this sudo. Sudo makes my linux computer more like an insecure windows computer, which is what I wanted to avoid in the first place. Can anyone comment on what am I misunderstanding? 

thank you

---

### Post by philinux on 2008-05-24
[http://www.psychocats.net/ubuntu/security#limiteduser](http://www.psychocats.net/ubuntu/security#limiteduser)

Explore this site.

---

### Post by eldragon on 2008-05-24
for starters, your password is your life, dont give it.

if you wish for people to have access to your files, then add them to your group, dont give them your password.


if you got hit by a security vulnerability in say, for example firefox, and it gets access to your userspace memory, this vulnerability will be boxed by your limited rights. it wont be able to infect your system (unless it knows of a way to escalate into systemwide privileges (like a second vulnerability in a process with systemwide rights in your system). but its much harder.

in linux, a user with no admin rights can do about anything a regular user on a working system needs to do, in windows, this is not possible, since normal computer usage usually needs write access to key system places, like program files or the registry.
so you should give users NO admin rights, unless you want them to configure your system for you.

when you use sudo, you got absolute power on what you can do with the system, its really handy when you need to fix / update a systemwide program. but you could still install regular programs without sudo (they will only be accesible by the user installing them).

sudo is here so that there is no need of a permament root user. which is a good thing, noone will be searching the web for answers to problems as root (and so, fall in a browser vulnerability that would give systemwide access to the attacker, since the browser is being run by root).

of course, with such a power, comes great responsability, **DO NOT** run scripts with sudo **WHICH YOU DO NOT KNOW WHAT THEY DO**. always wait for a couple of replies before running an unknown script from forums. see the rep of the user posting it. etcetera.

hope i cleared some points up :D

good luck

---

### Post by forrestcupp on 2008-05-24
There is nothing available in the world that can protect anyone if someone gets their password.  That's kind of like being upset that someone takes money from your account after you handed them your ATM card and gave them your pin #.

---

### Post by tom56 on 2008-05-24
> **iggy00 said:**
> So I don't understand the purpose of this sudo. Sudo makes my linux computer more like an insecure windows computer, which is what I wanted to avoid in the first place. Can anyone comment on what am I misunderstanding?

Treat your password as though it were your root password. If you do that it's no more of less secure than having a genuine root user.

---

### Post by iggy00 on 2008-05-24
okay, thanks to both. I guess from reading that link it is more of a philosophical difference. Personally, I *want* complete control over my computer with su/root. I can understand if someone feels uncomfortable with that, but with all respect I think that is more about them than about using root. 

also, not to split too many hairs, but this argument is speciousn and no really sound: 

> **So running as a limited user takes care of everything?**
Not exactly. This is a common argument made by Linux users, that if you run as administrator, your whole system can be borked, but if you run as a limited user, only your personal files can be damaged.

While that's somewhat true, personal files are usually more important to a user than system files. After all, I can reinstall Ubuntu in half an hour and have it running again the way I want it to within two hours. If I lost all my personal files, it would take me months to recreate a lot of them, and some I would not be able to recreate at all.

This is why it's really important to back up whatever files are important to you. 

that is not only "somewhat" true, it is completely true. Of course if someone were to hack the root password, they could 'bork' your personal files, too. they could delete the whole system, in fact. so your personal files are no safer with sudo than with su/root. using sudo doesn't protect your personal files in the least, so it's a faulty argument. 

just as i'm typing this, i notice forrestcupp also makes a logically faulty statement. it's what I hear all the time about sudo, which is why I thought I must be confused about something. he says: 

*"There is nothing available in the world that can protect anyone if someone gets their password. That's kind of like being upset that someone takes money from your account after you handed them your ATM card and gave them your pin #."*

I agree completely: if someone gets your password, that is bad. That's the whole point. But apparently a lot of the sudo users don't seem to understand the point that that is actually an argument AGAINST using sudo! Like I said, if they get your password (which we all agree is bad, no argument there), and you do NOT have sudo, you are relatively SAFER than if they get your password and you DO have sudo. If you have sudo and they get your password, you are potentially in a LOT MORE TROUBLE than if you do not have sudo. Without sudo, they can do everything your user can do. With sudo, they can do everything your user can do, PLUS whatever sudo things you can do. 

I guess I don't see what is so hard to understand about that, which is why I thought I must be missing something. thanks for the replies, not trying to start a flame war, just honestly thought I was misunderstanding something.

---

### Post by lazyart on 2008-05-24
The trick here would be to set the root password to something other than your user password.

And naturally you have to secure the machine as well, because rebooting into recovery mode puts you in the terminal as root, and all bets are off.

---

### Post by m_ad on 2008-05-24
> **lazyart said:**
> The trick here would be to set the root password to something other than your user password.

And naturally you have to secure the machine as well, because rebooting into recovery mode puts you in the terminal as root, and all bets are off.

this answered the question that I had..


when I setup ubuntu, it asked for my username/password. I think it must have automatically assumed the same password for root?

---

### Post by tom56 on 2008-05-24
> **m_ad said:**
> this answered the question that I had..


when I setup ubuntu, it asked for my username/password. I think it must have automatically assumed the same password for root?

No, there is no root password. Ubuntu doesn't activate the root account because it uses sudo to use the root account instead. This is also how Mac OS X tackles the same problem.

---

### Post by decoherence on 2008-05-24
This is a convenience thing about Ubuntu. Yes, it is one of the less paranoid, and therefore philosophically less secure configurations out there. Most Linux systems set up a root user and require you to use that password to access protected resources. So if someone gets access to your account password, they can steal and destroy your work, but they can't destroy the system.

> In windows, you log in as a user, and usually the user has administrative rights and can do anything. 

Which is no more or less secure than how it 'usually' works with Ubuntu. Except Ubuntu actually enforces authentication instead of merely asking "are you who you say you are?"

As lazyart said, achieving the result you want is simply a matter of setting a password for the root user.

sudo -s
passwd

now type 

visudo

and proceed to castrate you normal user account. Just comment out your user's line to remove all special access. Or check out some tutorials on configuring sudo to give your normal account access to specific programs only.

Your observation seems to be that the default configuration of Ubuntu (and specifically Ubuntu) is not to your liking, but it's quite easy to change.

---

### Post by iggy00 on 2008-05-24
> **decoherence said:**
> Your observation seems to be that the default configuration of Ubuntu (and specifically Ubuntu) is not to your liking, but it's quite easy to change.

yes, I just didn't know if I was missing some advantage of sudo, because to me it doesn't seem like an advantage. all the help pages, forum advice, etc. seems to assume you are using sudo, so I was wondering why I should keep it that way if I didn't like it. as long as it's just a different philosophy of doing things and not necessarily safer, I think I understand the issue better now and feel better about getting rid of it. thanks to everyone - wow, fast responses around here! :D

---

### Post by forrestcupp on 2008-05-24
I think I understand now.  You're not saying that su is safer than sudo; you're saying that you don't want su *or* sudo.  Saying su is safer than sudo is just illogical because once you give your password to su, you can do anything you want without entering the password again, which leaves room for accidental problems.  Sudo is exactly the same thing, only it asks for your password each time, which makes you think about what you're doing, eliminating some likelihood of mistakes.

But if you're saying that you would be safer without su *or* sudo privileges, all you need to do is set up an account without administrative privileges, and that user will not be able to use sudo at all.

---

