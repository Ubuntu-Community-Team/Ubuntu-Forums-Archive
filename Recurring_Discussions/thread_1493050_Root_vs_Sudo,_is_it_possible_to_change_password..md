---
title: "Root vs Sudo, is it possible to change password."
date: 2010-05-25
forum: Recurring Discussions
---

### Post by p2bc on 2010-05-25
I have a two part question really. The first part is to stimulate a discourse, to clear out the cobwebs and get the mind thinking. The second part which is directly related to the first, is the one I am looking to answer.

What is the point of root? What can root do that sudo can not do. My understand of it is this, the only difference between the two is that one is for a set period of time where the other is recursive. 

Everywhere you look, time and time again you get the warnings, be careful with root. You can to irrepitable damage to your system as root. So much so Ubuntu disables the account all together from start up. So in an overly simple example it is like walking around with a loaded gun. As root you walk around all the time with the gun strapped on, as sudo you have to go strap it on each and every time you need a gun. Correct me if I am wrong but in both cases you still can shoot your foot off.

What I am trying to say is, sudo is just as dangerous. So is it possible, and if not why not, for a user to be a sudo user but have a different password for sudo than for his standard password. Fundamentally creating a root user, but for a set period.

The problem as I see it. If user "X" works in an office, and you all know this can happen, user "Y" looks over his shoulder and see him log into his computer and sees his password "password" (super secure, recommend it to everyone), and for simplicity sake user "X" is a sudo for that computer. So it make no difference that there is no root account for that computer, that computer can be compromised by user "Y".

So now my scenario, if user "X" logs in, and user "Y" sees it, sure user "X" personal information can be accessed by user "Y", but if user "X" sudo has a different password at least the system is still safe. User 'X" sudo password being used less often and therefore less likely to be discovered, making it more secure than just user "X" password.

To use my gun example again, sure you can strap on the gun when you need it, but you still need to go get the bullets and load the gun. Which is just that more secure. One does not automatically mean the other.

So is it possible to have a different password as a user, and sudo user on the same system???


*[SIZE=1]wow that was long winded, just want to make sure it was clear.[/SIZE]*

---

### Post by philinux on 2010-05-25
See this.
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

And these for further explanation.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Thread moved to Recurring Discussions.

---

### Post by James78 on 2010-05-25
[quote="p2bc"]What I am trying to say is, sudo is just as dangerous. So is it possible, and if not why not, for a user to be a sudo user but have a different password for sudo than for his standard password. Fundamentally creating a root user, but for a set period.[/quote]I'm not entirely sure, but the configuration for sudo is in /etc/sudoers, you can edit the file with sudo visudo. [Here's a tutorial to it.]("http://ubuntuforums.org/showthread.php?t=1132821")

---

### Post by aysiu on 2010-05-25
> **p2bc said:**
> So in an overly simple example it is like walking around with a loaded gun. As root you walk around all the time with the gun strapped on, as sudo you have to go strap it on each and every time you need a gun. Correct me if I am wrong but in both cases you still can shoot your foot off. To use your analogy, using root would be like walking around with loaded guns pointed in every direction when you're trying to shoot only one target. Sudo, however, allows you to pull out your gun only when you want to shoot, and then it pulls out only one gun pointed at one target. Far less dangerous, since you will shoot only what you intend to shoot.

> What I am trying to say is, sudo is just as dangerous. It's not really, as I just explained above.

>  So is it possible, and if not why not, for a user to be a sudo user but have a different password for sudo than for his standard password. Fundamentally creating a root user, but for a set period. Check out this thread (the solution lies within):
[Different login and sudo passwords](http://ubuntuforums.org/showthread.php?p=1053358#post1053358)

> The problem as I see it. If user "X" works in an office, and you all know this can happen, user "Y" looks over his shoulder and see him log into his computer and sees his password "password" (super secure, recommend it to everyone), and for simplicity sake user "X" is a sudo for that computer. So it make no difference that there is no root account for that computer, that computer can be compromised by user "Y". If security is really that important, don't let user "Y" look over user "X"'s shoulder.

Or, if the "it's for security purposes" people are correct (hint: they are not), just type the password in the terminal, because there's no way without asterisks or dots as feedback that user "Y" could possibly look at the keys you're typing and remember at least some of them. Of course not.

---

### Post by libssd on 2010-05-25
One of my favorite computer books, *Linux and the Unix Philosophy*, by Mike Gancarz, has this memorable quote (comparing Atari and Unix OS):

> The Atari approach suggests that if the average person is given a gun, he is likely to shoot himself in the foot. By contrast, the UNIX system effectively hands the user an assault rifle, plugs in 20 rounds, and points it at his foot.
Using sudo, the assault rifle is in single-shot mode; using su, you're on full automatic, so you can screw up more faster. I resisted sudo at first, but have come to appreciate the extra safety net it provides. It's *possible* to change the root password, but not *neccessary*. I have decided I like the extra margin of safety.

---

### Post by p2bc on 2010-05-25
[LEFT]@James78

That was awesome, it does not answer my initial question but to lock down security even more and tailor it more specifically, very nice.

@aysiu

> 
To use your analogy, using root would be like walking around with loaded  guns pointed in every direction when you're trying to shoot only one  target. Sudo, however, allows you to pull out your gun only when you  want to shoot, ...
I disagree, because if i cd into /etc is doesn't matter if:
```

# rm *
-or-
$ sudo rm *

```It is still confined to the /etc folder, but will do a hell of alot of damage.

Once you do sudo anything and put you password in, you have 15 min to do what ever you want, granted you have to place sudo in front, but sudo rm or sudo cp will still work.
Yes as root you can do more autonomous self destruction, like a script can once launch.
I am talking more basic level here.

Here is the long story, but I will _try_ to keep it short. I am setting up my office. As of right now, I work by myself. I will be needing new employees soon. A secretary to answer the phone, book keep to keep things in order, someone to take over the design department. All of which will be running linux on their stations in some flavour or another. At the same time I am planning for the future. I do believe the designer for instances need sudo access to install new update and software as needed. At the same time I don't think the secretary and the accounting department need to access sudo privileges at all, but do realized that there maybe times that their system needs to be worked on locally or remotely. Also, nothing saying at the beginning they won't share a computer between the secretary and accountant.

> 
Or, if the "it's for security purposes" people are correct (hint: they  are not), just type the password in the terminal, because there's no way  without asterisks or dots as feedback that user "Y" could possibly look  at the keys you're typing and remember at least some of them. Of course  not.
Sure, but none of the people I mention in my scenario will be comfortable enough with linux desktop to begin with let alone the terminal

The question as I posed it, never was intended with malicious or hacker intent, because again like we all know, with they really want to get in they will get in, my question was more general local users. If Mr. Secretary sees Mr. IT guy logging into his computer to do some routine maintenance , or Mr. Designer guy, and discovers his password, a password that can compromise the whole system... It just got me to think, why are sudo passwords, and user password (those part of admin group) the same. If we are so conscious to make the system more secure by disabling root account, why not different passwords.

[SIZE=1]again long winded, starting to see a pattern here.[/SIZE]
[/LEFT]

---

### Post by aysiu on 2010-05-25
[QUOTE=p2bc;9358775
@aysiu

I disagree, because if i cd into /etc is doesn't matter if:
```

# rm *
-or-
$ sudo rm *

```It is still confined to the /etc folder, but will do a hell of alot of damage.[/QUOTE] You're not disagreeing with me. I didn't say you couldn't do anything stupid with sudo. I said with root you have guns pointing in all directions, but you're just trying to shoot one target. With sudo you have one gun pointing in only one direction trying to shoot one target.

If you aim at the wrong target, that's your problem.

But if you have only one gun, and you're aiming at the right thing, you're far less likely to inadvertently shoot something else you weren't aiming for.

---

### Post by p2bc on 2010-05-25
@aysiu and @elamericano

Thank you, that link and instructions worked as I have envision. I would consider it a work around, but one that works none the less. With the link James78 posted it has potential to be a very secure.

Thank you all.

---

