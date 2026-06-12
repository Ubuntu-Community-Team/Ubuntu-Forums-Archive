---
title: "Gaining access as root in ubuntu 10.10"
date: 2011-03-22
forum: Recurring Discussions
---

### Post by Johnny California on 2011-03-22
MY GOD NO!!!!  You should NEVER have access to root in your own computer!!! ITS VERY VERY DANGEROUS!!!  You could cause a hard drive EXPLOSION and take out California and perhaps part of Nevada!!!   Since only we are smart enough not to do this, and care for your own good...We will only let you use SUDO...(Remember its very dangerous)  SUDO is not as dangerous, as it could MAYBE only blow up a city like say the size of San Francisco, So be very careful not to slip hit your head, and delete any important system files...You know...Like when you drop your cigarette and accidentally type 'DELETE SYSTEM FILES' as you reach down to pick it up?  Let that cigarette burn, its not going anywhere...Keep your eyes on the keyboard at all times so you don't type anything dangerous (did I mention its really dangerous?).  You must NEVER question the machine my friend. 

  Other than that...Linux is a free operating system, and your free to do anything with it you wish.  Made by people who cherish freedom of speech and expression....

   ...The reluctant SUDOfed
:guitar::lolflag:

---

### Post by jerome1232 on 2011-03-22
edit: This wasn't directed at the op

I don't mean to be rude but you clearly don't understand WHY running as root is discouraged, and it is discouraged for good reason.


It's not because we're "saving" yourself from pressing the "delete system files" button.

While your running as root, every program, script, addon, java applet, and web page ran under root has the ability to modify any system file. 


Do you understand what that means? Any program you ran would have access to system files. Furthermore any script Firefox ran would have full access to your system files. Say hello dns redirection, say hello keyloggers.

I think the implications there are obvious. If you want to unlock the root account, you can find out by using google. IF you cannot find the answer to unlocking the root account using google than I daresay you ARE in danger of deleting system files based on your lack of familiarity with using a computer.



There is simply no reason for a ***Home*** ***Desktop ***System to run as root all the time. None.

---

### Post by Johnny California on 2011-03-22
Oh come on....So not only can we NOT play with our own computers...but we can't even have a little laugh based on the 2.3 million times someone says how "Dangerous" it is to log into your computer as root???  Lighten up.  Sometimes its even good to laugh at yourself...PEACE

---

### Post by Johnny California on 2011-03-22
BTW...Brilliant speech...except your directing it at the wrong person...No offence there Einstein, but I already know how to log into my computer.  Scroll back and read the rest of the posts...

BRILLIANT PEOPLE EXCITE ME

---

### Post by howefield on 2011-03-23
3 of the posts add nothing to the support question asked, therefore spliced off to own thread.

---

### Post by slackthumbz on 2011-03-23
[IMG]http://images.whatport80.com/images/thumb/c/cf/Trollface.jpg/400px-Trollface.jpg[/IMG]

```
sudo su
```

Problem OP?

---

### Post by sydbat on 2011-03-23
Like a bad penny, glossywhite just keeps coming back...this time in the guise of Johnny California. That makes at least 5 I have noticed since the original burnt beans...

Well played trolling is well played.

---

### Post by RiceMonster on 2011-03-23
> **sydbat said:**
> Like a bad penny, glossywhite just keeps coming back...this time in the guise of Johnny California. That makes at least 5 I have noticed since the original burnt beans...

Well played trolling is well played.

We should let him stay for the lulz

---

### Post by sydbat on 2011-03-23
> **RiceMonster said:**
> We should let him stay for the lulzAlthough, I am beginning to enjoy the 'challenge' of picking glossy out of the new users.

---

### Post by NightwishFan on 2011-03-23
> **sydbat said:**
> Although, I am beginning to enjoy the 'challenge' of picking glossy out of the new users.

Indeed, I noticed this myself.

Glossywhite if that is truly you, I bear you no enmity. If you wanted to post here so badly why not have a calm and good manner in your original account? :confused: I believe that ship has sailed.

As for the topic this thread is quite useful:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MarcusW on 2011-03-23
I think the root account is disabled for simplicity, not because it's "too dangerous". "sudo -s" will do the same thing as "su". Logging in as root in gdm is disabled even if the root account is enabled, so that doesn't change anything. The only real limitation I can think if is that you can't log in to a tty as root, but "sudo -s" after you've logged in isn't that hard, and you only have to remember *your* username/passwd.

---

### Post by sisco311 on 2011-03-23
> **MarcusW said:**
> I think the root account is disabled for simplicity, not because it's "too dangerous". "sudo -s" will do the same thing as "su". Logging in as root in gdm is disabled even if the root account is enabled, so that doesn't change anything. The only real limitation I can think if is that you can't log in to a tty as root, but "sudo -s" after you've logged in isn't that hard, and you only have to remember *your* username/passwd.

+1 and **sudo -i** will do (almost) the same thing as **su -**. ;)

Oh, and there is another little difference. If the root account password is enabled, you will be prompted for it when you boot in (switch to) single user mode (a.k.a recovery mode).

---

### Post by lisati on 2011-03-23
I don't recall [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) being mentioned in this thread..... :D

---

### Post by NightwishFan on 2011-03-23
> **NightwishFan said:**
> 
As for the topic this thread is quite useful:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ninja'd by NwF

---

### Post by aysiu on 2011-03-26
> **MarcusW said:**
> "sudo -s" will do the same thing as "su". I'd recommend ```
sudo -i
``` instead. You're far less likely to accidentally change ownership of a configuration file to root from user.

---

