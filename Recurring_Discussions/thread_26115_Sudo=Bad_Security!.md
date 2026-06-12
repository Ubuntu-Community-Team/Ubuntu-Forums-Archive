---
title: "Sudo=Bad Security!"
date: 2005-04-11
forum: Recurring Discussions
---

### Post by Xgates on 2005-04-11
This sudo thing, it's bad security, someone gets into the user account then they have your box simpler than if there was a root password on it. Having that root password means twice the effort is needed to get root on the box, now with people using Ubuntu only as sudo, all a cracker needs to get is the user account to gain control. Ubuntu needs to let people know about this, and that they can have a root password on the box and run it in a proper more secure way, and not something like this sudo ONLY thing going around thought for the sake of all the windows users, moving over to Linux, trying to make it easier, for the sacrifice in security.

And if the Ubuntu thinking here was to keep people from logging into their box as root then this is not good Unix teaching. RULE 1# is taught in Linux, you don't log in as root, and this needs to be taught in Ubuntu, not just trying to make the box eaiser by just having sudo as default to keep them from root logins, because this is for the sake of all the Windows newbies, wanting to be some wannabe Unix user looking for a easy way out, this not good Unix, or the Unix way, or did someone here forget we are running a Unix based OS.

Yes of course if the noobs log into the box as root by mistake the security is at a greater risk, but then you are suppose to be taught you NEVER login to Linux as root anyway, so what are we doing here, side tracking good thinking that is correct for a simpler way to keep people from doing this all in the name of security when after all the box is more insecure when running as sudo only as well.

Lets get back to the REAL basics, and start teching the newbies the CORRECT way, not by trying to make things easier for them,  but educating them, especially when you are compromising the box by doing it when this is not correct.

Teaching never login as root with a REAL box that has a root account, this is the Unix way! I mean PLEASE what are we running Windows here?

You get a TISK TISK for bad thinking --->  [-X

---

### Post by HungSquirrel on 2005-04-11
> Teaching never login as root with a REAL box that has a root account, this is the Unix way! I mean PLEASE what are we running Windows here?
The sudo method is nowhere near as bad as the Windows method of making all accounts passwordless administrator accounts by default.  Heck, with sudo at least you have to put in a password before you do something stupid.  Windows should implement something similar in Longhorn where the Administrator should have to input a password every time he does something that could mess up the system (install/remove/configure software/hardware, run Windows Update, etc.).  Many of the problems associated with Windows would be less severe if they did what Ubuntu does.  So, don't ever compare Ubuntu and Windows; Windows is MUCH worse!

---

### Post by dabeej on 2005-04-11
1. A normal user doesn't have high priv alone. Meaning, they would need to authenticate using sudo to do anything. With root, you don't need anything. Once you have root access, it's pretty much done.

2. You aren't really considering anything in mind other than physical access, look at whole thing and then make assumptions of bad security practices. Seeing how most security attacks are for and against root accounts with weak passwords. This atleast that problem. Also if anyone gains any local access to the box, they can pretty much do anything they want. If they acquire access remotely from the user acount with their password (through a trojan), then the way they did that is most likely the users fault.

3. Read the ubuntu security documentation for more reasoning why they did what they did.

Don't make assumptions. Security is a sensitive field.

---

### Post by TravisNewman on 2005-04-11
There's STILL only one password to crack to get root access
In this case, it's the user's password-- in other cases it's the root password. If you make your password complex, it's just as hard to crack as a root password. So what's the big deal?

Also, sudo prevents you from accidentaly doing something you don't want, OR keeping root sessions open, which are both security issues, even if only security from yourself.

---

### Post by HungSquirrel on 2005-04-11
> There's STILL only one password to crack to get root access
In this case, it's the user's password-- in other cases it's the root password.
Well, that depends.  For example, it's considered more secure if you disable root logins via FTP, SSH, etc.  In remote login scenarios with root logins disabled, having to crack two passwords (user, then root so you can su) makes the system more secure.

> Also, sudo prevents you from accidentaly doing something you don't want, OR keeping root sessions open, which are both security issues, even if only security from yourself.
These are my favorite features of sudo.  With a sufficiently paranoid timeout, sudo can be quite the system saver!

---

### Post by nocturn on 2005-04-12
1. You should *never* log in as root, even on non-sudo systems, you log in as a user and use su for root.
2. Never, ever send a password over a non-encrypted connection.

Sudo helps for security because it forces the root user to use least privileges when doing stuff, and not leaving logins open.
Condisder this:
$ ./configure; make
$ sudo make install

instead of running the configure and make as root to, it doesn't need it.

Another benefit of sudo is logging.  Every sudo command gets logged, so it is easier to find out later if something bad happened.  

Do you have any data to back up your claim that a root user is safer then sudo?

---

### Post by nocturn on 2005-04-12
The safest, but less comfortable way IMO is to have a userID you use to sudo from (different from your working ID).  When you need to do root stuff, log in with the sudo user and run the commands from there.

---

### Post by r00t on 2005-04-17
Are you suggesting that:

```

%admin  ALL=(ALL) NOPASSWD: ALL

```

isn't safe?  :lol:

Mark

---

### Post by wmcbrine on 2005-04-18
[QUOTE=Xgates]now with people using Ubuntu only as sudo, all a cracker needs to get is the user account to gain control.[/QUOTE]
Nope -- they need the password, too. There's a difference: it's possible in some circumstances to get into a user account without knowing the password, but that won't help you if you want to sudo. (Users can't even read the hashed passwords in /etc/shadow; and if they could, they'd still need to crack them.)

By inactivating the root account, Ubuntu removes one obvious target for crackers. Consider: guess root password vs. guess user name AND password. Of course you can disable root logins and achieve a similar effect. But I think the Ubuntu system is a win, overall. It discourages casual use of the root account, which is the *biggest* security hole in a non-sudo system. And it's not incovenient to use when you do need it.

BTW, for what it's worth, Mac OS X works the same way. (Indeed I'm surprised at how much the two systems have in common. Right down to the little swirly circle "hourglass" in Hoary... but I digress.) Windows is quite different, and trying to run it securely is kind of a pain.

---

### Post by s0c0 on 2005-05-01
Meh, it's not a big deal.  If you are worried than just do a sudo passwd root and start using your root account.  That's what I've done since I perfer the more traditional way.

Secondly, I don't think the Ubuntu distribution is meant to be a production server.  Sure I use it for my web server and a few other things, but I doubt I would ever setup a Ubuntu server for a client.  Ubuntu comes with too much crap on it's default install (but thats great for end-users). Thats what Slackware and BSD are for.

---

### Post by TravisNewman on 2005-05-02
wmcbrine-- exactly. it's much harder to break into a user account and guess the password than to break into the root account, since you don't need to pw to break into a root account, or any others. sudo, most importantly, makes you less of a danger to yourself as well.

---

### Post by nocturn on 2005-05-02
[QUOTE=s0c0]
Secondly, I don't think the Ubuntu distribution is meant to be a production server.  Sure I use it for my web server and a few other things, but I doubt I would ever setup a Ubuntu server for a client.  Ubuntu comes with too much crap on it's default install (but thats great for end-users). Thats what Slackware and BSD are for.[/QUOTE]

Yes, it is.  Ubuntu is meant to be a drop-in system for datacenters (from the wiki).
You can install a mean and lean system by using a custom install and choosing server.

---

### Post by Gandalf on 2005-05-02
[QUOTE=s0c0]Meh, it's not a big deal.  If you are worried than just do a sudo passwd root and start using your root account.  That's what I've done since I perfer the more traditional way.

Secondly, I don't think the Ubuntu distribution is meant to be a production server.  Sure I use it for my web server and a few other things, but I doubt I would ever setup a Ubuntu server for a client.  Ubuntu comes with too much crap on it's default install (but thats great for end-users). Thats what Slackware and BSD are for.[/QUOTE]
 well install with server option and you won't have that what you call crap :D i run ubuntu server and it's quiet cool!!!!
about sudo and the security issues he mentioned above, well as everyone said before, my opinion is that it is more secure, first the Sudoers users haven't standard names, a non-sudo distro well all attackers will try to crack the root account but on a sudo system, they have to try both user and password which make it even an impossible task, don't you think?!?!?...

and please please don't compare ubuntu to windows, because windows is crap shit, ubuntu ruleZZZZZZZZ!!!!! (and of course it's my opinion, i don't care also about other opposit opinions!!! )

---

### Post by goofrider on 2005-05-02
I think the orginal poster raised a valid point, and there are common assumptions about passwords that can be dangerous on an sudo system.

Traditionally, we have a very strong root password, and users have weaker passwords (out of convinience). However, on an sudo system, it must be stressed that every sudoer must have a user password as strong as what they'd use for a root password, otherwise, their user accounts would be a single weakness of the password chain. Not every sudoer may realize that 

This situation can become even more dangerous if you have many (10-20) sudoers, all using weak passwords without understanding the danger. Now instead of just one root password to crack, there are 10-20 weak passwords to crack.

What needs to be stressed are:

 * Keep sudoers at a minimum
 * Every sudoer account should be treated just like a root account
 * Every sudoer must have a strong password
 * Every sudoer must understand the implication of being an sudoer

---

### Post by Gandalf on 2005-05-02
well exactly, but an sudoer account must know already this, since he has been given a sudo access!!! w don't give sudo access to newbie, he must be a super user to get sudo account, know what i mean?

---

### Post by nocturn on 2005-05-02
[QUOTE=goofrider]
1 * Keep sudoers at a minimum
2* Every sudoer account should be treated just like a root account
3* Every sudoer must have a strong password
4* Every sudoer must understand the implication of being an sudoer[/QUOTE]

1) The same number of people that would normally get the root pw of the machine
2) Yes and no, you have to guard the password to the account with the same effort.  The good thing is if you forget to lock the screen (or log out), someone accessing the terminal cannot get root (without knowing your password).  This is acutally safer then logging in as root (something I have seen many times)
3) A good password policy is always a must.  
4) Yes, every sudoer should be capable of being root in any case.  Actually, this puts sudo at an advantage over giving several people root  because actions are logged (unless you sudo su -, but this is also logged).

---

### Post by s0c0 on 2005-05-02
[QUOTE=nocturn]Yes, it is.  Ubuntu is meant to be a drop-in system for datacenters (from the wiki).
You can install a mean and lean system by using a custom install and choosing server.[/QUOTE]

Hmmm... I wasn't aware of the server option.  I stand corrected, thanks!  I'll have to look into that.

---

### Post by dataw0lf on 2005-05-02
[QUOTE=s0c0] Slackware and BSD are for.[/QUOTE]

Slackware?? I didn't realize anybody still used it.  

*shakes his head sadly*

---

### Post by s0c0 on 2005-05-03
[QUOTE=dataw0lf]Slackware?? I didn't realize anybody still used it.  

*shakes his head sadly*[/QUOTE]

The guy sitting next to me swears by "the slack."

---

### Post by pdpi on 2005-05-03
[QUOTE=s0c0]The guy sitting next to me swears by "the slack."[/QUOTE]
 I also swear by the slack. Just not for all systems. I'm running Ubuntu on an Athlon 64 3500+ with 1 gig RAM. That's great, my system just plain rocks, and uses memory much more intelligently than windows. On my laptop, a poor lil' celeron 400 with 160 MB RAM, Ubuntu just makes the system crawl, much like Windows would. In that system, I run slackware. Handpicked packages, none of that automount thing, no nothing. Just the basics I need to work. I use fluxbox as my window manager. It's all configured for minimalism. And it works smoothly. With firefox, xmms, gvim and a ton of terminals open, I have like 70 megs of memory load, most due to firefox.

I must correct my statement. I swear by Linux. No distro is intrisicly better than another. Each has its own use.

---

### Post by syndicate on 2005-05-04
Guys, the entire point of sudo is to be able to delegate certain tasks to other junior administrators on full multi-user systems and not entrust them with the root password.  In addition to delegation, sudo frees you from changing the root password when an employee leaves the company.  

Giving everyone ALL=(ALL) ALL is a patently bad idea and it's (hopefully) not used this way.  Only one or two administrators should have this ability.  sudo is indispensible in medium to large environments.  

The old style of using "su" and disclosing the root password thinking is obsolete and should be frowned upon.  [-X

---

### Post by LordHunter317 on 2005-05-04
**NB:**This will be a very long-winded post, as I'm going to respond to everyone 's factual and logical mistakes. If you want to see my take on Ubuntu's policy, scroll to the end.
 
 > **Xgates]This sudo thing, it's bad security, someone gets into the user account then they have your box simpler than if there was a root password on it.[/quote]No, it doesn't. A password is a password. I just have to get the right password.
 
>  Having that root password means twice the effort is needed to get root on the box,No, it doesn't. It just means I have to get the root password instead of the user's password.
 
You're operating under the assumption that a root password will be harder to steal than a user's password. Realistically, that's rarely true. Most people who you could persuade to give you their account password would also be willing to give you the root password. Even if they know the importance of root. This is what social engineering is all about.
 
And if you remove the human factor, stealing one password becomes as equally likely as stealing another: you're relegated to brute-force style attacks. At which point, attempting to gain root is no harder than gaining a user's password. At least these days, anyway.
 
>  now with people using Ubuntu only as sudo, all a cracker needs to get is the user account to gain control.And all they need without sudo is to get the root password.
 
You're making the false assumption that a root password is somehow automatically more secure than a user's password. It's not. It's security still depends on the exact same factors. So without a compelling reason to believe that a root password is more secure, you're whole argument is reduce to illogic.
 
>  like this sudo ONLY thing going around thought for the sake of all the windows users, moving over to Linux, trying to make it easier, for the sacrifice in security.It's not a sacrifice, it's a distinct trade with good points and bad points. Just like having a root account has good points and bad points. I'll go over the benefits/costs of both below.
 
> And if the Ubuntu thinking here was to keep people from logging into their box as root then this is not good Unix teaching.I think it was to remove the need to use the account interactively as much as possible, or at least minimize it to the greatest extent possible.
 
Which is a sound security principle, and is taught by nearly every Linux introductory guide on the planet. UNIX too, if the guide is competently written (read: not for IRIX).
 
>  wanting to be some wannabe Unix user looking for a easy way out, this not good Unix, or the Unix way, or did someone here forget we are running a Unix based OS.Yes it is. sudo isn't a Linux creation. All the BSDs have it. It runs on every commerical UNIX on the planet.
 
> Yes of course if the noobs log into the box as root by mistake the security is at a greater risk,If it's a greater risk, then why encourage the practice. Unless there's some benefit (which you've failed to mention) this statement is contradictory.
 
>  but then you are suppose to be taught you NEVER login to Linux as root anyway,Except when you have to. This line of thinking is impossible to achieve, so you can't use it as an argument here.
 
> Lets get back to the REAL basics, and start teching the newbies the CORRECT way,You haven't shown how having a root account for interactive use is the correct way. And the enterprise would tell you that you're generally wrong. Enterprise systems, especially those that are co-sysadmined, tend to not have root access at all. The password is set to something fendishly long and locked away in a safe, and no one using the system knows it. Everyone uses sudo for any privileged access. 
 
 The only difference is their policy tends to be tighter than the one used in Ubuntu.  But I'll cover that as well, below.
 
>  especially when you are compromising the box by doing it when this is not correct.It's not compromising the box. sudo isn't some instant root-kit vector or something. You clearly don't understand what it's capable of, or how to apply it to a security scenario.
 
> Teaching never login as root with a REAL box that has a root account, this is the Unix way!Yeah, and guess how you do it ***survey says***: sudo.  
What other way do you purpose to do privileged tasks? Short of coming up with some sort of terrible hack using capabilities, or RBAC or MAC using SELinux or similar applications, there is no other solution. And you certainly don't suggest those alternatives so I'm forced to conclude you didn't intend for us to use them, either.
 
> You get a TISK TISK for bad thinking --->  [-XNo, you do, as it's patently obvious you didn't think this rant through before posting.
 
[quote=HungSquirrel]Windows should implement something similar in Longhorn where the Administrator should have to input a password every time he does something that could mess up the system (install/remove/configure software/hardware, run Windows Update, etc.). Many of the problems associated with Windows would be less severe if they did what Ubuntu does.[/quote]No, this is also incorrect. There are basically two cases to consider: home users and enterprise/corporate users.

[list=1]
[*]For home users, they're just going to enter the password anyway. It's not an effective deterrent to make them stop doing what they want to do said:**
> For corporate users, they can't do those privileged things anyway, so it's irrelevant.
[/list]Passworded access to privileged is good for proving you are who you say you are. It's also useful in case of an account compromise through means other than a password; the attacker only has access to the account, not the privileged functions available through sudo, as they've failed to compromise it.
 
 Since many daemons have to run as a user to access the user's files (and this i more secure than running as root) this is an important security consideration. It's also one reason why sudo requires a password to perform privileged tasks: it prevents privilege elevation in the event of an expolit of one of these daemons.
 
[quote=dabeej] Seeing how most security attacks are for and against root accounts with weak passwords.No, they're not. On UNIX and Linux, most security exploits don't involve passwords at all.
 
> **panickedthumb]If you make your password complex, it's just as hard to crack as a root password. So what's the big deal?[/quote]Actually, password complexity is meaningless since the advent of rainbow tables. Length is the only variable that determines how hard a password is to crack with a rainbow table. And rainbow tables for passwords up to 14-characters in length can be purchased, and the password cracked in a matter of minutes.
 
This is an aside, but an important one. While rainbow table attacks aren't terribly widespread yet (and only useful in the event of a compromise of /etc/shadow or wherever your passwords are stored) they do show that ironically, password "strength" is a mostly meaningless exercise.
 
>  Also, sudo prevents you from accidentaly doing something you don't wantNo, it really doesn't. The idea that having to type a password before you run a command is going to make you less likely to run the command is a fallacy. Hell, sudo doesn't even prompt you every time by default.
 
If you decide you're going to run something, having a password prompt isn't going to make you think twice. And even if it will make you personally think twice, it won't make everyone think twice, so it's not a very good argument for using sudo.
 
[quote=HungSquirrel]In remote login scenarios with root logins disabled, having to crack two passwords (user, then root so you can su) makes the system more secure.[/quote]Only slightly. Performing the same "hard" task twice is a linear increase in difficulty. Which may be a sufficent deterrent. But given that most exploits (ignoring social engineering) aren't password related, this isn't a great reason to justify having a root account w/ password, although it is a valid one.
 
It still comes down to: "Is the root password going to be any harder to acquire than the user's password?" The answer to that is generally no when you have a passworded root account.
 
 [quote=nocturn] Condisder this:
  $ ./configure said:**
> Sadly, this is a false example, as I can do that just as easily with su:```
./configure
 make
 su -c "make install"
```So this isn't a reason to use sudo either.
 
> The safest, but less comfortable way IMO is to have a userID you use to sudo from (different from your working ID).You're going to provide support for this. Once again, unless you can show compromising that account to be harder, it's not true.
 
> **wmcbrine]There's a difference: it's possible in some circumstances to get into a user account without knowing the password,Most circumstances, realistically. Most exploits aren't password related. 
 
> (Users can't even read the hashed passwords in /etc/shadow said:**
> Cracking them is trivial once /etc/shadow is gotten. Very trivial, in fact.
 
[quote] By inactivating the root account, Ubuntu removes one obvious target for crackers.System daemons still run as root and are still compromisable. The next correct step is to implement RBAC or MAC via something like SELinux.
 
[quote]Consider: guess root password vs. guess user name AND password.Guessing a username on a box is pretty trivial. Certain usernames are extermely common, and you have a very high chance of guessing it correctly. Certainly high enough that if you were going to randomly brute-force systems for weak passwords (e.g., that SSH brute-force attack that's been going for several months now) the username isn't a problem.
 
[quote=wmcbrine]exactly. it's much harder to break into a user account and guess the password than to break into the root account, since you don't need to pw to break into a root account, or any others[/quote]What you say here makes no sense. You either need the password, or a piece of software to exploit. Software exploits aren't a relevant reply to his comment.
 
[quote=goofrider]Traditionally, we have a very strong root password, and users have weaker passwords (out of convinience). However, on an sudo system, it must be stressed that every sudoer must have a user password as strong as what they'd use for a root password, otherwise, their user accounts would be a single weakness of the password chain.[/quote]While what you say is true, as I've pointed out twice before, the importance of password strength now is almost irrelevant. In the event of an /etc/shadow compromise I already know your password. By the time you've figure out that the compromise occured, I will have already accessed every account on the compromised system.
 
While strong passwords are still important to resist random-brute force attacks like the one I mentioned above, you don't need two levels of strenght. The password simply needs to be strong enough to resist certain basic levels of brute-forcing. Unprivileged user passwords should be that strong to, to prevent compromise of the system among other vectors.
 
[quote=nocturn]4) Yes, every sudoer should be capable of being root in any case. Actually, this puts sudo at an advantage over giving several people root because actions are logged (unless you sudo su -, but this is also logged).[/quote]No, they should not. Ideally, no one should be able to get a root shell at all, as that breaks the audit trail. And I've seen systems implemented where this is the case: root shell access was impossible, and only a select few of the people who could run sudo could change /etc/sudoers.
 
 Anyway, now that train wreck is over, let's talk about the **realities** of Ubuntu's sudo decision. It has advantages and disadvantages, which I'll cover in turn. Specifically, compared to the traditional interactive root account way.
 **Advantages:**
 
[list]
[*]It's more convinent for the home user. They don't have to remember two passwords, and they don't have to login in a completely seperate session to perform privileged tasks (ala Windows).
[*]It does provide an audit trail for actions performed. Note in this specific that this would be useless in the case of an intrusion, as an attacker could easily wipe the log. However, it is useful for debugging and other purposes.
[*]It allows for more fine-grained control over system privilege, though Ubuntu currently doesn't do this. Something which needs to be changed. Even a Windows XP level of administrators and users would be sufficent.
[/list]**Disadvantages:**
 
[list]
[*]In the event of a password compromise, it does mean the attacker has a full access to the system. However, this isn't as bad as it sounds. Realistically as I said above, the most common methods of gaining a password are going to yield the root password just as easily as the user's password. As such, this is **not a realistic disadvantage**.  I'm going to say that again, as people will ignore it:
 
**The above point is *NOT* a realistic disadvantage** to Ubuntu's method.
[*]It doesn't limit the user's ability to perform privileged tasks in any way, which has benefits beyond security.  To be fair, **having a root account has this same disadvantage**.
[/list]As much as I'd like to see the sudo policy be more than it is, that's not a workable solution with just sudo. This would require taking away more control than is possible from the user. It might be a workable solution using SELinux + sudo or similar, but that is sometime off. Even then, I'm not sure I'd be comfortable shipping a desktop distribution like that.
 
 So it looks to me like the sudo method has some positive advantages, and the only disadvantages it has are shared with having a root account anyway.
 
The simple fact of the matter is that the security of a password comes down to one thing and one thing only: the user who holds it. Holding two passwords instead of one doesn't make anything more secure unless the user treats one password more secure than the other. In this day and age, that's not really a very sensical policy, unless the user is capable of memorizing >14 character passwords. In which case, they could just memorize one long password instead of two.

---

### Post by wmcbrine on 2005-05-05
> **LordHunter317]Guessing a username on a box is pretty trivial. Certain usernames are extermely common,[/quote]I can't agree with that, unless you mean "users" like daemon, mail, or nobody. You might be able to guess a username *if* you knew the real name(s) of (some of) the user(s), or their account names elsewhere said:**
> [Quote=wmcbrine]exactly. it's much harder to break into a user account and guess the password than to break into the root account, since you don't need to pw to break into a root account, or any others[/quote]Um, that wasn't me, it was panickedthumb.

---

### Post by LordHunter317 on 2005-05-05
[QUOTE=wmcbrine]I can't agree with that, unless you mean "users" like daemon, mail, or nobody.[/quote]Look at the brute-force SSH attack that's be ongoing for a very long time now.  It uses precanned usernames (e.g., bill, bob, jill, administrator) and gets enough hits to obviously still be worth running. 

> Of course it also depends on the size of the system. I get the impression you're thinking of a big one, with a lot of user accounts to choose from. Me, I'm thinking of my own boxes, with only 1-3 regular accounts each.Obviously your odds of sucess with random guesses go up as the number accounts increase.

But the point still is:  if I randomly attacked only the account "john" on boxes on the Internet, I'd still probably get enough hits to be worth my while.  

If my goal is a specific machine, then trying to learn the username first instead of randomly guessing might be worthwhile.  But the reality of it is that you're more likely to be hit by a random-guess attack then one targeted specifically at your account and machine.

> Or do you mean "a box" as in "*some* box, out of a large pool" rather than "any given box"? That may be, but it's not really relevant to the individual user.It still is, just less so.  Your box is on the Internet, right?  That's a large pool of boxes.

> Um, that wasn't me, it was panickedthumb.My apolgoies.  It's hard to review a post that long and be sure everything is correct.

---

### Post by sprucio on 2005-05-08
I'm not so sure if sudo = bad security but I can certainly say that having sudo is starting to get on my nerves.

Luckily, we are able to change this easily but I wanted to ask, what security threats posses this machine now that it had sudo? It certainly looks like the default account that's created has been given some power and I would like to thoroughly understand how this is achieved in this distro.

BTW, is there an full online doc on how Ubuntu works? I've tried searching for docs and even though they are helpful, I haven't seen a full documentation on Ubuntu.

---

### Post by LordHunter317 on 2005-05-08
[QUOTE=sprucio]but I can certainly say that having sudo is starting to get on my nerves.[/quote]Running a root shell is no less annoying unless you have to do multiple tasks.  In which case, you can easily run 'sudo -s'.

> Luckily, we are able to change this easily but I wanted to ask, what security threats posses this machine now that it had sudo?If you just re-enable the root account, you effective have two passworded root accounts.  Compromise of your password or the root password means that the system has been fully compromised.

As I showed eariler, how much of an actual real-world risk that is a matter of some debate.   If your passwords are "strong" and you are responsible with them, you probably haven't increased your risk in any measurable way.

> It certainly looks like the default account that's created has been given some power and I would like to thoroughly understand how this is achieved in this distro.Via the /etc/sudoers file, like always with sudo.  I'm sure that's not the answer you want, but I don't understand the question, either.

---

### Post by Burgundavia on 2005-05-08
The biggest gain in security is not with the system but with the user. The reason most people log in as admin (or a user with those rights) on Windows is that it is a pain to log in and log out again just to do something like installing a piece of software. Sudo allows the user root/admin access when they need, without getting in the way much, which is good, otherwise they would log in as admin to save the trouble.

So basically, it makes it more secure by making common admin tasks easier to perform in a secure way.

Corey

---

### Post by elsewhere on 2005-05-08
[QUOTE=Burgundavia]So basically, it makes it more secure by making common admin tasks easier to perform in a secure way.[/QUOTE]

This is the point I like about sudo.  Hackers and crackers don't concern me, since more often that not, I'm the single biggest threat to my own system and have done more damage in the past than I care to admit when running under su.  At least sudo is a conscious extra step on my part, particularly if I run a command that requires root access when I may not have been expecting it.  I like to think it's inflicting some form of good practise on me.

Besides, I agree with what LordHunter was saying (at least, what I think he was saying, that was a lonnnggg post  ;) ), I can't imagine why my root password would be more secure if someone could obtain my personal one.  And if they gain physical access, it really doesn't matter either way.   

Of course, that's just my $0.02 for my situation.  I don't run with open ports and am already behind a very secure firewall when on the net, so I'm not concerned about casual drive-by attempts from the net for hacking my system.  I guess everyone has a different measure of where they stand on the secure vs convenience curve....

Cheers,
KV

---

### Post by nocturn on 2005-05-09
[QUOTE=LordHunter317]
 Sadly, this is a false example, as I can do that just as easily with su:```
./configure
 make
 su -c "make install"
```So this isn't a reason to use sudo either.
[/QUOTE]

You are correct, and many people already use su for this, but in reality, a great number of people just log in as root and run all commands like that.  
When logged in as unprivileged user (and sudo rights) you automaticly tend to type the extra prefix only when needed.

---

### Post by elamericano on 2006-05-26
Would it be any better to have a different password for sudo access? I have also been bothered that the same password to get into my most used account also gives sudo access. Maybe this would be roughly equivalent to what someone suggested about using a sudo enabled account only when necessary - only in this case, you would use the sudo account, but only the second password rarely.

[http://www.ubuntuforums.org/showthread.php?t=181877&page=2](http://www.ubuntuforums.org/showthread.php?t=181877&page=2)

---

### Post by Mano[FA] on 2006-05-31
I thank LordHunter317 for the big answer (it's nice to be aware of security risks and understand how sudo works)
I'm concerned by the same point of elamericano. Sometimes I have to log in by ssh or ftp by a remote computer I know very little about and that could be not secure (like using ftp on Windows IE that uses not encript password or on a sistem that could be keylogged and so on...) of course I do nothing as sudo in that case, but compromising my user account means compromise all the system. I'm thinking about work as a non non-sudo user and make a sudo user only for administation tasks, but it would also be nice to have 2 different password (one for logging, one for sudoing). Is the suggestion of  elamericano (see the link, page 2) safe enought? What should be better to do in my case?

---

### Post by RavenOfOdin on 2006-06-07
[QUOTE=Xgates]This sudo thing, it's bad security, someone gets into the user account then they have your box simpler than if there was a root password on it. . . .

You get a TISK TISK for bad thinking --->  [-X[/QUOTE]

Oh God, hasn't this been covered already and shot down numerous times?

---

### Post by Gowator on 2006-06-08
[QUOTE=elamericano]Would it be any better to have a different password for sudo access? I have also been bothered that the same password to get into my most used account also gives sudo access. Maybe this would be roughly equivalent to what someone suggested about using a sudo enabled account only when necessary - only in this case, you would use the sudo account, but only the second password rarely.

[http://www.ubuntuforums.org/showthread.php?t=181877&page=2](http://www.ubuntuforums.org/showthread.php?t=181877&page=2)[/QUOTE]
Obviously not since you don't understand it!

The sudoers file contains 
ALL:ALL this means any account can run as root including www-data, mysql or any other daemon account.  
Firefox or any web browser connects as YOUR account .. if it runs a CGI as sudo root it runs it as root.  

Ubuntu is fundamentally flawed .. the sudo policy is a advert for crackers.  
If I open my ports on a default Ubuntu account I get upwards of 50,000 **attacks per day** using simple brute force.  

Most users can work out how to deny root access but setting up a secure sshd is more complex... and most don't even try.  

Ubuntu is set to become the number one crackers target because at least XP users have worked out that they need a decent firewall whereas all we hear on Ubuntu forums is "don't mention sudo or we will lock the topic...". 

yeah great way to address security!  take the sand out of your ears and listen for a moment, if the real world is too frightening you can always stick your head back in the sand....

The point is most people will stick with defaults, they don't have time to secure everything and by giving every user root privs once they crack that users password is asking for problems....

I suggest everyone try their /var/log/auth.log and have a look...

---

### Post by Gandalf on 2006-06-08
Ehem... don't forget www-data and such have /bin/false as shell so even if they come, I don't think they can do much ;)

---

### Post by Gowator on 2006-06-08
> **Gandalf]Ehem... don't forget www-data and such have /bin/false as shell so even if they come, I don't think they can do much  said:**
> 

They can do less but how about whatever user you use to connect via firefox or p2p?  

Simple test try gmail, yahoo mail etc. etc. and see if that user has access to upload a file?  
Yep they have access to the entire filesystem ...

Don't forget www-data has access to CGI and scripts.... so they just need to run a sudo from the CGI ....

However 50,000 attacks per day is also just a drain on resources and since is obviously being targeted because of the pre-installed rootkit ...  

However why not search the blacklists .. why is it so many Ubuntu machines are compromised?  
I guess its a mix of
1) noobie users
2) pre-installed rootkit once they have a single account
3) The security approach of Ubuntu which seems to be never ever discuss the sudo policy.  

[QUOTE]I can't imagine why my root password would be more secure if someone could obtain my personal one. 
Well of course if you have a password length of 64+ for your normal password ...

but mostly answers like:
It saves the user having to type a root password at install.... to me this just shows the complete lack of regard for normal security in Ubuntu.

---

### Post by nocturn on 2006-06-08
[QUOTE=Gowator]
The sudoers file contains 
ALL:ALL this means any account can run as root including www-data, mysql or any other daemon account.  
Firefox or any web browser connects as YOUR account .. if it runs a CGI as sudo root it runs it as root.  
[/quote]

It does not on my system.  The file does have 
root    ALL=(ALL) ALL 
in it, which doesn't imply anything you stated.  There is nothing in the sudoers file that suggests that www-data or your user account (outside of the admin group) can use sudo to get root.

> 
Ubuntu is set to become the number one crackers target because at least XP users have worked out that they need a decent firewall whereas all we hear on Ubuntu forums is "don't mention sudo or we will lock the topic...". 


What are you talking about?  Ubuntu's default install does not need a firewall because there are no ports listening to the outside, hence nothing to protect.
The only added value would be an outbound filter which would scare most newbie users (and a lot of the average ones). 
The firewall issue has nothing to do with sudo (a firewall will not make sudo any safer).

> 
The point is most people will stick with defaults, they don't have time to secure everything and by giving every user root privs once they crack that users password is asking for problems....


But not every user gets root privs.  Only the one installing the system (we could not very well lock him out too).
Additional users needs to be given sudo privs manually.

---

### Post by nocturn on 2006-06-08
[QUOTE=Gowator]They can do less but how about whatever user you use to connect via firefox or p2p?  

Simple test try gmail, yahoo mail etc. etc. and see if that user has access to upload a file?  
Yep they have access to the entire filesystem ...

Don't forget www-data has access to CGI and scripts.... so they just need to run a sudo from the CGI ....
[/QUOTE]

I seriously don't understand what you are saying.
If you use an upload button, you can browse and read any directory and file that you have read access to, either because you are in the group that owns it or the other permissions are set.

Most of /usr is set to 755, which means you can read and upload these files.  You cannot write them however.
You also cannot read some files, namely /etc/shadow and /etc/sudoers as a normal user.

I can't see the security failure in any of this.

---

### Post by LordHunter317 on 2006-06-08
[QUOTE=Gowator]The sudoers file contains 
ALL:ALL this means any account can run as root including www-data, mysql or any other daemon account.[/quote]No, that's not the default policy.  ***That's not even valid policy.***  Do you even know what a valid /etc/sudoers line looks like?

The default policy is to let members of the admin group run anything they please.  In Warty, it was the user created at install was given full sudo.

***This means the basis for your entire rant is fundamentally wrong.***
  
> Firefox or any web browser connects as YOUR account .. if it runs a CGI as sudo root it runs it as root. No, firefox never runs as anything but your user.  It cannot run anything but as you user.  

And no, Apache (the default web server) will not run CGI scripts as anything but the apache user without specific elevation via suExec.  This includes via sudo, because the setuid bits are stripped from the CGI process.

You don't know what you're talking about.  This is a rather fundamental and gross error.

>   If I open my ports on a default Ubuntu account I get upwards of 50,000 **attacks per day** using simple brute force.  :rolleyes: I see that ***on every box I have facing the Internet.***  Even my crappy home router on dialup.  Yet I'm still competent enough to prevent those boxes from being compromised via that method.

> Most users can work out how to deny root access but setting up a secure sshd is more complex... and most don't even try.It's denied by default so they don't have to.

> Ubuntu is set to become the number one crackers target because at least XP users have worked out that they need a decent firewallUbuntu doesn't need one by default, which is why it doesn't include one.  If you're setting up servers and you're not competent enough to properly secure the box (including a firewall where appropriate) then you shouldn't be running servers. BTW, you have yet to convince that Ubuntu is remotely at fault here.

>  whereas all we hear on Ubuntu forums is "don't mention sudo or we will lock the topic...". While I don't doubt the moderators here would have done that, I haven't actually seen this occur.  This thread is open, isn't it?

> if the real world is too frightening you can always stick your head back in the sand....So how is that sand, btw?  ***You made your bed, you can lay in it.***

> The point is most people will stick with defaults, they don't have time to secure everything***Then they shouldn't be running servers.  Period.***

>  and by giving every user root privs once they crack that users password is asking for problems....Ubuntu doesn't do that, though.  It never has.

> They can do less but how about whatever user you use to connect via firefox or p2p?

Simple test try gmail, yahoo mail etc. etc. and see if that user has access to upload a file?
Yep they have access to the entire filesystem ...No, they do not.  You don't know what you're talking about.  Try uploading /etc/shadow from firefox.  You can't do it.

> However 50,000 attacks per day is also just a drain on resources and since is obviously being targeted because of the pre-installed rootkit ...***There is no pre-installed rootkit.  WTF would ever do such a thing?***

And no, the attacks are random and very-widespread.

> 3) The security approach of Ubuntu which seems to be never ever discuss the sudo policy. Which is why it's documented on the Wiki.  What the moderators do here has nothing to do with Ubuntu policy.  Not that you've provided evidence of your claim.

---

### Post by Raoul Duke on 2006-06-08
As a normal user I know little about security issues and am finding this thread very educating.

Little as I know, however, it seems to me that the 5-minute-window (or however long it is) after using the sudo command, where any command can be issued without authorization, effectivey makes Ubuntu security non-existant. Any attack which can gain user access need only lay in waiting until a sudo is issued, and thereafter own your machine.

That is why I never use sudo, always a root window, to get privileged accesss.

Or am I missing something?

---

### Post by LordHunter317 on 2006-06-08
[QUOTE=Raoul Duke]Little as I know, however, it seems to me that the 5-minute-window (or however long it is) after using the sudo command, where any command can be issued without authorization, effectivey makes Ubuntu security non-existant. Any attack which can gain user access need only lay in waiting until a sudo is issued, and thereafter own your machine.[/quote]But that's true even if you asked for the password every time.  Eventually, they'll be able to acquire the password from you and the game is over.  

> Or am I missing something?Yes, that stealing the password once you're on the box is relatively easy.

---

### Post by Raoul Duke on 2006-06-08
[QUOTE=LordHunter317]But that's true even if you asked for the password every time.  Eventually, they'll be able to acquire the password from you and the game is over.  
[/QUOTE]

So it is more secure to do as I do, which is to keep a root window open on an unused workspace?

---

### Post by LordHunter317 on 2006-06-08
Not especially, no.  Again, it's just a matter of time until they get the privileged password.  You had to enter a password to open that window, right?  Well, they can get it.

---

### Post by Gandalf on 2006-06-09
[QUOTE=nocturn]It does not on my system.  The file does have 
root    ALL=(ALL) ALL 
in it, which doesn't imply anything you stated.  There is nothing in the sudoers file that suggests that www-data or your user account (outside of the admin group) can use sudo to get root.
[/quote]
Just LOL !

Only a stupid will add ALL=(ALL) ALL That's not how it generally is, usually users give access to themself or if it is a huge/wide system they use the wheel group which is btw if enabled in PAM works the same for su (only wheel groups have su access) like on freebsd by default

firefox run as ur username, I use sudo without passsword, so even if an attacker (THAT'S a huge IF coz I challenge anyone out there to break into my network), he can't get much using sudo, sudo is limited here to some commands not all, but again if firefox has a bug, the attacker will not enjoy breaking ur system as much as enjoying deleteing your home folder contents, I mean seriously i Format like every week I don't give a damn about /, /home is a seperate partition, so if an attacker came here, I welcome him, do whatever he wants around /, but one file removed from /home will be so unacceptable, so really think of it again, harming /home/* does much more damage than /*, which lead us to FIREFOX=BAD SECURITY and not SUDO = BAD SECURITY, so, do i have to use elinks/links/lynx then ?? or maybe wget ??

So as Usual, DO NOT blame the software, blame ppl's stupidity, Like when someone got robed in his bank account and says that Credit Cards are useless and dangerous, well NO he should say, damn it i should have known that the damn  site was some kind of spam...

I love SU too, it's cool to type su than sudo su (or sudo -s -H), but i don't say sudo is a bad security, if someone break into ur account and had sudo access, he can also break to your root account, it's the same, except that root is more common an attacker will try it more often over ssh

> **Then they shouldn't be running servers. Period.** I just love this quote :D Nice and Wisely said LordHunter317

BTW the rest of my post is in [LordHunter317's post above](http://ubuntuforums.org/showpost.php?p=1111760&postcount=38), he said all what i wanted to say, maybe just GO LEARN SUDOERS then come and argue

---

### Post by LordHunter317 on 2006-06-09
[QUOTE=Gandalf]Just LOL !

Only a stupid will add ALL=(ALL) ALL[/quote]Uhh, the line nocturn posted was the Ubuntu Warty default and perfectly secure.  It means that ***root (and only root)*** can run any command on any host as any users.

Stop and think about this for a second.  If you don't understand what I just said, then ask.  

What would be dangerous (and what Gowator was trying to claim) was the policy was:```
ALL ALL = (ALL) ALL
```Note the leading ALL there, where root was.

That would be dangerous. But it isn't what is done, either.

> so even if an attacker (THAT'S a huge IF coz I challenge anyone out there to break into my network), he can't get much using sudo, sudo is limited here to some commands not all,In practice, unless you've very carefull audited your sudo policy, I bet money they can still compromise your system and probably trivially get root.

Auditing sudo policy is very difficult.  As a simple example, can you run less via sudo?  If so, they just got a root shell.  Or emacs?  Or vim?  Same deal.

---

### Post by Gandalf on 2006-06-09
Yes sorry i meant ALL ALL = (ALL) ALL when i was talking :)

when u run vim/less/etc.. via sudo, you got a shell access i agree, but the process is owned by root and not regular user, and it ain't accessible in any way by any other user, unless there's a security hole in the running software like bzip2 1.0.3 without the [CAN-2005-0953 bzip2 race condition](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=155742) patch where a user can have write access to file owned by another user ... not own a running process :)

---

### Post by LordHunter317 on 2006-06-09
[QUOTE=Gandalf]when u run vim/less/etc.. via sudo, you got a shell access i agree, but the process is owned by root and not regular user,[/quote]And that's how the attacker gets a root shell where they can do anything you like.  It lets an attacker circumvent sudo's security completely.

>  and it ain't accessible in any way by any other user,But that's not the concern.  Tne concern is the ability of the attacker to do anyhting they want as root using your account's elevated privileges.  The programs I mentioned are all paths to do that.

---

### Post by diehardzz on 2006-06-09
Hi, I'm not an expert in sudoers but I think if someone can get an user in a machine running ubuntu he can make anything he want even change root's password by typing "sudo passwd"

Isnt' that right ?

---

### Post by LordHunter317 on 2006-06-09
No, it's not right in the least.  You have to be either the first created account (Warty) or an account in the 'admin' group (every other release).  Then you can run any command you want as any user you want.

---

### Post by Gandalf on 2006-06-10
But guys, people, you are not getting the big picture here, can anyone tell me what's the difference between sudo and su when it comes to hacking ?? if i could crack ur user password i bet i can break into ur root account (i don't mean using sudo as sudo su), so please stop blaming sudo, but blame the user for either his stupid easy password or coz he writtent his password on a note above the screen lol

---

### Post by nocturn on 2006-06-12
[QUOTE=Gandalf]But guys, people, you are not getting the big picture here, can anyone tell me what's the difference between sudo and su when it comes to hacking ?? if i could crack ur user password i bet i can break into ur root account (i don't mean using sudo as sudo su), so please stop blaming sudo, but blame the user for either his stupid easy password or coz he writtent his password on a note above the screen lol[/QUOTE]

Which is better depends on your security model.  A valid reason to have a seperate root password (or second sudo account) would be that your threat model includes using your user password over an insecure connection or an insecure location (like a kiosk, Internet Cafe or a library).  

When the danger of password exposure is equal to both the root account and your user account, there is no advantage in having two.

---

### Post by LordHunter317 on 2006-06-12
[QUOTE=nocturn]Which is better depends on your security model.  A valid reason to have a seperate root password (or second sudo account) would be that your threat model includes using your user password over an insecure connection or an insecure location (like a kiosk, Internet Cafe or a library).  

When the danger of password exposure is equal to both the root account and your user account, there is no advantage in having two.[/QUOTE]In all of those locations, the exposure risk is the same.  IF you enter it, it's at risk.

---

### Post by nocturn on 2006-06-12
[QUOTE=LordHunter317]In all of those locations, the exposure risk is the same.  IF you enter it, it's at risk.[/QUOTE]

I meant that if you log in from untrusted (or semi-trusted) locations, you can benefit from having a user that cannot get root for those connections instead of using a sudo-enabled account. 

In this scenario, the impact of a password exposure would be less severe.

---

### Post by LordHunter317 on 2006-06-12
[QUOTE=nocturn]I meant that if you log in from untrusted (or semi-trusted) locations, you can benefit from having a user that cannot get root for those connections instead of using a sudo-enabled account.[/quote]Not especially, no. Giving them access to *any* accounts on your system is a bad thing and if they successfully avoid detection, it's usually only a matter of time before a sufficently motiviated and competent attacker gets root.

Yes, you've limited the immediate damage they can do, but most likely not the long term.

---

### Post by nocturn on 2006-06-12
[QUOTE=LordHunter317]Not especially, no. Giving them access to *any* accounts on your system is a bad thing and if they successfully avoid detection, it's usually only a matter of time before a sufficently motiviated and competent attacker gets root.

Yes, you've limited the immediate damage they can do, but most likely not the long term.[/QUOTE]

Yes, if they go undetected long enough, they could still gain root.  It's still better then them having root upfront and only increases the chance of catching the intrusion before it is too late.

---

### Post by BoneKracker on 2006-07-03
This might actually have been a more valuable and productive thread if it had not been started with an emotionally-charged and iconoclastic statement (i.e. "sudo = bad security!")  While it does get attention, that kind of language just puts people on the defensive.

I think we as a community could benefit from adult discussion of what possible issues may exist and what could be done to overcome them.  The subject is not taboo.  I can see how an individual using immature and unprofessional communication might meet with what they perceive to be resistance, though.


Personally, I think sudo is a good thing, when configured properly.  I also think people should study the man page.  Just look at the number of erroneous statements in the early posts of this thread.

Some constructive ways to look at this:

Taking the current configuration as a given, what can we as a user community do to enable users to effectively secure their system?

Under what conditions does the use of psuedo-root accounts represent security risks, and what can be done to reduce these.

Under what conditions is the use of pseudo-root accounts inappropriate, and should users in these scenarios disable sudo access?

etc.

---

### Post by llbbl on 2006-07-28
sudo isn't bad security if you only have one account on your machine. most ubuntu users dont even have a root account because they never set the password.

---

### Post by elamericano on 2006-07-29
Didn't we go over this? You have a root account, even if it doesn't yet have a valid password, or is otherwise disabled.

---

### Post by HunterPro on 2006-07-31
> **goofrider said:**
> I think the orginal poster raised a valid point, and there are common assumptions about passwords that can be dangerous on an sudo system.

Traditionally, we have a very strong root password, and users have weaker passwords (out of convinience). However, on an sudo system, it must be stressed that every sudoer must have a user password as strong as what they'd use for a root password, otherwise, their user accounts would be a single weakness of the password chain. Not every sudoer may realize that 

This situation can become even more dangerous if you have many (10-20) sudoers, all using weak passwords without understanding the danger. Now instead of just one root password to crack, there are 10-20 weak passwords to crack.

What needs to be stressed are:

 * Keep sudoers at a minimum
 * Every sudoer account should be treated just like a root account
 * Every sudoer must have a strong password
 * Every sudoer must understand the implication of being an sudoerif you require such a level of security, there are *far* more options in sudo to secure your system. If a user 'bill' is the guy that is always there and needs to be able to restart the server out of office hours, you can allow bill to restart the server using sudo reboot from 1700-0800. And Tina can be set up to clear the printer spooler if thats fubar and doesnt spit out any pages any more. sudo is the equivalent of the policies manager for Microsoft Windows. You will be able to set very strict rulesets for users, usergroups and systems. You can even say that Bill is allowed to sudo only when connecting from his workstation, and not from the other side of the world. All this makes sudo a *very* powerful system security and administration tool. If you want to find out more about it, check out `man visudo`. :)

Sudo isnt bad security. The way its used in ubuntu-desktop isn't, either. Its a decision made after evaluating the security versus usability issue. And I think its a good decision - loads of people at home won't even use different passwords for the root/superuser/administrator account and the $myname-account. And the people where security does matter - e.g. big corporations, people that are easily scared and other needy types - will find the solution to their specific security problem in the visudo manpage. So actually its good practice to ship Ubuntu with sudo - it lets people meet this great piece of software and thus helps spreading the possibility to create secure computing environments.

but hey, thats just me. I like sudo, and yeah, on my laptop I even have set the nopasswd flag for my username. I also have the keychain auto-unlocking on login. But I make sure every other entrypoint on my computer is secure, because I know what I am doing. At least, I believe I do ;)

And now, I need a very cold and refreshing beer. :P

---

### Post by st00ner on 2006-07-31
[http://www.milw0rm.com/exploits/2013](http://www.milw0rm.com/exploits/2013)

Ubuntu is vunerable in alot of ways. Look at the kernel revision....
Hacking root would be a joke lol. You better make sure no one can remote you....

Search "Linux" on milw0rm.com. See how many exploits most users are vunerable to? Local root is a joke.

---

### Post by aysiu on 2006-07-31
*sudo* is a great security model in theory. [The way Ubuntu has implemented it could be improved, even though the developers don't seem to agree with me on that one](http://www.ubuntuforums.org/showthread.php?t=219064).

---

### Post by LordHunter317 on 2006-07-31
Because you're totally wrong on all your points.

---

### Post by aysiu on 2006-07-31
> **LordHunter317 said:**
> Because you're totally wrong on all your points.
LordHunter317, you know I have a lot of respect for you opinions and knowledge (particularly about security), but you're going to have to do better than that. Can you elaborate, please? "You're totally wrong" doesn't get very far...

---

### Post by LordHunter317 on 2006-08-01
Frankly, I think it's pretty obvious why you're wrong, but I'll elaborate, sure.

For starters, sudo is no less fragile than any other network aware application on your system.  If a user messes with /etc/hosts or /etc/hostname without changing everything else they should and breaks sudo, it's not really the fault of sudo.  Why?  Because they broke other installed applications too, they just may not have noticed it.

Providing a way to restore sudo without rebooting is obvious nonsense.  Such a mechanism completely defeats the purpose of sudo.  And how you would raise privilege in the first place?  You'd have to write an setuid application to do it, which is not very attractive.

And the groups file is backed up by the system anytime you make a change, provided you don't edit it directly.  This is true of all Linux systems, not just Ubuntu.

As for the GUI integration, that's not minor work.  That's substantial work and it has nothing to do with sudo.  The applications needed privilege are at fault, not sudo.  Has nothing to do with it.

Making sudo safe to use with graphical applications is easy enough. Again, this isn't a bug in sudo per se, the correct answer is user education.  Fixing the issues with some shell-script hackery would be possible, but I'm not sure it's the sudo package's job to do so.  Nor am I sure it should be Ubuntu policy to do so, either.  

Ultimately, you can be bit by the problem using gksudo (AFAIK it doesn't do anything to avoid these issues).  Ultimately, new issues will be created so it'll always be a step behind anyway.

Ultimately, I don't see anythign where education isn't the right solution, as painful as it may be.  Any technical solution will be jury-rigging.

---

### Post by aysiu on 2006-08-01
I don't care if it's the *sudo* package. The way Ubuntu has implemented *sudo*, it's easily broken. I know you have to reboot to escalate privileges, but if there were a standard way that /etc/group and /etc/sudoers were backed up, then it would be far easier to give people instructions for fixing what they screwed up.

And the *gksudo* command with graphical applications should not be giving warnings that scare people and then encourage them to use *sudo* instead. That may be the "fault" of the individual applications and not *sudo*, but to the end-user, it's the same **effect**.

In any case, I realize none of this is going to happen. I'm just talking about in the ideal world. Likewise with the feedback in the terminal--clearly that's beyond the scope of even Ubuntu, as that's apparently how bash or whatever shell is constructed and isn't an easy fix, and people just have to get used to it. That doesn't negate the fact that *from an end-user's perspective*, it's confusing to get feedback from the GUI and not the CLI when entering your password.

I have legitimate gripes. They may not be easily solved, and they may not all have to do directly with the *sudo* package itself, but they are real problems. Yes, apparently, it will be a matter of education. It's a moot point, anyway, since the developer's aren't going to change these things.

---

### Post by nalmeth on 2006-08-01
LordHunter,

I'd have to agree that education is absolutely the best defense, but for average users like us, finding the relevant documentation (that's not over our heads, but still practical for everyday smart decisions) is difficult and time consuming.

So naturally, a lot of people are only as safe as the weakest point in their security model.

Is there a storehouse of documentation where *users *can educate themselves on everyday security practices that entails more than:

Keeping a strong password (which you've indicated is still useless if you're being personally targeted - rainbow method :confused: )
NEVER communicating the password in non-encryted transmissions
NEVER running as root user to do everyday stuff (like browse the web :p )
and so on and so forth

I've yet to find such a storehouse

I've found a few techniques that seem to only mask your online identity, and I'm really not certain of their usefulness or effectiveness...

Also, it seems every method to keep yourself secure has a way of being exploited itself (see chrootkit)
I think I practice safe use, but I can only see so far.

---

### Post by LordHunter317 on 2006-08-01
> **aysiu said:**
> I don't care if it's the *sudo* package.Well, you really need to if your want your suggestions to be taken seriously.  Technical problems require technical solutions which require technical understanding.  If you refuse to gain the required understanding, then you shouldn't be listened to.

> The way Ubuntu has implemented *sudo*, it's easily broken.No, it isn't.  Education is the only solution for users who are mucking with files they should not muck with.  Nothing you can do will prevent that.

> I know you have to reboot to escalate privileges, but if there were a standard way that /etc/group and /etc/sudoers were backed up, then it would be far easier to give people instructions for fixing what they screwed up.Not really.  'adduser myname admin' is no harder than 'cp /etc/group- /etc/group'.  The fact you haven't thought this through is upsetting really.  

Please don't go pushing for change when you don't understand the underlying issues.  Standardized backups would not make this eaiser.  

> And the *gksudo* command with graphical applications should not be giving warnings that scare people and then encourage them to use *sudo* instead.It umm, doesn't.
I'm not even sure what "false errors and warnings" you are talking about.  The warning message given by gksudo is quite valid.   It's not my problem if you don't understand X authentication or login issues, both of which you need to read up on.  Your analysis of these issues is quite wrong.

> It's a moot point, anyway, since the developer's aren't going to change these things.Because they shouldn't.  You don't understand the problems at hand.  They're not simple "problems" to solve, and I'm not really convinced the problems truly exist anyway.

---

### Post by aysiu on 2006-08-01
Yes, of course, "authentication rejected" isn't going to scare off users from using *gksudo*.

Please, if it's about education, educate me. You know I'm willing to learn. Talking down to me and telling me how ignorant I am doesn't solve things. You're absolutely right, of course--I have no idea what bug report to file, but there **is** a problem.

If the problem is a lack of education, propose a solution. I tell someone to *gksudo* something, and she gets a scary "error." What now? Apparently, it's not a bug.

---

### Post by LordHunter317 on 2006-08-01
> **aysiu said:**
> Yes, of course, "authentication rejected" isn't going to scare off users from using *gksudo*.That's not what I said.  What I said was the error was legtimate.  Scaring off the user is irrelevant.

> Please, if it's about education, educate me.Thinks like the basics of how X authentication work and how sudo sanatizes it's environment (and how to control it) are well documented and ought to be able to find the documentation and learn on your own.  Some of the really gory X stuff is in deadtree only, but you shouldn't need to learn that.  The details of the xauth manpage are sufficent, for the most part.

> I tell someone to *gksudo* something, and she gets a scary "error." What now? Apparently, it's not a bug.I'm not sure why the session manager is rejecting auth but X proper is not, but I bet it's XAUTHORITY related.  I'd have to test to create the issue, obviously.

---

### Post by aysiu on 2006-08-01
Sorry. The [details of the *xauth man* page](http://www.die.net/doc/linux/man/man1/xauth.1.html) are not sufficient for me. If that makes me stupid, then so be it--I'm stupid. I don't really see how that helps me understand the error any better.

---

### Post by gabba on 2006-08-01
Hello people, I understand all the worries about a virus/trojan/direct attacker gaining root access, but I wonder: is it that bad?

I think the worse security risk is an attacker gaining access to my user account and erasing or accessing my documents: those are the real valuable things I keep on my computer. Reinstalling the system is ridiculously easy and quick under Linux.

Root access seems to be a bad thing only if there are other users using the same computer, or if the computer is a server. Of course your desktop could be used to conduct a DDOS attack, so that's an additional threat, but not to YOU.

Just for the record I'm using the same installation of Windows XP for two years, I have a free firewall and antivirus that give me very few worries, and I haven't had a problem in all that time.

I wonder why people praise so much the security of Linux, and why Ubuntu doesn't come preinstalled with an antivirus, and a firewall that monitors outgoing connections. After all, apart from the fact that there are less viruses targeting Linux (for now) and that security holes are patched a bit quicker, your documents are at as much risk on your Ubuntu system that your Windows one.

---

### Post by aysiu on 2006-08-01
I partly agree with you--reinstallation is easy, and personal documents are ultimately more important than system files, but if you have a rootkit installed on your computer, you are likely to not even know your computer has been compromised, and your personal information can be stolen at the same time that your entire system is being controlled.

---

### Post by John.Michael.Kane on 2006-08-01
So what is the right way for an enduser to secure their system? I see many complaints people being told their answers are wrong yet those who say their in the know have not posted any doc's or howto: for fixing the issues. all that is said go read xyz educate yourself. I'm all for reading 500+ pages of secirity books,however. there are those who may want a more direct route. so if someone is too post what is best way to secure ones machine they should expect not to get helped or told rtfm. If you know howto fix said issues being talked about why not just post it.

---

### Post by aysiu on 2006-08-01
I read the man page for *xauth*--not helpful.

---

### Post by LordHunter317 on 2006-08-02
> **aysiu said:**
>  but if you have a rootkit installed on your computer, you are likely to not even know your computer has been compromised,Rootkit detection is simple.  Reboot to a live CD and compare to a known good baseline.  They stick out like sore thumbs.

At anyrate on the original method of discussion, the error is truly suprious.  I'm still not sure why the session manager is rejecting communication[1] but it doesn't matter.  It couldn't restart a root session *anyway* so it doesn't matter that the privileged application can't start as root.  If bothers you so much, tell people to:[list][*]Ignore it[*]Run applications --disable-sm[*]Redirect stderr to /dev/null[*]Don't run gksudo on the console[/list]

[quote=SD-Plissken]So what is the right way for an enduser to secure their system?[/quote]Don't be stupid on the Internet, which I've already said.

>  I see many complaints people being told their answers are wrong yet those who say their in the know have not posted any doc's or howto: for fixing the issues.Nonsense.  aysiu's questions are not those of an average user.

[1]The issue is likely one of the following:[list][*]gnome-session rejects any connections except from the user it is running as[*]There are multiple SECURITY cookies in play and the root session isn't seeing the right one.[/list]If you want even more details, go read the SECURITY extension docs, but it will be over the head of anyone who doesn't have X internals experience.  You did ask, however.

---

### Post by gabba on 2006-08-02
> **aysiu said:**
> I partly agree with you--reinstallation is easy, and personal documents are ultimately more important than system files, but if you have a rootkit installed on your computer, you are likely to not even know your computer has been compromised, and your personal information can be stolen at the same time that your entire system is being controlled.

Hmm... that's true. I wasn't thinking about rootkits, maybe more about the "traditional" types of viruses which try to damage your system as much as they can. If the malware stays hidden and waits for you to use your credit card online, that could be a very serious risk.

> **SD-Plissken said:**
> So what is the right way for an enduser to secure their system? I see many complaints people being told their answers are wrong yet those who say their in the know have not posted any doc's or howto: for fixing the issues. all that is said go read xyz educate yourself. I'm all for reading 500+ pages of secirity books,however. there are those who may want a more direct route. so if someone is too post what is best way to secure ones machine they should expect not to get helped or told rtfm. If you know howto fix said issues being talked about why not just post it.

I'll give you my personal tricks, which works for both Windows and GNU/Linux; maybe someone can give you more technical advice:
- YOU can be the greatest security risk: never click OK/I agree if you don't understand the dialog box in front of you; never install a program (unless from a very safe source) with default options; never type your password without making sure that you know what you're giving permission for.
- be very careful about what you download and install (waiting a day or two for anti-virus definitions to take into account the new threats before running a suspicious executable can be a good idea); identify very precisely everything you download (i.e. on windows it's easy to make an executable with a double extension (.mpg.exe) and a movie icon, so you launch it thinking it's safe)
- access the internet through a hardware router/firewall, with only the specific ports you need (for bittorrent, online gaming, and so on) redirected toward your computer. This way you don't have to worry much about incoming attacks, or whether your computer's firewall is well configured.
- keep your computer up to date with security updates. (Yeah, I know, duh.)
- Have an antivirus. I guess that having one on Linux is a good idea, despite people saying right and left it's not necessary. The day Linux becomes more popular with both desktop users and virus makers, these people are gonna cry.

Beyond that, on Linux, use sudo or the root account as scarcely as possible. Have a separate account that doesn't have sudo access and doesn't contain personal documents: you can use that account for testing potentially unsafe stuff.

If you want to go even beyond that, I read about SELinux which allows you to create security profiles for each application. I suppose it means that an unknown applications starts in a kind of sandbox. I don't know if SELinux exists outside of Fedora Core Linux, though.

---

### Post by John.Michael.Kane on 2006-08-02
> **LordHunter317 said:**
> If you want even more details, go read the SECURITY extension docs, but it will be over the head of anyone who doesn't have X internals experience.  You did ask, however.

This is the whole point you telling someone to go read a book which you then say is over the head of most users is pointless. your so in the know yet have not posted any methods to keep ones system safe. you can quote all the info you want. where is the info on how to properly secure an endusers system since you know all about security. telling someone don't be stupid on the internet helps none.

---

### Post by LordHunter317 on 2006-08-02
> **SD-Plissken said:**
> This is the whole point you telling someone to go read a book which you then say is over the head of most users is pointless.***But those comments aren't directed at most users.***  They're specifically directed at asyiu's sudo policy criticisms.

Which there's not really more elaboration necessary.  I could describe the way SECURITY works in higher-level terms, but it's not going to help anyone any.  He doesn't need to know how it works to understand the solutions, which I've provided.  And he already knew my preferred solution, "Just ignore it," because other people had told him as such.  He even admitted such. Given that, it seems senless to go in to great detail.  If he really wants to know the gory details, he can learn them himself.

> your so in the know yet have not posted any methods to keep ones system safe.***What part of, "Don't be stupid on the Internet?" is difficult to understand?*** I can elaborate further if someone really needs more details, but they're already been more or less spelled out twice in this thread by others.  But seriously, if you apply common sense, you'll be safe.  Someone who wants to make your penis six inches longer probably can't, and hot lesbians who want you probably aren't lesbians, or hot.  Some random, previously unknown guy who wants to give you $419 MILLION DOLLARS USD doesn't have it

Duh.  It doesn't take more than common sense to avoid 99% of the bad stuff out there.  

> where is the info on how to properly secure an endusers system since you know all about security.If you'd spend your time reading this thread instead of attacking me, you'd see it.  It's quite plain.

> telling someone don't be stupid on the internet helps none.Actually, it does.  Common sense is mostly the order of the day, just like it is when you're in an unfamiliar place or working with people you cannot fully trust.  Besides, it's pointless for me to repeat what others have already said multiple times in this thread.

---

### Post by John.Michael.Kane on 2006-08-02
LordHunter317 i'm not attacking you. I simply said that if you know of better methods for an enduser to secure his/her system then they should be made known. not everyone has degrees in cryptography and information security.

---

### Post by kerry_s on 2006-08-02
I know ubuntu is still considered a young distro compared the other main distro's(debian,redhat,...) but has any one ever had there Ubuntu system compromised? I have never heard about a compromised Ubuntu system,so that has got to tell you something about the security there. As for me i always set a root password anyway using> sudo passwd root < and my passwords are long with both (Aa and #1-0) but i've never even had any attempted breakins(yes i check years of windows use has made me paranoid LOL) i've been using linux for some years now and have never got anything at all. I spend alot of time online and my computers always on. I know linux is growing everyday and i'm sure it will only be a matter of time, but you can already see that linux is not going to make it easy for the hackers, alot of distro's are already running encryption of some kind and i can only see this trend growing to the point were you will only be able to see your information from the machine your running as the entire disk itself will be encrypted. anyhow, just my $0.02...

---

### Post by akak8ty on 2006-09-09
so yesterday, I read the opposite. take authorization of root, and the commands to do so, but today while looking in there, half the files in there are dead files anyhow- empty shells, things that got partially loaded then froze, leaving a file or a doc, but nothing more

Ya know.......:-k &%$*$&^%?

---

### Post by ronacc on 2006-09-09
Different uses need different security . I use my box as a single user home pc. I run with remote login disabled. I do not run as root if I can avoid it. With that said , I find sudo a great pain in the a** I want to be able to popup a root console or root file browser (with strong password of course)as I need it from my user acct. This lack of utility is one thing that keeps me using SuSe as my main system and Ubuntu as an occasional play thing.Yes we need good security but security that hinders usability will not help attract people to Ubuntu or any other distro.

sometimes you have to accept a little danger for utility. the is NO substitute for an informed and careful user.

---

### Post by akak8ty on 2006-09-09
Understood and agreed. I am used to having a little more control over my security features though. On Ubuntu, I enable one feature, the next day, it doesn't work. There is no rhyme or reason. Today I discovered my sound issue had something to do with my jack server, but after finding the command to run it, I was told its running, make it stop and start again--um...okay, so I'll have to do a search and sieze for those commands

I like control over port scans, access to ALL my files. I have files I need to install to that I don't have permission.
Example- Firefox 1.5.0.6 is compatible with Linux. I had issues with 1.5.0.5 on windows, and more trouble here.

I was able to install wine, which in some respect defeats the purpose of not relying on windows- sometimes It pops out wanting to be used, other times when I would like to use it, its no where to be found.

So I have authority to my root, that means nothing when half the files are broken, or missing. Or gives me permission, just so it can tell me I don't *really* have permission- it just has my name first.

I would like to install to files, but I don't have permission.
I should be able to access what I need when I want to and the adjustment of having to go find the right command to make it so is a little annoying. 

So that is the payoff for that which is free, I have to work a lot harder to accomplish very, very simple tasks.

I AM grown up enough to know what files not to alter, so I see no reason to ke kept from them- or to find the special code to get into them to see if they actually are in working order.
I have a lot of empty files.

I am finding my way around, and in so doing- while I appreciate the "ability to customize as I like" when one is fairly young in the program, its a bit time consuming.

It would also be helpful when people are discussing commands to try to fix issues (as I search for solutions) to provide the full command.

For some of us this is a new world, and while I am not unfamiliar to commands it takes a little longer than a few weeks to get them down.

I feel I've barely scratched the surface, but I catch on quick enough when the information is nearby for reference sake.
That is a task in itself.

---

### Post by aysiu on 2006-09-09
> **ronacc said:**
> I find sudo a great pain in the a** I want to be able to popup a root console or root file browser (with strong password of course)as I need it from my user acct. I think it's just a lack of education.

Want a root console? Type ```
sudo -s
``` There. Now you have a root console.

Want a root file browser? Create a launcher or keyboard shortcut for ```
gksudo nautilus
``` There. Now you have a root file browser.

Not using Nautilus? Try one of these: ```
gksudo thunar
``` ```
kdesu konqueror
```

---

### Post by akak8ty on 2006-09-09
> **aysiu said:**
> **I think it's just a lack of education.** WTH is that? Who do you think you are?
I can count on ONE hand the people I know who know anything about Linux.
Thanks for the codes. 

Want a root console? Type ```
sudo -s
``` There. Now you have a root console.

Want a root file browser? Create a launcher or keyboard shortcut for ```
gksudo nautilus
``` There. Now you have a root file browser.

Not using Nautilus? Try one of these: ```
gksudo thunar
``` ```
kdesu konqueror
```


Are you capable of being nice? I've yet to hear it- and don't bother responding. There are far more pleasant people here to talk to.

---

### Post by akak8ty on 2006-09-09
I want sound. **s-o-u-n-d**

So what? sudo sound? :rolleyes:

---

### Post by ronacc on 2006-09-09
In a way it is lack of education in that those commands are rather hard to find. I have used gksudo nautlius but the resulting nautilus does not seem to have full root privlages as it refuses to do some things that I can do from console. root konqureor isn't fully privalged either I have tried them both. I am not a complete newbe having run linux on and off since caldera openlinux 1.0 circa 1995.I do not instantly remember all the commands of the various distros ( maybe alzheimers setting in i'm 61). I am not afraid of the command line I learned basic and fortran a couple of decades before the gui was invented. I am lazy I find it easier to drag and drop rather than type # sudo cp ./xxx-yyy_zzz_0.8.5-3rbq.deb /aaa/bbb/ccc/ only to have the damn thing say "Im sorry dave I can't do that" because the second y should have been Y.
 My point is that Ubuntu  is suposed to be a gateway for windows users wanting to convert to linux and frustrating them is not the way to go.
  I have been windows free since 2001 so if I find ubuntu frustrating , mabye it is just a little.
  
 side note to akak8ty  check out the o'reilly pocket guides for a good quick reference.

---

### Post by akak8ty on 2006-09-09
Thanks ronacc. 
I have found tons of information online today;
Linuxcommand.org; some interesting things on HowtoForge.com. and even: [http://www.oreilly.com/catalog/debian/chapter/book/ch07_01.html](http://www.oreilly.com/catalog/debian/chapter/book/ch07_01.html).

So the internet is not lacking for information. 
I think to some degree I had an expectation regarding this forum that fell short initially, Many pages of bad eggs left me further questioning the integrity what I was getting into.
It was chalked off to humor and cynicism, but I was not amused.
(My first day here was quite unpalatable- including the womens thread...) I could work circles around people in windows, including my staff- but were talking another language here.
I felt like I was back in Paris, **_RUDE_** but at least spoke some of the language in paris.

Fortumately there are quite a few good people that made up for it, and for me if someone is doing a good job I let them now with out hesitation.
If someone is spewing rubbish, I'll let them know that too ;)
 
I've neem using open source and Sourceforge for a while and have had xampp on my windows side. Ubuntu uses Lampp. The educational software is very good for the young ones, some of the other things are gadgets. I had already been using Open office- so some is familiar, but I am also like a kid in a candy store with all my options.

Fortunately I had no problem with my wireless network running the two different operating systems. I just haven't had sound since Tuesday.

I've been laid up for a couple years, so I write, blog, op-eds.
I have my basics covered, its just getting into the nitty gritty of the bigger picture. This is a new learning toy for me. I am not able to do all I could once do physically, so I channel it into keeping my mind active and challenged.

Again, I am aware this release I just downloaded/installed us an unstable release, and programs that worked yesterday, don't work today.
Over all I am not unhappy at all- except one site I am on a lot the page jumps around like a mexican jumping bean. Now after running dom inspector, css imbedding, styles, invalid meta tags, diagnostics's and other validation tools, the site does have some issues and may not be compliant with Section 508, but that is the developers issue to contend with, and his country's laws.
 
Everything I know I learned by doing since I was very young. 
Research is my favorite hobby.

Windows may have done every thing for you, but there was a fee, (It didn't do it correctly, for one thing- I called it random acts of formatting, when you don't want it formatted!) and a price to pay- and I do mean 2 separate things. Bootleg was my friend. 

In the next couple weeks if I can accomplish what I need to I'll remove the windows side of my system, but I am not sure some of my essential programs will work- or what it will entail.
I have thousands of photographs, many from over seas that I like certain programs to work with.

Fortunately I am an old dog (_hardly_ literally) that _can_ be taught new tricks 8-) :p
forgive the typo's, I'm doing several things at once here

---

### Post by aysiu on 2006-09-10
> **ronacc said:**
> I have used gksudo nautlius but the resulting nautilus does not seem to have full root privlages as it refuses to do some things that I can do from console. I've never seen that to be the case. Can you give an example?

---

### Post by ronacc on 2006-09-10
Heres an example I was going to copy some mp3 audio files to an SD card , nautilius refused to erase some of the old files to make room (insufficent permissions) kill that (user) nautilus , gkudo sudo nautilus  it still wont do it , same reason BAH try root konq same result BAH again , reboot to SuSe erase files reboot to dapper try to copy (sudo etc) now no permission to copy to that directory , say nasty words , burn to CD , reboot to SuSe , copy files, install caspodder in SuSe , won't put up with that crap again.

side note to akak8ty  the jumpping bean effect is probably the fault of the site not you system, one site I use for my busines ( mapquest) has started doing that to me, I suspect its due to a new version of flash or something not agreeing with the browser I'm using (opera 8.54) also maybe IE only code some sights are BAD about that ( I have to use IE4linux running under wine to access 2 sites that I absolutely must have access to for my business)

---

### Post by akak8ty on 2006-09-10
The site to which I am referring is written in PHP and the developer of the program is always pushing Opera.
I let him know what i found in his scripts just using a couple of the tools I mentioned. Today its not jumpy- but my color config is gone. Its a game called Bushtarion. I took up gaming as well-
except December when I read 8 books.
fortunately there are a *couple* people my age playing, the rest are the fine  youth of mostly England, that they call Chav's, which is **not** a very nice thing. But they are not very nice kids either.

I don't care much for Opera. I have it on my system again, thinking I would give it another chance, but there is something how do I say...swiss cheese like about it - I could be very wrong, but I intuitively feel that there are a few holes in it.
I am working on getting the firefox upgrade, which did not come with the program, that is on my list of things to do. 

I used a couple of commands put on here yesterday. The third one I thought my machine would die for sure. 
kdesu konqueror literally almost konquered my system. 
I really am not crazy about the fact that you have to have permissions for each directory. I am trying to keep it simple- but I think thats just a pipe dream.:-\" :-\" :-\" :-\"

---

### Post by ronacc on 2006-09-10
I use Opera mostly but that is a matter of taste I also have quite a few others that I use from time to time ,konq , galeon , firefox , mozilla , ie4linux(ugh) , and still more. Mapquest wasn't jumping around this morning but the ads had changed , I think it was one of the flash ads that was causing the problem.

note to advertisers the more intrusive , flashier and annoying your ads the LESS likely I am to buy the product or anything else the compay that placed the ad makes.

permissions are necessary for security but there should be a consistant and easy way to deal with them. Once I make the conscious decission to "go root" I should be able to totaly destroy my system with a mouse click , when I knowingly choose that option the responsibility is mine .When I am in a user console or file manager protect me , when I chose to open a root console or FM and then shoot myself in the foot , oh well OUCH. A system that makes me jump through too many hoops dosn't suit my tastes.

 I am evaluating Ubuntu as a possibile distro to windows using freinds aI am trying to wean away from MS . All things considered it is probably the one I would recommend .

---

### Post by aysiu on 2006-09-10
> **ronacc said:**
> Heres an example I was going to copy some mp3 audio files to an SD card , nautilius refused to erase some of the old files to make room (insufficent permissions) kill that (user) nautilus , gkudo sudo nautilus  it still wont do it , same reason BAH try root konq same result BAH again Bah! That's not normal behavior.

Well, if SuSE works for you, use it. I've never experienced a file I couldn't erase with *gksudo nautilus* or *kdesu konqueror*. You know, you can actually enable the root account in Ubuntu, too, if you think that'll make a difference.

---

### Post by akak8ty on 2006-09-10
well this morning nothing was jumping, now everything is jumping, including this page.

My gut feeling is....REINSTALL. Or, the machine has been very heavily used for a couple years and its gonna blow up. haha

I also have a copy of edubuntu ready to go. I was just shy of space for both of them. 
I have a 40 gig 2nd hard drive drive I used for my photo's, so I moved them to another machine running windows on my home network. 

My little 4 year old grand niece is here often and is getting quite confident with herself on the computer. I am quite confident she can't do anything I can't fix- so far so good. 
I Love the puzzles, being a fan of Fine art, she can put together the 6-8 piece Degas, while --listening, um, no- sound issue- must fix. 
We talk about the "picture" and who painted it. 
She is a whiz at the memory games- its jaw dropping to watch. This accomplishment I'll gloat over a little... yet she right took to it, I only planted the seed, and initially guided the hand
Any how, I like EU's approach to education, but I said that already. 
We learned about money in Euros in the suite gcompris which won't do her any good here- but perhaps she sensed its worth more because she took every last coin out of my hands to put them in a safe place. :D Thats my girl. Aiding and abedding my escape from america.:KS

---

### Post by ronacc on 2006-09-10
I will retry both gksudo nautilius and kdesudo knoqueror perhaps I missed something , I do make mistakes. I will also enable a root acct , I hadn't looked into that. as I said above I am mainly learning/evaluating Ubuntu as an alternatve to windows for my non geek friends. I will also keep it around on my machine for the things it does well . I love synaptic as a package manager ,Suse needs help in that area. Yast is great at system configuration but as a package manager is at best, terrible and at worst ( as in the current release ) pretty much a disaster ,installing even a "standard" package can lead to dependency hell , and a "non official" package just grab the alkaseltzer AND the bourboun (not necessarly in that order).Smart is looking good but has a way to go to catch up to synaptic. I like the way very many things "just work" in ubuntu I havent experienced many of the problems I see posted in the forums , mabye just luck, maybe a little more carefull. First impressions do count. I don,t mind keeping more than one distro on my machine ( 3 right now) hard drive space is cheap these days,and using each for what it is best at.Trying to be "all things to all people " is one of the things that makes windows so bad ( and bloated).

---

### Post by ronacc on 2006-09-10
akak8ty could be your monitor , I was getting random trash occasionaly that completly cleared up when I sprung for an LCD , the previous was a crt and loosing sync is one of the common ways they start to fail, that could make the display " jumpy" if it starts after the machine has been on for a while its probably heat related check your fans and vents and heatsinks.

---

### Post by aysiu on 2006-09-10
If you're trying to "evaluate Ubuntu as an alternate to Windows for [your] non-geek friends," consider Mepis. It's based on Ubuntu, includes proprietary software and codecs, and has a root login enabled instead of Ubuntu's *sudo* business.

---

### Post by ronacc on 2006-09-11
Thanks for the tip , I have looked at mephis a while back , my "first impression" was that it was not as polished as Ubuntu. I'll see if there is a release newer than the one I looked at.I think we may be getting some "converts" when Vista hits the fan.Right now Ubuntu looks like the best bet for soon to be exwindows users.

---

### Post by TheWizzard on 2006-12-28
> **Gowator said:**
> The point is most people will stick with defaults, they don't have time to secure everything and by giving every user root privs once they crack that users password is asking for problems....

exactly the reason the ubunto approach is more secure :D

---

### Post by TheWizzard on 2006-12-28
> **akak8ty said:**
> Are you capable of being nice? I've yet to hear it- and don't bother responding. There are far more pleasant people here to talk to.
aysiu is one of the nicest, helpful persons on this forum. what's your problem :confused: 

on topic: there's always a trade off between security and userfriendliness. and i think ubuntu is  doing a good job. basically thee are 3 kinds of security treads: 
System: you want your system to operate OK
Files: you want your files to be OK
Privacy: you don't want strangers to be able to see your files

i think the bottom line is to encrypt your files and to make regular back-ups :-k

---

### Post by BoneKracker on 2006-12-29
...and you want timely security patches to protect you from increasingly frequent zero-day style exploits.

I saw a detailed (if somewhat non-scientific) analysis of security patch timeliness a few months ago that showed ubuntu is the fastest of the major distributions (and, surprisingly, that Suse pretty much _blows_ dead moose).  

Windows isn't even in the same ballpark, with something like 20% of the known exploits remaining unpatched at any given time, in many cases months and even years after their discovery (compared to a number that rounds off to zero for Linux).

When it comes to selecting a distribution, security is a primary consideration.  But _I worry less about configuration (which I am happy to do) and worry more about software quality and patch timeliness (which are beyond my control)_.

Check it out here (I know it's probably inaccurate, but it's an important facet to consider):
[http://searchsecurity.techtarget.com/originalContent/0,289142,sid14_gci1202417,00.html](http://searchsecurity.techtarget.com/originalContent/0,289142,sid14_gci1202417,00.html)

---

