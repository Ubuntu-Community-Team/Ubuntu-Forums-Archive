---
title: "BASH set command"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Aikifuku on 2008-10-18
Hello. I'm really new to using bash and the command line. I've noticed a difference between running the 'set' command on my OS X terminal and running it on my ubuntu terminal. 

on OS X a short list of the shell variables and there values is printed. This fits on one screen.

When I do the same thing in ubuntu I get a huge list of functions and shell variables that fills multiple screens.

Can anyone tell me why this difference occurs? Seems to me both are running bash so both should be set up with similar variables.

---

### Post by cwsnyder on 2008-10-18
You are close.  Both OS X and Ubuntu use the bash shell, but OS X is BSD based, Ubuntu is Linux based.  set the command sets shell and enviromental variables in Linux.  Indeed, Linux can use an enviromental variable to pass information from one program to another.  Variable setup depends on what the environment is.

---

### Post by Aikifuku on 2008-10-19
> **cwsnyder said:**
> You are close.  Both OS X and Ubuntu use the bash shell, but OS X is BSD based, Ubuntu is Linux based.  set the command sets shell and enviromental variables in Linux.  Indeed, Linux can use an enviromental variable to pass information from one program to another.  Variable setup depends on what the environment is.

Let me see if I understand you correctly. BSD can't use environment variables to pass info from one program to another and therefore you don't see function definitions with the set command on OS X?

Thanks for the reply.

---

### Post by scorp123 on 2008-10-19
> **Aikifuku said:**
> Let me see if I understand you correctly. BSD can't use environment variables to pass info from one program to another You misunderstood.

It's just that MacOS X doesn't use this too much. Why would it need to? Most of its GUI programs have their own config settings in the "System Preferences" somewhere somehow and they don't have to make use of such a traditionally UNIX-like mechanism. How many programs on MacOS X even make use of the shell?? Not so many I guess.

On Linux it makes much more sense to set so many variables, there so many more programs around that most likely will indeed make use of those settings.

---

### Post by Aikifuku on 2008-10-19
OOOOOOOOOOOOOOOOHHHHHHHHHHHH!!!!!


Thanks a lot I get it now. I guess I don't really know enough to understand why OS X wouldn't use the shell in the same way as linux. You've been really helpful. Danke. If I wanted to gain a better understanding of how Linux uses the shell where would I look?

---

### Post by scorp123 on 2008-10-19
> **Aikifuku said:**
> If I wanted to gain a better understanding of how Linux uses the shell where would I look? It uses it. A lot. That's all there is to say. As end-user you don't really have to care about how Linux uses the shell. One might even go so far to claim that all programs on UNIX-like operating systems such as Linux and BSD are in fact shell programs ... that pretty GUI-stuff is just a front-end for the real things that happen on the shell, hidden from your view. See the variation of the "Sith Code" below .... (yes, a few friends and me were obviously drunk when we came up with that ... :D )

... What you should be concerned about is how _you_ are going to use the shell. You should learn how to use it, it's always highly useful to know such stuff.

You could start here:
[http://www.amazon.com/Linux-Dummies-6th-Dee-Ann-LeBlanc/dp/0764579371](http://www.amazon.com/Linux-Dummies-6th-Dee-Ann-LeBlanc/dp/0764579371)

"Linux for Dummies" is written in a very funny and entertaining way and it teaches a few basic things. And as I said: it's highly entertaining. So you'll get plenty of chances to smile and laugh here and there which makes the learning experience much more pleasant. :)


[I]The Sith... ^H^H^H Shell Code

GUI's are a lie, they're just front-ends to the shell.
Through the shell, I gain sudo.
Through sudo, I gain power.
Through power, I gain root.
Through root, my chains are broken.
uid=0 shall free me.[/I]

---

