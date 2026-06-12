---
title: "Make my Account root"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by KristofferAndreas on 2008-05-10
Hi

Is there any possible way to make my account root so i dont have to write sudo and password when i start something...
and also have auto login...

thx
Kristoffer

---

### Post by SunnyRabbiera on 2008-05-10
well yes, but its generally not advised.
I know it can be annoying from a windows users perspective but its for your own good.

---

### Post by barbedsaber on 2008-05-10
every time you log in as root, god kills a kitten.
and a penguin.

if you want auto login for your normal account, go to system,> administration > login window > security and tick enable automatic login.

---

### Post by KristofferAndreas on 2008-05-10
I have enabled auto login...
I want to have root privileges so i dont have to type in password and sudo...
can someone tell me how? if it not smart i guess i have to learn the hard way...

thx

---

### Post by barbedsaber on 2008-05-10
trust me when I say you are better off typing in your password, if its really bothering you, give yourself a really short password, but dont run as root. Please, thing of the kittens, and penguins.

---

### Post by eragon100 on 2008-05-10
system -> administration -> login window

Go to tab "security" and tick the box "allow local system administrator login".

I believe that should do it:)

---

### Post by UnWarierMage224 on 2008-05-10
It's a very bad idea to log in as root, or use root routinely for whatever.
Take it from me, I hosed my system working as root. BAD. 

The easiest way to work as root, TEMPORARILY, is to use the gksudo command from a terminal (EX: "gksudo nautilus" will launch the file browser with root privileges). Close the terminal, stop being root. 

gksudo whatever will let you work as root for the time being. Again, close the terminal or the program, and you're not root. 

Working as non-root will keep you from accidentally deleting any critical system files. Also keeps you safe from baddies - hackers, usually. IIRC, hackers usually try to break your root account first. 

-'Mage

---

### Post by KristofferAndreas on 2008-05-10
ok, thx if u say so...
but is it possible to remove the are you sure you want to log inn as root or somthing?
i dosent remember what it says so i guessed but u now what i mean?

thx

---

### Post by Separ on 2008-05-10
You should generally not have to run many things as root. If you need to run multiple commands as root in terminal, use *su*. A lot of programs will also not run if you are root because of safety reasons as I found out with trying to start UnrealIRCd accidentally while still in super user mode.

---

### Post by eragon100 on 2008-05-10
And if you want to use su, you first have to go to:
system -> adminsration -> users and groups and manually set a password for the root user, becasue by default it's something random you can't gues in Ubuntu, because the developers want you to use sudo for everything :)

---

### Post by KristofferAndreas on 2008-05-10
Im new, and i want to remove the messege... is that possible...?

i also thank u for all the tips.. but im gonna learn the hard way..
so please answere the question...

thx

---

### Post by barbedsaber on 2008-05-10
you CAN run as root, but dont. no not even then.

not running as root keeps you safe. But what about programs that need root privileges to run, like apt-get I hear you ask.

well, the very clever developers, came up with sudo, which makes you root for a short time, and only for a particular program, this helps keep you safe.
and a bit of trivia, **sudo** means **s**uper **u**ser **do**

---

### Post by kwacka on 2008-05-10
Windows allows users to run with root privileges. This is the major cause of infections from virii, trojans, malware, spyware.

Now, belateldy, Vista introduced 'User access control" and there are idiots turning it off (there are even videos on YouTube to show the REALLY dumb ones how to do it).

That linux doesn't allow users these privileges by default is one of the reasons that linux doesn't.

For me, entering a password is a small price to pay - when you install/upgrade its fairly regular but after a short time you either don't need to do it or stop thinking about it.

BTW, I got flamed the last time I told someone how to do it. Just use the search function to find previous posts.

---

### Post by barbedsaber on 2008-05-10
> **eragon100 said:**
> And if you want to use su, you first have to go to:
system -> adminsration -> users and groups and manually set a password for the root user, becasue by default it's something random you can't gues in Ubuntu, because the developers want you to use sudo for everything :)


when you want to manually set the password, right click root, and, well you should be able to figure it out

dont say we didn't warn you when your system breaks.

---

### Post by KristofferAndreas on 2008-05-10
OK i hear u guys... thx to all of u...

---

### Post by RyanBFS on 2008-05-10
> **barbedsaber said:**
> every time you log in as root, god kills a kitten.
and a penguin.

if you want auto login for your normal account, go to system,> administration > login window > security and tick enable automatic login.

lol

---

### Post by eragon100 on 2008-05-10
Basically, logging in as root doesn't break your pc. However, click ONE wrong button and it's Ooooh-noooo :( :( :cry:
Don't. Ever. Log. In. As. Root, in case you didn't get it yet.

---

### Post by barbedsaber on 2008-05-10
oh, and did I mention that running as root is a BAD idea.

just thought it was worth mentioning.

aliens from mars will come and eat your, skin, and your family. they will also piss on your computer.

---

### Post by KristofferAndreas on 2008-05-10
I G E T I T
:p :p :p

---

### Post by HotShotDJ on 2008-05-10
> **KristofferAndreas said:**
> I G E T I T
:p :p :pVery wise!  Always remember and never forget:  Smart people learn from their own mistakes... Wise people learn from the mistakes of others. ;)

---

### Post by nlz on 2008-05-10
type in terminal

```
sudo passwd root
```

i like being root in the graphical interface.. Especially in multi system network environment you can get really fed up by all the permissions..

---

### Post by nowshining on 2008-05-10
it is annoying at first, however u'll get used to it, also if u want u can

sudo /bin/bash

insert ur pw and be in an all root prompt, and when done u can exit out of the root command viia the command exit.

---

### Post by cardinals_fan on 2008-05-10
> **eragon100 said:**
> And if you want to use su, you first have to go to:
system -> adminsration -> users and groups and manually set a password for the root user, becasue by default it's something random you can't gues in Ubuntu, because the developers want you to use sudo for everything :)
That really annoys me.  Why did they do that?

---

### Post by mister_pink on 2008-05-10
They didn't set it as something random - they didn't set it at all. The account is disabled. This is much more secure because you cant crack a disabled account! Also its because using the root account is completely unnecessary. 

Also, to people offering help, I believe its official forum policy not to. [http://ubuntuforums.org/showthread.php?t=765414&highlight=enabling+root+account+policy](http://ubuntuforums.org/showthread.php?t=765414&highlight=enabling+root+account+policy)

---

### Post by barbedsaber on 2008-05-10
oh, well, you didn't see me here.

/turn around and flee.

---

### Post by nowshining on 2008-05-10
the only way into root that not's blocked is press esc at the keyboard when grub starts the count down and choose recovery mode.

---

