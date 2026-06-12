---
title: "[SOLVED] clam"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by misswham on 2008-09-30
I have a few security questions.  How do I update the clam anti virus and how often should i do an update?  now i went to update signatures.  first off does update signatures mean it is updating the antivirus and when i tried to update it i got this error message and dont know what it means

You must be root to install updates

i am totally new to this and dont know what root means.  

also, if an infection is found will clam get rid of the infection?  i dont want to send a file to a windowz user.  

Can I set it to update itself?

I forgot how I installed clam but it is there under system tools.

---

### Post by Zzl1xndd on 2008-09-30
You need root access to update Clam, try opening a terminal window and typing 

```
gksudo clamtk
```

---

### Post by cariboo on 2008-09-30
Clamav only detects windows viruses, the chance of catching a linux virus in the wild is next to impossible. Have a look at this page:

[http://en.wikipedia.org/wiki/Linux_Viruses](http://en.wikipedia.org/wiki/Linux_Viruses)

All the malware listed on this page needs root access to install it. So the only way you will get infected is you go to the effort of installing it yourself.

Jim

---

### Post by misswham on 2008-09-30
The command worked.  Do i have to always type the command before updating and how often should I update?

---

### Post by Zzl1xndd on 2008-09-30
you could make a launcher with the command in it if you want a short cut, but it will ask you for the password each time. Although as was stated the odds of you getting a virus are slim to none.

---

### Post by doas777 on 2008-09-30
ok. 

sudo is a command you use to run another command as root in a terminal. heres what it looks like (don't worry what pwd is):
```

alpha10@21of2:~$ sudo pwd
[sudo] password for alpha10: 
/home/alpha10
alpha10@21of2:~$ 

```

gksu and gksudo are the same as sudo, but they are for GUI applications, like clamtk

you can update daily if you like, but if your talking about a desktop machine, you really don't need an AV scanner. i know it's hard to believe, but it is pretty true.

---

### Post by Coolride on 2008-10-01
I caught a virus pretty easy with Linux. I first noticed something was a miss when my browser screen size was messed up, so I reinstalled firefox, and that fixed that, but then Ubuntu would freeze when booting sometimes. I downloaded clam, and then ran it, and it found a trojan downloader virus of some kind, so i deleted it, and alls fine now. So now I use Avast for Linux, and check my system when I remember too.

---

