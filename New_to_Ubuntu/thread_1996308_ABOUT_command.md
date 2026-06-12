---
title: "ABOUT command"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by XeNaRaTiON on 2012-06-04
hi i am a new user in ubuntu. what does it mean by $ **sudo**.

---

### Post by orange2k on 2012-06-04
Sudo gives you temporary superuser powers (so called root powers) so you're able to change your system in a way normal users can't...:p

---

### Post by coffeecat on 2012-06-04
@XeNaRaTiON, have a read of this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You might want to bookmark the link too. :)

And welcome to the forum!

---

### Post by mcduck on 2012-06-04
It's short for "**S**ubstitute **U**ser **DO**", a command that allows you to execute the following commands as some other user.

If you don't specify any other user, it assumes you want to run the command as root (the main admin account of a Linux/Unix system). Using sudo this way is pretty much the basic idea of Ubuntu's way to administer the system, giving admin users the power to do what they need to do while at the same time preventing them from using full admin rights when they are not needed.

For better and more detailed explanation, you should read this document: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by shafi.dude99 on 2012-06-04
> **XeNaRaTiON said:**
> hi i am a new user in ubuntu. what does it mean by $ **sudo**.

try reading man page about sudo

man sudo

---

### Post by 3rdalbum on 2012-06-04
A lot of good replies already. I'll just mention that 'sudo' is only to be used on commands that need root access. Installing software, modifying system files, basically things that affect the whole system. Don't use 'sudo' for things that happen entirely in your own home directory, or you'll run into problems.

If unsure, try running your command without 'sudo'. If it works, then that's fine. If it says "permission denied" or something similar, then try it with 'sudo'.

---

### Post by sandyd on 2012-06-04
> **shafi.dude99 said:**
> try reading man page about sudo

man sudo

Stop pointing people towards the man docs.
They are useless for non-technical users.

Instead, point to the wiki, as others above have done.

---

### Post by shafi.dude99 on 2012-06-04
> **sandyd said:**
> Stop pointing people towards the man docs.
They are useless for non-technical users.

Instead, point to the wiki, as others above have done.

will keep this in mind ... but i love man it shows everything....

---

