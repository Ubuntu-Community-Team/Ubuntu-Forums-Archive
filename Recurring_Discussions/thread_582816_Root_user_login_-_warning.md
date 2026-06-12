---
title: "Root user login - warning"
date: 2007-10-20
forum: Recurring Discussions
---

### Post by hashaam83 on 2007-10-20
I have enabled root user and I am able to login as root user successfully.

The thing, as I login as root user I get following warning message:

**This session is running as privileged user.**

How can I turn this message off?

Hashaam

---

### Post by steve.horsley on 2007-10-20
Stop logging in as root. You should not be doing it - it poses a big security risk.

Try to mentally separate the two roles of user and administrator. When you need to wear your admin hat (which will be often at first, but less often as you get things set up how you like them), you will probably want either a root command prompt or a root file manager. You can get these for as long as you need them like this:

For root command prompt, open a command prompt and enter the command:
**sudo -i**
You may be asled for your password again. Now you have a root prompt where you can do your admin stuff, and then **exit** when you're done.

For a root file manager, press Alt-F2 and enter the command:
**gksudo nautilus**
which gives you a root privileged file manager. 

These steps are not too onerous, and nt running as root protects your system from trojans, macros and (more likely) user errors.

So you can become root when you need to, but don't be root all the time.

---

### Post by hashaam83 on 2007-10-20
I know it poses a security risk but I am sick of entering my password for any application I run and any command I execute at the terminal.

So, any ideas how to disable the warning?

Hashaam

---

### Post by Colro on 2007-10-20
Most applications you run and most commands you enter **don't** require root. You won't have to enter your root password very often at all once your system is set up the way you want it. There's a million and one reasons to *not* run as root, laziness really can't make up for all of them.

---

### Post by Jive Turkey on 2007-10-20
ROFL-don't bother disabling the warning because you are going to break the OS in less than a week and have to reinstall  anyway.  Seriously, are you using that pc for webbrowsing and email and stuff?  You are inviting disaster if you run those apps w/ root privileges.  There are a number of apps and activities that (for better or worse) rely on the sandboxing of limited privileges in order to not hose your system.

Sorry I don't know the answer to your question.  good luck, I hope it goes well for you.

---

### Post by kerry_s on 2007-10-20
> **hashaam83 said:**
> I have enabled root user and I am able to login as root user successfully.

The thing, as I login as root user I get following warning message:

**This session is running as privileged user.**

How can I turn this message off?

Hashaam

try looking in the root folder files, most likely .bash_profile or .bashrc to see if it's running the message script, then just comment it out. if it's not being run from there then check the /usr/bin executable for the session. you might also try running top with the message still up to see the script name if any.

---

### Post by Soarer on 2007-10-20
I guess as Ubuntu & Linux become more popular amongst ex-Windows users, we are going to get more of these kind of questions.  :(

---

### Post by kerry_s on 2007-10-20
> **Soarer said:**
> I guess as Ubuntu & Linux become more popular amongst ex-Windows users, we are going to get more of these kind of questions.  :(

it's no big deal, were not children here, we can decide what we want to do and live with what ever happens. we all have the right to choose.
if you don't make the mistakes, you never learn from them.

---

### Post by hashaam83 on 2007-10-20
Fine.

I have switched to normal user and stopped using root user session.

Thanks

Hashaam

---

### Post by Perfect Storm on 2007-10-20
Kerry is right, they will learn. Computers that run root will be owned in matter of time.


hashaam83: which aplications are you tired of typing in the password?

---

### Post by Soarer on 2007-10-20
> **kerry_s said:**
> it's no big deal, were not children here, we can decide what we want to do and live with what ever happens. we all have the right to choose.
if you don't make the mistakes, you never learn from them.

I don't disagree - I can just imagine the flames in Windows' forums when it all goes wrong & they can't fix it or get help.

Hashaam - good for you. I don't think you'll regret it.

---

### Post by ravenus on 2007-10-20
I guess the fact that you're not running the apps as root makes it possible to run linux systems without AV and spyware guards.

---

### Post by JohnCub on 2007-10-20
Something that struck me while reading this thread is a bit I'd like to borrow from Wikipedia's principles:

Don't bite the newbies.

As we already understand Windows based security is a much different world than in other operating systems.  This concept of having to allow risky situations by requiring a password is entirely foreign to many and even the UAC in vista is turned off on every user's vista machine I've touched.  It isn't ideal but it is a fact of life. To a certain degree it is natural to try to normalize situations by making them fit into our way of thinking, and running as root is one of the ways that windows users will try to accomodate their new system to behave like their old one.

Perhaps the solution is to educate, not castigate.

I don't know all the ins and outs of linux systems, only what I've picked up over the years.  It was firmly engrained in my from long ago that running anything as root is a bad idea.  

But in my mind I look at it this way:

Unix based operating systems have a way of running any command from a terminal.  If you can do it, you can do it with text.  Most systems have a "way in" whether it is telnet, ssh, an exploit in a game or other program, or what have you.  If someone can "get in" or take control of your session they will be able to do anything you can do.  Whether it is to use the built-in controls to make your computer a spam box, erase the contents of your hard drive, or even read every file on your system.  Therefore by running as a non-privileged user you lower your risk of losing or giving away your own data, which often amounts to knowing everything necessary to "be you" or "use you."  It can and will be frustrating to learn and retype your password for administrative duties but in time it will become second nature.  Once you have your own understanding of the process it will become part of your "computer-psyche" and it will occur to you, as it did to me, that it is deplorable that other operating systems do not follow suit, if only to protect your own personal data.


Embrace.  Not forsake.

---

### Post by sas on 2007-10-20
If it's the same applications you're using each time which are prompting you for root access you can make sudo not ask you for your password when running those applications, you do still need to type 'sudo' however.

See 'man sudoers' or  [http://www.gratisoft.us/sudo/man/sudoers.html#nopasswd_and_passwd](http://www.gratisoft.us/sudo/man/sudoers.html#nopasswd_and_passwd)

---

### Post by H1tm3n on 2007-10-21
> **Artificial Intelligence said:**
> Kerry is right, they will learn. Computers that run root will be owned in matter of time.


hashaam83: which aplications are you tired of typing in the password?

I had to gksudo my xmms player, LinuxDC++, and some other programs, because it chease to work the way they supposed to...

I was googling for an answer on how to login as root, but you guys underminded me... 


maybe u can help me with this:
the most problem I get is that of programs not remembering the last settings I had set up when I ran it.... for exmaple, xmms doesn't remember playlist, dc++ doesn't remmember the share....

it's installed in home folder.... probably some settings in root privileged folders??:(

---

### Post by Perfect Storm on 2007-10-21
I dunno if it's beyond repair, if you messed around with alot of permission. What is the username you made when installing ubuntu?

xmms is old as dust and I recommend using another player.

---

### Post by kerry_s on 2007-10-21
> **H1tm3n said:**
> I had to gksudo my xmms player, LinuxDC++, and some other programs, because it chease to work the way they supposed to...

I was googling for an answer on how to login as root, but you guys underminded me... 


maybe u can help me with this:
the most problem I get is that of programs not remembering the last settings I had set up when I ran it.... for exmaple, xmms doesn't remember playlist, dc++ doesn't remmember the share....

it's installed in home folder.... probably some settings in root privileged folders??:(

it's most likely you ran them with sudo, changing the owner to root, thus stripping you of access. just delete the hidden settings folders in your home directory for those applications. you might have to do it as root(press alt+f2 type> gksu nautilus /home) ctrl+h to see hidden files.

---

### Post by H1tm3n on 2007-10-23
I installed fresh Gusty, now it works ;)

BUT

I have another question:

DO I REALLY have to enter root pass (open gksudo nautilus, which unfortunatly hangs after few actions)... to read from my CD-ROM drive?

how do I manage groups to have that allowed.... I have set permisions so that I could read cd-rom drive in users and groups, but it doesn't work :confused:

[http://www.americasarmy.lt/hitman/screenshot1.png](http://www.americasarmy.lt/hitman/screenshot1.png)
[http://www.americasarmy.lt/hitman/screenshot2.png](http://www.americasarmy.lt/hitman/screenshot2.png)
[http://www.americasarmy.lt/hitman/screenshot3.png](http://www.americasarmy.lt/hitman/screenshot3.png)
[http://www.americasarmy.lt/hitman/screenshot4.png](http://www.americasarmy.lt/hitman/screenshot4.png)

---

### Post by quandary on 2007-10-23
Don't worry about the warnings. 
As hardcore windows users, we know what we do; so just ignore these Mac freaks.
If you want a secure OS, get OpenBSD. Don't touch LInux, then.
Working as root worked perfectly well for me since months now.
Reentering the root password every time is a pain in the ***, and probably much more insecure.

To deactivate the root warning:
login as root ;-)

Open gnome-terminal, type:
gedit /etc/bash.bashrc

search for the hint routine, which should look like this:
--------------------------------------------------------
 sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi
---------------------------------------------------

just comment it out. Looks like this, then:
----------------------------------------------------
# sudo hint
#if [ ! -e $HOME/.sudo_as_admin_successful ]; then
#    case " $(groups) " in *\ admin\ *)
#    if [ -x /usr/bin/sudo ]; then
#	cat <<-EOF
#	To run a command as administrator (user "root"), use "sudo <command>".
#	See "man sudo_root" for details.
#	
#	EOF
#    fi
#    esac
#fi
----------------------------------------------------

save. finished.

For windows-convenience, add at the end of the file:
---------------------------------
alias cd..='cd ..'
alias cls='clear'
---------------------------------

optionally, add also:'
-------------------------------
alias dir='ls -a'
---------------------------------
and:
-------------------------------
alias chkdsk='fsck -n'
---------------------------------
and:
-------------------------------
alias scandisk='fsck -r'
---------------------------------

Think that should have helped.

---

### Post by Soarer on 2007-10-23
> **quandary said:**
> Don't worry about the warnings. 
As hardcore windows users, we know what we do; so just ignore these Mac freaks.
If you want a secure OS, get OpenBSD. Don't touch LInux, then.
Working as root worked perfectly well for me since months now.
Reentering the root password every time is a pain in the ***, and probably much more insecure.

To deactivate the root warning:
login as root ;-)

Open gnome-terminal, type:
gedit /etc/bash.bashrc

search for the hint routine, which should look like this:
--------------------------------------------------------
 sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi
---------------------------------------------------

just comment it out. Looks like this, then:
----------------------------------------------------
# sudo hint
#if [ ! -e $HOME/.sudo_as_admin_successful ]; then
#    case " $(groups) " in *\ admin\ *)
#    if [ -x /usr/bin/sudo ]; then
#	cat <<-EOF
#	To run a command as administrator (user "root"), use "sudo <command>".
#	See "man sudo_root" for details.
#	
#	EOF
#    fi
#    esac
#fi
----------------------------------------------------

save. finished.

For windows-convenience, add at the end of the file:
---------------------------------
alias cd..='cd ..'
alias cls='clear'
---------------------------------

optionally, add also:'
-------------------------------
alias dir='ls -a'
---------------------------------
and:
-------------------------------
alias chkdsk='fsck -n'
---------------------------------
and:
-------------------------------
alias scandisk='fsck -r'
---------------------------------

Think that should have helped.

This post should come with a Public Health Warning, so here it is.

If you do the above, and get into problems, it is likely that no-one on these forums will be able to help you.

There are threads running at the moment - one user completely messed up the permissions in his system by running as root, and another ran sudo fsck on a mounted filesystem (just like renaming it to chkdsk as suggested above) and had to re-install.

I think this post is stupid & irresponsible but, hey it's your system that will break, not mine.

---

### Post by H1tm3n on 2007-10-23
> **Soarer said:**
> This post should come with a Public Health Warning, so here it is.

If you do the above, and get into problems, it is likely that no-one on these forums will be able to help you.

There are threads running at the moment - one user completely messed up the permissions in his system by running as root, and another ran sudo fsck on a mounted filesystem (just like renaming it to chkdsk as suggested above) and had to re-install.

I think this post is stupid & irresponsible but, hey it's your system that will break, not mine.


I'm not for disabling root pass in general, but, tell me, What bad could I possibly do by copying files from CD-ROM [Read Only Memory] disk? ... if nothing, then tell me how to at least get rid of that one...

---

### Post by JBAlaska on 2007-10-23
> This post should come with a Public Health Warning, so here it is.

If you do the above, and get into problems, it is likely that no-one on these forums will be able to help you.

There are threads running at the moment - one user completely messed up the permissions in his system by running as root, and another ran sudo fsck on a mounted filesystem (just like renaming it to chkdsk as suggested above) and had to re-install.

I think this post is stupid & irresponsible but, hey it's your system that will break, not mine.

While I do agree with the concept of using Ubuntu as a non privileged user, calling someone "stupid and irresponsible" is counter to the spirit of Ubuntu and these fine forums imho.

In my country (US) there is a alarming trend to protect people from them selfs, the government seems to believe that everyone is a ignorant moron and needs a warning label or law for everything from "the coffee in this cup is hot and will burn you" to "Clairol Hair Coloring: Do not use as an ice cream topping" <--Real
If you treat everyone as a moron, soon you will have a whole generation of moron's...erm..wait..to late lol.

But I digress, If a person wants to run his/her computer as root and understands and excepts the security implications, so be it. Telling users that they are stupid or that their computer will self destruct if run as root is not the way to educate them on the security advantages of running with reduced privileges.

---

### Post by Soarer on 2007-10-24
> **JBAlaska said:**
> While I do agree with the concept of using Ubuntu as a non privileged user, calling someone "stupid and irresponsible" is counter to the spirit of Ubuntu and these fine forums imho.

In my country (US) there is a alarming trend to protect people from them selfs, the government seems to believe that everyone is a ignorant moron and needs a warning label or law for everything from "the coffee in this cup is hot and will burn you" to "Clairol Hair Coloring: Do not use as an ice cream topping" <--Real
If you treat everyone as a moron, soon you will have a whole generation of moron's...erm..wait..to late lol.

But I digress, If a person wants to run his/her computer as root and understands and excepts the security implications, so be it. Telling users that they are stupid or that their computer will self destruct if run as root is not the way to educate them on the security advantages of running with reduced privileges.

I completely agree with your sentiment. 

The point is that this was posted in 'Absolute Beginner Talk:' where people are unlikely to ''understands and excepts the security implications'. They are more likely to ruin their system, blame Linux and flame Ubuntu. 

Of course, if they understand the consequences, as quandary probably does, it is fine. Linux is meant to be used how you want to. I just mentioned what the likely consequences are.

And I said the post was "stupid and irresponsible", not the poster. I am very sorry if I gave that impression.

---

### Post by Soarer on 2007-10-24
> **H1tm3n said:**
> I'm not for disabling root pass in general, but, tell me, What bad could I possibly do by copying files from CD-ROM [Read Only Memory] disk? ... if nothing, then tell me how to at least get rid of that one...

Using 'sudo cp' could overwrite  files which have the same name, if you are not careful where you copy to. I agree though it should not be necessary to become root to read CDROMs, and indeed it is not on my system, although it can be on USB drives.

I would guess that it's a problem in fstab, but I don't know enough to be sure. I'm sorry I can't help at this time.

---

### Post by sujoy on 2007-10-24
well, i dont want to enable root login any where in my system but still i do want to know how to enable and disable root login from both the command mode and the starting welcome (login) screen.

just for the sake of knowing it ........ i am too curious I guess :)

---

### Post by quandary on 2007-11-25
> **Soarer said:**
> This post should come with a Public Health Warning, so here it is.

If you do the above, and get into problems, it is likely that no-one on these forums will be able to help you.

There are threads running at the moment - one user completely messed up the permissions in his system by running as root, and another ran sudo fsck on a mounted filesystem (just like renaming it to chkdsk as suggested above) and had to re-install.

I think this post is stupid & irresponsible but, hey it's your system that will break, not mine.


sudo fsck *hmmm*
that means he didn't worked as root (would not have had to type sudo if he worked as root...) and messed up his system non the less. You see, you can mess it up even without login as root ;-)

Anyway, mine worked well since more than 6 month now with root. Think that says enough. Still, if you don't know what you do, you even shouldn't use sudo...

Furthermore i don't think my post is stupid. Nor is it irresponsible. Working with a computer means you have to know what you do. If you don't, just about anything can happen, with or without root...
Considering security:
Do you seriously think adding WARNINGS will add anything more than ZERO to security? 
Just look at windows Vista. What a nightmare! Security has been hardened to the extent you can't run normal software anymore, and the only things that still work flawlessly are the viruses!

If a computer is hacked, it's mostly (95%) because of either misconfiguration, not updating, or of some bright spark using a easy to guess 4 digit password eg. 0815, or even better: p like password (no joke, these are actual passwords ...). 
Running cracks and keygens with rootkits, keyloggers etc. for sure is a good idea, also ;-)
What does not running  as root help you against all of these? NOTHING AT ALL!

No root account is good for servers. There you configure and install software once, and afterwards, you don't want that anybody can alter or access these settings. Then it's good to have no root account. But none the less, you still have to update your software. If you don't you are yourself the one to blame, not the root account.

But desktops are not servers. Their usage scenario is completely different. They need software/hardware being added/removed on a almost daily basis (eg. USB drives or CD's R/W), configurations change often, and some programs need access to the root filesystem (network tools, debuggers, IDE's, sometimes even games). And the list goes on and on. And unfortunately, some programs don't work correctly with sudo etc. So you have to be root, at least sometimes...

So one could also say: 
Running not as root does not protect you if your OS or your applications are coded improperly...
If there are applications that rely on not being used as root for their security, you shouldn't use them anyway.

---

### Post by monkey56657 on 2007-12-03
Stop having a moan at those who want to use root. 

Ive used root on Linux for about 2 years now, and a full administrator account on windows...and had no problems. Yes its less secure but its all about the users choice. Choice is everything. The user can choose to be less secure for the advantage of not being continually nagged or continually having to enter their password. 

I know on windows if you get prompted with a security message most people don't even read it anyway. The ones who do are those who wouldn't even understand it. 

If you have to preach about something go preach the difference between good and bad to kids...then we wont have to worry about security no more....no more damn hackers and malicious programmers!

---

### Post by Perfect Storm on 2007-12-03
> **monkey56657 said:**
> Stop having a moan at those who want to use root. 

Ive used root on Linux for about 2 years now, and a full administrator account on windows...and had no problems. Yes its less secure but its all about the users choice. Choice is everything. The user can choose to be less secure for the advantage of not being continually nagged or continually having to enter their password. 

I know on windows if you get prompted with a security message most people don't even read it anyway. The ones who do are those who wouldn't even understand it. 

If you have to preach about something go preach the difference between good and bad to kids...then we wont have to worry about security no more....no more damn hackers and malicious programmers!

I have been using linux in 8 years if we have to flexing muscles <eye-rolling smiley>, and I have never logged in as root.
It's completed on your own account to do so. You know the risk, but to encourage other people to do so is a no-no if they don't know what they are messing with. 
What you do is your case, but it's normal to tell how linux is build to run. No one is preaching here but telling how it should be run normally.

---

### Post by mroy on 2007-12-11
So, is there a way to disable the root warning at logon ?

---

### Post by aonegodman on 2007-12-13
What is the root default password installed by Ubuntu?

---

### Post by Dr Small on 2007-12-13
> **aonegodman said:**
> What is the root default password installed by Ubuntu?
By default, when you install Ubuntu, the root password is not enabled.
To use sudo, it would be the same password as your login password.

Dr Small

---

### Post by jken146 on 2007-12-13
> **mroy said:**
> So, is there a way to disable the root warning at logon ?
It was posted a little way up the page.

---

### Post by khurrum1990 on 2007-12-13
If some one wants to use root account, let them, they r compromising their own system security. If some one messes up ur files or breaks into ur system and damages it then don't say Linux or Ubuntu sucks. We warned u, its up to u whether u follow our warning or not.

---

### Post by ingram on 2007-12-13
> **monkey56657 said:**
> Stop having a moan at those who want to use root. 

Ive used root on Linux for about 2 years now, and a full administrator account on windows...and had no problems. Yes its less secure but its all about the users choice. Choice is everything. The user can choose to be less secure for the advantage of not being continually nagged or continually having to enter their password. 

I know on windows if you get prompted with a security message most people don't even read it anyway. The ones who do are those who wouldn't even understand it. 

If you have to preach about something go preach the difference between good and bad to kids...then we wont have to worry about security no more....no more damn hackers and malicious programmers!

:lolflag:

Yeah, because hackers are evil. Everything bad that happens on a computer is the fault of some nameless virus or some computer hacker?

I have to wonder where people come up with that crap. I would say that some //or even most// of the problems that get blamed on a virus or a hacker are because some idiot was using root or admin to do something and screwed up their system.

---

### Post by ByteJuggler on 2007-12-13
> **hashaam83 said:**
> I know it poses a security risk but I am sick of entering my password for any application I run and any command I execute at the terminal

Sorry but thats exagerating it.  You don't have to enter it for ***any/every application* **you run or ***any/every command ***at the terminal.  If you do 

```
sudo -s 
```

Once, then you'll have a root shell, no further password entry required. Furthermore, Ubuntu will remember your password for like 15 mins or something, so it won't ask you for it again immediately, even if you use sudo again. You can even make a shortcut on a toolbar to open a root shell when needed (which means a single entry when you open the window.)  Same for setting up a shortcut for a root Nautilus explorer.

Edit: You can even create yourself a "set uid" copy of the shell executable, which when run will give you a root shell and will never ask for a password.  However, that's a big security risk if someone ever hacks your user account, since they then have unfettered root access if they discover and run your special "root enabled" shell.   

Please, it's a *really* bad idea to just log in as root all the time.

---

### Post by Dr Small on 2007-12-13
> **ingram said:**
> :lolflag:

Yeah, because hackers are evil. Everything bad that happens on a computer is the fault of some nameless virus or some computer hacker?

I have to wonder where people come up with that crap. I would say that some //or even most// of the problems that get blamed on a virus or a hacker are because some idiot was using root or admin to do something and screwed up their system.
Hacker doesn't mean evil :p Check my profile out. I am a hacker too :D

---

### Post by bapool on 2008-02-13
It seems to me that there are alot of people on this thread that seem to think logging in as root is a bad idea.  If you actually had more experience with all the Linux distros out there, you would know that the majority of distributions let you logon and use root, with no security problems at all.  The fact that Ubuntu lets the initial setup logon sudu root with the same password doesn't make it any more secure.  If I had your account I could open root in about 2 seconds anyway.  There are very simple reasons to use root and there are no more security risks if you use it correctly.

For the apache2 server that almost never gets logged onto, root might be used for remote access.  If the GUI is off (which we assume is true of any correctly configured server) there are no additional risks (we will also assume we have a appropriate root password.) 

These "attacks" an individuals in this thread are rediculous and are a demonstration of why we have a hard time getting some administrators to come over to Linux.  If they think they will be attacked and bashed for a simple questions, why would they join the Linux community at all?

Should root be used for a system with multiple individuals logging on?  Of course not.  

Is there a problem enabling it for a server that no other accounts exist on and is a web host?  No, especially on a web server.

I personally hate using sudu myself every time I want to do admin stuff, which is the only time my web servers get logged on to.  It was a good question, and luckily someone actually knew the answer.  If you don't, don't bash the person asking.  If you have good advice (and actualy reasons behind it) give it in a way that is constructive.  You lose any credibility by just saying "don't be stupid newbie." 

That is about as nice as I can say it.   Play nice or get out of the sandbox.

---

### Post by martin0641 on 2008-02-26
So I read all the posts here and still dont see any methods to disable the warning that pops up from the login screen.  I saw the post about commenting out the items in the bash file but that did not affect the login banner.  

Any help in getting rid of this would be helpful, for my purposes there is no choice but to login as root, and that banner is messing up a lot of things in the name of nanny-state daddy-knows-best paranoia.

I dont care if some people managed to install the darn OS without using root, its pretty arrogant and rude to yammer on like an elitist 9 year old instead of answering the question, and I suspect the reason for the lack of actual answers is that people just don't know and would rather come off as if their taking the high road, but its really just sad.

So if anyone can shed some light on this I'd appreciate it, there are different reasons for everything and even if something works in 99.999% of situations there is still 0.001% of the people out there that just need a simple answer with no strings attached.

Thanks in advance.

---

### Post by ByteJuggler on 2008-02-27
> **bapool said:**
> It seems to me that there are alot of people on this thread that seem to think logging in as root is a bad idea. 

No, thats misrepresenting people's position (or at least mine.)  Let me be clear: Logging in as root ocassionally for specific purposes is fine.  Logging in as root _all the time, _is what most people are objecting against.   In the original poster's question, the implication that people seem to be reading into the question is that if he's bothered about a warning then it must be because he's always logging on as root, since if he was only occassionally logging on as root, then presumably he could just ignore the warning and be done with it!  Hence the protestations/warnings.   It's been a tennet of Unix sysadmin security for decades that you just do not use the root account routinely, and the system warning about the dangers of lazy use of the root account is therefore a small inconvenience to help remind end-users coming from Windows who may not realise this difference in security policy.  By lazily generally using root as a normal user account, you're in effect opening the same attack vector (i.e. the logged on user's processes) to potential intruders, malicious scripts, etc which is exactly what you have on Windows, and that Microsoft is now trying to fix in various less than successful ways on Windows Vista.

Aslo: Let me be clear, I don't know how to disable the warning.  This is because it's not something that I've ever wanted to do in 15+ years of dealing with Unix and Linux systems (except when I was also a complete neophyte to Linux, about 15 years ago, at which point the system administrator sharply chastised me for logging on as root all the time and asked my why I really wanted to log on as root etc. etc.)  Since then, I've virtually never seen a valid reason for logging on as root _all the time_.  So, in my experience, this type of question usually comes up with new users that want to do this or that, and require root privileges for it.  The solution now, as then, is basically almost never is to give them permanent root access, but instead to set up root access for the task or program they need it for only, and only for as long as required.  So we are not being arrogant in the answers we're giving.  I'm sorry if it appears to you to be that way.  

Finally, with no sarcasm intended, if you really want to do this, you'll probably have to find out where the warning message is actually coming from (which script, or indeed if it's compiled into the X server or gnome or whatever), and then modify/edit the source to get rid of it.  The "beginners forum" then, is probably therefore not the right place to get this question answered.

---

### Post by FrozenFox on 2008-02-27
I don't know about you guys, but if I worked at a bank, I'd leave the vault open all day and just check back on it sometimes for evil-doers. All of those locks and combinations are such a hassle!

:popcorn:

---

### Post by ryanhaigh on 2008-02-27
martin0641  I don't know if it will work but you could try enabling autologin for root in gdm.conf. Of course there are additional security implications for doing this and I'm not sure whether gdm will allow it or still show the warning as I have never done it.

I read all the posts on this thread and can't see any others by you, maybe if you explain what you are doing that needs root access we can help you get around it.

---

### Post by martin0641 on 2008-02-27
A quick look at the responses by the community to this thread will quickly illuminate where the rub is.  Thought ByteJuggler gave a good explanation of why some people might be reluctant to answer the question, the fact remains that information is neutral, its how we wield it that is key.

People read these posts and go off on rants about their philosophies, forgetting that failure is the best teacher.  If so many people believe this is a bad idea, its best to let others find that out the hard way, because experience is a brooding teacher of no reproach, whose learnings cannot be ignored.

No one here knows what people plan to do with this information, many assumptions are made.  What if the information will be used in a LiveCD format where no changes are permanent?  In this scenario, the warning is 100% useless, and thus annoying, and getting rid of it is a valid course of action.  If the plan is to make an ISO of a training environment on short notice, where it might be possible to secure it properly if there was time, but there is no time, so a fast answer is needed. 

What if people want to use KVM software such a Synergy, and though the process is loaded by x11 for the login/password, and later by the Gnome session once login is complete, it is not loaded in the short time after the username/password when this warning pops up, causing the user to be stuck there with no way to click OK and move forward.

There are cases for every scenario.  There are times when men need to know how to make explosives out of their own urine.  Lets not restrict the flow of knowledge based on our preconceived notions, and instead arm each other with the information desired. Give us putty, and see what we make of it, it may be beyond your wildest imaginations, or it may just be a lesson burned into our own minds.  Either way, we all win.

---

### Post by martin0641 on 2008-02-27
Thank you for your interest ryanhaigh,  

It might sound like a cliche, but I really cant go into why I need the information.  I am doing something for my job, and I need to be able to get this done.  Security is a non-issue in my case, in fact security is actually bad in my case.

What I can say is that the fix for Synergy would also be a fix for my problem because they are similar in nature, so if someone can make a process load after the login and before the session, it would suffice for my purposes at this time.

As a bonus "problem" for some intrepid person to explore, what about activating Synergy as a basic process that is enabled even when booting as just a console, and staying loaded through the whole process.  This type of access might also help our dilemma.

I would however like to see a solution for the main topic in general, in the spirit of sharing for all.  Disabling this warning would be a win for free-thinkers libertarian values alike, which in the end are a bonus to all and restrict no one except those who seek to restrict themselves.  I'd rather die learning on my own than go just drinking the Koolaid.

---

### Post by ryanhaigh on 2008-02-27
[This thread]("http://ubuntuforums.org/showthread.php?t=267051") discusses how to start the onscreen keyboard orca when gdm starts, perhaps it could be modified to start synergy.

You might also see if you can find a thread on logging in without a login manager like gdm/kdm/xdm or seeing if any of these can be configured to allow root login without the warning.

---

### Post by asmoore82 on 2008-02-27
> **hashaam83 said:**
> I know it poses a security risk but I am sick of entering my password for any application I run and any command I execute at the terminal.

So, any ideas how to disable the warning?

Hashaam

you still should **[SIZE="2"][COLOR="Red"]NEVER[/COLOR][/SIZE]** log in to a full desktop session as root;
Enormous, Egregious security risks aside, dozens of everyday applications c*hange their behavior* when run as root.

the semi-proper way to do what you want is to allow your user account to use sudo without having to provide a password:
Open a terminal and run ```
sudo visudo
```
move the cursor down to this line: ```
# %sudo ALL=NOPASSWD: ALL
```
the cursor should be blinking over the '#'; press DELETE twice.
Hold CONTROL and Press X.
It will prompt you to save the changes; press Y.
It will show you the filename "/etc/sudoers.tmp; press BACKSPACE four times and press ENTER.
It will warn you that you will overwrite the file; press Y.
It will say "visudo: sudoers file unchanged" because you only uncommented a pre-existing option.

Now, you need to add your user account to the "sudo" group:
```
sudo gpasswd -a *<your_username>* sudo
```

And that is ALL; your GNU/Linux system now has 1 foot in the grave.

what were you doing that required you to enter your password so often that you tired of it?

EDIT: I thought this was a new thread and that I was an early response to the OP.
:lolflag:

---

### Post by mikewhatever on 2008-02-27
> **JBAlaska said:**
> While I do agree with the concept of using Ubuntu as a non privileged user, calling someone "stupid and irresponsible" is counter to the spirit of Ubuntu and these fine forums imho.

In my country (US) there is a alarming trend to protect people from them selfs, the government seems to believe that everyone is a ignorant moron and needs a warning label or law for everything from "the coffee in this cup is hot and will burn you" to "Clairol Hair Coloring: Do not use as an ice cream topping" <--Real
If you treat everyone as a moron, soon you will have a whole generation of moron's...erm..wait..to late lol.

But I digress, If a person wants to run his/her computer as root and understands and excepts the security implications, so be it. Telling users that they are stupid or that their computer will self destruct if run as root is not the way to educate them on the security advantages of running with reduced privileges.

You digressed indeed. What does running as root have to do with your country's government or a generation of morons? Do you believe US citizens are the only users of Linux? Running as root is dump and irresponsible. It opens up one's computer to attacks and malware, thus helping to infect others. This is a bitter legacy imposed by Microsoft after 15 years of market domination. It looms in a distant future, but, sooner or later, Linux will loose most of its security, once hard core Windows users start switching over, bring in their perverted practices. At least, I do not have to help the idiots.

---

### Post by martin0641 on 2008-02-29
The system wont let you set an auto login for root, once again it gives  warning about the devastation effects of running as root, I am beginning to think it will make my palms grow hair and make me go blind.

I'm going to try some of things suggested here to get around it.

Once again, if your just going to make some ignorant post about your personal opinion without attempting to figure out a solution, do everyone a favor and save the 1's and 0's for some other flame war, we don't want the internet filling up with posturing and elitism, cause that would be annoying.

---

### Post by ryanhaigh on 2008-02-29
Did you get te error when trying to set the autologin via the GUI under system>administration? If so you might want to try editing the file /etc/gdm/gdm.conf-custom using /etc/gdm/gdm.conf as a basis. You will want to add the following
```

[daemon]
# Automatic login, if true the first attached screen will $
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=true
AutomaticLogin=root

```

The daemon section header may already be there so just put the rest under that.

---

### Post by Soarer on 2008-03-01
> **martin0641 said:**
> 

Once again, if your just going to make some ignorant post about your personal opinion without attempting to figure out a solution, do everyone a favor and save the 1's and 0's for some other flame war, we don't want the internet filling up with posturing and elitism, cause that would be annoying.

Once again, this is a free forum and people can post whatever they like within the rules without needing permission from you.

You may not like the advice, and you are free to ignore it, but other people are free to offer it. I personally prefer if people pointed out dangers to me before I took a course of action which would be detrimental. I would also stop people putting their fingers in electric sockets if I saw them going to do that.

So I guess by your definition I am ignorant, posturing, elitist and annoying. I can live with that.

---

### Post by ByteJuggler on 2008-03-01
> **martin0641 said:**
> A quick look at the responses by the community to this thread will quickly illuminate where the rub is.  Thought ByteJuggler gave a good explanation of why some people might be reluctant to answer the question, the fact remains that information is neutral, its how we wield it that is key.

People read these posts and go off on rants about their philosophies, forgetting that failure is the best teacher.  If so many people believe this is a bad idea, its best to let others find that out the hard way, because experience is a brooding teacher of no reproach, whose learnings cannot be ignored.

No one here knows what people plan to do with this information, many assumptions are made.  What if the information will be used in a LiveCD format where no changes are permanent?  In this scenario, the warning is 100% useless, and thus annoying, and getting rid of it is a valid course of action.  If the plan is to make an ISO of a training environment on short notice, where it might be possible to secure it properly if there was time, but there is no time, so a fast answer is needed. 

What if people want to use KVM software such a Synergy, and though the process is loaded by x11 for the login/password, and later by the Gnome session once login is complete, it is not loaded in the short time after the username/password when this warning pops up, causing the user to be stuck there with no way to click OK and move forward.

There are cases for every scenario.  There are times when men need to know how to make explosives out of their own urine.  Lets not restrict the flow of knowledge based on our preconceived notions, and instead arm each other with the information desired. Give us putty, and see what we make of it, it may be beyond your wildest imaginations, or it may just be a lesson burned into our own minds.  Either way, we all win.

On the contrary, the information in this case is not neutral, as many years of experience (even if not your own) shows.  

Thank you for giving us an understanding of the real problem by mentioning the startup process and Synergy.  That is helpful. (If I may say so, all the philosophical pontification is less so and most of the scenario's you sketch have no requirement that requires logging in as root, never mind removing a warning on logon, which is the issue at hand here.)

In my experience this type of exchange where the asker assumes he knows how to solve his problem and then asks a detail type question about how to go about effecting one or more of the  steps of what he thinks is the solution, is very common on programming forums by newbie programmers.  Usually in such cases, it turns out that the question being asked is the wrong question as there are problems with the underlying assumptions and/or solution they came up with, and it usually then (as I suspect now)  is neccesary to understand the underlying problem being solved in order to give them truly appropriate advice.    I strongly get the sense this is going on here. 

For the record: I'm also finding your insinuations that all the opinions here are somehow ignorant and only personal opinions rather offensive.  For some of the questions and some of the opinions expressed in response on this beginners forum that may be true, but  I've already explained to you that this particular opinion is far from just someone's pet holy cow.  If you cannot be polite to the people you're requesting help from, respect their experience and knowledge, and are going to continue making veiled insults, then please go somewhere else.  This is a free community forum and the least you can do is respect the effort we're all making to actually respond to you by being polite, even if you think you somehow know better or don't agree with the answers.  And I find the implicit comparison with the Jonestown tradgedy and implied cultish behaviour doubly offensive.  Please cease these types of insinuations at once.

Furthermore, contrary to what many people seem to think these days, many things in life are in fact not a matter of personal opinion.  1+1 equals 2 no matter what anyone's personal opinion about 1+1 is. Some things are actually only learned through hard-earned experience of many years and thus it is not practical, possible or a good idea to learn everything in life through personal experience, as appealing and "free" as that idea may seem, not least due to the danger involved or the time or cost implications or whatever.  "Those who fail to learn from history are doomed to repeat it" and all that.   I might personally for example consider it a good idea to have the freedom to drive on the right hand side of the road and ignore the opinion of all those "self-limiting" drivers who seek to limit themselves by driving only on the left side of the road (here in the UK), but we both know that having me unilaterally deciding to appropriate that so called "freedom" (driving on the right side of the road) would likely only result in an accident with attendant injury and/or death of myself and probably other innocents.  True freedom in this case requires everyone being able to use the public road system without fear of injury or death, and that is only possible if everyone using the road system actually abides by the rules of the road.  If everyone just did what they wanted on the public roads in the name of freedom you would have very many more injuries and deaths as a result.  Or I might consider all these people who believe that the Inland Taipan is a deadly poisenous snake  to be ignorant, and think it's a good idea to experience its  bite myself and learn the lesson myself.  Anybody who acts on such a belief would be extremely lucky to get away alive as a single bite from that snake is enough to kill up to 100 people.  True freedom in this case is to go about my business, taking on board other's knowledge and experience, and avoiding bites by this snake.  (And yes I know these analogies may not be perfect, no analogy is,  I'm just making the point that sometimes true freedom lies in abiding by rules or take on board knowledge/experience gained by others.)  

Anyway, getting back on topic: Re modifying the startup process (implied question in your comment about Synergy), something that I can help with, see the following document for background:
[https://help.ubuntu.com/community/CustomXSession](https://help.ubuntu.com/community/CustomXSession)

I think that documentation might be slightly out of date however (having skimmed it quickly) at least for Gutsy.  The below steps should however suffice: 

1.) Enable root login from console, go System->Administration->Security, tick "Allow local system administrator login"  (I think you've already done this.) On general tab, tick "Default session" and select "Run XClient script" if its not already like that.
2.) Create a file in your home folder called .xsession (press alt-f2, and type "gedit ~/.xsession" and press enter.) Paste into it:
```
#!/usr/bin/env bash

/usr/bin/xterm &
exec gnome-session

```
3.) Make the file executable. (Open a terminal and enter at the prompt: "chmod u+x ~/.xsession", or use the explorer to change the permissions.)
4.) Log out and on the login screen click "Session" and make sure "Run XClient script" is selected
5.) Log in, and you should see an extra xterm start before gnome, when you log in.  That is due to the /usr/bin/xterm & line in the .xsession script. You can obviously edit this script to start whatever the heck you like, including starting synergy or anything else.

I honestly hope that helps you get around your problem.

Finally I've [googled]("http://www.google.co.uk/search?hl=en&q=%22running+a+session+as+a+privileged+user%22&btnG=Search&meta=")  part of the error message, it is clearly part of Gnome.  If you're therefore still hell bent on removing the message, I suggest you take this question to the Gnome developers list, as you'll need to modify and recompile part of gnome to remove the message.

---

### Post by ByteJuggler on 2008-03-01
> **martin0641 said:**
> 
As a bonus "problem" for some intrepid person to explore, what about activating Synergy as a basic process that is enabled even when booting as just a console, and staying loaded through the whole process.  This type of access might also help our dilemma.


It is fairly easy to make anything start during bootup (as opposed to user login), by putting a startup script in the  /etc/init.d/  folder and then linking it to the appropriate runlevel folder (/etc/rc2.d normally for runlevel 2).  Best is to view some of the scripts in /etc/init.d and see how they look.  If you'd like to investigate this option further, post back and I'll try to give you a simple skeleton startup script and instructions for linking into /etc/init.d and /etc/rc2.d

---

### Post by xrxca on 2008-03-03
There is NO reasonable way to disable this message.  

You could change the source (the check is hard coded) and recompile, or drop gnome.

I dont think kubuntu has the warning, and I know xubuntu doesn't (it's on one of our machines that had to have X in order to install a proprietary app, but X as never been needed since (a lot of pointless overhead for an install program))

---

### Post by aysiu on 2008-03-04
It's been almost 4 months with no answer, and most of the posts are just discussing the pros and cons of logging in as root, so I'm plopping this in Recurring Discussions.

As xrxca proposes, I suspect too that disabling the message would require recompiling Gnome. It is not a simple parameter in a text configuration file you can change.

---

### Post by martin0642 on 2008-09-27
Sorry about the wait.  I'm patient that way.

I'm going to address this mess one by one, to keep it simple.

For the Record:  I appreciate the information provided, but my using examples of problems I have seen is not tantamount to those being the problems I have, assumptions to that effect are of your own creation, not mine.

#1  Information is always neutral, no matter what.  There is no exception to this, ask anyone of import, and you'll quickly be informed that it's the context of how the information is used that matters.

#2  I'm not interested in your concept of respect.  I don't care what you think people should or should not do, this is a simple question, and if you don't want to answer it, bugger off.  Attempting to apply your culturally-relavent idea of what is or is not "respectful" is a waste of everyones time.  Most answers on this and other boards are full of people who think having the answer to a question makes them special:  it does not.  The amount of beans by your name is not indicative of anything special.  If I don't want to follow your personal definition of polite, I wont, nor should anyone else.  That's called facism in case you werent aware.  BTW:  I also don't care about your opinions on my use of the term "facism", for the record.

#3  I agree, many things arent personal preferences, this is something I try to get people to understand all the time.  This is not one of those cases.  We arent talking about someone who believes in lord baby jesus, we are talking about disabling a warning message.  We also arent talking about people eating rat poison.  We are talking about a warning message and basic admistration.  IT is often best conveyed by experience, and if people fail, thats what they get for taking on more than they can chew.

So if I offend, please get over it, the constant babyification of the civilized world is something that bothers me on a daily basis, and will be corrected once the radical groups of the world push us into a corner.  I'm a libertarian, so if your wondering why I object to your desire to apply your standards to me, it's a matter of principal.

So thank you for the information, I have recompiled Gnome, and have no more annoying message on my LiveCD which I use in much the same manner as Backtrack.  Please take note that, as I have said, freedom means free.  It means free to mess up, it means free to make bad decisions.  If you dissagree, then you arent getting the point and maybe you would prefer north korea where you can tell everyone what is best for them.  Freedom is not related to your personal views on best practices.  If you have a solution, I suggest you give the answer if you choose, and along side it give the *preferred* method of accomplishing that goal.  That's why it's called OPEN SOURCE.

I wish more people had to fight for their freedom, as I have, so they would have a better concept of what FREE means.  This is why I reject your *opinion* no matter how innocently it may have been intended.

Peace

---

### Post by kiwi-pete on 2008-09-30
> **ByteJuggler said:**
> 
1.) Enable root login from console, go System->Administration->Security, tick "Allow local system administrator login"  

Excuse me for butting in here, I have just done a fresh install on my Laptop and the Security menu is missing from System Admin.
Is there a reason for this?

---

### Post by smartboyathome on 2008-09-30
> **kiwi-pete said:**
> Excuse me for butting in here, I have just done a fresh install on my Laptop and the Security menu is missing from System Admin.
Is there a reason for this?

I think it is because Ubuntu supports sudo, not root login (which is what su does). If they enabled this, then they would have to deal with "Why can't I log in as root?" and "I enabled root login, but I don't know the password!", as the root password is not set.

---

### Post by aysiu on 2008-09-30
I've never heard of the Laptop and Security menu.

---

### Post by kiwi-pete on 2008-09-30
Thats odd, last time I installed Ubuntu on my Laptop, I had all sorts of privileges as administrator etc in the drop down menus. Seems for some reason this time some are missing.

---

### Post by jcrout on 2009-05-18
I was surprised by this thread.  The initial complaint (about disabling a warning message) reminded me about how I felt when I started managing RedHat builds.  I'd learned Linux on Red Hat then switched to Debian because I found the RedHat distro to be too similar to Windows.  (Support questions were always answered with a "fix" that involved a GUI, but it was the GUI that was always broken.)  So I've run Debian for more than 6 years.  

You want freedom? Just switch to Debian.  Run your own compilations for a few things.  Try Slackware or Linux From Scratch anddo a s custom compile everything.  

Remember that Ubuntu is Linux but Linux isn't Ubuntu.

Mac OSX is not "secure".  In fact, it is far less secure than Ubuntu, Debian, Red Hat, or any derivatives.  On my desk is a G4 running Panther.  (Version 10.something.something).  This belongs to a friend. I'm doing an ugrade for her.  I was stunned when I could execute this: "sudo su -" and become root. (UID=0).  (It is also slow but this may be a RAM issue).  CLI isn't bad.

In Debian, I can't become root without root password unless, as root, I've done something to undermine the base OS.

Debian has a live CD, now. The new Knoppix builds -- 5.3.1, and 6.x -- are fun to play wiith.  Adriane is especially interesting.

About the warning message:  As a rule, disabling a warning message is fine, but only if you know more about the OS than the folks who maintain it.  Only then.  If I think it is safe to disable a warning without being this certain, I know I don't know what I need to know, about the warning.  That's just me.

For what it is worth.

):P

---

### Post by sunshine77 on 2009-05-26
> **ByteJuggler said:**
> It is fairly easy to make anything start during bootup (as opposed to user login), by putting a startup script in the  /etc/init.d/  folder and then linking it to the appropriate runlevel folder (/etc/rc2.d normally for runlevel 2).  Best is to view some of the scripts in /etc/init.d and see how they look.  If you'd like to investigate this option further, post back and I'll try to give you a simple skeleton startup script and instructions for linking into /etc/init.d and /etc/rc2.d

Hi, 
actually i am also searching for how to autologin but not for Root just for normal user that come from LDAP authentication. Which part in ubuntu intrepid 8.10 should i start ?
i have already try "mingetty" for autologin user, it works. But for change to user that can come from any authentication server is very hard. 
If anyone have any ideas? 

Thanks a lot.

---

### Post by kiwi-pete on 2009-05-26
> **sunshine77 said:**
> Hi, 
actually i am also searching for how to autologin but not for Root just for normal user that come from LDAP authentication. Which part in ubuntu intrepid 8.10 should i start ?
i have already try "mingetty" for autologin user, it works. But for change to user that can come from any authentication server is very hard. 
If anyone have any ideas? 

Thanks a lot.

System; Administration; Login Window; Security; Tick the box "Enable Automatic Login"; Select User from the drop down box

---

### Post by sunshine77 on 2009-05-26
*System; Administration; Login Window; Security; Tick the box "Enable Automatic  Login"; Select User from the drop down box*


Thanks for reply, 

Actually i have already know how to enable autologin from the GUI.
But what i meant here is, i want to configure the "Select user from the drop down box".
I want to grab the "user" from other file/configuration. Do i need to recompile the Desktop(GDM/KDM) or 
i just can tweak the /etc/event.d/tty1 file or
i need to do something with the /etc/rc2.d ?
my initial objective is only to get autologin from console (without XDM/GDM/KDM)

What i have tried now are:
1. autologin user from console only that without (XDM/KDM/GDM).
but the problem i am facing right now when i want to integrate with my "identified user" (not the default user in the /etc/passwd ) my autologin failed.The normal login console appear.

Currently i am using ubuntu 8.10 intrepid.

my last line /etc/event.d/tty1 file as below:

respawn
exec /sbin/getty /sbin/autologin tty1


my autologin file, test.c

main()
{
     execlp("login","login","-f","username",0);
}

# i took this autologin script from other's website .


Thanks.

---

