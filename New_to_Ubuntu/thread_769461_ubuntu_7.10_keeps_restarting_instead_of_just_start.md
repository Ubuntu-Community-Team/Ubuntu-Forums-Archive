---
title: "ubuntu 7.10 keeps restarting instead of just starting, please help!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by lastwords on 2008-04-26
Ok, so this is most definately my fault... but help would be appreciated. I have been using ubuntu 7.10 (along side vista) on my compaq presario laptop for about a month now. The otherday, my comp (using ubuntu operating system) wasnt responding (because I had left it on for some hours while doing other things) so I shut it down incorrectly by holding down the on/off button... now when it starts up and gives me the option to load either vista or ubuntu, if i select ubuntu it says its performing some kind of scan, then says it failed and restarts, it does this continuely if I try to use ubuntu... please help!

---

### Post by lastwords on 2008-04-26
pppplease help someone! I cant access any of my linux documents or anything... would it help if i wrote down the exact error message its giving?

---

### Post by TeoBigusGeekus on 2008-04-26
Yes it would...
By the way, you can access your linux stuff with the live cd.

---

### Post by Mazza558 on 2008-04-26
> **lastwords said:**
> pppplease help someone! I cant access any of my linux documents or anything... would it help if i wrote down the exact error message its giving?

Yes.

---

### Post by grannyw on 2008-04-26
write the error message

---

### Post by lastwords on 2008-04-26
ok... hang on a sec i'll find a pen and paper and restart my comp in linux and write down the error message! thanks

---

### Post by lastwords on 2008-04-26
ok here goes:

/Dev/sd as contains a file system error
check forded
incodes that were part of a corupted link were found
unexpected inconsistancy
run fsck manually
fsck died exit staus 4
*automatic file system check of the root file system failed
check the root of the file system
a manual file system check should be performed then the system restarted.
the fsck should be performed in the maintainance mode with the root file system mounted in read only.

*root file system currently mounted in read only
a maintance shell will be started after performing this press control D
to terminate maintainance and restart
bash- no job control in this shell
bash- groups- command not found
bash- less pipe-command not found
bash- command- command not found
bash- dircolors-command not found
bash- command-command not found
bash- the- command not found

---

### Post by TeoBigusGeekus on 2008-04-26
After these messages, does your system get to to a maintenance shell or does it boot straight into Ubuntu?

---

### Post by lastwords on 2008-04-26
niether... it does nothing! the message just stays there, I waited for a good 10 minutes and nothing happened.. so I hit control D and it restarted and did exactly the same thing... D:

---

### Post by TeoBigusGeekus on 2008-04-26
> **lastwords said:**
> niether... it does nothing! the message just stays there, I waited for a good 10 minutes and nothing happened.. so I hit control D and it restarted and did exactly the same thing... D:

Can you type anything after the message appears?

---

### Post by lastwords on 2008-04-26
yes... it comes up with the command type prompt thing...
root user @ and my user name... or something like that (sorry I'm back using vista now) thanks so much for bearing with my terrible linux knowledge

---

### Post by TeoBigusGeekus on 2008-04-26
At that command prompt, type
```
fsck
```

---

### Post by lastwords on 2008-04-26
ok... will reboot in linux and try that. Any advice for what will happen/what I should do next?

---

### Post by TeoBigusGeekus on 2008-04-26
The fsck command will check your hard drive for errors and hopefully fix them.
If all goes well and you don't have a hardware problem, Ubuntu will boot normally.

---

### Post by lastwords on 2008-04-26
Yay! Thankyou so much! I cant thankyou enough! now all I have to do is fix my wireless... wish me luck. and have a great day!

---

### Post by TeoBigusGeekus on 2008-04-26
You're welcome!
Don't forget to mark the thread as solved!
Good luck with the wireless, you're gonna need it:)!

---

