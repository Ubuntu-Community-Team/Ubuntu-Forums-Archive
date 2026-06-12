---
title: "Social engineering (trojan) via gnome-look.org"
date: 2009-12-08
forum: Recurring Discussions
---

### Post by pbrane on 2009-12-08
> **Enlightened Shadow said:**
> The point is that I was dumb enough to think that Ubuntu was secure enough out here in the Linux wonderland that I love so much that I ended up on gnome-look downloading everything that looked cool without examining everything first.

Ubuntu is secure. We are the ones who make it un-secure by installing something using our root password. I didn't think about the fact that a .deb file from a trusted site would be malicious. Thanks for the lesson.

---

### Post by meho_r on 2009-12-08
> **pbrane said:**
> Ubuntu is secure. We are the ones who make it un-secure by installing something using our root password. I didn't think about the fact that a .deb file from a trusted site would be malicious. Thanks for the lesson.

You consider gnome-look a trusted website? Stick with official repos and PPAs and you'll be fine.

---

### Post by hwttdz on 2009-12-08
Aren't PPA's only as far as you trust the owner, as in anyone can get one.

---

### Post by pbrane on 2009-12-08
> **meho_r said:**
> You consider gnome-look a trusted website? Stick with official repos and PPAs and you'll be fine.
I didn't say I considered it a trusted site. I just meant it is a good idea not to assume it's safe to install debs. I think your advise is good.

---

### Post by MC707 on 2009-12-08
Muahaha could this be the first semi-massive Linux virus/trojan? Either way, I agree with pbrane, even for windows to a certain extent (at least in my PC):
> **pbrane said:**
> Ubuntu is secure. We are the ones who make it un-secure by installing something using our root password. I didn't think about the fact that a .deb file from a trusted site would be malicious. Thanks for the lesson.

---

### Post by NoaHall on 2009-12-08
Read this thread - [http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)

Basically, there's someone who put a .deb on gnome-look, users installed it, and now he's hacked their systems to perform a DDoS attack. 

Lesson : Don't install .deb files from unreliable sources. We have repos for a reason. Use them. And for crying out loud, screensavers don't use .deb files.

Oh, and here's the fix(in case someone browsing might want to check)
```
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash && sudo dpkg -r app5552
```

---

### Post by dragos240 on 2009-12-08
Well crap!

EDIT: It's been removed.

---

### Post by conorsulli on 2009-12-08
> **running_rabbit07 said:**
> This is what this link ([noparse]http://05748.t35.com/[/noparse]) says when opened via FF.

well I dont want a congrats...

Keep viruses in the windows world 

Thank you

---

### Post by doas777 on 2009-12-08
> **conorsulli said:**
> well I dont want a congrats...

Keep viruses in the windows world 

Thank you

just a point of terminology (not trying to be a jerk), but this is not a "virus". viruses spread, and exploit vulns in applications to perform their dirtywork.
what yo have there is a trojan.

sorry, it's jsut that everytime the word "virus" is used on this forum, it gets ugly from there. everyone would alternate between telling you that your issue never happened, or that you are the problem (neither of which is constructive.). i hate those threads...zealots vs zealots

---

### Post by running_rabbit07 on 2009-12-08
> **doas777 said:**
> just a point of terminology (not trying to be a jerk), but this is not a "virus". viruses spread, and exploit vulns in applications to perform their dirtywork.
what yo have there is a trojan.

sorry, it's jsut that everytime the word "virus" is used on this forum, it gets ugly from there. everyone would alternate between telling you that your issue never happened, or that you are the problem (neither of which is constructive.). i hate those threads...zealots vs zealots

Do you think the referenced link could have a negative effect when visited via FF? I've been watching conky since the visit and haven't seen anything new happening, but I am not the brightest at spotting orc mischief in Linux, yet.

---

### Post by NoaHall on 2009-12-08
> **running_rabbit07 said:**
> Do you think the referenced link could have a negative effect when visited via FF? I've been watching conky since the visit and haven't seen anything new happening, but I am not the brightest at spotting orc mischief in Linux, yet.

No, I don't think so. Not unless you're running firefox as root, or something.

---

### Post by running_rabbit07 on 2009-12-08
> **NoaHall said:**
> No, I don't think so. Not unless you're running firefox as root, or something.

 Nope, I know better. I am also running NoScript. And from from looking at NoScript while at the site, there was script there to be run.

---

### Post by conorsulli on 2009-12-08
> **doas777 said:**
> just a point of terminology (not trying to be a jerk), but this is not a "virus". viruses spread, and exploit vulns in applications to perform their dirtywork.
what yo have there is a trojan.

sorry, it's jsut that everytime the word "virus" is used on this forum, it gets ugly from there. everyone would alternate between telling you that your issue never happened, or that you are the problem (neither of which is constructive.). i hate those threads...zealots vs zealots

I get ya, wasn't really thinking but the message still applies... this clown put a lot of users at risk and we still don't know how many people still have this thing on there computers and just forgot about it when it didn't work and we don't know what this Douchebag intends on doing yet...

So this problem is still far from solved,Gnome-look gets many many views per day.........
Notice will probably have to go on to gnome-look

---

### Post by running_rabbit07 on 2009-12-08
> **conorsulli said:**
> I get ya, wasn't really thinking but the message still applies... this clown put a lot of users at risk and we still don't know how many people still have this thing on there computers and just forgot about it when it didn't work and we don't know what this Douchebag intends on doing yet...

So this problem is still far from solved,Gnome-look gets many many views per day.........
Notice will probably have to go on to gnome-look

I hope you weren't calling me a clown for posting the results of going to the site that is in the above mentioned script. I have no intention of messing with anybody's system.

---

### Post by Frak on 2009-12-08
Well, that would be the first largely successful Social Engineering malware attack, now wouldn't it?

---

### Post by bodhi.zazen on 2009-12-08
> **MC707 said:**
> Muahaha could this be the first semi-massive Linux virus/trojan? Either way, I agree with pbrane, even for windows to a certain extent (at least in my PC):

This is an example of what is called "Social Engineering" and social engineering is easier the cracking the OS.

[http://en.wikipedia.org/wiki/Social_engineering_%28security%29](http://en.wikipedia.org/wiki/Social_engineering_%28security%29)

As a general rule, Windows side, be very careful of image files needing to be run as .exe

Linux side, why should a theme be a .deb ? Sure there are valid reasons. Sure there are valid reasons, but you should at least pause.

---

### Post by NoaHall on 2009-12-08
> **Frak said:**
> Well, that would be the first largely successful Social Engineering malware attack, now wouldn't it?

Largely? So far, two known people infected :) Not many. Still, not a good sign.

---

### Post by dragos240 on 2009-12-08
Luckily I don't use screensavers on my servers :)

---

### Post by dragos240 on 2009-12-08
> **NoaHall said:**
> Largely? So far, two known people infected :) Not many. Still, not a good sign.

No, but it's down. The link is down now, so it's safe.

---

### Post by Frak on 2009-12-08
> **NoaHall said:**
> Largely? So far, two known people infected :) Not many. Still, not a good sign.
I know a couple more that don't post on the forums. As big as Gnome-look is, and how crazy people get over screensavers, you can reasonably deduce that there were more people infected.

---

### Post by Tipped OuT on 2009-12-08
Where is Linux's invincible security now?

---

### Post by RiceMonster on 2009-12-08
Proof right here that linux would get viruses if it were popular.

---

### Post by Random-penguin on 2009-12-08
I've been following this post with growing interest. I realize that users should always be wary of installing away from official repositories, but how much are Gnome-look ,etc, responsible for making sure that the software they host is malware free?

Also how can we improve / educate users basic admin responsibilities??

And I guess this answers part of my question:

[http://gnome-look.org/legalnotice/](http://gnome-look.org/legalnotice/)

See I always point out the obvious.....

---

### Post by Frak on 2009-12-08
> **Tipped OuT said:**
> Where is Linux's invincible security now?
Oh, you mean how [LinuxIsMalwareProof&#8482;]("http://www.tmrepository.com/trademarks/linuxismalwareproof/")?

---

### Post by dragos240 on 2009-12-08
> **Tipped OuT said:**
> Where is Linux's invincible security now?

Konata is the security of Linux now.

---

### Post by ibuclaw on 2009-12-08
> **Tipped OuT said:**
> Where is Linux's invincible security now?

1) Security is not invincible (you are going off a false positive here).
2) Security should never mean: prevent **administrators** from doing something they probably don't want to do - however good the intention.

Giving you administer / root privileges to a machine generally means that we trust that you can use / administer it wisely.
If you don't - then you can't complain/blame the software/OS if bad things happen.

Although we have AppArmor to prevent some instances of damage from occurring, but not all...

---

### Post by Techsnap on 2009-12-08
Just a few days ago I told someone that something like this is completely possible and they completely disagreed as I expected. 

Now look.

At the end of the day it's the usual, it's up to the user to make sure they keep their systems maintained, it's not the OS which is at fault.

---

### Post by Tipped OuT on 2009-12-08
> **dragos240 said:**
> Konata is the security of Linux now.

Oh, well we're screwed.

---

### Post by dragos240 on 2009-12-08
> **Tipped OuT said:**
> Oh, well we're screwed.

Yeah, she'll start to do [this]("http://www.youtube.com/watch?v=ndhzoB6Rt_s") if something happens.

---

### Post by squilookle on 2009-12-08
No system is invincible. 

However, I still think most Linux systems are safer than Windows systems... so long as you don't run untrusted software and don't give root access to anyone that does not know what they're doing, then this is harmless.

---

### Post by Techsnap on 2009-12-08
> However, I still think most Linux systems are safer than Windows systems... so long as you don't run untrusted software and don't give root access to anyone that does not know what they're doing, then this is harmless.

Apply the same theory to Windows.

---

### Post by squilookle on 2009-12-08
Fair point, Techsnap. 

What I mean is, I don't think a Windows system is as easy to secure, and is certainly not secure by default.

---

### Post by hoppipolla on 2009-12-08
I looked at the scripts, what a shame that someone decides to pointlessly damage other Linux users machines - what is their problem?

However, it does show the holes in the existing system. It's a wonderful system, but it does still follow this theory that the root user can do no wrong, which is just incorrect because not all "admins" are that bright!

We need to install packages like this (screensavers etc) for OUR USER ONLY BY DEFAULT, so damage is contained.

---

### Post by Hwæt on 2009-12-08
> **Techsnap said:**
> Apply the same theory to Windows.

Windows is vulnerable to drive-by downloads. All you have to do in Windows is surf the web to get a virus.

---

### Post by ibuclaw on 2009-12-08
> **fatality_uk said:**
> lol - unclean, unclean :D

Wondering how long before this gets slashdot'd or el'reged with a END OF DAYS "Linux Hacked" spin

This is neither end of days - nor Linux being hacked. Think of this as a warning to all **Debian** system users who download and run untrusted files and installers on their production machines.

99% of other Linux users will carry on their everyday life not knowing this ever happened...

> **hoppipolla said:**
> I looked at the scripts, what a shame that someone decides to pointlessly damage other Linux users machines - what is their problem?

However, it does show the holes in the existing system. It's a wonderful system, but it does still follow this theory that the root user can do no wrong, which is just incorrect because not all "admins" are that bright!

We need to install packages like this (screensavers etc) for OUR USER ONLY BY DEFAULT, so damage is contained.
Quite contrary, this is not a hole in the system. This is social engineering applied outside of lab testing.
It is no surprise that people fell for the cookie.

But as much as we teach you not to download anything from untrusted sites - people will fall for the "Linux Security" propaganda and get complacent.

Linux is a strong system **not** because of the system being "built ground up for security", that is but a small piece in the puzzle. Linux is a strong system because it's users are generally "in the know" about threats and prevention.

---

### Post by Frak on 2009-12-08
> **squilookle said:**
> No system is invincible. 

However, I still think most Linux systems are safer than Windows systems... so long as you don't run untrusted software and don't give root access to anyone that does not know what they're doing, then this is harmless.
Same on Windows. Don't run software that you don't trust as administrator.

---

### Post by Frak on 2009-12-08
> **Hwæt said:**
> Windows is vulnerable to drive-by downloads. All you have to do in Windows is surf the web to get a virus.
No.

---

### Post by kk0sse54 on 2009-12-08
> **Techsnap said:**
> Apply the same theory to Windows.

Oh so that's why I got a virus from visiting that one website? And don't even bother trying to tell me that it was porn or a result of my own incompetent safe browsing skills

---

### Post by Hwæt on 2009-12-08
> **Frak said:**
> No.

Tell that to the millions of Windows users who got a virus by looking at porn.

---

### Post by Sealbhach on 2009-12-08
So somebody downloaded a deb and executed it?

I think this vulnerability is already well known.

.

---

### Post by NoaHall on 2009-12-08
> **Sealbhach said:**
> So somebody downloaded a deb and executed it?

I think this vulnerability is already well known.

.

Ah, but someone used the knowledge to cause damage. It could have easily been done before, but it wasn't. This is why it's "shocking" news.

---

### Post by Frak on 2009-12-08
> **C!oud said:**
> Oh so that's why I got a virus from visiting that one website? And don't even bother trying to tell me that it was porn or a result of my own incompetent safe browsing skills
It was both.

---

### Post by Frak on 2009-12-08
> **Hwæt said:**
> Tell that to the millions of Windows users who got a virus by looking at porn.
I look at porn all the time, and my computer's fine. It's like drinking, just because I do it doesn't mean I'll shoot embarrassing photos of myself and post it online.

EDIT
That would make a great scandal...

---

### Post by murderslastcrow on 2009-12-08
Yeah, it still needs your permission to run it manually. It won't do it without your knowledge. This makes it extremely obvious where the problem comes from. Unless one of these packages becomes common in a closed-source package that many people are using, it wouldn't be a big problem.

Just don't install untrusted software, it's as simple as that. If you download and purposely install malware, that's your fault. The whole point is that you can have safe, prepackaged stuff in Add/Remove without having to scour the internet for stuff.

If we're comparing Windows to Linux, the difference here is 1. It needs your permission, and 2. You need to go out of your way to find the unsafe software, as it's highly uncommon that something popular will also be unsafe.

This stuff has happened before. I don't think it's something we have to worry about. The developers have the responsibility to make it safe, and they do a really good job of it. Also, if you release an unsafe package, everyone knows where it came from/who you are. You will be banned or blacklisted if you release an evil package. Also, if there's no source, why should we trust an insignificant package anyway?

I just think people are scared too easily. Security isn't black and white. It's all about the user not being silly and downloading crapware. If Linux were as popular as Windows, you would still have to go out and find this stuff, it wouldn't just hop onto your computer without your permission.

---

### Post by kevCast on 2009-12-08
And this is why I never install .debs from anything that's not in a repo. Much safer to look at the code and compile it.

---

### Post by Techsnap on 2009-12-08
> If we're comparing Windows to Linux, the difference here is 1. It needs your permission, and 2. You need to go out of your way to find the unsafe software, as it's highly uncommon that something popular will also be unsafe.

If you're using UAC in Windows Vista/7 or a User Profile on Windows NT/2K/XP it's going to want your permission.

---

### Post by julianb on 2009-12-08
> Proof right here that linux would get viruses if it were popular.

Writing linux malware is easy, if you can just get someone to run it on his/her computer.

"please run this bash script as root"
... one way or another, you'd better have a reason to trust that bash script.

Or how about

```
sudo apt-get install DeleteMyImportantFilesPlease
sudo apt-get install UseMyComputerToSendSpamPlease
sudo apt-get install PutMyComputerInAbotnetPlease
```

You can't make a system that is immune to these kinds of attacks, just like you can't make a system that completely protects people from the "please execute this code that includes the 'rm' command"  attacks:
[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

### Post by Random-penguin on 2009-12-08
> **tinivole said:**
> 

But as much as we teach you not to download anything from untrusted sites - people will fall for the "Linux Security" propaganda and get complacent.

Linux is a strong system **not** because of the system being "built ground up for security", that is but a small piece in the puzzle. Linux is a strong system because it's users are generally "in the know" about threats and prevention.


Yes this is so true, but we need to (especially in newbie friendly Ubuntu) get that basic knowledge across.... :D

---

### Post by NoaHall on 2009-12-08
If you want to have a completely secure system - here's one fact you won't like. You won't be able to install anything. Think of Chrome OS. They could easily make that very secure, and how? Taking away the users liberty and choosing what software for them.

---

### Post by Techsnap on 2009-12-08
> **NoaHall said:**
> If you want to have a completely secure system - here's one fact you won't like. You won't be able to install anything. Think of Chrome OS. They could easily make that very secure, and how? Taking away the users liberty and choosing what software for them.

Pull the Ethernet cable out, that's the most secure system.

---

### Post by Frak on 2009-12-08
> **murderslastcrow said:**
> I just think people are scared too easily. Security isn't black and white. It's all about the user not being silly and downloading crapware. If Linux were as popular as Windows, you would still have to go out and find this stuff, it wouldn't just hop onto your computer without your permission.

1. Maybe. There's a chance that holes will be found. There aren't enough police for the criminals *if ya know what I mean*.
2. Like Windows, when you throw commercial software into the mix, you get exploits through those. When people are attacked by drive-by-downloads, it's because of vulnerabilities in extensions such as Quicktime/Flash/Java/.NET Extensions/etc. It could even be through the browser itself.

> **Techsnap said:**
> If you're using UAC in Windows Vista/7 or a User Profile on Windows NT/2K/XP it's going to want your permission.

This.

---

### Post by ibuclaw on 2009-12-08
> **Random-penguin said:**
> Yes this is so true, but we need to (especially in newbie friendly Ubuntu) get that basic knowledge across.... :D

We have a "Security Discussions" sub-forum.

Although, no one really ever reads the stickies in there.

[Ubuntu Security. Written by bodhi.zazen]("http://ubuntuforums.org/showthread.php?t=510812")

Regards

---

### Post by NoaHall on 2009-12-08
> **Techsnap said:**
> Pull the Ethernet cable out, that's the most secure system.

Oh yeah? ;) What about user damage? ;) rm -rf etc.

---

### Post by Techsnap on 2009-12-08
> Oh yeah?  What about user damage?  rm -rf etc.

Well how about you just don't turn the system on. Don't connect any cables.. that's ultra secure. Anything else would be hardware related.

---

### Post by Frak on 2009-12-08
> **NoaHall said:**
> Oh yeah? ;) What about user damage? ;) rm -rf etc.
That yields an error if you try it on root. Ubuntu won't let you.

As for the whole security argument, it sounds like a case of [YoudHaveToRunAsRootForItToDoAnyDamage&#8482;]("http://www.tmrepository.com/trademarks/youdhavetorunasrootforittodoanydamage/").

Though, a truly secure system takes no input and yields no output.

---

### Post by NoaHall on 2009-12-08
> **Frak said:**
> That yields an error if you try it on root. Ubuntu won't let you.

As for the whole security argument, it sounds like a case of [YoudHaveToRunAsRootForItToDoAnyDamage™]("http://www.tmrepository.com/trademarks/youdhavetorunasrootforittodoanydamage/").

Though, a truly secure system takes no input and yields no output.

So ? You can still use it on files by accident.
Anyway, you're agreeing with me - the safest system is one where the user can't do anything.

---

### Post by Frak on 2009-12-08
> **NoaHall said:**
> So ? You can still use it on files by accident.
Anyway, you're agreeing with me - the safest system is one where the user can't do anything.
Why do all my responses have to be disagreements?

---

### Post by Techsnap on 2009-12-08
> Why do all my responses have to be disagreements?

Frak, I disagree.

---

### Post by NoaHall on 2009-12-08
> **Frak said:**
> Why do all my responses have to be disagreements?

Because you like to disagree. ;)

---

### Post by Frak on 2009-12-08
> **NoaHall said:**
> Because you like to disagree. ;)
[SIZE="1"][COLOR="White"]i[/COLOR][/SIZE]
> **Techsnap said:**
> Frak, I disagree.

RAWRAWRAWRAWRAWR

True.

---

### Post by Exodist on 2009-12-08
> **RiceMonster said:**
> Proof right here that linux would get viruses if it were popular.
Agreed!

---

### Post by Enlightened Shadow on 2009-12-08
Is it possible or not ever going to happen that in the future their be a program added in with the OS that scans Debian files and looks for scripts and then looks to see if commands like rm and such come up and if so inform the user of the risk these commands. That way at least the user knows that they should take a closer look at the file first?

---

### Post by SunnyRabbiera on 2009-12-08
Well no OS is 100% bulletproof, except maybe BSD.

---

### Post by NoaHall on 2009-12-08
> **SunnyRabbiera said:**
> Well no OS is bulletproof, except maybe BSD.

Great, now you've jinxed it! ;)

---

### Post by SunnyRabbiera on 2009-12-08
> **NoaHall said:**
> Great, now you've jinxed it! ;)

Well issues might come about for BSD too, anything is possible.
But irresponsibility is a leading cause of issues, no OS is safe from the end user.

---

### Post by Frak on 2009-12-08
> **SunnyRabbiera said:**
> Well issues might come about for BSD too, anything is possible.
But irresponsibility is a leading cause of issues, no OS is safe from the end user.
0110101010010101010101000
[COLOR="White"]000000000[/COLOR]^

That one is the bug in BSD. Massive.

---

### Post by koenn on 2009-12-08
> **Enlightened Shadow said:**
> Is it possible or not ever going to happen that in the future their be a program added in with the OS that scans Debian files and looks for scripts and then looks to see if commands like rm and such come up and if so inform the user of the risk these commands. That way at least the user knows that they should take a closer look at the file first?
even legit postinst and preinst scripts could do an 'rm' to clean out an old version before installing a new one, or delete temporary files, or so.
So that's going to be hard.
And you'd have to scan for anything that could be potentially harmfull - which is probably half of all the commands available in and to shell. 
I don't think you're going to want to confirm all that manually when you're installing a system.

---

### Post by lisati on 2009-12-08
> **Hwæt said:**
> Tell that to the millions of Windows users who got a virus by looking at porn.
Um er, I better keep the (imaginary) collection of "naughty" magazines away from my Windows machines!
> **Techsnap said:**
> Pull the Ethernet cable out, that's the most secure system.

With WiFi and power switched off as well.

---

### Post by user1397 on 2009-12-08
How about GNU/Hurd...isn't that pretty secure as its user base is like 5 people around the world? (yes an exaggeration, but not by much :)

---

### Post by Frak on 2009-12-08
> **ubuntuman001 said:**
> How about GNU/Hurd...isn't that pretty secure as its user base is like 5 people around the world? (yes an exaggeration, but not by much :)
Security Through Obscurity

---

### Post by conorsulli on 2009-12-08
> **Enlightened Shadow said:**
> Is it possible or not ever going to happen that in the future their be a program added in with the OS that scans Debian files and looks for scripts and then looks to see if commands like rm and such come up and if so inform the user of the risk these commands. That way at least the user knows that they should take a closer look at the file first?

Good suggestion, Could open this topic on ubuntu brainstorm!!

---

### Post by NoaHall on 2009-12-08
> **Frak said:**
> 0110101010010101010101000
[COLOR="White"]000000000[/COLOR]^

That one is the bug in BSD. Massive.

Nice one, I'll get fixing it right now ;) Hehe.

---

### Post by starcannon on 2009-12-08
> **Enlightened Shadow said:**
> The point is that I was dumb enough to think that Ubuntu was secure enough out here in the Linux wonderland that I love so much that I ended up on gnome-look downloading everything that looked cool without examining everything first.

With that reasoning, one could allow armed robbers into his vault; its  secure right? So nothing to fear from armed robbers, right? 

If you download, and run, give the admin password, any .deb; then you get what you were given.

Know your source before using the software.
Socially engineered viruses can only ever be stopped with education. Consider yourself schooled.

I would suggest we all report the guy who wrote that script, to his web host as well:
[http://www.t35.com/](http://www.t35.com/)

---

### Post by Enlightened Shadow on 2009-12-08
> **koenn said:**
> even legit postinst and preinst scripts could do an 'rm' to clean out an old version before installing a new one, or delete temporary files, or so.
So that's going to be hard.
And you'd have to scan for anything that could be potentially harmfull - which is probably half of all the commands available in and to shell. 
I don't think you're going to want to confirm all that manually when you're installing a system.

Yeah your right. Oh well I am going to have to be a whole lot more careful. It is sad to know that people still try to attack others even here in Linux. That is probably the one big reason that I left Winblows. I'm just glad that it wasn't anything that bad and didn't cause any damage to my machine. It sure opened my eyes though. The best thing about Linux is this right here. The fact that at least 80% of Linux users are people who are very good with computers such as programmers and not the general public.

Cheers everyone.

---

### Post by fatality_uk on 2009-12-08
> **SunnyRabbiera said:**
> Well no OS is 100% bulletproof, except maybe BSD.

I seem to remember my Oric 1 NEVER getting a virus, or ever hearing about ANYONE ever getting a virus, malware, trojan etc :D

---

### Post by Frak on 2009-12-08
> **fatality_uk said:**
> I seem to remember my Oric 1 NEVER getting a virus, or ever hearing about ANYONE ever getting a virus, malware, trojan etc :D
My pet rock never got a virus. He did pee on the carpet, though...

---

### Post by lisati on 2009-12-08
> **Frak said:**
> My pet rock never got a virus. He did pee on the carpet, though...

Sounds inconvenient. :)

---

### Post by fatality_uk on 2009-12-08
> **Frak said:**
> My pet rock never got a virus. He did pee on the carpet, though...

Bad rock, baaad rock!

---

### Post by pwnst*r on 2009-12-08
> **Tipped OuT said:**
> Where is Linux's invincible security now?

lol, so true.

---

### Post by pwnst*r on 2009-12-08
> **Techsnap said:**
> Pull the Ethernet cable out, that's the most secure system.

actually, pulling the power cord is the most secure system.

---

### Post by julianb on 2009-12-08
> If you want to have a completely secure system - here's one fact you won't like. You won't be able to install anything. Think of Chrome OS. They could easily make that very secure, and how? Taking away the users liberty and choosing what software for them.

There are gonna be people who "hack" chrome OS to run whatever apps they feel like on it. And that will be insecure. Kind of like if you run un-trusted software on your iPhone.

---

### Post by Simian Man on 2009-12-08
This thread reads like IRC.

I've said it a hundred times.  Security is almost totally about the user.  When people who get viruses on Windows begin running Linux, they will get viruses there too.

---

### Post by scouser73 on 2009-12-08
Off topic slightly, but this is the first time I've ever heard of anything malicious in Ubuntu, hell even in Linux.

---

### Post by The_Pirate_King on 2009-12-08
> **Frak said:**
> 0110101010010101010101000
[COLOR=White]000000000[/COLOR]^

That one is the bug in BSD. Massive.
I can tell by some of the pixels and having seen quite a few octets in my day.

---

### Post by Tipped OuT on 2009-12-08
> **pwnst*r said:**
> actually, pulling the power cord is the most secure system.

Actually, pulling the power cord, and locking it up in an highly encrypted fireproof, bulletproof, and hacker proof safe... is the most secure system.

---

### Post by hoppipolla on 2009-12-08
> **pwnst*r said:**
> lol, so true.

I don't actually remember any people at all claiming Linux was invincible. The sheer fact that that's a POSSIBLE interpretation says something about it's security.

---

### Post by bodhi.zazen on 2009-12-08
> **scouser73 said:**
> Off topic slightly, but this is the first time I've ever heard of anything malicious in Ubuntu, hell even in Linux.

LOL

No offense, but you need to get out more, security section perhaps or security sticky,

Run something like snort or mod_security, set up a honey pot.

---

### Post by pwnst*r on 2009-12-08
> **hoppipolla said:**
> I don't actually remember any people at all claiming Linux was invincible. The sheer fact that that's a POSSIBLE interpretation says something about it's security.

i never said invincible, so not sure where you're going with that.

---

### Post by pwnst*r on 2009-12-08
> **Tipped OuT said:**
> Actually, pulling the power cord, and locking it up in an highly encrypted fireproof, bulletproof, and hacker proof safe... is the most secure system.

...

---

### Post by Random-penguin on 2009-12-08
> **bodhi.zazen said:**
> LOL

No offense, but you need to get out more, security section perhaps or security sticky,

Run something like snort or mod_security, set up a honey pot.


And how helpful is this to a newbie / casual Ubuntu user???;)

---

### Post by issih on 2009-12-08
Personally I think any computer tossed into the Laurentian abyss is pretty unlikely to get a virus...especially if you don't put it in a water proof box.

---

### Post by dmizer on 2009-12-08
What I like ...

The malware removal tool
```
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash && sudo dpkg -r app5552
```

---

### Post by Tipped OuT on 2009-12-08
> **hoppipolla said:**
> I don't actually remember any people at all claiming Linux was invincible. The sheer fact that that's a POSSIBLE interpretation says something about it's security.

I was exaggerating what Linux fanboys say about Linux's security.

Humor.

---

### Post by bodhi.zazen on 2009-12-08
> **Random-penguin said:**
> And how helpful is this to a newbie / casual Ubuntu user???;)

Depends on the user I suppose.

Probably better then [USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn") 

You can lead a horse to water, but ...

---

### Post by bonzi on 2009-12-08
GNU/Linux is more secure because of the default settings. Many things in windows are much more secure than in GNU/Linux. For example NTFS is much more secure than ext3 if configured properly. But Microsoft fails at one thing to set the defaults properly. Its not because they dont know about it. Its because it will make things complex and all the new and inexperienced users will have a tough time. GNU/Linux has an advantage there. The users are not n00bs. But ever since it is getting popular and more and more ppl are starting to use the strong foundation is starting to become shaky. For example Fedora tried to allow users to install without root and ofcourse you must have heard about the cool thing chrome does, it adds the repository automatically.

---

### Post by Random-penguin on 2009-12-08
> **bodhi.zazen said:**
> Depends on the user I suppose.

Probably better then [USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn") 

You can lead a horse to water, but ...


That's true enough!!! I just think we _could_ do more to educate.... Possibly something in the initial install process... call me old fashioned but why not have help files or links on how things should be done (especially for those guys from Windows that are used to trying free software from various sources). Something that is there on the initial desktop... to be explored.......

---

### Post by BuffaloX on 2009-12-08
Just to correct some apparent misconceptions by some people.

This is not a virus, it has no ability to spread itself.
No security flaw has been exploited, so this does not in any way reflect on Linux level of security, either good or bad.

As frak mention I think it was the very first response, this is social engineering.
It was bound to happen sooner or later, and it wasn't even a clever attack, but very clumsy and amateurish.

The lesson learned from this is, we cannot trust stuff from random sites on the Internet. (big surprise)

Installing or running programs from unknown sources, is asking for it,  granting permissions is asking for it big time.

If you are unable to determine the risk when installing or running programs you download then don't. Wait until someone you trust has cleared it.

Blaming this on Linux security is like, if a guy calls you and ask you to transfer money to his account, and you do it.
Then afterwards blame your bank that the transfer actually happened, because it turned out to be a conman.

The function of an OS is to enable your system to run programs.
Conorsulli ran a program, and as far as I can tell, it ran just fine.

What would have been a security flaw, was if the program transferred itself to your computer, or ran by itself, or granted itself root privileges.

Conorsulli did a manual download, a manual run of the installer, and finally manually gave it root.
To get malware, you actually only need to complete the first two steps, or in case of a security exploit none.
But AFAIK no such exploits are known to exist.

---

### Post by tom66 on 2009-12-08
The most secure system is one that doesn't exist.

---

### Post by hoppipolla on 2009-12-08
> **tom66 said:**
> The most secure system is one that doesn't exist.

xD fair enough! It's not really a system then though is it? :)

---

### Post by lisati on 2009-12-08
> **Tipped OuT said:**
> Actually, pulling the power cord, and locking it up in an highly encrypted fireproof, bulletproof, and hacker proof safe... is the most secure system.

I would have suggested maybe a sledgehammer to dismantle the system and a spade or shovel to dig a hole in the garden for the pieces, and a truckload of concrete/cement to seal the deal.

---

### Post by lewisforlife on 2009-12-08
Linux is totally secure, please add my public key to your ~/.ssh/authorized_keys file so that I can lock down your system.

ssh-rsa FJDKLSAFJDF8+FDSJAKFDSLAFDJS878907890FHDSAFHDSJAKFDSA+FHDSJAFKLDSHAJFLSAHFDJFKLADHSAJFKDLSAFHDAKL

In addition to adding my public key, please give me your IP address and open up your SSH port on your router and NAT it to your linux box.  I promise I am just installing security enhancements on your box, I will not do anything else.

;)

---

### Post by sisco311 on 2009-12-08
> **dmizer said:**
> What I like ...

The malware removal tool
```
sudo rm -f /usr/bin/Auto.bash /usr/bin/run.bash /etc/profile.d/gnome.sh index.php run.bash && sudo dpkg -r app5552
```

Unfortunately Auto.bash is a script with an infinite loop in it which downloads run.bash from a server and executes it.

A couple of hours ago and content of the script was a ping command (intended as ping of death attack), now is a rm command.

---

### Post by hoppipolla on 2009-12-08
> **lisati said:**
> I would have suggested maybe a sledgehammer to dismantle the system and a spade or shovel to dig a hole in the garden for the pieces, and a truckload of concrete/cement to seal the deal.

Just set it alight :D


EDIT -- or a controlled explosion!


> **sisco311 said:**
> Unfortunately Auto.bash is a script with an infinite loop in it which downloads run.bash from a server and executes it.

A couple of hours ago and content of the script was a ping command (intended as ping of death attack), now is a rm command.

heh, wow so he has actually been changing the script as it goes?

But why, I just don't get the objective here... possibly proof-of-concept? or maybe he's just bored...

---

### Post by judge jankum on 2009-12-08
I'm pretty much new to all this but I read all the posts I can.. I got ate so bad so many times in "Winders" with malware/trojans it was like a blessing to find something like Synaptic! I'm "skeerd" to download and install anything unless it's through Synaptic, but that's just me....
One of the most fantastic things about Ubuntu also is this forum!!! The way people flocked to help any way they could, and the fast progress was amazing!!! To me this kind support puts Ubuntu far beyond any other system out there, at any price!!!!

---

### Post by Rainstride on 2009-12-08
this right here is why i make it a rule, to never install .deb packs unless i know for a fact that they are 100% safe.

---

### Post by sisco311 on 2009-12-08
> **lewisforlife said:**
> Linux is totally secure, please add my public key to your ~/.ssh/authorized_keys file so that I can lock down your system.

ssh-rsa FJDKLSAFJDF8+FDSJAKFDSLAFDJS878907890FHDSAFHDSJAKFDSA+FHDSJAFKLDSHAJFLSAHFDJFKLADHSAJFKDLSAFHDAKL

In addition to adding my public key, please give me your IP address and open up your SSH port on your router and NAT it to your linux box.  I promise I am just installing security enhancements on your box, I will not do anything else.

;)

Or one could simply install [evilmalware]("http://www.gnu.org/fun/jokes/evilmalware.html"). 
:)

---

### Post by 3rdalbum on 2009-12-08
Debian packages are inspectable.

Right-click on one and choose "Open in File Roller" or "Open in Archive Manager". A File Roller window will appear showing two or three .tar.gz archives. Open up the "data" one and have a look inside. You can see exactly what will be put into your filesystem, and audit it before installing.

Try doing that with an MSI!

---

### Post by lisati on 2009-12-08
> **hoppipolla said:**
> Just set it alight :D


EDIT -- or a controlled explosion!



Something for myhbusters?

---

### Post by sisco311 on 2009-12-08
> **hoppipolla said:**
> 
heh, wow so he has actually been changing the script as it goes?



Yep, she/he can change the script whenever she/he pleases to do so.

> **hoppipolla said:**
> 
But why, I just don't get the objective here... possibly proof-of-concept? or maybe he's just bored...

Maybe she considers this a challenge, but is not, it's so trivial...

---

### Post by 3rdalbum on 2009-12-08
> **Random-penguin said:**
> Now that would make sense and I am thinking of those new to the Linux experience... it can be all so daunting and easy to slip up on good admin practice. On one hand we're trying to push Linux out to the masses but we don't have clarity (for the newbie / casual user) on what is good practice!

I disagree - on countless occasions I've heard people saying "There are no viruses for Linux, but don't blindly install anything outside the repositories unless you're sure it's safe".

> I think part of the solution in Ubuntu would be a user friendly firewall by default with sensible settings.

Ubuntu goes one better, actually. It doesn't listen to incoming ports by default, therefore negating the need for a personal firewall unless you install server software.

A firewall would not do diddly squat for this trojan.

---

### Post by doas777 on 2009-12-08
> **hoppipolla said:**
> 
But why, I just don't get the objective here... possibly proof-of-concept? or maybe he's just bored...

he's playing. the exemplification of a script kiddie. wants to be a 1337 hax0r.
for a while there, he had a messsge for us on his page, taunting a little. the original thread indicates some changes as he went along. luckilly the op caught it while it was in dos mode, not self-destruct mode (flawed though it may be). it seems clear to me that he was experimenting at the same time the community were dissecting it.

---

### Post by earthpigg on 2009-12-08
> **3rdalbum said:**
> 
A firewall would not do diddly squat for this trojan.

beat me to it.

---

### Post by MooPi on 2009-12-08
Ok why, I have a small firewall box running Smoothwall that I constantly have to create rules to enable outgoing traffic that's blocked. Why would the malicious screensaver payload get through ?

> A firewall would not do diddly squat for this trojan. 

---

### Post by slakkie on 2009-12-08
> **MooPi said:**
> Ok why, I have a small firewall box running Smoothwall that I constantly have to create rules to enable outgoing traffic that's blocked. Why would the malicious screensaver payload get through ?

Because it opens a connection on a well-known port: 80. aka http.

---

### Post by Diluted on 2009-12-08
> **BuffaloX said:**
> This is not a virus, it has no ability to spread itself.
No security flaw has been exploited, so this does not in any way reflect on Linux level of security, either good or bad.
I think the problem here is that Linux is touted to be malware-free due to its security. If a user manages to get bad things onto their computer (even if it is not the fault of the OS), then I wouldn't be surprised to see them infer that Linux is insecure.

> As frak mention I think it was the very first response, this is social engineering.
It was bound to happen sooner or later, and it wasn't even a clever attack, but very clumsy and amateurish.
Oh, but it highlighted the fact that Linux users are susceptible to social engineering, which opens doors to more dangerous attacks. What if the attack was disguised properly? What if it actually provided the screensaver in question? If so, even I would not have noticed anything if I installed it from the GUI.

> **BuffaloX said:**
> The lesson learned from this is, we cannot trust stuff from random sites on the Internet. (big surprise)
The content was apparently from GNOME-Look.org, and I would not consider it to be a random site.

> **BuffaloX said:**
> Installing or running programs from unknown sources, is asking for it,  granting permissions is asking for it big time.
There is a demand for things which aren't in the repositories. I don't think there's a distribution out there which will package every themes, screensavers and other sorts of add-ons in existence.

> **BuffaloX said:**
> If you are unable to determine the risk when installing or running programs you download then don't. Wait until someone you trust has cleared it.
Shame there's no antivirus on Linux, so I'm going to have to learn shell scripting, disassemble the binary (if no scripts are used), monitor everything my computer does, or rely on comments from other users (who would be more interested in praising than suspecting if something is malicious). Well, I know a Linux guru, so I'll just bother him for every theme and screensaver I want to try out.

> **BuffaloX said:**
> Conorsulli did a manual download, a manual run of the installer, and finally manually gave it root.
To get malware, you actually only need to complete the first two steps, or in case of a security exploit none.
But AFAIK no such exploits are known to exist.
I think we've established that people would do the first two steps, so I probably won't bother to look for an exploit.

---

### Post by phrostbyte on 2009-12-08
If you just install stuff from the Ubuntu repository you are pretty safe. The problem is people downloaded this file from a 3rd party website. Windows doesn't have a trusted repository like Ubuntu does, so **YES**, it is generally less secure.

---

### Post by phrostbyte on 2009-12-08
> There is a demand for things which aren't in the repositories. I don't think there's a distribution out there which will package every themes, screensavers and other sorts of add-ons in existence.

If you download anything from any 3rd party website (ESPECIALLY a .deb) you are taking a risk. Unfortunately there is no good "solution" to this problem, because computers don't have some kind of AI that detect malicious code yet. And even if they did it would be imperfect (malicious is subjective, btw). So you are still taking the risk regardless. :)

---

### Post by aysiu on 2009-12-08
> **Diluted said:**
> I think the problem here is that Linux is touted to be malware-free due to its security. If a user manages to get bad things onto their computer (even if it is not the fault of the OS), then I wouldn't be surprised to see them infer that Linux is insecure. They would be inferring incorrectly. Social engineering always works on any operating system, no more how securely it's built.

> Oh, but it highlighted the fact that Linux users are susceptible to social engineering, which opens doors to more dangerous attacks. What if the attack was disguised properly? What if it actually provided the screensaver in question? If so, even I would not have noticed anything if I installed it from the GUI. As I stated before, social engineering works on all operating systems, as long as the user is gullible.

> The content was apparently from GNOME-Look.org, and I would not consider it to be a random site. **This** is the most disturbing part. Not only is not a random site, but it is one new users often get referred to when looking for themes. Either Gnome-Look.org needs a better vetting process, or the Ubuntu devs need to work on getting more themes into the official Ubuntu repositories.

> There is a demand for things which aren't in the repositories. I don't think there's a distribution out there which will package every themes, screensavers and other sorts of add-ons in existence. Well, I'll agree when it comes to themes. But the vast majority of popular Linux software applications is already in the repositories.

> Shame there's no antivirus on Linux, so I'm going to have to learn shell scripting, disassemble the binary (if no scripts are used), monitor everything my computer does, or rely on comments from other users (who would be more interested in praising than suspecting if something is malicious). Well, I know a Linux guru, so I'll just bother him for every theme and screensaver I want to try out. This makes no sense. If you'd had antivirus installed, it would not have detected this trojan. Antivirus is a useless placebo (even on Windows). Antivirus software is **not** a substitute for real security.

---

### Post by chillicampari on 2009-12-08
Diluted, your post rocks.

[IMG]http://i48.tinypic.com/2dieeqq.jpg[/IMG]


phrostbyte, I think there is a problem with perception (which I'll fall into also). Even though a site like gnome-look.org is a third party site, it still falls into community, which lends the idea of trust, even though it's primarily user generated content. I think someone is much more comfortable installing something from there than something from say big-willys-house-of-pr0ns-and-free-warez.net which just shouts untrustable. 

That combined with marketing of the Linux desktop as 'you don't have to worry about these things anymore' creates complacency.

---

### Post by phrostbyte on 2009-12-08
> **chillicampari said:**
> Diluted, your post rocks.

[IMG]http://i48.tinypic.com/2dieeqq.jpg[/IMG]


phrostbyte, I think there is a problem with perception (which I'll fall into also). Even though a site like gnome-look.org is a third party site, it still falls into community, which lends the idea of trust, even though it's primarily user generated content. I think someone is much more comfortable installing something from there than something from say big-willys-house-of-pr0ns-and-free-warez.net which just shouts untrustable. 

That combined with marketing of the Linux desktop as 'you don't have to worry about these things anymore' creates complacency.

Whoever markets Linux that way is wrong. I do think Linux is more secure then both Windows AND Mac OS X, and this doesn't change that. But there is no 100% intrusion proof security system both in the computer world or the real world. 

I can't even say completely sticking to the repo is 100% either, but I will say it's FAR FAR more safe then download random garbage off the Internet and running it with root privs.

And of all things, files which end in .deb can do literally anything to your computer. When they are executed, they run with full rights, as this is needed to install software (even with AppArmor/SELinux). It would be more difficult to code a virus in a theme file, for instance, because theme files aren't installers.

---

### Post by steveneddy on 2009-12-08
> **Tipped OuT said:**
> Where is Linux's invincible security now?

If the user installs from sources that aren't known to be secure then the user made their PC insecure.

Only install software from trusted sources and only use trusted repos.

The next step would be for someone to offer a patch that would make this type of vulnerability ineffectual.

---

### Post by phrostbyte on 2009-12-08
> **steveneddy said:**
> If the user installs from sources that aren't known to be secure then the user made their PC insecure.

Only install software from trusted sources and only use trusted repos.

The next step would be for someone to offer a patch that would make this type of vulnerability ineffectual.

There is no easy "patch" to this. A deb needs to be able to run with full rights, because it's suppose to be able to install ANY software, including kernel updates and even bootloaders. Anything is fair game in a .deb.

Perhaps what should be done disable the installation of third party .deb files which have not been vetted by peer review. Or at least give a warning for people to ignore. :P

---

### Post by chris200x9 on 2009-12-08
Hey, I can open xterm and run ```
sudo rm -rf
``` I AM A VIRUS!!1

this should really be a non-issue, I don't know why it's "news"

---

### Post by hoppipolla on 2009-12-08
> **chris200x9 said:**
> Hey, I can open xterm and run ```
sudo rm -rf
``` I AM A VIRUS!!1

this should really be a non-issue, I don't know why it's "news"

well, it's proof that it's easy to do a lot of damage with a standard debian package, and proof that these packages can be snuck up on Gnome-look. To be fair though certainly the former point I always considered to be quite obvious.

As for Gnome-look, sites like that can be quite "open" and community-maintained, so it's no surprise things like that can sneak up really ._.

More staff on GL might be a good idea, to monitor packages a little better, but even then could they ever keep up with them all?

---

### Post by aysiu on 2009-12-08
> **chris200x9 said:**
> I don't know why it's "news" It's news because the malicious .deb was on [http://www.gnome-look.org](http://www.gnome-look.org). If it had been on some shady site, I don't think it would be news.

---

### Post by lisati on 2009-12-08
Short of not using your computer, surely the best defense against malware and other nasty stuff is being aware of the potential risks and being smart about what you do? 

Sometimes the answer to the potential for trouble will involve software-based tools but more often it's up to the user.

---

### Post by chillicampari on 2009-12-08
> **phrostbyte said:**
> Whoever markets Linux that way is wrong. I do think Linux is more secure then both Windows AND Mac OS X, and this doesn't change that. But there is no 100% intrusion proof security system both in the computer world or the real world. 



Sure, we know that, but that doesn't change that it's been promoted as such (I've even heard it  at trade shows). 

> 
I can't even say completely sticking to the repo is 100% either, but I will say it's FAR FAR more safe then download random garbage off the Internet and running it with root privs.
I wasn't talking about the repos. Those of course should be 100% vetted on the distro default download locations.

> 
And of all things, files which end in .deb can do literally anything to your computer. When they are executed, they run with full rights, as this is needed to install software (even with AppArmor/SELinux). It would be more difficult to code a virus in a theme file, for instance, because theme files aren't installers.Well of course .debs are running with full rights. :o

---

### Post by chillicampari on 2009-12-08
> **phrostbyte said:**
> ... Or at least give a warning for people to ignore. :P

Heh- good point!:p

---

### Post by BuffaloX on 2009-12-08
> **Diluted said:**
> I think the problem here is that Linux is touted to be malware-free due to its security. If a user manages to get bad things onto their computer (even if it is not the fault of the OS), then I wouldn't be surprised to see them infer that Linux is insecure.


Linux is still malware free, if you follow simple guidelines.
You can dismiss the guidelines, and still your risk is very low.
There are no known zero-day or fly-by vulnerabilities. They may exist, and if they do, and it gets exploited, then we will see if the Linux community will be fast and efficient at eliminating it. I think it will.
This is not a guarantee, just much better than what Windows offers.

> **Diluted said:**
> 
Oh, but it highlighted the fact that Linux users are susceptible to social engineering, which opens doors to more dangerous attacks. What if the attack was disguised properly? What if it actually provided the screensaver in question? If so, even I would not have noticed anything if I installed it from the GUI.

No question this was a lame attempt, and not a real test in line with some of the clever stuff Windows hackers do.
Manually installable malware can never reach the same levels of success as real viruses do.

> **Diluted said:**
> 
The content was apparently from GNOME-Look.org, and I would not consider it to be a random site.

No it's not a random site, and I believe they are themselves victims.
But apparently we need to be sure that sites we download execute-ables from, have proper safeguards against stuff like this.

> **Diluted said:**
> 
There is a demand for things which aren't in the repositories. I don't think there's a distribution out there which will package every themes, screensavers and other sorts of add-ons in existence.

There don't have to be, just only download stuff you can trust, from sites you can trust. Just be at least a little bit careful.

> **Diluted said:**
> 
Shame there's no antivirus on Linux, so I'm going to have to learn shell scripting, disassemble the binary (if no scripts are used), monitor everything my computer does, or rely on comments from other users (who would be more interested in praising than suspecting if something is malicious). Well, I know a Linux guru, so I'll just bother him for every theme and screensaver I want to try out.


Haha I get the irony.
Clamav is in the repositories, and I think Avast, Panda and AVG also have anti virus programs for Linux.
These are usually used for systems that are in contact with Windows, either through wine, shared drives or dual boot. But there are some available if you feel you need it.

You don't need disassembly if you have the source. If the source is unavailable be a little bit more careful.

You can't trust random people on a random forum, but if someone says it has a virus, and another says no it doesn't. I would consider it very likely that it had a virus, and proceed with extreme care.

You don't need to monitors your system all the time, but you could do it if you install stuff you feel needs to be monitored, monitor network traffic, cpu usage and disk activity. If something weird is going on, you would probably be able to spot it pretty quickly. They are even available as nice eye candy, and you only have to use monitors if you are doing something you really shouldn't be doing, like installing untrusted packages. ;)

> **Diluted said:**
> 
I think we've established that people would do the first two steps, so I probably won't bother to look for an exploit.
[/QUOTE]
If you want your botnet to be successful you would.
It's been established that someone with his guards down, would go through all 3 steps. This time it was easy to catch someone with his guards down, because we haven't had much if any of this sort of problem before.
Next time it will be a little harder, and if it is equally amateurish, it may be caught before it infects one single person.

---

### Post by ijzl on 2009-12-08
hey guys, im ubuntu and linux is new to me.  I will be asking many questions on this forum :)
oh course.. searching first though.  Lets hope i dont fall for some stupid things like that without knowing.  :P

---

### Post by hoppipolla on 2009-12-08
> **ijzl said:**
> hey guys, im ubuntu and linux is new to me.  I will be asking many questions on this forum :)
oh course.. searching first though.  Lets hope i dont fall for some stupid things like that without knowing.  :P

haha well it's hard to ignore completely, but just keep your wits about you :)

I tend to only download things that have had a reasonable number of positive ratings or are from somewhere reputable, but yeah you could always check the contents of the file as well by checking the contents with something like file roller :)

---

### Post by qalimas on 2009-12-08
Anyone with physical access to get into any machine.

Backtrack.

chntpw to get into Windows, vi /etc/shadow to get into Linux.

---

### Post by lisati on 2009-12-08
> **ijzl said:**
> hey guys, im ubuntu and linux is new to me.  I will be asking many questions on this forum :)
oh course.. searching first though.  Lets hope i dont fall for some stupid things like that without knowing.  :P

Exactly. Even though none of my current crop of machines has been affected/infected for quite a while, I keep an eye on discussions like this one so I can be aware of what to watch out for. As the saying goes, "be alert, your country needs more lerts."

---

### Post by toupeiro on 2009-12-08
This exposes a hugely fundamental problem.  sudo is generally treated as benign as the ls command, and people do not realize, at all, what sudo is enabling in someones system .  This was a social hack, and the users knowledge was the weakest link.  This isn't something that was triggered through unprotected port access or hidden back doors.  In some ways ubuntu can be praised for making linux easy, but has it been made too easy?

---

### Post by Diluted on 2009-12-08
> **aysiu said:**
> They would be inferring incorrectly. Social engineering always works on any operating system, no more how securely it's built.
> **aysiu said:**
> As I stated before, social engineering works on all operating systems, as long as the user is gullible.
The problem I have with Linux advertising itself to be virus-free, spyware-free, *-free is that it will inevitably make some users think that is all they need to worry about for security (after all, nobody said you need to have common sense and a healthy dose of paranoia as well). People will become complacent as a result and be susceptible to these kinds of attacks.

> **aysiu said:**
> Well, I'll agree when it comes to themes. But the vast majority of popular Linux software applications is already in the repositories.
I agree that repositories provide a good amount of protection against malware. However, I think its effectiveness is reduced by the large number of distributions out there. It would be impossible for a developer to have their software on every repository, especially if it is a low profile one. The large number of repositories would encourage them to simply put the source and binaries on another website, which would technically be an untrusted source (unless the site will verify the contents as well, then you have to trust the competence of the testers themselves).

If there was a single repository which is compatible with all distributions, then I think it would work well. Unfortunately, it would take a lot of work to accommodate the different packaging standards, different versions, different filesystem layout and whatever differences which makes things work on one distribution and break on the other.

> **aysiu said:**
> This makes no sense. If you'd had antivirus installed, it would not have detected this trojan. Antivirus is a useless placebo (even on Windows). Antivirus software is not a substitute for real security.
Maybe not, but it is still some form of protection for a non-tech savy user. Of course, antivirus causes problems of its own, but at least it raises the bar for script kiddies using packaged or existing malware from the Internet.

> **BuffaloX said:**
> There don't have to be, just only download stuff you can trust, from sites you can trust. Just be at least a little bit careful.
There comes a point where trust and being careful can only get you so far. I can look up on the author to see if he is a new contributor on GNOME-Look.org, but that's no guarantee that his latest works are safe and that the past works are there to attract an audience. The only way you can be even more careful is to monitor the things you've downloaded to see if it exhibits strange behavior, and not everyone is willing to do that.

> **BuffaloX said:**
> Haha I get the irony.
Clamav is in the repositories, and I think Avast, Panda and AVG also have anti virus programs for Linux.
These are usually used for systems that are in contact with Windows, either through wine, shared drives or dual boot. But there are some available if you feel you need it.
Correct me if I'm wrong, but I think the antiviruses for Linux are designed to look for Windows malware, rather than Linux ones.

> **BuffaloX said:**
> You don't need disassembly if you have the source. If the source is unavailable be a little bit more careful.
Users would have to learn programming in order to read the source. Even if one can read, developers can obfuscate the code to hide its purpose. Or worse, the developers can provide a perfectly clean source code, but use their own version of the compiler to introduce a backdoor.

> **BuffaloX said:**
> You don't need to monitors your system all the time, but you could do it if you install stuff you feel needs to be monitored, monitor network traffic, cpu usage and disk activity. If something weird is going on, you would probably be able to spot it pretty quickly. They are even available as nice eye candy, and you only have to use monitors if you are doing something you really shouldn't be doing, like installing untrusted packages.
Ah, I don't mean resource monitoring, I mean things like process monitoring or packet sniffing. If I wanted to know if something is malware or not, I would be monitoring the application to see what it does and what kind of IP addresses it is establishing connections with. This would definitely require a higher sense of paranoia and I don't think normal users will put up with this just to see if something is acting strange.

---

### Post by MooPi on 2009-12-09
Calling this incident  a virus may be stretching the terminology a bit. This malicious software is not able to replicate or infect other machines without interaction from the user. There was no drive by installation or activeX code to zombify it's victim. Just poor decisions on software selection and implementation of a deb file. Linux has a while to go before we a a full blown virus outbreak that infects millions of computers. I won't worry knowing that my Linux box is now vulnerable.

---

### Post by lykwydchykyn on 2009-12-09
> **aysiu said:**
> It's news because the malicious .deb was on [http://www.gnome-look.org](http://www.gnome-look.org). If it had been on some shady site, I don't think it would be news.

What really troubles me about this is that gnome-look.org is part of freedesktop.org, which also runs kde-look.org and kde-apps.org (along with dozens of similar sites).  Those sites are tightly integrated into KDE with no obvious means of disabling the integration.

I've released stuff on KDE-look.org, and as far as I could tell there was no vetting process.  Heck, I could chuck binaries with no source code and it wouldn't stop me.

Maybe there needs to be a movement to improve opendesktop.org's security?

---

### Post by cariboo on 2009-12-09
Linux has always been vulnerable to this type of exploit. As with any operating system the user is the problem. A malware detector wouldn't work to stop anything.

I think it's time opendesktop.org changed their policy and make anyone that submits material prove that their theme/icons whatever don't contain any malicious scripts.

---

### Post by twogeo on 2009-12-09
> **running_rabbit07 said:**
>  Other than themes from that site, all other software I get comes from known safe sites, such as cisco.netacad.net and mozilla.com.

That's a good conservative attitude, but keep in mind that even though it's under the Mozilla umbrella, Mozilla Addons is no protection against uninvited code - given that an extension or theme is, by virtue of the omnipotence of monkey patches over browser rights, capable of  any action in your system that a browser  is capable of - - including monkeying with any other installed extension -- and that the most trusted extensions with Mozilla Addons approval are updated without code being examined by any trusted intermediary at all.  It's no airtight system against naughty people.
Until *FOMS syndrome is treatable, there are always going to be these kind of unwanted installs, whatever the system.
Good catching for this trojan!

*[SIZE=1]FearOfMissingSomething[/SIZE]

---

### Post by BenAshton24 on 2009-12-09
I quite honestly don't know what the fuss is about... DDoSsing a website about world of warcraft hacks, cheats & bots seems like a good cause to me! I'm not a hardcore gamer or anything, in fact I rarely ever play games, but I know that it sucks to be playing and then get Pwned by some noob with an aimbot.

Although the guy that posted the malware really should have though harder about what he was attacking; the Linux community doesn't take kindly to this sort of thing... The attempt was pretty weak anyway, using wget and a few 10 line bash scripts is hardly the most undercover way of doing things. He/She could at LEAST have put a screensaver in the deb to prevent suspicion... if a .deb screensaver wasn't enough already :P

---

### Post by BenAshton24 on 2009-12-09
> **lisati said:**
> Caution! Popup on site! (Appears to be an ad for an IQ test)

I know this is a bit irrelevant, but seriously! don't you have AdBlockPlus installed!? :P

---

### Post by Uncle Spellbinder on 2009-12-09
I think we all know the only reason Windows is so susceptible to virus/trojan/malware issues is it's vast and unparalleled popularity. If Mac, Linux, Solaris, or any other 2nd tier OS were anywhere near as widely used as Windows, they would also have a multitude of virus/trojan/malware issues.

Simple fact is, Widows is used worldwide buy more users than all other OS's combined. That's why Windows get's "infected" more than any other OS. 

If these hackers bothered to put as much work into Linux as they do Windows, there would be plenty of infected Linux users.

---

### Post by judge jankum on 2009-12-09
what is ad block plus?

---

### Post by BenAshton24 on 2009-12-09
Well, if Linux were more popular then there would be more people available to write security fixes as well as more people to write viruses. One main reason that windows has so many viruses is that it is closed source and relies on official updates from microsoft or third party antivirus companies. Removing a virus is suprisingly easier when you can find the hole that it got through. Another reason is that even the darkest hats of the internet have morals and attacking a FREE OS is something that would require new levels of submersion. Also, the security on Linux is far greater than that of Windows, with root privilages required to install anything or run anything that could truely damage your system. Social engineering is the one area that is difficult to secure. People grow complacent and download and run things without checking their integrity before hand. The only reason that this one got in was through social engineering and carelesness.

Ben.

---

### Post by mikewhatever on 2009-12-09
> **Uncle Spellbinder said:**
> I think we all know the only reason Windows is so susceptible to virus/trojan/malware issues is it's vast and unparalleled popularity. If Mac, Linux, Solaris, or any other 2nd tier OS were anywhere near as widely used as Windows, they would also have a multitude of virus/trojan/malware issues.

Simple fact is, Widows is used worldwide buy more users than all other OS's combined. That's why Windows get's "infected" more than any other OS. 

If these hackers bothered to put as much work into Linux as they do Windows, there would be plenty of infected Linux users.

Are you talking about social engineering or OS architecture and design? I think there is no question that the latter is more secure in Windows.

---

### Post by Icehuck on 2009-12-09
> **mikewhatever said:**
> Are you talking about social engineering or OS architecture and design? I think there is no question that the latter is more secure in Windows.

So why were apparmor and selinux developed then?

---

### Post by BenAshton24 on 2009-12-09
[http://adblockplus.org/en/](http://adblockplus.org/en/)

an addon for firefox that blocks adverts.

---

### Post by 3rdalbum on 2009-12-09
I'm wondering whether this trojan has been added to any anti-virus definitions for (say) AVG... it would be interesting to see if the AV vendors have the same response time on Linux as they do on Windows!

Also, about the firewall: The script tells Wget to request a page on port 80. All your web page requests come through port 80, which I imagine is not blocked. Even if your firewall can block specific applications, I'd be very surprised if you haven't already unblocked Wget.

And I'd like to correct myself. I said "A firewall would not do diddly squat". I meant to say "A firewall would do diddly squat".

---

### Post by NoaHall on 2009-12-09
> **cariboo907 said:**
> Linux has always been vulnerable to this type of exploit. As with any operating system the user is the problem. A malware detector wouldn't work to stop anything.

I think it's time opendesktop.org changed their policy and make anyone that submits material prove that their theme/icons whatever don't contain any malicious scripts.

I think they shouldn't be allowed to have .deb files on there, for sure. It's not needed.

---

### Post by Icehuck on 2009-12-09
> **NoaHall said:**
> I think they shouldn't be allowed to have .deb files on there, for sure. It's not needed.

Agree

---

### Post by Crunchy the Headcrab on 2009-12-09
> **Tipped OuT said:**
> Where is Linux's invincible security now?No OS is invincible to PEBCAK.

---

### Post by ElSlunko on 2009-12-09
Sucks for those who got infected!

---

### Post by lisati on 2009-12-09
> **Crunchy the Headcrab said:**
> No OS is invincible to PEBCAK.

Or ID Ten-Seven. :)

---

### Post by Hallvor on 2009-12-09
> **Uncle Spellbinder said:**
> I think we all know the only reason Windows is so susceptible to virus/trojan/malware issues is it's vast and unparalleled popularity. If Mac, Linux, Solaris, or any other 2nd tier OS were anywhere near as widely used as Windows, they would also have a multitude of virus/trojan/malware issues.

Simple fact is, Widows is used worldwide buy more users than all other OS's combined. That's why Windows get's "infected" more than any other OS. 

If these hackers bothered to put as much work into Linux as they do Windows, there would be plenty of infected Linux users.

Popularity is only a part of it. Popularity makes Windows a big target for malware writers who for the most part want to make a profit. But in order to spread the malware they must make sure that the malware will replicate and spread to create a mass infection. In Windows extremely many run their system as admin (equivalent of root) because of poor design, and things like activex in the browser only makes things easier. That could not only get you infected simply by visiting a website; you are also certain that the malware can do whatever it wants with your computer since it already has admin access. It can start sending spam, try to infect your friends on MSN and everything else the cracker wants.

Another attack vector is the lack of repositories and the installation of non-trusted software. The Windows way is often searching for an application on google, downloading it and running it. Even worse a lot of users download cracked software with P2P applications that can contain all sorts of malware. When the user installs them, they have admin access. In GNU/Linux users almost always use safe and trusted applications from repositories.

And finally, most GNU/Linux users are more knowledgeable when it comes to computers than the average Windows user.

Bottom line is that Windows is susceptible for several reasons, but popularity is only one of them.

---

### Post by Hallvor on 2009-12-09
> **NoaHall said:**
> I think they shouldn't be allowed to have .deb files on there, for sure. It's not needed.

External deb files are a disease.

---

### Post by mikewhatever on 2009-12-09
> **Icehuck said:**
> So why were apparmor and selinux developed then?

More secure doesn't mean bullet proof. In some environments, you may need a little or a lot more restriction. It's a relative thing, and there is probably no limit.

---

### Post by lykwydchykyn on 2009-12-09
> **Crunchy the Headcrab said:**
> No OS is invincible to PEBCAK.

> **lisati said:**
> Or ID Ten-Seven. :)

No, but we can put mechanisms in place to mitigate the risks a little and give people a reason to trust the community.

It's easy to call people idiots in hindsight, but are you telling me you've NEVER installed anything from a non-official repository or source?

---

### Post by doas777 on 2009-12-09
> **steveneddy said:**
> If the user installs from sources that aren't known to be secure then the user made their PC insecure.

Only install software from trusted sources and only use trusted repos.

The next step would be for someone to offer a patch that would make this type of vulnerability ineffectual.

that argument used to hold true if you were sticking to trusted websites in windows. the advent of ad networks and redirected content blew that one out of the water as well. yet somehow it is MSs fault that people are getting infected when going to reputable sites, while ubuntu is "secure" even though it has the same problem?

there can be no patch to that kind of exploit, since there is no vulnerability that is distinctly different from the legitimate vector. behavioral detection is the only means. second, why would you trust software from the repos? what if they are compromised? how safe are you then?

it's like saying your computer is safe, as long as you don't use it for anything interesting or important. 

don't get me wrong, I know that it is important not to do stupid things, but the abruptness to your post exposes a real double standard to how the community deals with the perception of malware.

---

### Post by mivo on 2009-12-09
> **Hallvor said:**
> And finally, most GNU/Linux users are more knowledgeable when it comes to computers than the average Windows user.

Ubuntu and other distros indirectly aim at changing that. The competence of the average Linux user is steadily declining. 

I think incidents like this one are helpful in a way. They tackle this dangerous "invincibility" myth and heighten security awareness. It does bite for those affected, but for the community at large there are some benefits.

---

### Post by pelle.k on 2009-12-09
There's no need to install themes system wide (unless of course your an admin). But that also goes for software. The missing ability to install applications on a user basis really need fixing.

Also, the lack of proper packages from official channels is really hurting linux. Distros can't agree on a common packaging standard, and thus every distro have it's own little package pool with lots of missing pieces. People with less technical know-how, or with malicious intent, naturally try to fill those gaps.

Fail!

---

### Post by Keyper7 on 2009-12-09
You know, all this talk about security is interesting and all, but I prefer to focus on something else: some guy wanted to use Gnome users to perform a DoS attack on a site related to a very mainstream game. If this is a not a sign of the increasing popularity of alternative OSes, I don't know what is.

---

### Post by Warpnow on 2009-12-09
I wouldn't want the kind of security that means removing me from control of my system.

I'd also never just randomly download a deb file from gnome-look and install it.

---

### Post by doas777 on 2009-12-09
> **pelle.k said:**
> There's no need to install themes system wide (unless of course your an admin). But that also goes for software. The missing ability to install applications on a user basis really need fixing.

Also, the lack of proper packages from official channels is really hurting linux. Distros can't agree on a common packaging standard, and thus every distro have it's own little package pool with lots of missing pieces. People with less technical know-how, or with malicious intent, naturally try to fill those gaps.

Fail!

agreed. it only took them like 2 years to figure out that Automatix was bad for your system?

---

### Post by Diluted on 2009-12-09
> **pelle.k said:**
> The missing ability to install applications on a user basis really need fixing.
This is an interesting point, since I thought Fedora had the right idea to allow users to install signed RPMs without root's password. Unfortunately, they backed down from the backlash that followed, with the community saying it would be insecure.

---

### Post by clanky on 2009-12-09
> **Warpnow said:**
> I wouldn't want the kind of security that means removing me from control of my system.

I'd also never just randomly download a deb file from gnome-look and install it.

This is where Linux will have to either change substantially or forget about the idea of having any sort of market share worth talking about.

If Linux market share increases then Linux is either going to have to be more idiot proof or become insecure, an increase in market share would mean that not only would there be more people using Linux who will download files without stopping and thinking, but there will be more incentive to create malware for Linux.

---

### Post by mivo on 2009-12-09
> **Keyper7 said:**
> ... perform a DoS attack on a site related to a very mainstream game. If this is a not a sign of the increasing popularity of alternative OSes, I don't know what is.

Or perhaps it was just easier to do with Linux. Has Windows become too secure? ;)

---

### Post by ibuclaw on 2009-12-09
> **clanky said:**
> This is where Linux will have to either change substantially or forget about the idea of having any sort of market share worth talking about.

If Linux market share increases then Linux is either going to have to be more idiot proof or become insecure, an increase in market share would mean that not only would there be more people using Linux who will download files without stopping and thinking, but there will be more incentive to create malware for Linux.

I disagree.

Everything that has happened here is not like it is an unknown possibility.
I recall having discussions on this type of happening almost a year back.

At the end of the day, this is not a bug, nor is this invalid behavour, and certainly is not a security hole - nor is it exploiting anything. All software is working as per design, and as such we can only assume that you are using it wisely.

In Windows you *may* think twice about downloading and running **OMgFreeWallpapers.exe** - so why would you think differently about the same but in a .deb format?

Complacency of users is the killer here - not the system. Therefore this is a non-issue as far as I'm concerned.

---

### Post by pelle.k on 2009-12-09
> **Diluted said:**
> This is an interesting point, since I thought Fedora had the right idea to allow users to install signed RPMs without root's password. Unfortunately, they backed down from the backlash that followed, with the community saying it would be insecure.
Maybe i worded that badly. What i meant that you should be able to install applications to your home folder (or only folder writable by ordinary users), i.e. an installations process running with your PID/GID, not as root. Thus no access to the root file system.
Of course you could let a sperarate installer process resolve dependencies (and install them as root) from a *secure* repository, but not the package itself. Per user installed applications.

Still, with a common packaging format, i think the need for that ^^ wouldn't be so pressing.

---

### Post by Diluted on 2009-12-09
I wasn't quite sure whether Fedora was allowing users to install any kind of signed packages, or just the ones which do not interact with system files (what I had in mind). Probably the former, judging from a bit more reading.

So yeah, ignore that.

---

### Post by Ghost|BTFH on 2009-12-09
> **Random-penguin said:**
> Yes this is so true, but we need to (especially in newbie friendly Ubuntu) get that basic knowledge across.... :D

How hard is it?  I'm sorry, I just can't believe that with almost 10.000 programs in the repositories, someone was meandering along the Intarweb and said, "Oh pooh...the 80+ screensavers just don't do it for me...oh! But here's one from some vague unknown source!!!"

Seriously...PEBKAC and ID-10-T are the main reasons for this kind of stuff.

I don't know how Ubuntu or any other Linux OS out there could make it easier to say "HEY! LOOK IN YOUR REPOSITORIES FOR PROGRAMS."

Megaphone perhaps?

I know, how about a desktop wallpaper that says, 

"USING ROOT IS DANGEROUS!  IF YOU MUST INSTALL A PIECE OF SOFTWARE FROM OUTSIDE THE REPOSITORIES, PLEASE MAKE SURE IT IS A SAFE AND TRUSTED SITE!"

I mean...the person was intelligent enough to look at the script, but dumb enough to install from an untrusted site?

Grrr...I see dumb people.

Cheers,
Ghost

---

### Post by lisati on 2009-12-09
> **BenAshton24 said:**
> I know this is a bit irrelevant, but seriously! don't you have AdBlockPlus installed!? :P

I don't have adblock at the moment (personal choice, most of the websites I visit don't do popups). Firefox blocked the poup on its own.

---

### Post by Enlightened Shadow on 2009-12-09
> **Ghost|BTFH said:**
> How hard is it?  I'm sorry, I just can't believe that with almost 10.000 programs in the repositories, someone was meandering along the Intarweb and said, "Oh pooh...the 80+ screensavers just don't do it for me...oh! But here's one from some vague unknown source!!!"

Seriously...PEBKAC and ID-10-T are the main reasons for this kind of stuff.

I don't know how Ubuntu or any other Linux OS out there could make it easier to say "HEY! LOOK IN YOUR REPOSITORIES FOR PROGRAMS."

Megaphone perhaps?

I know, how about a desktop wallpaper that says, 

"USING ROOT IS DANGEROUS!  IF YOU MUST INSTALL A PIECE OF SOFTWARE FROM OUTSIDE THE REPOSITORIES, PLEASE MAKE SURE IT IS A SAFE AND TRUSTED SITE!"

I mean...the person was intelligent enough to look at the script, but dumb enough to install from an untrusted site?

Grrr...I see dumb people.

Cheers,
Ghost

Just a quick question. Where in the repos is screensavers. You mentioned 80+ and I have never seen them.

---

### Post by Enlightened Shadow on 2009-12-09
Anyone know what he means?

---

### Post by NoaHall on 2009-12-09
> **Enlightened Shadow said:**
> Anyone know what he means?

Well, under the "Choose screensaver" option, I have at least 20. I haven't installed any ever.

---

### Post by hugmenot on 2009-12-09
I don&#8217;t agree this was social engineering. It was a script kiddie cobbling together a primitive trojan.

DEB packages can and do run scripts contained in them. They do this with administrator privileges. That means they can do anything to you system, there is no security checking in what they do whatsoever.

You&#8217;re lucky that this kid was so incompetent at it.

---

### Post by aysiu on 2009-12-09
> **hugmenot said:**
> I don’t agree this was social engineering. It was a script kiddie cobbling together a primitive trojan. Trojans rely on social engineering by definition.

---

### Post by NoaHall on 2009-12-09
> **hugmenot said:**
> I don’t agree this was social engineering. It was a script kiddie cobbling together a primitive trojan.

DEB packages can and do run scripts contained in them. They do this with administrator privileges. That means they can do anything to you system, there is no security checking in what they do whatsoever.

You’re lucky that this kid was so incompetent at it.

I think it was a test. Perhaps even done to show GNU/Linux could get a malware. The fact that we fixed it after about 20 minutes is irrelevant.

---

### Post by Ghost|BTFH on 2009-12-09
> **Enlightened Shadow said:**
> Just a quick question. Where in the repos is screensavers. You mentioned 80+ and I have never seen them.

I'm sorry Shadow, I ranted a bit earlier and that wasn't very polite of me.  Has nobody ever taught you how to use Synaptic Package Manager yet?

If you click on the search button, type in "screensaver" without quotes, one of the many things you will find is:

XScreenSaver and XScreenSaver-data which has details as follows:

[QUOTE=Synaptic]XScreenSaver is a modular screen saver and locker for X11,
containing more than 200 screen savers.[/QUOTE]

So, my count was a touch off. ^_^

But honestly, there's so many bloody programs in Linux, specifically in Debian builds and Ubuntu, that I just can't really fathom anyone going, "GOD! I really need XYZ and nobody's written a program to do that!!!"

The worst I've heard is, "I liked XYZ in Windows and nobody's written an EXACT BLOODY DUPLICATE OF IT so I don't have to relearn things."

When you are given pretty much everything you need at your fingertips, why search for more?

Cheers,
Ghost

---

### Post by lisati on 2009-12-09
> **aysiu said:**
> Trojans rely on social engineering by definition.

+1. The [horse]("http://en.wikipedia.org/wiki/Trojan_Horse") after which this particular form of malware was named is a good example. 

It looks like the stuff that prompted this group of threads has turned into a l[arge wooden rabbit]("http://en.wikipedia.org/wiki/Monty_python_holy_grail").

---

### Post by mivo on 2009-12-09
> **tinivole said:**
> In Windows you *may* think twice about downloading and running **OMgFreeWallpapers.exe** - so why would you think differently about the same but in a .deb format?

Because Linux advocates in their well-meaning missionary work focus heavily on how secure the OS is. In their attempts to portrait Windows as the OS where you magically contract viruses by merely looking at a page with the latest, uh, weather forcasts, can't do anything without malware crawling (and possibly nesting!) in the thermal paste of your computer and where at every corner lurks spyware just waiting to hijack your webcam to record when you pick your nose (or worse!) -- none of which could possibly happen in Linux --, they create a false sense of safety.

As a result, people become too trusting, quit applying common sense and just assume that nothing can touch them or their thermal paste.

---

### Post by ikt on 2009-12-09
> **NoaHall said:**
> I think it was a test. Perhaps even done to show GNU/Linux could get a malware.

Nobody has suggested linux can't be susceptible to malware, the same goes of OS X.

It is however more hardened and harder to do more damage without the user giving the malware root access, that is why we say nix is immune to viruses* and also to never run as root.

> A computer virus is a computer program that can copy itself and infect a computer.

---

### Post by aysiu on 2009-12-09
> **mivo said:**
> 
As a result, people become too trusting, quit applying common sense and just assume that nothing can touch them or their thermal paste. Well, I don't even think common sense figures into it this time. Veteran users know that a .deb for a theme looks dodgy (usually themes are compressed as .tar.gz or some other kind of tar file).

But if you're a new user and say "Hey, where can I get some good themes?" you're likely going to be pointed in the direction of [http://www.gnome-look.org](http://www.gnome-look.org), so why wouldn't you trust that site's downloads?

---

### Post by NoaHall on 2009-12-09
> **aysiu said:**
> Well, I don't even think common sense figures into it this time. Veteran users know that a .deb for a theme looks dodgy (usually themes are compressed as .tar.gz or some other kind of tar file).

But if you're a new user and say "Hey, where can I get some good themes?" you're likely going to be pointed in the direction of [http://www.gnome-look.org](http://www.gnome-look.org), so why wouldn't you trust that site's downloads?

Exactly my thoughts! :)

---

### Post by mivo on 2009-12-09
> **aysiu said:**
> But if you're a new user and say "Hey, where can I get some good themes?" you're likely going to be pointed in the direction of [http://www.gnome-look.org](http://www.gnome-look.org), so why wouldn't you trust that site's downloads?

I think what I meant to say is that a lot of (not yet experienced) Linux users have heard Linux/Windows security comparisons so often that there is no real awareness of any "dangers", so they don't really look into, or think about, ways how an outside source can damage their system.

They learn about malicious terminal commands (mostly thanks to the stickies and signatures here), but I never heard anyone mentioning that "threat" of .debs. It is "somehow" just accepted that they are safe by newer users (I'd say that the willingness to download .debs from unknown sites is also high among not yet experienced users.)

Information is the solution here. That's what I meant when I wrote earlier that in an indirect way this relatively harmless incident has good sides to it too. Not for the affected people, but for the community at large. This creates awareness and some sites may reconsider what formats they allow.

---

### Post by hugmenot on 2009-12-09
> **tinivole said:**
> 
In Windows you *may* think twice about downloading and running **OMgFreeWallpapers.exe** - so why would you think differently about the same but in a .deb format?

I think this may partially be due to them thinking a .deb is more like a .zip than like an .exe. It even has this cardboard boxes icon that .zip archives have.

---

### Post by joey-elijah on 2009-12-09
> **aysiu said:**
> Well, I don't even think common sense figures into it this time. Veteran users know that a .deb for a theme looks dodgy (usually themes are compressed as .tar.gz or some other kind of tar file).

But if you're a new user and say "Hey, where can I get some good themes?" you're likely going to be pointed in the direction of [http://www.gnome-look.org](http://www.gnome-look.org), so why wouldn't you trust that site's downloads?

That's really a good point - especially true because, in my experience, newbies gravitate to anything with a .deb because it's easier.

Themes do come in .deb's btw - ones that install GDM, Lock screens, themes, metacitys etc all at the same time so it's not foolish to not be suspicious a .deb as a theme.

---

### Post by hugmenot on 2009-12-09
> **aysiu said:**
> Trojans rely on social engineering by definition.

There was certainly deception involved, but in computer security parlance »social engineering« is normally used in distinction to conventional over-the-wire computerized exploits. As in, e.g.,  when I make a call to impersonate some authority, etc.

No actual social exchange took place here.

---

### Post by Ghost|BTFH on 2009-12-09
> **Enlightened Shadow said:**
> Anyone know what he means?

By the way, just so I'm never accused of not teaching anyone anything...

Go to _System -> Administration -> Synaptic Package Manager_

Click Search

Type in:

*xscreensaver*

From the list, select the following to install:

[B]xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra[/B]

and install them.

Now open a terminal and perform the following:
[I]
cd /usr/lib/xscreensaver
sudo cp * /usr/share/applications/screensaver[/I]

Now go to _System -> Preferences -> Screensaver_

Enjoy over 230 screensavers, without ever leaving the repositories.

Cheers,
Ghost

---

### Post by joey-elijah on 2009-12-09
> **mivo said:**
> I think what I meant to say is that a lot of (not yet experienced) Linux users have heard Linux/Windows security comparisons so often that there is no real awareness of any "dangers", so they don't really look into, or think about, ways how an outside source can damage their system.

They learn about malicious terminal commands (mostly thanks to the stickies and signatures here), but I never heard anyone mentioning that "threat" of .debs. It is "somehow" just accepted that they are safe by newer users (I'd say that the willingness to download .debs from unknown sites is also high among not yet experienced users.)

Information is the solution here. That's what I meant when I wrote earlier that in an indirect way this relatively harmless incident has good sides to it too. Not for the affected people, but for the community at large. This creates awareness and some sites may reconsider what formats they allow.

Doh i missed your reply, but yes you're totally bang-on-the-buck. I run an Ubuntu website/newsite (omgubuntu.co.uk) and whenever i post an application that needs to be compiled or only available as a standalone executable people scream for a .deb. 

The onus is on the user to trust the source, but newbies are lured into ubuntu with tales of a virus free future so don't think twice. I'll admit that up until this incident i probably was far more trusting of packages than i should've been. I think the key will be education and it's something i'll certainly be highlighting to my 10, 000 readers.

---

### Post by Zoot7 on 2009-12-09
> **Tipped OuT said:**
> Actually, pulling the power cord, and locking it up in an highly encrypted fireproof, bulletproof, and hacker proof safe... is the most secure system.
I've the most secure system possible!! 
A 15 year old 100MHz Pentium based system where the motherboard is blown and the old hard drive is dead, also the Power supply is useless on account of me removing several caps from it for a circuit a few years ago.

Try to infect that! ;)

---

### Post by aysiu on 2009-12-09
> **hugmenot said:**
> There was certainly deception involved, but in computer security parlance »social engineering« is normally used in distinction to conventional over-the-wire computerized exploits. As in, e.g.,  when I make a call to impersonate some authority, etc.

No actual social exchange took place here. A traditional social exchange doesn't need to take place.

Perhaps you want to try modifying [the Wikipedia entry on it](http://en.wikipedia.org/wiki/Social_engineering_(security)): > Social engineering is the act of manipulating people into performing actions or divulging confidential information. While similar to a confidence trick or simple fraud, the term typically applies to trickery or deception for the purpose of information gathering, fraud, or computer system access; in most cases the attacker never comes face-to-face with the victim. In any case, in the digital world, posting up a "theme" that's really a malicious script **is** a form social exchange.

---

### Post by doas777 on 2009-12-09
> **aysiu said:**
> A traditional social exchange doesn't need to take place.

Perhaps you want to try modifying [the Wikipedia entry on it]("http://en.wikipedia.org/wiki/Social_engineering_%28security%29"):  In any case, in the digital world, posting up a "theme" that's really a malicious script **is** a form social exchange.

so where do you draw the line between a booby trapped download, an a drive-by exploit coming from a banner add on cnn.com, or any other legit website?

---

### Post by bodhi.zazen on 2009-12-09
> **doas777 said:**
> so where do you draw the line between a booby trapped download, an a drive-by exploit coming from a banner add on cnn.com, or any other legit website?

Social engineering is where somebody gets you to take a specific action, such as installing a deb or running a script as root. The exploit has no way to urn without user intervention.

The second, drive by exploit, is where there is a hole in the code and no action on the users part is required. The exploit runs without user intervention (viewing a web site is not a user intervention as one should not exptect ot have their systems compromised simply by viewing a document or web site).

[http://www.ubuntu.com/usn/usn-821-1](http://www.ubuntu.com/usn/usn-821-1)

> If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program

So while both involve the user doing something, runing a script, running a script, or viewing a web site, in the first, social engineering, there is no flaw in the underlying code, nothing to patch.

In the second example, fix the code, fix the problem. Sure you can still tell people not to browse web sites, but there is a serious problem with the OS if simply viewing a web site and executing java script / flash results in a compromise of the OS.

---

### Post by nerdopolis on 2009-12-09
**samigina, **do you have that "theme" you mentioned?

I want to take a look at it, and investigate but it seems Gnome-look pulled the files to a theme called "Ninja Black" I don't know if thats the one or not.

---

### Post by hugmenot on 2009-12-09
I mainly brought this up because I felt labeling it as »social engineering« felt like an attempt to exculpate Ubuntu from this incident. (a la, »not a problem with Ubuntu, it was the user&#8217;s own fault«).

While I agree that the distribution per se was not exploited I think it is an effect of the habits and the recommendations in the Ubuntu community, in particular this forum, that makes people not hesitate and think when they install stuff from random sources and enter their sudo password. 

It&#8217;s all sudo here, sudo there, install that .deb, add that PPA, etc. 

Of course the moderators try to raise awareness by sometimes posting stickies with warnings, and the installation programs themselves usually warn not to trust software from strangers. But when you customize the hell out of your Ubuntu on a daily basis then your threshold of caution gets lowered naturally.

This is comparable to the Windows world where you get spammed with massive amounts of warning dialogs that you just blindly click away after a while.

---

### Post by aysiu on 2009-12-09
> **hugmenot said:**
> I mainly brought this up because I felt labeling it as »social engineering« felt like an attempt to exculpate Ubuntu from this incident. (a la, »not a problem with Ubuntu, it was the user&#8217;s own fault«).

While I agree that the distribution per se was not exploited I think it is an effect of the habits and the recommendations in the Ubuntu community, in particular this forum, that makes people not hesitate and think when they install stuff from random sources and enter their sudo password. Well, it is an attempt (and I hope a successful one) at exculpating the Ubuntu **operating system** from blame.

With regard to this incident there is, in fact, not a problem with Ubuntu, the software.

But you are absolutely correct in saying that the community is to blame for this. People (I am guilty of this as well) frequently recommend new users go to [http://www.gnome-look.org](http://www.gnome-look.org) to get themes. No one has ever said "Be careful what you download there, though, since anyone can upload a theme without it being properly vetted."

Sure, I've seen occasional vague warnings about "Only the official repositories can be trusted" and yet there are tutorials all over the place saying "Just download this .deb and double-click it" or "Just add this repository to your /etc/apt/sources.list."

I don't think there's much that can be done, though, except to see how things go. Truth be told, if there aren't that many trojans out there, it seems hollow to warn people against trojans. And when there are many trojans, it seems less hollow. The community has always acknowledged the possibility of trojans being created for Linux. It just seemed silly to harp on that possibility without it actually happening. More and more, though, it will happen. And, as it does, the community's emphasis in its warning will be stronger, and it will also be less hollow or disingenuous.

---

### Post by derrick81787 on 2009-12-09
I just came from here [http://ubuntuforums.org/showthread.php?t=1349678&page=15](http://ubuntuforums.org/showthread.php?t=1349678&page=15) and haven't read all of this new thread yet, but someone on the previous thread had a good point.  If this guy wouldn't have been lazy and would have actually created a working screensaver to go along with his package, he might not have ever been caught (at least not for a long while).  This could have caused some real damage, and the community should be aware of things like this.

It may have been the user's fault, but there's something to be said for the fact that it came from a site that most of us trust.  It's not necessarily gnome-looks' fault, but users just need to be aware that they should inspect .deb files closely when they download them from the net, no matter where they got them from.

---

### Post by HappyFeet on 2009-12-09
I installed a skin for VLC which rendered it useless. After much time spent purging, deleting config files, and any file associated with vlc, I could never get vlc to work right again. Even a different version would not work. A fresh install was needed to get back my beloved vlc. It is the last time I do anything outside of the repos.

---

### Post by hwttdz on 2009-12-09
I feel the goal of the operating system is to do what the user tells it to.  This user downloaded a file and ran it as root successfully executing it's contents.  This is the correct behavior for the OS (i.e. failure to install and execute contents of the package would have been a bug).  

Yes the user was misled as to what the code was doing.  There are a few possible solutions to this sort of problem, first is looking at the code and knowing what it does, which is possible thanks to the open source nature of linux/gnu/ubuntu, in this case the system is as safe as the user is knowledgable.  A second solution is trusting certain sources of code, in this case the system is as safe as the source is worthy of trust (or perhaps as safe as far as the user is not deceived into giving trust). 

Any malware/"virus"/trojan which requires sudo permissions is either capitalizing on the users lack of knowledge or misplaced trust.  And it is not part of the operating system to give the user knowledge or tell the user who to trust (it's a nice added value).   

The OS allows a user to do that for which the user has permissions (being too permissive is the admins fault).  And the OS allows the admin to do _ANYTHING_.  So if you're admin and you're not confident in your knowhow or in the reputability of the source don't give it root permissions. 

So in the end 
1) this wasn't a failing to the system
2) a system (excepting real security holes, such as buffer overflow, security escalation) is as secure as the admin is decievable, either through misplaced trust or lack of knowledge.

It's not productive to get angry at the computer for doing what you told it to do.  (I ran "rm *.ogg" in my Music folder yesterday and spent the rest of the night ripping CD's, that's not the system's fault, that's mine.  It was a typo in a rename command if you're curious.).

Windows was annoying to me when I used it not because it had security holes (I feel I was knowledgeable enough to avoid executing stupid code, block execution of untrusted scripts and whatnot).  But because it was hard to make it do what I wanted it to.  Hosting a website was harder, compiling code was harder, the command line was annoying (haven't used the new one so I make no claims about that), updating was more annoying, and I wouldn't dream of running a cluster.  If you actually visit update.microsoft.com fairly regularly windows patches the os itself.  I just found this harder than "update && upgrade", especially because I would then have to go update firefox, and itunes, and...  Of course it's a nice benefit that I feel linux has fewer legitimate holes, independent of my doing stupid things occasionally.

---

### Post by Elfy on 2009-12-09
Either keep the conversation civil or I will close the thread.

Thank you.

---

### Post by Georgia boy on 2009-12-09
So far I've only had done the ppa for Pidgin from their site when Yahoo was changing their stuff around. No downloads from other sites. Everything I need has come with Ubuntu and I find what I want in the Repros. Ghost brought up something on the gnome bit. Is it gnome-look.org or art.gnome.org/themes that everyone should be going to when looking for themes? Hell, I use my own pictures of things for wallpaper etc. Haven't even used any of the screensavers yet. Checked them out but just didn't care to install any of them. Granted I have seen some great looking themes elsewhere but just wasn't interested in installing them. According to Ghost he's found all of those in the repros. Saves even more trouble unless I decide to do some more of my own for myself. But I did notice when you go to a lot of sites there seems to usually be a choice of .deb or tar for downloading. So, what is the better of the two? Also seems from what I've been reading that the deb is the easiest to download?
Lets say that I want to get a program or update one we already have in the system. What do I want to use?

Tom

---

### Post by Ghost|BTFH on 2009-12-09
> **Georgia boy said:**
> So far I've only had done the ppa for Pidgin from their site when Yahoo was changing their stuff around. No downloads from other sites. Everything I need has come with Ubuntu and I find what I want in the Repros. Ghost brought up something on the gnome bit. Is it gnome-look.org or art.gnome.org/themes that everyone should be going to when looking for themes?

Tom

Hey Tom, just a quick note - I posted a simple how-to in the absolute beginner section that guides a person step-by-step (hopefully in clear and simple language) on installing a huge selection of screensavers and a nice variety of themes.

If they're not enough...when you click on **System -> Preferences -> Appearance**, it has an option in the lower left "_Get more themes online_" When you click on that, it takes you to art.gnome.org, where you will find - zero screensavers.  Also, the themes found there, are in tar.gz format, and are recognized by the system when you go to download them as theme files and you are asked if you would like to open it with theme-installer (default).

If you're interested in the article I wrote, please feel free to take a look, it's over at [http://ubuntuforums.org/showthread.php?t=1350746](http://ubuntuforums.org/showthread.php?t=1350746)

Cheers,
Ghost

---

### Post by Georgia boy on 2009-12-09
Thanks Ghost! I'll be checking that out. Wondering though about what would be better to use when going to a trusted site like OpenOffice.org or something else like that. Deb or Tar? Which would be better to use on a site like that?
Kind of confusing when I read throughout the forums on that.

Tom

---

### Post by NoaHall on 2009-12-09
> **Georgia boy said:**
> Thanks Ghost! I'll be checking that out. Wondering though about what would be better to use when going to a trusted site like OpenOffice.org or something else like that. Deb or Tar? Which would be better to use on a site like that?
Kind of confusing when I read throughout the forums on that.

Tom

On proper, safe sites, it doesn't matter - .deb really, it's easier.

---

### Post by h!v on 2009-12-09
1. There's plenty of deb files around the web. Many got installed through (supposedly)dpkg. Including mine I guess.
How about coming up with command to grep/cat out manually installed packages? dpkg should do that, but man points me to nowhere tbh.

I'd rather track down debs and have a look into them.

2. How about proposing Cannoncial to work on a simple heuristics patched into dpkg? dpkg tools(gencheck afaik) have some sort of this.
I'd see that, in next LTS, rather than completely bonkers "uTunes".

Cheers.

[size=1][COLOR="White"]Forgot FOSS community doesn't like when someone points out their's flaws to them. Years passed nothing changed.[/COLOR][/size]

---

### Post by Ghost|BTFH on 2009-12-09
> **h!v said:**
> 1. There's plenty of deb files around the web. Many got installed through (supposedly)dpkg. Including mine I guess.
How about coming up with command to grep/cat out manually installed packages? dpkg should do that, but man points me to nowhere tbh.

I'd rather track down debs and have a look into them.

2. How about proposing Cannoncial to work on a simple heuristics patched into dpkg? dpkg tools(gencheck afaik) have some sort of this.
I'd see that, in next LTS, rather than completely bonkers "uTunes".

Cheers.

That's a solid idea, however - there's a ton of programs out there that could be considered "unsafe" if they were misused.  I think the key issue would be what would you set it up to check?  Granted, the times you'd use dpkg wouldn't be that often, so it really wouldn't cause much of an issue for an end user.

As for locating manually installed packages in your system, you can do so with a little Synaptic Package Manager magic...

System -> Administration -> Synaptic Package Manager

Click Origin to see where packages have come from.

Click Status -> Installed (Local or Obsolete) to see what you manually installed.

For example, on my system, Status -> Installed shows me:

linux-image-2.6.28-17-generic (the previous kernel)
virtualbox (which I personally installed from sun's website)

Both of which I can manipulate from there.

Hope that helps!

Cheers,
Ghost

---

### Post by sisco311 on 2009-12-09
> **h!v said:**
> Forgot FOSS community doesn't like when someone points out their's flaws to them. Years passed nothing changed.


There are plans to establish and convey a trust level for software in PPAs, and let users easily add PPAs within the Software Center & encourage developers/package maintainers to use the PPA repose.

[https://wiki.ubuntu.com/SoftwareCenter]("https://wiki.ubuntu.com/SoftwareCenter")

---

### Post by h!v on 2009-12-09
> **Ghost|BTFH said:**
> That's a solid idea, however - there's a ton of programs out there that could be considered "unsafe" if they were misused.  I think the key issue would be what would you set it up to check?  Granted, the times you'd use dpkg wouldn't be that often, so it really wouldn't cause much of an issue for an end user.

As for locating manually installed packages in your system, you can do so with a little Synaptic Package Manager magic...

System -> Administration -> Synaptic Package Manager

Click Origin to see where packages have come from.

Click Status -> Installed (Local or Obsolete) to see what you manually installed.

For example, on my system, Status -> Installed shows me:

linux-image-2.6.28-17-generic (the previous kernel)
virtualbox (which I personally installed from sun's website)

Both of which I can manipulate from there.

Hope that helps!

Cheers,
Ghost

Helps but not by a lot. Staying in terminal would be more efficient for me. Just my nagging.

For the most part dpkg is issued, in howtos/commands for installing third party packages.

For heuristics part. That's not our problem to resolve, either discuss. Too long way to come, to fear about false positives too. After all it's only idea anyway.
Ubuntu has been pointed out as Vista and not-so-secured distro few times. I'd see Canonical teaming up with some of the security companies when they're trying to push Ubuntu to the masses. Neglecting security is not the best bet for any OS.


[COLOR="White"]sisco311 Look at edit reason for the post you quoted. Insult, ehh my boorish European mouth.[/COLOR]

---

### Post by bodhi.zazen on 2009-12-09
> **h!v said:**
> Neglecting security is not the best bet for any OS.

Exactly who do you think is neglecting security ? Certainly you are not Canonical implying I hope.

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

---

### Post by aysiu on 2009-12-09
> **h!v said:**
> I'd see Canonical teaming up with some of the security companies when they're trying to push Ubuntu to the masses. What would be an example of a "security" company. Do you think publishers of "antivirus" (placebo) software actually make people's computers secure?

---

### Post by h!v on 2009-12-09
> **bodhi.zazen said:**
> Exactly who do you think is neglecting security ? Certainly you are not Canonical implying I hope.

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

Your hopes come true!

> **aysiu said:**
> What would be an example of a "security" company. Do you think publishers of "antivirus" (placebo) software actually make people's computers secure?

Surely none of the "antivirus" company have ever worked on heuristics. Which is of course easiest to implement. Last but not least best bet to work on something is to neglect any possibility of getting a help from anyone in anything.

When exactly do we stop bulling each other and using sarcastic tone?

Cheers.

---

### Post by bodhi.zazen on 2009-12-09
> **h!v said:**
> When exactly do we stop bulling each other and using sarcastic tone?

Cheers.

Whenever you are ready. I think you will find the staff is quite knowledgeable about security.

---

### Post by Ghost|BTFH on 2009-12-09
> **h!v said:**
> Helps but not by a lot. Staying in terminal would be more efficient for me. Just my nagging.

For the most part dpkg is issued, in howtos/commands for installing third party packages.

For heuristics part. That's not our problem to resolve, either discuss. Too long way to come, to fear about false positives too. After all it's only idea anyway.
Ubuntu has been pointed out as Vista and not-so-secured distro few times. I'd see Canonical teaming up with some of the security companies when they're trying to push Ubuntu to the masses. Neglecting security is not the best bet for any OS.

First, I believe there are ways to check into what I talked about using apt-get instead of Syn.  I'm not a major CLI guy, I like my GUI. :)

Secondly, it's never too early to talk about false positives and how to prevent them if we were going to discuss a protection of this magnitude.  After all, if you start the ball rolling on a subject like this, it never stops.

As for the security of Ubuntu, I would have to disagree with you on this point - It was put up against Vista Ultimate Edition and Mac's latest OS in a competition awhile back.  If you hacked one of the laptops with those OSes on them at the competition, you won the laptop.

If I recall correctly, none of them fell the first day, but none were allowed to have any normal Internet connectivity.  When that was allowed on the second day, Vista fell first within 6 hours, I'm wanting to say, and then Mac that evening, if I recall.

Ubuntu didn't.  Nobody took home the Ubuntu laptop, because out of a major convention of hackers, nobody got access to it.

The #1 way into a Linux box is to sit down in front of it.  Short of that, you have to fool the person sitting in the chair in front of it.

Otherwise, good luck.  I'd call that pretty secure.  The only issues you could have with it are ID-10-T (aka idiot behind the keyboard) or PEBKAC (Problem Exists Between Keyboard And Chair)

Cheers,
Ghost

---

### Post by Hallvor on 2009-12-10
If you use a mainstream distro and only install trusted and digitally signed packages from the repositories you are about as safe as you can be on the internet. There are more than 20.000 packages to choose from. So there is no sane reason for a user to install a lot of debs that could be uploaded by any random cracker. But if you do, you remove a couple of layers of extra security. Installing a deb from the internet is like giving a total stranger the keys to your home. Sure, he may be a nice guy but he could also be a criminal.

This whole urge to point, click, download and install files from the web is a very close relative to the Windows way of point, click, download and install files by clicking next a few times. Installing files that way is a good way to bork and compromise your system &#8211; whatever comes first.

The biggest variable when it comes to OS security is the user.

---

### Post by mivo on 2009-12-10
> There are more than 20.000 packages to choose from. So there is no sane reason for a user to install a lot of debs that could be uploaded by any random cracker.

It is a sane reason to want to use up-to-date versions of software and not the old, feature-lacking "stable" versions that are often found in the repositories of the mainstream distros. It's not uncommon for FOSS applications to evolve relatively fast (vs. commercial applications). This isn't a problem for a rolling release distro (or for Windows), but with those six-month release distros, there's a good chance you'll want to use a software version that isn't in the repository. (Chrome beta, Thunderbird 3.0, latest video card drivers, etc.)

---

### Post by Hallvor on 2009-12-10
If they need all that bleeding edge stuff, Ubuntu is hardly a good distro for them anyway. It is only bleeding edge for a very short time. 

If they like their OS on the edge, a rolling release distro would be a much better choice, imho.

---

### Post by aysiu on 2009-12-10
> **Hallvor said:**
> If you use a mainstream distro and only install trusted and digitally signed packages from the repositories you are about as safe as you can be on the internet. There are more than 20.000 packages to choose from. So there is no sane reason for a user to install a lot of debs that could be uploaded by any random cracker. But if you do, you remove a couple of layers of extra security. Installing a deb from the internet is like giving a total stranger the keys to your home. Sure, he may be a nice guy but he could also be a criminal. When it comes to themes, the repositories selection is actually quite meager. That's why most new users are referred to [http://www.gnome-look.org](http://www.gnome-look.org) to get themes.

---

### Post by lykwydchykyn on 2009-12-10
The hype is all about "Ubuntu gots malware", and so many people are playing damage control by talking about how you shouldn't install software from untrusted sites.

That's missing the real point, IMHO.  The real point is that opendesktop.org is no longer a trusted site.  That's bad.

As I mentioned before, KDE 4 is integrated with its opendesktop.org sites (kde-look.org and kde-apps.org) seamlessly in the desktop environment.  This means I click a dialog and a list comes up in a dialog of cool stuff I can install into KDE.  No browser involved.

I don't know if GNOME 3 is planning similar functionality.  Anyone know?

Either way, as far as I can see, opendesktop.org is one of the most official-unofficial sites for Linux desktop content in existence.  It has the implicit trust of the community.  And now we find it's not trustworthy.  Pontificate all you want about not downloading stuff from "unofficial" repositories and strange websites, but when I can't trust a site that my desktop environment has hardcoded integration with, there's a real problem.

---

### Post by Tristam Green on 2009-12-10
By the way, I tried to install this on Windows 7, and I didn't get any stinky virus or trojan horse or redirections.

By that logic, it is blatantly obvious who the winner is here.

---

### Post by aysiu on 2009-12-10
> **lykwydchykyn said:**
> The hype is all about "Ubuntu gots malware", and so many people are playing damage control by talking about how you shouldn't install software from untrusted sites.

That's missing the real point, IMHO.  The real point is that opendesktop.org is no longer a trusted site.  That's bad. The problem here is too many extremes and too little balance.

**Extreme 1**
See? Ubuntu is just as susceptible to malware as Windows. It isn't safe! It isn't safe! Anything could happen. Argh!

**Extreme 2**
This is nothing. Nothing's wrong. It's the user's fault. Don't go to untrusted sites. Duh!

What we really need is...
**Balance**
Social engineering has always been a potential threat. This particular manifestation is worrisome because it is on a site that isn't normally shady or dodgy. _New users regularly get referred to Gnome Look to get themes._

---

### Post by Zoot7 on 2009-12-10
> **mivo said:**
> It is a sane reason to want to use up-to-date versions of software and not the old, feature-lacking "stable" versions that are often found in the repositories of the mainstream distros. It's not uncommon for FOSS applications to evolve relatively fast (vs. commercial applications). This isn't a problem for a rolling release distro (or for Windows), but with those six-month release distros, there's a good chance you'll want to use a software version that isn't in the repository. (Chrome beta, Thunderbird 3.0, latest video card drivers, etc.)
Well put. That is a problem with Linux in general IMO, the dependency issues requiring you to be fairly up to date in the distro you use if you want to use all the latest software. One such example is Vlc under Hardy; the latest release you can install is 0.99a, if you try installing the newer versions or try to build them from source, you'll run into dependency issues. And the dependencies aren't in the repos, sure you could go and download all of those, but you'll almost definitely find that they have dependencies too.
This is just not something that's a problem with Windows or the rolling release distros like Arch.

> **Tristam Green said:**
> By the way, I tried to install this on Windows 7, and I didn't get any stinky virus or trojan horse or redirections.

By that logic, it is blatantly obvious who the winner is here.
In *this* particular case, yes. Key word being this. ;)

---

### Post by aysiu on 2009-12-10
> **Zoot7 said:**
> Well put. That is a problem with Linux in general IMO, the dependency issues requiring you to be fairly up to date in the distro you use if you want to use all the latest software. One such example is Vlc under Hardy; the latest release you can install is 0.99a, if you try installing the newer versions or try to build them from source, you'll run into dependency issues. And the dependencies aren't in the repos, sure you could go and download all of those, but you'll almost definitely find that they have dependencies too.
This is just not something that's a problem with Windows or the rolling release distros like Arch. I've found that to be a problem for only a tiny minority of computer users (people who generally fall into the "power user" category - meaning folks who are most likely to be asked for computer help from family and friends than to ask for it of family and friends).

Most people don't really care about the latest software. They just want to get stuff done. So in the long-term (i.e., if consumer, and not server or embedded, Linux takes off), it won't really be a problem at all.

It's **currently** a problem, because right now the people most likely to use consumer Linux are ex-Windows power users.

But, as you said, there are also rolling release distros (Debian, Arch, PCLinuxOS) for those who really need the latest software right now (and not six months from now).

---

### Post by Zoot7 on 2009-12-10
> **aysiu said:**
> Most people don't really care about the latest software. They just want to get stuff done. So in the long-term (i.e., if consumer, and not server or embedded, Linux takes off), it won't really be a problem at all.
Indeed they don't. 
Even citing myself as an example; a lot of the applications I need on a day to day basis for both college and work are a couple of years old now, and I don't see any reason to upgrade them because they work fine as is now.
For example my home recording software suite is nearly 5 years old now, but it still works beautifully for what I want of it.
(Meant to add that into my last post, you beat me to it though)

> **aysiu said:**
> It's **currently** a problem, because right now the people most likely to use consumer Linux are ex-Windows power users.
Very good point. This was probably the main reason I abandoned Debian Stable in favour of Ubuntu.

---

### Post by aysiu on 2009-12-10
I'm actually one of these power users, and I learned my lesson last month.

At work, I do a little bit of work with PDFs (in Windows, not Ubuntu). When I had the opportunity to "upgrade" my Adobe Acrobat Professional from 8 to 9, I took it, and suddenly the interface was terrible, and it seemed some backward compatibility had been stripped out. So I had to downgrade back to 8.

The latest is not always the greatest. Power users always like to try the latest, though, anyway. It's some sort of weird compulsion.

The vast majority of users I know have (unfortunately) outdated and unpatched versions of Internet Explorer or Firefox, because they don't want to be bothered to install updates. So if Ubuntu suddenly got more third-party support, these people would be perfect for Ubuntu. Stick with LTS. Stick with old software. Still get security updates all in one place, though.

---

### Post by lykwydchykyn on 2009-12-10
> **aysiu said:**
> The problem here is too many extremes and too little balance.

**Extreme 1**
See? Ubuntu is just as susceptible to malware as Windows. It isn't safe! It isn't safe! Anything could happen. Argh!

**Extreme 2**
This is nothing. Nothing's wrong. It's the user's fault. Don't go to untrusted sites. Duh!

What we really need is...
**Balance**
Social engineering has always been a potential threat. This particular manifestation is worrisome because it is on a site that isn't normally shady or dodgy. _New users regularly get referred to Gnome Look to get themes._

Yes.  Exactly what I was trying to say, except I have a head cold and can't put words together coherently.

---

### Post by Zoot7 on 2009-12-10
> **aysiu said:**
> I'm actually one of these power users, and I learned my lesson last month.

At work, I do a little bit of work with PDFs (in Windows, not Ubuntu). When I had the opportunity to "upgrade" my Adobe Acrobat Professional from 8 to 9, I took it, and suddenly the interface was terrible, and it seemed some backward compatibility had been stripped out. So I had to downgrade back to 8.

The latest is not always the greatest. Power users always like to try the latest, though, anyway. It's some sort of weird compulsion.
Skype 4.0 was an example for me (I've to use Windows for Skype, i find the windows version preforms much better behind a http proxy than the linux one). I played with for about 20 minutes and then downgraded back to 3.8.

> **aysiu said:**
> So if Ubuntu suddenly got more third-party support, these people would be perfect for Ubuntu. Stick with LTS. Stick with old software. Still get security updates all in one place, though.
Agreed. My college is one such example of that. There's somewhere in the region of 400-500 PCs used for open access labs which are used for internet access alone around the campus, all with unmaintained, out of date copies of XP installed, along with dated software (IE6 for example).
The best thing they could do there IMO would to put something tried, tested and solid such as Red Hat on them and simply have a big icon "Firefox Web Browser" on the Desktop. It's a bit of a no-brainer considering the vast majority of the servers there are running Red Hat anyway.
I digress though..

---

### Post by gdp77 on 2009-12-10
I don't have the time to read the whole thread. I have only read some posts claiming that ubuntu is not safe, like windows blah blah blah.

1) It's not ubuntu's fault if the user downloads debs from untrusted sites, then executes them, then gives them root privileges. ( In addition to that, it's not ubuntu's fault if the user sets the pc on fire... )

2) Only totally ignorants with root privileges will fall victims of that kind of malware

3) No matter how many companies (a.k.a MS) target ubuntu with malware, no matter how many 14 year old no lifers write malicious scripts, THEY WILL NOT SUCCEED creating a virus that can reproduce itself. Only the ignorants will manage to contaminate their systems because of their ignorance, but there is no way to have a virus outburst in linux. Trojans and malware is one thing, a virus outburst is another.

---

### Post by aysiu on 2009-12-10
> **gdp77 said:**
> 
1) It's not ubuntu's fault if the user downloads debs from untrusted sites, then executes them, then gives them root privileges. ( In addition to that, it's not ubuntu's fault if the user sets the pc on fire... )

2) Only totally ignorants with root privileges will fall victims of that kind of malware So now Gnome Look is an untrusted site? Don't read the entire thread. Just read the last couple of pages, please.

---

### Post by hugmenot on 2009-12-10
> **gdp77 said:**
> 
2) Only totally ignorants with root privileges will fall victims of that kind of malware


Not true. There are ways to install trojans in a local user account. It&#8217;s even easier.

The most recent example was the executability of .desktop files. This was recognized as an issue by the Gnome developers. There are various ways to start a malicious program at each login: .profile, XDG autostart, etc. pp.

Almost everything that computer criminals want to achieve does not require root privileges at all. Think identity theft or network attacks like in this case.

> 
3) No matter how many companies (a.k.a MS) target ubuntu with malware, no matter how many 14 year old no lifers write malicious scripts, THEY WILL NOT SUCCEED creating a virus that can reproduce itself. Only the ignorants will manage to contaminate their systems because of their ignorance, but there is no way to have a virus outburst in linux. Trojans and malware is one thing, a virus outburst is another.
That has been shown to be feasible in the past. And it may well happen in the future. But old-fashioned viruses are not where the money is for criminals. There is more incentive for other types of exploits.

---

### Post by hwttdz on 2009-12-10
So while we agree it is terrible that people fall for the 419 scam, some people insist on blaming western union.  

On the other hand it would be nice if gnome-look submissions were somehow vetted.  But that's an independent problem from any holes in the OS.

---

### Post by doas777 on 2009-12-10
> **gdp77 said:**
> 
3) No matter how many companies (a.k.a MS) target ubuntu with malware, no matter how many 14 year old no lifers write malicious scripts, THEY WILL NOT SUCCEED creating a virus that can reproduce itself. Only the ignorants will manage to contaminate their systems because of their ignorance, but there is no way to have a virus outburst in linux. Trojans and malware is one thing, a virus outburst is another.

please keep in mind, a virus by definition uses*** application software vulnerabilities*** to act badly. a Worm on the otherhand, uses ***system software vulnerabilities*** to spread, but contains it's own code for most bad actions.

so all it takes to make a virus, is to find an app with an appropriately exploitable vulnerability. a worm however would require a special kind of vulnerability within linux itself.

more info here:
[http://www.google.com/search?q=virus+vs+worm&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=virus+vs+worm&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Frak on 2009-12-10
> **gdp77 said:**
> 3) No matter how many companies (a.k.a MS) target ubuntu with malware, no matter how many 14 year old no lifers write malicious scripts, THEY WILL NOT SUCCEED creating a virus that can reproduce itself. Only the ignorants will manage to contaminate their systems because of their ignorance, but there is no way to have a virus outburst in linux. Trojans and malware is one thing, a virus outburst is another.

Just like Windows, the propagation of malware will be through the ignorant. It's easier to infect within the system than it is to attack it from the front. Antivirus 2009 for instance.

Also

> **gdp77 said:**
> 3) No matter how many companies (a.k.a MS) target ubuntu with malware

It's tin-foil hat day! :popcorn:

---

### Post by NoaHall on 2009-12-10
> **Frak said:**
> Just like Windows, the propagation of malware will be through the ignorant. It's easier to infect within the system than it is to attack it from the front. Antivirus 2009 for instance.

Also



It's tin-foil hat day! :popcorn:

I was wondering when you'd turn up again with your kind and caring responses :rolleyes:

Anyway, at the moment, we are quite a wise community, and can quickly solve these problems :)

---

### Post by Frak on 2009-12-10
> **NoaHall said:**
> I was wondering when you'd turn up again with your kind and caring responses :rolleyes:

Anyway, at the moment, we are quite a wise community, and can quickly solve these problems :)
Yeah, you do that.

---

### Post by NoaHall on 2009-12-10
> **Frak said:**
> Yeah, you do that.

Tin foil hat - go!
Automated code searching eyes - go!
Voice control text editing - go!

All ready. Just hit me ;)

---

### Post by Frak on 2009-12-10
> **NoaHall said:**
> Tin foil hat - go!
Automated code searching eyes - go!
Voice control text editing - go!

All ready. Just hit me ;)
lol

[http://www.youtube.com/watch?v=KyLqUf4cdwc](http://www.youtube.com/watch?v=KyLqUf4cdwc)

---

### Post by NoaHall on 2009-12-10
> **Frak said:**
> lol

[http://www.youtube.com/watch?v=KyLqUf4cdwc](http://www.youtube.com/watch?v=KyLqUf4cdwc)

My cousin made a macro for typing code in Dreamweaver. He's a little lazy. ;)

---

### Post by Frak on 2009-12-10
> **NoaHall said:**
> My cousin made a macro for typing code in Dreamweaver. He's a little lazy. ;)
Meh, I use snippets religiously.

---

### Post by bilalakhtar on 2009-12-11
> **gdp77 said:**
> I don't have the time to read the whole thread. I have only read some posts claiming that ubuntu is not safe, like windows blah blah blah.

1) It's not ubuntu's fault if the user downloads debs from untrusted sites, then executes them, then gives them root privileges. ( In addition to that, it's not ubuntu's fault if the user sets the pc on fire... )

2) Only totally ignorants with root privileges will fall victims of that kind of malware

3) No matter how many companies (a.k.a MS) target ubuntu with malware, no matter how many 14 year old no lifers write malicious scripts, THEY WILL NOT SUCCEED creating a virus that can reproduce itself. Only the ignorants will manage to contaminate their systems because of their ignorance, but there is no way to have a virus outburst in linux. Trojans and malware is one thing, a virus outburst is another.

Well, Thats true.:popcorn:

---

### Post by Frak on 2009-12-11
I just rated nearly 20 GigaDurdens!

---

### Post by chillicampari on 2009-12-11
I'll just leave this here:

**The Malware Problem (and a Solution) - Amarok Blog**
[http://amarok.kde.org/blog/archives/1153-The-Malware-Problem-and-a-solution.html](http://amarok.kde.org/blog/archives/1153-The-Malware-Problem-and-a-solution.html)

---

### Post by lisati on 2009-12-11
> **Frak said:**
> I just rated nearly 20 GigaDurdens!

Wut? :confused:

---

### Post by Chronon on 2009-12-11
> **mivo said:**
> 
They learn about malicious terminal commands (mostly thanks to the stickies and signatures here), but I never heard anyone mentioning that "threat" of .debs. It is "somehow" just accepted that they are safe by newer users (I'd say that the willingness to download .debs from unknown sites is also high among not yet experienced users.)

I agree that this does offer a chance to clarify some of the pedagogy with regard to educating new users, though I'm not sure how widespread this idea about the safety of .debs really is.  I identified pretty early on that trusted repositories is a crucial and necessary ingredient in the security model here.  I was certainly never led to believe that random .debs should be trusted or that they can't be harmful.

---

### Post by rookcifer on 2009-12-11
> **Techsnap said:**
> If you're using UAC in Windows Vista/7 or a User Profile on Windows NT/2K/XP it's going to want your permission.

Yeah and it's going to want your permission for everything and annoy the hell out of you.  This is because there was no such concept as multi-user in the Windows world until the 2000's (and it hasn't even caught on in desktop Windows space until the last couple years).  As a result, developers still write their code to require admin access.   M$ is *way* behind the curve here.  I tried running my XP box under a LUA, and found it impossible for most software to run.  It is a PITA.  Win 7 is better, but most users will still run as admin.

Linux, on the other hand, has been fully multi-user from day one (1991) and Unix, it's mother, has been multi-user since the 1970's.  Even today, with Win 7, Windows is still not as functional of a multi-user system as the *nixes.  Case in point: try to log more than one user in at the same time. You can't do it with Windows without third party hacks.

What we have in the news here is a social engineering attack that would succeed with any ignorant user, no matter the OS.  You could be using some super secret NSA multi-level secured OS and still fall victim to something like this.  The advantage Linux has over 'doze is a strong tradition of multi-user security and privilege separation as well as open code and signed software repositories.  The privilege separation makes drive-by download infections (meaning you surf to a porn site and are pwned, like happens often on Windoze) unheard of and very difficult to pull off.

Basically, wake me up when we see a Conficker for Linux (17 years and still waiting).

P.S.  I see lots of ignorant people here say things like "See, this proves if Linux gets a bigger market share it will be plagued by viruses" and "Linux is security through obscurity."  This is the favorite line of Windows shills and AV companies.  It is, in fact, plain wrong.  Rick Moen can explain it better than me, so I will direct you to his very incisive and scintillating [article]("http://linuxmafia.com/~rick/faq/index.php?page=virus") on the matter.

---

### Post by mivo on 2009-12-11
> **rookcifer said:**
> P.S.  I see lots of ignorant people here say things like "See, this proves if Linux gets a bigger market share it will be plagued by viruses" and "Linux is security through obscurity."

Calling those who disagree with you "ignorant people" isn't helpful, especially if there is a point to the concerns they raise.

> This is the favorite line of Windows shills and AV companies.

So instead of the "Windows shills" and "AV companies" you would have us believe the Linux evangelists and zealots? Same thing, different packaging.

Aysiu made the best point in this thread: There is no room for extremes. It's about balance. There is no need for panic, and no constructive reason to deny the dangers.

---

### Post by clanky on 2009-12-11
It is disappointing that this has been moved to recurring discussions, surely something which has happened as recently as this can't be a recurring discussion?

I can only see that someone thought it was not a good idea to have a thread with "anti-linux" posts in the open, in fact the comments are not anti linux at all they are a wake up call to those who think that Linux is somehow ultra secure and that LinuxDoesn'tGetMalware(TM).

This thread should be in the open where people can see that security is and must be an issue for users of any OS.  Hiding it away is equivalent to sticking your fingers in your ears and shout LaLaLaLaLa I can't hear you at the top of your voice.

The only way to make **any** system secure is for users to be aware of what they are doing, and for this to happen people need to be educated, there are a lot of new Linux users on here who may not know what a .deb file is, but are able to blindly follow instructions on how to install one, these people need to be made aware that there are risks involved, for that reason could a mod / admin whoever please move this thread back to where it belongs?

---

### Post by Hallvor on 2009-12-11
Yes, this hardly belongs to the same category as "Does Ubuntu need antivirus?" or the umpteenth Arch thread.

---

### Post by mivo on 2009-12-11
> **Hallvor said:**
> Yes, this hardly belongs to the same category as "Does Ubuntu need antivirus?" or the umpteenth Arch thread.

Indeed, Arch doesn't use .debs. ;)

(Sorry, couldn't resist.)

---

### Post by clanky on 2009-12-11
> **tinivole said:**
> I disagree.

Everything that has happened here is not like it is an unknown possibility.
I recall having discussions on this type of happening almost a year back.

At the end of the day, this is not a bug, nor is this invalid behavour, and certainly is not a security hole - nor is it exploiting anything. All software is working as per design, and as such we can only assume that you are using it wisely.

In Windows you *may* think twice about downloading and running **OMgFreeWallpapers.exe** - so why would you think differently about the same but in a .deb format?

Complacency of users is the killer here - not the system. Therefore this is a non-issue as far as I'm concerned.

Sorry for not replying to this earlier, ship has been at sea.  I think you kind of missed the point of what I was saying. IT IS down to the complacency of users, as (if) Linux market share grows substantially there will be more and more complacent users.  

Anyone with half a brain can avoid viruses in Windows, the problem is that many windows users do not have the first clue what they are doing.  Apart from the fact that it is inherently more secure than windows the main reason that Linux is less susceptible to malware is that Linux users generally know a bit more about what they are doing.

If Linux became more popular there would be more clueless users who didn't know what they were doing and Linux would have to babysit them with more "are you sure" type pop-ups and more "user-proof" security measures.

There will be cries of "ZOMG I WANT MY FREEDUMZ" from some of the zealots, but the alternative is "security by obscurity".

---

### Post by rookcifer on 2009-12-11
> **clanky said:**
> Anyone with half a brain can avoid viruses in Windows, the problem is that many windows users do not have the first clue what they are doing.  

I disagree.  If this were true, then why do we have drive-by downloads on Windows?  Why can a pr0n site pwn your computer?  I consider myself computer saavy and I have had numerous malware infections (on Windows) simply by *browsing the web*.

> Apart from the fact that it is inherently more secure than windows the main reason that Linux is less susceptible to malware is that Linux users generally know a bit more about what they are doing.

That's one of several reasons, yes.

> If Linux became more popular there would be more clueless users who didn't know what they were doing and Linux would have to babysit them with more "are you sure" type pop-ups and more "user-proof" security measures.

And all we can do is keep telling newbs to only use the repositories.  

One thing that concerns me, however, is how easy it is to install .debs.  Nowadays it is point and click.  I miss the old days where, if it wasn't in the repos, you had to compile it. Since Ubuntu is the most popular distro, we will almost certainly see many rogue .deb websites pop-up.  There is little we can do to help newbs who give their root password to a rogue .deb.  Nothing except warn them.  Then again, there is nothing we can do to stop someone from dropping his PC off a cliff.  See where I am going?  

The truth is, this "malware" attack relies on social engineering.  There is no flaw here except with the user behind the keyboard.  There will always be an element of this on all OS's.  The people who keep saying "see we told ya so" are disingenuous because none of us "zealots" ever said Linux was immune from a user destroying *his own* system.

---

### Post by Ghost|BTFH on 2009-12-11
> **aysiu said:**
> When it comes to themes, the repositories selection is actually quite meager. That's why most new users are referred to [http://www.gnome-look.org](http://www.gnome-look.org) to get themes.

So, over 20 themes, each fully customizable with over 300,000 possible combinations for appearance is "quite meager"?

Holy carp.

Cheers,
Ghost

---

### Post by doas777 on 2009-12-11
> **Ghost|BTFH said:**
> So, over 20 themes, each fully customizable with over 300,000 possible combinations for appearance is "quite meager"?

Holy carp.

Cheers,
Ghost

we heard you about 6 pages back. thanks for the tip. the repos still don't have my custom darklooks gtk though.

---

### Post by benj1 on 2009-12-11
i have to say im quite surprised that gnome-look doesn't have any checks against this kind of thing, although now i know im more surprised it didn't happen sooner.

im also gratified by the number of people taking this seriously, in windows land this wouldn't register as a blip.

regarding everyone selling linux as 'imperious to viruses', i think the problem is that many less experienced users equate 'virus' with anything that can do harm to your computer, regardless of how it does it. Yes *technically* linux is very resistant to viruses, not of course trojans, but in the average users mind this means they are invulnerable. Perhaps we should focus on clarifying this misunderstanding, you can have the strongest safe in the world, but if you leave the door open...

---

### Post by RiceMonster on 2009-12-11
> **Ghost|BTFH said:**
> So, over 20 themes, each fully customizable with over 300,000 possible combinations for appearance is "quite meager"?

Holy carp.

Cheers,
Ghost

Compared to the variety of all the themes on GNOME-look, yes.

---

### Post by Ghost|BTFH on 2009-12-11
> **doas777 said:**
> we heard you about 6 pages back. thanks for the tip. the repos still don't have my custom darklooks gtk though.

Oh I see, and of course the default site that is linked via **Appearence**: art.gnome.org has nothing to offer.  Except for files that are already set up to be installed by default into the Themes via theme-installer, not requiring root access and thus being a million times safer.  

Glad you saw me six pages back, you're going to see a lot more of me, the more I hear people whine about having a ridiculous amount of options and calling them MEAGER.

You want even more options than over 300,000 from just the repositories?  Build your own - there ya go, unlimited options and you don't have to step out of the repositories to get it.  The only limits are your talent and imagination.  Go read a manual on how to make a theme and fully customize your Gnome.

Just, whatever you do, quit crying that a website like gnome-look is a necessary ingredient in the Ubuntu/gnome experience and that the user was fully justified in assuming that an unofficial site was safe when the file he wanted required root access to install.

Because both of those statements are false.

Cheers,
Ghost

---

### Post by aysiu on 2009-12-11
> **benj1 said:**
> 
regarding everyone selling linux as 'imperious to viruses', i think the problem is that many less experienced users equate 'virus' with anything that can do harm to your computer, regardless of how it does it. Yes *technically* linux is very resistant to viruses, not of course trojans, but in the average users mind this means they are invulnerable. Perhaps we should focus on clarifying this misunderstanding, you can have the strongest safe in the world, but if you leave the door open... I've tried to explain it to new users before, and my words fall on deaf ears, unfortunately.

Very few people want to see reason.

Reason is that there are varying degrees of security and risk, and that you can have a reasonable secure system and still have to be careful about what you do and what software you trust.

Unreasonable stances are *Linux is invincible* or *Linux is no more secure than Windows, only less popular so less of a target*.

Another unreasonable stance is *I don't really want to learn how to secure my system. I just want to install antivirus software just in case.*

So-called "antivirus" is useless. Ubuntu is reasonably secure with its defaults. If you're superparanoid, then use AppArmor and NoScript, and use only impossible-to-guess passwords. Then install only what's available through official repositories.

I've said it before and I'll say it again (who's listening, though?): **Antivirus will not protect you "just in case"**. Antivirus does nothing except make people feel complacent. Antivirus would not have stopped this trojan. The only thing that can stop trojans are people.

---

### Post by doas777 on 2009-12-11
> **Ghost|BTFH said:**
> Oh I see, and of course the default site that is linked via **Appearence**: art.gnome.org has nothing to offer.  Except for files that are already set up to be installed by default into the Themes via theme-installer, not requiring root access and thus being a million times safer.  

Glad you saw me six pages back, you're going to see a lot more of me, the more I hear people whine about having a ridiculous amount of options and calling them MEAGER.

You want even more options than over 300,000 from just the repositories?  Build your own - there ya go, unlimited options and you don't have to step out of the repositories to get it.  The only limits are your talent and imagination.  Go read a manual on how to make a theme and fully customize your Gnome.

Just, whatever you do, quit crying that a website like gnome-look is a necessary ingredient in the Ubuntu/gnome experience and that the user was fully justified in assuming that an unofficial site was safe when the file he wanted required root access to install.

Because both of those statements are false.

Cheers,
Ghost

I ain't saying your wrong, I'm just saying that your horse is dead so you can stop whipping it.

---

### Post by benj1 on 2009-12-11
> **aysiu said:**
> I've tried to explain it to new users before, and my words fall on deaf ears, unfortunately.

Very few people want to see reason.

Reason is that there are varying degrees of security and risk, and that you can have a reasonable secure system and still have to be careful about what you do and what software you trust.

Unreasonable stances are *Linux is invincible* or *Linux is no more secure than Windows, only less popular so less of a target*.

Another unreasonable stance is *I don't really want to learn how to secure my system. I just want to install antivirus software just in case.*

So-called "antivirus" is useless. Ubuntu is reasonably secure with its defaults. If you're superparanoid, then use AppArmor and NoScript, and use only impossible-to-guess passwords. Then install only what's available through official repositories.

I've said it before and I'll say it again (who's listening, though?): **Antivirus will not protect you "just in case"**. Antivirus does nothing except make people feel complacent. Antivirus would not have stopped this trojan. The only thing that can stop trojans are people.

i agree 100%, its just that sometimes "linux is invincible" is shouted a bit too loudly.
we can't force people to be security conscious but we can at least make sure they have the facts

---

### Post by aysiu on 2009-12-11
> **Ghost|BTFH said:**
> Oh I see, and of course the default site that is linked via **Appearence**: art.gnome.org has nothing to offer.  Except for files that are already set up to be installed by default into the Themes via theme-installer, not requiring root access and thus being a million times safer. Most of the themes on [http://www.gnome-look.org](http://www.gnome-look.org) are also safe and do not require root access. When I joined the forums back in 2005, no one was pointing to art.gnome.org, and with good reason. Back then, there was nothing there compared to gnome-look.org. Maybe that's still the case. I don't know. I haven't been to art.gnome.org lately.

The point is that for a new user to go to gnome-look.org is a perfectly reasonable action. It isn't some shady site. It's a site that is commonly recommended to new users on the forum. Do we want to start recommending new users **never** go to gnome-look.org? I think that's extremely short-sighted. The issue isn't really gnome-look.org itself. The issue is teaching people to be mindful of the fact that trojans can exist on any platform, no matter how securely the platform is put together.

And it's also about making people aware that even within an otherwise trustworthy site, you have to look at each element on that site with different eyes.

For example, a short while ago, we had a slew of users (they may have all been one user creating multiple accounts, too) telling new users to enter malicious commands into the terminal. Does that then make ubuntuforums.org an untrusted site? No. The site itself isn't untrustworthy. It's, for the vast majority of things, a helpful site with a lot of good tips. You just have to keep in mind that anyone can join the forums, and anyone can upload a theme to gnome-look.org.

If someone posts a command you're not sure of, Google it... or wait until other forum members weigh in on it. Did the person who gave you the command just join the forums? How many posts does she have? While new people who join often are just as knowledgeable if not more knowledgeable than forum veterans, forum veterans can generally be trusted (or we would have been banned long ago).

Same for themes. If a new account just uploaded a theme that has very few ratings or downloads... maybe you should wait until it's a bit more popular before you download it.

I don't see writing off an entire site as untrustworthy just because of one user who posted malicious code on it.

> Glad you saw me six pages back, you're going to see a lot more of me, the more I hear people whine about having a ridiculous amount of options and calling them MEAGER. And I'm going to keep whining about the options in **the repositories** being meager as long as only a handful of themes are in there. There are many, many themes on gnome-look.org that are not in the repositories.

> You want even more options than over 300,000 from just the repositories? Yes. And there are not 300,000 themes in the repositories. Nice try. >  Build your own - there ya go, unlimited options and you don't have to step out of the repositories to get it.  The only limits are your talent and imagination.  Go read a manual on how to make a theme and fully customize your Gnome. Why should I build my own when they already exist on gnome-look.org? 

> Just, whatever you do, quit crying that a website like gnome-look is a necessary ingredient in the Ubuntu/gnome experience and that the user was fully justified in assuming that an unofficial site was safe when the file he wanted required root access to install.

Because both of those statements are false. I didn't ever say gnome-look.org is **necessary**. I just said it's something that many new users get referred to to find more themes than are available in the repositories. It is not an untrusted site or a dodgy place to get themes. And most themes there do not come as .deb files or require root access.

---

### Post by benj1 on 2009-12-11
> **aysiu said:**
> 
The issue isn't really gnome-look.org itself. The issue is teaching people to be mindful of the fact that trojans can exist on any platform, no matter how securely the platform is put together.

true but gnome-look could still be improved, im not advocating vetting every package by hand (it would be best, but impractical),but simple things such as upload date and number of downloads, along with version control would help.

---

### Post by aysiu on 2009-12-11
> **benj1 said:**
> true but gnome-look could still be improved, im not advocating vetting every package by hand (it would be best, but impractical),but simple things such as upload date and number of downloads, along with version control would help.
It definitely could be improved.

I just don't like the idea of writing off the entire website just because of a couple of bad apples.

As I stated before, we've had some bad apples on the Ubuntu Forums, and I don't want people saying, "Oh, don't go to the Ubuntu Forums; they give you malicious commands" or people saying "Oh, don't go to Gnome Look; they have malicious .deb trojans."

---

### Post by Ghost|BTFH on 2009-12-11
> **doas777 said:**
> I ain't saying your wrong, I'm just saying that your horse is dead so you can stop whipping it.

Point taken, I'm going to rebut aysiu and then I'll be done with this.  Everyone else can keep arguing over it as much as they like. :)

[QUOTE=aysiu]The issue isn't really gnome-look.org itself. The issue is teaching people to be mindful of the fact that trojans can exist on any platform, no matter how securely the platform is put together.[/QUOTE]

I agree fully.  The issue was a stupid user who granted root access to a file he downloaded from an unsecured site.  Does that make it an evil site?  No.  It just makes the user stupid for not having learned the Golden Rule.  Don't give root to something unless you know what it is.

[QUOTE=aysiu]And there are not 300,000 themes in the repositories. Nice try.[/QUOTE]

Perhaps my previous posting didn't make it for some reason.  

Over 20 complete themes in the repositories, over 50 window borders, 50 controls, 10 icon sets offer a total combination of well over 300,000 desktop variations.  Is my math wrong?  This is what I referred to.  I do not call that amount of combinations meager at all, I'm sorry if you do.

[QUOTE=aysiu]Why should I build my own when they already exist on gnome-look.org?[/QUOTE]

If you want to be safe, you do things the safe way.  That means don't step out of the repositories.  If you do, what happens beyond that is on your head, not the OS's.  PEBKAC is a real issue.

[QUOTE=aysiu]I didn't ever say gnome-look.org is necessary. I just said it's something that many new users get referred to to find more themes than are available in the repositories. It is not an untrusted site or a dodgy place to get themes. And most themes there do not come as .deb files or require root access.[/QUOTE]

Then you're agreeing that it was the user's fault and there's really not much that needs to be done to the OS to "protect" future users?

Because that's been my whole point all along.  In fact, before I drop this thread entirely, for those who haven't read the whole thing, here are my points:

1) It was an ID-10-T error.  The user was stupid.

2) The website he went to isn't necessary at all.

3) The repositories have a nice selection of themes to offer, if you know where to look.  Education on what's already in there might be better than pointing someone over to a third-party site.

4) A secure system stays within the repositories.

'nuff said.  Please feel free to argue amongst yourselves.:popcorn:

Cheers,
Ghost

---

### Post by aysiu on 2009-12-11
> **Ghost|BTFH said:**
> 
Over 20 complete themes in the repositories, over 50 window borders, 50 controls, 10 icon sets offer a total combination of well over 300,000 desktop variations.  Is my math wrong?  This is what I referred to.  I do not call that amount of combinations meager at all, I'm sorry if you do. Be sorry all you want. I'm not. It's meager in comparison to what's available on Gnome Look. I will continue to go to Gnome Look to get themes. I don't see why I shouldn't.

> If you want to be safe, you do things the safe way.  That means don't step out of the repositories.  If you do, what happens beyond that is on your head, not the OS's.  PEBKAC is a real issue. I didn't put it on the OS's head. I fully agree PEBKAC is a real issue. I don't know whom you think you're arguing with.

> 
Then you're agreeing that it was the user's fault and there's really not much that needs to be done to the OS to "protect" future users? Yes. I fully agree with that statement. Read my other posts in this thread, and you'll see that's what I've been saying all along.

---

### Post by lisati on 2009-12-11
> **mivo said:**
> Indeed, Arch doesn't use .debs. ;)

(Sorry, couldn't resist.)
What? Does Arch use .msi files? (Just teasing!) :)

> **benj1 said:**
> 
regarding everyone selling linux as 'imperious to viruses', **i think the problem is that many less experienced users equate 'virus' with anything that can do harm to your computer, regardless of how it does it**. Yes *technically* linux is very resistant to viruses, not of course trojans, but in the average users mind this means they are invulnerable. Perhaps we should focus on clarifying this misunderstanding, you can have the strongest safe in the world, but if you leave the door open...
Exactly. Perhaps some education is needed?
> **aysiu said:**
> 
I've said it before and I'll say it again (who's listening, though?): **Antivirus will not protect you "just in case"**. Antivirus does nothing except make people feel complacent. Antivirus would not have stopped this trojan. The only thing that can stop trojans are people.
I'm listening! I only remember one occasion where malware caused serious problems on one of my machines, and the only person to blame was myself for knowingly opening a suspicious file. Having anti-virus sofware installed didn't help prevent the resulting problems.

My $0.02: AV software, at best, is only a tool, and should not be used as an excuse for sloppy habits.

---

### Post by alberthrocks on 2009-12-11
Social Engineering is a very common thing. It happens all the time.

The solution? Implement AppArmor, especially for programs that communicate. (Firefox, IM clients like Pidgin, others)

BUT.... how do you educate those who really have no idea what a browser is? (At least, what does the word "browser" mean.)

There is no way. I can keep educating my family and friends, but they will repeat the same mistakes... over and over again.

However, I have an idea. This may or may not work, may or may not have flaws. :)
Ubuntu already has a great notification system in effect, right?
Why not use it to inform the user about possible malware?
Here is a mockup:

[IMG]http://899620026955992051-a-1802744773732722657-s-sites.googlegroups.com/site/alberthrocks/home/images/WarningNotification.png?attachauth=ANoY7cosuSn7EGxvzFUXOwivJVC4O0Gah3SxlAz4PJfKsUX4A0NLP9FDEOZyW3PxzNuQNa-pTBbjmMOHUUfyN_dlcUlhFN3KmOdgDhmEXsWZforhbUzXXJxIRmxODVlh_sEk03LTjUIprJfn4bOtqkjS6j5zEyIw1KeVzPLcBHwyaXzRrTUFmI7z9ejyYQ4In4iqCAWZCFvuTrePrVV677W0wCaaYhqaSpDn3j9CU-Aw7Hv0kO7s1wY%3D&attredirects=0[/IMG]

A bit scary, eh? Here's a friendlier version (and shorter too!):

[IMG]http://899620026955992051-a-1802744773732722657-s-sites.googlegroups.com/site/alberthrocks/home/images/Warning_Notification_Friendlier.png?attachauth=ANoY7coW_0kzwQ16iShd58Jk8puBLIKZblteeWQ5er1IL7UDXsM1SgqL5lCoKobs0ClUQiI7cbop7q8BlO2wwnPesw8MbfD1PrH9JWkICd2Lu6cAKDDz_r9TMGJzCqipkoyWf47JP4y-dHnGbOLvEo2na_dq8KIsG5iGIxcomYe8bQALJEQvVFeeTC3T_V2EBH2PtiSkMyGNG0VGK6tc3Hmsmf9WoP9LbE22x1XT4gp4etkhJoCZjW8j6LhrDRKolrtjGf27Hbp6&attredirects=0[/IMG]

And after the user confirms (after clicking notification, confirm dialog
pops up to say yes or no):

[IMG]http://899620026955992051-a-1802744773732722657-s-sites.googlegroups.com/site/alberthrocks/home/images/Info_Reverted_File.png?attachauth=ANoY7cpLWk35bcsO3hjCzcySmPirSnBOYauBykimwiEYXJOARjWFNvANLzD5C7NiqXfbjO4hkfiyAJBDrqtWvGHtp9EWJDRvGNcsMxhb6vuF2YKluErdfBPDonp4tAmTgd8WnQ9ELXb-U2A77MNxzbsIzOsc5gH7QMn7r-NGSWifYVyR9QfG2tcTq1fFPELOL-2X3vdvO9KZyjj3eaIaCKK7u60WLEMqk7zqPPFNv6_r8c2qPqU__is%3D&attredirects=0[/IMG]

If we're talking about a new file (like in this incident):

[IMG]http://899620026955992051-a-1802744773732722657-s-sites.googlegroups.com/site/alberthrocks/home/images/Info_DeletedFile_TrashIcon_FINAL.png?attachauth=ANoY7crE7H-113YB0gDEnV3qFL1PCUY6NabODr9tXkSdHoIYs8UJwswiGbrZw8UKg8W2ZLbQfNK0Ub1PU-B5c3I5GCvDQWL9PPBRV0XVxDmeKsvC-y-llg6jLFOuMijwKAQvtvOA-Lom9DFbmSnwzRdZ2T5PmLnQBufEKSy3dNO3PDB6dK9IRVOSHtxkXo9mA_dtqwps1Gxj_rrJNGTcU-EmmIG4yf6dXH6ay4sV1YZi-vY0sbgIDXZexlpzyyw6u0LkmbhX7Myy&attredirects=0[/IMG]

or:

[IMG]http://899620026955992051-a-1802744773732722657-s-sites.googlegroups.com/site/alberthrocks/home/images/Info_DeletedFile_CheckIcon_FINAL.png?attachauth=ANoY7cqauLg2Af96rD0TWbNTzkKHOO3uAVFLZ29_Y5Xtvl0wUqk_mbcnyeESi7qUM97tcdBf9zdG1J498Ra5oXmnfORlzewt6NbCYXXvgFzTsPMO9Q6Bb9Iw-yGGV-N1rx4lMfrJq2O5i_Sfgx4znNt_pkv61sVVzVGsheMOLKycf8yPfy5-e9uIEJmT2bH09DXgTqy4x_16WrSul6kR1EFB1qu8DFnZL6TyWbTFOoZGbj8chr4CSelTDUvgcCxMFZ0pNAd6Wknl&attredirects=0[/IMG]

This is 100% implementable. inotify (kernel stuff) can do the file
change/add detection, while the notifications themselves are easy.

This is not without flaws. Just like the UAC, and the XP confirm to run,
people are bound to click (or in this case, ignore) the notifications.

The developers can probably make it more user friendlier.
Maybe the files can be checked to see if it is verified or not, or is a certain type that should be checked.

This is just an idea. Although I think this is a good solution, there are issues like space, efficiency, etc. that may affect this solution.

Any suggestions?

---

### Post by BuffaloX on 2009-12-11
Does anyone know if this has been reported to the police?
AFAIK this kind of malware is illegal in most countries.
If the uploader could be traced, it would be soo cool.
He/she probably camouflaged it, maybe did it through other systems, but then at least those systems could be warned they have an intruder.

---

### Post by duanedesign on 2009-12-13
> **Ghost|BTFH said:**
> The issue was a stupid user who granted root access to a file he downloaded from an unsecured site.

None of us are born knowing everything. This does not make one stupid.

Besides, this community revolves around being considerate and respectful and is better because of that. Remember a community where people feel uncomfortable or threatened is not a productive one.

---

### Post by Frak on 2009-12-13
> **duanedesign said:**
> None of us are born knowing everything. This does not make one stupid.

Besides, this community revolves around being considerate and respectful and is better because of that. Remember a community where people feel uncomfortable or threatened is not a productive one.
But a little common sense goes a long ways.

---

### Post by quinnten83 on 2009-12-13
> **Frak said:**
> Same on Windows. Don't run software that you don't trust as administrator.

good advise,
only that in windows you are always running as administrator otherwise you can't do crap. So, all those ActiveX scripts in the background just install the crappy malware for you because they already have the rights to.
At least Linux asks you for admin rights before installing. At that point though there is no more protection that can be applied. If the user decides to install something than they have opened themselves up to certain risks. This is no different than the user running sudo rm-f / as and admin.

It's sad though that this was placed on Gnome-look.People by and large consider gnome-look to be a trusted site. Much like you would trust sotpedia or tucows with the Windows software that is placed on their sites.

---

### Post by Diluted on 2009-12-13
> **quinnten83 said:**
> only that in windows you are always running as administrator otherwise you can't do crap. So, all those ActiveX scripts in the background just install the crappy malware for you because they already have the rights to.
You could always be proactive and create a standard user account in Windows. Its protection is just as good as in Linux.

> **quinnten83 said:**
> It's sad though that this was placed on Gnome-look.People by and large consider gnome-look to be a trusted site. Much like you would trust sotpedia or tucows with the Windows software that is placed on their sites.
Softpedia and Tucows are a bit different from GNOME-Look.org. Tucows (as far as I can see) only provides links to the software author's site. Softpedia will check for spyware and viruses and they will tell you if a software has it or not.

---

### Post by Techsnap on 2009-12-13
> At least Linux asks you for admin rights before installing. At that point though there is no more protection that can be applied. If the user decides to install something than they have opened themselves up to certain risks. This is no different than the user running sudo rm-f / as and admin.

If you had been bothered to create a normal user account on Windows you'd realise, oh Windows asks too.

---

### Post by mivo on 2009-12-13
> **Techsnap said:**
> If you had been bothered to create a normal user account on Windows you'd realise, oh Windows asks too.

Windows 7 asks in various instances even when you are using an administrator account. It will say that this or that action (i.e. changing permissions) requires admin privileges and ask if you wish to continue). This can probably be disabled, but I quite like it.

---

### Post by Frak on 2009-12-13
> **quinnten83 said:**
> At least Linux asks you for admin rights before installing. At that point though there is no more protection that can be applied. If the user decides to install something than they have opened themselves up to certain risks. This is no different than the user running sudo rm-f / as and admin.

Ubuntu is one of the special ones. Many distributions still give you default root/sub user accounts. No sudo. They don't ask you for permission, either you can do it, or you need to temp switch via superuser.

So "At least Linux asks you for admin rights before installing", no, it doesn't. The distribution places methods in for authentication, but it's no different than setting up a limited user in Windows.

---

### Post by Techsnap on 2009-12-13
Yes, try Slackware for example, you're given a root account, just like Windows by default, nothing more, just root. It's up to you to make your own account.. just like Windows. 

Ubuntu Is not Linux.

---

### Post by cometdog on 2009-12-14
Someone pointed out the propensity of new users to install .deb files.

I realized that I tend to do this as well -- in fact I hadn't really carefully considered the security implications of the doing so with sudo, despite the fact that I should really know better.

New users find it easier to install .deb files than to unzip other files, find an appropriate dumping ground for them, and figure out how to stick a launcher in a menu.

New users find it easier to remove something later that was installed via a .deb file.

Think about a new user running a make script and seeing all that info run past on the terminal.  A bunch of files were just sneezed all across the filesystem -- good luck tracking those down later if you need to remove them manually.  Particularly for someone migrating from Windows, where each program typically resides in its tidy directory under Program Files, this is very disconcerting.

New users have a greater degree of confidence that something available as a .deb file will actually end up working on their system.

And new users in general have very little concept of what kinds of downloads should be made available in .deb format, and what kinds of downloads should be available in other formats.

Anyway, glad this thread was around to read, to make me think a little more carefully the next time I'm about to double-click on one of those suckers.

---

### Post by Jeruvy on 2009-12-15
> **tinivole said:**
> 1) Security is not invincible (you are going off a false positive here).
2) Security should never mean: prevent **administrators** from doing something they probably don't want to do - however good the intention.

Giving you administer / root privileges to a machine generally means that we trust that you can use / administer it wisely.
If you don't - then you can't complain/blame the software/OS if bad things happen.

Although we have AppArmor to prevent some instances of damage from occurring, but not all...

I think this is a misnomer.  Many folks have adopted Linux because of the false sense of security even though many understand that security is not a 'program' it is a state of mind.  Those that understand how to secure and to diligently check there downloads do, and those that can't be bothered cause thats too geeky don't.  

I don't think its unrealistic to fortune tell here by saying that as Ubuntu and Linux becomes more popular, it will generate a larger share of 'haters' and those that wish to do harm, and malware will increase.  I do agree with your point that we shouldn't blame 'Microsoft' or 'Ubuntu' or even 'Gnome-look', but nearly everyone does or will since this is the focal point of the issue.  For Microsoft, part of this stems from the fact that for years they didn't bother considering the design issues that made malware prevelent in the first place.  I don't think Ubuntu or Linux in general has ignored this, but it's also abundantly clear that many fanboi's in the community and on these forums seem to think that it's the invincible impenetrable force against malware.  Which is truly the false sense of security here.

No computer/software is immune to infection, period.  As new users come on board many bring the same bad habits they have developed (which may have caused previous malware infections) with them.  And more important the malware authors come following on the popularity or simplicity.  This particular malware was very very simple but as we can see, the scale it could provide was also effective.

---

### Post by dentaku65 on 2009-12-16
I open a "bug" into 100 paper cuts
[https://bugs.launchpad.net/hundredpapercuts/+bug/497445](https://bugs.launchpad.net/hundredpapercuts/+bug/497445)

---

### Post by benj1 on 2009-12-16
> **dentaku65 said:**
> I open a "bug" into 100 paper cuts
[https://bugs.launchpad.net/hundredpapercuts/+bug/497445](https://bugs.launchpad.net/hundredpapercuts/+bug/497445)

for what its worth, i don't think this will get accepted as a papercut, as its probably not in the remit (small esily solvable problems).
although when the news of this first came out i did think of some kind of scanner, it would be difficult to do, and much much harder to be idiot proof, remember rm and cp are perfectly legitimate in both installation and general running of many apps, although something to scan and flag all rm's, cp's and downloads might be doable, a knowledgable user can then look at it and see that 'rm -rf /tmp/foo' and 'wget [www.documentation.com](www.documentation.com)' is probably fine but 'rm -rf /' and 'wget [www.evilmalware.com](www.evilmalware.com)' probably warrant further investigation.

---

### Post by aysiu on 2009-12-16
It's not a bug. Social engineering relies on tricking the user, not the operating system. If the user decides to install a malicious .deb and then authenticates with a sudoer password, the system can't do anything about it.

More importantly, that removal command is not the only malicious command out there. You can't keep a comprehensive database of *all* potentially malicious commands. And some commands may be malicious in some contexts and benign in others (as benj1 pointed out).

The bottom line is that people need to figure out what is trustworthy to install and what is not. What this event has done, hopefully, is make people realize that even on otherwise "trustworthy" sites like Gnome Look, you still have to vet what you download, because *anyone* can upload a "theme" to that site. Go by ratings and download numbers. **Ask** fellow forum members if you have any doubts about a theme's integrity.

---

### Post by dentaku65 on 2009-12-16
Thx benj1 & aysiu for the clarification...
but I have a question: is the scenario described for gnome-look.org can be replicated, for example, to a PPA repository?

---

### Post by aysiu on 2009-12-16
> **dentaku65 said:**
> Thx benj1 & aysiu for the clarification...
but I have a question: is the scenario described for gnome-look.org can be replicated, for example, to a PPA repository?
I don't think it's quite the same thing.

My understanding (and someone please correct me if I'm wrong here) is that not just anyone can create a PPA repository. I don't think it goes through quite the same stringent review that regular Ubuntu repositories go through, but I think you have to be someone related to Ubuntu or to a particular upstream software project in order to create a PPA repository.

With Gnome Look, I believe just anyone can upload a theme (or "theme") without any kind of vetting process whatsoever.

---

### Post by bodhi.zazen on 2009-12-16
> **dentaku65 said:**
> Thx benj1 & aysiu for the clarification...
but I have a question: is the scenario described for gnome-look.org can be replicated, for example, to a PPA repository?

Anybody can create a ppa, so, yes, ppa are subject to the potential for malignant .deb

Again not all ppa are created equal , some are individuals, and some are groups of individuals or specific projects.

Honestly, from your posts, I do not get the impression you understand what social engineering is or how to manage social engineering. To that end, please see :

[http://en.wikipedia.org/wiki/Social_engineering_%28security%29](http://en.wikipedia.org/wiki/Social_engineering_%28security%29)

Social engineering is the second most common method of cracking a system as it is easier to build a malignant .deb then it is to crack the underlying OS.

(#1 is weak passwords on VNC or ssh servers)

---

### Post by aysiu on 2009-12-16
> **bodhi.zazen said:**
> Anybody can create a ppa, so, yes, ppa are subject to the potential for malignant .deb Wow! I had no idea just anyone could. That's not good. Aren't they hosted on Launchpad?

---

### Post by bodhi.zazen on 2009-12-16
> **aysiu said:**
> Wow! I had no idea just anyone could. That's not good. Aren't they hosted on Launchpad?

Aye, I believe there has been some discussion about that, but, FYI :

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

So, as you can see, there are a few hoops one has to navigate, but there are no formal requirements or reviews (thus I personally am very cautious with ppa).

The only saving grace is that one must upload the source code, and LP builds the .deb, so the source code is (in theory) available or review (although I suppose it could be removed once the .deb is built).

---

### Post by NoaHall on 2009-12-16
> **dentaku65 said:**
> Thx benj1 & aysiu for the clarification...
but I have a question: is the scenario described for gnome-look.org can be replicated, for example, to a PPA repository?

Yes. But it will be checked and fixed very quickly too.

---

### Post by aysiu on 2009-12-16
> **bodhi.zazen said:**
> Aye, I believe there has been some discussion about that, but, FYI :

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

So, as you can see, there are a few hoops one has to navigate, but there are no formal requirements or reviews (thus I personally am very cautious with ppa).

The only saving grace is that one must upload the source code, and LP builds the .deb, so the source code is (in theory) available or review (although I suppose it could be removed once the .deb is built).
Good to know. So less likely than Gnome Look but not impossible.

This will be a big struggle Ubuntu will face more and more of as it gets more popular. Ease of use and security are constantly at odds. The easier it becomes to add third-party sources, the easier it gets to compromise users' systems through social engineering.

---

### Post by dentaku65 on 2009-12-16
> **bodhi.zazen said:**
> Anybody can create a ppa, so, yes, ppa are subject to the potential for malignant .deb

Again not all ppa are created equal , some are individuals, and some are groups of individuals or specific projects.

Honestly, from your posts, I do not get the impression you understand what social engineering is or how to manage social engineering. To that end, please see :

[http://en.wikipedia.org/wiki/Social_engineering_%28security%29](http://en.wikipedia.org/wiki/Social_engineering_%28security%29)

Social engineering is the second most common method of cracking a system as it is easier to build a malignant .deb then it is to crack the underlying OS.

(#1 is weak passwords on VNC or ssh servers)

...I ask the question about PPA for "the second most common method"; I was think about the scenario of the gnome-look and the popularity of ubuntu and PPA repos that users add on their system.
Thx for the explanation.

---

### Post by Chame_Wizard on 2009-12-16
I wonder what will happen with kde-look.org .:lolflag:

---

### Post by chillyomi on 2009-12-16
No viruses for Linux yet so im happy

---

### Post by benj1 on 2009-12-17
> **chillyomi said:**
> No viruses for Linux yet so im happy

there are linux viruses, im not sure that any are a threat anymore but they are possible.

[https://help.ubuntu.com/community/Linuxvirus]("https://help.ubuntu.com/community/Linuxvirus")

---

### Post by mivo on 2009-12-17
> **chillyomi said:**
> No viruses for Linux yet so im happy

In most cases, getting viruses requires an action on the user's end, just like the installation of malicious packages like in this case. Or differently put, people who, in their Windows days, had systems riddled with viruses, are more prone to having their Linux system compromised as well (especially if they believe that they are completely safe).

I also feel a compromised Linux system is more dangerous than a compromised Windows box.

---

### Post by TopEnder on 2010-01-27
Forum Members,  A timely reminder always be on guard, please read, [http://www.zdnet.com.au/blogs/null-pointer/soa/Carelessness-busts-Linux-security/0,2001102868,339299939,00.htm](http://www.zdnet.com.au/blogs/null-pointer/soa/Carelessness-busts-Linux-security/0,2001102868,339299939,00.htm)

---

### Post by italyanker on 2010-03-17
> **mivo said:**
> I also feel a compromised Linux system is more dangerous than a compromised Windows box.

Sure...I think if someone is ignorant about developing and/or understanding code or linux systems infrastructure ( except for an all days use ) he had to use safe and original repositories and garanteed software from these instead of install software he can't understand...
For the rest i say a very very very big LOL, 'cause the thing sounds so ridicuolous! :D
And...finally, i think that in ICT and computers the real security doesn't exist!But we can make security in our little everyday with little tips we can use...I think so that all people must know these tips in order to make his computer experience more secure! ;)

---

### Post by swoll1980 on 2010-03-17
Nothing can stop someone from voluntarily installing malware on their machine. Anyone who thought otherwise is unreasonable. Anyone who thinks a site like gnome-look.org, who lets everyone in the world upload anything they want, is a "trusted site" is unreasonable.

---

### Post by lykwydchykyn on 2010-03-17
> **swoll1980 said:**
> Nothing can stop someone from voluntarily installing malware on their machine. Anyone who thought otherwise is unreasonable. Anyone who thinks a site like gnome-look.org, who lets everyone in the world upload anything they want, is a "trusted site" is unreasonable.

Someone tell the KDE devs that, since kde-look.org is integrated into my configuration tools and cannot be disabled.

---

### Post by swoll1980 on 2010-03-17
> **lykwydchykyn said:**
> Someone tell the KDE devs that, since kde-look.org is integrated into my configuration tools and cannot be disabled.

It's a separate entity. KDE art something, or other. You can't just upload something to it like you can on the site it's self.

---

### Post by lykwydchykyn on 2010-03-17
> **swoll1980 said:**
> It's a separate entity. KDE art something, or other. You can't just upload something to it like you can on the site it's self.

No, it's kde-look.org, and it's integrated into the desktop via the K "get hot new stuff" dialog.  I know this because I've released 3 plasmoids on kde-look :D.

---

### Post by swoll1980 on 2010-03-17
> **lykwydchykyn said:**
> No, it's kde-look.org, and it's integrated into the desktop via the K "get hot new stuff" dialog.  I know this because I've released 3 plasmoids on kde-look :D.

It doesn't pull down the whole website though. It's sandboxed, the things it has access too are limited.

---

### Post by lykwydchykyn on 2010-03-17
> **swoll1980 said:**
> It doesn't pull down the whole website though. It's sandboxed, the things it has access too are limited.

You can get plasma scripts, so if you trust plasma scripts then I guess it's ok.  What makes you think they're sandboxed?

I haven't done a proof-of-concept (nor do I plan to; I'm not the sort to do something malicious to prove a point), but I don't see why I couldn't stick malicious code in a plasmoid's __init__() function.  It's just a python script.  Heck, one of my plasmoids (depending on how you configure it) calls console commands to work.

---

