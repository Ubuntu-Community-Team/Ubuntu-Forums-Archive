---
title: "installing programs in home"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by Yakir on 2012-09-16
(moved from Windows 2 years ago, never looked back)

I want to make sure I'm not missing something obvious here:

In the common case of working on our own computers, we're the computer's administrators, and therefore install all sorts of program on a system wide basis (i.e. with sudo in root). But is there any pros or cons to not doing that? Does anyone, at all, install stuff inside their own home directory (like ~/john/bin/program1)? Especially if they are the computer's soul users?

Thanks in advance!!!

---

### Post by newb85 on 2012-09-16
Well, I'm not entirely certain my computer has a soul, but I am my computer's sole user.  ;)

No, I have never had the urge to install a program in my home directory.  I can see absolutely no advantage to doing so, except maybe for not needing administrative privileges to install, update, and remove.  But then, I don't think the package management software is set up to install in the home directory, and I would consider bypassing package management software a much bigger inconvenience than entering my password.

I can imagine that for multi-user setups, it might be a way to limit which users can access what programs, but there's probably a much more intelligent way to accomplish such things.

Of course, everything I've said in this post is just semi-educated speculation.

---

### Post by MG&amp;TL on 2012-09-16
There are solutions such as *zeroinstall* for that problem. But no, generally I install apps system-wide, unless I happen to be building from source, in which case I may sandbox in my ~/code folder. :)

---

### Post by arsenic23 on 2012-09-16
Permissions aren't just about your user.  Different processes are owned by different groups and the programs and library you install need to maintain the proper permissions with 100% accuracy and reliability.

Also by installing programs in the user's directory you open up some folders and maybe even files to write access by the user.  This creates a HUGE security problem if everyone does it since now malware and virus manufacturers can start looking for targets in the vulnerable home directory.

Let's not talk about how messed up it would be adding your /home/user/bin/ directory into the PATH.

Well it's not really that bad.  I install some games and a few java programs into ~/progs just to keep them out of the main filesystem.  I wouldn't want a package manager messing around with them though; recipe for destruction.

---

### Post by mcduck on 2012-09-16
> **arsenic23 said:**
> 
Let's not talk about how messed up it would be adding your /home/user/bin/ directory into the PATH.


It's already automatically included in user's path if you just create the ~/bin directory... ;)

Anyway, I pretty much agree with other points. Making a system-wide install is usually more secure, and makes better use of the system's resources. And of course it's the only way when you are using the package management (whic you of course should be using when ever possible).

However there are some perfectly valid reasons to install some things inside user's home as well. Especially when youa re the only suer of the machine, or the program in question doesn't need to (or shouldn't) be accessible by other users. For example you'd usually want to keep things coming from outside of the package management separated from the rest of the stuff, so you'd install them in user's home (or /opt if you need to install it for multiple users). Things that you are currently developing, or testing, are handy to keep in your own home. And perhaps you end running a different version than what's available through package management, or a game/program that doesn't need any installing but can be run simply by extracting it's files somewhere. (I, for example, keep latest versions of Blender, and also some games and small utility applications and scripts in my own home directory.)

---

### Post by arsenic23 on 2012-09-16
> **mcduck said:**
> It's already automatically included in user's path if you just create the ~/bin directory... ;)

I just meant that having something in your home directory as part of PATH seemed dangerous to me.

---

### Post by Yakir on 2012-09-17
Wow! What an awesome response (all of you). I'm definitely gonna ask more questions here.. Great help!
OK, I got my answer. Thanks!

---

