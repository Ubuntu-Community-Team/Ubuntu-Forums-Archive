---
title: "ParolaPass: The Password Generator - Multiple Length, Strength and Type Options!"
date: 2006-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by AgenT on 2006-11-14
[CENTER][SIZE=5]**ParolaPass: The Password Generator**[/SIZE]
From the author of [Bonager: The Boot Scan Manager]("http://www.ubuntuforums.org/showthread.php?t=295262")
[/CENTER]

**ParolaPass is a secure password generator with support for many types of passwords. A very useful utility to fight against identity theft and crackers. Uses very powerful password generation algorithms. ParolaPass uses multiple algorithms depending on your needs.**

Easy to use, easy to install. Two clicks is all you need to do anything in ParolaPass.

**FEATURES:**[LIST]
[*]Ability to generate up to 100 passwords at a time *
[*]Passwords may be up to 100 characters in length *
[*]Notices when passwords are deemed too insecure
[*]7 different password strength options
[*]Different password types, including numbers-only (PIN) passwords
[*]No configuration needed[/LIST]ParolaPass is also very safe to use. No configuration files, no cruft on your hard drive. And removing ParolaPass is easy! Just use your package manager.

**INSTRUCTIONS:**
Before you install, you must download the installation program (deb file) given below.[LIST]
[*]Installation: 1) double-click on the deb file 2) click "Install"
[*]Starting ParolaPass: 1) click Applications -> Accessories -> ParolaPass
[*]Quiting ParolaPass: 1) click File -> Quit (or hit the "X" button)
[*]Using ParolaPass: 1) Choose password strength 2) click "OK"[/LIST]Simple, easy, elegant and fast.

* Please note: it is not recommended to use very high (over 20) password length and a large password count (over 20) at the same time on slower computers.

**FREQUENTLY ASKED QUESTIONS:**
Q: Does ParolaPass support Dapper AND Edgy (and Feisty?)?
A: Yes. ParolaPass now supports both Dapper AND Edgy (and Feisty)!

Q: Does ParolaPass support KDE (Kubuntu)?
A: No, ParolaPass does not support KDE right now. There are no plans for a KDE version of ParolaPass.

Q: Does ParolaPass support XFCE (Xubuntu)?
A: Yes, it should work. However, it has not been tested. Please post your results if you use ParolaPass on XFCE.

**SCREENSHOTS:**
(version 0.1)

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=19390&stc=1&d=1163550913[/IMG]
[weak (but pronounceable) stength]

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=19388&stc=1&d=1163550913[/IMG]
[using PIN option]

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=19389&stc=1&d=1163550913[/IMG]
["uncrackable" passwords]

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=19392&stc=1&d=1163550913[/IMG]
[applications menu location]

**DOWNLOAD:**
**:KS >>> [SIZE=5][ParolaPass v0.1]("http://www.ubuntuforums.org/attachment.php?attachmentid=19391&stc=1&d=1163550913")[/SIZE] <<<:KS**

**REQUIREMENTS:**
python (>=2.4), python-gnome2 (>=2.14.2), python-gtk2 (>=2.8.6), apg (>=2.2.3)

**SUGGESTIONS, CRITICISMS & FEEDBACK:**
Please make suggestions and criticisms in this forum. Any feedback about ParolaPass is VERY much appreciated!

---

### Post by PriceChild on 2006-11-16
Very nice... I'll have to try this out soon.

---

### Post by DC@DR on 2006-11-16
Does it have the function to store the generated passwords and protect those by a master password? Since with "uncrackable" pass, it's also "immemorizable" pass, then it's inconvenient to store the generated pass elsewhere. However, this app is definitely useful :)

---

### Post by AgenT on 2006-11-16
> **DC@DR said:**
> Does it have the function to store the generated passwords and protect those by a master password? Since with "uncrackable" pass, it's also "immemorizable" pass, then it's inconvenient to store the generated pass elsewhere. However, this app is definitely useful :)
Never thought of making ParolaPass function in this way. It is true that an "ucrackable" password is also one that is very hard to memorize (although, with enough time, it is memorizable). This is why there are levels of strength presented. Also, the "Strongest" strength differs greatly with "Very Strong" because the latter does not include non-standard characters. Yet "Very Strong" produces very strong passwords that are very difficult to crack but are much easier to memorize.

There is one cavet in making an addition to ParolaPass such as you describe: this feature already exists in GNOME by default (at least in Ubuntu). The Keyring Manager is made for one function: memorizing passwords and hiding them behind a master password. The Keyring Manager is also tightly integrated with GNOME so that it can be used with a lot of programs.

This makes the combination of ParolaPass and Keyring Manager a great one. It is because Keyring Manager already exists that maybe it would not be a good idea to include the same functionality into ParolaPass. What do you think?

---

### Post by stalefries on 2006-11-16
Maybe you should do some ParolaPass and Keyring Manager integration.

---

### Post by sonny on 2006-11-17
This is a great app... you can include an option for "forced" letters, for example if I want the password to include my nickname and my birthday and the password to be 20 characters long, it'll generate something like: ?"040983_[sonny]_?yh that way the password would be more easy to remember.

---

### Post by ciscosurfer on 2006-11-20
Looks like a fantastic app (functions like one, too!)

Good Job!

---

### Post by mssever on 2006-11-21
> **AgenT said:**
> Never thought of making ParolaPass function in this way. It is true that an "ucrackable" password is also one that is very hard to memorize (although, with enough time, it is memorizable). This is why there are levels of strength presented. Also, the "Strongest" strength differs greatly with "Very Strong" because the latter does not include non-standard characters. Yet "Very Strong" produces very strong passwords that are very difficult to crack but are much easier to memorize.

There is one cavet in making an addition to ParolaPass such as you describe: this feature already exists in GNOME by default (at least in Ubuntu). The Keyring Manager is made for one function: memorizing passwords and hiding them behind a master password. The Keyring Manager is also tightly integrated with GNOME so that it can be used with a lot of programs.

This makes the combination of ParolaPass and Keyring Manager a great one. It is because Keyring Manager already exists that maybe it would not be a good idea to include the same functionality into ParolaPass. What do you think?

I find the Gnome keyring manager to be the most annoying part of Gnome. Granted, I haven't used it broadly, but it appears to be impossible to change a password--even the master password--without a bunch of hacking. I use WPA on my wireless network, so I'm forced to use network-manager-gnome, as the standard tools are too dumb to understand WPA. When you enter the network key into nm-applet, the keyring manager pops up and requests a password, which can't be changes, as far as I can tell. Furthermore, I can't change my WPA key, because the keyring manager has it buried somewhere inaccessible. And it isn't just that it's encrypted. It can't be accessed or changed at all through any discoverable means.

I'd hate to see any other apps touch the keyring manager given how broken it is.

---

### Post by mssever on 2006-11-21
> **AgenT said:**
> **FREQUENTLY ASKED QUESTIONS:**
Q: Does ParolaPass support Dapper AND Edgy (and Feisty?)?
A: Yes. ParolaPass now supports both Dapper AND Edgy (and Feisty)!
[B]
<snip>

[/B]**REQUIREMENTS:**
python (>=2.4), python-gnome2 (>=2.14.2), python-gtk2 (>=2.8.6), apg (>=2.2.3)
I'm running Dapper with python-gnome2 version 2.12.4-0ubuntu1. A later version isn't available in any repository I have (including dapper-backports). You say that ParolaPass supports Dapper. How can I get the needed dependencies?

EDIT: I installed it on my Edgy machine--I like it. Now, if I could only use it on my main machine, which I haven't yet been willing to risk upgrading.

---

### Post by AgenT on 2006-11-21
> **mssever said:**
> I'm running Dapper with python-gnome2 version 2.12.4-0ubuntu1. A later version isn't available in any repository I have (including dapper-backports). You say that ParolaPass supports Dapper. How can I get the needed dependencies?

EDIT: I installed it on my Edgy machine--I like it. Now, if I could only use it on my main machine, which I haven't yet been willing to risk upgrading.Thank you for pointing this out. It may have been a mistake in the dependency requirements. I will look into it.

---

### Post by AgenT on 2006-11-21
> **stalefries said:**
> Maybe you should do some ParolaPass and Keyring Manager integration.
If you have any specific ideas, please list them. 

Right now, the only integration that I can think of would be to open up KeyRing Manager and that type of integration is not very appealing. Think about it: all you need to do is open KeyRing Manager yourself and copy/paste the password. It is not that difficult. Further integration is not possible because ParolaPass cannot guess what you are going to use that password for. You have to make that choice yourself and you can easily do that in Keyring Manager.

---

### Post by AgenT on 2006-11-21
> **sonny said:**
> This is a great app... you can include an option for "forced" letters, for example if I want the password to include my nickname and my birthday and the password to be 20 characters long, it'll generate something like: ?"040983_[sonny]_?yh that way the password would be more easy to remember.

Is this what you would like it to do: 1) enter a string such as "sonny" 2) select length such as 15 and 3) select numbers only. Output looking like this (assuming only 1 password is printed):
```
4569sonny593234
```
Is this correct? If so, then is this feature really needed? It would 1) require time to implement and 2) confuse users with options that are not really needed.

The reason for this is that you can have the exact same result if you do the following: take your string, sonny, and count the characters: 5. Take your length (15) and subtract 5 then use that as your string length (10). You will receive this password:
```
4569593234
```
Now just split it anywhere you want and automatically add your string (sonny). Done.

It only takes two very small extra steps to accomplish taking about 5-10 seconds. The two steps: 15 - 5 = 10 and combining "sonny" with the output.

What are your thoughts on this? Do you still think such a feature should be included? Maybe you were thinking of different?

---

### Post by Jefim on 2006-11-26
Hi, this program is really great! I like it, since I need to "create" passes all the time (I've created a javascript, which generates passes, but it's not the same - your program is better :D).
Anyway, the program is very nice - simple yet handy. Now, I have a feature request, which should be easy to implement. Sometimes, I have to create simple-to-speak passwords. By "simple-to-speak" I mean passes, that are easy to pronounce - "bicefobu", "ladawino", "koritami" and such (the idea is simple - first character is consonant, second is a vowel, third is again consonant, 4th is again vowel etc. - you get the point). All the characters should be either lower-case or upper-case (otherwise they would be hard to remember). So, can you add such functionality?
It should be simple to implement and you have to add 1 chiose to the parol strength control.

---

### Post by AgenT on 2006-11-26
> **Jefim said:**
> Hi, this program is really great! I like it, since I need to "create" passes all the time (I've created a javascript, which generates passes, but it's not the same - your program is better :D).
Anyway, the program is very nice - simple yet handy. Now, I have a feature request, which should be easy to implement. Sometimes, I have to create simple-to-speak passwords. By "simple-to-speak" I mean passes, that are easy to pronounce - "bicefobu", "ladawino", "koritami" and such (the idea is simple - first character is consonant, second is a vowel, third is again consonant, 4th is again vowel etc. - you get the point). All the characters should be either lower-case or upper-case (otherwise they would be hard to remember). So, can you add such functionality?
It should be simple to implement and you have to add 1 chiose to the parol strength control.
This is already an option in ParolaPass. Strengths "Very Weak" and "Weak" both produce pronounceable passwords. Thank you for pointing this out as it shows that users are not aware of this feature. I will try to make it easier to understand in the program.

And just so you know, the consonant/vowel alterations are very English and Romantic language centric. In other languages, such strings are not easy to pronounce and consonant/consonant/vowel or some other combinations is easier for them.

Thank you for your feedback.

---

### Post by mssever on 2006-11-26
Here's another feature request: Would you consider making a command line interface to the program that's suitable for use in scripts? I'm thinking of a situation in which I want to present users (eg, a website) with a list of passwords from which they must choose one, in order to prevent weak passwords. Obviously, firing up a GUI won't cut it for such a purpose.

My idea is that it could take the parameters --strength --length --count and write the generated passwords to stdout, one per line.

---

### Post by AgenT on 2006-11-26
> **mssever said:**
> Here's another feature request: Would you consider making a command line interface to the program that's suitable for use in scripts? I'm thinking of a situation in which I want to present users (eg, a website) with a list of passwords from which they must choose one, in order to prevent weak passwords. Obviously, firing up a GUI won't cut it for such a purpose.

My idea is that it could take the parameters --strength --length --count and write the generated passwords to stdout, one per line.There are a lot of command line programs already available. Two off the top of my head are: pwgen and apg. ParolaPass actually uses apg for password generation because it is very powerful and has some very sophisticated algorithms (why reinvent the wheel?).

---

### Post by mssever on 2006-11-26
> **AgenT said:**
> There are a lot of command line programs already available. Two off the top of my head are: pwgen and apg. ParolaPass actually uses apg for password generation because it is very powerful and has some very sophisticated algorithms (why reinvent the wheel?).

Thanks. I didn't know about those problems (didn't look, really).

---

### Post by Jefim on 2006-11-27
> **AgenT said:**
> This is already an option in ParolaPass. Strengths "Very Weak" and "Weak" both produce pronounceable passwords. Thank you for pointing this out as it shows that users are not aware of this feature. I will try to make it easier to understand in the program.

And just so you know, the consonant/vowel alterations are very English and Romantic language centric. In other languages, such strings are not easy to pronounce and consonant/consonant/vowel or some other combinations is easier for them.

Thank you for your feedback.

Hmmm... OK, now I understand that. I suppose, that I'll use these functions then (this vowel/consonant scheme was just a tradition of mine :) ). But really, you should write short reviews of options available in your app.

---

### Post by lizzardS on 2007-06-06
Hmmm.  I have downloaded the application but can't seem to find it to install? I am running the feisty fawn.  I had the same issue with apg.  (Which I apt-getted)  Any suggestions?:?:

WHOOP!  Never mind ! I found it... my bad!

---

### Post by sci-fi guy on 2007-10-25
Two questions:
Does this work on Gutsy?
...with 64-bit?

---

### Post by dannet on 2007-10-31
Thank you for the app, its **very** useful... 

> **sci-fi guy said:**
> Two questions:
Does this work on Gutsy?
...with 64-bit?

Im using it in Gusty and yes, it works perfectly.. :)

---

### Post by FattyCNS on 2007-11-03
Thanks! This is exactly what I was looking for.

---

### Post by imT on 2008-01-22
> **FattyCNS said:**
> Thanks! This is exactly what I was looking for.

:) i wanned to wrote a similar thing...:lolflag:
thanks, grate app :popcorn:

---

### Post by jdanov on 2008-05-21
Great THANK YOU :guitar::guitar::guitar:

---

### Post by tanis.mezzelfo on 2008-10-01
Great!

---

### Post by Lars_W_Tierp on 2009-02-11
Thanks alot!
Came in really handy a couple of minutes ago.

---

### Post by coolglobal on 2009-02-20
This should be available in synaptic.

---

### Post by Ascenti0n on 2009-02-28
Thank you AgenT - this is very cool, simple and 'does what it says on the tin'. I use this now as well as APG. :)

---

### Post by nonanano on 2009-03-24
This is a great app which is almost perfect.

Perfect would be:
- allowing me to set defaults length, count and strength as I currently have to change all three every time I start the app, but I always change them to the same settings.
- giving me another option that will just generate the passwords on program launch (although this would only work if the first feature was added).

---

### Post by vagrale13 on 2010-03-17
Very nice!! 

I tasted with:
-** Ubuntu Karmic 9.10** *32bit*
-** Ubuntu Lucid**** 10.04 *Alpha3*** *32bit*
-** Xubuntu ****Karmic ****9.10** *32bit*

and works fine! :D

---

