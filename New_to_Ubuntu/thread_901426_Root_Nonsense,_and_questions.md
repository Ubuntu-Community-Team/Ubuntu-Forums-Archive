---
title: "Root Nonsense, and questions"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Nahalmmv on 2008-08-26
Hullo,

I came here when Ubuntu 7.something was coming out, and it didn't work with my ATI driver, so I gave up on linux for a while because the other distros wouldn't work either.

Welp with Ubuntu 8.1, things are exciting. I finally have a distro I can use on my laptops and computers. Only thing is I am a solid nubsauce newbie when it comes to 99% of all things linux.

I come from a long line of dying OSs (from win3.1 to more recently Vista), and I'm used to being able to easily make my login account the same as the administrator account. Welp in Ubuntu, it doesn't let me do that when I install, and when I try to access the root from the login window (by typing "root" as username) it won't let me. How do I make the root my login account, because I am tired of working from the admin account and being limited in some aspects. I mean, the beauty of linux that I have found thus far is that it's so small and easy to just reinstall, that if I mess something up.. well just throw it back on (it's even easier with my HD image program, which lets me take a snapshot of my HD right after installing the OS, so if I mess something up I can just apply the already installed image to the HD).

I just want total control of my linux OS, not secondary in which I have to constantly enable groups for the administration account when I want to burp or fart in the settings department.

Also, what's up with the vista-esque verification junk? Like when I want to do something on administrator account, it pops up a little box that asks me to verify my password to continue, while as vista just has the click box. While both are annoying for someone not seeking that level of security, linux is more annoying because I have to retype my password over and over again. How do I turn this off?

One last thing. I tried to connect to my university's wireless, and it was going well till I tried to mess with the wireless network log on settings. The WPA1 and WPA2 sheet doesn't have an option for "Username" it just has "Password". And my university's login system requires a username (student name) and a password (6 digit number) in order to log in. I would like to use my laptop to take notes because vista drains too much battery power.

I guess one more question... lol. How do you extend battery life for laptops. I worked with power settings, and it seemed to do well, but is there processor settings for when idle, or hard drive settings when idle... 

One more sorry (just excited), is there a way to run the OS in ram like DSL lets you? I have buckets of ram, and the regular Ubuntu mode (from hard drive) doesn't even touch 1% ram usage. (something ELSE I LOVE about linux)

Any help would be much appreciated, and I'll be checking back here on this thread frequently. I would like to switch over family members OSs to linux as well, using virtual box only to run windows on a virtual HD for windows only stuff. They've all used my laptop for websurfing, and with swiftfox, they love the ultra fast speed that "SLOTHernet Explorer" could never match.

Plus all the girls love the ubuntu Worm game. (surprisingly, so do many of the girls in my university I sit by in class lol) :rolleyes:

Thanks again.

PEACE

---

### Post by barbedsaber on 2008-08-26
I think this will answer some of your questions.
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
(psst, not being r00t = good :))
edit: maybe not what you were looking for, I will keep looking

> doing daily work as the superuser can be dangerous. You could type a command incorrectly and destroy the system. Ideally, you run as a user that has only the privileges needed for the task at hand. In some cases, this is necessarily root, but most of the time it is a regular user.


I can't find the thing I was looking for, but basically, it explains that not running as root (administator, has a load pf security advantages, for example, a program can't run loose, and destry everything, because it is not run with administrative privileges. (you can format your C drive in windows, no questions asked, and generally, that is a baaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaad thing.) It is in fact forum policy, to not tell people how to log in as, or be root user. it keeps you safe,
its for your own good.
every time you log in as root, god kills a kitten.
please, think of the kittens.

\/ \/ lolcat agrees with me \/ \/

---

### Post by Nythain on 2008-08-26
ok, though this is strongly ill-advised, to enable root account
sudo passwd root

but, before doing that, please consider the alternative of adding your account to the sudoers file and making it so you dont need a password to do sudo stuff
> 
Just incase any other morons like myself find this thread in their attempt to edit their sudoers, here are some tips that would have saved me some time...

1) add to the bottom of the file as the last entry has the highest priority
2) even if you add NOPASSWD, when you ultimately run these commands, you still have to add the sudo prefix (it just wont ask you for a password obviously)
3) no need to faff around with creating groups; this is what ultimately worked for my needs:
jack ALL=(ALL) NOPASSWD: /usr/sbin/pm-suspend, /sbin/shutdown

Hope this helps someone,
Jack

EDIT: another great tip was to avoid using that horrifying editor vi:
add to bottom of ~/.bashrc
export EDITOR=vim
then log out and back in again
then edit sudoers with -E flag:
sudo -E visudo

while still not the most advised solution, you still keep the security of not having a root account. No root account is secure for many reasons, the best being, without a "root" account, its that much harder for someone to break into your computer, because now, they have to figure out your exact username and password, instead of already knowing the username "root"
It will also still keep you safe from fubaring your system because aything that needs root access will still require the "sudo" so you know if you are about to do something potentially dangerous to your own system.

---

### Post by arpanaut on 2008-08-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[COLOR="RoyalBlue"]Purely a Personal Opinion![/COLOR]

If Ubuntu's Security model, and usage scheme don't suit your needs maybe you should look elsewhere.

If you do not understand WHY the Ubuntu developers set things up this way, MAYBE you shouldn't be using a "internet connected" computer at all.

The way of the future will be more username & password prompts: Get Used to It! 
It's for everyone's well being.

[COLOR="Blue"]End of Personal Opinion[/COLOR]

P.S.  Good Luck with the girls at the University!  LOL

---

### Post by nicedude on 2008-08-26
I agree with [arpanaut]("http://ubuntuforums.org/member.php?u=45953") . Ubuntu is one of the most secured OS's in play right now. And although I am a linux noob I am not a computer noob. Now if you think XP or Vista is secure you are delusional as anyone with a live boot CD can either change your admin password to one they want or steal your microsoft encrypted password file and crack it later with a rainbow table in a couple of minutes ( nice what things are considered encrypted by MS, thank god banks don't protect your money in such a shoddy fashion or we would all be flat broke ). So in general Ubuntu is much harder for an intruder ( either physically at your PC or across the Internet ) to attack and penetrate it successfully. In fact you would literally have to get some source code from them and then install it ( which takes root pass ) or pick a password like "password" for a VNC server or Samba share etc. So just use your Ubuntu and be happy in trusting us nice folks or go back to Windows and trust bill gates ( I won't even trust him as far as I can throw him, cause I can probably throw him 5 feet and that is way too much trust for him :-) )

---

### Post by Nepherte on 2008-08-26
> **Nythain said:**
> ok, though this is strongly ill-advised, to enable root account
sudo passwd root

As Nythain alraedy suggested, just forget about that command and try to learn sudo. **I strongly recommend not to login as root**. Although logging in with root doesn't necessarily mean it will harm your system (a few other distributions have it enabled as well, freedom of choice remember), it assists you in not messing up your system. It's just how ubuntu works. Information can be found here: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by gidi75 on 2008-08-26
pues si hombre como lo hago estoy en problemas porque tengo varios pcs con mouse serial y no he podido configurarlo para trabajar con ubuntu   please help S.O.S   etc

---

### Post by drubin on 2008-08-26
> **Nahalmmv said:**
> Plus all the girls love the ubuntu Worm game. (surprisingly, so do many of the girls in my university I sit by in class lol)

LOL

I also used to get anoyed by it, coming from other os's. But I have since enabled sudo on my CentOs servers.

---

### Post by Nahalmmv on 2008-08-26
Thx so much for the replies so far.

It isn't that I don't appreciate the added security or anything, I learned about the added security box from when Vista came out, and I understand why it's there. It's just, some basic options in ubuntu, or rather basic things to edit, seem to be a part of the security thing. Oh well, I'll look up the options posted above for making it to where I don't destroy... um... stuff? Lol, yet maintain freedom from that phantom menace.

One other thing. Why in the world did the developers make some of the games on ubuntu so freakin impossible to beat. Like the classical "four across" game. I mean lvl 1 has thus far handed me my manhood in a paper bag 14 out of the 14 times I have challenged it. No one else in my family has been able to beat level one either, and we play the game on a regular basis with one another (we all drive a coupla hours to a meeting house and play board games and watch movies and stuff to keep family relationships tight).

Lol thanks again.

PEACE

---

### Post by drubin on 2008-08-26
> **Nahalmmv said:**
> ... Why in the world did the developers make some of the games on ubuntu so freakin impossible to beat. Like the classical "four across" game. I mean lvl 1 has thus far handed me my manhood in a paper bag 14 out of the 14 times I have challenged it. No one else in my family has been able to beat level one either...

Simple answer because they can, They wanted to make it so that you have to come back and play more, "must have more".

If you beat them first time you would never come back would you?

---

### Post by Nahalmmv on 2008-08-26
> **rubinboy said:**
> Simple answer because they can, They wanted to make it so that you have to come back and play more, "must have more".

If you beat them first time you would never come back would you?

If some big bully in school beats me up on a regular basis... I'll just go cry in a corner somewhere, not challenge him to an Ultimate Fighting Championship :lolflag:

Maybe make level 1 moderate so that people can beat it, and get their foot in the door. Sometimes all people need is a little taste of victory to get hooked.


Peace

---

### Post by kdorf on 2008-08-26
> **Nahalmmv said:**
> If some big bully in school beats me up on a regular basis... I'll just go cry in a corner somewhere, not challenge him to an Ultimate Fighting Championship :lolflag:

Maybe make level 1 moderate so that people can beat it, and get their foot in the door. Sometimes all people need is a little taste of victory to get hooked.


Peace

Just hold the down arrow when four across starts. You'll win half the time.

To continue on this topic, logging in as root can be dangerous and is especially so with a GUI. My rule of thumb is if you don't yet know how to enable graphical login of the root account, you probably shouldn't be trying to. It's entirely too easy to destroy your system, and it's downright stupid to do so. Excuse the harsh language.

---

