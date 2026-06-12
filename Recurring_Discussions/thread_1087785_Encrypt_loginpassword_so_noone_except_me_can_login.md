---
title: "Encrypt login/password so noone except me can login"
date: 2009-03-05
forum: Recurring Discussions
---

### Post by riahc3 on 2009-03-05
Hey

Today a friend of mine got to GRUB, logged in (I belive) in recovery mode, and using several commands he was able to login with root access/as root without using any password or/and my username. He told me that I didnt have my password encrypted so that why he was able to do it.

My question is how can I change this so only I can log in.

---

### Post by mdebusk on 2009-03-05
> **riahc3 said:**
> My question is how can I change this so only I can log in.

Easiest and probably best: password-protect your BIOS.

Direct answer to your question: [password-protect grub]("http://ubuntuforums.org/showthread.php?t=7353").

---

### Post by Seq on 2009-03-05
> **riahc3 said:**
> Hey

Today a friend of mine got to GRUB, logged in (I belive) in recovery mode, and using several commands he was able to login with root access/as root without using any password or/and my username. He told me that I didnt have my password encrypted so that why he was able to do it.

My question is how can I change this so only I can log in.

Physical access wins. Always. Recovery mode does not need a password to access it and throws you into a root console. You could password-protect GRUB, but now all he needs is a livecd/boot-disk/etc to get access to your disk. You could restrict your BIOS, but all he has to do now is open the case and take the drive.

The only option for "absolute" security of your data is disk encryption. Jaunty will have some home directory encryption soon, but this still allows him to drop something onto your system (keylogger, init script, rootkit, etc). You could encrypt your root filesystem, but will have to enter a passphrase on every mount. Then all your friend needs is rocks in a tube sock to get your password...

There ARE ways to secure physical access, but each step just gets more annoying. So find your balance: Short of disk encryption, there is still a trivial way to your data.

As for not having your password encrypted, that's crazy talk. You don't need a password for recovery mode (that's the point). All passwords are hashed, regardless in /etc/shadow.

---

### Post by cariboo on 2009-03-05
The easiest way  to solve the problem of anyone being able to start in recovery mode is to password recovery mode. Use StartUp-Manager to set the password. StartUp-Manager is available in the repositories.

Jim

---

### Post by koenn on 2009-03-05
> **Seq said:**
> Physical access wins.  yes, but there's somewhat of a difference between selecting "Linux (recovery mode)" from a menu and have full control over a working system, or having to dismantle a PC to reset the BIOS,  or pull out the drive to steal some data.

> **Seq said:**
> You don't need a password for recovery mode (that's the point) . No, it's not. Recovery Mode is a single user super-user environment for system maintenance and repair. It makes perfect sense to protect it on a system that is physically accessible.

There's alway a way to work around these things, but at least they'd require more than 3 key strokes.

---

### Post by Seq on 2009-03-05
> **koenn said:**
> yes, but there's somewhat of a difference between selecting "Linux (recovery mode)" from a menu and have full control over a working system, or having to dismantle a PC to reset the BIOS,  or pull out the drive to steal some data.

I see the level of effort required varies, but if the goal was to get your data or get into your system, that difference in effort is minimal. Most computers I've worked on have been simple enough. Even laptops typically only have 1-3 screws to get to the hard disk. We're talking about 30 seconds. If you were a target, a password in grub is not an obstacle.

> **koenn said:**
> No, it's not. Recovery Mode is a single user super-user environment for system maintenance and repair. It makes perfect sense to protect it on a system that is physically accessible.

What if you forgot your password? One could make all sorts of arguments for not doing that, but it does happen (maybe not with you or me, sure).

> **koenn said:**
> There's alway a way to work around these things, but at least they'd require more than 3 key strokes.

Ubuntu's own livecd only needs one keystroke (Depending on language). The issue comes down to this: Adding a recovery password is only going to prevent somebody from booting into recovery mode. If they actually wanted your data, it doesn't stop them. If they did not want your data, then what is the worry.

Now if you were running a lab (school or library) or something along those lines, I could see the desire to restrict grub and boot access, while not caring about privacy (stop the kids from adding themselves to wheel/admin/administrators, or whatever group their OS uses). It stops easy access, and there is (assumingly) either limited physical access to actually get into the machine (a lock, etc) or adequate supervision where this will be noticed.

This doesn't sound like that situation. Feel free to put Grub passwords and BIOS restrictions in, but realize this does not give you security, it just gives you slightly more time to notice and stop a physical breach (assuming you are present).

---

### Post by bodhi.zazen on 2009-03-05
> **riahc3 said:**
> Hey

Today a friend of mine got to GRUB, logged in (I belive) in recovery mode, and using several commands he was able to login with root access/as root without using any password or/and my username. He told me that I didnt have my password encrypted so that why he was able to do it.

My question is how can I change this so only I can log in.

I moved this discussion to recurring discussions as it comes up from time to time and is often debated.

If you wish to use things such as a password on your BIOS or GRUB or what not by all means do so.

BUT I would caution you that in a cracker has physical access these passwords will not do very much (as has been pointed out).

The only real protection you have is to encrypt your installation, and while that may protect your data, it does not stop someone from stealing your hardware and installing any OS they wish.

---

### Post by koenn on 2009-03-05
> **Seq said:**
> I see the level of effort required varies, but if the goal was to get your data or get into your system, According to the OP, to goal was to prevent others from logging in.

> **Seq said:**
> What if you forgot your password? You create a grub command line that bypasses init and boots straight to a root shell without password check.
To prevent others from doing the same, you password-protect grub
To prevent others from booting a live CD or other bootable medium to bypass grub and remove the password protection, you lock the BIOS so the boot medium order can't be changed.
At this point, you can no longer bypass logon protection without tools and preparation. It stops all those that are curious enough to have a go, but usually don't walk around with live cd's and screw driver sets in their pockets.

If someone is determined to break in or steal your data, they still can. If someone is determined to steal your car, they will. Does that mean you leave your car parked with the doors unlocked ? 


> **Seq said:**
> 
 The issue comes down to this: Adding a recovery password is only going to prevent somebody from booting into recovery mode. If they actually wanted your data, it doesn't stop them. If they did not want your data, then what is the worry. I can think of a number of interesting things to do with a root session on a working computer. Set it up as a zombie, a spam bot, a warez server. Set up traps to capture your other passwords, the ones that give accesss to the real good stuff (online accounts, access to vpn's or other computerrs, ...). Set up a backdoor for remote access so I can engage in all sorts of questionable activity from a session on your computer, not mine. 
That's a lot more interesting than stealing a hard disk that probably only contains a music collection, some emails to a girl friend, or a collection of low quality porn. 



> **Seq said:**
> 
Feel free to put Grub passwords and BIOS restrictions in, but realize this does not give you security, it just gives you slightly more time to notice and stop a physical breach (assuming you are present).
As I pointed out, to goal is to build up security, with a few simple measures to block the majority of the cases, and additional  measures for the tougher cases [if it's worth the trouble]. Skipping the simplier stuff, and have everything hinging on disk encryption,  does not give more or better security, but rather less.

---

### Post by smartboyathome on 2009-03-05
> **koenn said:**
> You create a grub command line that bypasses init and boots straight to a root shell without password check.
To prevent others from doing the same, you password-protect grub
To prevent others from booting a live CD or other bootable medium to bypass grub and remove the password protection, you lock the BIOS so the boot medium order can't be changed.
At this point, you can no longer bypass logon protection without tools and preparation. It stops all those that are curious enough to have a go, but usually don't walk around with live cd's and screw driver sets in their pockets.

If that were so, wouldn't we be in the same position? If you forget your GRUB password, you won't be able to fix it without a livecd. At the same time, others will be able to use that too. If it were me and I had a lot of money, I would just buy a retina scanner and modify GRUB to scan your retina to make sure it is you before allowing you to boot up your computer.

---

### Post by Seq on 2009-03-05
> **koenn said:**
> I can think of a number of interesting things to do with a root session on a working computer. Set it up as a zombie, a spam bot, a warez server. Set up traps to capture your other passwords, the ones that give accesss to the real good stuff (online accounts, access to vpn's or other computerrs, ...). Set up a backdoor for remote access so I can engage in all sorts of questionable activity from a session on your computer, not mine.

That's a lot more interesting than stealing a hard disk that probably only contains a music collection, some emails to a girl friend, or a collection of low quality porn.

Right, which is why I noted that while jaunty will have Home Directory encryption available, it won't stop messing about with the system.

A person who was looking for a machine to compromise for actual nefarious purposes (online accounts, proxying nefarious activities), this is the kind of person that would go the extra few steps to do it. After all, they are actually benefiting from it now, so there is more incentive.

---

### Post by Seq on 2009-03-05
> **smartboyathome said:**
> If it were me and I had a lot of money, I would just buy a retina scanner and modify GRUB to scan your retina to make sure it is you before allowing you to boot up your computer.

Biometrics are good for identification, but not authentication. Retina scanning would be more secure than fingerprint scanning as there is no physical residue left over, but again assumes that you are in possession of both of your eyes. All it takes is one determined criminal with a spoon, and your security is lost! :)

---

### Post by Seq on 2009-03-05
You've probably all seen this, but discussing merits of security and encryption was summed up by [XKCD's Encryption comic]("http://xkcd.com/538/")

---

### Post by koenn on 2009-03-05
> **smartboyathome said:**
> If that were so, wouldn't we be in the same position? If you forget your GRUB password, you won't be able to fix it without a livecd. At the same time, others will be able to use that too. .
Hence the BIOS password, that prevents others from setting "boot from CD', but not me. But if I forgot the BIOS password, ...  and so on, ad infinitum.

You seem to fail to see how all these measures complement and enhance each other. That's why people say security consists of layers.  
It also is a matter of trade-offs : If I didn't have a computer, I wouldn't have to worry about others logging in as root. I would also be missing a lot of fun, and a job.

---

### Post by koenn on 2009-03-05
> **Seq said:**
> 
A person who was looking for a machine to compromise for actual nefarious purposes (online accounts, proxying nefarious activities), this is the kind of person that would go the extra few steps to do it. After all, they are actually benefiting from it now, so there is more incentive.
yes, but 
a/ they're not the ones interested in stealing your hard disk, which was sort of the point you were trying to make

b/ I'll go back to the car analogy : just because there are thiefs out there who are determined enough to bring in a tow truck if that's what it takes to steal your car; or just because  a thief can probably pick your lock and hotwire your car in under 5 minutes, does that mean it is a good idea to leave your car unlocked and with the keys in the ignition whenever and where ever you park it ?

---

### Post by bodhi.zazen on 2009-03-05
LOL, good thing I moved this thread.

> **koenn said:**
>  <clip> Skipping the simplier stuff, and have everything hinging on disk encryption,  does not give more or better security, but rather less.

I do not know how you can say that. I will put my encrypted install up against your "simpler stuff" (I assume you mean a BIOS and GRUB Password) any day of the week.

Is it impossible to crack encryption, of course not. But sure is wicked hard.

I see two fallacies in the arguments here :

1. The flaw with the car analogy is that I do not park my computer on the street.

2. I am not saying there is no role for BIOS and GRUB passwords, as has been pointed out, and rightly so, they can help.

It is just that, IMO, their value is over rated and if you are relying on them or advocating their use you should also understand their limitations and how easily they are defeated.

Physical access == bad news, no two ways about it.

---

### Post by koenn on 2009-03-05
> **bodhi.zazen said:**
>  I will put my encrypted install up against your "simpler stuff" (I assume you mean a BIOS and GRUB Password) any day of the week.It's bed time in Belgium so if it's a pissing contest you're looking for, that'll have to wait

> **bodhi.zazen said:**
> 
1. The flaw with the car analogy is that I do not park my computer on the street.
The flaw with this rebutal is that I don't run an operating system on my car. 


> **bodhi.zazen said:**
> 
2. I am not saying there is no role for BIOS and GRUB passwords, as has been pointed out, and rightly so, they can help.

It is just that, IMO, their value is over rated and if you are relying on them or advocating their use you should also understand their limitations and how easily they are defeated.
 It should be clear from my posts in this thread that I fully understand the limitations of BIOS and GRUB passwords - I practically gave instructions on how to bypass them. In doing so, I also provided the context of what their intended use is. I don't see why you have a problem with that.

---

### Post by cardinals_fan on 2009-03-05
The Recovery Mode option provides a free root login.  Insecure?  Yes, but if they have physical access you're screwed anyway.  Encrypt your sensitive files - I see encrypting the whole drive as a waste of time.

---

### Post by ac7ss on 2009-03-05
> **koenn said:**
> At this point, you can no longer bypass logon protection without tools and preparation. It stops all those that are curious enough to have a go, but usually don't walk around with live cd's and screw driver sets in their pockets.

If someone is determined to break in or steal your data, they still can. If someone is determined to steal your car, they will. Does that mean you leave your car parked with the doors unlocked ?



I actually walk around with ALL the tools you would need, including (in my car) security bits.

The point is:
[LIST]
[*]Encrypt sensitive data (with strong password)
[*]Secure the physical machine.
[*]Use a firewall.
[*]Check logs. (/var/log/auth.log in particular)
[/LIST]

I caught someone trying to run some software on my machine (a port scan for an entire class A network) due to my watching the net traffic gauge. It taught me a bit about locking down the system.

---

### Post by riahc3 on 2009-03-05
WOW This topic has gotten big...

Ill try to reenact again: (forget about the BIOS). He simply in the GRUB menu activated something (not sure if it was recovery; doesnt matter) and he got root access. How can I prevent this, being or not being in recovery mode?

---

### Post by cardinals_fan on 2009-03-05
> **riahc3 said:**
> 
Ill try to reenact again: (forget about the BIOS). He simply in the GRUB menu activated something (not sure if it was recovery; doesnt matter) and he got root access. How can I prevent this, being or not being in recovery mode?
The easiest option is to edit your /boot/grub/menu.lst and remove the recovery line.  WARNING: IF YOU SCREW UP, YOUR SYSTEM MAY NOT BOOT.  So be careful and do your homework before messing with it.  There is a graphical tool (don't remember the name) that will do the same - it's in the Ubuntu repos.

This still doesn't do that much good.  Someone could still boot a live CD and chroot into your system.  The best option for real security is for you to encrypt your sensitive data (or the whole drive, but that's a bit more demanding).  It could still be cracked with physical access, but should slow someone down a bit.  Also put these files in unexpected places.

---

### Post by riahc3 on 2009-03-06
> **cardinals_fan said:**
> The easiest option is to edit your /boot/grub/menu.lst and remove the recovery line.  WARNING: IF YOU SCREW UP, YOUR SYSTEM MAY NOT BOOT.  So be careful and do your homework before messing with it.  There is a graphical tool (don't remember the name) that will do the same - it's in the Ubuntu repos.

This still doesn't do that much good.  Someone could still boot a live CD and chroot into your system.  The best option for real security is for you to encrypt your sensitive data (or the whole drive, but that's a bit more demanding).  It could still be cracked with physical access, but should slow someone down a bit.  Also put these files in unexpected places.

In this case, besides removing or not the recovry mode, is there a way to only allow login in the system with a username and password?

---

### Post by koenn on 2009-03-06
> **riahc3 said:**
> In this case, besides removing or not the recovry mode, is there a way to only allow login in the system with a username and password?
yes, put a password on the recovery mode, and/or the recovery mode menu item in grub. People have posted links to howtos earlier in this thread.

---

### Post by bodhi.zazen on 2009-03-06
> **riahc3 said:**
> WOW This topic has gotten big...

Ill try to reenact again: (forget about the BIOS). He simply in the GRUB menu activated something (not sure if it was recovery; doesnt matter) and he got root access. How can I prevent this, being or not being in recovery mode?

You have 3 option, listed in order of my opinion.

#1 - use the alternate CD and install with encryption. You will then need a password and/or key to both boot and access your data.

#2 - Put a password on your BIOS and GRUB. I consider this helpful in that it will deter casual booting, but it will not do much, if anything, to stop anyone with a few simple tools from boot your computer anyways and will not protect your data the way encryption will.

#3 - Remove, or comment out the stanzas in /boot/grub/menu.lst with "recovery mode" listed in them. Honestly this is about equal to #2 in terms of security.

And last, #4, set a root password. This is not really the best choice, but if you do that you will be asked a password (for root) when booting to recovery mode. As with #2 &  #3 it is easily defeated and will not protect your personal data.

---

### Post by aysiu on 2009-03-06
* Extremely off-topic, I know * > **bodhi.zazen said:**
> 
Is it impossible to crack encryption, of course not. But sure is **wicked hard.** Your profile says you're in Montana, but this last bit looks very Boston to me :)

* Back on topic *

I kind of see Koenn's point. I proposed a Brainstorm idea to make recovery mode a little less obvious:
[http://brainstorm.ubuntu.com/idea/8679/](http://brainstorm.ubuntu.com/idea/8679/)

Didn't get a lot of support.

I think what Koenn is pointing out is the difference between security, lack of security, and advertising of vulnerabilities. They all produce different outcomes.

If you have excellent security, your computer won't be compromised.
If you have security through obscurity, your computer may not be compromised.
If you advertise security holes, your computer will be compromised.

While you could make the case that security through obscurity isn't effective security, it's at least better than flat-out inviting mischievous people to mess with your computer.

The way I look at it is, there are three kinds of people when it comes to your computer: [list][*]Extremely malicious parties who will do whatever it takes to breach your security and do bad things with your computer[*]Pranksters who just want to mess around with your computer[*]People who are trustworthy and respect your privacy[/list] Yes, the malicious parties won't be stopped by hiding recovery mode, but you at least keep the pranksters out, and the OP's "friend" sounds very much like one of these pranksters, who take more pleasure out of saying "Ha ha. Look how easy that was for me to mess with you" than they would take out of unscrewing all the screws in the computer and removing the battery for two minutes to reset the BIOS password.

---

### Post by cardinals_fan on 2009-03-06
> **riahc3 said:**
> In this case, besides removing or not the recovry mode, is there a way to only allow login in the system with a username and password?
Just remove recovery.  You can't have it both ways - you either allow root login with physical access or you don't.
> **bodhi.zazen said:**
> 
And last, #4, set a root password. This is not really the best choice, but if you do that you will be asked a password (for root) when booting to recovery mode. As with #2 &  #3 it is easily defeated and will not protect your personal data.
I will point out that there is no inherent insecurity in having a root password.  A root login is only dangerous if you use it.

---

### Post by koenn on 2009-03-06
> **aysiu said:**
> ...
Yes, the malicious parties won't be stopped by hiding recovery mode, but you at least keep the pranksters out, and the OP's "friend" sounds very much like one of these pranksters, who take more pleasure out of saying "Ha ha. Look how easy that was for me to mess with you" than they would take out of unscrewing all the screws in the computer and removing the battery for two minutes to reset the BIOS password.
Sums it up quite nicely, although I would still make a distinction between "hiding" recovery mode and putting a password on it. 
Like I said earlier, a combination of BIOS, grub and possibly root password gets you to the point were the workarounds require screwdrivers and such. That rules out the pranksters and the 'crimes of opportunity'. I wouldn't call that "obscurity".

---

### Post by aysiu on 2009-03-06
> **koenn said:**
> Sums it up quite nicely, although I would still make a distinction between "hiding" recovery mode and putting a password on it. 
Like I said earlier, a combination of BIOS, grub and possibly root password gets you to the point were the workarounds require screwdrivers and such. That rules out the pranksters and the 'crimes of opportunity'. I wouldn't call that "obscurity".
Distinction acknowledged.

The point is that there are degrees of security and access. It's not just total easy access or no access at all.

---

