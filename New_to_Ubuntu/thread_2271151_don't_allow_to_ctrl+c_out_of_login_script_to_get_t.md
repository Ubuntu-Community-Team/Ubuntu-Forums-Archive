---
title: "don't allow to ctrl+c out of login script to get to a prompt"
date: 2015-03-27
forum: New to Ubuntu
---

### Post by ben5 on 2015-03-27
I want to make it impossible for someone to get to a normal shell prompt.   I want to give some options in the login script they can select but if they press ctrl+c I want the terminal to close instead of giving them a prompt.  Is this possible?

---

### Post by DuckHook on 2015-03-28
I don't know what your situation is, but my question is: why would you want to do this? Disabling shell access is a nuclear option. Disabling <Ctrl>+<c> is only scarcely less severe. A robust system is designed to allow the user to kill a rogue process. You don't want to leave yourself the only option of physically pulling the plug. However, if you are intent on doing this, then [here]("http://askubuntu.com/questions/359301/how-to-login-desktop-without-being-interrupted-by-ctrlc") and [here]("http://askubuntu.com/questions/477474/prevent-command-from-stopping-when-pressing-ctrlc") are simple instructions to change the proper config files and disable <Ctrl>+<c> at login.

---

### Post by sisco311 on 2015-03-28
How do you start your login script?

---

### Post by ben5 on 2015-03-28
> **DuckHook said:**
> I don't know what your situation is, but my question is: why would you want to do this? Disabling shell access is a nuclear option. Disabling <Ctrl>+<c> is only scarcely less severe. A robust system is designed to allow the user to kill a rogue process. You don't want to leave yourself the only option of physically pulling the plug. However, if you are intent on doing this, then [here]("http://askubuntu.com/questions/359301/how-to-login-desktop-without-being-interrupted-by-ctrlc") and [here]("http://askubuntu.com/questions/477474/prevent-command-from-stopping-when-pressing-ctrlc") are simple instructions to change the proper config files and disable <Ctrl>+<c> at login.

Thanks much! stty intr undef is exactly what I needed!
To answer your question: This is in a market research call center (we do phone surveys) where we have a hundreds low level employees who do the interviewing and who, to be perfectly blunt, can't be trusted.  I realize they are probably ignorant of the fact they could use ctrl+c or of how to do anything at a command prompt... and they are in a limited shell anyway... but I would feel better if they have no access to a command prompt.  

I shouldn't ever need to pull the plug.  I can ssh into these machines remotely and kill any process I need to.

---

### Post by DuckHook on 2015-03-28
> **ben5 said:**
> Thanks much! stty intr undef is exactly what I needed!
To answer your question: This is in a market research call center (we do phone surveys) where we have a hundreds low level employees who do the interviewing and who, to be perfectly blunt, can't be trusted.  I realize they are probably ignorant of the fact they could use ctrl+c or of how to do anything at a command prompt... and they are in a limited shell anyway... but I would feel better if they have no access to a command prompt.  

I shouldn't ever need to pull the plug.  I can ssh into these machines remotely and kill any process I need to.Immediately after my post, it occurred to me that you might be trying to create some sort of kiosk environment where disabling such functionality is a necessity. Thanks for the update. For the benefit of future users, kindly mark thread "solved".

---

