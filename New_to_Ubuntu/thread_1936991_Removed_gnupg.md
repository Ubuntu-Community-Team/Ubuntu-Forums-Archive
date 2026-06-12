---
title: "Removed gnupg"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by iamag on 2012-03-07
Hey ubuntu forums, 

Just recently began using linux, having some troubles but none the less cool t use something different, 

well in short, I was deleting programs and typed sudo apt-get remove gnupg and then it prompted me with typing Yes do as I say! instead of just the regular yes or no for removing apps

wellit started deleting alot of things and now I do not have my ubuntu one or my software manager, 

Question is how do i get this all back?!! boy does this suck hope i don have to reformat but i guess if its what i have to do then i a left with no choice 

maybe some someone out there can hlp

thnks!

---

### Post by papibe on 2012-03-07
Try this:
```
sudo apt-get install gnupg
```
Tell us how it goes.
Regards.

---

### Post by raja.genupula on 2012-03-07
for software center
```
sudo apt-get install software-center
```

but why you removed gnupg ?

the remaining software which you have removed you can get from software-center .

---

### Post by iamag on 2012-03-07
hello

thank you to you both for quick replies, i was going to remove to try to reinstall since I was having troubles encrypting a message, maybe this would be a good time to ask that as well 

so i have a key already and i was trying to use Kgpg but when i try to encrypt it gives me some error hence why i was trying to reinstall everything, any ideas on what im doing wrong or do you know of any alternative programs for encrypting messages? 

I was a windows user prior to this and it was simple linux is definitely a new game to me

---

### Post by iamag on 2012-03-07
double

---

### Post by iamag on 2012-03-07
ok now it is saying that sudo apt-get is not a command ha.. i must have really messed something up

edit:

sudo: apt-get: command not found is the exact line in terminal

---

### Post by mörgæs on 2012-03-07
Changed the title to a more informative one.

---

### Post by mastablasta on 2012-03-07
ouch... you removed the packaging tool?
 
the easiest way might be to reinstall the OS (not reformat but only install over the current version).

---

### Post by raja.genupula on 2012-03-07
yeah reinstall is the only way i think

---

### Post by iamag on 2012-03-07
thank you for changing the title I apologize for that and will make sure to take note for the future, 

alright well definitely a learning experience from this 

how do i go about installing the OS over the current without reformatting, I do have the data backed up but 
i would hate to have to do this all over again 

I have the iso on CD so do i have to just run the CD and install? im such a noob!!?!?!?

---

### Post by mörgæs on 2012-03-07
Good :-)

For reinstalling: Did you read the link in my signature?

---

### Post by iamag on 2012-03-07
which link do you mean i see there are several ones 

also will the update delete any of the programs on my machine? 

I appreciate the immediate feedback it is great help to me

---

### Post by mastablasta on 2012-03-07
the very bottom one.

if you reinstall (but not reformat the drive) it should only return it into the state it was first in. porgramms should stay there. I mean i never tried it in Linux but it windows it's liek that. maybe a short cut will be necessary here and there, but for the most part.... you just overwrite the stuff that was there on install. and also it will/should add the missign libraries that you accidentally uninstalled.

---

### Post by iamag on 2012-03-07
Ok i just dont want to make anymore mistakes 

this is where im looking right now [http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
which is the last link in morts signature, 

am i supposed to do this?

**7 - Installation.**

Remove all unnecessary USB devices before installing, but keep the internet cable attached.

Boot with the Ubuntu version of your choice and follow the instructions  on screen. If a question does not make sense to you, just follow the  defaults.

If the normal CD gives trouble during installation, the first step is  trying the alternate (text-based) install CD in stead. The finished  system will be the same, the only difference is that the installation  process itself has another look and feel.

After a boot, Ubuntu will ask for permission to download and install bugfixes. Approve everything here, but [COLOR=Red]don't install closed-source graphics drivers[/COLOR],  even if Ubuntu suggests this. Only after a thorough testing and a  number of reboots with open-source drivers, confirming that everything  works, you can experiment with closed-source. The reason behind this is  that closed-source drivers sometimes break the system, so best is to  isolate this kind of error.

---

### Post by iamag on 2012-03-07
still having troubles, 

ahhh!!!

---

### Post by iamag on 2012-03-07
Ok I managed to solve my problem and for anyone who has the same problem in the future and anyone who uninstalls GnuPG and loses software center as well as gets the same error i did when trying to use apt-get 

just go to synaptic file manager and type in apt in the search bar, when it comes it just DL and then retry the apt-get command and it will work, 

thanks for everyone for the input and appreciate all those who attempted to help me hopefully anyone who has this problem in the future can find this and use it!!

best regards,

---

### Post by mörgæs on 2012-03-08
Good, please mark the thread 'solved' using 'thread tools'.

---

