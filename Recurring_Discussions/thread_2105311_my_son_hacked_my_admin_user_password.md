---
title: "my son hacked my admin user password"
date: 2013-01-15
forum: Recurring Discussions
---

### Post by rontopia on 2013-01-15
hi all

1 of the things that I don't care for in Ubuntu is the lack of a traditional root password for the root user.  here's why, my very clever son found this way around my admin user password and has installed software that I didn't want on the computer. when I asked him how he did it this is what he said


I booted it in recovery mode and them selected netroot mode and then typed 'passwd ronm' and it asked of for a new password.

ronm is the admin. He has his own account.  How do I stop him from doing this?

---

### Post by MG&amp;TL on 2013-01-15
A root password won't stop that. You could equally set the root password from recovery mode.

If your son has physical access to the box, and he's bright enough to do that, there's not a lot on the actual software side to stop him. I'd respectfully suggest a parental approach instead.

Opinion: if your son is good with computers, this is to be encouraged! Talk to him about it, there's a lot of constructive, educational fun to be had with computers, rather than just 'hacking' them.

---

### Post by Cheesemill on 2013-01-15
As the old saying goes, physical access = root access.

Even if you lock down recovery mode there is nothing to stop him booting from a Live CD and changing the password from that.

---

### Post by haqking on 2013-01-15
The only thing you can do is get him to teach you Linux ;-)

Peace

---

### Post by SeijiSensei on 2013-01-15
Sometimes you can set a password in the BIOS that must be entered before the machine will boot.

Even if you set a traditional root password, that would not have stopped him from booting into recovery mode and changing that one.

---

### Post by Mopar1973Man on 2013-01-15
I think its cool that your son had out smarted you. ;)

But I'm sure the guys here are right if he's got physical access to the computer he's going to figure out a way of hacking the computer.

---

### Post by CharlesA on 2013-01-15
> **MG&TL said:**
> A root password won't stop that. You could equally set the root password from recovery mode.

If your son has physical access to the box, and he's bright enough to do that, there's not a lot on the actual software side to stop him. I'd respectfully suggest a parental approach instead.

Opinion: if your son is good with computers, this is to be encouraged! Talk to him about it, there's a lot of constructive, educational fun to be had with computers, rather than just 'hacking' them.

This is the best solution (at least IMHO). BIOS password is another idea, but those are fairly easy to get around too.

---

### Post by alphaamanitin on 2013-01-15
Yeah BIOS password can often be defeated by removing the CMOS battery if I recall correctly?

AlphaA

---

### Post by CharlesA on 2013-01-15
> **alphaamanitin said:**
> Yeah BIOS password can often be defeated by removing the CMOS battery if I recall correctly?

AlphaA

At least for desktops. I have heard conflicting reports about laptops.

---

### Post by Petro Dawg on 2013-01-15
If your son (which I'm assuming is still a child) can, or is willing to, bypass a BIOS password (which, as a kid, I would never have had nerve to do; while I can easily envision my younger self doing what he did) then don't bother trying own a computer that he cannot access, unless you are willing to lock your computer in a safe when you are not using it.

If you don't want to go to that extreme then, get him a POS, next to free, old computer and let him put whatever dumb junk he feels like on it, perhaps then he'll leave yours alone.  

I suggest an "old" computer (circa 2000) because he will have to become more resourceful to get it to do what he wants it to do, which can lead to developing valuable skills.  And you can probably find someone nearby more than willing to give you one free.  I know I've thrown many away myself, as people keep giving them to me.

---

### Post by Herman on 2013-01-16
You could Install Ubuntu in a LUKS encrypted file system. 
That's a good way to protect a computer from people who have physical access.

---

### Post by Warren Hill on 2013-01-16
As stated in earlier posts if someone has physical access they have root access.

You can make things as difficult as possible by setting the BIOS to only boot from the hard drive and adding a BIOS password.

If it were my son I would be encouraging him to learn as much linux/unix as possible.  Perhaps even getting another PC is is allowed to hack.

Its about trust.  If you encourage his curiosity by giving him a legitimate place to experiment and learn kids are more likely to respect the rules you give them.

After all you have to trust you have brought you son up well enough that he will behave in other circumstances and won't for example lie and steal.

---

### Post by Lars Noodén on 2013-01-16
You can [set a password on Grub](https://help.ubuntu.com/community/Grub2/Passwords) to prevent certain options like the recovery mode from being selected.  You'd also have to change the BIOS to prevent booting from a recovery CD.  

Best would be working things out with your son.  There are no reliable technical solutions to social problems.

---

### Post by Habitual on 2013-01-16
60. 
[My five-year-old child advisor will also be asked to  decipher any code I am thinking of using. If he breaks the code in under  30 seconds, it will not be used. Note: this also applies to passwords.]("http://www.eviloverlord.com/lists/overlord.html")

---

### Post by Tjalleman on 2013-01-16
Just a small tip from a psychologist: its better to encourage the computer-skills of your son and be interested in it and communicate about it. This is a better way to control your son's computer behavior than a password.

Keep connected ;)

---

### Post by spynappels on 2013-01-16
Take him to a CoderDojo and develop his skills, that way you can also guide him in the ethical use of those skills.

---

### Post by rontopia on 2013-01-16
Thanks for all the parenting tips. 

For the record.  The computer is specifically for the kids. Is several years old and I chose to put linux on it so as to spark their curious nature. Im not inclined to keep them from learning anything about computers in general. However I am inclined to have them ask for permission rather than forgiveness after the fact. 

I have been using unix/linux perhaps longer than most of you have been alive. I run linux at work and design integrated circuits with it. I myself know how to hack root in a few different ways but sense I am root in my own home at least, and the occasion to hack comes up so infrequently in the work environment. .. I have not given it much thought.. which is why I came here.. to see if there was a way to stop this action.with respect, if I want parenting tips, I would go to a parenting website not the ubuntu fourms. 

I will try thr bias pw and turn off cdrom/usb access. But to me mee this is a glaring security problem. That really shouldn't b.

---

### Post by haqking on 2013-01-16
> **rontopia said:**
> Thanks for all the parenting tips. 

For the record.  The computer is specifically for the kids. Is several years old and I chose to put linux on it so as to spark their curious nature. Im not inclined to keep them from learning anything about computers in general. However I am inclined to have them ask for permission rather than forgiveness after the fact. 

**I have been using unix/linux perhaps longer than most of you have been alive.** I run linux at work and design integrated circuits with it. I myself know how to hack root in a few different ways but sense I am root in my own home at least, and the occasion to hack comes up so infrequently in the work environment. .. I have not given it much thought.. which is why I came here.. to see if there was a way to stop this action.with respect, if I want parenting tips, I would go to a parenting website not the ubuntu fourms. 

I will try thr bias pw and turn off cdrom/usb access. But to me mee this is a glaring security problem. That really shouldn't b.

And you didnt know physical access is root access ?

As for "hack" by using either the original definition or the common media definition, it is neither.  It is a simple systems admin feature.

---

### Post by nothingspecial on 2013-01-16
What you really need is a room, with a lock and key.

Then give him restricted ssh access to a walled off bit of the computer from another computer (work station).

---

### Post by rontopia on 2013-01-16
> **haqking said:**
> And you didnt know physical access is root access ?

As for "hack" by using either the original definition or the common media definition, it is neither.  It is a simple systems admin feature.


I understand it but have never had an occasion to really want to stop it.. do you have a suggestion . also I mean hack in the tridiional sense.

---

### Post by rontopia on 2013-01-16
> **nothingspecial said:**
> What you really need is a room, with a lock and key.

Then give him restricted ssh access to a walled off bit of the computer from another computer (work station).


I really dont want to go to that extreme. I want hime to explore and to learn.. I just want him to ask permission befoe installing updates and software. Thats all.

---

### Post by Habitual on 2013-01-16
> **rontopia said:**
> But to me mee this is a glaring security problem. That really shouldn't b.
...
I have been using unix/linux perhaps longer than most of you have been alive
Lack of Security certainly sounds like a "user" experience to me.

booting single and changing passwords is a Feature not a "glaring security problem". You got boned once, you should be motivated to 'fix' your setup with renewed enthusiasm.

The First Security Rule is "There is NO Security without physical security".
If I can put my hands on it, there's a chance you haven't done due diligence and I could work with that. Anyone, at any age with desire can google how to do this.

Power-On passwords
Restricted BIOS and boot options.
Password the boot manager.

> **rontopia said:**
> I run linux at work and design integrated circuits with it great, I have Tang in my kitchen, doesn't make me an astronaut.

The burden is yours.

---

### Post by haqking on 2013-01-16
> **rontopia said:**
> I understand it but have never had an occasion to really want to stop it.. do you have a suggestion . also I mean hack in the tridiional sense.

The only thing you can do as are already mentioned.

If the person has physical access and is allowed to use the machine then BIOS passwords, Grub passwords, keys and locks wont do anything really if your child is likely to "ignore" you.

if they will listen to you then tell them not to use recovery console ;-)

You could look at sulogin if its a priority. (it will mean enabling root and giving it a password)

[http://linux.about.com/library/cmd/blcmdl8_sulogin.htm](http://linux.about.com/library/cmd/blcmdl8_sulogin.htm)

See here [http://www.stuartellis.eu/articles/securing-linux/#securing-recovery](http://www.stuartellis.eu/articles/securing-linux/#securing-recovery) (things are slightly different for Ubuntu than most other distros in this respect)

---

### Post by rontopia on 2013-01-16
> **Habitual said:**
> Lack of Security certainly sounds like a "user" experience to me.

booting single and changing passwords is a Feature not a "glaring security problem". You got boned once, you should be motivated to 'fix' your setup with renewed enthusiasm.

The First Security Rule is "There is NO Security without physical security".
If I can put my hands on it, there's a chance you haven't done due diligence and I could work with that. Anyone, at any age with desire can google how to do this.

Power-On passwords
Restricted BIOS and boot options.
Password the boot manager.

 great, I have Tang in my kitchen, doesn't make me an astronaut


I seriously doubt you have tang in your kitchen.

When did help fourms become so snipie? I guess its somehow cool now?

And if the burden is not shared,  why respond at all?  Why would we have a fourm?  Heck lets shut down the internet...  The purpose of a fourm is the exchange of  shared burdens..

---

### Post by sffvba[e0rt on 2013-01-16
> **rontopia said:**
> I seriously doubt you have tang in your kitchen.

When did help fourms become so snipie? I guess its somehow cool now?

And if the burden is not shared,  why respond at all?  Why would we have a fourm?  Heck lets shut down the internet...  The purpose of a fourm is the exchange of  shared burdens..

This isn't a problem with Ubuntu.  Advice has been given and this thread is becoming circular.


404

---

### Post by Elfy on 2013-01-16
*Thread moved to **Recurring Discussions**.*

This comes up over and over again.

---

### Post by brusegadi on 2013-01-16
What about encrypted home folder? So if he changes the password from recovery mode the disk will still be encrypted since you need the original password for decryption.

---

### Post by Paddy Landau on 2013-01-16
The only way you can truly prevent this if your son has physical access is to encrypt your disk. That has the downside that *you* will have to boot your computer. Once booted, your son will be able to boot into his account.

As already stated, you can use LUKS. Another option is Truecrypt.

---

### Post by IWantFroyo on 2013-01-16
Any computer is hackable if you can access it physically. There's not much you can do, other than encrypt the HDD and hope he doesn't use Ophcrack.

Telling him not to touch it without your permission is the only real solution.

Also, please don't use the "I've been using Linux longer than you've been alive" argument. I know people in this thread who have used Gentoo and etc.

If you don't want us to be "snipie" then don't snap at us.

---

### Post by sidzen on 2013-01-16
How do you stop him?  Get him his own PC, of course! (Duh!)
BTW, I have a son who is probably old enough to have a son the age of yours!

---

### Post by brusegadi on 2013-01-16
A bit off topic, but Ophcrack cant be used to crack an encrypted HDD, its only for the windows password, correct?

---

### Post by IWantFroyo on 2013-01-16
No. Ophcrack can be used to break into encrypted systems.

---

### Post by CharlesA on 2013-01-16
> **IWantFroyo said:**
> No. Ophcrack can be used to break into encrypted systems.

News to me, I thought it was only used for Windows passwords.

---

### Post by IWantFroyo on 2013-01-16
O_o

I haven't used it. I just read that it can be used to break into encrypted systems.

Maybe it is just for Windows passwords.

Edit: Yep. It is. :(

---

### Post by CharlesA on 2013-01-16
Lol. Happens to everyone. ;)

---

### Post by cprofitt on 2013-01-17
> [Advice is what we ask for when we already know the answer but wish we didn't.]("http://www.wisdomquotes.com/quote/erica-jong-2.html")
 [RIGHT]~ Erica Jong  [/RIGHT]
I think this summarizes the thread repartee.

---

### Post by SeijiSensei on 2013-01-17
> I want hime to explore and to learn.. I just want him to ask permission befoe installing updates and software. Thats all. 

I'm a bit puzzled by the notion that you gave your kid a computer to play with but want to control what he installs on it.  Those seem incompatible to me.  Even if he "breaks" the installation somehow, which is very unlikely in my opinion, reinstallation takes just a few minutes.

---

### Post by CharlesA on 2013-01-17
> **SeijiSensei said:**
> I'm a bit puzzled by the notion that you gave your kid a computer to play with but want to control what he installs on it.  Those seem incompatible to me.  Even if he "breaks" the installation somehow, which is very unlikely in my opinion, reinstallation takes just a few minutes.

Indeed. A reinstall even takes less time if you clone the drive and restore it, but reinstalling from scratch doesn't take too long either.

---

### Post by Bandit on 2013-01-17
> **haqking said:**
> The only thing you can do is get him to teach you Linux ;-)

Peace

LOL This.. ):P

Props to the kid...

---

### Post by JustinR on 2013-01-17
[http://www.linuxquestions.org/questions/linux-software-2/howto-disable-single-user-mode-544529/](http://www.linuxquestions.org/questions/linux-software-2/howto-disable-single-user-mode-544529/)

quote from : [http://www.cyberciti.biz/tips/tips-to-protect-linux-servers-physical-console-access.html](http://www.cyberciti.biz/tips/tips-to-protect-linux-servers-physical-console-access.html)

> 
**Enable Authentication for Single-User Mode**

Single-User mode is used for a system recovery. However, by default, no authentication is used if single-user mode is selected. This can be used to bypassing security on the server and gaining root access. To enable authentication for single-user mode, open the /etc/inittab, file:
# vi /etc/inittab

 Add the following line to the file:
~~:S:wait:/sbin/sulogin

 Save and close the file.


---

### Post by Bandit on 2013-01-17
> **SeijiSensei said:**
> I'm a bit puzzled by the notion that you gave your kid a computer to play with but want to control what he installs on it.  Those seem incompatible to me.  Even if he "breaks" the installation somehow, which is very unlikely in my opinion, reinstallation takes just a few minutes.

Not to mention if you knows enough to get around admin p/w, chances are he isnt going to break then system on purpose.

---

### Post by Metallion on 2013-01-17
> **rontopia said:**
> However I am inclined to have them ask for permission rather than forgiveness after the fact.

Dude, with all due respect this is a parenting question no matter how you look a it. Compliment him for his skills to change the password but tell him he's not allowed to install stuff without your permission.

---

### Post by matt_symes on 2013-01-19
If you want to just stop him installing software (i have not read through all the posts) then here's a solution that will test his sys admin skills a little.

```

matthew-S206:/home/matthew % which apt-get         
/usr/bin/apt-get
matthew-S206:/home/matthew % sudo chmod -x /usr/bin/apt-get
matthew-S206:/home/matthew % sudo apt-get update
sudo: apt-get: command not found
matthew-S206:/home/matthew % sudo chmod +x /usr/bin/apt-get
matthew-S206:/home/matthew % sudo apt-get update           
Ign http://security.ubuntu.com quantal-security InRelease
Ign http://extras.ubuntu.com quantal InRelease                      
Ign http://gb.archive.ubuntu.com quantal InRelease
<snip>
```This can, of course be extended (update-manager, software etc). You can script it on your login to enable it and disable on logout of your account.

This is one of a number of solutions you may consider.

---

### Post by sunfromhere on 2013-01-19
> **JustinR said:**
> [http://www.linuxquestions.org/questions/linux-software-2/howto-disable-single-user-mode-544529/](http://www.linuxquestions.org/questions/linux-software-2/howto-disable-single-user-mode-544529/)

quote from : [http://www.cyberciti.biz/tips/tips-to-protect-linux-servers-physical-console-access.html](http://www.cyberciti.biz/tips/tips-to-protect-linux-servers-physical-console-access.html)

And since there's no inittab in Ubuntu, what to do?

---

### Post by Gone fishing on 2013-01-20
If he has physical access to the box and is capable of starting in recovery and changing passwords then you can do nothing at a software level. I suggest you discuss the use and missuse of geek skills. Id get him his own box with no OS and let him download, install and play.

IT skill are a great thing to develop, problem solving skills even better.

---

### Post by aysiu on 2013-01-20
People keep saying "physical access is root access," which is true, of course, but then seem to also imply the child *must* have physical access in order to use the computer, which is absolutely untrue.

This may seem a bit over the top, but you can set up a kiosk-type situation, in which you have a Linux desktop computer locked in a box, with enough of a hole to let up wires for a keyboard, mouse, and monitor. Short of your son taking out a saw and sawing open the box (or successfully picking the lock), he essentially no longer has physical access, and thus cannot remove the CMOS battery or boot up a live CD/USB or bypass the Grub password.

Another way to go about this is similar but a bit different. Supposing you don't have or don't want to purchase a kiosk-like box. Lock the computer up in a room or closet and enable *openssh-server* or VNC so your son can remote in from another room and play around with his login... remotely. This is similar to how most companies are set up with Linux servers (can apply to desktops, too, in this case). You've basically set up a "server room" for a desktop.

P.S. I know it's very frustrating to be getting parenting advice from people when you're looking for a technical solution, but it's also equally frustrating for people here *you're asking help from* to get the condescending "I was using Linux before you were born" bit.

---

