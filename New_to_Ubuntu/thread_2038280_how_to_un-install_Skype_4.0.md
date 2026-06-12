---
title: "how to un-install Skype 4.0?"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by Old-un on 2012-08-06
My son or daughter installed Skype 4.0 on my Ubuntu Desktop and when i try to run the software it freezes. So i opened up a terminal and typed:

sudo apt-get purge Skype 4.0

After that i restarted the computer but it's still there?

Can anyone help me please!

---

### Post by kr1sti on 2012-08-06
Have you tried un-installing it from the ubuntu software center?

---

### Post by Old-un on 2012-08-06
Hi kr1sti,

When i looked in the Ubuntu Software Center,  Skype was not even installed and i then went to the terminal and typed: sudo apt-get purge skype 4.0.

Obviously something is not working properly but i haven't a clue what?

---

### Post by mastablasta on 2012-08-06
are you sure that the installed package you are trying to purge is named exactly ```
skype 4.0
``` ?

---

### Post by sahabcse on 2012-08-06
some configuration still present in the machine.

Just run the command 

$sudo updatedb

in terminal and try.

else type

$locate skype

and forcefully remove all the skype related files.

---

### Post by little_penguin on 2012-08-06
Have you tried purging it without including the version number? E.g.:
 
```
sudo apt-get purge skype
```

---

### Post by NikTh on 2012-08-06
Hi , 
try this command 
```
sudo apt-get purge skype skype-bin
``` 

skype-bin = little picture of skype in Dash . 
Thanks

---

### Post by Old-un on 2012-08-06
When in a terminal i typed:
sudo apt-get purge skype
and the output was:
Skype is not installed so not removed.

Still in a terminal i then typed:
sudo apt-get purge skype 4.0
and this time there was a long list generated none of which made any sense to me.

Thinking of the dark days when i was a Windows user and failed to un-install a certain program and sometimes the answer was to install the program you wished to remove and then try to remove it which did sometimes work.

Do you think that procedure might work here?

---

### Post by Old-un on 2012-08-06
Just opened a terminal and typed: ```
sudo apt-get purge skype skype-bin
``` which seems to have done the trick because i can't find any instance of Skype.

Thanks for all the help everyone ):P

---

### Post by NikTh on 2012-08-06
Hi , 
glad you solved. 

If you wantmark** thread** **as solved** from **thread tools **
Thanks

---

