---
title: "How to disable the 6 gettyes?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by andy_blah on 2008-04-27
How could I disable all the 6 virtual terminals? I never use them and I have seen somewhere that they are eating resources.

---

### Post by cubeist on 2008-04-27
> **andy_blah said:**
> How could I disable all the 6 virtual terminals? I never use them and I have seen somewhere that they are eating resources.

I can't help you turn them off, but I can tell you they use hardly any resources... no cpu and maybe 2 or 3MB of ram...

---

### Post by andy_blah on 2008-04-27
Even if it does not consume so much resources, it would be a waste to have them running without any use. So does anybody know how to disable them?

---

### Post by cubeist on 2008-04-27
> **andy_blah said:**
> Even if it does not consume so much resources, it would be a waste to have them running without any use. So does anybody know how to disable them?

Unless you are severely short of ram (like less than 64MB left (type free -m in a terminal to see how much ram remains)) I would not worry about them at all...they use virtually no system resources...

If you insist on disabling them at boot you will have to mess with aspects of your system that should not be touched by anything less than an advanced user...that being said, there are some tutorials on the web regarding tty's, or a unix system administrator textbook is a good place to begin when altering the "guts" of a system... :)

---

### Post by andy_blah on 2008-04-27
I would not like to "operate" on the current installation of Ubuntu, so I would pass your suggestion. I was thinking rather of a change in a configuration file somewhere in Ubuntu or such. Really, dosen`t anybody know a solution?

---

### Post by cubeist on 2008-04-27
> **andy_blah said:**
> I would not like to "operate" on the current installation of Ubuntu, so I would pass your suggestion. I was thinking rather of a change in a configuration file somewhere in Ubuntu or such. Really, dosen`t anybody know a solution?

There is no configuration file to turn these off at boot... the only way is to change things in your system that may cause you headaches in the future...

Why do you need these off?  They don't DO anything!

---

### Post by andy_blah on 2008-04-27
BECAUSE I want to see for myself if they really have the impact on my computer`s performance, does that finally make you wonder off and to try to solve other threads? Sorry to be so rough but you`re becoming a nuisance.

---

### Post by cubeist on 2008-04-27
a nuisance... nice... I am trying to save you from screwing up your system.

First - they have zero impact on performance... I am not just saying that... they really don't do anything to consume resources.  Disabling a tty will not give you any performance boost whatsoever... anyone that has said disabling them will magically improve your performance is wrong!

Second, if you insist on disabling tty's there are some shorthand tutorials on the web that will tell you how ... it's not hard...but also not an advisable course of action.

Good luck and good day to you sir!

---

### Post by arvevans on 2008-04-27
andy_blah

Everybody seems to be trying to help you not destroy your system.  However, everybody has to do this once or twice in order to develop an appreciation of the consequences.  

Go to a "terminal" screen (the dreaded CLI interface).
Enter "man getty" and read over the man page very carefully.
You will notice that there are references to /etc/inittab, and some other things as well.  Most everything that is configured in /etc/... is text based, so you can play around as long as you have a working system to play with.  

Playing around in this area of Linux can be destructive, but is also very educational.  There are books that talk about the internals of POSIX based operating systems (UNIX, BSD, OS-X, Minix, etc.).  I would suggest that you consult several of these if you are really serious about mucking about in system definition files.

Systems programmers have to start someplace to learn about system internals.  Maybe you are at that point.  I would suggest that you use a second computer as your system internals playground, and don't keep anything critical stored on it...because you may have to totally reload it's OS frequently.

Good luck,

Arv
_._

---

### Post by Oldsoldier2003 on 2008-04-27
go to /etc/event.d
edit the /etc/event.d/tty<#>  scripts and comment out the exec line at the end

restart the computer, or kill the ttys that you edited.

Its always a good idea to keep at least 1 or 2 ttys in case you have an X problem...

---

### Post by Oldsoldier2003 on 2008-04-27
As a side note on the subject, disabling gettys is a very common thing, espcially for people that have low memory installations. In itself disabling gettys is not a system breaker, as long as you leave one for emergencies. people runing xen usually remove the ttys since they are useless to them...

---

### Post by andy_blah on 2008-04-27
> **Oldsoldier2003 said:**
> go to /etc/event.d
edit the /etc/event.d/tty<#>  scripts and comment out the exec line at the end

restart the computer, or kill the ttys that you edited.

Its always a good idea to keep at least 1 or 2 ttys in case you have an X problem...

That`s exactly for what I was looking for! It worked, and also, I listened to your advice and left tty1 open.
I do have myself a low-memory computer (378MB DDR) so that`s why I wanted to try this solution. It did get rid of 2% usage in the memory, so that`s quite satisfactory for me.

Thank-you for your advice, arvevans I may try that one day. Sorry for being rough to you cubeist, but I hate repeating myself.

---

### Post by Lappymode on 2008-08-06
> **arvevans said:**
> andy_blah

Everybody seems to be trying to help you not destroy your system.  However, everybody has to do this once or twice in order to develop an appreciation of the consequences.  

Go to a "terminal" screen (the dreaded CLI interface).
Enter "man getty" and read over the man page very carefully.
You will notice that there are references to /etc/inittab, and some other things as well.  Most everything that is configured in /etc/... is text based, so you can play around as long as you have a working system to play with.  

Playing around in this area of Linux can be destructive, but is also very educational.  There are books that talk about the internals of POSIX based operating systems (UNIX, BSD, OS-X, Minix, etc.).  I would suggest that you consult several of these if you are really serious about mucking about in system definition files.

Systems programmers have to start someplace to learn about system internals.  Maybe you are at that point.  I would suggest that you use a second computer as your system internals playground, and don't keep anything critical stored on it...because you may have to totally reload it's OS frequently.

Good luck,

Arv
_._


Hey! Sorry to bump, but I thought clarifing something was needed:
Since upstart was lastly added, /etc/inittab is not present, so the solution is actually to play with the events as has been adviced.

Best Regards.

---

