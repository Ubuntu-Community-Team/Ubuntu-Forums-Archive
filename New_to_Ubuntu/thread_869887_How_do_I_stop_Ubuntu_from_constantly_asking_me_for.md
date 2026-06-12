---
title: "How do I stop Ubuntu from constantly asking me for my password?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by nathanscottdaniels on 2008-07-25
HA!  People think Vista is over-protective.  At least it doesn't ask for your password every five minutes whenever you want to change a setting or install a program.  And at least Vista's prompts can be turned off.  How do I turn them off in Ubuntu?

---

### Post by overdrank on 2008-07-25
> **nathanscottdaniels said:**
> HA!  People think Vista is over-protective.  At least it doesn't ask for your password every five minutes whenever you want to change a setting or install a program.  And at least Vista's prompts can be turned off.  How do I turn them off in Ubuntu?

Hi and it is not wise and that is why Ubuntu is secure.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by brian_p on 2008-07-25
> **nathanscottdaniels said:**
> HA!  People think Vista is over-protective.  At least it doesn't ask for your password every five minutes whenever you want to change a setting or install a program.  And at least Vista's prompts can be turned off.  How do I turn them off in Ubuntu?

Editing /etc/sudoers is one way but coincidentally:

[http://ubuntuforums.org/showthread.php?t=857449](http://ubuntuforums.org/showthread.php?t=857449)

---

### Post by aeiah on 2008-07-25
run as root. its there for a reason, though. in normal day to day usage you probably wont need to type your password every 5 minutes. perhaps instead you should consider setting your password to something very very short until you have everything set up as you'd like, and then go back to a safer password.

---

### Post by m_ad on 2008-07-25
> **nathanscottdaniels said:**
> HA!  People think Vista is over-protective.  At least it doesn't ask for your password every five minutes whenever you want to change a setting or install a program.  And at least Vista's prompts can be turned off.  How do I turn them off in Ubuntu?

You don't - this is to protect your files. Try reading [this]("http://www.psychocats.net/ubuntu/permissions") article.

> What you may be used to
My guess is you're probably a typical ex-Windows user (as I was), used to running as Administrator and being able to edit pretty much any file you want&#8212;even system files, even the registry&#8212;at will, very little stopping you... maybe the occasional "read-only" file that you can just make read/write by checking a little box in the Properties dialogue.

You may also never have installed and configured an operating system before (especially if you bought a computer with Windows preinstalled for you). 

---

### Post by muteXe on 2008-07-25
@OP:  if you prefer unsecure systems I suggest you stay with windows.

---

### Post by Frenske on 2008-07-25
sudo is more or less to protect the files from YOU and off course other people too.

---

### Post by adamogardner on 2008-07-25
if you want to execute several commands in a row here are two ways to go:
1st, you can execute the sudo -s command which will execute a shell as root user. 2nd, you can do the same thing by rinnung the sudo /bin/bash command.  Don't forget to exit the root shell when your done, Otherwise..

---

### Post by BDNiner on 2008-07-25
You can enable to root account and login as root. I would not recommend this though, it is very easy to ruin your system.

---

### Post by nathanscottdaniels on 2008-07-25
I am not an ex-windows user, I AM a Windows Vista user. (I am not poor, I can buy my OS)  I just have to run Ubuntu on my laptop (reluctantly) because one of the fans broke and now XP runs it too hot and kills the battery to fast.

Anyway, what I am talking about is the prompts that come up every time I click Add/Remove Programs and similar applets.  Normal day-to-day use for me DOES require my password every five minutes  because everything stops working on this system and i have to go in and fix it.  I don't give a damn if it is insecure not to have the password prompts.  I would never trust my important data to a homemade OS anyway.

---

### Post by LowSky on 2008-07-25
So you come on a ubuntu forum and bash us for our choice to use something more secure and free, and then mention that you use Vista, then XP (which is it). 
Also read other people postings as Overdrank gave you the answer to your Root question. And in this day and age why can't you type "root linux" into a google or yahoo, or msn (maybe Windows Live, As you seem to prefer Microsoft products). Be kind to us, because as a person who can afford an OS you came here for free help, seems cheap.

---

### Post by overdrank on 2008-07-25
> **nathanscottdaniels said:**
> I am not an ex-windows user, I AM a Windows Vista user. (I am not poor, I can buy my OS)  I just have to run Ubuntu on my laptop (reluctantly) because one of the fans broke and now XP runs it too hot and kills the battery to fast.

Anyway, what I am talking about is the prompts that come up every time I click Add/Remove Programs and similar applets.  Normal day-to-day use for me DOES require my password every five minutes  because everything stops working on this system and i have to go in and fix it.  I don't give a damn if it is insecure not to have the password prompts.  I would never trust my important data to a homemade OS anyway.

I see in no previous post about you being poor so you could not buy your OS. I see in no previous post anyone being rude to you, only caution given in advice. If you will read the post I linked in the previous post you will find your answer. Pleas keep it civil and polite.

---

### Post by northern lights on 2008-07-25
> **nathanscottdaniels said:**
> I am not an ex-windows user, I AM a Windows Vista user. (I am not poor, I can buy my OS)
Hey, don't imply what you're implying...

> **nathanscottdaniels said:**
> I just have to run Ubuntu on my laptop (reluctantly) because one of the fans broke
As if an operating system was cheaper than a new fan...
(compare above quote...)
:roll:

> **nathanscottdaniels said:**
> I would never trust my important data to a homemade OS anyway.
Maybe you had better called it:
I would never trust myself to "homemake" and maintain an OS stable enough for my important data.


I'm usually not much of a hater, but please Nathan, whether reluctantly or not, _you_ choose Ubuntu and, more importantly, _you_ are in need of support, so please cut it out and keep it in the realms of the polite...

---

### Post by gerbalblaste on 2008-07-25
Those prompts are there to keep your system secure. They keep your system safe from YOU.

Root is the equivilent of administrator under windows. You can change anything, delete anything on your system. Several times I have been messing around with root and bricked my OS because I didn't know what I was doing.

If you want to use Ubuntu choose a short secure password and get used to typing it in every so often. Once you've got everything configured and installed you won't have to type it in that often.



Insulting people is not the way to get help or win friends. Ubuntu users aren't freeloaders we contribute back to build what we use. **In any case cost is no way to appraise quality.**

---

### Post by adamogardner on 2008-07-25
simma down ow!

---

### Post by germanix on 2008-07-25
nathanscottdaniels, you seem to be an extremely arrogant person and not well informed either. You certainly deserve Vista and Vista deserves you.

---

### Post by aysiu on 2008-07-25
> **adamogardner said:**
> if you want to execute several commands in a row here are two ways to go:
1st, you can execute the sudo -s command which will execute a shell as root user. 2nd, you can do the same thing by rinnung the sudo /bin/bash command.  Don't forget to exit the root shell when your done, Otherwise.. Please **never** run *sudo -s*. It gives you a root prompt, but it uses the user's environment, which can lead to user settings files and folders become owned by root and thus later unchangeable.

If you need a root terminal, use ```
sudo -i
``` instead.

If you need a root browser, use ```
gksudo nautilus
```

I don't really see how the OP could be entering a password every five minutes, though. As far as I know, the *sudo* timeout is fifteen minutes.

You need to enter your password only to change system-wide settings anyway. There should be no need to change system-wide settings every five minutes.

---

### Post by anjilslaire on 2008-07-25
> **nathanscottdaniels said:**
> I am not an ex-windows user, I AM a Windows Vista user. (I am not poor, I can buy my OS)  I just have to run Ubuntu on my laptop (reluctantly) because one of the fans broke and now XP runs it too hot and kills the battery to fast. 

If you're not poor, take your laptop in for repair.

> 
Anyway, what I am talking about is the prompts that come up every time I click Add/Remove Programs and similar applets.  Normal day-to-day use for me DOES require my password every five minutes  because everything stops working on this system and i have to go in and fix it.  I don't give a damn if it is insecure not to have the password prompts.  I would never trust my important data to a homemade OS anyway.

You don't care about security, yet you don't trust your data to this OS.
Try this on for size:
If you ran Windows securely, you wouldn't run as Admin, you'd run as a User, and simply use Run AS, or log into the Admin account to manage these installations, etc. It's what I do on my XP partition.

Also, I would never trust my important data to a system I don't own, and can't be sure of what it's doing. I prefer to actually own my own data, thanks.

---

### Post by billgoldberg on 2008-07-25
Hey guys, it isn't very wise to tell users new to linux in general how to become root.

For their own protection.

No offense to the OP, but if you run as root, you will mess up your install in record time.

When do you need to enter your password?

-> installing software
-> changing/copying/pasting file in the root folder
-> opening some applications (because they do #1 and/or #2)

That's about it?

---

### Post by arpanaut on 2008-07-25
^what they said^

and if I may add; that running any OS on any computer with a broken fan is putting your hardware in jeopardy 
So fix your fan and take your fanboy attitude back to Vista.

See Ya! Wouldn't wanna be Ya......

---

### Post by aysiu on 2008-07-25
nathanscottdaniels, I know you're frustrated, but this is the Ubuntu security model, and we have a forum policy about subverting that model:
[Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=765414)

Please read it. It will give you answers and also tell you the limitations on the kind of help you'll get on these forums (you're welcome to get help elsewhere at your own risk).

---

