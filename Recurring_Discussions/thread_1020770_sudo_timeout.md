---
title: "sudo timeout"
date: 2008-12-24
forum: Recurring Discussions
---

### Post by Kinetic_lord on 2008-12-24
I've done this by mistake, i'm showing this so that the developers can fix the bug. 

Type in terminal:

gksudo something (i typed nautlius instead of nautilus)

after that type 

gksudo nautilus 

or gksudo synaptic

it will open it without asking root password. Bad guys can just erase my hard disk this way...

P.S. I've done it by mistake, i have not tried to hack Ubuntu. Please don't give me any penalty points. :)

---

### Post by billgoldberg on 2008-12-24
> **Kinetic_lord said:**
> I've done this by mistake, i'm showing this so that the developers can fix the bug. 

Type in terminal:

gksudo something (i typed nautlius instead of nautilus)

after that type 

gksudo nautilus 

or gksudo synaptic

it will open it without asking root password. Bad guys can just erase my hard disk this way...

P.S. I've done it by mistake, i have not tried to hack Ubuntu. Please don't give me any penalty points. :)

That's called "sudo timeout".

It's set to 15 minutes by default on Ubuntu, what is very, very unsafe.

If you want to disable that:

[http://linuxowns.wordpress.com/2008/10/21/change-gksudo-timeout/](http://linuxowns.wordpress.com/2008/10/21/change-gksudo-timeout/)

---

### Post by jbrown96 on 2008-12-24
After you type a command that requires authentication, the authorization remains for a short time (15 minutes I think). It's no bug.

---

### Post by Rocket2DMn on 2008-12-24
Not a bug.  Not a hack.

sudo and graphical sudo are designed to work this way, see above for how to change the configuration.

---

### Post by davec64 on 2008-12-24
You're alright!

It's not a bug it's by design!

You are doing it all from the same terminal, thereofre once you've entered the password for that terminal it remembers it for next time. This allows you to run a series of commands without having to enter the password again.

If you close the terminal and then open a fresh one you'll need to enter the password again.

I can't remember but there might even be a time limit on the password as well!

---

### Post by artir on 2008-12-24
Ubuntu doesn't have bugs! Those are just undocumented features :P

---

### Post by magmon on 2008-12-24
> **artir said:**
> Ubuntu doesn't have bugs! Those are just undocumented features :P

+1, made me lol

---

### Post by Kinetic_lord on 2008-12-24
Well... not bug, i couldn't find the right word :D. Well, the point is that you can access applications wtih no root pass :D. (and that's not good) :D

---

### Post by Kinetic_lord on 2008-12-24
> **artir said:**
> Ubuntu doesn't have bugs! Those are just undocumented features :P

Right :D!

---

### Post by lykwydchykyn on 2008-12-24
I agree it's unsafe.  However, even with the timeout, you still have people griping that they have to type in their password all the time.

---

### Post by magmon on 2008-12-24
> **lykwydchykyn said:**
> I agree it's unsafe.  However, even with the timeout, you still have people griping that they have to type in their password all the time.

The system is perfectly flawed...

---

### Post by Eisenwinter on 2008-12-24
I think sudo in itself is a security risk, people don't even have to know the root password, they just need to know your regular username's password, and they can do anything.

---

### Post by Rocket2DMn on 2008-12-24
sudo is an extremely powerful tool, esp. in situations where multiple users have access to a machine/server/system.  You can control in a lot of detail what users can and cannot do with the sudo command.  In Ubuntu it defaults to the original user of the system having full admin privileges - this is part of Ubuntu's security model so that users don't have to setup a root password.  Having a root password (and also having to remember that password) is more of a security risk to a system than a user having sudo.
Not having to enter a password *every single time* you run sudo, after running it once, is for convenience.  It is expected that to use sudo and punch in your password, you take that extra second to realize that what you are doing is an administrative task.  sudo can be configured so that you have to enter a password every time, but it would be a major pain to have to deal with for a lot of people.  It's a tradeoff of convenience and security.  It's still your job to protect your computer and your password - if you're in an environment where others have access to your machine, then lock the screen when you step afk.

---

### Post by p_quarles on 2008-12-24
> **Kinetic_lord said:**
> Well... not bug, i couldn't find the right word :D. Well, the point is that you can access applications wtih no root pass :D. (and that's not good) :D

No, you can't access those applications without a root password. You have already entered your password once, and this authenticates you for the next 15 minutes. This behavior is easy to change, if you so wish, and is default for considered and valid reasons. It's not a flaw in the system. 

This is nothing more than a misunderstanding of how sudo works.

---

### Post by TWO on 2008-12-24
> **lykwydchykyn said:**
> I agree it's unsafe.  However, even with the timeout, you still have people griping that they have to type in their password all the time.

Aye. Anyone giving instructions to people using sudo should be telling them to run ```
sudo -k
``` once they're done.

---

### Post by lswb on 2008-12-24
> **TWO said:**
> Aye. Anyone giving instructions to people using sudo should be telling them to run ```
sudo -k
``` once they're done.

Too bad sudo -k doesn't work the way its documentation describes. Try opening 2 termnals, run a command with sudo in each, then issue sudo -k or sudo -K in one of them. The other will still allow sudo commands without password. 

Even worse, run a gui program that requies a password, like synaptic. Regardless of if you use "sudo -k", for the next 15 minutes synaptic will start without a password.

In fact, you can even log out completely and log back in again and still not need a password for sudo within the timeout period.

---

### Post by macogw on 2008-12-24
You can forcibly end the sudo timeout by typing "sudo -k"

---

### Post by p_quarles on 2008-12-24
> **lswb said:**
> Too bad sudo -k doesn't work the way its documentation describes. Try opening 2 termnals, run a command with sudo in each, then issue sudo -k or sudo -K in one of them. The other will still allow sudo commands without password. 

Even worse, run a gui program that requies a password, like synaptic. Regardless of if you use "sudo -k", for the next 15 minutes synaptic will start without a password.

In fact, you can even log out completely and log back in again and still not need a password for sudo within the timeout period.

> **macogw said:**
> You can forcibly end the sudo timeout by typing "sudo -k"

What lswb says is true, though. sudo -k will not close the timeout period for another shell session. At least in 8.10.

---

### Post by red_Marvin on 2008-12-25
> **lswb said:**
> Too bad sudo -k doesn't work the way its documentation describes. Try opening 2 termnals, run a command with sudo in each, then issue sudo -k or sudo -K in one of them. The other will still allow sudo commands without password.
I don't see how that contradicts the documentation, you are running two different shells/prompts, sudo in the first one, won't set the timestamp for the second terminal, you will still be asked for the password.
sudo -k in one of the terminals will in the same way not affect the other terminal. This is even true for two bash prompts running through screen.

---

### Post by lswb on 2008-12-25
> **red_Marvin said:**
> I don't see how that contradicts the documentation, you are running two different shells/prompts, sudo in the first one, won't set the timestamp for the second terminal, you will still be asked for the password.
sudo -k in one of the terminals will in the same way not affect the other terminal. This is even true for two bash prompts running through screen.

Well, here is what the man page for sudo says about -K and -k. I've emphasized 2 things that I feel don't agree with the actual behavior of sudo.
> 
   -K  The -K (sure kill) option is like -k except that it removes the
           user’s timestamp entirely.  Like -k, this option does not require a
           password.

       -k  The -k (kill) option to sudo invalidates the user’s timestamp by
           setting the time on it to the Epoch.  [B]The next time sudo is run a
           password will be required. [/B] This option does not require a password
           and was added to [B]allow a user to revoke sudo permissions from a
           .logout file.[/B]


I don't see anything in there about "unless you happen to have another shell open somewhere" and the logout part is just flat out wrong, IMHO the correct behavior for sudo -k or -K would be to require a password the next time it is invoked, regardless of from which shell session or tty. If -k or -K doesn't do this by design, then it should be explained, and an option that DOES have this behaviour really needs to be added.

---

### Post by red_Marvin on 2008-12-26
Hmm, yes I guess that is a matter of interpretation, I compare it with say, the bash history, that also isn't shared between terminals. But since this confusion *can* arise it seems that there should be a clarification made.

---

