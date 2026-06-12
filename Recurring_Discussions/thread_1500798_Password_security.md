---
title: "Password security"
date: 2010-06-03
forum: Recurring Discussions
---

### Post by ken.sharp on 2010-06-03
Ok, so Ubuntu security is such that we do not have Anti-Virus protection, Firewall protection is pretty gimp (Compared to two way firewalls such as Zone-Alarm), 

... and anybody could send a command to your computer unless you have to type in a password for Administrative privelages.

Here's my question: How often has the pop-up asking for your password EVER came up WITHOUT you typing your password?

Does it not come up when YOU are trying to install a program?

Has it EVER popped up just out of the blue without YOU trying to do something?

All I'm saying is: for myself and others (who have run systems with zero security for several years) (who know how to keep a system safe) (who know how to backup data just in case) (who are willing to risk everything because the inconvieniences of such security measures are worse than the risks of viruses to them) ...

Why is there not a way to shut off the Linux equivelant to the M.S. User Account Controls?

Simple question right. 

Yet every post about this topic just says, "you'll get used to it".

Does nobody question this after using it for a while?

Has it ever saved your computer? 

I am sure and have no doubt that there are a few stories out there.

But how many more stories are there out there in which it has been nothing more than an Annoyance and a deterent to new users?

It is obvious that the only two reasons why a new user would have any troubles making the switch today with Ubuntu 10.04 is just two reasons.

1. The security needs work.
2. A system like Wine needs improvements.

Whoever can accomplish these two tasks can make Linux Ubuntu more popular than any other operating system out there. 

To give you an idea of the popularity factor: Oakley sun-glasses: They are not really so special. Others can make almost exact replicas; yet, they sold for hundreds of dollars a pair and everybody was buying them in the 80's. Their popularity came from one thing. They knew the customer was always right. 

Case in point: I have heard of several customers who had purchased their $100 plus sun glasses who contacted the company. The company (on each and every occasion) sent the customers a box full of new Oakleys. Obviously the sunglasses were cheap to make compared to the price they were sold at. But Oakley knew how to satisfy the customers.

If Linux does the same... by correcting the two factors i mentioned... Linux would be a global competitor and the developers would be showered with donations from busninesses who would appreciate the O.S. and want it to do this or that for their business. If Linux continued with this customer satisfaction philosophy... it would eventually be capable of putting its competitors six feet under in our lifetime (unless its competitors learn the importance of customer satisfaction).

Anyways I have learned how to reduce the password request to a touch of the space bar... That is the best I could come up with after haveing the O.S. installed for one full day. 

Now to see if I can get MSO2010 Professional to run in Wine, which I have never ran before... being new to Linux. 

So far Linux is pretty simple to figure out... but the MSO2010 is needed for college... because lets face it, nobody wants to do their citations all by hand with several books out on how to do every type of citation. I go to a University which requires you to publish your work... I write papers with citations every week. So Wine had better work for this. (I have installed all of the citation tools available for Linux as well, so if Wine does not work, I may see if anything else will do the job. Then I am back to Windows7 until they get that fixed if this does not work. 

By the way, I don't mind things being complex, obviously; I just want there to BE a way to do things. I keep everything backed up and secured on flash drives, DVD disks, & external H.D. s. Risks? What risks?

For example I have my entire installation (programs, files, installers, system files, etc.) the whole thing backed up on external H.D. as well as DVD disks. And I can wipe my H.D. reformat it, delete it, etc. and simply pop the disks in and install the entire O.S. without an install disk, simply by copying the files from the disk into the partition. It takes 20 miniutes and It works great. So there is nothing I can lose there even if my whole computer is hit by a meteorite and driven 20 ft under. I can get new hardware and in 20 minutes I'm back where I started. 

Then my college work, I keep it backed up on flash drives, which I swap out.

Personal info I keep it on Disks and flash drives which are dual encrypted. 

So again I say, Risk? What risk?  

I prefer getting viruses to having an O.S. that is worse than a virus. 

1. A virus to me is a 20 miniute fix.
2. An O.S. that is annoying to me that can never be fixed... that is worse than any virus I could ever imagine. It is the whole reason I dislike Microsoft! Because they started thinking they were right and they knew what was best for the customer... Thus you can not do several things with M.S. Windows O.S. Isn't that the whole point to switching? Isn't that why we prefer Firefox over explorer? Isn't that what the customers who switch to Open Source O.S.s all HOPE for?

Remove the helmet rules and give the customers the options. Warn them fully about the risks. And let them climb trees.

---

### Post by rookcifer on 2010-06-03
People who complain about having to spend 5 seconds of their time to type in a password occasionally will never have secure systems.

And sudo is not the same thing as UAC, as UAC was put in Windows intentionally as an annoyance (not as a security boundary).

---

### Post by snowpine on 2010-06-03
Hi Ken, in Linux there is a user called "root" who can do ANYTHING without typing a password. The creators of Ubuntu have decided to disable the root account and use "sudo" instead. You can read all about this decision (including instructions to re-enable the root account, as well as an explanation why it's not a good idea) here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

I think you are over-reacting and reading too much into Ubuntu's default settings. The default is a sane basic configuration for most users, but it is only a default; you can easily change the system for your needs--this is the true meaning of open-source. :)

---

### Post by pricetech on 2010-06-03
In before the mods close.

---

### Post by sanderd17 on 2010-06-03
Use other linux distro's, like puppy, it only has a root account so you never need to type your password except when you log in. 

And for wine: go complain to the software makers if they could make a Linux version of go to the wine team and fix bugs.

Btw, I once saw a desktop theme that asked for a password and didn't thrust that. Opened in a virtual machine and it was a virus. A little virus, it only did a ping to a certain site but still a virus.

---

### Post by sydbat on 2010-06-03
So um...no one noticed that this "person" signed up simply to troll?  This is their one and only post. 

Either they are a troll or one sophisticated spam bot...

---

### Post by SunnyRabbiera on 2010-06-03
Probably a troll

---

### Post by lovinglinux on 2010-06-03
> **ken.sharp said:**
> Ok, so Ubuntu security is such that we do not have Anti-Virus protection, Firewall protection is pretty gimp (Compared to two way firewalls such as Zone-Alarm)

Seriously?

Anyway, there are several anti-virus programs for Linux, but not everybody use them because is pointless, unless you need to scan a Windows partition or protect other Windows machine in your network.

The Firewall included with Ubuntu is very powerful and works like a charm. Nevertheless, it is usually unnecessary. The thing is that, unlike Windows, Ubuntu doesn't have (by default) listening servers that you should be worried about. So all ports are already closed and using a firewall would only block traffic to ports that would reject any unrequested incoming traffic anyway. Windows users on the other hand need the firewall because all the security holes and useless dangerous services that listen to ports by default.

BTW, Zone-Alarm sucks. The best free firewall for Windows I ever used is Comodo.

Read the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=510812) sticky.

> **ken.sharp said:**
> ... and anybody could send a command to your computer unless you have to type in a password for Administrative privelages

No, they can't. As already mentioned, all ports are already closed. By default, there are no applications capable of accepting remote command execution running.

> **ken.sharp said:**
> Here's my question: How often has the pop-up asking for your password EVER came up WITHOUT you typing your password?

I don't understand the question. The system will ask for password every time you need to perform an action that require administrative rights. After inserting the password on a terminal, you will continue to have administrative rights for a couple of minutes.

> **ken.sharp said:**
> Does it not come up when YOU are trying to install a program?

See previous question.

> **ken.sharp said:**
> Has it EVER popped up just out of the blue without YOU trying to do something?

No. I never heard of such thing.

> **ken.sharp said:**
> All I'm saying is: for myself and others (who have run systems with zero security for several years) (who know how to keep a system safe) (who know how to backup data just in case) (who are willing to risk everything because the inconvieniences of such security measures are worse than the risks of viruses to them) ...

Why is there not a way to shut off the Linux equivelant to the M.S. User Account Controls?

Simple question right. 

See posts #2 and #3. I agree with #2.


> **ken.sharp said:**
> Yet every post about this topic just says, "you'll get used to it".

You'll get used to it.

> **ken.sharp said:**
> Does nobody question this after using it for a while?

Yes. Read post #2.

> **ken.sharp said:**
> Has it ever saved your computer? 

I am sure and have no doubt that there are a few stories out there.

But how many more stories are there out there in which it has been nothing more than an Annoyance and a deterent to new users?

I almost deleted my entire system. It wasn't exactly my mistake, but it is too long to explain here. The fact is that this could happen to anyone.


> **ken.sharp said:**
> It is obvious that the only two reasons why a new user would have any troubles making the switch today with Ubuntu 10.04 is just two reasons.

1. The security needs work.
2. A system like Wine needs improvements.

Whoever can accomplish these two tasks can make Linux Ubuntu more popular than any other operating system out there.

Any system needs security improvements and maintenance. There is no such thing as a 100% secure system. Nevertheless, everything you have pinted out is not a problem, but a misunderstanding from your part about how Linux works and the a strong dependency on how things work on Windows. Basically you need to enroll in a "Windows Detox" program.

You are not supposed to use Wine for everything. Use Wine only when you can't find an alternative native application. Most of the time you will be able to find software for Linux that do the same job or better.  I only use Wine for one application and it works like a charm. Obviously that you can't run all Windows applications with Wine and some will work with serious limitations, but considering what Wine does, it is pretty amazing. You have no idea how difficult is to make such application and release it for free.

> **ken.sharp said:**
> To give you an idea of the popularity factor: Oakley sun-glasses: They are not really so special. Others can make almost exact replicas; yet, they sold for hundreds of dollars a pair and everybody was buying them in the 80's. Their popularity came from one thing. They knew the customer was always right. 

Case in point: I have heard of several customers who had purchased their $100 plus sun glasses who contacted the company. The company (on each and every occasion) sent the customers a box full of new Oakleys. Obviously the sunglasses were cheap to make compared to the price they were sold at. But Oakley knew how to satisfy the customers.

If Linux does the same... by correcting the two factors i mentioned... Linux would be a global competitor and the developers would be showered with donations from busninesses who would appreciate the O.S. and want it to do this or that for their business. If Linux continued with this customer satisfaction philosophy... it would eventually be capable of putting its competitors six feet under in our lifetime (unless its competitors learn the importance of customer satisfaction).

Ubuntu is already free, so what is the point?

> **ken.sharp said:**
> Now to see if I can get MSO2010 Professional to run in Wine, which I have never ran before... being new to Linux. 

So far Linux is pretty simple to figure out... but the MSO2010 is needed for college... because lets face it, nobody wants to do their citations all by hand with several books out on how to do every type of citation. I go to a University which requires you to publish your work... I write papers with citations every week. So Wine had better work for this. (I have installed all of the citation tools available for Linux as well, so if Wine does not work, I may see if anything else will do the job. Then I am back to Windows7 until they get that fixed if this does not work.

It has been a long time since I needed to publish scientific articles with citations, but I never used Office for that. There are several tools for that and I'm sure you will find a better Linux version.

> **ken.sharp said:**
> By the way, I don't mind things being complex, obviously; I just want there to BE a way to do things. I keep everything backed up and secured on flash drives, DVD disks, & external H.D. s. Risks? What risks?

For example I have my entire installation (programs, files, installers, system files, etc.) the whole thing backed up on external H.D. as well as DVD disks. And I can wipe my H.D. reformat it, delete it, etc. and simply pop the disks in and install the entire O.S. without an install disk, simply by copying the files from the disk into the partition. It takes 20 miniutes and It works great. So there is nothing I can lose there even if my whole computer is hit by a meteorite and driven 20 ft under. I can get new hardware and in 20 minutes I'm back where I started. 

Then my college work, I keep it backed up on flash drives, which I swap out.

Personal info I keep it on Disks and flash drives which are dual encrypted. 

So again I say, Risk? What risk?  

I prefer getting viruses to having an O.S. that is worse than a virus. 

1. A virus to me is a 20 miniute fix.
2. An O.S. that is annoying to me that can never be fixed... that is worse than any virus I could ever imagine. It is the whole reason I dislike Microsoft! Because they started thinking they were right and they knew what was best for the customer... Thus you can not do several things with M.S. Windows O.S. Isn't that the whole point to switching? Isn't that why we prefer Firefox over explorer? Isn't that what the customers who switch to Open Source O.S.s all HOPE for?

Remove the helmet rules and give the customers the options. Warn them fully about the risks. And let them climb trees.

Seriously? You need to read more about how Linux works and how much you can do with it before posting such threads. I don't mean to be rude or disrespectful, but you are making a fool of yourself.

---

### Post by asbesto on 2010-06-10
Me too in this thread. The password request in Ubuntu Desktop is totally useless, a waste of time, resources, and madness for users.

I have to write MY password for MY computer in MY house, where I live ALONE with my wife. Who can stole my account LOCALLY? MY DOG? :confused:
Also considering that I don't have any open port, so no ssh or telnet or whatsoever? :)

And the password came out for gdm login; for adding packages, for editing network configuration, for changing system parameters, startup applications, services... it's incredibly stupid.

I wrote an howto about avoiding all this, but I think I cant post here because the administrators think this is a "way to obtain illegal access to systems". I can't write about that, I will be kicked out of the forum. You can find by yourself from my web pages around in the internet.

Instead, I wrote my howto on our wiki. But everything I wrote is all in the man pages, so no secret circunvention or security breaches.

Some time ago they also added the PolicyKit, doing the same work as su, sudo, wheel group, pam, keyring manager and i don't remember what else: asking for password. I was officially warned for showing how to disable password asking for that crap: it was in the man page of PolicyKit, as example! And now, as I stated time ago, this PolicyKit was removed from Ubuntu.

This is not Windows, so why has to become stupid as Windows? 

:D

---

### Post by BoneKracker on 2010-06-10
> **asbesto said:**
> This is not Windows, so why has to become stupid as Windows?

Spoken like someone unaware of how the present authentication security features in Windows evolved.

While UNIX existed as a multi-user OS from the beginning, DOS/Windows was not.  Windows was a fundamentally disconnected, single-user operating system.  No need whatsoever for any kind of security of access controls on that kind of system.

UNIX and its variants have always had a privileged account (or accounts) for administration and less-privileged accounts for users.  Windows tried to incorporate this feature about 15 years ago, but made it pretty much optional.  Developers and users pretty much blew it off.  End-user applications (such as games) continued to be written that could only run if you started them as an administrator.  As a result, users generally continued to run their systems as administrators.

Only recently (past five to eight years or so), and generally only in corporate IT settings, have users been forced or advised to operate windows without administrative privileges.  Even in XP, when you installed it, you were automatically given an administrative account.  Eventually this started to take its toll on the security reputation of Windows, as malware after malware exploited this weakness.

Finally, in Vista, Microsoft tried to force users to operate without admin privileges, but they kind of screwed up their implementation, making it awkward, intrusive, and annoying.

On the Linux side, systems administrators have typically not even wanted to do administrative tasks in a graphical environment (which itself introduces security risks by broadening the attack surface), so simply being able to login as root or su root has been adequate.  However, now that "desktop linux" is becoming popular, there are many users who lack the skills to administer their own systems and it has become necessary to temporarily provide an easy mechanism to grant administrative privileges to graphical processes started by an unprivileged user.

That happens to be similar to what you see in the latest versions of Windows, but it's not copied from Windows.  On the contrary, Windows' new mechanisms of temporarily authorizing administrative rights to non-administrative mimics what has been available in Linux for a long time.

---

### Post by pricetech on 2010-06-24
> **BoneKracker said:**
>  End-user applications (such as games) continued to be written that could only run if you started them as an administrator.

Sadly this is true of even "reputable" applications from equally "reputable" vendors.

I'd like to have the time I've spent working around this back so I can put it to good use.

---

### Post by Chame_Wizard on 2010-06-24
I love the Linux password security,especially those by the Debian family based distro(Kubuntu in my case).:lolflag:

---

### Post by Penguin Guy on 2010-06-24
> **ken.sharp said:**
> It is obvious that the only two reasons why a new user would have any troubles making the switch today with Ubuntu 10.04 is just two reasons.

1. The security needs work.
2. A system like Wine needs improvements.

The security model was designed for big servers with terminal clients and was never really adapted properly for the desktop. The developers don't like change, so we're probably stuck with it forever. If you want to disable passwords completely just [take a look on Google]("http://www.google.com/search?q=how+to+disable+password+prompts+in+Ubuntu"), we're not allowed to post instructions on disabling authentication on these forums.

---

### Post by -kg- on 2010-06-27
Penguin Guy *"almost"* said it all.

Hey, if you want to enable your root account and never have to type in a password again, then by all means, ***do it!***  There's no one here who is trying to tell you how to use or configure your computer - they're only trying to tell you why you might not want to, and I think there have been some well-presented arguments.

In the end, though, Ubuntu (and most every other Linux distribution) is "free and open-source"; you do not have to "ask permission" from Canonical or anyone here to install, configure, re-compile, or do anything you want to with your computer or installation.  You're free to massively change your installation and come out with your own distribution - based on Ubuntu, Debian, or even Arch or Slackware, if you want to and have the skill.  No one here, or in the Linux community at large, would even *think* of stopping you!

Just don't expect us to violate Forum policies and hand you that information here.  As Penguin Guy said, the information is all over the Internet.  Find a page, follow the directions, and enjoy!  The Linux philosophy is, "It's *your* computer, and you should be able to do what you want to with it!"

---

### Post by prodigy_ on 2010-06-27
> **ken.sharp said:**
> Firewall protection is pretty gimp
Obvious troll is obvious.

/yawn

---

On an unrelated note, I just keep root (su or sudo -i) shell open at all times. And since in Linux I prefer to do things from CLI, pop up windows don't bother me.

---

### Post by cariboo on 2010-06-27
This is just to clear up some misconception about root logins. The original [sticky]("http:///ubuntuforums.org/showthread.php?t=716201") was rather poorly worded, it mainly stated we don't allow graphical login as root tutorials. The new [sticky]("http://ubuntuforums.org/showthread.php?t=1486138") states what our policy is. We have no problem with anyone showing someone how to log in as root, as long as the dangers and/or alternate ways of doing the same thing are explained at the same time.

As far as we're concerned, it's your computer, and you can do anything you want with it.

---

### Post by sydbat on 2010-06-28
> **prodigy_ said:**
> Obvious troll is obvious.

/yawn

---

On an unrelated note, I just keep root (su or sudo -i) shell open at all times. And since in Linux I prefer to do things from CLI, pop up windows don't bother me.Hmmm...where have I heard that before...[http://ubuntuforums.org/showpost.php?p=9406054&postcount=6](http://ubuntuforums.org/showpost.php?p=9406054&postcount=6)

---

### Post by asbesto on 2010-06-28
Why everybody is confusing the absurd asking and asking and asking for the same password on a personal computer with "enabling root access"???

"Enabling root access" has nothing to do with this! :)

---

### Post by -kg- on 2010-07-02
> **asbesto said:**
> Why everybody is confusing the absurd asking and asking and asking for the same password on a personal computer with "enabling root access"???

"Enabling root access" has nothing to do with this! :)

Then I must be very confused indeed.  This is the way I see it:

Most "hacking" is done not to boot into a computer and log in as a user.  It is done while the computer is running and already logged into a user's account.  While sometimes the hacker tries to hack in manually, the usual way is to cause some software (a virus, or trojan, or key logger) to be installed.

Under Linux, this is mostly done as an Administrative task and requires the Administrative password to perform them.  This gives you security in that you have to acknowledge that you're performing this action and it's not some malware (or someone) doing so without your knowledge.

If you log in as Super User (root), you have access to all these functions without the need of the password or permissions, since root has access to everything.  This is dangerous in that any software from any source has these permissions as well.

If you eliminate the password under normal users accounts, then every user that has an account has total access to everything as well, all without the need for a password to acknowledge it, including any malware that attempts to install itself.  Every user has access to every other users accounts, and to completely screw up the entire installation, knowingly or unknowingly.

So under the "no password" scenario, everyone has access to the entire system and its administrative commands.  This is why I'm confused, because I can see no difference between this and logging in as root.  In both cases, everyone (including malware) has access to everything and can do anything with and to the system without a password.

I don't like to be confused.  Can you explain the difference between requiring no password for Administrative commands and access for normal user accounts, and logging in as root (other than using the users personal settings, naturally)?

---

### Post by asbesto on 2010-07-02
> **-kg- said:**
> Then I must be very confused indeed.  This is the way I see it:

If you eliminate the password under normal users accounts, then every user that has an account has total access to everything as well

So under the "no password" scenario, everyone has access to the entire system and its administrative commands.  This is why I'm confused, 

I don't like to be confused.  Can you explain the difference between requiring no password for Administrative commands and access for normal user accounts, and logging in as root (other than using the users personal settings, naturally)?

I'm not talking about a multiuser system; I'm just talking about my own computer, with no other users at all. So, no one can log into my machine, becase they don't know how to do this and there are no users on my system other than me. For example I don't have a sshd daemon running, no apache/php, no ftp or telnet or anything at all.

I can only log locally from my keyboard. Who can log in as user and gain access here? Normally, nobody. 

And if an hacker can exploit my system, it certainly does it with a security flaw that permit him to gain root access at all without any care about passwords etc. So having such kind of security by passwords is totally unuseful to protect me from stack smashing or other kind of attacks. :)

And so, having such a painful asking for the same password again and again for doing normal tasks, on my desktop pc, is a waste of time, and is very annoying.

---

