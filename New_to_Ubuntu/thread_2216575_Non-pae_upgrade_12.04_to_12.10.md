---
title: "Non-pae upgrade 12.04 to 12.10"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by mattw1 on 2014-04-12
Hello. I'm sure that this question has been asked a thousand times but I could not find a specific answer anywhere in the threads so I apologize for taking up time and space.

 I have an old thinkpad t42 on which I recently installed lunbuntu 12.04.  It is dual boot with Windows XP which I keep to run some very specific, non-internet dependent programs.The machine has a pentium M chip in it and 768mb RAM.  It is, as I understand it, a non-pae machine, whatever that means.  Anyway, I installed lubuntu 12.04 because of the expiration of XP support and in the short time I have been using it, I think it is great.  But now I get a pop up screen asking me if I want to upgrade to 12.10 and I don't know if I should because of the PAE issue, that is, my thinkpad is, as I said, non-pae and, again, as I understand it, 12.10 does not support non-pae.  

Thank you 

Matt W

IBM Thinkpad T42
768mb RAM
60gb HD

---

### Post by mörgæs on 2014-04-12
It has indeed. Please see this one:

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by mattw1 on 2014-04-12
Thank you. Yes, I had read all of that prior to posting but I have to admit to not fully understanding it.  I guess my real question is this:  I understand that if I were to do a clean install of 12.10, it would not work on my non-pae machine.  In fact, I tried it and that's how I found out I needed to use 12.04, because I got an error message.  But, in this case, because it would be an "upgrade" from an existing, already installed and working system, I thought that might make a difference.  And to be honest, I still don't know the answer.  Thanks again.  Matt.

---

### Post by mörgæs on 2014-04-12
At the very top of the text you will see that a new boot option **forcepae** has been added to 14.04, eliminating all the trouble in relation to 12.10 and 13.*.
Always fresh installs.

---

### Post by mattw1 on 2014-04-12
Went ahead and did that.  Worked fine and am now working with 14.04. Thank you.  One last question:  Can you tell me how I enable the "available wireless networks" icon -or something that tells what wireless connections are available - on the bottom taskbar?  I've looked through all of the available panel applets but can't seem to find one for that purpose.

---

