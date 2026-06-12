---
title: "Physical access is root access"
date: 2009-07-31
forum: Recurring Discussions
---

### Post by musicisbest on 2009-07-31
I'm a noob, running 9.04

Stumbled upon this vid:

[http://www.butterscotch.com/tutorial/How-To-Reset-Your-Password-In-Ubuntu?](http://www.butterscotch.com/tutorial/How-To-Reset-Your-Password-In-Ubuntu?)

It basically shows how to reset password by dropping to root shell on startup and entering "passwd {username} ; it's ridiculously easy and takes about 1 min. assuming you know the username of the account.

How can I disable this feature? Is it doable without adding a BIOS password?

Don't really want to login twice everytime I fire up my laptop, if possible.

Thanks

---

### Post by philcamlin on 2009-07-31
There is no way to "disable" that. It's a fact of life. Anyone with physical access to your computer can become root. As mentioned, encryption is the only option that would be effective.

---

### Post by Dr Small on 2009-07-31
The point is moot, because if a person has physical access to your system, you're up a creek anyway. This can not be preformed without physical access to your system (the guy has to be sitting right at your terminal).

The best way to do this altogether is to fully encrypt your system.

---

### Post by philcamlin on 2009-07-31
> **Dr Small said:**
> The point is moot, because if a person has physical access to your system, you're up a creek anyway. This can not be preformed without physical access to your system (the guy has to be sitting right at your terminal).

The best way to do this altogether is to fully encrypt your system.

ex: BIOS password :popcorn:

---

### Post by Dr Small on 2009-07-31
> **philcamlin said:**
> ex: BIOS password :popcorn:
The BIOS password can be circumvented with physical access, also.

---

### Post by philcamlin on 2009-07-31
> **Dr Small said:**
> The BIOS password can be circumvented with physical access, also.

true but its one more obsticle the person has to get past 
a bios password is a good idea but its not foolproof either

---

### Post by snowpine on 2009-07-31
Don't leave your computer lying around where untrusted people can access it, basically is the bottom line. You can add a bios password, encrypt the drive, etc. but if you have top secret files on there, your best bet is to use a removable/external hard drive and keep it under lock and key. Physical access is total access.

---

### Post by aysiu on 2009-07-31
Physical access is root access.

More details here:
[http://ubuntuforums.org/showthread.php?t=989517](http://ubuntuforums.org/showthread.php?t=989517)

---

### Post by Dr Small on 2009-07-31
> **snowpine said:**
> Don't leave your computer lying around where untrusted people can access it, basically is the bottom line. You can add a bios password, encrypt the drive, etc. but if you have top secret files on there, your best bet is to use a removable/external hard drive and keep it under lock and key. Physical access is total access.

> **aysiu said:**
> Physical access is root access.

+1 to both of you

---

### Post by musicisbest on 2009-07-31
holy crap!...replies in minutes; better than most paid support! Thanks!

------

I think I found an easy solution to protect my data if my laptop is stolen or someone has physical access.  

"ecryptfs&#8208;utils" package and the command "ecryptfs&#8208;setup&#8208;private" 

it created an encrypted folder /home/{username}/private. Behaves like any other folder i.e. encryption/decryption is automatic. When I changed my password via original post, the data there was gone. Same result when booting off live cd.

found this tip in [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

------

noticed some settings in BIOS setup: "setup password" and "power-on password". I'm assuming 2 different passwords, one to allow entering setup and one just to allow boot up. 

There was another option "Drivelock password" , but it was grayed out for some reason (maybe needs original OS that this laptop came with: Vista Business, but that's just a guess).

I need to do more research on BIOS options and how to bypass them. Any links appreciated.

Anyhoo, my data should be safe. I also plan to make it as much a PITA as possible for someone to use this laptop if stolen. And it ***should*** raise a red flag if brought to pc repair shop...i.e. "You set all these passwords and forgot them???"

Thanks again

---

### Post by Dr Small on 2009-07-31
> **musicisbest said:**
> I need to do more research on BIOS options and how to bypass them. Any links appreciated.

Open the case, pull the CMOS battery, give it five minutes, reinstall battery, reboot.

Or, find the CMOS jumper, switch it over, reboot.

---

### Post by musicisbest on 2009-07-31
It's a laptop. According to the service guide, I'd have to remove

hard drive
memory cover
dvd burner
switch cover
keyboard
display assembly
base enclosure

to get access to the RTC battery. Not gonna happen. :) 

I was wondering if it was possible software-wise.

---

### Post by snowpine on 2009-07-31
If it's a laptop, a malicious person could simply steal it, then hack into it at their leisure. :)

---

### Post by snakeman21 on 2009-08-01
> **musicisbest said:**
> holy crap!...replies in minutes; better than most paid support! Thanks!

That's one of the many advantages of being a part of the open source community!  We're all part of a team, and we know that if we help out n00bs, those n00bs will learn more and eventually help out other n00bs.  We all started with the same knowledge about Linux:  Virtually none.  These forums saved my butt many times when I first made the switch to Linux.  Now, in return, I do my part by checking the forum every day and helping as many people as I can.  And no matter how long you've been doing it, there's always something new to learn.  

I hate to sound preachy, but the open source community is such a great thing... We're comprised of countless individuals from around the world, perfectly willing to do whatever we can to help out others, and we expect nothing in return besides a simple, "Thanks for your help."  

Welcome to a whole new world.

---

### Post by Tipped OuT on 2009-08-01
> **Dr Small said:**
> The BIOS password can be circumvented with physical access, also.

Just use a BIOS _and_ hard drive password.

---

### Post by Viva on 2009-08-01
> **snakeman21 said:**
> that's one of the many advantages of being a part of the open source community!  We're all part of a team, and we know that if we help out n00bs, those n00bs will learn more and eventually help out other n00bs.  We all started with the same knowledge about linux:  Virtually none.  These forums saved my butt many times when i first made the switch to linux.  Now, in return, i do my part by checking the forum every day and helping as many people as i can.  And no matter how long you've been doing it, there's always something new to learn.  

I hate to sound preachy, but the open source community is such a great thing... We're comprised of countless individuals from around the world, perfectly willing to do whatever we can to help out others, and we expect nothing in return besides a simple, "thanks for your help."  

welcome to a whole new world.

+1

---

### Post by CharmyBee on 2009-08-01
> **Dr Small said:**
> Open the case, pull the CMOS battery, give it five minutes, reinstall battery, reboot.

Or, find the CMOS jumper, switch it over, reboot.

Some defenses:
- Strip case screws to slow them down. Handy if you have gator grip.
- Build some muscle. 99.9% of the time, a computer compromiser can't match up against beefy muscles. They might even be vulnerable to water guns filled with cold water!
- Downgrade to an old AT case with a key lock that prevents keyboard access.
- Mod your case to appear like an ordinary object for more cover. Bonus points if ordinary object is still functional as intended.
- Have a specially built desk with a computer space that is closable, and lockable. Lock it when not in use. The only way in is picking or just hammering down property in pure frustration (in which you can have more sue opportunity over with)

---

### Post by Tipped OuT on 2009-08-01
> **CharmyBee said:**
> Some defenses:
- Strip case screws to slow them down. Handy if you have gator grip.
- Build some muscle. 99.9% of the time, a computer compromiser can't match up against beefy muscles. They might even be vulnerable to water guns filled with cold water!
- Downgrade to an old AT case with a key lock that prevents keyboard access.
- Mod your case to appear like an ordinary object for more cover. Bonus points if ordinary object is still functional as intended.
- Have a specially built desk with a computer space that is closable, and lockable. Lock it when not in use. The only way in is picking or just hammering down property in pure frustration (in which you can have more sue opportunity over with)

Also, if the OP is using a laptop... there's no way in hell they can mess with his CMOS. :P

---

### Post by snakeman21 on 2009-08-01
> **Tipped OuT said:**
> Also, if the OP is using a laptop... there's no way in hell they can mess with his CMOS. :P

Yes, there is.  It's the same as doing it with a desktop computer, once you pull out some of the components.  It's a little trickier, but the concept is the same.  I know this because someone said the same thing you said... So to find out, I tried it... successfully.  Sure, the battery is a little harder to get to.  But if it's a laptop, as someone already stated, someone will most likely steal it and then crack it "at their leisure"  I think were the words used.  Best bet is physical security, like locking a laptop in a safe that's bolted to the floor.  When I leave the house for long periods of time, I lock my lappy in my gun safe.

---

### Post by aysiu on 2009-08-01
If it's a stolen laptop, wouldn't it be easier to just physically remove the hard drive and put it in an enclosure or another laptop instead of bothering to reset the BIOS by removing the battery?

I do agree that anything you can do to slow down the process will annoy whomever the intruder/thief is, but if your unencrypted laptop is stolen and the thief has any sense, your data is compromised.

---

### Post by lykwydchykyn on 2009-08-01
> **aysiu said:**
> If it's a stolen laptop, wouldn't it be easier to just physically remove the hard drive and put it in an enclosure or another laptop instead of bothering to reset the BIOS by removing the battery?


Darn, you beat me to it!
> 
I do agree that anything you can do to slow down the process will annoy whomever the intruder/thief is, but if your unencrypted laptop is stolen and the thief has any sense, your data is compromised.

I'd add that probably the majority of people who would make off with your laptop could care less about your data.  It's probably headed to the nearest shady pawn shop.

We had a big thing happen here last year where some State government laptops got stolen, which happened to have voter registration data on them for most the citizens of Nashville.  There was a big todo which included the government offering to pay for free "identity protection" service for anyone possibly compromised.  

Turned out they caught the guys who stole the laptops, and they just wanted the hardware to sell for cash.

---

### Post by swoll1980 on 2009-08-01
I agree. If someone with malicious intentions has physical access to your files, there is absolutely no way to secure them. Any thing you do to protect them, will only slow someone down. On top of that it's a laptop. No ones going to sit around trying to hack into your files, they will simply take it, and have as much time as they need to do whatever. Computers are inherently insecure.

---

### Post by aysiu on 2009-08-01
I agree that's *probably* what most thieves want (the hardware, not the data), but if you have any sensitive data, it's still best to play on the safe side and encrypt it instead of relying on BIOS and Grub passwords, which are easily bypassed.

---

### Post by snakeman21 on 2009-08-01
> **aysiu said:**
> I do agree that anything you can do to slow down the process will annoy whomever the intruder/thief is, but if your unencrypted laptop is stolen and the thief has any sense, your data is compromised.

Hence the reason my laptop stays locked up with my guns when I leave home for longer periods of time.  The sad thing about it is that it's really not very hard to do.  I know ten-year-olds that could do it without much of a problem.

---

### Post by bhishan on 2009-10-16
I don't get it ... what's the use of the password protection then?

---

### Post by aysiu on 2009-10-16
> **bhishan said:**
> I don't get it ... what's the use of the password protection then?
Read the thread I just moved your post to.

---

