---
title: "password problem"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by Mark 53 on 2013-03-28
my laptop a ASUS K52N   AMD 64   needs a password  every time it boots up , the asus  symbol comes up for 1 second then a Blue box , asking for a password ," I know what the password is " , it was set when I set a password in the BIOS , Now I can not get into the bios to remove the password option , does any one know how I can get into the bios to fix this Very annoying problem , I have pressed every thing , combinations of keys numbers you name it , before the blue box comes up ... Please any help , Mark

---

### Post by Mark Phelps on 2013-03-28
This is a problem with using BIOS passwords -- you can easily get locked out of the machine.

If this were a desktop, I'd tell you to remove the battery on the motherboard, short out the CMOS pins, and reboot.  This would reset the BIOS to its default and remove any password.

But, being a laptop, I don't know what else you would do.

---

### Post by Mark 53 on 2013-05-07
Sorry I did not get back quicker  , Thanks for that Mark , maybe when I get a new laptop , so for now  , I will just have to put up with it , Mark

---

### Post by Mark 53 on 2013-05-07
I have this problem with password , like lots of ubuntu uses , changing the  <<<   password  >>> , Administrator password , when you make it so you have NO password , next time you log in , it comes up with , ( you need the password ) I am getting **Very **annoyed with this , there is NO password , can some UBUNTU genius[COLOR=#0000ff]*** PLEASE***[/COLOR]  write a small  program to simple fix this [COLOR=#ff0000]VERY ANNOYING[/COLOR] problem , I can NOT download software , BECAUSE , I need the NONE existing password ,[COLOR=#ff0000]** GRrrrrrr **[/COLOR] , also , if you actually  want to have a password , ubuntu  will NOT allow you to use a simple 1 - 2 - 3 or 4  letter or number password , needs to be longer  ....  Come on guys , Please a bit of common sence for us older Ubuntu fans , any help , Mark

---

### Post by Mark Phelps on 2013-05-07
Your rant is confusing.  

My earlier comments to you were regarding a BIOS password -- because that looked like the problem you're having. The BIOS password, if that is what you're encountering, has NOTHING to do with any OS, Ubuntu or otherwise.  To change the BIOS password on a laptop, you would have to disassemble it to the degree that you could remove the BIOS battery -- NOT a simple thing to do.  Quite obviously, with a hardware problem like this, there is no "small program" anyone could write to fix this.

---

### Post by mcduck on 2013-05-07
The key to enter BIOS setup on K52N is DEL. Just hold it down while turning on the machine.

---

### Post by Lightning Dragon on 2013-05-07
Hi

Are you saying the BIOS has a password lock on it? I would say try removing the battery, but as far as I know it is impossible because the trick doesn't work on your labtop. However, I do have a few tricks you can try to use to bypass the password. When it comes up, press ESC 3 or 4 times. If that doesn't work, press it 3 or 4 times _before_ the password screen appears. You can also try repetitively tapping the Ctrl key as soon as you power on your computer to reset the BIOS to stock and see if the password is gone or reverted back.

The only other option I know of is flashing your BIOS, and which if it is performed wrong, your computer becomes as useful as a rock.

Or are you talking about an actual Ubuntu account log in?

---

### Post by DuckHook on 2013-05-07
As many have already noted, it is not at all clear what your problem is. Is it:

1. The password on your actual hardware (your BIOS), or
2. The password on your operating system (Ubuntu)?

From your post #1, it sounds like your BIOS. But from your latest post, it sounds like Ubuntu. You have already received good advice for the case of a hardware password. Hardware passwords have nothing to do with Ubuntu and you will just have to look up your computer manufacturer documents to see if they have a way of resetting this password.

However, if the situation is that of a software password, then you must appreciate that you are still barking up the wrong tree. I will try to explain why:

A defining difference between almost all Linux distros and Windows is the inherently higher security of Linux. However, this security is only as good as the measures that users are prepared to adopt. Among these measures, one of the most critical is a willingness to adhere to good authentication practices. If you are trying to disable password challenges, then you are destroying a central security measure of Linux and, in essence, trying to turn Linux into Windows. If so, then you are better off just staying with Windows, since it is more mainstream and runs more software than Linux.

Likewise, your request that an UBUNTU genius write a program to nerf Linux security is akin to asking Michelangelo to whitewash the Sistine chapel so as to get rid of the nudity. I'm not even close to a genius, but I have resolved to never give advice that nerfs security. Instead, I try to educate new users about proper security, and it starts with the following links:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

If you nonetheless insist on doing away with your Ubuntu password protection, then you are on your own. I will also add that it will then only be a matter of time before you *are* owned and become one of the army of spambots that infest the Wonderful World of Windows and are the scourge of the Internet.

---

### Post by Mark 53 on 2013-05-09
yes the bios password is the biggest problem , but , as I stated , I will just have to put up with it , save my bucks for a NEW hard drive and start again , thanks for your help Mark , sincerely , Mark

---

### Post by Mark 53 on 2013-05-09
duck hook , why is it that some people love to big note them selves , you had it right in the first 2 of your lines , problem  1     ( my bios password problem  ) and Number 2 line ,   (  Ubuntu administrator password    ) and as for your PARANOID security rant , windows WAS on this laptop , But when I downloaded Ubuntu 12.4 , I deleted windows 7  for my only love ubuntu ..  I have NEVER used microsoft **** and never will , stay cool brother , the only real threat to your life and security IS , the ONLY world terrorist , the  USA  thanks dude ,:) Mark

---

### Post by Mark 53 on 2013-05-09
NO  second prize , I have built 3 computers  , and I have tried all that stuff , Thanks anyway , Mark

---

### Post by Mark 53 on 2013-05-09
yer  been there , thanks , Mark

---

### Post by Kopkins on 2013-05-09
Buying a new hard drive won't fix your problem. The BIOS is **not **a part of the hard drive, it's integrated into the motherboard.

And as someone said the key to enter BIOS on your computer should be the DEL key, so try tapping it or holding it at boot.

---

### Post by dino99 on 2013-05-09
but if that bios is tattoed to only install a MS OS , then change that laptop (guaranty)/sell it & by a new (non tattoed)/file a complaint & ask huge money/....

---

### Post by DuckHook on 2013-05-09
Given constraints of time and knowledge, we have no choice but to make some assumptions about people who post on an Absolute Beginners section since there is no other info to go on. One of those is that they behave with the typical Windows laxity when it comes to security. Even with every intention to help, this involves us in a conundrum when people ask for ways to cripple said security: do we just tell them how, or do we try to educate about the larger issue? Does further enablement of bad practices constitute real help? Perhaps it does. I've just decided that I will offer the larger perspective.

Sorry if I come across as being too full of myself. It was still my intention to be helpful, but you are free to just ignore me if you want.

---

### Post by Zill on 2013-05-10
Mark 53:  In view of the limited information you initially supplied the advice offered on this thread has, IMHO, been appropriate.  DuckHook, in particular, made some excellent points that are very relevant to newbies, many of whom will be searching these forums for good advice.

You are, of course, free to configure your machines as you wish.  Unfortunately, as DuckHook pointed out, *all* us internet users are paying the price for the millions of insecure and mis-configured machines out there!

---

