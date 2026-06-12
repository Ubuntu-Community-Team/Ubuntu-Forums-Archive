---
title: "[SOLVED] synaptic package manager problem"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by lyni on 2008-07-01
hi, I am trying to download thru synaptic and it was interrupted. now I get this message 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

when I put dpkg --configure -a into the terminal it says 'command not found'
could someone please point me in the right direction as to what I should do?
thank you
lyni

---

### Post by Elfy on 2008-07-01
You need to run it as root

```
sudo dpkg --configure -a
```

What you have forgotten or not realised, is that when you started synaptic you did so as root - when it asked for the password. So it knows that the command should be run as root - and doesn't tell you.

---

### Post by robertchahine on 2008-07-01
go to the applications  pannel>Accessories>Terminal.
Then write this code
```

sudo dpkg --configure -a
```
then it will ask you about your password, type your password.
This should solve the problem

---

### Post by hyper_ch on 2008-07-01
why do people never read the error messages (or search the forums)?

---

### Post by Elfy on 2008-07-01
> **hyper_ch said:**
> why do people never read the error messages (or search the forums)?

Search engines don't work on a clean install :D

He/she did read the error message and tried it but without root rights.

It's a shame the title search thing doesn't work on new threads still as I saw the same title a few days ago :)

---

### Post by robertchahine on 2008-07-01
> why do people never read the error messages (or search the forums)?
You're right, but it's ok, first he has only 10 beans, second it's absolute beginner talk, he's welcome

---

### Post by hyper_ch on 2008-07-01
yeah but still, yesterday there were 3-4 threads with the same error... a simple search first would have solved it ;)

---

### Post by Mornedhel on 2008-07-01
I'm afraid that this is because of the general philosophy behind Ubuntu, that it should be available to even beginner users, to "just work". Now while it seems to me that a distribution that "just works" is great, it will also bring in the people who come straight out of Windows, with no real previous experience with computers, and whose idea of technical information or documentation is their computer-savvy buddy on MSN. [Longer rant here, complete with examples, edited out before I get too angry and banned.]

Oh well. Most people here still are worth it, and if no distribution takes the trouble of being beginner-friendly, Linux will remain an elitist's choice, which is not great either...

---

### Post by robertchahine on 2008-07-01
yep you're right, we should stay friendly (everybody here still friendly)

---

### Post by lyni on 2008-07-01
thank you to all who helped. it has been a bit tortuous but I think I have it corrected now. I am pleased so many of you are willing to assist very new people who are trying to make the best of the ubuntu system and stay away from 'the other' major one. and thanks to the moderators who set up this beginners section for us.
thanks again
lyni

---

